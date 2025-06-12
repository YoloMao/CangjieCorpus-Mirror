# 结构体

## struct OptionLevel

```cangjie
public struct OptionLevel {
    public static const ICMP: Int32
    public static const IP: Int32
    public static const RAW: Int32
    public static const SOCKET: Int32
    public static const TCP: Int32
    public static const UDP: Int32
}
```

功能：提供了常用的套接字选项级别。

### static const ICMP

```cangjie
public static const ICMP: Int32
```

功能：控制 `ICMP` 协议行为的套接字选项级别。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const IP

```cangjie
public static const IP: Int32
```

功能：控制 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 协议行为的套接字选项级别。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const RAW

```cangjie
public static const RAW: Int32
```

功能：控制 `RAW` 协议行为的套接字选项级别。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SOCKET

```cangjie
public static const SOCKET: Int32
```

功能：控制基本套接字行为的套接字选项级别。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const TCP

```cangjie
public static const TCP: Int32
```

功能：控制 `TCP` 协议行为的套接字选项级别。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const UDP

```cangjie
public static const UDP: Int32
```

功能：控制 `UDP` 协议行为的套接字选项级别。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## struct OptionName

```cangjie
public struct OptionName {
    public static const IP_HDRINCL: Int32
    public static const IP_TOS: Int32
    public static const IP_TTL: Int32
    public static const SO_ACCEPTCONN: Int32
    public static const SO_BROADCAST: Int32
    public static const SO_DEBUG: Int32
    public static const SO_DONTROUTE: Int32
    public static const SO_ERROR: Int32
    public static const SO_KEEPALIVE: Int32
    public static const SO_LINGER: Int32
    public static const SO_OOBINLINE: Int32
    public static const SO_RCVBUF: Int32
    public static const SO_RCVTIMEO: Int32
    public static const SO_REUSEADDR: Int32
    public static const SO_SNDBUF: Int32
    public static const SO_SNDTIMEO: Int32
    public static const TCP_KEEPCNT: Int32
    public static const TCP_KEEPIDLE: Int32
    public static const TCP_KEEPINTVL: Int32
    public static const TCP_NODELAY: Int32
}
```

功能：提供了常用的套接字选项。

### static const IP_HDRINCL

```cangjie
public static const IP_HDRINCL: Int32
```

功能：用于在发送数据包时指定 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 头部是否由应用程序提供的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const IP_TOS

```cangjie
public static const IP_TOS: Int32
```

功能：用于指定数据包服务类型和优先级的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const IP_TTL

```cangjie
public static const IP_TTL: Int32
```

功能：用于限制[IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip)数据包在网络中传输最大跳数的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_ACCEPTCONN

```cangjie
public static const SO_ACCEPTCONN: Int32
```

功能：用于查询套接字是否处于监听状态的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_BROADCAST

```cangjie
public static const SO_BROADCAST: Int32
```

功能：用于设置套接字是否允许发送广播消息的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_DEBUG

```cangjie
public static const SO_DEBUG: Int32
```

功能：用于启用或禁用调试模式的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_DONTROUTE

```cangjie
public static const SO_DONTROUTE: Int32
```

功能：用于在连接套接字时，不路由套接字数据包的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_ERROR

```cangjie
public static const SO_ERROR: Int32
```

功能：获取和清除套接字上错误状态的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_KEEPALIVE

```cangjie
public static const SO_KEEPALIVE: Int32
```

功能：用于检测 `TCP` 连接是否仍然处于活动状态的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_LINGER

```cangjie
public static const SO_LINGER: Int32
```

功能：用于设置套接字关闭时行为的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_OOBINLINE

```cangjie
public static const SO_OOBINLINE: Int32
```

功能：用于控制接收带外数据方式的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_RCVBUF

```cangjie
public static const SO_RCVBUF: Int32
```

功能：用于设置套接字接收缓冲区大小的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_RCVTIMEO

