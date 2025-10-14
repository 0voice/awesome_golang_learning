# 面试题解答：如何控制 Goroutine 的并发数量？

## 一、基础认知：为什么需要控制 Goroutine 并发数量？
Goroutine 虽然轻量（初始栈仅 2KB），但无限制创建会导致：
- 系统资源耗尽（内存、CPU 调度开销剧增）
- 对下游服务造成流量冲击（如高并发数据库请求导致连接池耗尽）
- 程序稳定性下降（GC 压力增大，调度延迟增加）

控制并发数量的核心是**限制同时运行的 Goroutine 数量**，确保系统在可控范围内高效运行。

---

## 二、核心方法：4 种控制 Goroutine 并发数量的方式

### 1. 基于带缓冲 Channel 的信号量（最常用）
**原理**：利用缓冲 Channel 的容量作为并发数上限，每个 Goroutine 启动前先获取“信号”（从 Channel 接收数据），结束后释放“信号”（向 Channel 发送数据）。

```go
func main() {
    const concurrency = 5 // 最大并发数
    sem := make(chan struct{}, concurrency)
    tasks := 20 // 总任务数

    for i := 0; i < tasks; i++ {
        sem <- struct{}{} // 获取信号，满则阻塞
        go func(taskID int) {
            defer func() { <-sem }() // 释放信号
            // 执行任务
            fmt.Printf("处理任务 %d\n", taskID)
            time.Sleep(100 * time.Millisecond)
        }(i)
    }

    // 等待所有信号释放（所有任务完成）
    for i := 0; i < concurrency; i++ {
        sem <- struct{}{}
    }
}
```

**优点**：实现简单，无需额外依赖，天然支持阻塞等待。


### 2. 基于 sync.WaitGroup + 带缓冲 Channel
**原理**：结合 WaitGroup 等待所有任务完成，用 Channel 控制并发数，适合需要等待所有任务结束的场景。

```go
func main() {
    const concurrency = 3
    sem := make(chan struct{}, concurrency)
    var wg sync.WaitGroup
    tasks := 10

    wg.Add(tasks)
    for i := 0; i < tasks; i++ {
        sem <- struct{}{}
        go func(taskID int) {
            defer func() {
                wg.Done()
                <-sem
            }()
            fmt.Printf("处理任务 %d\n", taskID)
            time.Sleep(100 * time.Millisecond)
        }(i)
    }

    wg.Wait() // 等待所有任务完成
}
```

**优点**：清晰控制任务生命周期，适合批量任务场景。


### 3. 基于工作池（Worker Pool）模式
**原理**：预先创建固定数量的 Worker Goroutine，通过任务 Channel 分发任务，Worker 处理完一个任务后再取下一个。

```go
func worker(id int, tasks <-chan int, wg *sync.WaitGroup) {
    defer wg.Done()
    for task := range tasks {
        fmt.Printf("Worker %d 处理任务 %d\n", id, task)
        time.Sleep(100 * time.Millisecond)
    }
}

func main() {
    const (
        concurrency = 4 // Worker 数量（并发数）
        tasksCount  = 15
    )

    tasks := make(chan int, tasksCount)
    var wg sync.WaitGroup

    // 启动 Worker
    wg.Add(concurrency)
    for i := 0; i < concurrency; i++ {
        go worker(i, tasks, &wg)
    }

    // 发送任务
    for i := 0; i < tasksCount; i++ {
        tasks <- i
    }
    close(tasks) // 任务发送完毕，关闭 Channel

    wg.Wait() // 等待所有 Worker 完成
}
```

**优点**：避免频繁创建销毁 Goroutine，适合任务数量多且持续的场景。


### 4. 基于第三方库 ants（高性能 Goroutine 池）
**原理**：`ants` 是一个轻量级、高性能的 Goroutine 池，支持动态调整 Worker 数量、任务队列管理和资源复用，简化并发控制。

**安装**：
```bash
go get -u github.com/panjf2000/ants/v2
```

