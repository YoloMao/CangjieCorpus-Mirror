# std 模块

>  **注意：**
>
> 当前暂不支持通过 import std 直接导入 std 模块，否则，在编译阶段会报无法找到 std 包的错误（error: can not find package 'std'） 。建议当前使用导入 std 子包的形式使用 std 模块。

## std 功能介绍

std 模块意指标准库，标准库是指在编程语言中预先定义的一组函数、类、结构体等，旨在提供常用的功能和工具，以便开发者能够更快速、更高效地编写程序。

仓颉标准库提供的能力包括（不限于）：

- 输入输出：控制台输入输出、文件输入输出等。
- 数据结构：数组、链表、哈希表等。
- 算法：排序、求和、求幂、求对数等。
- 日期和时间：获取时间、格式化时间、设置定时任务等。
- 并发编程：锁、原子操作等。

仓颉标准库有其三项特点和追求：

- 使用方便：标准库随编译器、工具链一起发布，不需要用户另外下载，开箱即用。
- 功能通用：标准库提供了开发者最常使用的一些库能力，旨在为开发者解决大部分基础问题。
- 质量标杆：标准库追求在性能、代码风格等方面为其他仓颉库树立范例和标杆。

## std 模块的包列表

std 模块提供了如下包：

|                              包名                              |    功能    |
| -------------------------------------------------------------- | --------- |
| [core](./core/core_package_overview.md)                        | core 包是标准库的核心包，提供了适用仓颉语言编程最基本的一些 API 能力。 |
| [argopt](./argopt/argopt_package_overview.md)                        | argopt 包提供从命令行参数字符串解析出参数名和参数值的相关能力。 |
| [ast](./ast/ast_package_overview.md)                        | ast 包主要包含了仓颉源码的语法解析器和仓颉语法树节点，提供语法解析函数。 |
| [binary](./binary/binary_package_overview.md)                        | binary 包提供了基础数据类型和二进制字节数组的不同端序转换接口，以及端序反转接口。 |
| [collection](./collection/collection_package_overview.md)                        | collection 包提供了常见数据结构的高效实现、相关抽象的接口的定义以及在集合类型中常用的函数功能。 |
| [collection.concurrent](./collection_concurrent/collection_concurrent_package_overview.md)                        | collection.concurrent 包提供了并发安全的集合类型实现。 |
| [console](./console/console_package_overview.md)                        | console 包提供和标准输入、标准输出、标准错误进行交互的方法。 |
| [convert](./convert/convert_package_overview.md)                        | convert 包提供从字符串转到特定类型的 Convert 系列函数。 |
| [crypto.cipher](./crypto/cipher/cipher_package_overview.md)                        | crypto.cipher 包提供对称加解密通用接口。 |
| [crypto.digest](./crypto/digest/digest_package_overview.md)                        | crypto.digest 包提供常用摘要算法的通用接口，包括 MD5、SHA1、SHA224、SHA256、SHA384、SHA512、HMAC、SM3。 |
| [database.sql](./database_sql/database_sql_package_overview.md)                        | database.sql 包提供仓颉访问数据库的接口。 |
| [ffi.python](./ffi_python/ffi_python_package_overview.md)                        | ffi.python 包提供仓颉与 Python 语言互操作调用的能力，以兼容强大的计算和 AI 生态。 |
| [format](./format/format_package_overview.md)                        | format 包提供格式化能力，主要为将仓颉类型实例转换为格式化字符串。 |
| [fs](./fs/fs_package_overview.md)                        | fs（file system）包提供对文件、文件夹、路径、文件元数据信息的一些操作函数。 |
| [io](./io/io_package_overview.md)                        | io 包提供程序与外部设备进行数据交换的能力。 |
| [log](./log/stdlog_package_overview.md)                        | log 包提供日志管理和打印功能。 |
| [math](./math/math_package_overview.md)                        | math 包提供常见的数学运算，常数定义，浮点数处理等功能。 |
| [math.numeric](./math_numeric/math_numeric_package_overview.md)                        | math.numeric 包对基础类型可表达范围之外提供扩展能力。 |
| [objectpool](./objectpool/objectpool_package_overview.md)                        | objectpool 包提供了对象缓存和复用的功能。 |
| [os](./os/os_package_overview.md)                        | os 包提供了包括获取或操作当前进程相关信息(如进程参数、环境变量、目录信息等)，注册回调函数及退出当前进程等能力。 |
| [os.posix](./os_posix/os_posix_package_overview.md)                        | os.posix 包主要适配 POSIX 系统接口。 |
| [os.process](./os_process/os_process_package_overview.md)                        | os.process 包主要提供 Process 进程操作接口，主要包括进程创建，标准流获取，进程等待，进程信息查询等。 |
| [overflow](./overflow/overflow_package_overview.md)                        | overflow 包提供了溢出处理相关能力。 |
| [random](./random/random_package_overview.md)                        | random 包提供生成伪随机数的能力。 |
| [reflect](./reflect/reflect_package_overview.md)                        | reflect 包提供了反射功能，使得程序在运行时能够获取到各种实例的类型信息，并进行各种读写和调用操作。 |
| [regex](./regex/regex_package_overview.md)                        | regex 包使用正则表达式分析处理文本的能力（仅支持 Ascii 编码字符串），支持查找、分割、替换、验证等功能。 |
| [runtime](./runtime/runtime_package_overview.md)                        | runtime 包的作用是与程序的运行时环境进行交互，提供了一系列函数和变量，用于控制、管理和监视程序的执行。 |
| [socket](./socket/socket_package_overview.md)                        | socket 包用于进行网络通信，提供启动 Socket 服务器、连接 Socket 服务器、发送数据、接收数据等功能。 |
| [sort](./sort/sort_package_overview.md)                        | sort 包提供数组类型的排序函数。 |
| [sync](./sync/sync_package_overview.md)                        | sync 包提供并发编程相关的能力。 |
| [time](./time/time_package_overview.md)                        | time 包提供了与时间相关的类型，包括日期时间，时间间隔，单调时间和时区等，并提供了计算和比较的功能。 |
| [unicode](./unicode/unicode_package_overview.md)                        | unicode 包提供了按 unicode 编码标准处理字符的能力。 |
| [unittest](./unittest/unittest_package_overview.md)                        | unittest 包用于编写仓颉项目单元测试代码，提供包括代码编写、运行和调测在内的基本功能。 |
| [unittest.mock](./unittest_mock/unittest_mock_package_overview.md)                        |unittest.mock 包提供仓颉单元测试的**mock 框架**，提供 API 用于创建和配置**mock 对象** ，这些 mock 对象与真实对象拥有签名一致的 API 。 |
| [unittest.testmacro](./unittest_testmacro/unittest_testmacro_package_overview.md)                        | unittest.testmacro 为单元测试框架提供了用户所需的宏。 |
| [unittest.mock.mockmacro](./unittest_mock_mockmacro/unittest_mock_mockmacro_package_overview.md)                        | unittest.mock.mockmacro 为 mock 框架提供了用户所需的宏。 |
| [unittest.common](./unittest_common/unittest_common_package_overview.md)                        | unittest.common 为单元测试框架提供了打印所需的类型和一些通用方法。 |
| [unittest.diff](./unittest_diff/unittest_diff_package_overview.md)                        | unittest.diff 为单元测试框架提供了打印差异对比信息所需的 API 。 |
| [unittest.prop_test](./unittest_prop_test/unittest_prop_test_package_overview.md)                        | unittest.prop_test 为单元测试框架提供了参数化测试所需的类型和一些通用方法。 |