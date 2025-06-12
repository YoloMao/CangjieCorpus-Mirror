# net 模块

>  **注意：**
>
> 当前暂不支持通过 import net 直接导入 net 模块，否则，在编译阶段会报无法找到 net 包的错误（error: can not find package 'net'） 。建议当前使用导入 net 子包的形式使用 net 模块。

## net 功能介绍

net 模块提供了网络通信相关的能力。

在 http 应用层，支持基于 http 相关协议的 http/1.1，http/2，websocket 客户端和服务端的开发。

在 tls 传输层，支持基于 TLS 1.2 和 TLS 1.3 协议的加密网络通信。

## net 模块的包列表

net 模块提供了如下包：

|                              包名                              |    功能    |
| -------------------------------------------------------------- | --------- |
| [http](./http/http_package_overview.md)                        | http 包提供 HTTP/1.1，HTTP/2，WebSocket 协议的 server、client 端实现。 |
| [tls](./tls/tls_package_overview.md)                        | tls 包用于进行安全加密的网络通信，提供创建 TLS 服务器、基于协议进行 TLS 握手、收发加密数据、恢复 TLS 会话等能力。 |
