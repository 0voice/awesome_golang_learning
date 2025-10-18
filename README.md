# 🔥 Awesome Golang Learning: One-Stop Guide to Master Go (2025 Edition)

## English Overview

A curated roadmap for Go learners: From zero basics to advanced (Go 1.23+). Covers syntax, concurrency, frameworks (Gin/Beego), DB (GORM/Redis), and new 2025 tracks: Cloud-native (K8s/Docker) & AI (LangChain-Go RAG bots). Includes 69 interview Qs, books/videos, and 10+ hands-on projects to avoid common pitfalls.

**Quick Learning Path (Table Summary):**

| Stage        | Duration   | Focus                                 | Project Example                                              |
| ------------ | ---------- | ------------------------------------- | ------------------------------------------------------------ |
| Beginner     | 1-2 weeks  | Syntax, setup                         | Guessing game (code: fib seq + file I/O)                     |
| Intermediate | 3-4 weeks  | Concurrency, Gin API, testing         | RealWorld app (Gin + JWT + unit tests)                       |
| Advanced     | 2-3 months | Microservices, Redis, **NEW: K8s/AI** | Todo microservice (gRPC + Docker) or RAG Chatbot (LangChain-Go) |

Dive deeper in Chinese below for full resources! 👇  

 <h1 align="center">📚 Golang一站式学习仓库</h1>
 <p align="center">
  🌟 本仓库旨在为学习 Golang 的程序员们提供学习资源导航
</p>
 <p align="center">
  💡 涵盖从基础知识到实战项目的资料与示例，帮助你快速入门并逐步进阶！持续更新中······
</p>

🆕 **更新说明（2025.10.17）**：基于2025年Go生态（Go 1.23+），路径更注重实践导向。新增**测试**（进阶防bug）、**云原生**（高级部署K8s）和**AI分支**（高级玩LangChain-Go建bot）。新增☁️云原生和🤖AI相关技术文章和配套实战项目。

---

## 📌 目录

