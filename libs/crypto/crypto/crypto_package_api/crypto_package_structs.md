# 结构体

## struct OperationMode

```cangjie
public struct OperationMode <: ToString & Equatable<OperationMode>
```

功能： 对称加解密算法的工作模式。

父类型：

- [ToString](../../../std/core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Equatable](../../../std/core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[OperationMode](#struct-operationmode)>

### static let ECB

```cangjie
public static let ECB
```

功能：Electronic CodeBook(单子密码本)工作模式。

类型：[OperationMode](crypto_package_structs.md#struct-operationmode)

### static let CBC

```cangjie
public static let CBC
```

功能：Cipher Block Chaining(密码分组链接)工作模式。

类型：[OperationMode](crypto_package_structs.md#struct-operationmode)

### static let OFB

```cangjie
public static let OFB
```

功能：Output FeedBack(输出反馈)工作模式。

类型：[OperationMode](crypto_package_structs.md#struct-operationmode)

### static let CFB

```cangjie
public static let CFB
```

功能：Output FeedBack(密文反馈)工作模式。

类型：[OperationMode](crypto_package_structs.md#struct-operationmode)

### static let CTR

```cangjie
public static let CTR
```

功能：CounTeR(计数器)工作模式。

类型：[OperationMode](crypto_package_structs.md#struct-operationmode)

### static let GCM

```cangjie
public static let GCM
```

功能：Galois Counter(伽罗瓦计数器)工作模式。

类型：[OperationMode](crypto_package_structs.md#struct-operationmode)

### let mode

```cangjie
public let mode: String
```

功能：operation 分组加解密的工作模式，目前支持 ECB、CBC CFB OFB CTR GCM。

类型：[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)

### func toString()

```cangjie
public override func toString(): String
```

功能：获取工作模式字符串。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - 工作模式字符串。

### func ==(OperationMode)

```cangjie
public operator override func ==(other: OperationMode): Bool
```

功能：工作模式比较是否相同。

参数：

- other: [OperationMode](crypto_package_structs.md#struct-operationmode) - 工作模式。

返回值：

- [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) - true 相同， false不相同。

### func !=(OperationMode)

```cangjie
public operator override func !=(other: OperationMode): Bool
```

功能：工作模式比较是否不相同。

参数：

- other: [OperationMode](crypto_package_structs.md#struct-operationmode) - 工作模式。

返回值：

- [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) - true 不相同， false相同。


## struct PaddingMode

```cangjie
public struct PaddingMode <: Equatable<PaddingMode>
```

功能： 对称加解密算法的工填充模式。

父类型：

- [Equatable](../../../std/core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[PaddingMode](#struct-paddingmode)>

### static let NoPadding

```cangjie
public static let NoPadding
```

功能：不填充。

类型：[PaddingMode](crypto_package_structs.md#struct-paddingmode)

### static let PKCS7Padding

```cangjie
public static let PKCS7Padding
```

功能：采用PKCS7协议填充。

类型：[PaddingMode](crypto_package_structs.md#struct-paddingmode)

### let paddingType

```cangjie
public let paddingType: Int64
```

功能：分组加解密填充方式，目前支持非填充和 pkcs7 填充。

类型：[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)

### func ==(PaddingMode)

```cangjie
public operator override func ==(other: PaddingMode): Bool
```

功能：填充模式比较是否相同。

参数：

- other: [PaddingMode](crypto_package_structs.md#struct-paddingmode) - 填充模式。

返回值：

- [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) - true 相同， false不相同。

### func !=(PaddingMode)

```cangjie
public operator override func !=(other: PaddingMode): Bool
```

功能：工作模式比较是否不相同。

参数：

- other: [PaddingMode](crypto_package_structs.md#struct-paddingmode)  - 填充模式。

返回值：

- [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) - true 不相同， false相同。