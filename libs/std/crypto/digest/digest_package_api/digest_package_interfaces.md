# 接口

## interface Digest

```cangjie
public interface Digest {
    prop size: Int64
    prop blockSize: Int64
}
```

功能：摘要算法接口，继承该接口的 class、interface、struct 也需要遵守该接口中函数的入参及返回值定义。

### prop blockSize

```cangjie
prop blockSize: Int64
```

功能：返回[Block](../../../ast/ast_package_api/ast_package_classes.md#class-block)块长度，单位字节。

类型：[Int64](../../../core/core_package_api/core_package_intrinsics.md#int64)

### prop size

```cangjie
prop size: Int64
```

功能：返回生成的摘要信息长度，单位字节。

类型：[Int64](../../../core/core_package_api/core_package_intrinsics.md#int64)

### func finish()

```cangjie
func finish(): Array<Byte>
```

功能：返回生成的 digest 值。

返回值：

- [Array](../../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../core/core_package_api/core_package_types.md#type-byte)> - 返回生成摘要值。

### func reset()

```cangjie
mut func reset(): Unit
```

功能：重置 digest 对象到初始状态。

### func write(Array\<Byte>)

```cangjie
mut func write(buffer: Array<Byte>): Unit
```

功能：使用给定的 buffer 更新 digest 对象。
