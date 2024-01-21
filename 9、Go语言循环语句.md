## Go 语言循环语句

Go 语言提供了以下几种类型循环处理语句：

| 循环类型                                                   | 描述                                 |
| :--------------------------------------------------------- | :----------------------------------- |
| [for 循环](https://www.runoob.com/go/go-for-loop.html)     | 重复执行语句块                       |
| [循环嵌套](https://www.runoob.com/go/go-nested-loops.html) | 在 for 循环中嵌套一个或多个 for 循环 |

#### for 循环

##### 语法

Go 语言的 For 循环有 3 种形式，只有其中的一种使用分号。

和 C 语言的 for 一样：

> `for init; condition; post { }`

和 C 的 while 一样：

> `for condition { }`

和 C 的 for(;;) 一样：

>`for { }`

for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。格式如下：

```go
for key, value := range oldMap {
    newMap[key] = value
}
```

如果只想读取 key：

`for key := range oldMap`

或

`for key, _ := range oldMap`

如果只想读取 key：

`for key := range oldMap`

#### 循环控制语句

循环控制语句可以控制循环体内语句的执行过程。

GO 语言支持以下几种循环控制语句：

| 控制语句                                                     | 描述                                             |
| :----------------------------------------------------------- | :----------------------------------------------- |
| [break 语句](https://www.runoob.com/go/go-break-statement.html) | 经常用于中断当前 for 循环或跳出 switch 语句      |
| [continue 语句](https://www.runoob.com/go/go-continue-statement.html) | 跳过当前循环的剩余语句，然后继续进行下一轮循环。 |
| [goto 语句](https://www.runoob.com/go/go-goto-statement.html) | 将控制转移到被标记的语句。                       |

**可以用标号 label 跳出当前的n重循环**