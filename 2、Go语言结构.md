## Go语言结构

#### Go 语言的基础组成

```go
package main
import "fmt"
func main() {
   /* 这是我的第一个简单的程序 */
   fmt.Println("Hello, World!")
}
```

- 包声明

  第一行代码 *package main* 定义了包名。你必须在源文件中非注释的第一行指明这个文件属于哪个包，如：package main。package main表示一个可独立执行的程序，每个 Go 应用程序都包含一个名为 main 的包

- 引入包

  下一行 *import "fmt"* 告诉 Go 编译器这个程序需要使用 fmt 包

- 函数

  main 函数是每一个可执行程序所必须包含的，一般来说都是在启动后第一个执行的函数（如果有 init() 函数则会先执行该函数)

- 变量

- 语句 & 表达式

- 注释

   /\*···\*/ 是注释
   
------

#### 执行Go程序

1. 将文件保存为hello.go

2. 打开命令行，进入该文件保存的目录

3. 输入命令 `go run hello.go` 并按下回车键执行代码

4. 我们还可以使用 `go build` 命令来生成二进制文件,如：

   > `$ go build hello.go 
   > $ ls
   > hello    hello.go
   > $ ./hello 
   > Hello, World!`


#### 注意：

- 需要注意的是**`{`** 不能单独放在一行，所以以下代码在运行时会产生错误

```go
package main
import "fmt"
func main()  
{  // 错误，{ 不能在单独的行上
    fmt.Println("Hello, World!")
}
```



