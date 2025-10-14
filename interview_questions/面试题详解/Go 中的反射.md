# 面试题解答：Go 中的反射

## 一、基础认知：反射是什么？
**反射（Reflection）** 是 Go 语言提供的一种在**运行时**动态**检查类型信息**和**操作对象值**的机制。  
通过反射，我们可以：
- 在运行时获取变量的类型信息（Type）
- 在运行时获取变量的值（Value）
- 在运行时修改变量的值（前提是可寻址且可设置）
- 在运行时调用对象的方法

Go 语言的反射主要通过标准库 `reflect` 包实现。

---

## 二、核心机制：反射的两大基本概念

在 `reflect` 包中，有两个核心类型：
1. **`reflect.Type`**  
   表示**变量的静态类型信息**（type），不包含值。
   
2. **`reflect.Value`**  
   表示**变量的值信息**（value），可以读取和修改值。

### 1. 获取反射对象
```go
import "reflect"

var x int = 42

t := reflect.TypeOf(x)  // 获取类型信息
v := reflect.ValueOf(x) // 获取值信息

fmt.Println(t) // int
fmt.Println(v) // 42
```

### 2. 从反射对象还原到普通值
```go
y := v.Interface()      // 将 Value 转回 interface{}
z := y.(int)            // 类型断言
fmt.Println(z)          // 42
```

---

## 三、反射的主要作用与功能

### 1. **运行时获取类型信息**
- 获取变量的类型名、Kind（基础类型）、方法列表等。
```go
type User struct {
    Name string
    Age  int
}

u := User{"Alice", 20}
t := reflect.TypeOf(u)

fmt.Println(t.Name())  // User
fmt.Println(t.Kind())  // struct

// 获取字段信息
for i := 0; i < t.NumField(); i++ {
    fmt.Println(t.Field(i).Name) // Name, Age
}
```

### 2. **运行时获取和修改值**
- 使用 `reflect.Value` 可以读取和修改变量值（需要可寻址且可设置）。
```go
var x int = 10
v := reflect.ValueOf(&x).Elem() // 取指针指向的元素
v.SetInt(20)
fmt.Println(x) // 20
```

### 3. **动态调用方法**
- 通过反射可以在运行时调用任意方法。
```go
type Math struct{}

func (m *Math) Add(a, b int) int {
    return a + b
}

m := &Math{}
v := reflect.ValueOf(m)
method := v.MethodByName("Add")
args := []reflect.Value{
    reflect.ValueOf(2),
    reflect.ValueOf(3),
}
result := method.Call(args)
fmt.Println(result[0].Int()) // 5
```

### 4. **结构体标签（Struct Tag）解析**
- 反射是读取结构体标签的唯一方式，广泛用于 JSON 序列化、ORM 映射等。
```go
type User struct {
    Name string `json:"name" db:"username"`
    Age  int    `json:"age"`
}

t := reflect.TypeOf(User{})
field := t.FieldByName("Name")
fmt.Println(field.Tag.Get("json")) // name
fmt.Println(field.Tag.Get("db"))   // username
```

---

## 四、使用场景

### 1. **序列化/反序列化库**
- JSON、XML、Protobuf 等库使用反射来动态处理任意类型。
```go
// encoding/json 内部使用反射
data, _ := json.Marshal(User{"Alice", 20})
fmt.Println(string(data)) // {"name":"Alice","age":20}
```

### 2. **ORM 框架**
- ORM 框架通过反射将结构体映射到数据库表。
```go
// gorm 等 ORM 框架使用反射读取 struct tag
// 自动生成 SQL
```

### 3. **依赖注入框架**
- 依赖注入框架使用反射自动创建对象并注入依赖。

### 4. **测试框架**
- 测试框架使用反射查找并执行测试函数。

### 5. **配置文件解析**
- 从配置文件动态加载到结构体中。

---

## 五、注意事项与最佳实践

### 1. **性能开销**
- 反射操作比直接调用慢 1~2 个数量级，不适合性能敏感的热点路径。

### 2. **类型安全**
- 反射绕过了编译期类型检查，容易引发运行时 panic，需谨慎使用。

### 3. **可设置性（Setability）**
- 只有当 `Value` 是可寻址且不是通过 unexported 字段获取时，才能修改值。
```go
var x int = 10
v := reflect.ValueOf(x)
// v.SetInt(20) // panic: reflect.Value.SetInt using unaddressable value
```

### 4. **避免过度使用**
- 能用静态类型解决的问题，就不要用反射；
- 反射应该作为“最后手段”使用。

---

## 六、面试延伸：加分考点

### 1. **反射的实现原理**
- Go 反射基于类型信息表（type descriptor）和值的指针；
- `reflect.TypeOf` 和 `reflect.ValueOf` 本质上是从接口值中提取类型和值信息。

### 2. **反射与类型断言的区别**
- **类型断言**：编译期已知可能的类型，运行时判断；
- **反射**：完全在运行时动态获取类型信息，更灵活但性能更低。

### 3. **反射的常见陷阱**
- 对不可寻址的值尝试修改；
- 对接口值直接取 `Elem()`；
- 忽略 `Kind()` 与 `Type()` 的区别。

---

## 七、总结：面试答题模板（直接套用）
> Go 中的反射是一种在运行时动态获取类型信息和操作对象的机制，通过 `reflect` 包实现。  
> 它的核心是 `reflect.Type`（类型信息）和 `reflect.Value`（值信息）。  
> 反射的主要作用包括：运行时获取类型信息、读取和修改值、动态调用方法、解析结构体标签等。  
> 广泛应用于序列化/反序列化库、ORM 框架、依赖注入和测试框架等。  
> 使用反射需要注意性能开销、类型安全和可设置性等问题。  
> 反射是一种强大但有代价的工具，应在确实需要动态处理未知类型时使用。
