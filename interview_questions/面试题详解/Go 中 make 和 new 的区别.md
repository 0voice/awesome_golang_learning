# 面试题解答：Go 中 make 和 new 的区别

## 一、基础认知：make 和 new 是什么？

### 1. **new**
- **作用**：为**任意类型**分配内存，并返回指向该类型零值的**指针**。
- **语法**：`new(T)`
- **返回值类型**：`*T`
- **特点**：
  - 分配内存
  - 将内存置为零值
  - 返回指针

**示例**：
```go
p := new(int)      // p 是 *int 类型
fmt.Println(*p)    // 输出 0
```

---

### 2. **make**
- **作用**：只能为 **slice、map、channel** 这三种引用类型分配内存并初始化。
- **语法**：`make(T, size)` 或 `make(T, size, cap)`（slice 可指定容量）
- **返回值类型**：`T`（不是指针）
- **特点**：
  - 分配内存
  - 初始化（准备好数据结构，如 slice 的底层数组、map 的哈希表、channel 的环形队列）
  - 返回初始化后的**引用类型本身**

**示例**：
```go
s := make([]int, 0, 5)  // len=0, cap=5
m := make(map[string]int)
ch := make(chan int, 1)
```

---

## 二、核心区别对比

| 对比维度 | new | make |
|----------|-----|------|
| **适用类型** | 任意类型 | 仅 slice、map、channel |
| **返回值** | `*T`（指针） | `T`（引用类型本身） |
| **内存初始化** | 仅置零值 | 置零值 + 初始化内部结构 |
| **分配位置** | 堆或栈（编译器逃逸分析决定） | 堆（通常） |
| **用途** | 创建值类型指针或需要零值指针的场景 | 创建并初始化引用类型 |

---

## 三、使用场景

### 1. **适合用 new 的场景**
- 需要一个指向零值的指针：
```go
type User struct {
    Name string
    Age  int
}

u := new(User) // u 是 *User，字段全为零值
```
- 配合 sync.Pool 等需要指针的场景

### 2. **适合用 make 的场景**
- 创建 slice、map、channel 并初始化：
```go
nums := make([]int, 3, 10)
cache := make(map[string]interface{})
messages := make(chan string, 100)
```

---

## 四、底层原理分析

### 1. **new 的底层**
`new(T)` 在编译后会被转换为 `runtime.newobject`，它：
1. 分配 `sizeof(T)` 大小的内存块
2. 将内存清零
3. 返回 `*T` 类型的指针

### 2. **make 的底层**
`make(T, ...)` 会根据类型调用不同的 runtime 函数：
- **slice**：`runtime.makeslice`（分配底层数组并设置 len/cap）
- **map**：`runtime.makemap`（创建 hmap 结构并初始化桶）
- **channel**：`runtime.makechan`（创建 hchan 结构并分配环形缓冲区）

这些函数不仅分配内存，还会对数据结构进行必要的初始化。

---

## 五、易错点

1. **对引用类型使用 new**：
```go
m := new(map[string]int)
// *m["key"] = 1 // 编译错误：invalid indirect of m["key"] (type int)
```
正确做法是使用 make：
```go
m := make(map[string]int)
m["key"] = 1
```

2. **忘记 make 而直接使用引用类型**：
```go
var s []int
s[0] = 1 // panic: runtime error: index out of range [0] with length 0
```
正确做法：
```go
s := make([]int, 1)
s[0] = 1
```

---

## 六、面试延伸：加分考点

### 1. **为什么 slice、map、channel 必须用 make 创建？**
因为这三种类型在使用前需要初始化内部数据结构：
- slice 需要底层数组和 len/cap 设置
- map 需要哈希表结构初始化
- channel 需要环形队列和同步结构初始化

`new` 只会分配内存并置零，不会进行这些必要的初始化。

### 2. **make 与复合字面量的区别？**
复合字面量（如 `[]int{1,2,3}`）也能创建 slice/map，但它是**创建并初始化内容**，而 make 是**创建并初始化结构**。

### 3. **性能对比**
- `new` 非常轻量，几乎无额外开销
- `make` 除了分配内存，还有初始化开销（尤其是 map 和 channel）

---

## 七、总结：面试答题模板（直接套用）
> Go 中的 `new` 和 `make` 都是内存分配函数，但用途不同。  
> `new(T)` 为任意类型分配内存并返回指针 `*T`，仅将内存置为零值；  
> `make(T)` 只能用于 slice、map、channel，返回类型本身，不仅分配内存还会初始化内部结构。  
> 选择建议：创建值类型指针用 `new`，创建引用类型用 `make`。  
> 常见错误是对引用类型使用 `new` 或忘记 make 直接使用引用类型。
