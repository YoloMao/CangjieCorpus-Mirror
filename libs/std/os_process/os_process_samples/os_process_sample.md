# 任意进程相关操作

下面是任意进程相关操作示例，以下示例不支持 Windows 平台。

代码如下：

<!-- verify -->

```cangjie
import std.os.process.*
import std.fs.*

main(): Int64 {
    let echoProcess: SubProcess = Process.start("sleep", "10s")
    let ofProcess: Process = Process.of(echoProcess.pid)
    println(ofProcess.pid)
    println(ofProcess.name)
    println(ofProcess.command)
    println(ofProcess.arguments.toString())
    println(ofProcess.commandLine.toString())
    ofProcess.terminate(force: true)
    return 0
}
```

运行结果可能如下：

```text
78980
sleep
sleep
[10s]
[sleep, 10s]
```
