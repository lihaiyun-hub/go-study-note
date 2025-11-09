# Golang 基础学习笔记

## 一、Go语言简介
Go语言（Golang）是由Google在2009年推出的开源编程语言，拥有高性能、简洁语法和强大的并发支持。它结合了C语言的高效与Python的易用，广泛用于后端开发、云计算、分布式系统和微服务。

**Go语言特点：**
- 编译型语言，执行速度快
- 内置并发支持（goroutine、channel）
- 强类型、静态类型
- 自带垃圾回收（GC）
- 简洁的语法与强大的标准库

---

## 二、环境安装与配置

### 1. 安装 Go
前往 [Go 官网](https://go.dev/dl/) 下载并安装。

### 2. 设置环境变量
```bash
# Linux / macOS
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```
```powershell
# Windows
setx GOROOT "C:\Go"
setx GOPATH "%USERPROFILE%\go"
setx PATH "%PATH%;%GOROOT%\bin;%GOPATH%\bin"
```

### 3. 验证安装
```bash
go version
```

---

## 三、基础语法

### 1. Hello World
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

### 2. 变量与常量
```go
var a int = 10
b := 20
const pi = 3.14
```

### 3. 基本类型
- 整型：int、int8、int16、int32、int64
- 浮点型：float32、float64
- 字符串：string
- 布尔型：bool

### 4. 流程控制
```go
if x > 10 {
    fmt.Println("x > 10")
} else {
    fmt.Println("x <= 10")
}

for i := 0; i < 5; i++ {
    fmt.Println(i)
}

switch day {
case "Mon":
    fmt.Println("Start of week")
default:
    fmt.Println("Other day")
}
```

---

## 四、数组、切片、映射

### 1. 数组
```go
var arr [3]int = [3]int{1, 2, 3}
```

### 2. 切片
```go
s := []int{1, 2, 3}
s = append(s, 4)
```

### 3. 映射（Map）
```go
m := map[string]int{"apple": 5, "banana": 2}
m["orange"] = 3
```

---

## 五、结构体与方法
```go
type Person struct {
    Name string
    Age  int
}

func (p Person) SayHello() {
    fmt.Println("Hello, my name is", p.Name)
}
```

---

## 六、接口与多态
```go
type Speaker interface {
    Speak()
}

type Dog struct{}
func (d Dog) Speak() { fmt.Println("Woof!") }

func main() {
    var s Speaker = Dog{}
    s.Speak()
}
```

---

## 七、并发编程

### 1. Goroutine
```go
go func() {
    fmt.Println("Running in goroutine")
}()
```

### 2. Channel
```go
ch := make(chan int)
go func() {
    ch <- 10
}()
x := <-ch
fmt.Println(x)
```

---

## 八、模块管理

### 1. 初始化模块
```bash
go mod init example.com/hello
```

### 2. 下载依赖
```bash
go get github.com/gin-gonic/gin
```

### 3. 构建项目
```bash
go build
```

---

## 九、常见错误与最佳实践
- 不要滥用全局变量
- 错误处理使用 `if err != nil`
- 注意协程泄漏
- 使用 `defer` 释放资源
- 优先使用结构体方法而非裸函数
- 使用 `context` 管理并发任务

