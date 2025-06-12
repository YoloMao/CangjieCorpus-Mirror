# 获取参数、环境变量及相关目录信息
<!-- verify -->

```cangjie
import std.os.*
import std.fs.*
import std.collection.*

main(): Unit {
    let args: Array<String> = getArgs()
    let envs: HashMap<String, String> = envVars()
    let currentDir: Directory = currentDir()
    let homeDir: Directory = homeDir()
    let tempDir: Directory = tempDir()
    let processorCount: Int64 = processorCount()

    println("args: ${args}")
    println("envs: ${envs}")
    println("currentDir: ${currentDir.info.path.toString()}")
    println("homeDir: ${homeDir.info.path.toString()}")
    println("tempDir: ${tempDir.info.path.toString()}")
    println("processorCount: ${processorCount}")
    return
}
```

运行结果如下（根据系统与运行环境不同返回结果可能不同）：

```text
args: []
envs: [(USER, root),(PWD, /root/code/cangjie)]
currentDir: /root/code/cangjie
homeDir: /root
tempDir: /tmp
processorCount: 96
```
