## Go 语言变量

声明变量的一般形式是使用 var 关键字：

`var identifier type`

可以一次声明多个变量：

`var identifier1, identifier2 type`

#### 变量声明

**1. 指定变量类型，如果没有初始化，则变量默认为零值**


- 数值类型（包括complex64/128）为 0

- 布尔类型为 **false**

- 字符串为 **""**（空字符串）

- 以下几种类型为 **nil**(零值或空值)：

  > `var a *int
  > var a []int
  > var a map[string] int
  > var a chan int
  > var a func(string) int
  > var a error  //error 是接口`

**2. 根据值自行判定变量类型**

```go
package main
import "fmt"
func main() {
    var d = true
    fmt.Println(d)
}
```

输出结果是：`true`

**3. 如果变量已经使用 var 声明过了，再使用 `:=` 声明变量，就产生编译错误，格式：**

`v_name := value`

```go
var intVal int 
intVal :=1 // 这时候会产生编译错误，因为 intVal 已经声明，不需要重新声明
```

**`intVal := 1`** 相等于：

```go
var intVal int 
intVal =1 
```

#### 多变量声明

```go
package main
import "fmt"
var x, y int
var (  // 这种因式分解关键字的写法一般用于声明全局变量
    a int
    b bool
)
var c, d int = 1, 2
var e, f = 123, "hello"
//这种不带声明格式的只能在函数体中出现
//g, h := 123, "hello"
func main(){
    g, h := 123, "hello"
    fmt.Println(x, y, a, b, c, d, e, f, g, h)
}
```

#### 值类型和引用类型

**值类型：**
值类型的变量直接存储值，当这个值被赋值给一个新变量时，会创建一个新的副本。这意味着对于同一个值类型变量的操作，不会影响其他变量的值。常见的值类型包括：基本数据类型（如int、float、bool等）、数组、结构体等

**引用类型：**
引用类型的变量存储的是一个地址，这个地址指向实际的数据。当这个变量被赋值给一个新变量时，会创建一个新的变量，但它们都指向同一个地址。这意味着对于同一个引用类型变量的操作，会影响其他变量的值。常见的引用类型包括：指针、切片、映射、通道等

#### 简短形式，使用 := 赋值操作符

可以在变量的初始化时省略变量的类型而由系统自动推断，声明语句写上 var 关键字其实是显得有些多余了

**`:=`**是使用变量的首选形式，但是它只能被用在函数体内，而不可以用于全局变量的声明与赋值。使用操作符 := 可以高效地创建一个新的变量，称之为初始化声明

#### 注意事项

如果你声明了一个局部变量却没有在相同的代码块中使用它，会得到编译错误，例如下面这个例子当中的变量 a：

```go
package main
import "fmt"
func main() {
   var a string = "abc"
   fmt.Println("hello, world")
}
```

尝试编译这段代码将得到错误 **`a declared but not used`**

**但是全局变量是允许声明但不使用的**

#### 空白标识符

```go
package main
import "fmt"
func main() {
  _,numb,strs := numbers() //只获取函数返回值的后两个
  fmt.Println(numb,strs)
}
//一个可以返回多个值的函数
func numbers()(int,int,string){
  a , b , c := 1 , 2 , "str"
  return a,b,c
}
```

