# 类

## class IPMask

```cangjie
public class IPMask <: ToString {
    public init(buf: Array<UInt8>)
    public init(ones: Int64, bits: Int64)
    public init(a: UInt8, b: UInt8, c: UInt8, d: UInt8)
}
```

功能：[IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 掩码，操作 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址和路由地址。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)

### init(Array\<UInt8>)

```cangjie
public init(buf: Array<UInt8>)
```

功能：初始化掩码值。

参数：

- buf: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)> - 掩码值。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `buf` 里的值超出阈值，不符合 IPv4/IPv6 要求时，抛出异常。

### init(Int64, Int64)

```cangjie
public init(ones: Int64, bits: Int64)
```

功能：初始化掩码值。

参数：

- ones: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 高位 1 的个数。
- bits: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - `bit` 位总个数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `bits` 值超出阈值，不符合 IPv4/IPv6 要求时，抛出异常。

### init(UInt8, UInt8, UInt8, UInt8)

```cangjie
public init(a: UInt8, b: UInt8, c: UInt8, d: UInt8)
```

功能：初始化掩码值，参数值分别是 IPv4 的 4 个字节 `a.b.c.d`。

参数：

- a: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 最高字节。
- b: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 次高字节。
- c: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 次低字节。
- d: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 最低字节。

### func size()

```cangjie
public func size(): (Int64, Int64)
```

功能：获取高位 1 的个数，以及总 `bit` 位数。

返回值：

