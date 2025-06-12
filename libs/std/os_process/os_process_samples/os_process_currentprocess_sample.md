# 当前进程相关操作

下面是当前进程相关操作示例，以下示例不支持 Windows 平台。

代码如下：

<!-- verify -->

```cangjie
import std.os.process.*

main(): Int64 {
    let curProcess = Process.current
    println(curProcess.pid)
    println(curProcess.name)
    println(curProcess.command)
    println(curProcess.arguments.toString())
    println(curProcess.commandLine.toString())
    println(curProcess.workingDirectory.toString())
    curProcess.atExit(printText)
    curProcess.exit(0)
    return 0
}

func printText(): Unit {
    println("hello cangjie!")
}
```

运行结果可能如下（输出结果中main为当前进程执行命令名，回调执行完成后当前进程会退出）：

```text
75590
./main
./main
[]
[./main]
/root/code/Process/test
hello cangjie!
```
