# 类

## class DebugDataProvider

```cangjie
public class DebugDataProvider <: FuzzDataProvider
```

功能：此类继承了 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 类型，额外增加了调试信息。

父类型：

- [FuzzDataProvider](#class-fuzzdataprovider)

### func consumeAll()

```cangjie
public override func consumeAll(): Array<UInt8>
```

功能：将所有数据转换成 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)> - [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

### func consumeAllAsAscii()

```cangjie
public override func consumeAllAsAscii(): String
```

功能：将所有数据转换成 Ascii [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - Ascii [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeAllAsString()

```cangjie
public override func consumeAllAsString(): String
```

功能：将所有数据转换成 utf8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - utf8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeAsciiString(Int64)

```cangjie
public override func consumeAsciiString(maxLength: Int64): String
```

功能：将数据转换成 Ascii  [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

参数：

- maxLength: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型的最大长度。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeBool()

```cangjie
public override func consumeBool(): Bool
```

功能：将数据转换成 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型实例。

返回值：

- [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) - [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型实例。

### func consumeBools(Int64)

```cangjie
public override func consumeBools(count: Int64): Array<Bool>
```

功能：将指定数量的数据转换成 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)> - [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型数组。

### func consumeByte()

```cangjie
public override func consumeByte(): Byte
```

功能：将数据转换成 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型实例。

返回值：

- [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) - [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型实例。

### func consumeBytes(Int64)

```cangjie
public override func consumeBytes(count: Int64): Array<Byte>
```

功能：将指定数量的数据转换成 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)> - [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型数组。

### func consumeFloat32()

```cangjie
public override func consumeFloat32(): Float32
```

功能：将数据转换成 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) 类型实例。

返回值：

- [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) - [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) 类型实例。

### func consumeFloat64()

```cangjie
public override func consumeFloat64(): Float64
```

功能：将数据转换成 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 类型实例。

返回值：

- [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) - [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 类型实例。

### func consumeInt16()

```cangjie
public override func consumeInt16(): Int16
```

功能：将数据转换成 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型实例。

返回值：

- [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) - [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型实例。

### func consumeInt16s(Int64)

```cangjie
public override func consumeInt16s(count: Int64): Array<Int16>
```

功能：将指定数量的数据转换成 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)> - [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型数组。

### func consumeInt32()

```cangjie
public override func consumeInt32(): Int32
```

功能：将数据转换成 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型实例。

返回值：

- [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型实例。

### func consumeInt32s(Int64)

```cangjie
public override func consumeInt32s(count: Int64): Array<Int32>
```

功能：将指定数量的数据转换成 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)> - [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型数组。

### func consumeInt64()

```cangjie
public override func consumeInt64(): Int64
```

功能：将数据转换成 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型实例。

返回值：

- [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型实例。

### func consumeInt64s(Int64)

```cangjie
public override func consumeInt64s(count: Int64): Array<Int64>
```

功能：将指定数量的数据转换成 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)> - [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型数组。

### func consumeInt8()

```cangjie
public override func consumeInt8(): Int8
```

功能：将数据转换成 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型实例。

返回值：

- [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) - [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型实例。

### func consumeInt8s(Int64)

```cangjie
public override func consumeInt8s(count: Int64): Array<Int8>
```

功能：将指定数量的数据转换成 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)> - [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型数组。

### func consumeRune()

```cangjie
public override func consumeRune(): Rune
```

功能：将数据转换成 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型实例。

返回值：

- [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) - [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型实例。

### func consumeString(Int64)

```cangjie
public override func consumeString(maxLength: Int64): String
```

功能：将数据转换成 utf8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

参数：

- maxLength: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型的最大长度。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeUInt16()

```cangjie
public override func consumeUInt16(): UInt16
```

功能：将数据转换成 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型实例。

返回值：

- [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) - [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型实例。

### func consumeUInt16s(Int64)

```cangjie
public override func consumeUInt16s(count: Int64): Array<UInt16>
```

功能：将指定数量的数据转换成 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)> - [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型数组。

### func consumeUInt32()

```cangjie
public override func consumeUInt32(): UInt32
```

功能：将数据转换成 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型实例。

返回值：

- [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) - [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型实例。

### func consumeUInt32s(Int64)

```cangjie
public override func consumeUInt32s(count: Int64): Array<UInt32>
```

功能：将指定数量的数据转换成 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)> - [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型数组。

### func consumeUInt64()

```cangjie
public override func consumeUInt64(): UInt64
```

功能：将数据转换成 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型实例。

返回值：

- [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) - [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型实例。

### func consumeUInt64s(Int64)

```cangjie
public override func consumeUInt64s(count: Int64): Array<UInt64>
```

功能：将指定数量的数据转换成 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)> - [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型数组。

### func consumeUInt8()

```cangjie
public override func consumeUInt8(): UInt8
```

功能：将数据转换成 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型实例。

返回值：

- [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) - [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型实例。

### func consumeUInt8s(Int64)

```cangjie
public override func consumeUInt8s(count: Int64): Array<UInt8>
```

功能：将指定数量的数据转换成 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)> - [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

### func wrap(FuzzDataProvider)

```cangjie
public static func wrap(dp: FuzzDataProvider): DebugDataProvider
```

功能：根据 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 实例创建 [DebugDataProvider](fuzz_package_classes.md#class-debugdataprovider) 实例。

参数：

- dp: [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) - [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 类型实例。

返回值：

- [DebugDataProvider](fuzz_package_classes.md#class-debugdataprovider) - 类型实例。

## class Fuzzer

```cangjie
public class Fuzzer {
    public init(targetFunction: (Array<UInt8>) -> Int32)
    public init(targetFunction: (Array<UInt8>) -> Int32, args: Array<String>)
    public init(targetFunction: (FuzzDataProvider) -> Int32)
    public init(targetFunction: (FuzzDataProvider) -> Int32, args: Array<String>)
}
```

功能：[Fuzzer](fuzz_package_classes.md#class-fuzzer) 类提供了 fuzz 工具的创建。用户提供需要进行 fuzz 测试的函数 `targetFunction`，以及设置特定的 fuzz 运行参数 `args` 比如 fuzz 执行次数、初始种子、生成数据最大长度等，可创建相应类型的 [Fuzzer](fuzz_package_classes.md#class-fuzzer)。

### init((Array\<UInt8>) -> Int32)

```cangjie
public init(targetFunction: (Array<UInt8>) -> Int32)
```

功能：根据以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数，创建 [Fuzzer](fuzz_package_classes.md#class-fuzzer) 实例。

参数：

- targetFunction: ([Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

### init((Array\<UInt8>) -> Int32, Array\<String>)

```cangjie
public init(targetFunction: (Array<UInt8>) -> Int32, args: Array<String>)
```

功能：根据以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数，以及 Fuzz 运行参数，创建 [Fuzzer](fuzz_package_classes.md#class-fuzzer) 实例。

参数：

- targetFunction: ([Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。
- args: [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)> - Fuzz 运行参数。

### init((FuzzDataProvider) -> Int32)

```cangjie
public init(targetFunction: (FuzzDataProvider) -> Int32)
```

功能：根据以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数，创建 [Fuzzer](fuzz_package_classes.md#class-fuzzer) 实例。

参数：

- targetFunction: ([FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider)) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

### init((FuzzDataProvider) -> Int32, Array\<String>)

```cangjie
public init(targetFunction: (FuzzDataProvider) -> Int32, args: Array<String>)
```

功能：根据以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数，以及 Fuzz 运行参数，创建 [Fuzzer](fuzz_package_classes.md#class-fuzzer) 实例。

参数：

- targetFunction: ([FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider)) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。
- args: [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)> - Fuzz 运行参数。

### func disableDebugDataProvider()

```cangjie
public func disableDebugDataProvider(): Unit
```

功能：关闭调试信息打印功能，当 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider).consumeXXX 被调用时，返回值将不被打印到 `stdout`。

### func disableFakeCoverage()

```cangjie
public func disableFakeCoverage(): Unit
```

功能：关闭调用 `enableFakeCoverage` 对 Fuzz 的影响。

### func enableDebugDataProvider()

```cangjie
public func enableDebugDataProvider(): Unit
```

功能：启用调试信息打印功能，当 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider).consumeXXX 被调用时，返回值将被打印到 `stdout`。该功能默认为关闭。

### func enableFakeCoverage()

```cangjie
public func enableFakeCoverage(): Unit
```

功能：创建一块虚假的覆盖率反馈区域，保持 Fuzz 持续进行。在 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 模式下，前几轮运行时可能由于数据不足而导致没有覆盖率，libfuzzer 会退出。该功能默认为关闭。

### func getArgs()

```cangjie
public func getArgs(): Array<String>
```

功能：获取 Fuzz 运行参数。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)> - 当前 Fuzz 运行参数。

### func setArgs(Array\<String>)

```cangjie
public func setArgs(args: Array<String>): Unit
```

功能：设置 Fuzz 运行参数。

参数：

- args: [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)> - Fuzz 运行参数。

### func setTargetFunction((Array\<UInt8>) -> Int32)

```cangjie
public func setTargetFunction(targetFunction: (Array<UInt8>) -> Int32): Unit
```

功能：设置 Fuzz 目标函数。

参数：

- targetFunction: ([Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

### func setTargetFunction((FuzzDataProvider) -> Int32)

```cangjie
public func setTargetFunction(targetFunction: (FuzzDataProvider) -> Int32): Unit
```

功能：设置 Fuzz 目标函数。

参数：

- targetFunction: ([FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider)) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

### func startFuzz()

```cangjie
public func startFuzz(): Unit
```

功能：执行 Fuzz。

## class FuzzerBuilder

```cangjie
public class FuzzerBuilder {
    public init(targetFunction: (Array<UInt8>) -> Int32)
    public init(targetFunction: (FuzzDataProvider) -> Int32)
}
```

功能：此类用于 [Fuzzer](fuzz_package_classes.md#class-fuzzer) 类的构建。

### init((Array\<UInt8>) -> Int32)

```cangjie
public init(targetFunction: (Array<UInt8>) -> Int32)
```

功能：根据以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数，创建 [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) 实例。

参数：

- targetFunction: ([Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

### init((FuzzDataProvider) -> Int32)

```cangjie
public init(targetFunction: (FuzzDataProvider) -> Int32)
```

功能：根据以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数，创建 [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) 实例。

参数：

- targetFunction: ([FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider)) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

### func build()

```cangjie
public func build(): Fuzzer
```

功能：生成一个 [Fuzzer](fuzz_package_classes.md#class-fuzzer) 实例。

返回值：

- [Fuzzer](fuzz_package_classes.md#class-fuzzer) - [Fuzzer](fuzz_package_classes.md#class-fuzzer) 实例。

### func setArgs(Array\<String>)

```cangjie
public func setArgs(args: Array<String>): FuzzerBuilder
```

功能：设置 Fuzz 运行参数。

参数：

- args: [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)> - Fuzz 运行参数。

返回值：

- [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) - 当前 [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) 实例。

### func setTargetFunction((Array\<UInt8>) -> Int32)

```cangjie
public func setTargetFunction(targetFunction: (Array<UInt8>) -> Int32): FuzzerBuilder
```

功能：设置 Fuzz 目标函数。

参数：

- targetFunction: ([Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 数组为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

返回值：

- [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) - 当前 [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) 实例。

### func setTargetFunction((FuzzDataProvider) -> Int32)

```cangjie
public func setTargetFunction(targetFunction: (FuzzDataProvider) -> Int32): FuzzerBuilder
```

功能：设置 Fuzz 目标函数。

参数：

- targetFunction: ([FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider)) ->[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 以 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 为参数，以 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 为返回值的目标函数。

返回值：

- [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) - 当前 [FuzzerBuilder](fuzz_package_classes.md#class-fuzzerbuilder) 实例。

## class FuzzDataProvider

```cangjie
public open class FuzzDataProvider {
    public let data: Array<UInt8>
    public var remainingBytes: Int64
    public var offset: Int64
}
```

功能：[FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 是一个工具类，目的是将变异数据的字节流转化为标准的仓颉基本数据。

当前支持的数据结构如下：

| 目标类型          | API                                  | 说明                                               |
|---------------|--------------------------------------|--------------------------------------------------|
| [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)          | consumeBool()                        | 获取 1 个 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。         |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)>   | consumeBools(count: Int64)           | 获取 N 个 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。         |
| [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)          | consumeByte()                        | 获取 1 个 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。         |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)>   | consumeBytes(count: Int64)           | 获取 N 个 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。         |
| [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)         | consumeUInt8()                       | 获取 1 个 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)        | consumeUInt16()                      | 获取 1 个 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。       |
| [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)        | consumeUInt32()                      | 获取 1 个 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。       |
| [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)        | consumeUInt64()                      | 获取 1 个 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。       |
| [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)          | consumeInt8()                        | 获取 1 个 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。         |
| [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)         | consumeInt16()                       | 获取 1 个 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)         | consumeInt32()                       | 获取 1 个 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)         | consumeInt32()                       | 获取 1 个 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)         | consumeFloat32()                       | 获取 1 个 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)         | consumeFloat64()                       | 获取 1 个 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>  | consumeUInt8s(count: Int64)          | 获取 N 个 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)> | consumeUInt16s(count: Int64)         | 获取 N 个 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。       |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)> | consumeUInt32s(count: Int64)         | 获取 N 个 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。       |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)> | consumeUInt64s(count: Int64)         | 获取 N 个 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。       |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)>   | consumeInt8s(count: Int64)           | 获取 N 个 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。         |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)>  | consumeInt16s(count: Int64)          | 获取 N 个 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)>  | consumeInt32s(count: Int64)          | 获取 N 个 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)>  | consumeInt32s(count: Int64)          | 获取 N 个 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。        |
| [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune)          | consumeRune()                        | 获取 1 个 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune)，变异数据长度不足时，抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)。         |
| [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)        | consumeAsciiString(maxLength: Int64) | 获取 1 个纯 ASCII 的 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)，长度为 0 到 maxLength，可以为 0。           |
| [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)        | consumeString(maxLength: Int64)      | 获取 1 个 UTF8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)，长度为 0 到 maxLength，可以为 0。             |
| [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>  | consumeAll()                         | 将 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 中的剩余内容全部转化为字节数组。                    |
| [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)        | consumeAllAsAscii()                  | 将 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 中的剩余内容全部转化为纯 ASCII 的 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)。           |
| [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)        | consumeAllAsString()                 | 将 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 中的剩余内容全部转化为 UTF8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)，末尾多余的字符不会被消耗。 |

在数据长度不足时，调用上述大部分虽然会抛出 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception)，但编写 fuzz 函数时通常并不需要对它进行处理，[ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception) 默认会被 fuzz 框架捕获，告诉 libfuzzer 该次运行无效，请继续下一轮变异。随着执行时间的变长，变异数据也会逐渐变长，直到满足 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 的需求。

如果达到了 `max_len` 仍无法满足 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 的需求，则进程退出，请修改 fuzz 测试用例（推荐） 或 增大 `max_len`（不推荐）。

### let data

```cangjie
public let data: Array<UInt8>
```

功能：变异数据。

类型：[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>

### var offset

```cangjie
public var offset: Int64
```

功能：已转化的字节数。

类型：[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)

### var remainingBytes

```cangjie
public var remainingBytes: Int64
```

功能：剩余字节数。

类型：[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)

### func consumeAll()

```cangjie
public open func consumeAll(): Array<UInt8>
```

功能：将所有数据转换成 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)> - [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

### func consumeAllAsAscii()

```cangjie
public open func consumeAllAsAscii(): String
```

功能：将所有数据转换成 Ascii [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - Ascii [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeAllAsString()

```cangjie
public open func consumeAllAsString(): String
```

功能：将所有数据转换成 utf8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - utf8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeAsciiString(Int64)

```cangjie
public open func consumeAsciiString(maxLength: Int64): String
```

功能：将数据转换成 Ascii  [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

参数：

- maxLength: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型的最大长度。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeBool()

```cangjie
public open func consumeBool(): Bool
```

功能：将数据转换成 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型实例。

返回值：

- [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) - [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型实例。

### func consumeBools(Int64)

```cangjie
public open func consumeBools(count: Int64): Array<Bool>
```

功能：将指定数量的数据转换成 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)> - [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型数组。

### func consumeByte()

```cangjie
public open func consumeByte(): Byte
```

功能：将数据转换成 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型实例。

返回值：

- [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) - [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型实例。

### func consumeBytes(Int64)

```cangjie
public open func consumeBytes(count: Int64): Array<Byte>
```

功能：将指定数量的数据转换成 [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../../std/core/core_package_api/core_package_types.md#type-byte)> - [Byte](../../../std/core/core_package_api/core_package_types.md#type-byte) 类型数组。

### func consumeFloat32()

```cangjie
public open func consumeFloat32(): Float32
```

功能：将数据转换成 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) 类型实例。

返回值：

- [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) - [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) 类型实例。

### func consumeFloat64()

```cangjie
public open func consumeFloat64(): Float64
```

功能：将数据转换成 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 类型实例。

返回值：

- [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) - [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 类型实例。

### func consumeInt16()

```cangjie
public open func consumeInt16(): Int16
```

功能：将数据转换成 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型实例。

返回值：

- [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) - [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型实例。

### func consumeInt16s(Int64)

```cangjie
public open func consumeInt16s(count: Int64): Array<Int16>
```

功能：将指定数量的数据转换成 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)> - [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型数组。

### func consumeInt32()

```cangjie
public open func consumeInt32(): Int32
```

功能：将数据转换成 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型实例。

返回值：

- [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型实例。

### func consumeInt32s(Int64)

```cangjie
public open func consumeInt32s(count: Int64): Array<Int32>
```

功能：将指定数量的数据转换成 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)> - [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型数组。

### func consumeInt64()

```cangjie
public open func consumeInt64(): Int64
```

功能：将数据转换成 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型实例。

返回值：

- [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型实例。

### func consumeInt64s(Int64)

```cangjie
public open func consumeInt64s(count: Int64): Array<Int64>
```

功能：将指定数量的数据转换成 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)> - [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型数组。

### func consumeInt8()

```cangjie
public open func consumeInt8(): Int8
```

功能：将数据转换成 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型实例。

返回值：

- [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) - [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型实例。

### func consumeInt8s(Int64)

```cangjie
public open func consumeInt8s(count: Int64): Array<Int8>
```

功能：将指定数量的数据转换成 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)> - [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型数组。

### func consumeRune()

```cangjie
public open func consumeRune(): Rune
```

功能：将数据转换成 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型实例。

返回值：

- [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) - [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型实例。

### func consumeString(Int64)

```cangjie
public open func consumeString(maxLength: Int64): String
```

功能：将数据转换成 utf8 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

参数：

- maxLength: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型的最大长度。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实例。

### func consumeUInt16()

```cangjie
public open func consumeUInt16(): UInt16
```

功能：将数据转换成 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型实例。

返回值：

- [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) - [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型实例。

### func consumeUInt16s(Int64)

```cangjie
public open func consumeUInt16s(count: Int64): Array<UInt16>
```

功能：将指定数量的数据转换成 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)> - [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型数组。

### func consumeUInt32()

```cangjie
public open func consumeUInt32(): UInt32
```

功能：将数据转换成 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型实例。

返回值：

- [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) - [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型实例。

### func consumeUInt32s(Int64)

```cangjie
public open func consumeUInt32s(count: Int64): Array<UInt32>
```

功能：将指定数量的数据转换成 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)> - [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型数组。

### func consumeUInt64()

```cangjie
public open func consumeUInt64(): UInt64
```

功能：将数据转换成 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型实例。

返回值：

- [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) - [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型实例。

### func consumeUInt64s(Int64)

```cangjie
public open func consumeUInt64s(count: Int64): Array<UInt64>
```

功能：将指定数量的数据转换成 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)> - [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型数组。

### func consumeUInt8()

```cangjie
public open func consumeUInt8(): UInt8
```

功能：将数据转换成 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型实例。

返回值：

- [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) - [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型实例。

### func consumeUInt8s(Int64)

```cangjie
public open func consumeUInt8s(count: Int64): Array<UInt8>
```

功能：将指定数量的数据转换成 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

参数：

- count: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 指定转换的数据量。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)> - [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型数组。

### static func withCangjieData(Array\<UInt8>)

```cangjie
public static func withCangjieData(data: Array<UInt8>): FuzzDataProvider
```

功能：使用 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)> 类型的数据生成 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 类型实例。

参数：

- data: [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)> - 输入的外部数据。

返回值：

- [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) - 构造的 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 类型实例。

### static func withNativeData(CPointer\<UInt8>, Int64)

```cangjie
public static unsafe func withNativeData(data: CPointer<UInt8>, length: Int64): FuzzDataProvider
```

功能：使用 C 指针数据生成 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 类型实例。

参数：

- data: [CPointer](../../../std/core/core_package_api/core_package_intrinsics.md#cpointert)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)> - 输入的外部数据。
- length: [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 数据长度。

返回值：

- [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) - 构造的 [FuzzDataProvider](fuzz_package_classes.md#class-fuzzdataprovider) 类型实例。
