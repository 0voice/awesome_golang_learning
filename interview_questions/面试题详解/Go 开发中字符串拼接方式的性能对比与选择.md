# 面试题：Go 开发中字符串拼接方式的性能对比与选择
## 一、解题思路：为什么需要选择不同的拼接方式？

Go 的字符串是**不可变类型**，本质是一个只读的字节数组。每次修改或拼接都会产生新的字符串对象并复制底层数据，这导致：

- 频繁拼接会造成大量内存分配与拷贝
- 不同拼接方式在性能和适用场景上差异很大

因此，选择合适的拼接方式需要考虑：
- 数据量大小
- 是否在循环中拼接
- 是否需要格式化
- 是否需要同时处理字节和字符串

---

## 二、深度解析：四种核心拼接方式

### 1. `+` 运算符：简单但低效
**用法**：
```go
s := "a" + "b" + "c"
```
**原理**：
- 每次 `+` 都会创建新字符串并复制旧数据
- 循环中使用会导致 O(n²) 时间复杂度和大量临时对象

**适用场景**：
- 少量固定字符串拼接（编译期可优化为一次分配）

---

### 2. `fmt.Sprintf`：方便格式化但性能一般
**用法**：
```go
s := fmt.Sprintf("%s%s%s", "a", "b", "c")
```
**原理**：
- 通过反射解析参数类型
- 格式化处理带来额外开销

**适用场景**：
- 需要格式化输出（如数字与字符串混合）
- 非性能敏感的简单场景

---

### 3. `bytes.Buffer`：字节与字符串混合处理
**用法**：
```go
var buf bytes.Buffer
buf.WriteString("a")
buf.WriteString("b")
buf.WriteString("c")
s := buf.String()
```
**原理**：
- 底层维护 `[]byte` 切片，追加效率高
- `String()` 方法会拷贝底层数据，有额外开销

**适用场景**：
- 同时处理字节和字符串
- 需要利用 `ReadFrom`/`WriteTo` 等流操作方法

---

### 4. `strings.Builder` 与 `strings.Join`：高性能首选
**用法**：
```go
// Builder
var b strings.Builder
b.WriteString("a")
b.WriteString("b")
b.WriteString("c")
s := b.String()

// Join
s := strings.Join([]string{"a", "b", "c"}, "")
```
**原理**：
- `Builder` 底层是 `[]byte`，`String()` 零拷贝转换
- `Join` 预计算总长度，减少内存分配

**适用场景**：
- 大量字符串拼接（尤其是循环中）
- 已知大致长度可提前 `Grow()` 预分配
- 拼接字符串切片并自定义分隔符

---

## 三、避坑指南：性能优化与常见错误

1. **避免循环中使用 `+` 拼接**
   ```go
   // 错误做法
   var s string
   for _, part := range parts {
       s += part  // 每次都会重新分配
   }
   
   // 正确做法
   var b strings.Builder
   b.Grow(totalLen)
   for _, part := range parts {
       b.WriteString(part)
   }
   s := b.String()
   ```

2. **合理使用预分配**
   ```go
   var b strings.Builder
   b.Grow(1024)  // 已知大致长度时提前分配
   ```

3. **注意 `bytes.Buffer` 的拷贝开销**
   - 频繁调用 `String()` 会造成多次内存拷贝
   - 考虑直接使用 `Bytes()` 方法避免拷贝

4. **`fmt.Sprintf` 不适合纯字符串拼接**
   - 性能较差，应优先选择 `strings.Builder` 或 `Join`

---

## 四、回答示例：如何选择最佳拼接方式？

### 场景1：少量固定字符串拼接
```go
// 直接使用 +
s := "hello" + " " + "world"
```

### 场景2：循环中拼接大量字符串
```go
// 使用 strings.Builder 并预分配
var b strings.Builder
b.Grow(len(parts) * avgLen)  // 估算容量
for _, p := range parts {
    b.WriteString(p)
}
s := b.String()
```

### 场景3：拼接字符串切片
```go
// 使用 strings.Join
s := strings.Join(parts, ", ")
```

### 场景4：混合处理字节和字符串
```go
// 使用 bytes.Buffer
var buf bytes.Buffer
buf.WriteString("count: ")
buf.Write([]byte(strconv.Itoa(100)))
s := buf.String()
```

### 场景5：格式化输出
```go
// 使用 fmt.Sprintf
s := fmt.Sprintf("User %s (ID: %d)", name, id)
```
