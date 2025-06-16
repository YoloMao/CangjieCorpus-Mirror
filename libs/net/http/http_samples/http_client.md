# client

## Hello World
<!-- compile -->

```cangjie
import net.http.*

main () {
    // 1. 构建 client 实例
    let client = ClientBuilder().build()
    // 2. 发送 request
    let rsp = client.get("http://example.com/hello")
    // 3. 读取response
    println(rsp)
    // 4. 关闭连接
    client.close()
}
```

运行结果如下：

```text
HTTP/1.1 200 OK
accept-ranges: bytes
age: 258597
cache-control: max-age=604800
content-type: text/html
date: Wed, 05 Jun 2024 02:19:26 GMT
etag: "3147526947"
expires: Wed, 12 Jun 2024 02:19:26 GMT
last-modified: Thu, 17 Oct 2019 07:18:26 GMT
server: ECAcc (lac/55A4)
vary: Accept-Encoding
x-cache: HIT
content-length: 1256
connection: close

body size: 1256
```

## 自定义 client 网络配置
<!-- compile -->

```cangjie
import std.socket.{TcpSocket, SocketAddress}
import std.convert.Parsable
import std.fs.*
import net.tls.*
import crypto.x509.X509Certificate
import net.http.*

//该程序需要用户配置存在且合法的文件路径才能执行
main () {
    // 1. 自定义配置
    // tls 配置
    var tlsConfig = TlsClientConfig()
    let pem = String.fromUtf8(File("/rootCerPath", OpenOption.Open(true, false)).readToEnd())
    tlsConfig.verifyMode = CustomCA(X509Certificate.decodeFromPem(pem))
    tlsConfig.alpnProtocolsList = ["h2"]
    // connector
    let TcpSocketConnector = { sa: SocketAddress =>
        let socket = TcpSocket(sa)
        socket.connect()
        return socket
    }
    // 2. 构建 client 实例
    let client = ClientBuilder()
                      .tlsConfig(tlsConfig)
                      .enablePush(false)
                      .connector(TcpSocketConnector)
                      .build()
    // 3. 发送 request
    let rsp = client.get("https://example.com/hello")
    // 4. 读取response
    let buf = Array<UInt8>(1024, item: 0)
    let len = rsp.body.read(buf)
    println(String.fromUtf8(buf.slice(0, len)))
    // 5. 关闭连接
    client.close()
}
```

## request中的 chunked 与 trailer
<!-- compile -->

```cangjie
import std.io.*
import std.fs.*
import net.http.*

func checksum(chunk: Array<UInt8>): Int64 {
    var sum = 0
    for (i in chunk) {
        if (i == b'\n') {
            sum += 1
        }
    }
    return sum / 2
}

//该程序需要用户配置存在且合法的文件路径才能执行
main () {
    // 1. 构建 client 实例
    let client = ClientBuilder().build()
    var requestBuilder = HttpRequestBuilder()
    let file = File("./res.jpg", OpenOption.Open(true, false))
    let sum = checksum(file.readToEnd())
    let req = requestBuilder
                   .method("PUT")
                   .url("https://example.com/src/")
                   .header("Transfer-Encoding","chunked")
                   .header("Trailer","checksum")
                   .body(FileBody("./res.jpg"))
                   .trailer("checksum", sum.toString())
                   .build()
    let rsp = client.send(req)
    println(rsp)
    client.close()
}

class FileBody <: InputStream {
    var file: File
    init(path: String) { file = File(path, OpenOption.Open(true, false))}
    public func read(buf: Array<UInt8>): Int64 {
        file.read(buf)
    }
}
```

## 配置代理
<!-- compile -->

```cangjie
import net.http.*

main () {
    // 1. 构建 client 实例
    let client = ClientBuilder()
                      .httpProxy("http://192.168.0.1:8080")
                      .build()
    // 2. 发送 request，所有 request都会被发送至192.168.0.1地址的8080端口，而不是example.com
    let rsp = client.get("http://example.com/hello")
    // 3. 读取response
    println(rsp)
    // 4. 关闭连接
    client.close()
}
```
