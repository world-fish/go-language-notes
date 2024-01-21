## Go语言基础语法

#### Go 标记

Go 程序可以由多个标记组成，可以是关键字，标识符，常量，字符串，符号。如以下 GO 语句由 6 个标记组成：

```go
fmt.Println("Hello, World!")
```

6 个标记分别是：

> `fmt
> .
> Println
> (
> "Hello, World!"
> )`

#### 行分隔符

在Go中，一行代表一个语句结束，不需要以**`;`**结尾

如果你打算将多个语句写在同一行，它们则必须使用**`;`**人为区分

------

#### 注释

```注释
// 单行注释
/*
 Author by 菜鸟教程
 我是多行注释
 */
```

------

#### 标识符

标识符用来命名变量、类型等程序实体。一个标识符实际上就是一个或是多个字母(A~Z和a~z)数字(0~9)、下划线_组成的序列，但是第一个字符必须是字母或下划线而不能是数字

------

#### 字符串连接

Go 语言的字符串连接可以通过 **+** 实现,也可以直接由**`,`**拼接

```go
package main
import "fmt"
func main() {
    fmt.Println("Google" + "Runoob")
		fmt.Println("Google", "Runoob")
}
```

以上实例输出结果为

`GoogleRunoob
Google Runoob`

------

格式化字符串

Go 语言中使用 **fmt.Sprintf** 或 **fmt.Printf** 格式化字符串并赋值给新串：

- **Sprintf** 根据格式化参数生成格式化的字符串并返回该字符串（有返回值，但不输出）
- **Printf** 根据格式化参数生成格式化的字符串并写入标准输出（输出，无返回值）

**Sprintf** 实例：

```go
package main
import (
    "fmt"
)
func main() {
   // %d表示整型数字，%s表示字符串
    var stockcode=123
    var enddate="2020-12-31"
    var url="Code=%d&endDate=%s"
    var target_url=fmt.Sprintf(url,stockcode,enddate)
    fmt.Println(target_url)
}
```

输出结果为：

`Code=123&endDate=2020-12-31`

**Printf**实例：

```go
package main
import (
    "fmt"
)
func main() {
   // %d 表示整型数字，%s 表示字符串
    var stockcode=123
    var enddate="2020-12-31"
    var url="Code=%d&endDate=%s"
    fmt.Printf(url,stockcode,enddate)
}
```

输出结果为：

`Code=123&endDate=2020-12-31`