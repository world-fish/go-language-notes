## Go 语言常量

常量是一个简单值的标识符，在程序运行时，不会被修改的量。

常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。

#### 常量的定义格式：

`const identifier [type] = value`

- 显式类型定义： `const b string = "abc"`
- 隐式类型定义： `const b = "abc"`

常量可以用len(), cap(), unsafe.Sizeof()函数计算表达式的值。常量表达式中，函数必须是内置函数，否则编译不过：

```go
package main
import "unsafe"
const (
    a = "abc"
    b = len(a)
    c = unsafe.Sizeof(a)
)
func main(){
    println(a, b, c)
}
```

以上实例运行结果为：

`abc 3 16`

注：

在Go语言中，字符串类型是一个结构体，包含一个指向底层数据的指针和一个表示字符串长度的整数。在64位系统上，每个指针占用8字节，整数占用8字节。因此，一个字符串类型在64位系统上总共占用16字节的空间

内置函数是 Go 语言标准库中提供的函数，可以直接使用，无需导入任何包

常量表达式是指在编译时就可以完全计算出结果的表达式

#### iota

iota，特殊常量，可以认为是一个可以被编译器修改的常量。

iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中每新增一行常量声明将使 iota 计数一次(iota 可理解为 const 语句块中的行索引)。

##### iota 用法

```go
package main
import "fmt"
func main() {
    const (
            a = iota   //0
            b          //1
            c          //2
            d = "ha"   //独立值，iota += 1
            e          //"ha"   iota += 1
            f = 100    //iota +=1
            g          //100  iota +=1
            h = iota   //7,恢复计数
            i          //8
    )
    fmt.Println(a,b,c,d,e,f,g,h,i)
}
```

在定义常量组时，如果不提供初始值，则表示将使用上行的表达式(因为没有显式赋值，会继承自上一个常量的值)

##### 一个有趣的的 iota 实例：

```go
package main
import "fmt"
const (
    i=1<<iota
    j=3<<iota
    k
    l
)
func main() {
    fmt.Println("i=",i)
    fmt.Println("j=",j)
    fmt.Println("k=",k)
    fmt.Println("l=",l)
}
```

以上实例运行结果为：

>**`i= 1
>j= 6
>k= 12
>l= 24`**

简单表述：

>**`i=1：左移 0 位，不变仍为 1。
>j=3：左移 1 位，变为二进制 110，即 6。
>k=3：左移 2 位，变为二进制 1100，即 12。
>l=3：左移 3 位，变为二进制 11000，即 24。`**

注：**`<<n==\*(2^n)`**

