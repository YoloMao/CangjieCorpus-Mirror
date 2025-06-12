# 类

## class Random

```cangjie
public open class Random
```

功能： 提供生成伪随机数的相关功能。

示例：

```cangjie
import std.random.*
main() {
    let m: Random = Random()
    /* 创建 Random 对象并设置种子来获取随机对象 */
    m.seed = 3
    let b: Bool = m.nextBool()
    let c: Int8 = m.nextInt8()
    print("b=${b is Bool},")/* 对象也可以是 Bool 类型 */
    println("c=${c is Int8}")
    return 0
}
```

运行结果:

```text
b=true,c=true
```

### prop seed

```cangjie
public open mut prop seed: UInt64
```

功能： 设置或者获取种子的大小，如果设置相同随机种子，生成的伪随机数列表相同。

类型：[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)

### init()

```cangjie
public init()
```

功能： 默认无参构造函数创建新的 [Random](random_package_classes.md#class-random) 对象。

### init(UInt64)

```cangjie
public init(seed: UInt64)
```

功能：使用随机数种子创建新的 [Random](random_package_classes.md#class-random) 对象。

参数：

- seed: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 随机数种子，如果设置相同随机种子，生成的伪随机数列表相同。

### func next(UInt64)

```cangjie
public open func next(bits: UInt64): UInt64
```

功能： 生成一个用户指定位长的随机整数。

参数：

- bits: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 要生成的伪随机数的位数，取值范围 (0, 64]。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 用户指定位长的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `bits` 等于 0 ，或大于 64，超过所能截取的 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 长度，则抛出异常。

### func nextBool()

```cangjie
public open func nextBool(): Bool
```

功能：获取一个布尔类型的伪随机值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 一个 [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) 类型的伪随机数。

### func nextFloat16()

```cangjie
public open func nextFloat16(): Float16
```

功能：获取一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的伪随机数，其范围为 [0.0, 1.0)。

返回值：

- [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - 一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的伪随机数。

### func nextFloat32()

```cangjie
public open func nextFloat32(): Float32
```

功能：获取一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的伪随机数，其范围为 [0.0, 1.0)。

返回值：

- [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - 一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的伪随机数。

### func nextFloat64()

```cangjie
public open func nextFloat64(): Float64
```

功能：获取一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的伪随机数，其范围为 [0.0, 1.0)。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的伪随机数。

### func nextGaussianFloat16(Float16, Float16)

```cangjie
public func nextGaussianFloat16(mean!: Float16 = 0.0, sigma!: Float16 = 1.0): Float16
```

功能：获取一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的符合指定均值与标准差的高斯分布的随机数。

默认获取一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型且符合均值为 0.0 标准差为 1.0 的高斯分布的随机数。其中均值是期望值，可解释为位置参数，决定了分布的位置，标准差可解释为尺度参数，决定了分布的幅度。此函数调用了函数 `nextGaussianFloat16Implement` 得到返回值，所以当子类继承 [Random](random_package_classes.md#class-random) 并覆写 `nextGaussianFloat64Implement` 函数时，调用子类的该函数将会返回覆写的函数的返回值。

参数：

- mean!: [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - 均值，默认值 0.0。
- sigma!: [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - 标准差，默认值 1.0。

返回值：

- [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - 一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的随机数。

### func nextGaussianFloat16Implement(Float16, Float16)

```cangjie
protected open func nextGaussianFloat16Implement(mean: Float16, sigma: Float16): Float16
```

功能： `nextGaussianFloat16` 的实现函数，获取一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的符合指定均值与标准差的高斯分布的随机数。

获取一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型，且符合均值为 `mean` 标准差为 `sigma` 的高斯分布的随机数。其中均值是期望值，可解释为位置参数，决定了分布的位置，标准差可解释为尺度参数，决定了分布的幅度。此函数是 `nextGaussianFloat16` 的实现函数，非公开，当子类继承 [Random](random_package_classes.md#class-random) 并覆写此函数时，调用子类的 `nextGaussianFloat16` 函数将会返回此函数的返回值。

参数：

- mean: [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - 均值。
- sigma: [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - 标准差。

返回值：

- [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - 一个 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的随机数。

### func nextGaussianFloat32(Float32, Float32)

```cangjie
public func nextGaussianFloat32(mean!: Float32 = 0.0, sigma!: Float32 = 1.0): Float32
```

功能：获取一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的符合指定均值与标准差的高斯分布的随机数。

默认获取一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型且符合均值为 0.0 标准差为 1.0 的高斯分布的随机数。其中均值是期望值，可解释为位置参数，决定了分布的位置，标准差可解释为尺度参数，决定了分布的幅度。此函数调用了函数 `nextGaussianFloat32Implement` 得到返回值，所以当子类继承 [Random](random_package_classes.md#class-random) 并覆写 `nextGaussianFloat64Implement` 函数时，调用子类的该函数将会返回覆写的函数的返回值。

参数：

- mean!: [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - 均值，默认值 0.0。
- sigma!: [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - 标准差，默认值 1.0。

返回值：

- [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - 一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的随机数。

### func nextGaussianFloat32Implement(Float32, Float32)

```cangjie
protected open func nextGaussianFloat32Implement(mean: Float32, sigma: Float32): Float32
```

功能： `nextGaussianFloat32` 的实现函数，获取一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的符合指定均值与标准差的高斯分布的随机数。

获取一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型，且符合均值为 `mean` 标准差为 `sigma` 的高斯分布的随机数。其中均值是期望值，可解释为位置参数，决定了分布的位置，标准差可解释为尺度参数，决定了分布的幅度。此函数是 `nextGaussianFloat32` 的实现函数，非公开，当子类继承 [Random](random_package_classes.md#class-random) 并覆写此函数时，调用子类的 `nextGaussianFloat32` 函数将会返回此函数的返回值。

参数：

- mean: [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - 均值。
- sigma: [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - 标准差。

返回值：

- [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - 一个 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的随机数。

### func nextGaussianFloat64(Float64, Float64)

```cangjie
public func nextGaussianFloat64(mean!: Float64 = 0.0, sigma!: Float64 = 1.0): Float64
```

功能：获取一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的符合指定均值与标准差的高斯分布的随机数。

默认获取一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型且符合均值为 0.0 标准差为 1.0 的高斯分布的随机数。其中均值是期望值，可解释为位置参数，决定了分布的位置，标准差可解释为尺度参数，决定了分布的幅度。此函数调用了函数 `nextGaussianFloat64Implement` 得到返回值，所以当子类继承 [Random](random_package_classes.md#class-random) 并覆写 `nextGaussianFloat64Implement` 函数时，调用子类的该函数将会返回覆写的函数的返回值。

参数：

- mean!: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 均值，默认值 0.0。
- sigma!: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 标准差，默认值 1.0。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的随机数。

### func nextGaussianFloat64Implement(Float64, Float64)

```cangjie
protected open func nextGaussianFloat64Implement(mean: Float64, sigma: Float64): Float64
```

功能： `nextGaussianFloat64` 的实现函数，获取一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的符合指定均值与标准差的高斯分布的随机数。

获取一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型，且符合均值为 `mean` 标准差为 `sigma` 的高斯分布的随机数。其中均值是期望值，可解释为位置参数，决定了分布的位置，标准差可解释为尺度参数，决定了分布的幅度。此函数是 `nextGaussianFloat64` 的实现函数，非公开，当子类继承 [Random](random_package_classes.md#class-random) 并覆写此函数时，调用子类的 `nextGaussianFloat64` 函数将会返回此函数的返回值。

参数：

- mean: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 均值。
- sigma: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 标准差。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 一个 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的随机数。

### func nextInt16()

```cangjie
public open func nextInt16(): Int16
```

功能：获取一个 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型的伪随机数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 一个 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型的伪随机数。

### func nextInt16(Int16)

```cangjie
public open func nextInt16(upper: Int16): Int16
```

功能：获取一个范围在 [0, `upper`) 的 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型的伪随机数。

参数：

- upper: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 表示生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [Int16](../../core/core_package_api/core_package_intrinsics.md#int16).Max]。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 一个 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 小于等于 0，抛出异常。

### func nextInt32()

```cangjie
public open func nextInt32(): Int32
```

功能：获取一个 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型的伪随机数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 一个 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型的伪随机数。

### func nextInt32(Int32)

```cangjie
public open func nextInt32(upper: Int32): Int32
```

功能：获取一个范围在 [0, `upper`) 的 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型的伪随机数。

参数：

- upper: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 表示生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [Int32](../../core/core_package_api/core_package_intrinsics.md#int32).Max]。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 一个 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 小于等于 0，抛出异常。

### func nextInt64()

```cangjie
public open func nextInt64(): Int64
```

功能：获取一个 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的伪随机数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 一个 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的伪随机数。

### func nextInt64(Int64)

```cangjie
public open func nextInt64(upper: Int64): Int64
```

功能：获取一个范围在 [0, `upper`) 的 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的伪随机数。

参数：

- upper: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [Int64](../../core/core_package_api/core_package_intrinsics.md#int64).Max]。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 一个 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 小于等于 0，抛出异常。

### func nextInt8()

```cangjie
public open func nextInt8(): Int8
```

功能：获取一个 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的伪随机数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 一个 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的伪随机数。

### func nextInt8(Int8): Int8

```cangjie
public open func nextInt8(upper: Int8): Int8
```

功能：获取一个范围在 [0, `upper`) 的 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的伪随机数。

参数：

- upper: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [Int8](../../core/core_package_api/core_package_intrinsics.md#int8).Max]。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 一个 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 小于等于 0，抛出异常。

### func nextUInt16()

```cangjie
public open func nextUInt16(): UInt16
```

功能：获取一个 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型的伪随机数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 一个 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型的伪随机数。

### func nextUInt16(UInt16)

```cangjie
public open func nextUInt16(upper: UInt16): UInt16
```

功能：获取一个范围在 [0, `upper`) 的 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型的伪随机数。

参数：

- upper: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).Max]。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 一个 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 等于 0，抛出异常。

### func nextUInt32()

```cangjie
public open func nextUInt32(): UInt32
```

功能：获取一个 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型的伪随机数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 一个 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型的伪随机数。

### func nextUInt32(UInt32)

```cangjie
public open func nextUInt32(upper: UInt32): UInt32
```

功能：获取一个范围在 [0, `upper`) 的 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型的伪随机数。

参数：

- upper: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).Max]。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 一个 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 等于 0，抛出异常。

### func nextUInt64()

```cangjie
public open func nextUInt64(): UInt64
```

功能：获取一个 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型的伪随机数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 一个 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型的伪随机数。

### func nextUInt64(UInt64)

```cangjie
public open func nextUInt64(upper: UInt64): UInt64
```

功能：获取一个范围在 [0, `upper`) 的 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型的伪随机数。

参数：

- upper: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).Max]。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 一个 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 等于 0，抛出异常。

### func nextUInt8()

```cangjie
public open func nextUInt8(): UInt8
```

功能：获取一个 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型的伪随机数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 一个 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型的伪随机数。

### func nextUInt8(UInt8)

```cangjie
public open func nextUInt8(upper: UInt8): UInt8
```

功能：获取一个范围在 [0, `upper`) 的 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型的伪随机数。

参数：

- upper: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 生成的伪随机数范围上界（不包括 `upper`），取值范围 (0, [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).Max]。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 一个 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型的伪随机数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 `upper` 等于 0，抛出异常。

### func nextUInt8s(Array\<UInt8>)

```cangjie
public open func nextUInt8s(array: Array<UInt8>): Array<UInt8>
```

功能：生成随机数替换入参数组中的每个元素。

参数：

- array: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)> - 被替换的数组

返回值：

- [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)> - 返回替换后的 [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)。
