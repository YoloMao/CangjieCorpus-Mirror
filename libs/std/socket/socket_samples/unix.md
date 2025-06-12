# UNIX 使用示例

<!-- verify -->

```cangjie
import std.socket.*
import std.time.*
import std.sync.*

let SOCKET_PATH = "/tmp/tmpsock"

func runUnixServer() {
    try (serverSocket = UnixServerSocket(bindAt: SOCKET_PATH)) {
        serverSocket.bind()

        try (client = serverSocket.accept()) {
            client.write("hello".toArray())
        }
    }
}

main(): Int64 {
    spawn {
        runUnixServer()
    }
    sleep(Duration.second)

    try (socket = UnixSocket(SOCKET_PATH)) {
        socket.connect()

        let buf = Array<Byte>(10, item: 0)
        socket.read(buf)

        println(String.fromUtf8(buf)) // hello
    }

    return 0
}
```

运行结果:

```text
hello
```
