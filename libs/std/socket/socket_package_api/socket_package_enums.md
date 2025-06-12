# 枚举

## enum SocketAddressKind

```cangjie
public enum SocketAddressKind <: ToString & Equatable<SocketAddressKind> {
    | IPv4
    | IPv6
    | Unix
}
```

功能：互联网通信协议种类。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[SocketAddressKind](#enum-socketaddresskind)>

### IPv4

```cangjie
IPv4
```

功能：代表 IPv4 协议。

### IPv6

```cangjie
IPv6
```

功能：代表 IPv6 协议。

### Unix

```cangjie
Unix
```

功能：代表 Unix 协议。

### func toString()

```cangjie
public func toString(): String
```

功能：将枚举值转换为字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的字符串。

### operator func !=(SocketAddressKind)

```cangjie
public operator func !=(that: SocketAddressKind): Bool
```

功能：判断两个 [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind) 是否不相等。

参数：

- that: [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind) - 传入的 [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果不相等，则返回 `true`；否则，返回 `false`。

### operator func ==(SocketAddressKind)

```cangjie
public operator func ==(that: SocketAddressKind): Bool
```

功能：判断两个 [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind) 是否相等。

参数：

- that: [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind) - 传入的 [SocketAddressKind](socket_package_enums.md#enum-socketaddresskind)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果相等，则返回 `true`；否则，返回 `false`。

## enum SocketNet

```cangjie
public enum SocketNet <: ToString & Equatable<SocketNet> {
    | TCP
    | UDP
    | UNIX
}
```

功能：传输层协议类型。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[SocketNet](#enum-socketnet)>

### TCP

```cangjie
TCP
```

功能：代表 TCP 协议。

### UDP

```cangjie
UDP
```

功能：代表 UDP 协议。

### UNIX

```cangjie
UNIX
```

功能：代表 UNIX 协议。

### func toString()

```cangjie
public func toString(): String
```

功能：将枚举值转换为字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的字符串。

### operator func !=(SocketNet)

```cangjie
public operator func !=(that: SocketNet): Bool
```

功能：判断两个 [SocketNet](socket_package_enums.md#enum-socketnet) 是否不相等。

参数：

- that: [SocketNet](socket_package_enums.md#enum-socketnet) - 传入的 [SocketNet](socket_package_enums.md#enum-socketnet)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果不相等，则返回 `true`；否则，返回 `false`。

### operator func ==(SocketNet)

```cangjie
public operator func ==(that: SocketNet): Bool
```

功能：判断两个 [SocketNet](socket_package_enums.md#enum-socketnet) 是否相等。

参数：

- that: [SocketNet](socket_package_enums.md#enum-socketnet) - 的 [SocketNet](socket_package_enums.md#enum-socketnet)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果相等，则返回 `true`；否则，返回 `false`。
