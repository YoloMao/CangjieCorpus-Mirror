# 函数

## func fromHexString(String)

```cangjie
public func fromHexString(data: String): Option<Array<Byte>>
```

功能：此函数用于 Hex 编码的字符串的解码。

参数：

- data: [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - 要解码的 Hex 编码的字符串。

返回值：

- [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)>> - 输入空字符串会返回 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)>>.Some([Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)>())，解码失败会返回 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)>>.None。

## func toHexString(Array\<Byte>)

```cangjie
public func toHexString(data: Array<Byte>): String
```

功能：此函数用于将 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 数组转换成 Hex 编码的字符串。

参数：

- data: [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)> - 要编码的 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 数组。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - 返回编码后的字符串。
