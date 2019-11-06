###              Go 语言结构





一   Go 语言的基础组成有以下几个部分：

- 包声明
- 引入包
- 函数
- 变量
- 语句 & 表达式
- 注释





二   实例代码





```
package main

import "fmt"

func main() {
   /* 这是我的第一个简单的程序 */
   fmt.Println("Hello, World!")
}
```



​       



* 第一行 *package main* 定义了包名，表示一个可独立执行的程序。
* *import "fmt"* 告诉 Go 编译器这个程序需要使用 fmt 包（的函数，或其他元素），fmt 包实现了格式化 IO（输入/输出）的函数
*  *func main()* 是程序开始执行的函数。
* /*...*/ 是注释，在程序执行时将被忽略。
* *fmt.Println(...)* 可以将字符串输出到控制台，









### Go语言基础语法



一  GO标记



Go 程序可以由多个标记组成，可以是关键字，标识符，常量，字符串，符号。如以下 GO 语句由 6 个标记组成：



```
fmt.Println("Hello, World!")
```



每行一个标记

```
. fmt
2. .
3. Println
4. (
5. "Hello, World!"
6. )
```





### GO语言数据类型





#####   一    作用：

用于声明函数和变量





#####   二   分类

* 布尔型：值只可以是常量 true 或者 false

* 数字类型：整型 int 和浮点型 float32、float64

* 字符串类型: 串固定长度的字符连接起来的字符序列.

* 派生类型:

  * 指针

  * 数组

  * 结构化

  * Channel

  * 函数

  * 切片

  * 接口

  * Map






### GO语言变量



##### 一   组成形式：由字母、数字、下划线组成，其中首个字符不能为数字。



1. ##### 声明变量的一般形式是使用 var 关键字：


```
var identifier type
```

    2. ##### 可以一次声明多个变量

```
var identifier1, identifier2 type
```



    3. ##### 代码实例



```
package main
import "fmt"
func main() {
    var a string = "Runoob"
    fmt.Println(a)

    var b, c int = 1, 2
    fmt.Println(b, c)
}


```

```
Runoob
1 2
```





####  二   变量声明方法



1.  **指定变量类型，如果没有初始化，则变量默认为零值**。


```
var v_name v_type
v_name = value
```

​      

```
package main
import "fmt"
func main() {

    // 声明一个变量并初始化
    var a = "RUNOOB"
    fmt.Println(a)

    // 没有初始化就为零值
    var b int
    fmt.Println(b)

    // bool 零值为 false
    var c bool
    fmt.Println(c)
}
```

```
RUNOOB
0
false
```



2. #####  根据值自行判断变量类型

```
var v_name = value
```



```
package main
import "fmt"
func main() {
    var d = true
    fmt.Println(d)
}
```

```
true
```



     3. ##### 省略 var, 注意 := 左侧如果没有声明新的变量，就产生编译错误，格式：



```
v_name := value
```



```
package main
import "fmt"
func main() {
    f := "Runoob" // var f string = "Runoob"

    fmt.Println(f)
}
```

​     

```
Runoob 
```







### GO语言常量



#### 一  什么是常量：

1.  常量是一个简单值的标识符，在程序运行时，不会被修改的量。

   常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。

   

          2. 定义格式：

```
onst identifier [type] = value
```



3.  实例



```
package main

import "fmt"

func main() {
   const LENGTH int = 10
   const WIDTH int = 5   
   var area int
   const a, b, c = 1, false, "str" //多重赋值

   area = LENGTH * WIDTH
   fmt.Printf("面积为 : %d", area)
   println()
   println(a, b, c)
```

运行结果

```
面积为 : 50
1 false str
```







#### 二   iota 



1. #####  iota介绍


*  iota，特殊常量，可以认为是一个可以被编译器修改的常量。

* iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，const 中每新增一行常量声明将使 iota 计数一次

* 可用于枚举



​    

2. ##### iota用法

```
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



运行结果



```
0 1 2 ha ha 100 100 7 8
```









### GO语言运算符



* 算术运算符
* 关系运算符
* 逻辑运算符
* 位运算符
* 赋值运算符
* 其他运算符



#### 一  算术运算符

