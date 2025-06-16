# cookie

## Client
<!-- verify -->

```cangjie
import net.http.*
import encoding.url.*
import std.socket.*
import std.time.*
import std.sync.*

main() {
    // 1、启动socket服务器
    let serverSocket = TcpServerSocket(bindAt: 0)
    serverSocket.bind()
    let fut = spawn {
        serverPacketCapture(serverSocket)
    }
    sleep(Duration.millisecond * 10)
    // 客户端一般从 response 中的 Set-Cookie header 中读取 cookie，并将其存入 cookieJar 中，
    // 下次发起 request时，将其放在 request 的 Cookie header 中发送
    // 2、启动客户端
    let client = ClientBuilder().build()
    let port = serverSocket.localAddress.port
    var u = URL.parse("http://127.0.0.1:${port}/a/b/c")
    var r = HttpRequestBuilder()
                        .url(u)
                        .build()
    // 3、发送request
    client.send(r)
    sleep(Duration.second * 2)
    r = HttpRequestBuilder()
                        .url(u)
                        .build()
    // 4、发送新 request，从 CookieJar 中取出 cookie，并转成 Cookie header 中的值
    // 此时 cookie 2=2 已经过期，因此只发送 1=1 cookie
    client.send(r)
    // 5、关闭客户端
    client.close()
    fut.get()
    serverSocket.close()
}

func serverPacketCapture(serverSocket: TcpServerSocket) {
    let buf = Array<UInt8>(500, item: 0)
    let server = serverSocket.accept()
    var i = server.read(buf)
    println(String.fromUtf8(buf[..i]))
    // GET /a/b/c HTTP/1.1
    // host: 127.0.0.1:44649
    // user-agent: CANGJIEUSERAGENT_1_1
    // connection: keep-alive
    // content-length: 0
    //
    // 过期时间为 4 秒的 cookie1
    let cookie1 = Cookie("1", "1", maxAge: 4, domain: "127.0.0.1", path: "/a/b/")
    let setCookie1 = cookie1.toSetCookieString()
    // 过期时间为 2 秒的 cookie2
    let cookie2 = Cookie("2", "2", maxAge: 2, path: "/a/")
    let setCookie2 = cookie2.toSetCookieString()
    // 服务器发送 Set-Cookie 头，客户端解析并将其存进 CookieJar 中
    server.write("HTTP/1.1 204 ok\r\nSet-Cookie: ${setCookie1}\r\nSet-Cookie: ${setCookie2}\r\nConnection: close\r\n\r\n".toArray())

    let server2 = serverSocket.accept()
    i = server2.read(buf)
    // 接收客户端的带 cookie 的请求
    println(String.fromUtf8(buf[..i]))
    // GET /a/b/c HTTP/1.1
    // host: 127.0.0.1:34857
    // cookie: 1=1
    // user-agent: CANGJIEUSERAGENT_1_1
    // connection: keep-alive
    // content-length: 0
    //
    server2.write("HTTP/1.1 204 ok\r\nConnection: close\r\n\r\n".toArray())
    server2.close()
}
```

运行结果如下：

```text
GET /a/b/c HTTP/1.1
host: 127.0.0.1:37359
user-agent: CANGJIEUSERAGENT_1_1
connection: keep-alive
content-length: 0


GET /a/b/c HTTP/1.1
host: 127.0.0.1:37359
cookie: 1=1
user-agent: CANGJIEUSERAGENT_1_1
connection: keep-alive
content-length: 0
```

## Server
<!-- compile -->

```cangjie
import net.http.*

main () {
   // 服务器设置 cookie 时将 cookie 放在 Set-Cookie header 中发给客户端
    // 1. 构建 Server 实例
    let server = ServerBuilder()
                       .addr("127.0.0.1")
                       .port(8080)
                       .build()
    // 2. 注册 HttpRequestHandler
    server.distributor.register("/index", {httpContext =>
        let cookie = Cookie("name", "value")
        httpContext.responseBuilder.header("Set-Cookie", cookie.toSetCookieString()).body("Hello 仓颉!")
    })
    // 3. 启动服务
    server.serve()
}
```
