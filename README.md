# Go-Programming-Notes

## Introduction

This repo records the daily programming nodes in Golang.

### Why Golang?

Golang是一种非常适合分布式系统/数据库(Distributed System/database)，区块链(Blockchain)项目开发的编程语言。

- **语法简单**。它学习曲线平滑。有其他高级语言编程经验的人，可以快速上手。
- **高并发基因**。它对高并发，分布式程序有更加灵活简洁的标准库支持。不需要依赖第三方库就可以快速构建后端/网络/高并发应用。
- **跨平台**。它支持跨系统交叉编译。MacOS/Win 也可以编译Linux下可以运行的程序，不需要担心环境依赖的问题。
- **新**。相对于C/C++，Golang的设计理念更新，历史包袱更少，对各种数据结构/文件比如JSON, CSV支持简洁流畅。
- **快**。它相比C++编译快，相比Python运行快。

所以Golang非常适合做一些分布式，区块链领域的学术/工程项目的原型(Prototype)开发工作。

### 不足

- **轮子少**。相比于Java生态系统中充足的轮子，Go社区中的轮子的发展还属于初级阶段。
- **代码冗余**。相比于C++，Golang对范型(Generic Programming)支持较差。对同一份逻辑，不同的数据结构需要重复的代码。

## General Tips

- 保持包名和目录名的一致。
- 包名尽量简短，应该为小写单词，不要使用下划线或者驼峰式命名。
- 文件名为小写单词，使用下划线分割。
- Go语言区分大小写，小写字母开头的单词为包内访问，相当于Java/C++中的Private。跨包使用的成员变量/函数要使用大写字母开头。
- 变量和结构体的命名使用驼峰式。
- 通过更改首字母的大小写，来控制结构体的使用场景。
- 常量通常使用全部大写字母。
- Go结构体默认的小写字母开头的变量不是public的不能跨包访问。
- 通过go run *.go || go build .的方式来运行多文件同package调度的go程序
- Go语言中包括数组和Slice两种集合型数据结构。
- Go语言中的数据大小是固定的。
- Go语言中中Slice(切片)的大小可以是动态的。
- Go语言中，可以定义一个不指明长度的切片。
- 二维切片需要初始化:

```go
    //2-D Slice init
    // 初始化一个n行m列的切片
    var K[][] int.
    for i := 0; i <=n; i++ {
        inline := make([]int, m)
        K := append(K, inline)
    }
```

- Go 自带了解析CSV的库 “encoding/csv”
- Go Interface 是一种type
- 要实现Interface 必须实现interface中所有的方法
- 使用runtime Package中的 MemStats 和 ReadMemStats 来测量当前程序中Memory的使用状况。
- Context 是 Go 1.7 之后新引入的标准库接口。
- sync/atomic标准库包中提供的原子操作，通常是无锁的。
- Function Types: A function type denotes the set of all functions with the same parameter and result types.


## FQA

- What is struct{} and struct{}{} ?
  - struct{} 表示一个零元素的struct结构。通常会被用在没有任何信息被存储的场景中。
  - struct{}{} 表示一个存储了struct{}的Composite literal.
  - Source: [Stackoverflow](https://stackoverflow.com/questions/45122905/how-do-struct-and-struct-work-in-go)

## Go Unit Testing

- Go 单元测试中，执行到t.Error()/ t.Errorf() 测试函数会输出错误的log信息并继续执行。
- Go 单元测试中，执行到t.Fatal()/ t.Fatalf() 测试函数会输出错误的log信息并结束测试。
- Go 单元测试中，如果不满足断言assert.Equal() 测试函数会结束并报错。

## Go and C and Python

- Python 可以调用Go编译的动态链接库 and.so (Shared Object)
- Go编译成so文件时，需要在函数上一行添加//export xxx(函数名).
  - 注意//与export中间不能有空格
  - Example 位于example/pygo

## Log

- Log.Fatal会直接退出程序，不会执行defer相关的函数

## Reference

- Go语言高性能编程[link](https://geektutu.com/post/high-performance-go.html)
- Go By Example[link](https://gobyexample.com/)