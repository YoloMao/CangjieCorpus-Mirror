# server

## Hello 仓颉

<!-- compile -->

```cangjie
import net.http.ServerBuilder

main () {
    // 1. 构建 Server 实例
    let server = ServerBuilder()
                        .addr("127.0.0.1")
                        .port(8080)
                        .build()
    // 2. 注册 HttpRequestHandler
    server.distributor.register("/index", {httpContext =>
        httpContext.responseBuilder.body("Hello 仓颉!")
    })
    // 3. 启动服务
    server.serve()
}
```

## 通过 request distributor注册处理器

<!-- compile -->

```cangjie
import net.http.{ServerBuilder, HttpRequestHandler, FuncHandler}

main () {
    // 1. 构建 Server 实例
    let server = ServerBuilder()
                        .addr("127.0.0.1")
                        .port(8080)
                        .build()
    var a: HttpRequestHandler = FuncHandler({ httpContext =>
        httpContext.responseBuilder.body("index")
    })
    var b: HttpRequestHandler = FuncHandler({ httpContext =>
        httpContext.responseBuilder.body("id")
    })
    var c: HttpRequestHandler = FuncHandler({ httpContext =>
        httpContext.responseBuilder.body("help")
    })
    server.distributor.register("/index", a)
    server.distributor.register("/id", b)
    server.distributor.register("/help", c)
    // 2. 启动服务
    server.serve()
}
```

## 自定义 request distributor与处理器

<!-- compile -->

```cangjie
import net.http.*
import std.collection.HashMap

class NaiveDistributor <: HttpRequestDistributor {
    let map = HashMap<String, HttpRequestHandler>()
    public func register(path: String, handler: HttpRequestHandler): Unit {
        map.put(path, handler)
    }

    public func distribute(path: String): HttpRequestHandler {
        if (path == "/index") {
            return PageHandler()
        }
        return NotFoundHandler()
    }
}

// 返回一个简单的 HTML 页面
class PageHandler <: HttpRequestHandler {
    public func handle(httpContext: HttpContext): Unit {
        httpContext.responseBuilder.body("<html></html>")
    }
}

main () {
    // 1. 构建 Server 实例
    let server = ServerBuilder()
                        .addr("127.0.0.1")
                        .port(8080)
                        .distributor(NaiveDistributor()) // 自定义分发器
                        .build()
    // 2. 启动服务
    server.serve()
}
```

## 自定义 server 网络配置

<!-- compile -->

```cangjie
import std.fs.*
import net.tls.*
import crypto.x509.{X509Certificate, PrivateKey}
import net.http.*

//该程序需要用户配置存在且合法的文件路径才能执行
main () {
    // 1. 自定义配置
    // tcp 配置
    var transportCfg = TransportConfig()
    transportCfg.readBufferSize = 8192
    // tls 配置 需要传入配套的证书与私钥文件路径
    let pem0 = String.fromUtf8(File("/certPath", OpenOption.Open(true, false)).readToEnd())
    let pem02 = String.fromUtf8(File("/keyPath", OpenOption.Open(true, false)).readToEnd())
    var tlsConfig = TlsServerConfig(X509Certificate.decodeFromPem(pem0), PrivateKey.decodeFromPem(pem02))
    tlsConfig.supportedAlpnProtocols = ["h2"]
    // 2. 构建 Server 实例
    let server = ServerBuilder()
                       .addr("127.0.0.1")
                       .port(8080)
                       .transportConfig(transportCfg)
                       .tlsConfig(tlsConfig)
                       .headerTableSize(10 * 1024)
                       .maxRequestHeaderSize(1024 * 1024)
                       .build()
    // 3. 注册 HttpRequestHandler
    server.distributor.register("/index", {httpContext =>
        httpContext.responseBuilder.body("Hello 仓颉!")
    })
    // 4. 启动服务
    server.serve()
}
```

## response中的 chunked与trailer

<!-- compile -->

```cangjie
import net.http.*
import std.io.*
import std.collection.HashMap

func checksum(chunk: Array<UInt8>): Int64 {
    var sum = 0
    for (i in chunk) {
        if (i == UInt8(UInt32(r'\n'))) {
            sum += 1
        }
    }
    return sum / 2
}

main () {
    // 1. 构建 Server 实例
    let server = ServerBuilder()
                        .addr("127.0.0.1")
                        .port(8080)
                        .build()
    // 2. 注册 HttpRequestHandler
    server.distributor.register("/index", {httpContext =>
        let responseBuilder = httpContext.responseBuilder
        responseBuilder.header("transfer-encoding", "chunked") // 设置response头
        responseBuilder.header("trailer", "checkSum")
        let writer = HttpResponseWriter(httpContext)
        var sum = 0
        for (_ in 0..10) {
            let chunk = Array<UInt8>(10, item: 0)
            sum += checksum(chunk)
            writer.write(chunk) // 立即发送
        }
        responseBuilder.trailer("checkSum", "${sum}") // handler结束后发送
    })
    // 3. 启动服务
    server.serve()
}
```

