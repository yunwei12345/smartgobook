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

