# 接口

## interface BlockCipher

```cangjie
public interface BlockCipher {
    prop blockSize: Int64
    func encrypt(input: Array<Byte>): Array<Byte>
    func decrypt(input: Array<Byte>): Array<Byte>
}
```

功能：分组加解密算法接口，继承该接口的 class、interface、struct 也需要遵守该接口中函数的入参及返回值定义。

### prop blockSize

```cangjie
prop blockSize: Int64
```

功能：分组块长度，单位字节。

类型：[Int64](../../../core/core_package_api/core_package_intrinsics.md#int64)


### func encrypt(Array\<Byte>)

```cangjie
func encrypt(input: Array<Byte>): Array<Byte>
```

功能：提供加密函数。

参数：

- input: [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 待进行加密的数据。

返回值：

- [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 加密后的结果。

### func decrypt(Array\<Byte>)

```cangjie
func decrypt(input: Array<Byte>): Array<Byte>
```

功能：提供解密函数。

参数：

- input: [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 待进行解密的数据。

返回值：

- [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 解密后的结果。