* [简介](#-简介)
* [仓库一览](#-仓库一览)
* [推荐学习路径](#-推荐学习路径)
* [学习资料](#-学习资料)
  * [官方资料](#-官方资料)
  * [精选书籍](#-精选书籍)
  * [入门教程](#-入门教程)
  * [进阶技术](#-进阶技术)
  * [技术文章](#-技术文章)
  * [学习视频](#-学习视频)
  * [面试题](#-面试题)
* [Web框架](#-Web框架)
  * [Gin框架](#Gin框架)
  * [Beego框架](#Beego框架)
* [相关技术](#-相关技术)
  * [网络基础](#-网络基础)
  * [MySQL](#-MySQL)
  * [Redis](#-Redis)
* [项目实战](#-项目实战)
---

## 🚀 简介
Golang（又称 Go）是由Google于 2009 年推出的静态强类型、编译型编程语言，核心设计目标是解决 “大规模系统开发中的效率、并发、部署复杂度” 问题，兼顾了 C 语言的性能与 Python 的开发便捷性，目前已成为云原生、后端服务、工具开发领域的主流语言之一。

---

## 🔍 仓库一览

* 提供 基础知识 + 工具框架 + 实战项目 的学习参考

* 收录 学习资料、书籍、面试题、开源项目，避免信息碎片化

---


## 🐾 推荐学习路径

### 一、入门阶段（1-2周）：🔥搞定基础语法，跑通第一个程序

#### 🎯核心目标
掌握 Go 基础语法，能独立写简单程序，理解模块化开发。

#### 📖必学资源
| 学习类型 | 推荐资源 | 核心任务 |
|----------|----------|----------|
| 环境搭建 | 1. 「学习资料-官方资料-Go官方文档」安装指南<br>2. 「技术文章-下载和安装Go」 | 10分钟内完成SDK安装，能运行 `go version` 验证 |
| 语法学习 | 1. 「入门教程-官方教程」（边学边练）<br>2. 「精选书籍-入门阶段-Go 语言圣经」前5章<br>🆕 B站“尚硅谷Go入门”前3小时 | 掌握变量/切片/map/函数/循环，能写简单逻辑 |
| 辅助资源 | 1. 「学习视频-8小时转职Golang工程师」前3小时<br>2. 语法卡壳查「入门教程」的学习网站 | 快速解决基础疑问，避免卡壳 |

#### 🛠️配套实战项目（难度 ⭐，入门级）
直接练「小案例+简单项目」，巩固语法：
1. 基础小练习：写「斐波那契数列」「简单文件读写」「命令行参数解析」
2. 入门项目：go-by-example 的「guessing-game（猜数字）」和「simpledict（简易翻译）」
   - 前置知识：仅需 Go 基础语法
   - 学习目标：熟悉变量/循环/HTTP 客户端调用，获得第一个可运行的小工具

### 二、进阶阶段（3-4周）：⚡突破核心特性，能做功能开发

#### 🎯核心目标
掌握并发、数据库、Web 框架，能打通「HTTP + 数据库」完整链路。  
🆕 **测试基础**（第3-4周末，学表驱动测试，防并发bug）。

#### 📖必学资源
| 学习类型 | 推荐资源 | 核心任务 |
|----------|----------|----------|
| 核心特性 | 1. 「进阶技术-并发」「进阶技术-错误处理」「进阶技术-标准库」<br>2. 「精选书籍-进阶阶段-Effective Go」<br>🧪 **测试资源**：「技术文章-Golang单元测试最佳实践：避免常见陷阱」「技术文章-深入掌握Go 单元测试：从基础到进阶的完整指南」「技术文章-Go 单元测试进阶：AI 加持下的高效实践与避坑指南」| 理解 goroutine/channel/sync 包，能处理并发任务；🧪测试：用testing包覆盖80%代码，跑race detector查bug |
| 数据库 | 1. 「相关技术-MySQL」基础连接与增删改查<br>2. 「相关技术-GORM」入门用法 | 能用 GORM 完成数据的 CRUD，理解 ORM 映射 |
| Web 框架 | 1. 「Web框架-Gin框架」基础路由与中间件<br>2. 「技术文章-使用 Go 和 Gin 开发 RESTful API」<br>🧪 **测试**：「技术文章-Go 单元测试完全指南（一）- 基本测试流程」 | 能写简单接口，处理请求参数和返回 JSON；🧪测试：为接口加单元测试（e.g., mock DB） |

#### 🛠️配套实战项目（难度 ⭐⭐-⭐⭐⭐，进阶级）
选择 1-2 个项目练手，重点在“功能实现”+测试：
1. golang-gin-realworld-example-app
   - 前置知识：Gin 框架 + RESTful API 概念
   - 学习目标：实现完整的用户/文章 CRUD 接口，掌握 JWT 认证和 API 规范
   - 🆕 **新增测试**：加单元测试（testing + testify），覆盖CRUD 80%
2. go-backend-clean-architecture
   - 前置知识：HTTP 服务 + 分层架构概念
   - 学习目标：理解整洁架构，学会按“接口层-业务层-数据层”组织代码
   - 🆕 **新增测试**：跑并发测试（go test -race），查内存泄漏
3. miniblog （基础功能部分）
   - 前置知识：Gin + GORM + JWT 基础
   - 学习目标：实现博客的文章/用户管理，掌握分层开发和简单权限控制
   - 🆕 **新增测试**：表驱动测试用户登录（e.g., 输入/输出表格）（⭐⭐⭐）

**测试代码**（进阶项目中用）：
```go
package main

import "testing"

func TestAdd(t *testing.T) {
    tests := []struct{ a, b, want int }{
        {1, 2, 3},
        {5, 7, 12},
    }
    for _, tt := range tests {  // 表驱动测试
        if got := add(tt.a, tt.b); got != tt.want {
            t.Errorf("add(%d, %d) = %d, want %d", tt.a, tt.b, got, tt.want)
        }
    }
}

func add(x, y int) int { return x + y }
```
运行：`go test`。

### 三、高级阶段（2-3个月）：🏆积累工程经验，能做复杂项目

#### 🎯核心目标
掌握微服务、权限系统、工程化实践，能应对企业级项目需求。  
🆕 **云原生**（第5-6周，Docker/K8s部署微服务，2025后端必备）。  
🆕 **AI分支**（第7-8周，LangChain-Go搞AI代理，玩RAG聊天bot）。

#### 📖必学资源
| 学习类型 | 推荐资源 | 核心任务 |
|----------|----------|----------|
| 微服务/分布式 | 1. 「技术文章-Golang gRPC微服务」「技术文章-微服务调度」<br>2. 「进阶技术-反射」「进阶技术-测试」<br>☁️ **云原生**：「技术文章-2025新范式：Go-blueprint极速集成Kubernetes容器编排实战指南」「技术文章-从单体到Kubernetes：Go 服务如何容器化并上线？」「技术文章-Go语言操作Kubernetes资源的深入指南」；B站“Docker Go部署教程” | 理解 gRPC/服务注册发现，能写单元测试和性能测试；☁️云原生：Docker打包API，K8s部署微服务（kubectl apply） |
| 高级特性 | 1. 「相关技术-Redis」缓存/分布式锁<br>2. 「技术文章-内存泄漏排查」「技术文章-性能分析」 | 能用 Redis 做缓存，了解性能优化和问题排查 |
| 工程化 | 1. 「技术文章-Go Module包管理器」「技术文章-持续集成部署」<br>2. 「精选书籍-深入阶段-Go 语言设计与实现」（选读）<br>☁️ **云原生**：「技术文章-初次尝试Kubernetes + helm 部署golang应用」 | 掌握依赖管理和项目部署，理解 Go 底层原理；☁️云原生：CI/CD用GitHub Actions，上阿里云 |
| **🤖AI分支** | 🆕 「技术文章-（2025）使用langchain实现朴素与进阶RAG」「技术文章-Go最新实现RAG 使用LangChain实现图检索查询(1)」「技术文章-从RAG框架到低代码自动化：LlamaIndex、LangChain 与n8n 全解析！」；B站“LangChain-Go AI入门” | LLM集成（OpenAI API）；RAG管道；AI代理（ReAct模式） |

#### 🛠️配套实战项目（难度 ⭐⭐⭐⭐-⭐⭐⭐⭐⭐，高级）
选择 1 个项目深入开发，重点在“架构设计和工程化”+云/AI：
1. rpcx
   - 前置知识：网络编程 + 服务发现概念
   - 学习目标：实现 RPC 服务的调用与注册，理解分布式系统基础
2. Ferry （工单系统核心功能）
   - 前置知识：Gin + Vue + MySQL/Redis
   - 学习目标：开发带流程引擎的工单系统，处理复杂业务逻辑和权限
3. IAM （身份认证模块）
   - 前置知识：微服务 + OAuth2.0/JWT
   - 学习目标：理解企业级权限系统设计，掌握微服务间通信和安全认证
4. Gin-vue-admin （完整项目）
   - 前置知识：Gin + Vue + Casbin + 代码生成器
   - 学习目标：掌握前后端分离项目的开发流程，熟悉权限控制和工程化工具
5. 🆕 **☁️云原生项目**：微服务Todo App（用gRPC+K8s部署，上阿里云或腾讯云，⭐⭐⭐）
   - 前置知识：gRPC + Docker基础
   - 学习目标：打包Go服务，K8s orchestration；监控用Prometheus
   - **Dockerfile**：
     ```
     FROM golang:1.23 AS build
     WORKDIR /app
     COPY . .
     RUN go build -o main .
     FROM alpine:latest
     COPY --from=build /app/main .
     CMD ["./main"]
     ```
     运行：`docker build -t todo . && docker run -p 8080:8080 todo`。
6. 🆕 **🤖AI项目**：简单RAG聊天bot（LangChain-Go+OpenAI，搜文档答题，⭐⭐⭐⭐）；
   - 前置知识：OpenAI API + 向量DB
   - 学习目标：goroutine并发查询；RAG增强生成；云部署bot到Heroku
   - **快速启动**：
     ```go
     package main

     import (
         "context"
         "github.com/tmc/langchaingo/llms/openai"  // go get github.com/tmc/langchaingo
         "github.com/tmc/langchaingo/chains"
     )

     func main() {
         llm, _ := openai.NewChat()  // 加你的API key
         qa := chains.NewConversationChain(llm)
         res, _ := qa.Call(context.Background(), map[string]any{"input": "Go怎么建AI代理？"})
         fmt.Println(res["response"])  // AI直接回答！
     }
     ```
     运行：`go mod init ai-test && go run main.go`。



推荐资源：[go开源路线图](https://roadmap.sh/golang)

---

## 📚 学习资料
### 🍀 官方资料
**Go官方文档**：[https://go.dev/ref/spec](https://go.dev/ref/spec)

**Go语言中文网**：[https://go.p2hp.com/](https://go.p2hp.com/)

**Go编程最佳实践**：[https://go.dev/doc/effective_go](https://go.dev/doc/effective_go) 

**Go谷歌开源仓库**：[https://cs.opensource.google/go](https://cs.opensource.google/go)

**Go语言GitHub仓库**：[https://github.com/golang/go](https://github.com/golang/go)

---
### 📖 精选书籍
#### 入门阶段
| No. | title | author |
| :--- | :--- | :--- |
| 1 | Go 语言圣经 | Alan A. A. Donovan、Brian W. Kernighan |
| 2 | Go 入门指南 | Caleb Doxsey |

#### 进阶阶段
| No. | title | author |
| :--- | :--- | :--- |
| 1 | Effective Go | Go 官方团队 |
| 2 | Go Web 编程 | 谢孟军 |
| 3 | Go 语言高性能编程 | 极客时间 |

#### 深入阶段
| No. | title | author |
| :--- | :--- | :--- |
| 1 | Go 语言设计与实现 | draveness |
| 2 | Go 高级编程 | 柴树杉、曹春晖 |
| 3 | Go 语言设计哲学 | 陈皓 |

#### 2025推荐新书籍
| 阶段 | 书名 | 作者 | 推荐理由 |
| :--- | :--- | :--- | :--- |
| 入门 | Learning Go (2nd Ed.) | Jon Bodner | 2025更新版，聚焦1.23迭代器，社区Top1 |
| 进阶 | 100 Go Mistakes and How to Avoid Them | Teiva Harsanyi | 实用坑点指南 |
| 深入 | Go 1.23 Personal Top Features | Dmytro Misik | 聚焦PGO和GC优化 |

---
### 📝 入门教程

#### 快速启动
```go
// main.go
package main

import "fmt"

func main() {
    fmt.Println("Hello Go!")
}
```
运行命令：`go mod init hello` && `go run main.go`。  

#### 推荐网站
| No. | address |
| :--- | :--- |
| 1 | [官方教程](https://tour.go-zh.org/welcome/1) |
| 2 | [菜鸟教程](https://www.runoob.com/go/go-tutorial.html) |
| 3 | [C语言中文网](https://c.biancheng.net/golang/syntax/) |
| 4 | [Go语言圣经](https://gopl-zh.github.io/ch1/ch1-01.html) |
| 5 | [Golang中文学习文档](https://golang.halfiisland.com/essential/base/1.grammer.html) |

#### 语法基础
| No. | address |
| :--- | :--- |
| 1 | [基本语法](https://golang.halfiisland.com/essential/base/1.grammer.html) |
| 2 | [数据类型](https://golang.halfiisland.com/essential/base/10.datatype.html) |
| 3 | [常量](https://golang.halfiisland.com/essential/base/30.constant.html) |
| 4 | [变量](https://golang.halfiisland.com/essential/base/40.variable.html) |
| 5 | [输入输出](https://golang.halfiisland.com/essential/base/45.inout.html) |
| 6 | [条件控制](https://golang.halfiisland.com/essential/base/52.condition.html) |
| 7 | [循环控制](https://golang.halfiisland.com/essential/base/55.loop.html) |
| 8 | [切片](https://golang.halfiisland.com/essential/base/60.slice.html) |
| 9 | [字符串](https://golang.halfiisland.com/essential/base/62.string.html) |
| 10 | [映射表](https://golang.halfiisland.com/essential/base/65.map.html) |
| 11 | [指针](https://golang.halfiisland.com/essential/base/67.pointer.html) |
| 12 | [函数](https://golang.halfiisland.com/essential/base/69.func.html) |
| 13 | [结构体](https://golang.halfiisland.com/essential/base/75.struct.html) |
| 14 | [方法](https://golang.halfiisland.com/essential/base/80.method.html) |


---
### 🔧 进阶技术
| No. | address |
| :--- | :--- |
| 1 | [接口](https://golang.halfiisland.com/essential/senior/85.interface.html) |
| 2 | [泛型](https://golang.halfiisland.com/essential/senior/90.generic.html) |
| 3 | [迭代器](https://golang.halfiisland.com/essential/senior/91.iterator.html) |
| 4 | [类型](https://golang.halfiisland.com/essential/senior/92.types.html) |
| 5 | [错误](https://golang.halfiisland.com/essential/senior/95.error.html) |
| 6 | [文件](https://golang.halfiisland.com/essential/senior/100.io.html) |
| 7 | [反射](https://golang.halfiisland.com/essential/senior/105.reflect.html) |
| 8 | [并发](https://golang.halfiisland.com/essential/senior/110.concurrency.html) |
| 9 | [模块](https://golang.halfiisland.com/essential/senior/115.module.html) |
| 10 | [测试](https://golang.halfiisland.com/essential/senior/120.test.html) |
| 11 | [标准库](https://golang.halfiisland.com/essential/std/0.intro.html) |


---
### 📊 技术文章
| No. | article |
|-----|---------|
| 1 | [下载和安装Go](https://go.p2hp.com/doc/install) |
| 2 | [创建一个 Go 模块](https://go.p2hp.com/go.dev/doc/tutorial/create-module) |
| 3 | [多模块工作区入门](https://go.p2hp.com/go.dev/doc/tutorial/workspaces) |
| 4 | [使用 Go 和 Gin 开发 RESTful API](https://go.p2hp.com/go.dev/doc/tutorial/web-service-gin) |
| 5 | [泛型入门](https://go.p2hp.com/go.dev/doc/tutorial/generics) |
| 6 | [模糊测试](https://go.p2hp.com/go.dev/doc/tutorial/fuzz) |
| 7 | [编写 Web 应用程序](https://go.p2hp.com/go.dev/doc/tutorial/web-service) |
| 8 | [管理依赖项](https://go.p2hp.com/go.dev/doc/modules/managing-dependencies) |
| 9 | [访问关系数据库](https://go.p2hp.com/go.dev/doc/tutorial/database-access) |
| 10 | [编辑器插件和 IDE](https://go.p2hp.com/go.dev/doc/tutorial/editor-plugins) |
| 11 | [Go语言中使用sqlx来操作事务](https://go.p2hp.com/go.dev/doc/tutorial/sqlx-transactions) |
| 12 | [Golang学习笔记之Golang与Mysql交互](https://go.p2hp.com/go.dev/doc/tutorial/mysql-interaction) |
| 13 | [手把手带你从0搭建一个Golang ORM框架（全）！](https://go.p2hp.com/go.dev/doc/tutorial/build-orm-framework) |
| 14 | [golang源码分析（2）：Golang context 包](https://go.p2hp.com/go.dev/doc/tutorial/context-package) |
| 15 | [Golang可能会踩的58个坑](https://go.p2hp.com/go.dev/doc/tutorial/58-golang-pits) |
| 16 | [golang硬核技术（一）内存管理](https://go.p2hp.com/go.dev/doc/tutorial/memory-management) |
| 17 | [golang 定时任务处理](https://go.p2hp.com/go.dev/doc/tutorial/scheduled-tasks) |
| 18 | [golang高级进阶（一）：进程、线程、并发、并行、goroutine协程](https://go.p2hp.com/go.dev/doc/tutorial/concurrency-advanced) |
| 19 | [白话 Golang 协程池](https://go.p2hp.com/go.dev/doc/tutorial/goroutine-pool) |
| 20 | [全文图解Golang 调度器 GMP 原理与调度](https://go.p2hp.com/go.dev/doc/tutorial/gmp-scheduler) |
| 21 | [深入理解Go语言中的Channel与Select](https://go.p2hp.com/go.dev/doc/tutorial/channel-select) |
| 22 | [同步原语与锁](https://go.p2hp.com/go.dev/doc/tutorial/sync-primitives) |
| 23 | [使用Golang实现高效二分查找算法详解与实战案例](https://go.p2hp.com/go.dev/doc/tutorial/binary-search) |
| 24 | [掌握Golang项目从零到部署：全面解析持续集成与持续部署实践](https://go.p2hp.com/go.dev/doc/tutorial/ci-cd-deployment) |
| 25 | [Go语言中常见100问题](https://go.p2hp.com/go.dev/doc/tutorial/100-go-questions) |
| 26 | [Go 精妙的互斥锁设计](https://go.p2hp.com/go.dev/doc/tutorial/mutex-design) |
| 27 | [基于go语言gin框架的web项目骨架](https://go.p2hp.com/go.dev/doc/tutorial/gin-skeleton) |
| 28 | [Golang Context深入理解](https://go.p2hp.com/go.dev/doc/tutorial/context-deep-dive) |
| 29 | [打造 Go 语言最快的排序算法](https://go.p2hp.com/go.dev/doc/tutorial/fast-sorting) |
| 30 | [Go知识点：Go Module包管理器](https://go.p2hp.com/go.dev/doc/tutorial/go-modules) |
| 31 | [如何写出优雅的 Golang 代码](https://go.p2hp.com/go.dev/doc/tutorial/elegant-go-code) |
| 32 | [Go语言错误码设计与管理实践](https://go.p2hp.com/go.dev/doc/tutorial/error-codes) |
| 33 | [Golang进阶4-Go 工程化实践和配置中心](https://go.p2hp.com/go.dev/doc/tutorial/engineering-practices) |
| 34 | [Golang 任务队列策略](https://go.p2hp.com/go.dev/doc/tutorial/task-queue) |
| 35 | [golang中beego框架代理问题；及go mod使用教程](https://go.p2hp.com/go.dev/doc/tutorial/beego-proxy-go-mod) |
| 36 | [详解Go语言I/O多路复用netpoller模型](https://go.p2hp.com/go.dev/doc/tutorial/netpoller) |
| 37 | [Golang socket数据结构](https://go.p2hp.com/go.dev/doc/tutorial/socket-structures) |
| 38 | [Golang gRPC微服务](https://go.p2hp.com/go.dev/doc/tutorial/grpc-microservices) |
| 39 | [golang slice扩容原理](https://go.p2hp.com/go.dev/doc/tutorial/slice-resizing) |
| 40 | [Go 服务端开发总结](https://go.p2hp.com/go.dev/doc/tutorial/server-summary) |
| 41 | [Go 语言标准库 text/template 包深入浅出](https://go.p2hp.com/go.dev/doc/tutorial/text-template) |
| 42 | [你不知道的 Golang 打包配置文件](https://go.p2hp.com/go.dev/doc/tutorial/packaging-configs) |
| 43 | [为什么在Go语言中要慎用interface{}](https://go.p2hp.com/go.dev/doc/tutorial/caution-interface) |
| 44 | [用Go语言实现23种设计模式](https://go.p2hp.com/go.dev/doc/tutorial/design-patterns) |
| 45 | [编程语言错误处理机制的演变与 Go 的实践](https://go.p2hp.com/go.dev/doc/tutorial/error-handling-evolution) |
| 46 | [入门 go 语言汇编，看懂 GMP 源码](https://go.p2hp.com/go.dev/doc/tutorial/go-assembly-gmp) |
| 47 | [Golang单元测试最佳实践：避免常见陷阱](https://blog.csdn.net/2502_91590613/article/details/147156679) |
| 48 | [深入掌握Go 单元测试：从基础到进阶的完整指南](https://juejin.cn/post/7416186135917199394) |
| 49 | [Go 单元测试进阶：AI 加持下的高效实践与避坑指南](https://blog.csdn.net/DiDi_Tech/article/details/149264952) |
| 50 | [Go 单元测试完全指南（一）- 基本测试流程](https://juejin.cn/post/7366647007060918283) |
| 51 | [☁️ 2025新范式：Go-blueprint极速集成Kubernetes容器编排实战指南](https://blog.csdn.net/gitblog_00139/article/details/151644713) |
| 52 | [☁️ 从单体到Kubernetes：Go 服务如何容器化并上线？](https://juejin.cn/post/7498950758474989583) |
| 53 | [☁️ Go语言操作Kubernetes资源的深入指南](https://blog.csdn.net/perl8/article/details/151662008) |
| 54 | [☁️ 初次尝试Kubernetes + helm 部署golang应用](https://juejin.cn/post/6962441214926782477) |
| 55 | [🤖 （2025）使用langchain实现朴素与进阶RAG](https://blog.csdn.net/ngadminq/article/details/147839082) |
| 56 | [🤖 Go最新实现RAG 使用LangChain实现图检索查询(1)](https://blog.csdn.net/2401_84904900/article/details/138987501) |
| 57 | [🤖 从RAG框架到低代码自动化：LlamaIndex、LangChain 与n8n 全解析！](https://juejin.cn/post/7521696304939073587) |
| 58 | [🤖 各类模型接入LangChain的全流程实战（含演示+代码）](https://juejin.cn/post/7526792151829872690)








### 📺 学习视频
| No. | address |
| :--- | :--- |
| 1 | [8小时转职Golang工程师(如果你想低成本学习Go语言)](https://www.bilibili.com/video/BV1gf4y1r79E?spm_id_from=333.788.videopod.episodes&vd_source=836f76a8160d2eb8c8ea2397a180536d&p=2) |
| 2 | [【尚硅谷】Golang入门到实战教程丨一套精通GO语言](https://www.bilibili.com/video/BV1ME411Y71o/?spm_id_from=333.337.search-card.all.click&vd_source=836f76a8160d2eb8c8ea2397a180536d) |
| 3 | [【2025年新版】Go语言教程_Golang入门实战全套视频教程](https://www.bilibili.com/video/BV1Rm421N7Jy/?spm_id_from=333.337.search-card.all.click&vd_source=836f76a8160d2eb8c8ea2397a180536d) |
| 4 | [golang零基础入门到精通(Java程序员转行golang开发必看)](https://www.bilibili.com/video/BV1bN4y1Z7BT/?spm_id_from=333.337.search-card.all.click&vd_source=836f76a8160d2eb8c8ea2397a180536d) |

---
### 👥 面试题
[1. golang 中 make 和 new 的区别？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_1)  
[2. 数组和切片（slice）的区别是什么？（高频）](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_2)  
[3. defer 关键字的作用、执行顺序及对返回值的影响是什么？（高频）](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_3)  
[4. 字符串拼接的方式有哪些？哪种效率最高？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_4)  
[5. rune 类型的作用是什么？与 byte 的区别是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_5)  
[6. 反射（reflection）是什么？如何使用反射获取类型信息和修改变量值？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_6)  
[7. Go 语言中 struct tag 的作用是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_7)  
[8. 说说 Go 中的 init 函数，和它的执行顺序？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_8)  
[9. Go 语言中函数是值传递还是引用传递？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_9)  
[10. nil interface {} 与 nil 的区别？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_10)  
[11. 类型断言和类型转换的区别？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_11)  
[12. Go 没有传统的“异常机制”，产生 panic 后如何捕获？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_12)  
[13. Map 的底层实现、并发安全性及扩容机制是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_13)  
[14. 如何判断 Map 中是否包含某个键？如何实现有序 Map？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_14)  
[15. golang 哪些类型可以作为 map key？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_15)  
[16. golang 规范中，哪些数据类型不可以比较？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_16)  
[17. slice 的底层结构是怎样的？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_17)  
[18. slice 是怎么扩容的？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_18)  
[19. java和go语言数据结构有什么共同点？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_19)  
[20. Goroutine 是什么？与线程的区别是什么？如何创建 Goroutine？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_20)  
[21. golang 的进程、线程、协程的区别？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_21)  
[22. Channel 的作用、底层结构及线程安全性如何？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_22)  
[23. 无缓冲 Channel 和带缓冲 Channel 的区别是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_23)  
[24. GMP 调度模型的核心组件及调度流程是什么？（高频）](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_24)  
[25. 如何控制 Goroutine 的并发数量？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_25)  
[26. Golang中的sync包是用来干什么的？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_26)  
[27. Golang中的channel会造成死锁吗？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_27)  
[28. golang如何实现生产消费者模型？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_28)  
[29. go开发中，如何保证并发安全？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_29)  
[30. 讲一讲sync.map 怎么取出值？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_30)  
[31. map是并发安全的吗？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_31)  
[32. Golang 的垃圾回收（GC）机制及演进过程是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_32)  
[33. 什么是内存逃逸？哪些情况会导致内存逃逸？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_33)  
[34. Go 是如何分配内存的？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_34)  
[35. 什么是内存泄漏？Golang 中常见的内存泄漏场景及排查方式是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_35)  
[36. 性能分析有哪些方式？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_36)  
[37. 如何用context控制超时时间？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_37)  
[38. 如何使用 context 包进行 Goroutine 间的上下文管理？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_38)  
[39. 怎么实现单例模式？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_39)
[40. MySQL的引擎有了解吗？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_40)  
[41. MySQL 索引有哪些类型？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_41)  
[42. 为什么 InnoDB 用 B+树做索引？为什么不是 B 树、哈希或红黑树？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_42)  
[43. 哪些情况会导致索引失效？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_43)  
[44. 索引设计的原则是什么？（如何设计高效索引）](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_44)  
[45. 事务的 ACID 特性分别指什么？InnoDB 如何保证 ACID？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_45)  
[46. MySQL 有哪 4 种事务隔离级别？各级别能解决什么问题？InnoDB 默认隔离级别是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_46)  
[47. InnoDB 的 MVCC是如何实现的？undo log 和 read view 在其中的作用是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_47)  
[48. InnoDB 支持哪些锁？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_48)  
[49. MySQL 死锁的产生条件是什么？如何排查和避免？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_49)  
[50. 如何解读 EXPLAIN 执行计划？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_50)  
[51. 常见的 SQL 优化手段有哪些？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_51)  
[52. 为什么要分库分表？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_52)  
[53. 分库分表的常用策略？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_53)  
[54. Redis支持哪些数据结构？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_54)  
[55. Redis的持久化机制有哪些？RDB和AOF的区别是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_55)  
[56. Redis的过期键删除策略是什么？为什么采用这种策略？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_56)  
[57. Redis的内存淘汰策略有哪些？如何选择？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_57)  
[58. Redis如何实现分布式锁？有什么注意事项？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_58)  
[59. Redis主从复制的原理是什么？有什么作用？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_59)  
[60. Redis哨兵模式的工作原理是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_60)  
[61. Redis如何处理缓存穿透问题？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_61)  
[62. Redis如何处理缓存击穿问题？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_62)  
[63. Redis如何处理缓存雪崩问题？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_63)  
[64. 如何保证Redis和数据库数据一致性？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_64)  
[65. Redis为什么是单线程的？单线程为什么还能高性能？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_65)  
[66. Redis的事务机制是怎样的？有什么局限性？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_66)  
[67. Redis的发布订阅机制是什么？有什么应用场景？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_67)  
[68. Redis的Stream数据结构是什么？与List有什么区别？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_68)  
[69. Redis的Bitmap是什么？有什么应用场景？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/README.md#subject_69)  

<br>

#### Golang面试题 深度解析+面试回答模板：[Golang面试题 深度解析+面试回答模板](https://github.com/0voice/awesome_golang_learning/tree/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3)  
#### 大厂面试真题： [Golang大厂面试真题](https://github.com/0voice/awesome_golang_learning/tree/main/interview_questions/%E9%9D%A2%E8%AF%95%E7%9C%9F%E9%A2%98)  

---


## 🔨 web框架
### Gin框架
#### 一、Gin 框架简介  
Gin 是一个用 Go (Golang) 编写的高性能 HTTP Web 框架。它基于 Radix Tree 路由算法，性能接近原生 net/http，同时提供了简洁易用的 API 和灵活的中间件机制。
Gin 非常适合：
- 构建高性能的 RESTful API
- 微服务架构
- 快速开发 Web 应用
- 需要高度扩展性的项目

 **为什么选择 Gin？**  
⚡ **高性能**：基于 Radix Tree 路由，处理请求速度极快  
📦 **轻量级**：核心代码简洁，依赖少  
🔌 **中间件支持**：灵活的中间件机制，易于扩展  
📝 **JSON 自动绑定**：方便处理请求数据和返回响应  
🌐 **丰富的生态**：大量官方和社区开发的插件  
📚 **详细文档**：完善的中文和英文文档

#### 二、安装Gin
**2.1 首先需要安装Go（需要1.10+版本），然后可以使用下面的Go命令安装Gin。**
```bash
go get -u github.com/gin-gonic/gin
```

**2.2 将其导入您的代码中：**
```bash
import "github.com/gin-gonic/gin"
```
示例：
```go
package main

import "github.com/gin-gonic/gin"

func main() {
    // 创建一个默认的 Gin 引擎（带 Logger 和 Recovery 中间件）
    r := gin.Default()

    // 定义路由
    r.GET("/ping", func(c *gin.Context) {
        c.JSON(200, gin.H{
            "message": "pong",
        })
    })

    // 启动服务
    r.Run(":8080")
}
```
运行：
```bash
go run main.go
curl http://localhost:8080/ping
```
---
#### 三、核心功能
**3.1 路由**  
Gin 支持多种路由类型：
```go
// 基本路由
r.GET("/hello", func(c *gin.Context) { c.String(200, "Hello Gin") })
r.POST("/submit", submitHandler)

// 参数路由
r.GET("/user/:name", func(c *gin.Context) {
    name := c.Param("name")
    c.String(200, "Hello %s", name)
})
// 通配符路由
r.GET("/assets/*filepath", func(c *gin.Context) {
    path := c.Param("filepath")
    c.String(200, "Asset path: %s", path)
})
```
✅ 场景：适用于构建 RESTful API、版本化 API（如 /v1/user）、静态资源服务等。  
<br>
**3.2 路由分组（routes group）**   
通过 `Group` 可以将一组路由归类，方便管理中间件和路径前缀：
```go
// API 版本 1
v1 := r.Group("/v1")
v1.GET("/login", loginHandler)
v1.POST("/submit", submitHandler)

// API 版本 2
v2 := r.Group("/v2")
v2.GET("/user", getUserHandler)
v2.POST("/upload", uploadHandler)
```
✅ 场景：多版本 API 管理、后台与前台路由分离、权限控制分组等。  
<br>
**3.3 参数绑定与校验**  
Gin 支持自动将请求数据（JSON、表单、Query 参数等）绑定到结构体，并支持数据校验：
```go
type LoginRequest struct {
    Username string `json:"username" binding:"required"`
    Password string `json:"password" binding:"required,min=6"`
}

r.POST("/login", func(c *gin.Context) {
    var req LoginRequest
    if err := c.ShouldBindJSON(&req); err != nil {
        c.JSON(400, gin.H{"error": err.Error()})
        return
    }
    c.JSON(200, gin.H{"status": "login success"})
})
```
✅ 场景：API 输入验证、减少重复解析代码、提高开发效率。  
<br>
**3.4 中间件机制**    
Gin 的中间件机制非常灵活，可以在请求处理的不同阶段插入自定义逻辑：
```go
// 自定义日志中间件
func Logger() gin.HandlerFunc {
    return func(c *gin.Context) {
        t := time.Now()
        c.Next() // 调用后续处理函数
        latency := time.Since(t)
        log.Printf("method=%s path=%s latency=%s", c.Request.Method, c.Request.URL.Path, latency)
    }
}

// 应用中间件
r.Use(Logger())
```
常用内置中间件：
- gin.Logger()：请求日志记录
- gin.Recovery()：Panic 恢复并返回 500
- gin.BasicAuth()：HTTP 基本认证

✅ 场景：日志记录、权限验证、跨域处理、限流、请求耗时统计等。  
<br>
**3.5 响应渲染**  
Gin 支持多种响应格式，让你轻松返回 JSON、XML、HTML 等数据：
```go
// JSON 响应
c.JSON(200, gin.H{"message": "hello"})

// XML 响应
c.XML(200, gin.H{"message": "hello"})

// HTML 模板渲染
r.LoadHTMLGlob("templates/*")
c.HTML(200, "index.tmpl", gin.H{
    "title": "Gin Example",
})
```
✅ 场景：API 数据返回、网页渲染、前后端分离项目。  
<br>
**3.6 静态文件服务**  
轻松提供静态文件访问：
```go
// 提供整个目录
r.Static("/assets", "./assets")

// 提供单个文件
r.StaticFile("/favicon.ico", "./resources/favicon.ico")
```
✅ 场景：网站图片、CSS、JavaScript 文件、下载文件等。  
<br>
**3.7 文件上传**  
支持单文件和多文件上传：
```go
// 单文件上传
r.POST("/upload", func(c *gin.Context) {
    file, _ := c.FormFile("file")
    c.SaveUploadedFile(file, "./uploads/"+file.Filename)
    c.JSON(200, gin.H{"message": "file uploaded"})
})
```
✅ 场景：用户头像上传、附件上传、批量文件上传。  
<br>
**3.8 异步任务**    
支持在请求处理中启动异步任务，避免阻塞响应：
```go
r.GET("/long_async", func(c *gin.Context) {
    // 创建请求上下文副本
    cCp := c.Copy()
    go func() {
        time.Sleep(5 * time.Second)
        log.Println("Async task done: " + cCp.Request.URL.Path)
    }()
    c.JSON(200, gin.H{"status": "processing"})
})
```
✅ 场景：发送邮件、生成报表、日志处理等耗时操作。  
<br>
**💡 总结**  
Gin 的核心功能覆盖了 Web 开发的大部分需求，尤其是 **路由系统、中间件机制、参数绑定** 这三大特性，让开发者可以快速构建高性能、可扩展的 Web 应用。无论是轻量级 API 还是复杂的微服务，Gin 都能提供简洁而强大的工具支持。

参考资料：http://www.topgoer.cn/docs/ginkuangjia/ginkuangjia-1c50hfaag99k2

---
### Beego框架
#### 一、Beego框架简介
Beego 是 Go 语言生态中一款 全功能 Web 框架，遵循 "开箱即用" 设计理念，内置 ORM、日志、会话、缓存等核心组件，无需大量第三方依赖即可快速构建完整 Web 应用。无论是传统 MVC 项目、RESTful API 还是微服务，Beego 都能提供简洁高效的解决方案。  

GitHub 地址：https://github.com/beego/beego  
官方文档：https://beego.vip/docs/  

**为什么选择 Beego？**   
📦 **全栈集成**：内置 ORM（数据库交互）、Session（会话管理）、Cache（缓存）、Log（日志）等组件，无需额外选型    
🔧 **开发工具链**：自带 bee 命令行工具，支持代码生成、热重载、项目打包，大幅提升开发效率  
📐 **MVC 架构**：严格遵循 Model-View-Controller 设计模式，项目结构清晰，便于维护  
🌐 **多场景支持**：既支持传统 HTML 渲染的 Web 应用，也支持 RESTful API 和微服务  
👷 **内置安全特性**：自动防御 XSS、CSRF、SQL 注入等常见安全问题，降低安全开发成本  
📊 **性能监控**：内置监控面板，可实时查看请求 QPS、响应时间、内存占用等指标  

#### 二、安装Beego
**2.1 环境准备**
首先安装 Beego 框架和官方命令行工具 bee：
```bash
# 安装 Beego 核心库
go get github.com/beego/beego/v2@latest

# 安装 bee 命令行工具（用于项目创建、热重载等）
go install github.com/beego/bee/v2@latest
```

验证安装：
```bash
# 查看 bee 版本，确认安装成功
bee version
```
**2.2 创建第一个 Beego 项目**  
使用 bee 工具快速生成项目骨架：
```bash
# 创建名为 "mybeegoapp" 的项目
bee new mybeegoapp

# 进入项目目录
cd mybeegoapp

# 启动项目（默认热重载，代码修改后自动重启）
bee run
```

访问 `http://localhost:8080`，即可看到 Beego 默认欢迎页，说明项目启动成功！  

**2.3 项目目录结构**  
`bee new` 生成的项目遵循标准 MVC 结构，清晰易懂：  
```plaintext
mybeegoapp/
├── conf/          # 配置文件目录
│   └── app.conf   # 项目核心配置（端口、环境、数据库等）
├── controllers/   # 控制器目录（处理请求逻辑）
│   └── default.go # 默认控制器
├── models/        # 模型目录（数据库交互、业务逻辑）
├── routers/       # 路由配置目录（映射 URL 到控制器）
│   └── router.go  # 路由规则定义
├── static/        # 静态资源目录（CSS、JS、图片等）
│   ├── css/
│   ├── img/
│   └── js/
├── views/         # 视图目录（HTML 模板）
│   └── index.tpl  # 默认首页模板
├── main.go        # 项目入口文件
└── go.mod         # Go Modules 依赖配置
```

#### 三、核心功能
**3.1 路由配置：URL 映射到控制器**  
路由是请求的入口，Beego 支持多种路由规则，配置文件在 routers/router.go 中。
基本路由（GET/POST 等）
```go
package routers

import (
    "mybeegoapp/controllers"
    "github.com/beego/beego/v2/server/web"
)

func init() {
    // 1. 基本路由：GET 请求，URL "/hello" 映射到 DefaultController 的 Hello 方法
    web.Router("/hello", &controllers.DefaultController{}, "get:Hello")

    // 2. 多方法路由：同一 URL 支持 GET/POST，分别映射到不同方法
    web.Router("/submit", &controllers.DefaultController{}, "get:ShowForm;post:HandleSubmit")

    // 3. 带参数的路由：URL 中的 ":id" 作为参数传递给控制器
    web.Router("/user/:id", &controllers.UserController{}, "get:GetUser")
}
```
**3.2 控制器：处理请求逻辑**    
控制器负责接收请求、处理业务逻辑、返回响应，代码放在 controllers/ 目录下。  
示例：实现一个用户控制器
```go
// controllers/user.go
package controllers

import (
    "github.com/beego/beego/v2/server/web"
    "github.com/beego/beego/v2/server/web/context"
)

// UserController 定义用户相关控制器
type UserController struct {
    web.Controller // 嵌入 Beego 基础控制器，继承核心方法
}

// GetUser 处理 "/user/:id" 的 GET 请求
func (c *UserController) GetUser() {
    // 1. 获取 URL 参数（从路由 ":id" 中获取）
    userId := c.Ctx.Input.Param(":id")

    // 2. 模拟业务逻辑（如从数据库查询用户）
    userName := "Alice" // 实际项目中应从 models 层获取数据

    // 3. 返回响应：支持 HTML 模板渲染或 JSON 输出
    // 方式1：渲染 HTML 模板（模板文件在 views/user.tpl）
    c.Data["UserId"] = userId
    c.Data["UserName"] = userName
    c.TplName = "user.tpl" // 指定模板文件

    // 方式2：返回 JSON（适合 API 场景）
    // c.Data["json"] = map[string]interface{}{
    //     "code": 200,
    //     "data": map[string]string{
    //         "id":   userId,
    //         "name": userName,
    //     },
    // }
    // c.ServeJSON() // 自动设置 Content-Type 为 application/json
}

// 中间件：在控制器方法执行前拦截请求（如权限校验）
func (c *UserController) Prepare() {
    // 示例：验证用户是否登录（未登录则重定向到登录页）
    isLogin := c.GetSession("isLogin") // 从 Session 获取登录状态
    if isLogin == nil || isLogin.(bool) == false {
        c.Ctx.Redirect(302, "/login") // 重定向到登录页
    }
}
```
**3.3 模型（ORM）：数据库交互**    
Beego 内置强大的 ORM 组件，支持 MySQL、PostgreSQL、SQLite 等主流数据库，无需手写 SQL 即可完成数据操作。  

**步骤 1**：配置数据库（conf/app.conf）
```ini
# conf/app.conf
appname = mybeegoapp
httpport = 8080
runmode = dev # 开发环境（dev）/ 生产环境（prod）

# 数据库配置（MySQL 示例）
db.driver = mysql
db.user = root
db.password = your_password
db.host = 127.0.0.1
db.port = 3306
db.name = mybeego_db
```

**步骤 2**：初始化 ORM（models/init.go）
```go
// models/init.go
package models

import (
    "github.com/beego/beego/v2/client/orm"
    _ "github.com/go-sql-driver/mysql" // 导入 MySQL 驱动（_ 表示只执行 init 函数）
    "github.com/beego/beego/v2/server/web"
)

func init() {
    // 1. 读取配置文件中的数据库信息
    driver, _ := web.AppConfig.String("db.driver")
    user, _ := web.AppConfig.String("db.user")
    password, _ := web.AppConfig.String("db.password")
    host, _ := web.AppConfig.String("db.host")
    port, _ := web.AppConfig.String("db.port")
    dbName, _ := web.AppConfig.String("db.name")

    // 2. 拼接数据库连接字符串
    connStr := user + ":" + password + "@tcp(" + host + ":" + port + ")/" + dbName + "?charset=utf8mb4"

    // 3. 注册数据库驱动和连接
    orm.RegisterDriver(driver, orm.DRMySQL)
    orm.RegisterDataBase("default", driver, connStr)

    // 4. 自动创建表（开发环境使用，生产环境建议手动执行 SQL）
    orm.RunSyncdb("default", false, true)
}
```

**步骤 3**：定义模型并操作数据库
```go
// models/user.go
package models

import (
    "github.com/beego/beego/v2/client/orm"
    "time"
)

// User 定义用户模型（对应数据库中的 user 表）
type User struct {
    Id        int       `orm:"auto;pk"` // 自增主键
    Username  string    `orm:"size(50);unique"` // 用户名（唯一，长度 50）
    Password  string    `orm:"size(100)"` // 密码（建议存储哈希值）
    Email     string    `orm:"size(100);unique"` // 邮箱（唯一）
    CreatedAt time.Time `orm:"auto_now_add"` // 创建时间（自动填充当前时间）
    UpdatedAt time.Time `orm:"auto_now"` // 更新时间（自动更新为当前时间）
}

// 注册模型（让 ORM 识别）
func init() {
    orm.RegisterModel(new(User))
}

// AddUser 新增用户
func AddUser(username, password, email string) (int64, error) {
    o := orm.NewOrm()
    user := User{
        Username: username,
        Password: password, // 实际项目中应使用 bcrypt 等算法加密密码
        Email:    email,
    }
    // 插入数据，返回主键 ID 和错误
    return o.Insert(&user)
}

// GetUserByUsername 根据用户名查询用户
func GetUserByUsername(username string) (*User, error) {
    o := orm.NewOrm()
    user := &User{}
    // 根据 Username 字段查询（使用 Filter 条件）
    err := o.QueryTable("user").Filter("Username", username).One(user)
    return user, err
}
```

**3.4 视图模板：HTML 渲染**  
Beego 支持基于 Go 原生模板语法的视图渲染，模板文件放在 `views/` 目录下，支持模板继承、变量渲染、循环判断等功能。
示例 1：基础模板（views/base.tpl）
```html
<!-- views/base.tpl：基础模板，供其他页面继承 -->
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <title>{{.Title}} - MyBeegoApp</title>
    <!-- 引入静态资源（CSS/JS） -->
    <link rel="stylesheet" href="/static/css/style.css">
</head>
<body>
    <!-- 导航栏 -->
    <nav>
        <a href="/">首页</a>
        <a href="/user/{{.CurrentUser.Id}}">我的主页</a>
        <a href="/logout">退出登录</a>
    </nav>

    <!-- 内容区域（子模板填充） -->
    {{block "content" .}}{{end}}

    <!-- 页脚 -->
    <footer>
        © 2024 MyBeegoApp - Powered by Beego
    </footer>
</body>
</html>
```

示例 2：子模板（views/user.tpl）
```html
<!-- views/user.tpl：继承 base.tpl，填充 content 区域 -->
{{extend "base.tpl"}}

{{block "content" .}}
<div class="user-info">
    <h1>用户信息</h1>
    <p>用户 ID：{{.UserId}}</p>
    <p>用户名：{{.UserName}}</p>
    <p>注册时间：{{.User.CreatedAt.Format "2006-01-02 15:04:05"}}</p>
</div>
{{end}}
```
**3.5 会话管理（Session）**    
Beego 内置 Session 组件，支持内存、文件、Redis 等多种存储方式，用于保存用户登录状态、临时数据等。  

**配置 Session（conf/app.conf）**
```ini
# Session 配置
sessionon = true # 开启 Session
sessionprovider = file # 存储方式：file（文件）/ redis（Redis）/ memory（内存，开发用）
sessionproviderconfig = ./tmp/sessions # 文件存储路径（需手动创建 tmp/sessions 目录）
sessiongcmaxlifetime = 3600 # Session 有效期（秒）
```
**在控制器中使用 Session**
```go
// 登录成功后设置 Session
func (c *LoginController) HandleLogin() {
    username := c.GetString("username")
    password := c.GetString("password")

    // 验证用户名密码（实际项目中应调用 models 层方法）
    if username == "admin" && password == "123456" {
        // 设置 Session：标记用户已登录
        c.SetSession("isLogin", true)
        c.SetSession("username", username)
        // 重定向到首页
        c.Redirect(302, "/")
    } else {
        // 登录失败，返回错误信息
        c.Data["error"] = "用户名或密码错误"
        c.TplName = "login.tpl"
    }
}

// 退出登录：删除 Session
func (c *LoginController) Logout() {
    // 删除指定 Session
    c.DelSession("isLogin")
    c.DelSession("username")
    // 或清空所有 Session
    // c.DestroySession()
    // 重定向到登录页
    c.Redirect(302, "/login")
}
```
**3.6 缓存（Cache）**  
Beego 内置缓存组件，支持内存、Redis、Memcached 等存储方式，用于减轻数据库压力，提升高频访问接口的响应速度。
示例：使用缓存存储热门数据
```go

package controllers

import (
    "github.com/beego/beego/v2/client/cache"
    "github.com/beego/beego/v2/server/web"
    "time"
    _ "github.com/beego/beego/v2/client/cache/redis" // 导入 Redis 缓存驱动
)

type HotController struct {
    web.Controller
}

func (c *HotController) GetHotArticles() {
    // 1. 初始化缓存（Redis 示例）
    cacheConfig := `{"key":"mybeego_cache","conn":"127.0.0.1:6379","dbNum":"0","password":""}`
    cacheObj, err := cache.NewCache("redis", cacheConfig)
    if err != nil {
        c.Data["json"] = map[string]interface{}{"code": 500, "msg": "缓存初始化失败"}
        c.ServeJSON()
        return
    }

    // 2. 尝试从缓存获取数据
    cacheKey := "hot_articles"
    var hotArticles []map[string]interface{}
    if err := cacheObj.Get(cacheKey, &hotArticles); err == nil {
        // 缓存命中，直接返回数据
        c.Data["json"] = map[string]interface{}{"code": 200, "data": hotArticles}
        c.ServeJSON()
        return
    }

    // 3. 缓存未命中，从数据库查询数据（模拟）
    hotArticles = []map[string]interface{}{
        {"id": 1, "title": "Beego 入门教程"},
        {"id": 2, "title": "Golang 并发编程"},
    }

    // 4. 将数据存入缓存（设置有效期 10 分钟）
    cacheObj.Put(cacheKey, hotArticles, 10*time.Minute)

    // 5. 返回数据
    c.Data["json"] = map[string]interface{}{"code": 200, "data": hotArticles}
    c.ServeJSON()
}
```
#### 四、进阶实战：构建 RESTful API

Beego 非常适合构建 RESTful API，通过路由映射和 JSON 响应，可以快速实现规范的 API 服务。

**4.1 定义 API 路由（routers/router.go）**
```go
package routers

import (
    "mybeegoapp/controllers"
    "github.com/beego/beego/v2/server/web"
)

func init() {
    // API 路由分组（前缀 /api/v1）
    api := web.NewNamespace("/api/v1",
        // 用户相关 API
        web.NSNamespace("/users",
            web.Router("", &controllers.UserAPIController{}, "get:List;post:Create"), // GET /api/v1/users（列表）、POST（创建）
            web.Router("/:id", &controllers.UserAPIController{}, "get:Get;put:Update;delete:Delete"), // GET（详情）、PUT（更新）、DELETE（删除）
        ),

        // 文章相关 API
        web.NSNamespace("/articles",
            web.Router("", &controllers.ArticleAPIController{}, "get:List;post:Create"), // GET /api/v1/articles（列表）、POST（创建）
            web.Router("/:id", &controllers.ArticleAPIController{}, "get:Get;put:Update;delete:Delete"), // GET（详情）、PUT（更新）、DELETE（删除）
        ),
    )

    // 注册路由组
    web.AddNamespace(api)
}
```
**4.2 控制器实现（controllers/user_api.go 示例）**
```go
package controllers

import (
    "mybeegoapp/models"
    "github.com/beego/beego/v2/server/web"
)

// UserAPIController 处理用户相关 API 请求
type UserAPIController struct {
    web.Controller
}

// @Title List
// @Description 获取用户列表
// @Success 200 {array} models.User
// @router / [get]
func (c *UserAPIController) List() {
    users, err := models.GetAllUsers()
    if err != nil {
        c.Data["json"] = map[string]interface{}{"code": 500, "msg": err.Error()}
    } else {
        c.Data["json"] = map[string]interface{}{"code": 200, "data": users}
    }
    c.ServeJSON()
}

// @Title Create
// @Description 创建用户
// @Param   body        body    models.User true        "用户信息"
// @Success 201 {string} 成功创建
// @router / [post]
func (c *UserAPIController) Create() {
    var user models.User
    if err := c.ParseForm(&user); err != nil {
        c.Data["json"] = map[string]interface{}{"code": 400, "msg": "参数错误"}
        c.ServeJSON()
        return
    }
    _, err := models.AddUser(user.Username, user.Password, user.Email)
    if err != nil {
        c.Data["json"] = map[string]interface{}{"code": 500, "msg": err.Error()}
    } else {
        c.Data["json"] = map[string]interface{}{"code": 201, "msg": "创建成功"}
    }
    c.ServeJSON()
}

// @Title Get
// @Description 根据 ID 获取用户信息
// @Param   id      path    string true        "用户ID"
// @Success 200 {object} models.User
// @router /:id [get]
func (c *UserAPIController) Get() {
    id := c.Ctx.Input.Param(":id")
    user, err := models.GetUserById(id)
    if err != nil {
        c.Data["json"] = map[string]interface{}{"code": 404, "msg": "用户不存在"}
    } else {
        c.Data["json"] = map[string]interface{}{"code": 200, "data": user}
    }
    c.ServeJSON()
}

// @Title Update
// @Description 更新用户信息
// @Param   id      path    string true        "用户ID"
// @Param   body    body    models.User true        "用户信息"
// @Success 200 {string} 更新成功
// @router /:id [put]
func (c *UserAPIController) Update() {
    id := c.Ctx.Input.Param(":id")
    var user models.User
    if err := c.ParseForm(&user); err != nil {
        c.Data["json"] = map[string]interface{}{"code": 400, "msg": "参数错误"}
        c.ServeJSON()
        return
    }
    err := models.UpdateUser(id, &user)
    if err != nil {
        c.Data["json"] = map[string]interface{}{"code": 500, "msg": err.Error()}
    } else {
        c.Data["json"] = map[string]interface{}{"code": 200, "msg": "更新成功"}
    }
    c.ServeJSON()
}

// @Title Delete
// @Description 删除用户
// @Param   id      path    string true        "用户ID"
// @Success 200 {string} 删除成功
// @router /:id [delete]
func (c *UserAPIController) Delete() {
    id := c.Ctx.Input.Param(":id")
    err := models.DeleteUser(id)
    if err != nil {
        c.Data["json"] = map[string]interface{}{"code": 500, "msg": err.Error()}
    } else {
        c.Data["json"] = map[string]interface{}{"code": 200, "msg": "删除成功"}
    }
    c.ServeJSON()
}
```
参考资料：http://www.topgoer.cn/docs/beegozhongwenwendang/beegozhongwenwendang-1c5087bb5qpst

---
## 🎨 相关技术

### 🌐 网络基础
#### 一、为什么 Go 开发者需要网络知识  
Go 语言的强项之一就是网络编程，很多项目直接基于 TCP/UDP/HTTP 协议，比如：
- Web 后端（HTTP API）
- 微服务（gRPC、HTTP/2）
- 中间件（代理、网关、消息队列客户端）
- 分布式系统（服务发现、负载均衡）
  
如果不懂网络基础，就很难理解 Go 网络库的设计原理和运行机制，遇到问题也不知道怎么排查。

---

#### 二、Web 开发必备网络理论

**2.1 TCP/IP 四层模型**
- 网络接口层（ARP、MAC）
- 网络层（IP 地址、ICMP、路由）
- 传输层（TCP、UDP）
- 应用层（HTTP、DNS、WebSocket）
---

**2.2 核心协议详解（★★★★★ 核心）**  

 **（1）TCP 协议（Go 网络开发的 "基石"）**
| 核心特性       | 原理要点                                                                 | Go 中需注意的问题                                           |
|----------------|--------------------------------------------------------------------------|------------------------------------------------------------|
| 面向连接       | 三次握手（建立）、四次挥手（断开）                                       | 避免 "半连接"（用`net.Listen`的`Accept`自动处理）            |
| 可靠传输       | 序列号、确认应答（ACK）、重传机制                                         | 无需手动实现，Go 标准库已封装                               |
| 粘包 / 拆包    | 原因：TCP 是 "流协议"，无消息边界                                        | 需手动处理（3种方案：固定长度 / 分隔符 / 消息头 + 长度）    |
| 拥塞控制       | 慢启动→拥塞避免→快速重传→快速恢复                                        | 理解即可，Go 底层自动适配                                   |

**（2）HTTP 协议（Web/API 开发必备）**
| 核心组成       | 原理要点                                                                 | Go 中对应操作                                               |
|----------------|--------------------------------------------------------------------------|------------------------------------------------------------|
| 请求结构       | 请求行（方法 + URL + 版本）→请求头→请求体                                | `http.Request`结构体（`r.Method`/`r.URL`/`r.Body`）          |
| 响应结构       | 状态行（版本 + 状态码）→响应头→响应体                                    | `http.ResponseWriter`（`w.WriteHeader`/`w.Write`）           |
| 方法 / 状态码  | 常用方法：GET（查）、POST（增）、PUT（改）、DELETE（删）<br>常用状态码：200（成功）、404（未找到）、500（服务错） | `r.Method`判断请求类型<br>`w.WriteHeader(http.StatusOK)`设置状态码 |
| 版本差异       | HTTP 1.1（长连接）、HTTP 2（多路复用）、HTTP 3（基于 UDP）                | Go `net/http`默认支持 HTTP 1.1，需扩展库支持 HTTP 2/3       |

**（3）UDP 协议（实时场景补充）**
| 核心特性       | 原理要点                                                                 | Go 应用场景                                                 |
|----------------|--------------------------------------------------------------------------|------------------------------------------------------------|
| 无连接         | 无需握手，直接发数据包                                                   | 视频 / 语音传输、游戏同步、心跳检测                         |
| 不可靠         | 不保证送达、不保证顺序                                                   | 需上层实现重传（如 RTCP 协议）                              |
| 轻量快速       | 数据包体积小，延迟低                                                     | 高性能场景（如日志收集）                                   |


---
#### 三、相关书籍
- 《计算机网络（谢希仁）》
- 《TCP/IP 详解 卷 1：协议》
- 《HTTP 权威指南》
---
#### 四、在线资源
- [Go 标准库 net 包文档](https://pkg.go.dev/net)
- [Go 标准库 net/http 包文档](https://pkg.go.dev/net/http)
- [TopGoer 教程/网络编程](http://www.topgoer.com/%E7%BD%91%E7%BB%9C%E7%BC%96%E7%A8%8B/)
---


### 🐬 MySQL

#### 一、安装MySQL驱动    

1.1 安装 MySQL  
首先，确保你的系统中安装了 MySQL 数据库。可以从官网下载安装包进行安装，或者使用包管理器进行安装。  

1.2 安装 Go MySQL 驱动  
在 Go 中，最常用的 MySQL 驱动是 go-sql-driver/mysql。在终端运行以下命令进行安装：
```bash
go get -u github.com/go-sql-driver/mysql
```
1.3 配置数据库连接信息  
在开始编码之前，需要在 MySQL 中创建一个新的数据库和用户，并授予相应的权限。同时，记录下数据库的主机名、端口号、用户名和密码，这些信息将在后续的代码中用于建立连接。

---

#### 二、连接MySQL  

在 Go 中，使用 database/sql 包来管理数据库连接。以下是一个简单的示例，展示如何建立连接：

```go
import (
    "database/sql"
    _ "github.com/go-sql-driver/mysql"
)

dsn := "user:password@tcp(127.0.0.1:3306)/dbname?charset=utf8mb4&parseTime=true&loc=Local"
db, err := sql.Open("mysql", dsn)
if err != nil {
    panic(err)
}
defer db.Close()

// 验证连接
err = db.Ping()
if err != nil {
    panic(err)
}
```
---
#### 三、增删改查

一旦连接建立，就可以执行 SQL了： 

3.1 创建表：  
```go
_, err := db.Exec(`
CREATE TABLE IF NOT EXISTS users (
    id BIGINT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50) NOT NULL,
    age INT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
`)
```
3.2 插入数据：
```go
res, err := db.Exec("INSERT INTO users(name, age) VALUES (?, ?)", "Alice", 20)
lastID, _ := res.LastInsertId()  // 获取插入ID
```
3.3 查询数据：
```go
rows, err := db.Query("SELECT id, name, age FROM users WHERE age > ?", 18)
defer rows.Close()

for rows.Next() {
    var id int64
    var name string
    var age int
    rows.Scan(&id, &name, &age)
    fmt.Printf("ID: %d, Name: %s, Age: %d\n", id, name, age)
}
```
3.4 删除数据：
```go
res, err := db.Exec("DELETE FROM users WHERE name=?", "Alice")
rowsAffected, _ := res.RowsAffected()
```
---
#### 四、事务处理

在处理涉及多个数据库操作的业务逻辑时，事务是保证数据一致性的关键。以下是一个简单的事务处理示例：  

```go
tx, err := db.Begin()
if err != nil {
    panic(err)
}

_, err = tx.Exec("INSERT INTO users(name, age) VALUES (?, ?)", "Bob", 25)
if err != nil {
    tx.Rollback()
    panic(err)
}

err = tx.Commit()
if err != nil {
    panic(err)
}
```
---
#### 五、连接池的使用

5.1 连接池的重要性：  
在高并发的场景下，建立和关闭数据库连接的开销是非常大的。使用连接池可以复用数据库连接，提高性能。  

5.2 连接池配置：
```go
db.SetMaxOpenConns(100)           // 最大打开连接数
db.SetMaxIdleConns(20)            // 最大空闲连接数
db.SetConnMaxLifetime(time.Hour)  // 连接最大存活时间
db.SetConnMaxIdleTime(30*time.Minute) // 连接最大空闲时间
```
---

### GORM的使用   
作为 Go 语言中最受欢迎的对象关系映射（ORM）库，GORM 提供了一套简洁且功能强大的 API，极大地简化了数据库操作。  

#### 一、GORM 简介
GORM 是用 Go 语言编写的 ORM 库，它基于 httprouter 和 Go 标准库构建。其主要特点包括：  
- 简洁易用：通过定义结构体来映射数据库表，简化数据操作；
- 功能全面：支持 CRUD、事务、预加载、关联关系、自动迁移等常见功能；
- 扩展性强：内置钩子函数、插件机制以及对多种数据库（MySQL、PostgreSQL、SQLite、SQL Server 等）的支持；
- 性能优秀：经过大量优化，能够在高并发场景下保持稳定性能。

参考:[GORM官方文档](https://gorm.io/zh_CN/docs/index.html)  

---
#### 二、环境搭建与安装
在使用 GORM 之前，首先需要安装 Go 环境，然后通过 ```go get``` 命令安装 GORM 及所需数据库驱动。例如，如果你使用 MySQL 数据库，在终端运行以下命令安装：

```bash
# 安装 MySQL 驱动
go get -u gorm.io/driver/mysql

# 安装 GORM 框架
go get -u gorm.io/gorm
```
##### ⚠️ ```gorm.io/driver/mysql``` 是 GORM v2 推荐的 MySQL 驱动，支持 database/sql 接口。  


安装完成后，在项目代码中导入相关包：
```go
import (
    "gorm.io/gorm"
    "gorm.io/driver/mysql"
)
```
---
#### 三、连接数据库

GORM 通过 ```gorm.Open()``` 来创建数据库连接。我们需要提供 DSN（Data Source Name） 告诉 GORM 如何连接 MySQL。
```go
package main

import (
  "gorm.io/driver/mysql"
  "gorm.io/gorm"
)

func main() {
  // DSN 格式：user:password@tcp(IP:端口)/数据库名?参数
  dsn := "root:123456@tcp(127.0.0.1:3306)/testdb?charset=utf8mb4&parseTime=True&loc=Local"
  
  // 打开数据库连接
  db, err := gorm.Open(mysql.Open(dsn), &gorm.Config{})
  if err != nil {
    panic("failed to connect database")
  }

  // 配置连接池
  sqlDB, _ := db.DB()
  sqlDB.SetMaxOpenConns(100) // 最大打开连接数
  sqlDB.SetMaxIdleConns(20)  // 最大空闲连接数
  sqlDB.SetConnMaxLifetime(time.Hour) // 连接最大存活时间
}
```
---

#### 四、模型定义（Model） 
在 GORM 中，模型就是一个 Go 结构体，每个字段对应数据库表的一列。
```go
type User struct {
  gorm.Model           // 内置字段：ID, CreatedAt, UpdatedAt, DeletedAt
  Name       string
  Age        int
  Email      string `gorm:"unique"` // Email 唯一
  Password   string
}
```
```gorm.Model``` 是 GORM 提供的基础模型结构体，帮你自动添加：
- ID：主键
- CreatedAt：创建时间
- UpdatedAt：更新时间
- DeletedAt：删除时间（用于软删除）
---
#### 五、数据库迁移（Auto Migration）  
GORM 提供 ```AutoMigrate()``` 方法，可以根据模型自动创建或更新数据库表结构。  
```go
// 自动迁移
db.AutoMigrate(&User{})
```
特点：  
- 只会新增字段和索引，不会删除已有字段或索引
- 非常适合在开发阶段快速同步表结构
---
#### 六、CRUD 操作   
6.1 创建（Create）
使用 ```db.Create() ```插入一条记录到数据库。
```go
user := User{Name: "Alice", Age: 20, Email: "alice@example.com", Password: "123456"}
result := db.Create(&user)

fmt.Println(user.ID)             // 插入后ID会自动回填
fmt.Println(result.Error)        // 错误信息
fmt.Println(result.RowsAffected) // 影响行数
```
6.2 查询（Read）
GORM 提供了多种查询方法，最常用的是：
- ```First()```：查询第一条记录
- ```Find()```：查询多条记录
- ```Where()```：添加条件
```go
var user User
// 根据主键查询
db.First(&user, 1) // 查询 ID=1 的用户
fmt.Printf("%+v\n", user)

// 条件查询
var users []User
db.Where("age > ?", 18).Find(&users)

// 模糊查询
db.Where("name LIKE ?", "%li%").Find(&users)

// 排序
db.Order("age desc").Find(&users)
```
6.3 更新（Update）
GORM 提供```Update()（单字段```）和```Updates()（多字段）```两种方法。
```go
// 更新单个字段
db.Model(&User{ID: 1}).Update("Age", 21)

// 更新多个字段
db.Model(&User{ID: 1}).Updates(User{Name: "Alice Updated", Age: 22})

// 更新选定字段（忽略零值）
db.Model(&User{ID: 1}).Select("Name").Updates(User{Name: "Alice Selected", Age: 0})
```
6.4 删除（Delete）
默认是软删除（更新 ```DeletedAt``` 字段），不会真正删除数据。
```go
// 软删除
db.Delete(&User{}, 1)

// 物理删除（真正删除数据）
db.Unscoped().Delete(&User{}, 1)
```
---
#### 七、事务处理
GORM 支持数据库事务，可以保证一系列操作的原子性。  
```go
tx := db.Begin()
if tx.Error != nil {
  panic(tx.Error)
}

if err := tx.Create(&User{Name: "Bob", Age: 25}).Error; err != nil {
  tx.Rollback()
  panic(err)
}

if err := tx.Create(&User{Name: "Charlie", Age: 30}).Error; err != nil {
  tx.Rollback()
  panic(err)
}

tx.Commit()
```
---
#### 八、关联关系
GORM 支持常见的关联关系：
- Has One（一对一）
- Has Many（一对多）
- Belongs To（属于）
- Many To Many（多对多）
一对多示例：
```go
type User struct {
  gorm.Model
  Name  string
  Posts []Post // 一个用户有多篇文章
}

type Post struct {
  gorm.Model
  Title  string
  UserID uint // 外键
}

// 创建用户和文章
db.Create(&User{
  Name: "Alice",
  Posts: []Post{
    {Title: "Post 1"},
    {Title: "Post 2"},
  },
})

// 查询时预加载关联
var user User
db.Preload("Posts").First(&user, 1)
```
---
#### 九、钩子函数（Hooks）  
Hooks 是在创建、更新、删除等操作前后自动调用的函数，方便你在数据变更时做额外逻辑（如数据校验、密码加密）。
```go
func (u *User) BeforeCreate(tx *gorm.DB) error {
  fmt.Println("Before Create")
  return nil
}

func (u *User) AfterCreate(tx *gorm.DB) error {
  fmt.Println("After Create")
  return nil
}
```
---
#### 十、常见问题与最佳实践
10.1 字段标签（Tags）  
```go
type User struct {
  gorm.Model
  Email string `gorm:"unique;not null"`
  Age   int    `gorm:"default:18"`
}
```
10.2 零值问题  
- 默认 GORM 会忽略零值字段更新
- 解决方法：db.Model(...).Select("字段名").Updates(...)

10.3 软删除  
- 带 gorm.DeletedAt 字段的模型默认启用软删除
- 使用 Unscoped() 查询所有记录（包括已删除的）
  
10.4 性能优化  
- 批量插入：db.CreateInBatches(users, 100)
- 避免 N+1 查询：对于复杂关联查询，预加载（Preload）可以减少 N+1 查询问题，但在数据量较大时要注意性能
  
10.5 批量操作  
- 尽可能使用批量插入和更新，减少数据库连接次数；

#### 十一、实战案例
下面是一个简单的示例，展示如何使用 GORM 完成一个用户的 CRUD 操作，并处理一对多关联关系：
```go
package main

import (
    "fmt"
    "log"
    "time"

    "gorm.io/driver/mysql"
    "gorm.io/gorm"
)

type User struct {
    ID        uint      `gorm:"primaryKey"`
    Name      string    `gorm:"size:100;not null"`
    Age       int       `gorm:"not null"`
    Email     string    `gorm:"unique;not null"`
    Orders    []Order   // 一对多关联关系
    CreatedAt time.Time
}

type Order struct {
    ID     uint   `gorm:"primaryKey"`
    Item   string `gorm:"not null"`
    UserID uint
}

func main() {
    dsn := "username:password@tcp(127.0.0.1:3306)/dbname?charset=utf8mb4&parseTime=True&loc=Local"
    db, err := gorm.Open(mysql.Open(dsn), &gorm.Config{})
    if err != nil {
        log.Fatal("连接数据库失败：", err)
    }

    // 自动迁移，确保数据库表结构和模型同步
    db.AutoMigrate(&User{}, &Order{})

    // 创建用户及关联订单
    user := User{
        Name:  "Alice",
        Age:   28,
        Email: "alice@example.com",
        Orders: []Order{
            {Item: "Laptop"},
            {Item: "Smartphone"},
        },
    }
    db.Create(&user)

    // 查询用户及其订单
    var u User
    db.Preload("Orders").First(&u, user.ID)
    fmt.Printf("用户：%v\n订单：%v\n", u, u.Orders)

    // 更新用户数据
    db.Model(&u).Update("Age", 29)

    // 删除用户记录（级联删除订单需要手动处理或设置外键约束）
    db.Delete(&u)
}
```
在上述示例中，我们通过自动迁移确保数据库表结构与模型保持一致，并实现了用户和订单的创建、查询、更新和删除操作。通过 Preload 方法，我们还演示了如何加载关联数据。

---

### 💾 Redis

#### 一、简介
Redis 是一个开源的高性能键值数据库，支持多种数据结构，广泛用于缓存、消息队列、排行榜等场景。Go-Redis（github.com/redis/go-redis）是 Go 语言中最流行的 Redis 客户端之一，支持：  
- 单机、哨兵（Sentinel）、集群（Cluster）模式
- 连接池管理
- 发布 / 订阅
- 事务与管道（Pipeline）
- Lua 脚本
- 分布式锁

本教程基于 go-redis v9，它是目前的稳定版本，API 简洁且类型安全。

#### 二、安装
go-redis 支持最新的两个 Go 版本。您只能在 Go 模块中使用它，因此您必须在开始之前初始化一个 Go 模块，或者将您的代码添加到现有模块中。
```bash
go mod init github.com/my/repo
```

使用 go get 命令安装 go-redis/v9
```bash
go get github.com/redis/go-redis/v9
```

#### 三、连接Redis
3.1 以下示例展示了连接到 Redis 服务器的最简单方法:
```go
import (
	"context"
	"fmt"
	"github.com/redis/go-redis/v9"
)

func main() {    
    client := redis.NewClient(&redis.Options{
        Addr:	  "localhost:6379",
        Password: "", // No password set
        DB:		  0,  // Use default DB
        Protocol: 2,  // Connection protocol
    })
}
```

也可以使用连接字符串进行连接:
```go
opt, err := redis.ParseURL("redis://<user>:<pass>@localhost:6379/<db>")
if err != nil {
	panic(err)
}
client := redis.NewClient(opt)
```

连接后，可以通过存储和检索一个简单的字符串来测试连接:
```go
ctx := context.Background()

err := client.Set(ctx, "foo", "bar", 0).Err()
if err != nil {
    panic(err)
}

val, err := client.Get(ctx, "foo").Result()
if err != nil {
    panic(err)
}
fmt.Println("foo", val)
```

**3.2 哨兵模式**    
要连接到由 Redis Sentinel 管理的 Redis 服务器
```go
import "github.com/redis/go-redis/v9"

rdb := redis.NewFailoverClient(&redis.FailoverOptions{
    MasterName:    "mymaster",
    SentinelAddrs: []string{"127.0.0.1:26379", "127.0.0.1:26380"},
})
```
要连接到 Redis Sentinel 本身
```go
import "github.com/redis/go-redis/v9"

sentinel := redis.NewSentinelClient(&redis.Options{
    Addr: ":9126",
})

addr, err := sentinel.GetMasterAddrByName(ctx, "master-name").Result()
```
**3.3 集群模式**      
要连接到 Redis 集群，请使用 `NewClusterClient()`。可以使用 Addrs 选项指定一个或多个集群端点
```go
rdb := redis.NewClusterClient(&redis.ClusterOptions{
    Addrs: []string{
        "127.0.0.1:7000",
        "127.0.0.1:7001",
        "127.0.0.1:7002",
    },
})
```
**3.4 使用 TLS 连接生产环境 Redis**
```go
// Load client cert
cert, err := tls.LoadX509KeyPair("redis_user.crt", "redis_user_private.key")
if err != nil {
    log.Fatal(err)
}

// Load CA cert
caCert, err := os.ReadFile("redis_ca.pem")
if err != nil {
    log.Fatal(err)
}
caCertPool := x509.NewCertPool()
caCertPool.AppendCertsFromPEM(caCert)

client := redis.NewClient(&redis.Options{
    Addr:     "my-redis.cloud.redislabs.com:6379",
    Username: "default", // use your Redis user. More info https://redis.ac.cn/docs/latest/operate/oss_and_stack/management/security/acl/
    Password: "secret", // use your Redis password
    TLSConfig: &tls.Config{
        MinVersion:   tls.VersionTLS12,
        Certificates: []tls.Certificate{cert},
        RootCAs:      caCertPool,
    },
})

//send SET command
err = client.Set(ctx, "foo", "bar", 0).Err()
if err != nil {
    panic(err)
}

//send GET command and print the value
val, err := client.Get(ctx, "foo").Result()
if err != nil {
    panic(err)
}
fmt.Println("foo", val)
```
---
#### 四、 核心数据类型操作
**4.1 String**
```go
// 设置值
err := rdb.Set(ctx, "name", "Alice", 0).Err()

// 获取值
val, _ := rdb.Get(ctx, "name").Result()

// 自增
count, _ := rdb.Incr(ctx, "counter").Result()
```

**4.2 Hash**
```go
// 设置字段
err := rdb.HSet(ctx, "user:1", "name", "Alice", "age", 20).Err()

// 获取字段
name, _ := rdb.HGet(ctx, "user:1", "name").Result()

// 获取所有字段
user, _ := rdb.HGetAll(ctx, "user:1").Result()
```

**4.3 List**
```go
// 左侧添加
err := rdb.LPush(ctx, "queue", "task1", "task2").Err()

// 右侧弹出
task, _ := rdb.RPop(ctx, "queue").Result()

// 获取范围
elements, _ := rdb.LRange(ctx, "queue", 0, -1).Result()
```

**4.4 Set**
```go
// 添加元素
err := rdb.SAdd(ctx, "tags", "go", "redis").Err()

// 获取所有元素
tags, _ := rdb.SMembers(ctx, "tags").Result()

// 判断元素是否存在
exists, _ := rdb.SIsMember(ctx, "tags", "go").Result()
```

**4.5 Sorted Set**
```go
// 添加元素
err := rdb.ZAdd(ctx, "rank", redis.Z{Score: 90, Member: "Alice"}).Err()

// 获取排名
members, _ := rdb.ZRange(ctx, "rank", 0, -1).WithScores().Result()
```
---
#### 五. 高级功能
**5.1 管道（Pipeline）**
```go
pipe := rdb.Pipeline()
pipe.Incr(ctx, "counter1")
pipe.Incr(ctx, "counter2")
_, err := pipe.Exec(ctx)
```
**5.2 事务**
```go
tx := rdb.Multi()
tx.Incr(ctx, "counter1")
tx.Incr(ctx, "counter2")
_, err := tx.Exec(ctx)
```
**5.3 发布 / 订阅**
```go
// 发布
err := rdb.Publish(ctx, "channel1", "hello").Err()

// 订阅
pubsub := rdb.Subscribe(ctx, "channel1")
ch := pubsub.Channel()
for msg := range ch {
    fmt.Println(msg.Channel, msg.Payload)
}
```
**5.4 分布式锁**
```go
lock := redis.NewLock(rdb, "lock_key")
err := lock.Acquire(ctx)
defer lock.Release(ctx)
```
---

#### 六、 实战案例
**6.1 缓存示例**
```go
func GetUser(ctx context.Context, rdb *redis.Client, id string) (User, error) {
    // 先查缓存
    data, err := rdb.Get(ctx, "user:"+id).Result()
    if err == nil {
        var user User
        json.Unmarshal([]byte(data), &user)
        return user, nil
    }

    // 缓存未命中，查数据库
    user := queryUserFromDB(id)
    
    // 写入缓存
    jsonData, _ := json.Marshal(user)
    rdb.SetEx(ctx, "user:"+id, jsonData, 10*time.Minute)
    
    return user, nil
}
```
**6.2 排行榜**
```go
// 添加成绩
rdb.ZAdd(ctx, "rank", redis.Z{Score: 95, Member: "Alice"})
rdb.ZAdd(ctx, "rank", redis.Z{Score: 88, Member: "Bob"})

// 获取前三名
result, _ := rdb.ZRevRangeWithScores(ctx, "rank", 0, 2).Result()
for _, z := range result {
    fmt.Printf("%s: %.0f\n", z.Member, z.Score)
}
```
参考资料：https://redis.ac.cn/docs/latest/develop/clients/go/transpipe/
https://redis.golang.ac.cn/guide/ring.html

---

## 💻 项目实战

| 难度 | 项目地址 | 前置知识 | 学习目标 | 项目描述 | 适合阶段 |
|------|----------|----------|----------|----------|----------|
| ⭐ | [go-by-example](https://github.com/mmcgrana/gobyexample) | - Go 基础语法<br>- HTTP 客户端<br>- 并发编程（goroutine/channel） | - 掌握 Go 语法的实际应用<br>- 学会调用第三方 API<br>- 理解并发任务处理<br>- 了解网络代理服务器原理 | 提供大量 Go 语言的示例代码，从基础到进阶覆盖语法、并发、网络等多个方面，适合边学边练。 | 入门 |
| ⭐⭐ | [golang-gin-realworld-example-app](https://github.com/gothinkster/golang-gin-realworld-example-app) | - Go 基础语法<br>- Gin 框架<br>- RESTful API 设计<br>- JWT 认证 | - 掌握 RESTful API 开发规范<br>- 学会用 Gin 实现完整的 CRUD<br>- 理解 JWT 认证流程<br>- 熟悉 Swagger API 文档生成 | 基于 Gin 框架实现的 RealWorld 示例项目，包含用户管理、文章发布等功能，完全符合生产级 API 标准。 | 进阶 |
| ⭐⭐ | [go-backend-clean-architecture](https://github.com/bxcodec/go-clean-arch) | - Go 基础语法<br>- HTTP 服务开发<br>- 分层架构概念 | - 理解整洁架构（Clean Architecture）<br>- 掌握 Go 项目的合理目录结构<br>- 学会依赖注入<br>- 提升代码可维护性与可测试性 | 演示如何用 Go 实现整洁架构，代码分层清晰，易于测试和维护，适合想提升架构能力的开发者。 | 进阶 |
| ⭐⭐⭐ | [miniblog](https://github.com/EDDYCJY/go-gin-example) | - Go 基础语法<br>- Gin 框架<br>- GORM<br>- JWT / Casbin 基础 | - 掌握分层架构设计（API / Service / DAO）<br>- 学会 JWT 认证与 Casbin 权限控制<br>- 理解单元测试与性能测试<br>- 熟悉 Go 项目工程化实践 | 一个功能完备的博客系统，包含文章管理、用户认证、权限控制等模块，项目结构清晰，适合学习工程化开发。 | 进阶 |
| ⭐⭐⭐ | [rpcx](https://github.com/rcrowley/go-metrics) | - Go 基础语法<br>- 网络编程基础（TCP/UDP）<br>- 服务发现概念 | - 理解 RPC 原理及与 HTTP 的区别<br>- 掌握 rpcx 框架的使用<br>- 学会服务注册与发现（etcd/consul/zookeeper）<br>- 了解分布式系统基础 | 高性能的 Go RPC 框架，支持多种序列化协议和服务发现方式，适合构建分布式系统和微服务。 | 进阶 |
| ⭐⭐⭐⭐ | [Ferry](https://github.com/lanyulei/ferry) | - Go 基础语法<br>- Gin 框架<br>- Vue.js 基础<br>- MySQL / Redis 基础 | - 掌握前后端分离工单系统开发<br>- 学会流程引擎设计<br>- 理解权限管理与任务调度<br>- 提升复杂业务逻辑实现能力 | 企业级工单系统，支持流程定义、任务分配、权限控制等功能，前后端分离架构，适合学习复杂业务开发。 | 高级 |
| ⭐⭐⭐⭐ | [go-kit](https://github.com/go-kit/kit) | - Go 基础语法<br>- 微服务概念<br>- HTTP / RPC 基础 | - 掌握 go-kit 微服务框架<br>- 学会使用中间件扩展服务功能<br>- 了解服务注册与发现<br>- 掌握可观测性（日志、监控、追踪） | 一套用于构建微服务的 Go 开发工具集，提供了服务发现、负载均衡、监控等组件，适合构建高可用微服务。 | 高级 |
| ⭐⭐⭐⭐⭐ | [IAM](https://github.com/marmotedu/iam) | - Go 基础语法<br>- 微服务架构<br>- MySQL / Redis<br>- OAuth2.0 / JWT | - 掌握企业级身份认证系统设计<br>- 学会权限管理与访问控制<br>- 理解微服务间通信<br>- 熟悉 Go 在大型项目中的工程化实践 | 企业级身份认证与授权系统，支持多租户、细粒度权限控制，基于微服务架构实现，适合学习大型系统设计。 | 高级 |
| ⭐⭐⭐⭐⭐ | [Gin-vue-admin](https://github.com/flipped-aurora/gin-vue-admin) | - Go 基础语法<br>- Gin 框架<br>- Vue.js 基础<br>- MySQL 基础<br>- JWT 认证原理 | - 掌握前后端分离开发流程<br>- 学会使用 Gin 构建 RESTful API<br>- 理解 JWT 鉴权与动态路由<br>- 掌握 Casbin 权限控制<br>- 熟悉代码生成器与项目脚手架使用 | 一套完整的前后端分离权限管理系统，内置代码生成器、动态路由、RBAC 权限控制等功能，适合作为企业级项目脚手架。 | 高级 |
| 🆕 ⭐⭐⭐ | [marcoshuck/todo](https://github.com/marcoshuck/todo) | - gRPC + Docker基础<br>- 微服务概念 | - 打包Go服务，K8s orchestration<br>- 监控用Prometheus<br>- 部署上阿里云/腾讯云 | A production-grade todo app applying Go, gRPC, Docker, Kubernetes, Zap, Jaeger, Prometheus, Grafana and more. 教你从单体到云微服务全流程。 | 高级（云原生） |
| 🆕 ⭐⭐⭐⭐ | [build-on-aws/rag-golang-postgresql-langchain](https://github.com/build-on-aws/rag-golang-postgresql-langchain) | - OpenAI API + 向量DB (PostgreSQL)<br>- LangChain-Go基础 | - 实现RAG管道，提升LLM准确性<br>- 用LangChain-Go集成PostgreSQL向量搜索<br>- 建简单聊天bot，扩展多代理 | How to use Retrieval Augmented Generation (RAG) for Go applications. Implement RAG (using LangChain and PostgreSQL) to improve the accuracy and relevance of LLM responses. 适合AI转Go开发者。 | 高级（AI分支） |
