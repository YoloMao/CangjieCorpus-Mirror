# Windows 平台子进程结束后删除子进程可执行文件

下面是 Windows 平台子进程结束后删除子进程可执行文件失败后的处理示例。

代码如下：

<!-- verify -->

```cangjie
import std.os.process.*
import std.io.*
import std.fs.*
import std.time.*
import std.sync.*

// 以Windows平台相关命令举例说明, 以下用例需要在当前目录下提前创建 “test.exe” 可执行文件
main(): Int64 {
    Process.runOutput("cmd.exe", "/c", "test.exe")
    for (_ in 0..5) {
        try {
            File.delete(".\\test.exe")
            break
        } catch (e: FSException) {
            if (e.message != "Failed to recursive delete directory: \"Access is denied.\".") {
                throw e
            }
            sleep(Duration.millisecond * 5)
        }
    }
    println("delete file success.")
    return 0
}
```

运行结果可能如下：

```text
delete file success.
```