```cangjie
public static const SO_RCVTIMEO: Int32
```

功能：用于设置套接字接收数据超时时间的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_REUSEADDR

```cangjie
public static const SO_REUSEADDR: Int32
```

功能：用于在套接字关闭后立即释放其绑定端口，以便其他套接字可以立即绑定该端口的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_SNDBUF

```cangjie
public static const SO_SNDBUF: Int32
```

功能：用于设置套接字发送缓冲区大小的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const SO_SNDTIMEO

```cangjie
public static const SO_SNDTIMEO: Int32
```

功能：用于设置套接字发送数据超时时间的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const TCP_KEEPCNT

```cangjie
public static const TCP_KEEPCNT: Int32
```

功能：用于控制 TCP 连接中发送保持存活探测报文次数的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const TCP_KEEPIDLE

```cangjie
public static const TCP_KEEPIDLE: Int32
```

功能：用于设置在没有收到对端确认的情况下，`TCP` 保持连接最大次数的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const TCP_KEEPINTVL

```cangjie
public static const TCP_KEEPINTVL: Int32
```

功能：用于设置 `TCP` 保持连接时发送探测报文时间间隔的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### static const TCP_NODELAY

```cangjie
public static const TCP_NODELAY: Int32
```

功能：用于控制 `TCP` 协议延迟行为的套接字选项。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## struct ProtocolType

```cangjie
public struct ProtocolType <: Equatable<ProtocolType> & ToString & Hashable {
    public static let ICMP: ProtocolType
    public static let IPV4: ProtocolType
    public static let IPV6: ProtocolType
    public static let RAW: ProtocolType
    public static let TCP: ProtocolType
    public static let UDP: ProtocolType
    public static let Unspecified: ProtocolType
    public init(protocol: Int32)
}
```

功能：提供了常用的套接字协议，以及通过指定 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值来构建套接字协议的功能。

父类型：

- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[ProtocolType](#struct-protocoltype)>
- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)

### static let ICMP

```cangjie
public static let ICMP: ProtocolType
```

功能：指定协议类型为 `ICMP`。

