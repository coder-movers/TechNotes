### go命令

> 项目初始化
>
> ```
> go mod init <文件夹名>
> ```

| 命令     | 用例                                  | 说明                                                        |
| -------- | ------------------------------------- | ----------------------------------------------------------- |
| build    | go build main.go                      | 生成exe可执行文件                                           |
| run      | go run main.go                        | 运行go文件                                                  |
| clean    | go clean                              | 移除对象文件                                                |
| env      | go env                                | 打印go的环境信息                                            |
| bug      |                                       | 启动错误报告                                                |
| fix      | go tool fix                           | 修复                                                        |
| fmt      |                                       | 运行gofmt格式化                                             |
| generate |                                       | 从processing source生成go文件，一般不用                     |
| get      | go get github.com/go-sql-driver/mysql | 下载并安装包和依赖，使用前需要先执行`go mod init 文件夹名 ` |
| install  |                                       | 编译并安装包和依赖，和go get 差不多                         |
| list     | go list                               | 列出包                                                      |
| test     |                                       | 运行测试                                                    |
| tool     | go tool                               | 运行go提供的工具                                            |
| version  | go version                            | 显示go的版本                                                |
| vet      | go tool vet                           | 运行vet工具                                                 |



### go mod 命令

| 命令                           | 说明                                                         |
| ------------------------------ | ------------------------------------------------------------ |
| go mod init <项目模块名称>     | 初始化模块                                                   |
| go mod tidy                    | 依赖关系处理，根据go.mod文件                                 |
| go mod vendor                  | 将依赖包复制到项目下的vendor目录（如果包呗屏蔽/墙，可以使用这个命令，随后使用go build -mod=vendor编译） |
| go list -m all                 | 显示依赖关系                                                 |
| go list -m -json all           | 显示详细依赖关系                                             |
| go mod download [path@version] | 下载依赖（[path@version]是非必写的）                         |



### go语言数据类型

| 类型       |         | 描述                                          | 举例                                                         |
| ---------- | ------- | --------------------------------------------- | ------------------------------------------------------------ |
| 布尔型     | bool    |                                               |                                                              |
| 数字类型   | int     | 整型，包括Int8，int16，int32，int64，默认值0  |                                                              |
|            | uint    | 无符号整型，包括uInt8，uint16，uint32，uint64 |                                                              |
|            | float32 | 浮点型，默认值0.0                             |                                                              |
|            | float64 | 浮点型                                        |                                                              |
| 字符串类型 | string  |                                               |                                                              |
| 派生类型   |         | 指针类型（Pointer）                           |                                                              |
|            |         | 数组类型                                      | var arr = [3]int{1,2,3}也可以var arr = [...]int{1,2,3} `...`表示不定长数组 |
|            |         | 结构化类型（struct）                          |                                                              |
|            |         | Channel类型                                   |                                                              |
|            |         | 函数类型                                      |                                                              |
|            |         | 切片类型                                      | var s = []int{1,2,3}和数组很像                               |
|            |         | 接口类型（interface）                         |                                                              |
|            |         | Map类型                                       |                                                              |



### Printf时的数字类型占位符

| 占位符 | 说明                 |
| ------ | -------------------- |
| %d     | 以十进制输出         |
| %u     | 输出无符号十进制数   |
| %b     | 以二进制输出         |
| %o     | 以八进制输出         |
| %x     | 以十六进制输出，小写 |
| %X     | 以十六进制输出，大写 |
| %f     | 输出浮点数           |
| %.2f   | 浮点类型保留两位小数 |

> 其他占位符
>
> | 占位符 | 说明         |
> | ------ | ------------ |
> | %c     | 输出单个字符 |
> | %p     | 指针类型     |



### 注意事项

声明过的变量必须使用  不使用的话可以用`_`代替，表示匿名变量



### 数组截取

```go
	arr1 := [...]string{"a", "b", "c", "d"}
	fmt.Println(arr1[:])   // 截取全部
	fmt.Println(arr1[2:3]) // 从索引2截取到3 左闭右开
	fmt.Println(arr1[:3])  // 截取索引0-3
	fmt.Println(arr1[2:])  // 截取索引2-最后
```



### 结构体作为函数参数

两种情况：

1. 直接传递结构体，这是一个副本（拷贝），在函数内部不会改变外部结构体的内容
2. 传递结构体指针，这是在函数内部，能够改变外部结构体内容



### OCP原则

> ”开-闭“原则（Open-Closed Principle,常缩写为OCP）

对扩展是开放的，对修改是关闭的。



### 首字母问题

> struct中的属性首字母大写的话在其他包也可访问
>
> func 的首字母大写也表示在其他模块中可以使用
>
> 首字母小写则表示私有属性 在其他包无法访问



### channel

> 注意：如果通道关闭，读多写少，没有了就是默认值，例如int就是0，如果没有关闭就会死锁

```go
var c = make(chan int) // 创建int类型通道
c <- 1 // 将1放入通道

a := <- c //将值取出通道
```



### channel的select

1. select是Go中的一个控制结构，类似于`switch`语句，用于处理异步IO操作。`select`会监听case语句中channel的读写操作，当`case`中`channel`读写操作为非阻塞状态（即能读写）时，将会触发相应的动作。

   > select中的case语句必须是一个channel操作
   >
   > select中的default子句总是可运行的

2. 如果有多个`case`都可运行，`select`会随机公平地选出一个执行，其他的不会执行。

3. 如果没有可运行的`case`语句，且有`default`语句，那么就会执行`default`的动作

4. 如果没有可运行的`case`语句，且没有`default`语句，那么`select`将会阻塞，直到某个`case`通信可以运行



### Timer和Ticker

Timer只执行一次，Ticker可以周期性执行