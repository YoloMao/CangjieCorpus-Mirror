# UnixDatagram 使用示例

<!-- verify -->

```cangjie
import std.socket.*
import std.time.*
import std.sync.*
import std.fs.*
import std.os.*
import std.random.*

func createTempFile(): String {
    let tempDir: Path = tempDir().info.path

    let index: String = Random().nextUInt64().toString()

    return tempDir.join("tmp${index}").toString()
}

func runUnixDatagramServer(serverPath: String, clientPath: String) {
    try (serverSocket = UnixDatagramSocket(bindAt: serverPath)) {
        serverSocket.bind()

        let buf = Array<Byte>(3, item: 0)

        let (clientAddr, read) = serverSocket.receiveFrom(buf)

        if (read == 3 && buf == Array<Byte>([1, 2, 3])) {
            println("server received")
        }
        if (clientAddr.toString() == clientPath) {
            println("client address correct")
        }
    }
}

main(): Int64 {
    let clientPath = createTempFile()
    let serverPath = createTempFile()
    spawn {
        runUnixDatagramServer(serverPath, clientPath)
    }
    sleep(Duration.second)

    try (unixSocket = UnixDatagramSocket(bindAt: clientPath)) {
        unixSocket.sendTimeout = Duration.second * 2
        unixSocket.bind()
        unixSocket.connect(serverPath)

        unixSocket.send(Array<Byte>([1, 2, 3]))
        sleep(Duration.second)
    }

    return 0
}
```

运行结果:

```text
server received
client address correct
```
