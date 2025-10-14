# 面试题解答：如何用 context 实现请求超时控制

## 一、基础认知：context 是什么？
**context** 是 Go 语言在 `context` 包中提供的一种**跨 Goroutine 传递请求作用域数据、取消信号和截止时间**的机制。  
它主要用于：
- 传递请求上下文（如 trace ID、用户信息）
- 控制 Goroutine 生命周期（取消、超时）
- 在复杂调用链中统一管理截止时间

context 包的核心类型是：
```go
type Context interface {
    Deadline() (deadline time.Time, ok bool)
    Done() <-chan struct{}
    Err() error
    Value(key interface{}) interface{}
}
```

---

## 二、核心机制：context 控制超时的原理

### 1. 三种创建可取消 context 的方式
1. **`context.WithCancel(parent)`**  
   创建可手动取消的 context
   
2. **`context.WithDeadline(parent, d)`**  
   创建在指定时间点自动取消的 context
   
3. **`context.WithTimeout(parent, timeout)`**  
   创建在指定时长后自动取消的 context（本质是 `WithDeadline` 的封装）

### 2. 超时控制的工作原理
- 当 context 被取消（手动或超时），其 `Done()` 通道会被关闭；
- 监听 `Done()` 通道即可感知取消事件；
- 配合 `select` 语句，可以在超时或取消时中断当前操作。

---

## 三、实战代码：用 context 实现请求超时控制

### 场景：HTTP 请求超时控制
```go
package main

import (
    "context"
    "fmt"
    "net/http"
    "time"
)

func main() {
    // 创建一个 2 秒超时的 context
    ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
    defer cancel() // 确保资源释放

    req, err := http.NewRequestWithContext(ctx, "GET", "https://example.com", nil)
    if err != nil {
        fmt.Printf("创建请求失败: %v\n", err)
        return
    }

    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        // 检查是否是超时错误
        if ctx.Err() == context.DeadlineExceeded {
            fmt.Println("请求超时")
            return
        }
        fmt.Printf("请求失败: %v\n", err)
        return
    }
    defer resp.Body.Close()

    fmt.Printf("请求成功，状态码: %d\n", resp.StatusCode)
}
```

### 场景：自定义任务超时控制
```go
package main

import (
    "context"
    "fmt"
    "time"
)

func doTask(ctx context.Context) error {
    select {
    case <-time.After(3 * time.Second): // 模拟耗时任务
        fmt.Println("任务完成")
        return nil
    case <-ctx.Done(): // 监听取消信号
        return ctx.Err()
    }
}

func main() {
    ctx, cancel := context.WithTimeout(context.Background(), 2*time.Second)
    defer cancel()

    err := doTask(ctx)
    if err != nil {
        if err == context.DeadlineExceeded {
            fmt.Println("任务执行超时")
        } else {
            fmt.Printf("任务执行失败: %v\n", err)
        }
        return
    }
    fmt.Println("程序正常结束")
}
```

---

## 四、注意事项与最佳实践

### 1. 传递 context 而非派生多个
- context 应该在调用链中传递，而不是在每个函数中创建新的根 context
- 这样可以确保整个调用链共享同一个取消信号

### 2. context 是线程安全的
- context 可以被多个 Goroutine 同时使用
- 但通常建议在调用链中传递，而非跨多个独立流程共享

### 3. 尽早取消无用的 context
- 使用 `defer cancel()` 确保即使函数提前返回，也能及时释放资源
- 避免 Goroutine 泄漏

### 4. 不要存储 context 到结构体中
- context 应该显式传递，而不是作为结构体字段
- 结构体应该设计为无状态或自包含的

### 5. 区分取消原因
- `ctx.Err()` 返回 `context.DeadlineExceeded` 表示超时
- 返回 `context.Canceled` 表示手动取消

---

## 五、面试延伸：加分考点

### 1. context 与 channel 的区别？
- **context**：专注于请求作用域的生命周期管理，可传递数据
- **channel**：通用的通信机制，可传递任何数据，不限于生命周期管理

### 2. 如何实现级联超时控制？
父级 context 取消会级联取消所有子 context：
```go
root := context.Background()
parent, cancel := context.WithTimeout(root, 5*time.Second)
defer cancel()

child, _ := context.WithTimeout(parent, 10*time.Second) // 实际超时时间是 5 秒
```

### 3. context 的实现原理？
- context 本质上是一个不可变的数据结构
- 取消信号通过 channel 广播
- 子 context 会监听父 context 的取消信号

---

## 六、总结：面试答题模板（直接套用）
> Go 的 context 包提供了请求作用域的生命周期管理机制，可用于传递数据、取消信号和控制超时。  
> 实现请求超时控制主要使用 `context.WithTimeout` 或 `context.WithDeadline` 创建带超时的 context，然后在业务逻辑中监听 `ctx.Done()` 通道。  
> 当超时发生时，`ctx.Done()` 会被关闭，我们可以通过 `ctx.Err()` 判断是超时还是手动取消。  
> 最佳实践包括：在调用链中传递 context、使用 `defer cancel()` 及时释放资源、区分不同的取消原因。  
> context 在线程安全的前提下，实现了跨 Goroutine 的生命周期管理，是构建可靠服务的重要工具。
