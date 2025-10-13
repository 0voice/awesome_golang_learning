# 📖 Go语言面试题深度解析
💡 本文档整理 Go 语言高频面试题及深度解析，以 “答案框架 + 原理拆解 + 实战避坑” 形式，帮你既会答题、更懂背后逻辑，适用于备考与学习。

<br>

### 📌 目录
[Map 的底层实现、并发安全性及扩容机制是什么？](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Map%20%E7%9A%84%E5%BA%95%E5%B1%82%E5%AE%9E%E7%8E%B0%E3%80%81%E5%B9%B6%E5%8F%91%E5%AE%89%E5%85%A8%E6%80%A7%E5%8F%8A%E6%89%A9%E5%AE%B9%E6%9C%BA%E5%88%B6%E6%98%AF%E4%BB%80%E4%B9%88%EF%BC%9F.md)  
[进程、线程、协程的区别](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Go%E8%AF%AD%E8%A8%80%E4%B8%AD%E7%9A%84%E8%BF%9B%E7%A8%8B%E3%80%81%E7%BA%BF%E7%A8%8B%E3%80%81%E5%8D%8F%E7%A8%8B%E7%9A%84%E5%8C%BA%E5%88%AB.md)  
[Go 字符串拼接的 4 种方式、底层原理及场景选择](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Go%20%E5%AD%97%E7%AC%A6%E4%B8%B2%E6%8B%BC%E6%8E%A5%E7%9A%84%204%20%E7%A7%8D%E6%96%B9%E5%BC%8F%E3%80%81%E5%BA%95%E5%B1%82%E5%8E%9F%E7%90%86%E5%8F%8A%E5%9C%BA%E6%99%AF%E9%80%89%E6%8B%A9.md)  
[GMP 调度模型](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Go%20%E8%AF%AD%E8%A8%80%20GMP%20%E8%B0%83%E5%BA%A6%E6%A8%A1%E5%9E%8B.md)  
[defer 的执行机制](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Go%20%E4%B8%AD%20defer%20%E7%9A%84%E6%89%A7%E8%A1%8C%E6%9C%BA%E5%88%B6.md)  
[GC 垃圾回收机制](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Go%20%E8%AF%AD%E8%A8%80%20GC%20%E5%9E%83%E5%9C%BE%E5%9B%9E%E6%94%B6%E6%9C%BA%E5%88%B6.md)  
[Go语言中的channel](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Go%20%E8%AF%AD%E8%A8%80%E4%B8%AD%E7%9A%84Channel%20.md)
[Go 切片（slice）的底层结构](https://github.com/0voice/awesome_golang_learning/blob/main/interview_questions/%E9%9D%A2%E8%AF%95%E9%A2%98%E8%AF%A6%E8%A7%A3/Go%20%E5%88%87%E7%89%87%EF%BC%88slice%EF%BC%89%E7%9A%84%E5%BA%95%E5%B1%82%E7%BB%93%E6%9E%84.md)  