- ([Int64](../../core/core_package_api/core_package_intrinsics.md#int64)，[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)) - 高位 1 的个数，以及总 `bit` 位数，若掩码格式不符合高位均为 1 的格式，返回 `(0, 0)`。

### func toString()

```cangjie
public func toString(): String
```

功能：将 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 掩码转换为字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的字符串。

## class RawSocket

```cangjie
public class RawSocket {
    public init(domain: SocketDomain, `type`: SocketType, protocol: ProtocolType)
}
```

功能：[RawSocket](socket_package_classes.md#class-rawsocket) 提供了套接字的基本功能。

可以访问特定通信域（domain）、类型（type）和协议（protocol）组合的套接字。Socket 包已经提供了 TCP、 UDP 等常用网络协议的支持，因此，该类型适用于其他类型的网络编程需求。

> **注意：**
>
> - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 已经验证的功能包括 TCP、UDP、UDS 以及 ICMP 协议套接字，其它类型使用上可能存在预期之外的问题。
> - 此外，由于接口的开放性，可以使用 `connect` 再 `listen` 的组合，部分场景可能存在预期外的问题。建议开发者使用时遵循正常的调用逻辑，避免产生问题。

### prop localAddr

```cangjie
public prop localAddr: RawAddress
```

功能：获取当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例的本地地址。

类型：[RawAddress](socket_package_structs.md#struct-rawaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或无法获取本地地址时，抛出异常。

### prop readTimeout

```cangjie
public mut prop readTimeout: ?Duration
```

功能：获取或设置当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例的读超时时间。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当设置的读超时时间为负时，抛出异常。

### prop remoteAddr

```cangjie
public prop remoteAddr: RawAddress
```

功能：获取当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例的对端地址。

类型：[RawAddress](socket_package_structs.md#struct-rawaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或无法获取对端地址时，抛出异常。

### prop writeTimeout

```cangjie
public mut prop writeTimeout: ?Duration
```

功能：获取或设置当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例的写超时时间。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当设置的写超时时间为负时，抛出异常。

### init(SocketDomain, SocketType, ProtocolType)

```cangjie
public init(domain: SocketDomain, `type`: SocketType, protocol: ProtocolType)
```

功能：创建特定通信域、类型、协议组合的套接字。

参数：

- domain: [SocketDomain](socket_package_structs.md#struct-socketdomain) - 通信域。
- \`type`: [SocketType](socket_package_structs.md#struct-sockettype) - 套接字类型。
- protocol: [ProtocolType](socket_package_structs.md#struct-protocoltype) - 协议类型。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当通信域、类型、协议组合无法创建套接字时，抛出异常。

### func accept(?Duration)

```cangjie
public func accept(timeout!: ?Duration = None): RawSocket
```

功能：接收当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例监听时挂起连接队列上的第一个连接请求，返回一个用于通信的 [RawSocket](socket_package_classes.md#class-rawsocket)。

参数：

- timeout!: ?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 等待连接请求的最大时间，默认值 `None` 表示一直等待。

返回值：

- [RawSocket](socket_package_classes.md#class-rawsocket) - 用于通信的新 [RawSocket](socket_package_classes.md#class-rawsocket) 实例。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或接收失败时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当等待超时时，抛出异常。

### func bind(RawAddress)

```cangjie
public func bind(addr: RawAddress): Unit
```

功能：将当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例与指定的套接字地址进行绑定。

参数：

- addr: [RawAddress](socket_package_structs.md#struct-rawaddress) - 套接字地址。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或绑定失败时，抛出异常。

### func close()

```cangjie
public func close(): Unit
```

功能：关闭当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例。

### func connect(RawAddress, ?Duration)

```cangjie
public func connect(addr: RawAddress, timeout!: ?Duration = None): Unit
```

功能：向目标地址发送连接请求。

参数：

- addr: [RawAddress](socket_package_structs.md#struct-rawaddress) - 发送连接请求的目标地址。
- timeout!: ?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 等待连接接收的最大时间，默认值 `None` 表示一直等待。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或接收失败时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当等待超时时，抛出异常。

### func getSocketOption(Int32, Int32, CPointer\<Byte>, CPointer\<Int32>)

```cangjie
public unsafe func getSocketOption(level: Int32, option: Int32, value: CPointer<Byte>, len: CPointer<Int32>): Unit
```

功能：获取套接字选项的值。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 套接字选项级别。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 套接字选项名。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 套接字选项值。
- len: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)> - 套接字选项值的长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或获取套接字选项失败时，抛出异常。

### func listen(Int32)

```cangjie
public func listen(backlog: Int32): Unit
```

功能：监听当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例绑定的地址。

参数：

- backlog: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 等待队列增长的最大长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或监听失败时，抛出异常。

### func receive(Array\<Byte>, Int32)

```cangjie
public func receive(buffer: Array<Byte>, flags: Int32): Int64
```

功能：接收来自连接对端发送的数据。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储接收数据的数组。
- flags: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 指定函数行为的标志。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 数据长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或接收数据失败时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当超过指定的读超时时间时，抛出异常。

### func receiveFrom(Array\<Byte>, Int32)

```cangjie
public func receiveFrom(buffer: Array<Byte>, flags: Int32): (RawAddress, Int64)
```

功能：接收来自其它 [RawSocket](socket_package_classes.md#class-rawsocket) 实例的数据。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储接收数据的数组。
- flags: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 指定函数行为的标志。

返回值：

- ([RawAddress](socket_package_structs.md#struct-rawaddress), [Int64](../../core/core_package_api/core_package_intrinsics.md#int64)) - 数据来源的地址和数据长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或接收数据失败时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当超过指定的读超时时间时，抛出异常。

### func send(Array\<Byte>, Int32)

```cangjie
public func send(buffer: Array<Byte>, flags: Int32): Unit
```

功能：向连接的对端发送数据。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 数据。
- flags: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 指定函数行为的标志。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或发送数据失败时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当超过指定的写超时时间时，抛出异常。

### func sendTo(RawAddress, Array\<Byte>, Int32)

```cangjie
public func sendTo(addr: RawAddress, buffer: Array<Byte>, flags: Int32): Unit
```

功能：向目标地址发送数据。若 [RawSocket](socket_package_classes.md#class-rawsocket) 是 `DATAGRAM` 类型，发送的数据包大小不允许超过 65507 字节。

参数：

- addr: [RawAddress](socket_package_structs.md#struct-rawaddress) - 发送数据的目标地址。
- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 数据。
- flags: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 指定函数行为的标志。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或发送数据失败时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当超过指定的写超时时间时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - macOS 平台下当 `connect` 被调用后调用 `sendTo`，抛出异常。

### func setSocketOption(Int32, Int32, CPointer\<Byte>, Int32)

```cangjie
public unsafe func setSocketOption(level: Int32, option: Int32, value: CPointer<Byte>, len: Int32): Unit
```

功能：设置套接字选项。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 套接字选项级别。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 套接字选项名。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 套接字选项值。
- len: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 套接字选项值的长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当前 [RawSocket](socket_package_classes.md#class-rawsocket) 实例已经关闭，或设置套接字选项失败时，抛出异常。

## class SocketAddress

```cangjie
public open class SocketAddress <: ToString & Hashable & Equatable<SocketAddress> {
    public init(kind: SocketAddressKind, address: Array<UInt8>, port: UInt16)
    public init(hostAddress: String, port: UInt16)
    public init(unixPath!: String)
}
```

功能：具有特定类型、地址和端口的套接字地址。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)
- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[SocketAddress](#class-socketaddress)>

### prop address

```cangjie
public prop address: Array<UInt8>
```

功能：获取地址。

类型：[Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)>

### prop defaultMask

```cangjie
public prop defaultMask: Option<IPMask>
```

功能：获取默认掩码。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[IPMask](socket_package_classes.md#class-ipmask)>

### prop hostAddress

```cangjie
public prop hostAddress: String
```

功能：获取主机地址。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop hostName

```cangjie
public prop hostName: Option<String>
```

功能：获取名称，不存在时返回 `None`。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>

### prop kind

```cangjie
public prop kind: SocketAddressKind
```

功能：获取地址类型。

类型：[SocketAddressKind](socket_package_enums.md#enum-socketaddresskind)

### prop port

```cangjie
public prop port: UInt16
```

功能：获取端口。

类型：[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)

### prop zone

```cangjie
public prop zone: Option<String>
```

功能：获取 IPv6 地址族。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>

### init(SocketAddressKind, Array\<UInt8>, UInt16)

```cangjie
public init(kind: SocketAddressKind, address: Array<UInt8>, port: UInt16)
```

功能：根据传入的套接字地址类型，[IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址和端口号创建 [SocketAddress](socket_package_classes.md#class-socketaddress) 实例。

参数：

- kind: [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind) - 套接字地址类型。
- address: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)> - [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址。
- port: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 端口号。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当地址长度不符合地址类型要求时，抛出异常。

### init(String)

```cangjie
public init(unixPath!: String)
```

功能：根据传入的文件地址创建 [SocketAddress](socket_package_classes.md#class-socketaddress) 实例。

参数：

- unixPath!: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 连接的文件地址。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当地址无法解析成 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 格式，或不符合地址类型要求，抛出异常。

### init(String, UInt16)

```cangjie
public init(hostAddress: String, port: UInt16)
```

功能：根据传入的 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址和端口号创建 [SocketAddress](socket_package_classes.md#class-socketaddress) 实例。

参数：

- hostAddress: [String](../../core/core_package_api/core_package_structs.md#struct-string) - [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址。
- port: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 端口号。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当地址无法解析成 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 格式，或不符合地址类型要求时，抛出异常。

### static func resolve(String, UInt64)

```cangjie
public static func resolve(domain: String, port: UInt16): ?SocketAddress
```

功能：解析域和端口，并构造 [SocketAddress](socket_package_classes.md#class-socketaddress) 的实例。

当传入 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址时，不包含 DNS 能力。当传入域名地址时，通过 `getaddrinfo` 解析得到 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址，其中优先解析 IPv4 地址，并仅返回获取到的首个 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址。

参数：

- domain: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 域。
- port: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 端口。

返回值：

- ?[SocketAddress](socket_package_classes.md#class-socketaddress) - 如果解析域和端口成功，返回 [SocketAddress](socket_package_classes.md#class-socketaddress) 实例，否则返回 `None`。

### func hashCode()

```cangjie
public open func hashCode(): Int64
```

功能：获取 `hashcode` 值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - `hashcode` 值。

### func kapString()

```cangjie
public func kapString(): String
```

功能：获取 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 协议、地址和端口字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 协议、地址和端口字符串。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当地址的大小与 IPv4 或 IPv6 不匹配时，抛出异常。

### func mask(IPMask)

```cangjie
public func mask(mask: IPMask): SocketAddressWithMask
```

功能：使用掩码处理地址。

参数：

- mask: [IPMask](socket_package_classes.md#class-ipmask) - 掩码。

返回值：

- [SocketAddressWithMask](socket_package_classes.md#class-socketaddresswithmask) - 被处理后的地址。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当掩码长度不符合地址长度时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当缓存空间不符合 IPv4/IPv6 要求时，抛出异常。

### func setHostName(String)

```cangjie
public func setHostName(name: String): Unit
```

功能：设置主机名。

### func toString()

```cangjie
public open func toString(): String
```

功能：获取地址对象字符串。

格式为："127.0.0.1:2048"， "[::]:2048"，"[212c:3742::ffff:5863:6f00]:2048" 等。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当地址不合法时，抛出异常。

### operator func !=(SocketAddress)

```cangjie
public operator func != (that: SocketAddress): Bool
```

功能：判断两个 [SocketAddress](socket_package_classes.md#class-socketaddress) 是否不相等。

参数：

- that: [SocketAddress](socket_package_classes.md#class-socketaddress) - 传入的 [SocketAddress](socket_package_classes.md#class-socketaddress)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果两个 [SocketAddress](socket_package_classes.md#class-socketaddress) 不相等，则返回 `true`；否则，返回 `false`。

### operator func ==(SocketAddress)

```cangjie
public operator func ==(that: SocketAddress): Bool
```

功能：判断两个 [SocketAddress](socket_package_classes.md#class-socketaddress) 是否相等。

参数：

- that: [SocketAddress](socket_package_classes.md#class-socketaddress) - 传入的 [SocketAddress](socket_package_classes.md#class-socketaddress)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果两个 [SocketAddress](socket_package_classes.md#class-socketaddress) 相等，则返回 `true`；否则，返回 `false`。

## class SocketAddressWithMask

```cangjie
public class SocketAddressWithMask <: SocketAddress {
    public init(kind: SocketAddressKind, address: Array<UInt8>, port: UInt16, mask: IPMask)
    public init(hostAddress: String, port: UInt16, mask: IPMask)
    public init(socketAddr: SocketAddress, mask: IPMask)
}
```

功能：提供带有掩码的 [SocketAddress](socket_package_classes.md#class-socketaddress)。

父类型：

- [SocketAddress](#class-socketaddress)

### prop ipMask

```cangjie
public mut prop ipMask: IPMask
```

功能：设置/获取 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 掩码。

类型：[IPMask](socket_package_classes.md#class-ipmask)

### init(SocketAddress, IPMask)

```cangjie
public init(socketAddr: SocketAddress, mask: IPMask)
```

功能：创建 [SocketAddressWithMask](socket_package_classes.md#class-socketaddresswithmask) 实例。

参数：

- socketAddr: [SocketAddress](socket_package_classes.md#class-socketaddress) - 地址。
- mask: [IPMask](socket_package_classes.md#class-ipmask) - 掩码。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当参数 `socketAddr` 不合法时，抛出异常。

### init(SocketAddressKind, Array\<UInt8>, UInt16, IPMask)

```cangjie
public init(kind: SocketAddressKind, address: Array<UInt8>, port: UInt16, mask: IPMask)
```

功能：创建 [SocketAddressWithMask](socket_package_classes.md#class-socketaddresswithmask) 实例。

参数：

- kind: [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind) - [SocketAddress](socket_package_classes.md#class-socketaddress) 类型。
- address: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)> - 符合 `kind` 所指定类型的地址。
- port: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 端口。
- mask: [IPMask](socket_package_classes.md#class-ipmask) - 掩码。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当参数 `address` 传入的地址不符合参数 `kind` 地址类型的要求时，抛出异常。

### init(String, UInt16, IPMask)

```cangjie
public init(hostAddress: String, port: UInt16, mask: IPMask)
```

功能：创建 [SocketAddressWithMask](socket_package_classes.md#class-socketaddresswithmask) 实例。

参数：

- hostAddress: [String](../../core/core_package_api/core_package_structs.md#struct-string) - [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址字符串。
- port: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 端口。
- mask: [IPMask](socket_package_classes.md#class-ipmask) - 掩码。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当参数 `hostAddress` 无法解析成合法的 [IP](../../../crypto/x509/x509_package_api/x509_package_type.md#type-ip) 地址时，抛出异常。

### func clone()

```cangjie
public func clone(): SocketAddressWithMask
```

功能：使用绑定的掩码处理地址，复制一个 [SocketAddressWithMask](socket_package_classes.md#class-socketaddresswithmask) 实例。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当掩码长度不符合地址长度时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当缓存长度不足时，抛出异常。

### func hashCode()

```cangjie
public override func hashCode(): Int64
```

功能：获取 [SocketAddressWithMask](socket_package_classes.md#class-socketaddresswithmask) 的 `hashcode` 值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - `hashcode` 值。

### func toString()

```cangjie
public override func toString(): String
```

功能：将 [SocketAddressWithMask](socket_package_classes.md#class-socketaddresswithmask) 转换为字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的字符串。

## class TcpServerSocket

```cangjie
public class TcpServerSocket <: ServerSocket {
    public init(bindAt!: SocketAddress)
    public init(bindAt!: UInt16)
}
```

功能：监听 TCP 连接的服务端。

套接字被创建后，可通过属性和 `setSocketOptionXX` 接口配置属性。
启动监听需要调用 `bind()` 将套接字绑定到本地端口。`accept()` 接口将接受 TCP 连接，阻塞等待连接，若队列中已有连接，则可立即返回。
套接字需要通过 close 显式关闭。

父类型：

- [ServerSocket](socket_package_interfaces.md#interface-serversocket)

### prop backlogSize

```cangjie
public mut prop backlogSize: Int64
```

功能：设置和读取 `backlog` 大小。

仅可在调用 `bind` 前调用，否则将抛出异常。
变量是否生效取决于系统行为。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当在 `bind` 后调用时，抛出异常。

### prop bindToDevice

```cangjie
public mut prop bindToDevice: ?String
```

功能：设置和读取绑定网卡。

类型：?[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop localAddress

```cangjie
public override prop localAddress: SocketAddress
```

功能：读取 `Socket` 将要或已经被绑定的本地地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭时，抛出异常。

### prop receiveBufferSize

```cangjie
public mut prop receiveBufferSize: Int64
```

功能：设置和读取 `SO_RCVBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop reuseAddress

```cangjie
public mut prop reuseAddress: Bool
```

功能：设置和读取 `SO_REUSEADDR` 属性，默认设置为 `true`。

属性生效后的行为取决于系统，使用前，请参阅不同系统针对此属性 `SO_REUSEADDR/SOCK_REUSEADDR` 的说明文档。

类型：[Bool](../../core/core_package_api/core_package_intrinsics.md#bool)

### prop reusePort

```cangjie
public mut prop reusePort: Bool
```

功能：设置和读取 `SO_REUSEPORT` 属性。

仅可在绑定前被修改。Windows 上可使用 `SO_REUSEADDR`，无该属性，抛出异常。
属性默认及配置生效后的行为取决于系统，使用前，请参阅不同系统针对此属性 `SO_REUSEPORT` 的说明文档。
同时开启 `SO_REUSEADDR/SO_REUSEPORT` 会导致不可预知的系统错误，用户需谨慎配置值。

类型：[Bool](../../core/core_package_api/core_package_intrinsics.md#bool)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) -  Windows 上不支持此类型，抛出异常。

### prop sendBufferSize

```cangjie
public mut prop sendBufferSize: Int64
```

功能：设置和读取 `SO_SNDBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### init(SocketAddress)

```cangjie
public init(bindAt!: SocketAddress)
```

功能：创建一个 [TcpServerSocket](socket_package_classes.md#class-tcpserversocket) 实例，尚未绑定，因此客户端无法连接。

参数：

- bindAt!: [SocketAddress](socket_package_classes.md#class-socketaddress) - 指定本地绑定地址，端口号设置为 0 表示随机绑定空闲的本地地址。

### init(UInt16)

```cangjie
public init(bindAt!: UInt16)
```

功能：创建一个 [TcpServerSocket](socket_package_classes.md#class-tcpserversocket) 实例，尚未绑定，因此客户端无法连接。

参数：

- bindAt!: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 指定本地绑定端口，0 表示随机绑定空闲的本地端口。

### func accept()

```cangjie
public override func accept(): TcpSocket
```

功能：监听或接受客户端连接。阻塞等待。

返回值：

- [TcpSocket](socket_package_classes.md#class-tcpsocket) - 客户端套接字。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当因系统原因监听失败时，抛出异常。

### func accept(?Duration)

```cangjie
public override func accept(timeout!: ?Duration): TcpSocket
```

功能：监听或接受客户端连接。

参数：

- timeout!: ?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 超时时间。

返回值：

- [TcpSocket](socket_package_classes.md#class-tcpsocket) - 客户端套接字。

异常：

- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当连接超时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当因系统原因监听失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### func bind()

```cangjie
public override func bind(): Unit
```

功能：绑定本地端口失败后需要 `close` 套接字，不支持多次重试。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当因系统原因绑定失败时，抛出异常。

### func close()

```cangjie
public override func close(): Unit
```

功能：关闭套接字。接口允许多次调用。

### func getSocketOption(Int32, Int32, CPointer\<Unit>, CPointer\<UIntNative>)

```cangjie
public func getSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: CPointer<UIntNative>
): Unit
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)> - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时，抛出异常。

### func getSocketOptionBool(Int32, Int32)

```cangjie
public func getSocketOptionBool(
    level: Int32,
    option: Int32
): Bool
```

功能：获取指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false`，非 `0 => true`。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false`，非 `0 => true`。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func getSocketOptionIntNative(Int32, Int32)

```cangjie
public func getSocketOptionIntNative(
    level: Int32,
    option: Int32
): IntNative
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 获取的套接字参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func isClosed()

```cangjie
public override func isClosed(): Bool
```

功能：检查套接字是否关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果已经关闭，返回 `true`，否则返回 `false`。

### func setSocketOption(Int32, Int32, CPointer\<Unit>, UIntNative)

```cangjie
public func setSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: UIntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionBool(Int32, Int32，Bool)

```cangjie
public func setSocketOptionBool(
    level: Int32,
    option: Int32,
    value: Bool
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionIntNative(Int32, Int32, IntNative)

```cangjie
public func setSocketOptionIntNative(
    level: Int32,
    option: Int32,
    value: IntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func toString()

```cangjie
public override func toString(): String
```

功能：返回当前 [TcpServerSocket](socket_package_classes.md#class-tcpserversocket) 的状态信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 包含当前 [TcpServerSocket](socket_package_classes.md#class-tcpserversocket) 状态信息的字符串。

## class TcpSocket

```cangjie
public class TcpSocket <: StreamingSocket & Equatable<TcpSocket> & Hashable {
    public init(address: String, port: UInt16)
    public init(address: SocketAddress)
    public init(address: SocketAddress, localAddress!: ?SocketAddress)
}
```

功能：请求 TCP 连接的客户端。

当实例对象被创建后，可使用 `connect` 函数创建连接，并在结束时显式执行 `close` 操作。
该类型继承自 [StreamingSocket](socket_package_interfaces.md#interface-streamingsocket)， 可参阅 [StreamingSocket](socket_package_interfaces.md#interface-streamingsocket) 章节获取更多信息。

父类型：

- [StreamingSocket](socket_package_interfaces.md#interface-streamingsocket)
- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[TcpSocket](#class-tcpsocket)>
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)

### prop bindToDevice

```cangjie
public mut prop bindToDevice: ?String
```

功能：设置和读取绑定网卡。

类型：?[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop keepAlive

```cangjie
public mut prop keepAlive: ?SocketKeepAliveConfig
```

功能：设置和读取保活属性，`None` 表示关闭保活。

用户未设置时将使用系统默认配置。设置此配置可能会被延迟或被系统忽略，取决于系统的处理能力。

类型：?[SocketKeepAliveConfig](socket_package_structs.md#struct-socketkeepaliveconfig)

### prop linger

```cangjie
public mut prop linger: ?Duration
```

功能：设置和读取 `SO_LINGER` 属性，默认值取决于系统，`None` 表示禁用此选项。

> **说明：**
>
> - 如果 `SO_LINGER` 被设置为 `Some(v)`，当套接字关闭时，如果还有等待的字节流，我们将在关闭连接前等待 `v` 时间，如果超过时间，字节流还未被发送，连接将会被异常终止（通过 RST 报文关闭）。
> - 如果 `SO_LINGER` 被设置为 `None`，当套接字关闭时，连接将被立即关闭，如果当前等待发送的字符，使用 FIN-ACK 关闭连接，当还有剩余待发送的字符时，使用 RST 关闭连接。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### prop localAddress

```cangjie
public override prop localAddress: SocketAddress
```

功能：读取 `Socket` 将要或已经被绑定的本地地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭或无可用的本地地址（本地地址未配置并且套接字未连接）时，抛出异常。

### prop noDelay

```cangjie
public mut prop noDelay: Bool
```

功能：设置和读取 `TCP_NODELAY` 属性，默认为 `true`。

这个选项将禁用 Nagel 算法，所有写入字节被无延迟得转发。当属性设置为 `false` 时，Nagel 算法将在发包前引入延时时间。

类型：[Bool](../../core/core_package_api/core_package_intrinsics.md#bool)

### prop quickAcknowledge

```cangjie
public mut prop quickAcknowledge: Bool
```

功能：设置和读取 `TCP_QUICKACK` 属性，默认为 `false`。

这个选项类似于 `noDelay`，但仅影响 TCP ACK 和第一次响应。不支持 Windows 和 macOS 系统。

类型：[Bool](../../core/core_package_api/core_package_intrinsics.md#bool)

### prop readTimeout

```cangjie
public override mut prop readTimeout: ?Duration
```

功能：设置和读取读操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值；过大时将设置为最大超时时间（2<sup>63</sup>-1 纳秒）；默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### prop receiveBufferSize

```cangjie
public mut prop receiveBufferSize: Int64
```

功能：设置和读取 `SO_RCVBUF` 属性，提供一种方式指定收包缓存大小。选项的生效情况取决于系统。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop remoteAddress

```cangjie
public override prop remoteAddress: SocketAddress
```

功能：读取 `Socket` 已经或将要连接的远端地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭时，抛出异常。

### prop sendBufferSize

```cangjie
public mut prop sendBufferSize: Int64
```

功能：设置和读取 `SO_SNDBUF` 属性，提供一种方式指定发包缓存大小。选项的生效情况取决于系统。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop writeTimeout

```cangjie
public override mut prop writeTimeout: ?Duration
```

功能：设置和读取写操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值；过大时将设置为最大超时时间（2<sup>63</sup>-1 纳秒）；默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### init(SocketAddress)

```cangjie
public init(address: SocketAddress)
```

功能：创建一个未连接的套接字。

参数：

- address: [SocketAddress](socket_package_classes.md#class-socketaddress) - 即将要连接的地址。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `address` 参数不合法或者 Windows 平台下地址为全零地址时，抛出异常。

### init(SocketAddress, ?SocketAddress)

```cangjie
public init(address: SocketAddress, localAddress!: ?SocketAddress)
```

功能：创建一个未连接的套接字，并且绑定到指定本地地址，本地地址为 `None` 时，将随机选定地址去绑定。

此接口当 `localAddress` 不为 `None` 时，将默认设置 `SO_REUSEADDR` 为 `true`，否则可能导致 "address already in use" 的错误。如果需要变更此配置，可以通过调用 setSocketOptionBool([SocketOptions](socket_package_structs.md#struct-socketoptions).SOL_SOCKET, [SocketOptions](socket_package_structs.md#struct-socketoptions).SO_REUSEADDR, false)。另外，本地地址和远端地址需要均为 IPv4。

参数：

- address: [SocketAddress](socket_package_classes.md#class-socketaddress) - 即将要连接的地址。
- localAddress!: ?[SocketAddress](socket_package_classes.md#class-socketaddress) - 绑定的本地地址。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `address` 参数不合法或者 Windows 平台下地址为全零地址时，抛出异常。

### init(String, UInt16)

```cangjie
public init(address: String, port: UInt16)
```

功能：创建一个未连接的套接字。

参数：

- address: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 即将要连接的地址。
- port: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 即将要连接的端口。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `address` 参数不合法或者 Windows 平台下地址为全零地址时，抛出异常。

### func close()

```cangjie
public func close(): Unit
```

功能：关闭套接字，所有操作除了 `close/isClosed` 之外，均不允许再调用。接口允许多次调用。

### func connect(?Duration)

```cangjie
public func connect(timeout!: ?Duration = None): Unit
```

功能：连接远端套接字，会自动绑定本地地址，因此不需要进行额外的绑定操作。

参数：

- timeout!: ?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 连接超时时间，`None` 表示无超时时间，并且连接操作无重试，当服务端拒绝连接时，将返回连接失败。并且此操作包含了绑定操作，因此无需重复调用 `bind` 接口。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当远端地址不合法或者连接超时时间小于 0 或者超时时间小于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当连接因系统原因（例如：套接字已关闭，没有访问权限，系统错误等）无法建立时，抛出异常。再次调用可能成功。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当连接超时时，抛出异常。

### func getSocketOption(Int32, Int32, CPointer\<Unit>, CPointer\<UIntNative>)

```cangjie
public func getSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: CPointer<UIntNative>
): Unit
```

功能：读取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)> - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时，抛出异常。

### func getSocketOptionBool(Int32, Int32)

```cangjie
public func getSocketOptionBool(
    level: Int32,
    option: Int32
): Bool
```

功能：读取指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false`，非 `0 => true`。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 读取到的参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func getSocketOptionIntNative(Int32, Int32)

```cangjie
public func getSocketOptionIntNative(
    level: Int32,
    option: Int32
): IntNative
```

功能：读取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func hashCode()

```cangjie
public override func hashCode(): Int64
```

功能：获取当前 [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例的哈希值。

### func isClosed()

```cangjie
public func isClosed(): Bool
```

功能：判断套接字是否通过调用 `close` 显式关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 套接字是否已经调用 `close` 显式关闭。是则返回 `true`；否则返回 `false`。

### func read(Array\<Byte>)

```cangjie
public override func read(buffer: Array<Byte>): Int64
```

功能：读取报文。超时情况按 `readTimeout` 决定，详见 `readTimeout`。

> **说明：**
>
> - 由于系统底层接口差异，如果连接被对端关闭，`read` 和 `write` 接口的行为也有相应的差异。
> - Windows 系统上，对端关闭连接后，如果本端调用一次 `write`，会导致清空缓冲区内容，在此基础上再调用 `read` 会抛出连接关闭异常。
> - Linux/macOS 系统上，对端关闭连接后，先调用 `write` 再调用 `read` 函数仍会读出缓冲区中的内容。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储读出数据的缓冲区。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 读取的数据长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `buffer` 大小为 0 或者因系统原因读取失败时，抛出异常。

### func setSocketOption(Int32, Int32, CPointer\<Unit>, UIntNative)

```cangjie
public func setSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: UIntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionBool(Int32, Int32, Bool)

```cangjie
public func setSocketOptionBool(
    level: Int32,
    option: Int32,
    value: Bool
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionIntNative(Int32, Int32, IntNative)

```cangjie
public func setSocketOptionIntNative(
    level: Int32,
    option: Int32,
    value: IntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func toString()

```cangjie
public override func toString(): String
```

功能：返回当前 [TcpSocket](socket_package_classes.md#class-tcpsocket) 的状态信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 包含当前 [TcpSocket](socket_package_classes.md#class-tcpsocket) 状态信息的字符串。

### func write(Array\<Byte>)

```cangjie
public override func write(payload: Array<Byte>): Unit
```

功能：写入报文。超时情况按 `writeTimeout` 决定，详见 `writeTimeout`。

参数：

- payload: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储写入数据的缓冲区。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `buffer` 大小为 0 或者当因系统原因写入失败时，抛出异常。

### operator func !=(TcpSocket)

```cangjie
public override operator func !=(other: TcpSocket): Bool
```

功能：判断两个 [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例是否不等。

参数：

- other: [TcpSocket](socket_package_classes.md#class-tcpsocket) - 参与比较的 [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果两个 [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例不等，则返回 `true`；否则，返回 `false`。

### operator func ==(TcpSocket)

```cangjie
public override operator func ==(other: TcpSocket): Bool
```

功能：判断两个 [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例是否相等。

参数：

- other: [TcpSocket](socket_package_classes.md#class-tcpsocket) - 参与比较的 [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果两个 [TcpSocket](socket_package_classes.md#class-tcpsocket) 实例相等，则返回 `true`；否则，返回 `false`。

## class UdpSocket

```cangjie
public class UdpSocket <: DatagramSocket {
    public init(bindAt!: SocketAddress)
    public init(bindAt!: UInt16)
}
```

功能：提供 udp 报文通信。

`UDPSocket` 创建实例后，需要调用 `bind()` 绑定，可在不与远端建连的前提下接受报文。不过，`UDPSocket` 也可以通过 `connect()/disconnect()` 接口进行建连。
UDP 协议要求传输报文大小不可超过 64KB 。
`UDPSocket` 需要被显式 `close()` 。可以参阅 [DatagramSocket](socket_package_interfaces.md#interface-datagramsocket) 获取更多信息。

父类型：

- [DatagramSocket](socket_package_interfaces.md#interface-datagramsocket)

### prop localAddress

```cangjie
public override prop localAddress: SocketAddress
```

功能：读取 `Socket` 将要或已经被绑定的本地地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭或无可用的本地地址（本地地址未配置并且套接字未连接）时，抛出异常。

### prop receiveBufferSize

```cangjie
public mut prop receiveBufferSize: Int64
```

功能：设置和读取 `SO_RCVBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop receiveTimeout

```cangjie
public override mut prop receiveTimeout: ?Duration
```

功能：设置和读取 `receive/receiveFrom` 操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值；过大时将设置为最大超时时间（2<sup>63</sup>-1 纳秒）；默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### prop remoteAddress

```cangjie
public override prop remoteAddress: ?SocketAddress
```

功能：读取 `Socket` 已经连接的远端地址，当 `Socket` 未连接时返回 `None`。

类型：?[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭时，抛出异常。

### prop reuseAddress

```cangjie
public mut prop reuseAddress: Bool
```

功能：设置和读取 `SO_REUSEADDR` 属性。

属性默认以及生效后的行为取决于系统，使用前，请参阅不同系统针对此属性 `SO_REUSEADDR/SOCK_REUSEADDR` 的说明文档。

类型：[Bool](../../core/core_package_api/core_package_intrinsics.md#bool)

### prop reusePort

```cangjie
public mut prop reusePort: Bool
```

功能：设置和读取 `SO_REUSEPORT` 属性。

Windows 上可使用 `SO_REUSEADDR`，但无 `SO_REUSEPORT` 属性，因此会抛出异常。
属性默认以及配置生效后的行为取决于系统，使用前，请参阅不同系统针对此属性 `SO_REUSEPORT` 的说明文档。

类型：[Bool](../../core/core_package_api/core_package_intrinsics.md#bool)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - Windows 上不支持此类型，抛出异常。

### prop sendBufferSize

```cangjie
public mut prop sendBufferSize: Int64
```

功能：设置和读取 `SO_SNDBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop sendTimeout

```cangjie
public override mut prop sendTimeout: ?Duration
```

功能：设置和读取 `send/sendTo` 操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值；过大时将设置为最大超时时间（2<sup>63</sup>-1 纳秒）；默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

### init(SocketAddress)

```cangjie
public init(bindAt!: SocketAddress)
```

功能：创建一个未绑定的 `UDPSocket` 实例。

参数：

- bindAt!: [SocketAddress](socket_package_classes.md#class-socketaddress) - 绑定地址及端口。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### init(UInt64)

```cangjie
public init(bindAt!: UInt16)
```

功能：创建一个未绑定的 `UDPSocket` 实例。

参数：

- bindAt!: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 绑定端口。

### func bind()

```cangjie
public func bind(): Unit
```

功能：绑定本地端口失败后需要 `close` 套接字，不支持多次重试。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当因系统原因绑定失败时，抛出异常。

### func close()

```cangjie
public override func close(): Unit
```

功能：关闭套接字，所有操作除了 `close/isClosed` 之外，均不允许再调用。接口允许多次调用。

### func connect(SocketAddress)

```cangjie
public func connect(remote: SocketAddress): Unit
```

功能：连接特定远端地址，可通过 `disconnect` 撤销配置。

仅接受该远端地址的报文。必须在调用 `bind` 后执行。此操作执行后，端口将开始接收 ICMP 报文，若收到异常报文后，可能导致 `send/sendTo` 执行失败。

参数：

- remote: [SocketAddress](socket_package_classes.md#class-socketaddress) - 远端地址。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当远端地址不合法时，抛出异常，
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当端口未绑定、连接因系统原因无法建立或者 Windows 平台下远端地址为全零地址时，抛出异常。

### func disconnect()

```cangjie
public func disconnect(): Unit
```

功能：停止连接。取消仅收取特定对端报文。可在 `connect` 前调用，可多次调用。

### func getSocketOption(Int32, Int32, CPointer\<Unit>, CPointer\<UIntNative>)

```cangjie
public func getSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: CPointer<UIntNative>
): Unit
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)> - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时，抛出异常。

### func getSocketOptionBool(Int32, Int32)

```cangjie
public func getSocketOptionBool(
    level: Int32,
    option: Int32
): Bool
```

功能：获取指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false`，非 `0 => true`。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false`，非 `0 => true`。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func getSocketOptionIntNative(Int32, Int32)

```cangjie
public func getSocketOptionIntNative(
    level: Int32,
    option: Int32
): IntNative
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 指定的套接字参数值

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时抛出异常

### func isClosed()

```cangjie
public override func isClosed(): Bool
```

功能：判断套接字是否通过调用 `close` 显式关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该套接字已调用 `close` 显示关闭，则返回 `true`；否则，返回 `false`。

### func receive(Array\<Byte>)

```cangjie
public func receive(buffer: Array<Byte>): Int64
```

功能：从 `connect` 连接到的地址收取报文。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储收取到的报文的地址

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 收取到的报文大小。

### func receiveFrom(Array\<Byte>)

```cangjie
public override func receiveFrom(buffer: Array<Byte>): (SocketAddress, Int64)
```

功能：接收报文。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储收取到报文的缓存地址

返回值：

- ([SocketAddress](socket_package_classes.md#class-socketaddress), [Int64](../../core/core_package_api/core_package_intrinsics.md#int64)) - 收取到的报文的发送端地址，及实际收取到的报文大小，可能为 0 或者大于参数 `buffer` 的大小。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当本机缓存过小无法读取报文时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当读取超时时，抛出异常。

### func send(Array\<Byte>)

```cangjie
public func send(payload: Array<Byte>): Unit
```

功能：发送报文到 `connect` 连接到的地址。

参数：

- payload: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 发送报文内容。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `payload` 的大小超出系统限制或者系统发送失败（例如：当 `connect` 被调用，并且收到异常 ICMP 报文时，发送失败）时，抛出异常。

### func sendTo(SocketAddress, Array\<Byte>)

```cangjie
public override func sendTo(recipient: SocketAddress, payload: Array<Byte>): Unit
```

功能：发送报文。当没有足够的缓存地址时可能会被阻塞。

参数：

- recipient: [SocketAddress](socket_package_classes.md#class-socketaddress) - 发送的对端地址。
- payload: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 发送报文内容。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `payload` 的大小超出系统限制、系统发送失败（例如：当 `connect` 被调用，并且收到异常 ICMP 报文时，发送失败）、Windows 平台下远端地址为全零地址或者 macOS 平台下 `connect` 被调用后调用 `sendTo` 时，抛出异常。

### func setSocketOption(Int32, Int32, CPointer\<Unit>, UIntNative)

```cangjie
public func setSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: UIntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionBool(Int32, Int32, Bool)

```cangjie
public func setSocketOptionBool(
    level: Int32,
    option: Int32,
    value: Bool
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionIntNative(Int32, Int32, IntNative)

```cangjie
public func setSocketOptionIntNative(
    level: Int32,
    option: Int32,
    value: IntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func toString()

```cangjie
public override func toString(): String
```

功能：返回当前 [UdpSocket](socket_package_classes.md#class-udpsocket) 的状态信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 包含当前 [UdpSocket](socket_package_classes.md#class-udpsocket) 状态信息的字符串。

## class UnixDatagramSocket

```cangjie
public class UnixDatagramSocket <: DatagramSocket {
    public init(bindAt!: SocketAddress)
    public init(bindAt!: String)
}
```

功能：提供基于数据包的主机通讯能力。

[UnixDatagramSocket](socket_package_classes.md#class-unixdatagramsocket) 实例创建后，应当显式调用 `bind()` 接口绑定。`Unix` 数据包套接字不需要连接，不需要与远端握手多次。不过用户也可以通过 `connect/disconnect` 接口与远端建连和断连。
不同于 UDP，UDS 没有数据包大小限制，限制来源于操作系统和接口实现。
套接字资源需要用 `close` 接口显式回收。可参阅 [DatagramSocket](socket_package_interfaces.md#interface-datagramsocket) 获取更多信息。

> **注意：**
>
> - 该类型不支持在 Windows 平台上运行。

父类型：

- [DatagramSocket](socket_package_interfaces.md#interface-datagramsocket)

### prop localAddress

```cangjie
public override prop localAddress: SocketAddress
```

功能：读取 `socket` 将要或已经绑定的本地地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `socket` 已经关闭时，抛出异常。

### prop receiveBufferSize

```cangjie
public mut prop receiveBufferSize: Int64
```

功能：设置和读取 `SO_RCVBUF` 属性，提供一种方式指定发包缓存大小。选项的生效情况取决于系统。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop receiveTimeout

```cangjie
public override mut prop receiveTimeout: ?Duration
```

功能：设置和读取 `receive/receiveFrom` 操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值；过大时将设置为最大超时时间（2<sup>63</sup>-1 纳秒）；默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### prop remoteAddress

```cangjie
public override prop remoteAddress: ?SocketAddress
```

功能：读取 `Socket` 已经连接的远端地址，当 `Socket` 未连接时返回 `None`。

类型：?[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭时，抛出异常。

### prop sendBufferSize

```cangjie
public mut prop sendBufferSize: Int64
```

功能：设置和读取 `SO_SNDBUF` 属性，提供一种方式指定发包缓存大小。选项的生效情况取决于系统。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop sendTimeout

```cangjie
public override mut prop sendTimeout: ?Duration
```

功能：设置和读取 `send/sendTo` 操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值；过大时将设置为最大超时时间（2<sup>63</sup>-1 纳秒）；默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### init(SocketAddress)

```cangjie
public init(bindAt!: SocketAddress)
```

功能：创建一个未连接的 [UnixDatagramSocket](socket_package_classes.md#class-unixdatagramsocket) 实例。

此文件类型可通过 [isSock](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-issockstring)() 判断是否存在，可通过 [unlink](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-unlinkstring)() 接口删除。

参数：

- bindAt!: [SocketAddress](socket_package_classes.md#class-socketaddress) - 连接的套接字地址。地址应当不存在，在 `bind` 时会创建。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当路径为空或已存在时，抛出异常。

### init(String)

```cangjie
public init(bindAt!: String)
```

功能：创建一个未连接的 [UnixDatagramSocket](socket_package_classes.md#class-unixdatagramsocket) 实例。

此文件类型可通过 [isSock](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-issockstring)() 判断是否存在，可通过 [unlink](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-unlinkstring)() 接口删除。

参数：

- bindAt!: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 连接的文件地址。文件地址应当不存在，在 `bind` 时会创建。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当路径为空或已存在时，抛出异常。

### func bind()

```cangjie
public func bind(): Unit
```

功能：绑定一个 `Unix datagram` 套接字，并创建监听队列。

此接口自动在本地地址中创建一个套接字文件，如该文件已存在则会绑定失败。此文件类型可通过 [isSock](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-issockstring) 判断是否存在，可通过 [unlink](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-unlinkstring)() 接口删除，失败后需要 `close` 套接字，不支持多次重试。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当文件地址已存在，或文件创建失败时，抛出异常。

### func close()

```cangjie
public override func close(): Unit
```

功能：关闭套接字，所有操作除了 `close/isClosed` 之外，均不允许再调用。接口允许多次调用。

### func connect(SocketAddress)

```cangjie
public func connect(remote: SocketAddress): Unit
```

功能：连接特定远端地址，可通过 `disconnect` 撤销配置。

仅接受该远端地址的报文。默认执行 `bind`，因此不需额外调用 `bind`。此操作执行后，端口将开始接收 ICMP 报文，若收到异常报文后，可能导致 `send/sendTo` 执行失败。

参数：

- remote: [SocketAddress](socket_package_classes.md#class-socketaddress) - 远端套接字地址。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当地址未绑定时，抛出异常。

### func connect(String)

```cangjie
public func connect(remotePath: String): Unit
```

功能：连接特定远端地址，可通过 `disconnect` 撤销配置。

仅接受该远端地址的报文。必须在 `bind` 后调用。此操作执行后，端口将开始接收 ICMP 报文，若收到异常报文后，可能导致 `send/sendTo` 执行失败。

参数：

- remotePath: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 远端文件地址。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当地址未绑定时，抛出异常。

### func disconnect()

```cangjie
public func disconnect(): Unit
```

功能：停止连接。取消仅收取特定对端报文。可在 `connect` 前调用，可多次调用。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当未绑定时，抛出异常。

### func getSocketOption(Int32, Int32, CPointer\<Unit>, CPointer\<UIntNative>)

```cangjie
public func getSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: CPointer<UIntNative>
): Unit
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<UIntNative> - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时，抛出异常。

### func getSocketOptionIntNative(Int32, Int32)

```cangjie
public func getSocketOptionIntNative(
    level: Int32,
    option: Int32
): IntNative
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 返回指定的套接字参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func isClosed()

```cangjie
public override func isClosed(): Bool
```

功能：判断套接字是否通过调用 `close` 显式关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 返回套接字是否已经通过调用 `close` 显式关闭。是则返回 `true`；否则，返回 `false`。

### func receive(Array\<Byte>)

```cangjie
public func receive(buffer: Array<Byte>): Int64
```

功能：从 `connect` 连接到的地址收取报文。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储收取到的报文的地址。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 收取到的报文大小。

### func receiveFrom(Array\<Byte>)

```cangjie
public override func receiveFrom(buffer: Array<Byte>): (SocketAddress, Int64)
```

功能：收取报文。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储收取到报文的地址。

返回值：

- ([SocketAddress](socket_package_classes.md#class-socketaddress), [Int64](../../core/core_package_api/core_package_intrinsics.md#int64)) - 收取到的报文的发送端地址，及实际收取到的报文大小，可能为 0 或者大于参数 `buffer` 的大小。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 本机缓存过小无法读取报文时，抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当读取超时时，抛出异常。

### func send(Array\<Byte>)

```cangjie
public func send(payload: Array<Byte>): Unit
```

功能：发送报文到 `connect` 连接到的地址。

参数：

- payload: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 发送报文内容。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `payload` 的大小超出系统限制或者系统发送失败（例如：当 `connect` 被调用，并且收到异常 ICMP 报文时，发送失败）时，抛出异常。

### func sendTo(SocketAddress, Array\<Byte>)

```cangjie
public override func sendTo(recipient: SocketAddress, payload: Array<Byte>): Unit
```

功能：发送报文。当没有足够的缓存地址时可能会被阻塞。

参数：

- recipient: [SocketAddress](socket_package_classes.md#class-socketaddress) - 发送的对端地址。
- payload: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 发送报文内容。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `payload` 的大小超出系统限制、系统发送失败（例如：当 `connect` 被调用，并且收到异常 ICMP 报文时，发送失败）或者 macOS 平台下 `connect` 被调用后调用 `sendTo` 时，抛出异常。

### func setSocketOption(Int32, Int32, CPointer\<Unit>, UIntNative)

```cangjie
public func setSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: UIntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionBool(Int32, Int32, Bool)

```cangjie
public func setSocketOptionBool(
    level: Int32,
    option: Int32,
    value: Bool
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionIntNative(Int32, Int32，IntNative)

```cangjie
public func setSocketOptionIntNative(
    level: Int32,
    option: Int32,
    value: IntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时抛出异常

#### func getSocketOptionBool(Int32, Int32)

```cangjie
public func getSocketOptionBool(
    level: Int32,
    option: Int32
): Bool
```

功能：获取指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false，非 0 => true`。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 返回指定的套接字参数值。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false，非 0 => true`。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时，抛出异常。

### func toString()

```cangjie
public override func toString(): String
```

功能：返回当前 `UDS` 的状态信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 包含当前 `UDS` 状态信息的字符串。

## class UnixServerSocket

```cangjie
public class UnixServerSocket <: ServerSocket
```

功能：提供基于双工流的主机通讯服务端。

[UnixServerSocket](socket_package_classes.md#class-unixserversocket) 监听连接，创建后可以通过属性和 `setSocketOptionXX` 接口配置属性值。需要调用 `bind()` 接口绑定本地地址开始监听连接。可以通过 `accept()` 接口接受连接。

> **注意：**
>
> - 该类型不支持在 Windows 平台上运行。

父类型：

- [ServerSocket](socket_package_interfaces.md#interface-serversocket)

### prop backlogSize

```cangjie
public mut prop backlogSize: Int64
```

功能：设置和读取 `backlog` 大小。仅可在调用 `bind` 前调用，否则将抛出异常。
变量是否生效取决于系统行为。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当在 `bind` 后调用，将抛出异常。

### prop localAddress

```cangjie
public override prop localAddress: SocketAddress
```

功能：读取 `Socket` 将要或已经被绑定的本地地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭时，抛出异常。

### prop receiveBufferSize

```cangjie
public mut prop receiveBufferSize: Int64
```

功能：设置和读取 `SO_RCVBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop sendBufferSize

```cangjie
public mut prop sendBufferSize: Int64
```

功能：设置和读取 `SO_SNDBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### init(SocketAddress)

```cangjie
public init(bindAt!: SocketAddress)
```

功能：创建一个未连接的 [UnixServerSocket](socket_package_classes.md#class-unixserversocket) 实例。

参数：

- bindAt!: [SocketAddress](socket_package_classes.md#class-socketaddress) - 连接的套接字地址

### init(String)

```cangjie
public init(bindAt!: String)
```

功能：创建一个未连接的 [UnixServerSocket](socket_package_classes.md#class-unixserversocket) 实例。

此文件类型可通过 [isSock](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-issockstring) 判断是否存在，可通过 [unlink](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-unlinkstring)() 接口删除。

参数：

- bindAt!: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 连接的文件地址

### func accept()

```cangjie
public override func accept(): UnixSocket
```

功能：等待接受一个客户端的连接，或从队列中读取连接。

返回值：

- [UnixSocket](socket_package_classes.md#class-unixsocket) - 连接的客户端套接字。

### func accept(?Duration)

```cangjie
public override func accept(timeout!: ?Duration): UnixSocket
```

功能：等待接受一个客户端的连接，或从队列中读取连接。

参数：

- timeout!: ?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 超时时间。

返回值：

- [UnixSocket](socket_package_classes.md#class-unixsocket) - 连接的客户端套接字

异常：

- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当连接超时时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### func bind()

```cangjie
public override func bind(): Unit
```

功能：绑定一个 `Unix domain` 套接字，并创建监听队列。

此接口自动在本地地址中创建一个套接字文件，如该文件已存在则会绑定失败。此文件类型可通过 [isSock](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-issockstring) 接口判断是否存在，可通过 [unlink](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-unlinkstring)() 接口删除，失败后需要 `close` 套接字，不支持多次重试。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当因系统原因绑定失败时，抛出异常。

### func close()

```cangjie
public override func close(): Unit
```

功能：关闭套接字，该套接字的所有操作除了 `close/isClosed` 之外，均不允许再调用。此接口允许多次调用。

### func getSocketOption(Int32, Int32, CPointer\<Unit>, CPointer\<UIntNative>)

```cangjie
public func getSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: CPointer<UIntNative>
): Unit
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)> - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时，抛出异常。

### func getSocketOptionBool(Int32, Int32）

```cangjie
public func getSocketOptionBool(
    level: Int32,
    option: Int32
): Bool
```

功能：获取指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false，非 0 => true`。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 返回指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false，非 0 => true`。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func getSocketOptionIntNative(Int32, Int32)

```cangjie
public func getSocketOptionIntNative(
    level: Int32,
    option: Int32
): IntNative
```

功能：获取返回值为整型的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 指定的套接字参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func isClosed()

```cangjie
public override func isClosed(): Bool
```

功能：判断套接字是否通过调用 `close` 显式关闭。

### func setSocketOption(Int32, Int32, CPointer\<Unit>, UIntNative)

```cangjie
public func setSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: UIntNative
): Unit
```

功能：设置返回值为整型的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionBool(Int32, Int32, Bool）

```cangjie
public func setSocketOptionBool(
    level: Int32,
    option: Int32,
    value: Bool
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionIntNative(Int32, Int32, IntNative)

```cangjie
public func setSocketOptionIntNative(
    level: Int32,
    option: Int32,
    value: IntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func toString()

```cangjie
public override func toString(): String
```

功能：返回当前 [UnixServerSocket](socket_package_classes.md#class-unixserversocket) 的状态信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 包含当前 [UnixServerSocket](socket_package_classes.md#class-unixserversocket) 状态信息的字符串。

## class UnixSocket

```cangjie
public class UnixSocket <: StreamingSocket {
    public init(address: SocketAddress)
    public init(path: String)
}
```

功能：提供基于双工流的主机通讯客户端。

[UnixSocket](socket_package_classes.md#class-unixsocket) 实例创建后应调用 `connect()` 接口创建连接，并且在结束时显式调用 `close()` 回收资源。可参阅 [StreamingSocket](socket_package_interfaces.md#interface-streamingsocket) 获取更多信息。

> **注意：**
>
> - 该类型不支持在 Windows 平台上运行。

父类型：

- [StreamingSocket](socket_package_interfaces.md#interface-streamingsocket)

### prop localAddress

```cangjie
public override prop localAddress: SocketAddress
```

功能：读取 `Socket` 将要或已经被绑定的本地地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭或无可用的本地地址（本地地址未配置并且套接字未连接）时，抛出异常。

### prop readTimeout

```cangjie
public override mut prop readTimeout: ?Duration
```

功能：设置和读取读操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值，过大时将设置为`None`，默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### prop receiveBufferSize

```cangjie
public mut prop receiveBufferSize: Int64
```

功能：设置和读取 `SO_RCVBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop remoteAddress

```cangjie
public override prop remoteAddress: SocketAddress
```

功能：读取 `Socket` 已经或将要连接的远端地址。

类型：[SocketAddress](socket_package_classes.md#class-socketaddress)

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已经被关闭时，抛出异常。

### prop sendBufferSize

```cangjie
public mut prop sendBufferSize: Int64
```

功能：设置和读取 `SO_SNDBUF` 属性。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `size` 小于等于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `Socket` 已关闭时，抛出异常。

### prop writeTimeout

```cangjie
public override mut prop writeTimeout: ?Duration
```

功能：设置和读取写操作超时时间。

如果设置的时间过小将会设置为最小时钟周期值；过大时将设置为最大超时时间（2<sup>63</sup>-1 纳秒）；默认值为 `None`。

类型：?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration)

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当超时时间小于 0 时，抛出异常。

### init(SocketAddress)

```cangjie
public init(address: SocketAddress)
```

功能：创建一个未连接的 [UnixSocket](socket_package_classes.md#class-unixsocket) 实例。

参数：

- address: [SocketAddress](socket_package_classes.md#class-socketaddress) - 连接的套接字地址。

### init(String)

```cangjie
public init(path: String)
```

功能：创建一个未连接的 [UnixSocket](socket_package_classes.md#class-unixsocket) 实例。

此文件类型可通过 [isSock](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-issockstring) 判断是否存在，可通过 [unlink](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-unlinkstring)() 接口删除。

参数：

- path: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 连接的文件地址。

### func close()

```cangjie
public func close(): Unit
```

功能：关闭套接字，所有操作除了 `close/isClosed` 之外，均不允许再调用。接口允许多次调用。

### func connect(?Duration)

```cangjie
public func connect(timeout!: ?Duration = None): Unit
```

功能：建立远端连接，对端拒绝时连接失败，会自动绑定本地地址，因此不需要进行额外的绑定操作。

参数：

- timeout!: ?[Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 超时时间，`None` 表示无超时时间。Unix 与 Tcp 不同，队列已满时，调用立即返回错误，而非重试阻塞等待。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当远端地址不合法或者超时时间小于 0 时，抛出异常。
- [SocketException](socket_package_exceptions.md#class-socketexception) - 当连接因系统原因无法建立时。抛出异常。
- [SocketTimeoutException](socket_package_exceptions.md#class-sockettimeoutexception) - 当连接超时时。抛出异常。

### func getSocketOption(Int32, Int32, CPointer\<Unit>, CPointer\<UIntNative>)

```cangjie
public func getSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: CPointer<UIntNative>
): Unit
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)> - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时，抛出异常。

### func getSocketOptionBool(Int32, Int32)

```cangjie
public func getSocketOptionBool(
    level: Int32,
    option: Int32
): Bool
```

功能：获取指定的套接字参数。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false`，非 `0 => true`。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 返回指定的套接字参数值。从 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 强转而来。`0 => false`，非 `0 => true`。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func getSocketOptionIntNative(Int32, Int32)

```cangjie
public func getSocketOptionIntNative(
    level: Int32,
    option: Int32
): IntNative
```

功能：获取指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 指定的套接字参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `getsockopt` 返回失败时或参数大小超过 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的阈值时，抛出异常。

### func isClosed()

```cangjie
public func isClosed(): Bool
```

功能：判断套接字是否通过调用 `close` 显式关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 返回套接字是否已经调用 `close` 显示关闭。是则返回 `true`；否则，返回 `false`。

### func read(Array\<Byte>)

```cangjie
public override func read(buffer: Array<Byte>): Int64
```

功能：读取报文。超时情况按 `readTimeout` 决定，详见 `readTimeout`。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 读取的数据存储变量。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 读取的数据长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `buffer` 大小为 0 或者因系统原因读取失败时，抛出异常。

### func setSocketOption(Int32, Int32, CPointer\<Unit>, UIntNative)

```cangjie
public func setSocketOption(
    level: Int32,
    option: Int32,
    value: CPointer<Unit>,
    valueLength: UIntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)> - 参数值。
- valueLength: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 参数值长度。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionBool(Int32, Int32, Bool）

```cangjie
public func setSocketOptionBool(
    level: Int32,
    option: Int32,
    value: Bool
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func setSocketOptionIntNative(Int32, Int32, IntNative)

```cangjie
public func setSocketOptionIntNative(
    level: Int32,
    option: Int32,
    value: IntNative
): Unit
```

功能：设置指定的套接字参数。

参数：

- level: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 层级，例如 `SOL_SOCKET`。
- option: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 参数，例如 `SO_KEEPALIVE`。
- value: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 参数值。

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `setsockopt` 返回失败时，抛出异常。

### func toString()

```cangjie
public override func toString(): String
```

功能：返回当前 [UnixSocket](socket_package_classes.md#class-unixsocket) 的状态信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 包含当前 [UnixSocket](socket_package_classes.md#class-unixsocket) 状态信息的字符串。

### func write(Array\<Byte>)

```cangjie
public override func write(buffer: Array<Byte>): Unit
```

功能：读取写入。超时情况按 `writeTimeout` 决定，详见 `writeTimeout`。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 写入的数据存储变量

异常：

- [SocketException](socket_package_exceptions.md#class-socketexception) - 当 `buffer` 大小为 0 时抛出异常，当因系统原因写入失败时，抛出异常。
