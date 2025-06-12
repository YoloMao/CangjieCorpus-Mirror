# std.socket 包

## 功能介绍

socket 包用于进行网络通信，提供启动 `Socket` 服务器、连接 `Socket` 服务器、发送数据、接收数据等功能。

我们支持 UDP/TCP/UDS 三种 `Socket` 类型，用户可按需选用。

UDP(User Datagram Protocol，用户数据报协议)是一种无连接的传输协议，它不提供可靠性和流量控制，但是具有较低的延迟和较小的网络开销。UDP协议主要用于一些实时性要求高的应用场景，例如视频直播、在线游戏等。

TCP（Transmission Control Protocol，传输控制协议）是一种面向连接的、可靠的传输协议。它提供了可靠的数据传输、流量控制、拥塞控制、错误检测和流量管理等功能，是互联网中最常用的传输协议之一。

UDS（Unix Domain Socket）是一种用于在同一台计算机上的进程之间进行通信的机制。与网络套接字不同，UDS不需要网络协议栈和网络设备，因此可以更快地进行通信，具有更低的延迟和更高的吞吐量。

如下为本库提供 `Socket` 的类继承关系：

```cangjie
Hierarchy
 Resource
 ├StreamingSocket
 │   ├TcpSocket
 │   └UnixSocket
 │
 ├DatagramSocket
 │   ├UdpSocket
 │   └UnixDatagramSocket
 │
 └ServerSocket
     ├TcpServerSocket
     └UnixServerSocket
```

## API 列表

### 常量&变量

|              常量&变量名          |           功能           |
| --------------------------- | ------------------------ |
| [IPV4_ALL_ROUTER](./socket_package_api/socket_package_constants_vars.md#let-ipv4_all_router) | IPv4 预留的组播地址。 |
| [IPV4_ALL_SYSTEM](./socket_package_api/socket_package_constants_vars.md#let-ipv4_all_system) | IPv4 多播地址。 |
| [IPV4_BROADCAST](./socket_package_api/socket_package_constants_vars.md#let-ipv4_broadcast) | IPv4 广播地址。 |
| [IPV4_LOCAL_HOST](./socket_package_api/socket_package_constants_vars.md#let-ipv4_local_host) | IPv4 本地地址。 |
| [IPV4_ZERO](./socket_package_api/socket_package_constants_vars.md#let-ipv4_zero) | IPv4 通用地址。 |
| [IPV6_INTERFACE_LOCAL_ALL_NODES](./socket_package_api/socket_package_constants_vars.md#let-ipv6_interface_local_all_nodes) | IPv6 在节点本地范围的所有节点多播地址。 |
| [IPV6_LINK_LOCAL_ALL_NODES](./socket_package_api/socket_package_constants_vars.md#let-ipv6_link_local_all_nodes) | IPv6 在链路本地范围的所有节点多播地址。 |
| [IPV6_LINK_LOCAL_ALL_ROUTERS](./socket_package_api/socket_package_constants_vars.md#let-ipv6_link_local_all_routers) | IPv6 链路本地范围的所有路由器多播地址。 |
| [IPV6_LOOPBACK](./socket_package_api/socket_package_constants_vars.md#let-ipv6_loopback) | IPv6 环回地址（本地地址）。 |
| [IPV6_ZERO](./socket_package_api/socket_package_constants_vars.md#let-ipv6_zero) | IPv6 通用地址。 |

### 接口

|              接口名          |           功能           |
| --------------------------- | ------------------------ |
| [DatagramSocket](./socket_package_api/socket_package_interfaces.md#interface-datagramsocket) | `DatagramSocket` 是一种接收和读取数据包的套接字。 |
| [ServerSocket](./socket_package_api/socket_package_interfaces.md#interface-serversocket) | 提供服务端的 `Socket` 需要的接口。 |
| [StreamingSocket](./socket_package_api/socket_package_interfaces.md#interface-streamingsocket) | 双工流模式下的运行的 `Socket`，可被读写。 |

### 类

|              类名          |           功能           |
| --------------------------- | ------------------------ |
| [IPMask](./socket_package_api/socket_package_classes.md#class-ipmask) | IP 掩码，操作 IP 地址和路由地址。 |
| [RawSocket](./socket_package_api/socket_package_classes.md#class-rawsocket) | `RawSocket` 提供了套接字的基本功能。 |
| [SocketAddress](./socket_package_api/socket_package_classes.md#class-socketaddress) | 具有特定类型、地址和端口的套接字地址。 |
| [SocketAddressWithMask](./socket_package_api/socket_package_classes.md#class-socketaddresswithmask) | 提供带有掩码的 `SocketAddress`。 |
| [TcpServerSocket](./socket_package_api/socket_package_classes.md#class-tcpserversocket) | 监听 TCP 连接的服务端。 |
| [TcpSocket](./socket_package_api/socket_package_classes.md#class-tcpsocket) | 请求 TCP 连接的客户端。|
| [UdpSocket](./socket_package_api/socket_package_classes.md#class-udpsocket) | 提供 udp 报文通信。 |
| [UnixDatagramSocket](./socket_package_api/socket_package_classes.md#class-unixdatagramsocket) | 提供基于数据包的主机通讯能力。 |
| [UnixServerSocket](./socket_package_api/socket_package_classes.md#class-unixserversocket) | 提供基于双工流的主机通讯服务端。 |
| [UnixSocket](./socket_package_api/socket_package_classes.md#class-unixsocket) | 提供基于双工流的主机通讯客户端。 |

### 枚举

|              枚举名          |           功能           |
| --------------------------- | ------------------------ |
| [SocketAddressKind](./socket_package_api/socket_package_enums.md#enum-socketaddresskind) | 互联网通信协议种类。 |
| [SocketNet](./socket_package_api/socket_package_enums.md#enum-socketnet) | 传输层协议类型。 |

### 结构体

|              结构体名          |           功能           |
| --------------------------- | ------------------------ |
| [OptionLevel](./socket_package_api/socket_package_structs.md#struct-optionlevel) | 提供了常用的套接字选项级别。 |
| [OptionName](./socket_package_api/socket_package_structs.md#struct-optionname) | 提供了常用的套接字选项。 |
| [ProtocolType](./socket_package_api/socket_package_structs.md#struct-protocoltype) | 提供了常用的套接字协议，以及通过指定 `Int32` 值来构建套接字协议的功能。 |
| [RawAddress](./socket_package_api/socket_package_structs.md#struct-rawaddress) | 提供了 `RawSocket` 的通信地址创建和获取功能。 |
| [SocketDomain](./socket_package_api/socket_package_structs.md#struct-socketdomain) | 提供了常用的套接字通信域，以及通过指定 `Int32` 值来构建套接字通信域的功能。 |
| [SocketKeepAliveConfig](./socket_package_api/socket_package_structs.md#struct-socketkeepaliveconfig) | TCP KeepAlive 属性配置。 |
| [SocketOptions](./socket_package_api/socket_package_structs.md#struct-socketoptions) | `SocketOptions` 存储了设置套接字选项的一些参数常量方便后续调用。|
| [SocketType](./socket_package_api/socket_package_structs.md#struct-sockettype) | 提供了常用的套接字类型，以及通过指定 `Int32` 值来构建套接字类型的功能。 |

### 异常类

|              异常类名          |           功能           |
| --------------------------- | ------------------------ |
| [SocketException](./socket_package_api/socket_package_exceptions.md#class-socketexception) | 提供套接字相关的异常处理。 |
| [SocketTimeoutException](./socket_package_api/socket_package_exceptions.md#class-sockettimeoutexception) | 提供字符格式相关的异常处理。 |
