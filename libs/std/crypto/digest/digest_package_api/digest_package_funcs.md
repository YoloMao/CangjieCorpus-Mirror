# 函数

## func digest\<T>(T, Array\<Byte>) where T <: Digest

```cangjie
public func digest<T>(algorithm: T, data: Array<Byte>): Array<Byte> where T <: Digest
```

功能：提供 digest 泛型函数，实现用指定的摘要算法进行摘要运算。

参数：

- algorithm: T - 具体的摘要算法。
- data: [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 待进行摘要运算的数据。

返回值：

- [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 摘要运算结果。

## func digest\<T>(T, String) where T <: Digest

```cangjie
public func digest<T>(algorithm: T, data: String): Array<Byte> where T <: Digest
```

功能：提供 digest 泛型函数，实现用指定的摘要算法进行摘要运算。

参数：

- algorithm: T - 具体的摘要算法。
- data: [String](../../../core/core_package_api/core_package_structs.md#struct-string) - 待进行摘要运算的数据。

返回值：

- [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 摘要运算结果。