类型：[ProtocolType](socket_package_structs.md#struct-protocoltype)

### static let IPV4

```cangjie
public static let IPV4: ProtocolType
```

功能：指定协议类型为 `IPv4` 。

类型：[ProtocolType](socket_package_structs.md#struct-protocoltype)

### static let IPV6

```cangjie
public static let IPV6: ProtocolType
```

功能：指定协议类型为 `IPv6`。

类型：[ProtocolType](socket_package_structs.md#struct-protocoltype)

### static let RAW

```cangjie
public static let RAW: ProtocolType
```

功能：指定协议类型为 `RAW`。

类型：[ProtocolType](socket_package_structs.md#struct-protocoltype)

### static let TCP

```cangjie
public static let TCP: ProtocolType
```

功能：指定协议类型为 `TCP`。

类型：[ProtocolType](socket_package_structs.md#struct-protocoltype)

### static let UDP

```cangjie
public static let UDP: ProtocolType
```

功能：指定协议类型为 `UDP`。

类型：[ProtocolType](socket_package_structs.md#struct-protocoltype)

### static let Unspecified

```cangjie
public static let Unspecified: ProtocolType
```

功能：不指定协议类型。

类型：[ProtocolType](socket_package_structs.md#struct-protocoltype)

### init(Int32)

```cangjie
public init(protocol: Int32)
```

功能：通过指定套接字协议值创建协议。

参数：

- protocol: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 套接字协议值。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：返回当前 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：返回当前 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例的字符串表示。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 当前 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例的字符串表示。

### operator func !=(ProtocolType)

```cangjie
public operator func !=(r: ProtocolType): Bool
```

功能：判断两个 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例是否不等。

参数：

- r: [ProtocolType](socket_package_structs.md#struct-protocoltype) - 参与比较的 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 当二者代表的 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值不等时，返回 `true`；否则，返回 `false`。

### operator func ==(ProtocolType)

```cangjie
public operator func ==(r: ProtocolType): Bool
```

功能：判断两个 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例是否相等。

参数：

- r: [ProtocolType](socket_package_structs.md#struct-protocoltype) - 参与比较的 [ProtocolType](socket_package_structs.md#struct-protocoltype) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 当二者代表的 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值相等时，返回 `true`；否则，返回 `false`。

## struct RawAddress

```cangjie
public struct RawAddress {
    public init(addr: Array<Byte>)
}
```

功能：提供了 [RawSocket](socket_package_classes.md#class-rawsocket) 的通信地址创建和获取功能。

### prop addr

```cangjie
public prop addr: Array<Byte>
```

功能：获取地址。

类型：[Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)>

### init(Array\<Byte>)

```cangjie
public init(addr: Array<Byte>)
```

功能：根据字节数组创建地址。

参数：

- addr: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储地址的字节数组。

## struct SocketDomain

```cangjie
public struct SocketDomain <: Equatable<SocketDomain> & ToString & Hashable {
    public static let IPV4: SocketDomain
    public static let IPV6: SocketDomain
    public static let NETLINK: SocketDomain
    public static let PACKET: SocketDomain
    public static let UNIX: SocketDomain
    public init(domain: Int32)
}
```

功能：提供了常用的套接字通信域，以及通过指定 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值来构建套接字通信域的功能。

父类型：

- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[SocketDomain](#struct-socketdomain)>
- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)

### static let IPV4

```cangjie
public static let IPV4: SocketDomain
```

功能：`IPv4` 通信域。

类型：[SocketDomain](socket_package_structs.md#struct-socketdomain)

### static let IPV6

```cangjie
public static let IPV6: SocketDomain
```

功能：`IPv6` 通信域。

类型：[SocketDomain](socket_package_structs.md#struct-socketdomain)

### static let NETLINK

```cangjie
public static let NETLINK: SocketDomain
```

功能：内核和用户空间进程之间通信。

> **注意：**
>
> - 该常量在 Windows 平台不提供。

类型：[SocketDomain](socket_package_structs.md#struct-socketdomain)

### static let PACKET

```cangjie
public static let PACKET: SocketDomain
```

功能：允许用户空间程序直接访问网络数据包。

> **注意：**
>
> - 该常量在 Windows 平台不提供。

类型：[SocketDomain](socket_package_structs.md#struct-socketdomain)

### static let UNIX

```cangjie
public static let UNIX: SocketDomain
```

功能：本机通信。

类型：[SocketDomain](socket_package_structs.md#struct-socketdomain)

### init(Int32)

```cangjie
public init(domain: Int32)
```

功能：根据指定通信域值创建套接字通信域。

参数：

- domain: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 通信域值。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：返回当前 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：返回当前 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例的字符串表示。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 当前 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例的字符串表示。

### operator func !=(SocketDomain)

```cangjie
public operator func !=(r: SocketDomain): Bool
```

功能：比较两个 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例是否不等。

参数：

- r: [SocketDomain](socket_package_structs.md#struct-socketdomain) - 参与比较的 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 当二者代表的 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值不等时，返回 `true`；否则，返回 `false`。

### operator func ==(SocketDomain)

```cangjie
public operator func ==(r: SocketDomain): Bool
```

功能：比较两个 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例是否相等。

参数：

- r: [SocketDomain](socket_package_structs.md#struct-socketdomain) - 参与比较的 [SocketDomain](socket_package_structs.md#struct-socketdomain) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 当二者代表的 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值相等时，返回 `true`；否则，返回 `false`。

## struct SocketKeepAliveConfig

```cangjie
public struct SocketKeepAliveConfig <: ToString & Equatable<SocketKeepAliveConfig> {
    public let count: UInt32
    public let idle: Duration
    public let interval: Duration
    public init(idle!: Duration = Duration.second * 45, interval!: Duration = Duration.second * 5, count!: UInt32 = 5)
}
```

功能：TCP KeepAlive 属性配置。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[SocketKeepAliveConfig](#struct-socketkeepaliveconfig)>

### let count

```cangjie
public let count: UInt32
```

功能：查询连接是否失效的报文个数。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

### let idle

```cangjie
public let idle: Duration
```

功能：允许连接空闲的时长，空闲超长将关闭连接。

类型：[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

### let interval

```cangjie
public let interval: Duration
```

功能：保活报文发送周期。

类型：[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

### init(Duration, Duration, UInt32)

```cangjie
public init(idle!: Duration = Duration.second * 45, interval!: Duration = Duration.second * 5, count!: UInt32 = 5)
```

功能：初始化 [SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig) 实例对象。

参数：

- idle!: [Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 允许空闲的时长，默认 45 秒。
- interval!: [Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 保活报文发送周期，默认 45 秒。
- [count](../../collection/collection_package_api/collection_package_function.md#func-counttiterablet)!: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 查询连接是否失效的报文个数， 默认 5 个。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当配置为空闲状态或设置间隔小于 0 时，抛出异常。

### func toString()

```cangjie
public override func toString(): String
```

功能：将 TCP KeepAlive 属性配置转换为字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的字符串。

### operator func !=(SocketKeepAliveConfig)

```cangjie
public override operator func !=(other: SocketKeepAliveConfig): Bool
```

功能：判断两个 [SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig) 实例是否不等。

参数：

- other: [SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig) - 参与比较的 [SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果不等，则返回 `true`；否则，返回 `false`。

### operator func ==(SocketKeepAliveConfig)

```cangjie
public override operator func ==(other: SocketKeepAliveConfig): Bool
```

功能：判断两个 [SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig) 实例是否相等。

参数：

- other: [SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig) - 参与比较的 [SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果相等，则返回 `true`；否则，返回 `false`。

## struct SocketOptions

```cangjie
public struct SocketOptions {
    public static const IPPROTO_TCP
    public static const IPPROTO_UDP
    public static const SOL_SOCKET
    public static const SO_BINDTODEVICE
    public static const SO_KEEPALIVE
    public static const SO_LINGER
    public static const SO_RCVBUF
    public static const SO_REUSEADDR
    public static const SO_REUSEPORT
    public static const SO_SNDBUF
    public static const TCP_NODELAY
    public static const TCP_QUICKACK
}
```

功能：[SocketOptions](socket_package_structs.md#struct-socketoptions) 存储了设置套接字选项的一些参数常量方便后续调用。

### const IPPROTO_TCP

```cangjie
public static const IPPROTO_TCP: Int32 = IPPROTO_TCP
```

功能：常数，用于将套接字选项的 `level` 层级设为 `IPPROTO_TCP`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const IPPROTO_UDP

```cangjie
public static const IPPROTO_UDP: Int32 = IPPROTO_UDP
```

功能：常数，用于将套接字选项的 `level` 层级设为 `IPPROTO_UDP`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SOL_SOCKET

```cangjie
public static const SOL_SOCKET: Int32 = SOL_SOCKET
```

功能：常数，用于将套接字选项的 `level` 层级设为 `SOL_SOCKET`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SO_BINDTODEVICE

```cangjie
public static const SO_BINDTODEVICE: Int32 = SOCK_BINDTODEVICE
```

功能：常数，用于将套接字选项的 `optname` 设为 `SO_BINDTODEVICE`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SO_KEEPALIVE

```cangjie
public static const SO_KEEPALIVE: Int32 = SOCK_KEEPALIVE
```

功能：常数，用于将套接字选项的 `optname` 设为 `SO_KEEPALIVE`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SO_LINGER

```cangjie
public static const SO_LINGER: Int32 = SOCK_LINGER
```

功能：常数，用于将套接字选项的 `optname` 设为 `SO_LINGER`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SO_RCVBUF

```cangjie
public static const SO_RCVBUF: Int32 = SOCK_RCVBUF
```

功能：常数，用于将套接字选项的 `optname` 设为 `SO_RCVBUF`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SO_REUSEADDR

```cangjie
public static const SO_REUSEADDR: Int32 = SOCK_REUSEADDR
```

功能：常数，用于将套接字选项的 `optname` 设为 `SO_REUSEADDR`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SO_REUSEPORT

```cangjie
public static const SO_REUSEPORT: Int32 = SOCK_REUSEPORT
```

功能：常数，用于将套接字选项的 `optname` 设为 `SO_REUSEPORT`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const SO_SNDBUF

```cangjie
public static const SO_SNDBUF: Int32 = SOCK_SNDBUF
```

功能：常数，用于将套接字选项的 `optname` 设为 `SO_SNDBUF`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const TCP_NODELAY

```cangjie
public static const TCP_NODELAY: Int32 = SOCK_TCP_NODELAY
```

功能：常数，用于将套接字选项的 `optname` 设为 `TCP_NODELAY`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### const TCP_QUICKACK

```cangjie
public static const TCP_QUICKACK: Int32 = SOCK_TCP_QUICKACK
```

功能：常数，用于将套接字选项的 `optname` 设为 `TCP_QUICKACK`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## struct SocketType

```cangjie
public struct SocketType <: Equatable<SocketType> & ToString & Hashable {
    public static let DATAGRAM: SocketType
    public static let RAW: SocketType
    public static let SEQPACKET: SocketType
    public static let STREAM: SocketType
    public init(`type`: Int32)
}
```

功能：提供了常用的套接字类型，以及通过指定 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值来构建套接字类型的功能。

父类型：

- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[SocketType](#struct-sockettype)>
- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)

### static let DATAGRAM

```cangjie
public static let DATAGRAM: SocketType
```

功能：数据报套接字类型。

类型：[SocketType](socket_package_structs.md#struct-sockettype)

### static let RAW

```cangjie
public static let RAW: SocketType
```

功能：原始套接字类型。

类型：[SocketType](socket_package_structs.md#struct-sockettype)

### static let SEQPACKET

```cangjie
public static let SEQPACKET: SocketType
```

功能：有序数据包套接字类型。

类型：[SocketType](socket_package_structs.md#struct-sockettype)

### static let STREAM

```cangjie
public static let STREAM: SocketType
```

功能：流式套接字类型。

类型：[SocketType](socket_package_structs.md#struct-sockettype)

### init(Int32)

```cangjie
public init(`type`: Int32)
```

功能：通过指定套接字类型值创建套接字类型。

参数：

- \`type`: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 套接字类型值。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：返回当前 [SocketType](socket_package_structs.md#struct-sockettype) 实例的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [SocketType](socket_package_structs.md#struct-sockettype) 实例的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：返回当前 [SocketType](socket_package_structs.md#struct-sockettype) 实例的字符串表示。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 当前 [SocketType](socket_package_structs.md#struct-sockettype) 实例的字符串表示。

### operator func !=(SocketType)

```cangjie
public operator func !=(r: SocketType): Bool
```

功能：判断两个 [SocketType](socket_package_structs.md#struct-sockettype) 实例是否不等。

参数：

- r: [SocketType](socket_package_structs.md#struct-sockettype) - 参与比较的 [SocketType](socket_package_structs.md#struct-sockettype) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 当二者代表的 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值不等时，返回 `true`；否则，返回 `false`。

### operator func ==(SocketType)

```cangjie
public operator func ==(r: SocketType): Bool
```

功能：判断两个 [SocketType](socket_package_structs.md#struct-sockettype) 实例是否相等。

参数：

- r: [SocketType](socket_package_structs.md#struct-sockettype) - 参与比较的 [SocketType](socket_package_structs.md#struct-sockettype) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 当二者代表的 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 值相等时，返回 `true`；否则，返回 `false`。