**示例**：
```go
package main

import (
    "fmt"
    "time"
    "github.com/panjf2000/ants/v2"
)

func taskFunc(taskID int) {
    fmt.Printf("处理任务 %d\n", taskID)
    time.Sleep(100 * time.Millisecond)
}

func main() {
    defer ants.Release() // 释放池资源

    const (
        concurrency = 5 // 最大并发数
        tasksCount  = 20
    )

    // 创建一个带缓冲的 Goroutine 池，设置最大并发数
    pool, err := ants.NewPool(concurrency)
    if err != nil {
        panic(err)
    }

    // 提交任务
    for i := 0; i < tasksCount; i++ {
        taskID := i
        // 向池提交任务，超过并发数时任务会进入队列等待
        if err := pool.Submit(func() {
            taskFunc(taskID)
        }); err != nil {
            fmt.Printf("提交任务 %d 失败: %v\n", taskID, err)
        }
    }

    pool.Wait() // 等待所有任务完成
    fmt.Println("所有任务处理完毕")
}
```

**核心特性**：
- 自动管理 Goroutine 生命周期，避免频繁创建销毁开销
- 支持任务队列缓冲，超过并发数的任务会排队
- 提供超时控制、错误处理、动态调整 Worker 数量等高级功能
- 性能优异，适合高并发场景

**优点**：开箱即用，功能完善，大幅简化并发控制代码，适合生产环境。

---

## 三、关键区别与场景选择

| 方法 | 适用场景 | 优点 | 缺点 |
|------|----------|------|------|
| 信号量 Channel | 简单并发控制，临时任务 | 实现简单，轻量 | 需手动等待所有任务结束 |
| WaitGroup + Channel | 批量任务，需等待完成 | 清晰控制生命周期 | 代码稍复杂 |
| 工作池模式 | 高频任务，长期运行 | 性能好，可复用 Worker | 初始化成本高，需手动实现队列 |
| ants 库 | 生产环境，复杂并发场景 | 功能完善，性能优，支持高级特性 | 依赖第三方库 |

**选择建议**：
- 简单场景或demo优先用“信号量 Channel”
- 自建项目且需可控性用“工作池模式”
- 生产环境、高并发或复杂场景优先用“ants 库”（成熟稳定，减少重复造轮子）

---

## 四、注意事项与最佳实践

1. **合理设置并发数**：
   - 计算密集型任务：并发数 ≈ CPU 核心数
   - I/O 密集型任务：并发数可适当提高（如 10~100，根据下游服务承载能力调整）

2. **避免 Goroutine 泄漏**：
   - 手动实现时确保所有 Goroutine 能正常退出（通过 Channel 关闭、上下文取消等）
   - 使用 ants 时需调用 `ants.Release()` 释放资源

3. **监控与调优**：
   - 手动实现可通过 `runtime.NumGoroutine()` 监控实时 Goroutine 数量
   - ants 提供 `Pool.Stats()` 方法查看池状态（活跃 Worker 数、排队任务数等）

4. **结合 context 实现超时控制**：
   ```go
   // ants 中结合 context 控制任务超时
   ctx, cancel := context.WithTimeout(context.Background(), 5*time.Second)
   defer cancel()
   
   pool.Submit(func() {
       select {
       case <-ctx.Done():
           fmt.Println("任务超时")
           return
       default:
           taskFunc(taskID)
       }
   })
   ```

---

## 五、面试延伸：加分考点

1. **ants 库的核心优势是什么？**  
   - 复用 Goroutine 减少创建销毁开销（比原生 Goroutine 池性能提升 30%+）
   - 支持任务队列和阻塞/非阻塞提交模式
   - 提供完善的错误处理和资源监控
   - 兼容 context 实现超时和取消

2. **手动实现 vs 第三方库如何选择？**  
   - 面试中需掌握手动实现原理（体现对并发的理解）
   - 实际开发中优先用成熟库（如 ants），减少bug，提高效率

3. **高并发场景下 ants 如何避免性能瓶颈？**  
   - 采用无锁队列减少竞争
   - 预创建 Worker 减少动态调度开销
   - 支持任务批处理和优先级队列（高级特性）

---

## 六、总结：面试答题模板（直接套用）
> 控制 Goroutine 并发数量的核心是限制同时运行的 Goroutine 数量，常用方法有四种：  
> 1. 基于带缓冲 Channel 的信号量：利用缓冲区容量控制并发，实现简单；  
> 2. 结合 sync.WaitGroup：适合批量任务，需等待所有任务完成；  
> 3. 工作池模式：预先创建固定数量 Worker，适合高频任务；  
> 4. 第三方库 ants：高性能 Goroutine 池，支持任务队列和资源复用，适合生产环境。  
> 选择时需根据场景：简单场景用信号量 Channel，自建项目用工作池，生产环境优先用 ants 库。  
> 注意合理设置并发数，避免 Goroutine 泄漏，并结合 context 实现超时控制。
