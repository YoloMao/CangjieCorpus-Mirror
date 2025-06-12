# log
<!-- compile -->

```cangjie
import std.log.*
import net.http.*

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
    // 3. 开启日志
    server.logger.level = DEBUG
    // client端通过client.logger.level = DEBUG 开启
    // 4. 启动服务
    server.serve()
}
```

运行结果如下所示：

```text
2024/01/25 17:23:54.344205 DEBUG Logger [Server#serve] bindAndListen(127.0.0.1, 8080)
```