## 处理重定向 request

<!-- compile -->

```cangjie
import net.http.*

main () {
    // 1. 构建 Server 实例
    let server = ServerBuilder()
                        .addr("127.0.0.1")
                        .port(8080)
                        .build()
    // 2. 注册 HttpRequestHandler
    server.distributor.register("/redirecta",RedirectHandler("/movedsource", 308))
    server.distributor.register("/redirectb",RedirectHandler("http://www.example.com", 308))
    // 3. 启动服务
    server.serve()
}
```

## tls 证书热加载

<!-- compile -->

```cangjie
import std.fs.*
import net.tls.*
import crypto.x509.{X509Certificate, PrivateKey}
import net.http.*

//该程序需要用户配置存在且合法的文件路径才能执行
main() {
    // 1. tls 配置
    let pem0 = String.fromUtf8(File("/certPath", OpenOption.Open(true, false)).readToEnd())
    let pem02 = String.fromUtf8(File("/keyPath", OpenOption.Open(true, false)).readToEnd())
    var tlsConfig = TlsServerConfig(X509Certificate.decodeFromPem(pem0), PrivateKey.decodeFromPem(pem02))
    tlsConfig.supportedAlpnProtocols = ["http/1.1"]
    let pem = String.fromUtf8(File("/rootCerPath", OpenOption.Open(true, false)).readToEnd())
    tlsConfig.verifyMode = CustomCA(X509Certificate.decodeFromPem(pem))
    // 2. 构建 Server 实例，并启动服务
    let server = ServerBuilder()
                        .addr("127.0.0.1")
                        .port(8080)
                        .tlsConfig(tlsConfig)
                        .build()
    spawn {
        server.serve()
    }
    // 3. 更新 tls 证书和私钥，之后收到的 request将使用新的证书和私钥
    server.updateCert("/newCerPath", "/newKeyPath")
    // 4. 更新 CA， 双向认证时使用，之后收到的 request将使用新的CA
    server.updateCA("/newRootCerPath")
}
```

## server push

仅用于 HTTP/2

client:

<!-- compile -->

```cangjie
import std.fs.*
import std.collection.ArrayList
import net.tls.*
import crypto.x509.X509Certificate
import net.http.*

//该程序需要用户配置存在且合法的文件路径才能执行
// client：
main() {
    // 1. tls 配置
    var tlsConfig = TlsClientConfig()
    let pem = String.fromUtf8(File("/rootCerPath", OpenOption.Open(true, false)).readToEnd())
    tlsConfig.verifyMode = CustomCA(X509Certificate.decodeFromPem(pem))
    tlsConfig.alpnProtocolsList = ["h2"]
    // 2. 构建 Client 实例
    let client = ClientBuilder()
                    .tlsConfig(tlsConfig)
                    .build()
    // 3. 发送 request，收response
    let response = client.get("https://example.com/index.html")
    // 4. 收 pushResponse，此例中相当于 client.get("http://example.com/picture.png") 的response
    let pushResponses: Option<ArrayList<HttpResponse>> = response.getPush()
    client.close()
}
```

server:

<!-- compile -->

```cangjie
import std.fs.*
import net.tls.*
import crypto.x509.{X509Certificate, PrivateKey}
import net.http.*

//该程序需要用户配置存在且合法的文件路径才能执行
main() {
    // 1. tls 配置
    let pem0 = String.fromUtf8(File("/certPath", OpenOption.Open(true, false)).readToEnd())
    let pem02 = String.fromUtf8(File("/keyPath", OpenOption.Open(true, false)).readToEnd())
    var tlsConfig = TlsServerConfig(X509Certificate.decodeFromPem(pem0), PrivateKey.decodeFromPem(pem02))
    tlsConfig.supportedAlpnProtocols = ["h2"]
    // 2. 构建 Server 实例
    let server = ServerBuilder()
                    .addr("127.0.0.1")
                    .port(8080)
                    .tlsConfig(tlsConfig)
                    .build()
    // 3. 注册原 request 的 handler
    server.distributor.register("/index.html", {httpContext =>
        let pusher = HttpResponsePusher.getPusher(httpContext)
        match (pusher) {
            case Some(pusher) =>
                pusher.push("/picture.png", "GET", httpContext.request.headers)
            case None =>
                ()
        }

    })
    // 4. 注册 pushRequest 的 handler
    server.distributor.register("/picture.png", {httpContext =>
        httpContext.responseBuilder.body("picture.png")
    })
    // 4. 启动服务
    server.serve()
}
```
