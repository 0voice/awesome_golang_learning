# 面试题解答：Go 中的锁及 sync.Mutex 与 sync.RWMutex 的区别

## 一、基础认知：为什么需要锁？
在并发编程中，多个 Goroutine 可能同时访问和修改共享资源，这种情况称为**数据竞争（data race）**。  
**锁（Lock）** 是一种同步原语，用来**保证在同一时刻只有一个或一类 Goroutine 可以访问共享资源**，从而避免数据竞争和保证数据一致性。

Go 提供了多种锁机制，其中 `sync.Mutex` 和 `sync.RWMutex` 是最常用的两种。

---

## 二、Go 中常见的锁类型

| 锁类型 | 特点 | 适用场景 |
|--------|------|----------|
| **`sync.Mutex`** | 互斥锁，完全互斥，同一时刻只允许一个 Goroutine 访问 | 写操作频繁，读写比例接近 |
| **`sync.RWMutex`** | 读写锁，允许多个读，但写是互斥的 | 读多写少的场景 |
| **`sync.WaitGroup`** | 不是锁，是同步等待组 | 等待一组 Goroutine 完成 |
| **`sync.Cond`** | 条件变量，用于等待某个条件成立 | 生产者-消费者模型 |
| **`sync.Map`** | 并发安全的 Map，内置读写锁 | 高并发下的 Map 访问 |
| **`sync/atomic` 原子操作** | 无锁机制，通过 CPU 指令保证原子性 | 简单的计数器、标志位等 |

---

## 三、`sync.Mutex` 详解

### 1. 定义
```go
type Mutex struct {
    // 内部实现
}
```
`Mutex` 是 Go 提供的**互斥锁**，实现了 `Locker` 接口：
```go
type Locker interface {
    Lock()
    Unlock()
}
```

### 2. 核心特性
- **互斥性**：`Lock()` 会阻塞直到获取锁，`Unlock()` 释放锁；
- **非可重入**：同一个 Goroutine 不能重复 `Lock()`（会导致死锁）；
- **无读写区分**：无论是读还是写，都需要获取相同的锁。

### 3. 基本用法
```go
var mu sync.Mutex
count := 0

func increment() {
    mu.Lock()
    defer mu.Unlock()
    count++
}
```

---

## 四、`sync.RWMutex` 详解

### 1. 定义
```go
type RWMutex struct {
    // 内部实现
}
```
`RWMutex` 是读写锁，提供两种锁：
- **读锁**：`RLock()` / `RUnlock()`
- **写锁**：`Lock()` / `Unlock()`

### 2. 核心特性
- **多读单写**：多个 Goroutine 可以同时获取读锁，但写锁是互斥的；
- **写优先**（或公平策略）：写锁等待时，新的读锁会被阻塞，防止写饥饿；
- **可升级/降级**：不能直接从读锁升级为写锁（会死锁），但可以从写锁降级为读锁。

### 3. 基本用法
```go
var rwmu sync.RWMutex
data := make(map[string]int)

// 读操作
func get(key string) int {
    rwmu.RLock()
    defer rwmu.RUnlock()
    return data[key]
}

// 写操作
func set(key string, value int) {
    rwmu.Lock()
    defer rwmu.Unlock()
    data[key] = value
}
```

---

## 五、`sync.Mutex` vs `sync.RWMutex` 对比

| 对比维度 | `sync.Mutex` | `sync.RWMutex` |
|----------|--------------|----------------|
| **锁类型** | 互斥锁 | 读写锁 |
| **并发读** | 不允许（读也需要互斥） | 允许（多个读锁可共存） |
| **写操作** | 互斥 | 互斥 |
| **性能** | 简单场景下性能好 | 读多写少场景性能更好 |
| **实现复杂度** | 简单 | 复杂（需要维护读/写状态） |
| **可能问题** | 无特殊问题 | 写饥饿（已在 Go 1.9+ 优化） |
| **适用场景** | 写操作频繁，读写比例接近 | 读多写少 |

---

## 六、使用场景建议

### 1. 优先使用 `sync.Mutex` 的场景
- 写操作频繁，或读写比例接近；
- 临界区操作简单，锁竞争不激烈；
- 避免引入不必要的复杂度。

### 2. 优先使用 `sync.RWMutex` 的场景
- 读多写少（如缓存系统、配置读取）；
- 读操作耗时较长，希望多个读可以并发执行；
- 写操作频率低，且可以接受写等待。

---

## 七、常见错误与最佳实践

### 1. 死锁问题
- **重复 Lock**：同一 Goroutine 重复 `Lock()` 会导致死锁；
- **RLock 升级为 Lock**：已获取读锁的 Goroutine 再尝试获取写锁会导致死锁；
- **忘记 Unlock**：必须保证 `Unlock()` 总是被执行（建议使用 `defer`）。

### 2. 性能考虑
- 锁的粒度要小：只保护必要的共享资源；
- 避免在锁内执行耗时操作；
- 高并发下考虑使用无锁数据结构（`sync/atomic`）或分片锁。

### 3. 读写锁的公平性
- Go 1.9+ 对 `RWMutex` 做了写优先优化，防止写饥饿；
- 在极读多写少的场景下，仍可能出现写等待时间较长的情况。

---

## 八、面试延伸：加分考点

### 1. `sync.Mutex` 的实现原理？
- Go 的 `Mutex` 有两种模式：正常模式和饥饿模式；
- 正常模式下，等待的 Goroutine 排队获取锁，被唤醒的 Goroutine 与新到来的 Goroutine 竞争；
- 饥饿模式下，直接将锁交给等待时间最长的 Goroutine，防止线程饥饿。

### 2. `sync.RWMutex` 如何实现多读单写？
- 内部维护一个写锁和一个读计数；
- 读锁：递增读计数，若写锁已被持有则等待；
- 写锁：等待所有读锁释放，并阻止新的读锁获取。

### 3. 如何选择合适的锁？
- 简单场景优先用 `Mutex`；
- 读多写少用 `RWMutex`；
- 极简单的计数器用 `sync/atomic`；
- 高并发 Map 用 `sync.Map`。

---

## 九、总结：面试答题模板（直接套用）
> Go 提供了多种锁机制，其中 `sync.Mutex` 和 `sync.RWMutex` 是最常用的两种。  
> `sync.Mutex` 是互斥锁，同一时刻只允许一个 Goroutine 访问临界区，适用于写操作频繁的场景；  
> `sync.RWMutex` 是读写锁，允许多个读并发访问，但写操作是互斥的，适用于读多写少的场景。  
> 两者的主要区别在于对读操作的处理：Mutex 完全互斥，RWMutex 区分读写，支持并发读。  
> 使用时需注意死锁风险，合理选择锁类型，并减小锁的粒度以提高性能。
