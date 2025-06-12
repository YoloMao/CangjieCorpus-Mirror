# 内置类型

## Bool

功能：表示布尔类型，有 `true` 和 `false` 两种取值。

### extend Bool <: Equatable\<Bool>

```cangjie
extend Bool <: Equatable<Bool>
```

功能：为 [Bool](core_package_intrinsics.md#bool) 类型扩展 [Equatable](core_package_interfaces.md#interface-equatablet)\<[Bool](core_package_intrinsics.md#bool)> 接口，支持判等操作。

父类型：

- [Equatable](core_package_interfaces.md#interface-equatablet)\<[Bool](#bool)>

### extend Bool <: Hashable

```cangjie
extend Bool <: Hashable
```

功能：为 [Bool](core_package_intrinsics.md#bool) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Bool <: ToString

```cangjie
extend Bool <: ToString
```

功能：为 [Bool](core_package_intrinsics.md#bool) 类型其扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Bool](core_package_intrinsics.md#bool) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## CPointer\<T>

功能：表示 `T` 类型实例的指针，在与 C 语言互操作的场景下使用，对应 C 语言的 `T*`。

其中 `T` 必须满足 [CType](core_package_interfaces.md#interface-ctype) 约束。

[CPointer](core_package_intrinsics.md#cpointert) 类型必须满足：

- 大小和对齐与平台相关。
- 对它做加减法算术运算、读写内存，是需要在 unsafe 上下文操作的。
- [CPointer](core_package_intrinsics.md#cpointert)\<T1> 可以在 unsafe 上下文中使用类型强制转换，变成 [CPointer](core_package_intrinsics.md#cpointert)\<T2> 类型。

### extend\<T> CPointer\<T>

```cangjie
extend<T> CPointer<T>
```

功能：为 [CPointer](core_package_intrinsics.md#cpointert)\<T> 扩展一些必要的指针使用相关接口，包含判空、读写数据等接口。

其中泛型 `T` 为指针类型，其满足 [CType](core_package_interfaces.md#interface-ctype) 约束。对 [CPointer](core_package_intrinsics.md#cpointert) 做运算需要在 `unsafe` 上下文中进行。

#### func asResource()

```cangjie
public func asResource(): CPointerResource<T>
```

功能：获取该指针 [CPointerResource](core_package_structs.md#struct-cpointerresourcet-where-t--ctype) 实例，后者可以在 `try-with-resource` 语法上下文中实现内容自动释放。

返回值：

- [CPointerResource](core_package_structs.md#struct-cpointerresourcet-where-t--ctype)\<T> - 当前指针对应的 [CPointerResource](core_package_structs.md#struct-cpointerresourcet-where-t--ctype) 实例。

#### func isNotNull()

```cangjie
public func isNotNull(): Bool
```

功能：判断指针是否不为空。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果不为空返回 true，否则返回 false。

#### func isNull()

```cangjie
public func isNull(): Bool
```

功能：判断指针是否为空。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果为空返回 true，否则返回 false。

#### func read()

```cangjie
public unsafe func read(): T
```

功能：读取第一个数据，该接口需要用户保证指针的合法性，否则发生未定义行为。

返回值：

- T - 该对象类型的第一个数据。

#### func read(Int64)

```cangjie
public unsafe func read(idx: Int64): T
```

功能：根据下标读取对应的数据，该接口需要用户保证指针的合法性，否则发生未定义行为。

参数：

- idx: [Int64](core_package_intrinsics.md#int64) - 要获取数据的下标。

返回值：

- T - 输入下标对应的数据。

#### func toUIntNative()

```cangjie
public func toUIntNative(): UIntNative
```

功能：获取该指针的整型形式。

返回值：

- [UIntNative](core_package_intrinsics.md#uintnative) - 该指针的整型形式。

#### func write(Int64, T)

```cangjie
public unsafe func write(idx: Int64, value: T): Unit
```

功能：在指定下标位置写入一个数据，该接口需要用户保证指针的合法性，否则发生未定义行为。

参数：

- idx: [Int64](core_package_intrinsics.md#int64) - 指定的下标位置。
- value: T - 写入的数据。

#### func write(T)

```cangjie
public unsafe func write(value: T): Unit
```

功能：写入一个数据，该数据总是在第一个，该接口需要用户保证指针的合法性，否则发生未定义行为。

参数：

- value: T - 要写入的数据。

#### operator func +(Int64)

```cangjie
public unsafe operator func +(offset: Int64): CPointer<T>
```

功能：[CPointer](core_package_intrinsics.md#cpointert) 对象指针后移，同 C 语言的指针加法操作。

参数：

- offset: [Int64](core_package_intrinsics.md#int64) - 偏移量。

返回值：

- [CPointer](core_package_intrinsics.md#cpointert)\<T> - 返回偏移后的指针。

#### operator func -(Int64)

```cangjie
public unsafe operator func -(offset: Int64): CPointer<T>
```

功能：[CPointer](core_package_intrinsics.md#cpointert) 对象指针前移，同 C 语言的指针减法操作。

参数：

- offset: [Int64](core_package_intrinsics.md#int64) - 偏移量。

返回值：

- [CPointer](core_package_intrinsics.md#cpointert)\<T> - 返回偏移后的指针。

## CString

功能：表示 C 风格字符串，在与 C 语言互操作的场景下使用。

可以通过 [CString](core_package_intrinsics.md#cstring) 的构造函数或 [LibC](core_package_structs.md#struct-libc) 的 `mallocCString` 创建 C 风格字符串，如需在仓颉端释放，则调用 [LibC](core_package_structs.md#struct-libc) 的 free 方法。

### extend CString <: ToString

```cangjie
extend CString <: ToString
```

功能：为 [CString](core_package_intrinsics.md#cstring) 类型扩展一些字符串指针常用方法，包括判空、获取长度、判等、获取子串等。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func asResource()

```cangjie
public func asResource(): CStringResource
```

功能：获取当前 [CString](core_package_intrinsics.md#cstring) 实例对应的 [CStringResource](core_package_structs.md#struct-cstringresource) C 字符串资源类型实例。

[CStringResource](core_package_structs.md#struct-cstringresource) 实现了 [Resource](core_package_interfaces.md#interface-resource) 接口，可以在 `try-with-resource` 语法上下文中实现资源自动释放。

返回值：

- [CStringResource](core_package_structs.md#struct-cstringresource) - 对应的 [CStringResource](core_package_structs.md#struct-cstringresource) C 字符串资源类型实例。

#### func compare(CString)

```cangjie
public func compare(str: CString): Int32
```

功能：按字典序比较两个字符串，同 C 语言中的 `strcmp`。

参数：

- str: [CString](core_package_intrinsics.md#cstring) - 比较的目标字符串。

返回值：

- [Int32](core_package_intrinsics.md#int32) - 两者相等返回 0，如果当前字符串比参数 str 小，返回 -1，否则返回 1。

异常：

- [Exception](core_package_exceptions.md#class-exception) - 如果被比较的两个 [CString](core_package_intrinsics.md#cstring) 中存在空指针，抛出异常。

#### func endsWith(CString)

```cangjie
public func endsWith(suffix: CString): Bool
```

功能：判断字符串是否包含指定后缀。

参数：

- suffix: [CString](core_package_intrinsics.md#cstring) - 匹配的目标后缀字符串。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果该字符串包含 suffix 后缀，返回 true，如果该字符串不包含 suffix 后缀，返回 false，特别地，如果原字符串或者 suffix 后缀字符串指针为空，均返回 false。

#### func equals(CString)

```cangjie
public func equals(rhs: CString): Bool
```

功能：判断两个字符串是否相等。

参数：

- rhs: [CString](core_package_intrinsics.md#cstring) - 比较的目标字符串。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果两个字符串相等，返回 true，否则返回 false。

#### func equalsLower(CString)

```cangjie
public func equalsLower(rhs: CString): Bool
```

功能：判断两个字符串是否相等，忽略大小写。

参数：

- rhs: [CString](core_package_intrinsics.md#cstring) - 匹配的目标字符串。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果两个字符串忽略大小写相等，返回 true，否则返回 false。

#### func getChars()

```cangjie
public func getChars(): CPointer<UInt8>
```

功能：获取该字符串的指针。

返回值：

- [CPointer](./core_package_intrinsics.md#cpointert)\<[UInt8](./core_package_intrinsics.md#uint8)> - 该字符串的指针。

#### func isEmpty()

```cangjie
public func isEmpty(): Bool
```

功能：判断字符串是否为空字符串。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果为空字符串或字符串指针为空，返回 true，否则返回 false。

#### func isNotEmpty()

```cangjie
public func isNotEmpty(): Bool
```

功能：判断字符串是否不为空字符串。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果不为空字符串，返回 true，如果字符串指针为空，返回 false。

#### func isNull()

```cangjie
public func isNull(): Bool
```

功能：判断字符串指针是否为空。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果字符串指针为空，返回 true，否则返回 false。

#### func size()

```cangjie
public func size(): Int64
```

功能：返回该字符串长度，同 C 语言中的 `strlen`。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 字符串长度。

#### func startsWith(CString)

```cangjie
public func startsWith(prefix: CString): Bool
```

功能：判断字符串是否包含指定前缀。

参数：

- prefix: [CString](core_package_intrinsics.md#cstring) - 匹配的目标前缀字符串。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果该字符串包含 prefix 前缀，返回 true，如果该字符串不包含 prefix 前缀，返回 false，特别地，如果原字符串或者 prefix 前缀字符串指针为空，均返回 false。

#### func subCString(UIntNative)

```cangjie
public func subCString(beginIndex: UIntNative): CString
```

功能：截取指定位置开始至字符串结束的子串。

> **注意：**
>
> 1. 该接口返回为字符串的副本，返回的子串使用完后需要手动 free。
> 2. 如果 beginIndex 与字符串长度相等，将返回空指针。

参数：

- beginIndex: [UIntNative](core_package_intrinsics.md#uintnative) - 截取的起始位置，取值范围为 [0, this.size()]。

返回值：

- [CString](core_package_intrinsics.md#cstring) - 截取的子串。

异常：

- [IndexOutOfBoundsException](core_package_exceptions.md#class-indexoutofboundsexception) - 如果 beginIndex 大于字符串长度，抛出异常。
- [IllegalMemoryException](core_package_exceptions.md#class-illegalmemoryexception) - 如果内存申请失败或内存拷贝失败时，抛出异常。

#### func subCString(UIntNative, UIntNative)

```cangjie
public func subCString(beginIndex: UIntNative, subLen: UIntNative): CString
```

功能：截取字符串的子串，指定起始位置和截取长度。

如果截取的末尾位置超出字符串长度，截取至字符串末尾。

> **注意：**
>
> 1. 该接口返回为字符串的副本，返回的子串使用完后需要手动 free。
> 2. 如果 beginIndex 等于于字符串长度，或 subLen 等于 0，返回空指针。

参数：

- beginIndex: [UIntNative](core_package_intrinsics.md#uintnative) - 截取的起始位置，取值范围为 [0, this.size()]。
- subLen: [UIntNative](core_package_intrinsics.md#uintnative) - 截取长度，取值范围为 [0, [UIntNative](core_package_intrinsics.md#uintnative).Max]。

返回值：

- [CString](core_package_intrinsics.md#cstring) - 截取的子串。

异常：

- [IndexOutOfBoundsException](core_package_exceptions.md#class-indexoutofboundsexception) - 如果 beginIndex 大于字符串长度，抛出异常。
- [IllegalMemoryException](core_package_exceptions.md#class-illegalmemoryexception) - 如果内存申请失败或内存拷贝失败时，抛出异常。

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [CString](core_package_intrinsics.md#cstring) 类型转为仓颉的 [String](core_package_structs.md#struct-string) 类型。

返回值：

- [String](core_package_structs.md#struct-string) - 转换后的字符串。

## Float16

功能：表示 16 位浮点数，符合 `IEEE 754` 中的半精度格式（`binary16`）。

### extend Float16 <: Comparable\<Float16>

```cangjie
extend Float16 <: Comparable<Float16>
```

功能：为 [Float16](core_package_intrinsics.md#float16) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Float16](core_package_intrinsics.md#float16)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Float16](#float16)>

#### func compare(Float16)

```cangjie
public func compare(rhs: Float16): Ordering
```

功能：判断当前 [Float16](core_package_intrinsics.md#float16) 值与指定 [Float16](core_package_intrinsics.md#float16) 值的大小关系。

参数：

- rhs: [Float16](core_package_intrinsics.md#float16) - 待比较的另一个 [Float16](core_package_intrinsics.md#float16) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Float16 <: FloatToBits

```cangjie
extend Float16 <: FloatToBits
```

功能：为 [Float16](core_package_intrinsics.md#float16) 实现 [FloatToBits](core_package_interfaces.md#interface-floattobits) 接口，支持与 [UInt16](core_package_intrinsics.md#uint16) 互相转换。

父类型：

- [FloatToBits](core_package_interfaces.md#interface-floattobits)

#### static func fromBits(UInt16)

```cangjie
public static func fromBits(bits: UInt16): Float16
```

功能：将指定的 [UInt16](core_package_intrinsics.md#uint16) 数转换为 [Float16](core_package_intrinsics.md#float16) 数。

参数：

- bits: [UInt16](core_package_intrinsics.md#uint16) - 要转换的数字。

返回值：

- [Float16](core_package_intrinsics.md#float16) - 转换结果，其位与参数 bits 值相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    let v = Float16.fromBits(0x4A40)
    @Assert(v, 12.5)
}
```

#### func toBits()

```cangjie
public func toBits(): UInt16
```

功能：将指定的 [Float16](core_package_intrinsics.md#float16) 数转换为以位表示的对应 [UInt16](core_package_intrinsics.md#uint16) 数。

返回值：

- [UInt16](core_package_intrinsics.md#uint16) - 转换结果，其值与 [Float16](core_package_intrinsics.md#float16) 的位表示相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    @Assert(12.5f16.toBits(), 0x4A40)
}
```

### extend Float16 <: Hashable

```cangjie
extend Float16 <: Hashable
```

功能：为 [Float16](core_package_intrinsics.md#float16) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Float16 <: ToString

```cangjie
extend Float16 <: ToString
```

功能：为 [Float16](core_package_intrinsics.md#float16) 类型其扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

默认保留 6 位小数，如需其他精度 [String](core_package_structs.md#struct-string) 请参考 [Formatter](../../format/format_package_api/format_package_interfaces.md#interface-formatter) 扩展。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Float16](core_package_intrinsics.md#float16) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Float32

功能：表示 32 位浮点数，符合 `IEEE 754` 中的单精度格式（`binary32`）。

### extend Float32 <: Comparable\<Float32>

```cangjie
extend Float32 <: Comparable<Float32>
```

功能：为 [Float32](core_package_intrinsics.md#float32) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Float32](core_package_intrinsics.md#float32)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Float32](#float32)>

#### func compare(Float32)

```cangjie
public func compare(rhs: Float32): Ordering
```

功能：判断当前 [Float32](core_package_intrinsics.md#float32) 值与指定 [Float32](core_package_intrinsics.md#float32) 值的大小关系。

参数：

- rhs: [Float32](core_package_intrinsics.md#float32) - 待比较的另一个 [Float32](core_package_intrinsics.md#float32) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Float32 <: FloatToBits

```cangjie
extend Float32 <: FloatToBits
```

功能：为 [Float32](core_package_intrinsics.md#float32) 实现 [FloatToBits](core_package_interfaces.md#interface-floattobits) 接口，支持与 [UInt32](core_package_intrinsics.md#uint32) 互相转换。

父类型：

- [FloatToBits](core_package_interfaces.md#interface-floattobits)

#### static func fromBits(UInt32)

```cangjie
public static func fromBits(bits: UInt32): Float32
```

功能：将指定的 [UInt32](core_package_intrinsics.md#uint32) 数转换为 [Float32](core_package_intrinsics.md#float32) 数。

参数：

- bits: [UInt32](core_package_intrinsics.md#uint32) - 要转换的数字。

返回值：

- [Float32](core_package_intrinsics.md#float32) - 转换结果，其位与参数 bits 值相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    let v = Float32.fromBits(0x41480000)
    @Assert(v, 12.5)
}
```

#### func toBits()

```cangjie
public func toBits(): UInt32
```

功能：将指定的 [Float32](core_package_intrinsics.md#float32) 数转换为以位表示的对应 [UInt32](core_package_intrinsics.md#uint32) 数。

返回值：

- [UInt32](core_package_intrinsics.md#uint32) - 转换结果，其值与 [Float32](core_package_intrinsics.md#float32) 的位表示相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    @Assert(12.5f32.toBits(), 0x41480000)
}
```

### extend Float32 <: Hashable

```cangjie
extend Float32 <: Hashable
```

功能：为 [Float32](core_package_intrinsics.md#float32) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Float32 <: ToString

```cangjie
extend Float32 <: ToString
```

功能：为 [Float32](core_package_intrinsics.md#float32) 类型其扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

默认保留 6 位小数，如需其他精度 [String](core_package_structs.md#struct-string) 请参考 [Formatter](../../format/format_package_api/format_package_interfaces.md#interface-formatter) 扩展。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Float32](core_package_intrinsics.md#float32) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Float64

功能：表示 64 位浮点数，符合 `IEEE 754` 中的双精度格式（`binary64`）。

### extend Float64 <: Comparable\<Float64>

```cangjie
extend Float64 <: Comparable<Float64>
```

功能：为 [Float64](core_package_intrinsics.md#float64) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Float64](core_package_intrinsics.md#float64)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Float64](#float64)>

#### func compare(Float64)

```cangjie
public func compare(rhs: Float64): Ordering
```

功能：判断当前 [Float64](core_package_intrinsics.md#float64) 值与指定 [Float64](core_package_intrinsics.md#float64) 值的大小关系。

参数：

- rhs: [Float64](core_package_intrinsics.md#float64) - 待比较的另一个 [Float64](core_package_intrinsics.md#float64) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Float64 <: FloatToBits

```cangjie
extend Float64 <: FloatToBits
```

功能：为 [Float64](core_package_intrinsics.md#float64) 实现 [FloatToBits](core_package_interfaces.md#interface-floattobits) 接口，支持与 [UInt64](core_package_intrinsics.md#uint64) 互相转换。

父类型：

- [FloatToBits](core_package_interfaces.md#interface-floattobits)

#### static func fromBits(UInt64)

```cangjie
public static func fromBits(bits: UInt64): Float64
```

功能：将指定的 [UInt64](core_package_intrinsics.md#uint64) 数转换为 [Float64](core_package_intrinsics.md#float64) 数。

参数：

- bits: [UInt64](core_package_intrinsics.md#uint64) - 要转换的数字。

返回值：

- [Float64](core_package_intrinsics.md#float64) - 转换结果，其位与参数 bits 值相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    let v = Float64.fromBits(0x4029000000000000)
    @Assert(v, 12.5)
}
```

#### func toBits()

```cangjie
public func toBits(): UInt64
```

功能：将指定的 Float64 数转换为以位表示的对应 [UInt64](core_package_intrinsics.md#uint64) 数。

返回值：

- [UInt64](core_package_intrinsics.md#uint64) - 转换结果，其值与 [Float64](core_package_intrinsics.md#float64) 的位表示相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    @Assert(12.5f64.toBits(), 0x4029000000000000)
}
```

### extend Float64 <: Hashable

```cangjie
extend Float64 <: Hashable
```

功能：为 [Float64](core_package_intrinsics.md#float64) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Float64 <: ToString

```cangjie
extend Float64 <: ToString
```

功能：为 [Float64](core_package_intrinsics.md#float64) 类型其扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

默认保留 6 位小数，如需其他精度 [String](core_package_structs.md#struct-string) 请参考 [Formatter](../../format/format_package_api/format_package_interfaces.md#interface-formatter) 扩展。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Float64](core_package_intrinsics.md#float64) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Int16

功能：表示 16 位有符号整型，表示范围为 [-2^{15}, 2^{15} - 1]。

### extend Int16 <: Comparable\<Int16>

```cangjie
extend Int16 <: Comparable<Int16>
```

功能：为 [Int16](core_package_intrinsics.md#int16) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int16](core_package_intrinsics.md#int16)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int16](#int16)>

#### func compare(Int16)

```cangjie
public func compare(rhs: Int16): Ordering
```

功能：判断当前 [Int16](core_package_intrinsics.md#int16) 值与指定 [Int16](core_package_intrinsics.md#int16) 值的大小关系。

参数：

- rhs: [Int16](core_package_intrinsics.md#int16) - 待比较的另一个 [Int16](core_package_intrinsics.md#int16) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Int16 <: Countable\<Int16>

```cangjie
extend Int16 <: Countable<Int16>
```

功能：为 [Int16](core_package_intrinsics.md#int16) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[Int16](core_package_intrinsics.md#int16)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[Int16](#int16)>

#### func next(Int64)

```cangjie
public func next(right: Int64): Int16
```

功能：获取当前 [Int16](core_package_intrinsics.md#int16) 值往右数 `right` 后所到位置的 [Int16](core_package_intrinsics.md#int16) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [Int16](core_package_intrinsics.md#int16) - 往右数 `right` 后所到位置的 [Int16](core_package_intrinsics.md#int16) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [Int16](core_package_intrinsics.md#int16) 值的位置信息，即将该 [Int16](core_package_intrinsics.md#int16) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [Int16](core_package_intrinsics.md#int16) 值的位置信息。

### extend Int16 <: Hashable

```cangjie
extend Int16 <: Hashable
```

功能：为 [Int16](core_package_intrinsics.md#int16) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Int16 <: ToString

```cangjie
extend Int16 <: ToString
```

功能：这里为 [Int16](core_package_intrinsics.md#int16) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Int16](core_package_intrinsics.md#int16) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Int32

功能：表示 32 位有符号整型，表示范围为 [-2^{31}, 2^{31} - 1]。

### extend Int32 <: Comparable\<Int32>

```cangjie
extend Int32 <: Comparable<Int32>
```

功能：为 [Int32](core_package_intrinsics.md#int32) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int32](core_package_intrinsics.md#int32)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int32](#int32)>

#### func compare(Int32)

```cangjie
public func compare(rhs: Int32): Ordering
```

功能：判断当前 [Int32](core_package_intrinsics.md#int32) 值与指定 [Int32](core_package_intrinsics.md#int32) 值的大小关系。

参数：

- rhs: [Int32](core_package_intrinsics.md#int32) - 待比较的另一个 [Int32](core_package_intrinsics.md#int32) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Int32 <: Countable\<Int32>

```cangjie
extend Int32 <: Countable<Int32>
```

功能：为 [Int32](core_package_intrinsics.md#int32) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[Int32](core_package_intrinsics.md#int32)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[Int32](#int32)>

#### func next(Int64)

```cangjie
public func next(right: Int64): Int32
```

功能：获取当前 [Int32](core_package_intrinsics.md#int32) 值往右数 `right` 后所到位置的 [Int32](core_package_intrinsics.md#int32) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [Int32](core_package_intrinsics.md#int32) - 往右数 `right` 后所到位置的 [Int32](core_package_intrinsics.md#int32) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [Int32](core_package_intrinsics.md#int32) 值的位置信息，即将该 [Int32](core_package_intrinsics.md#int32) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [Int32](core_package_intrinsics.md#int32) 值的位置信息。

### extend Int32 <: Hashable

```cangjie
extend Int32 <: Hashable
```

功能：为 [Int32](core_package_intrinsics.md#int32) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Int32 <: ToString

```cangjie
extend Int32 <: ToString
```

功能：这里为 [Int32](core_package_intrinsics.md#int32) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Int32](core_package_intrinsics.md#int32) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Int64

功能：表示 64 位有符号整型，表示范围为 [-2^{63}, 2^{63} - 1]。

### extend Int64 <: Comparable\<Int64>

```cangjie
extend Int64 <: Comparable<Int64>
```

功能：为 [Int64](core_package_intrinsics.md#int64) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int64](core_package_intrinsics.md#int64)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int64](#int64)>

#### func compare(Int64)

```cangjie
public func compare(rhs: Int64): Ordering
```

功能：判断当前 [Int64](core_package_intrinsics.md#int64) 值与指定 [Int64](core_package_intrinsics.md#int64) 值的大小关系。

参数：

- rhs: [Int64](core_package_intrinsics.md#int64) - 待比较的另一个 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ 如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Int64 <: Countable\<Int64>

```cangjie
extend Int64 <: Countable<Int64>
```

功能：为 [Int64](core_package_intrinsics.md#int64) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[Int64](core_package_intrinsics.md#int64)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[Int64](#int64)>

#### func next(Int64)

```cangjie
public func next(right: Int64): Int64
```

功能：获取当前 [Int64](core_package_intrinsics.md#int64) 值往右数 `right` 后所到位置的 [Int64](core_package_intrinsics.md#int64) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 往右数 `right` 后所到位置的 [Int64](core_package_intrinsics.md#int64) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [Int64](core_package_intrinsics.md#int64) 值的位置信息，即返回该 [Int64](core_package_intrinsics.md#int64) 值本身。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [Int64](core_package_intrinsics.md#int64) 值的位置信息。

### extend Int64 <: Hashable

```cangjie
extend Int64 <: Hashable
```

功能：为 [Int64](core_package_intrinsics.md#int64) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Int64 <: ToString

```cangjie
extend Int64 <: ToString
```

功能：这里为 [Int64](core_package_intrinsics.md#int64) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Int64](core_package_intrinsics.md#int64) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Int8

功能：表示 8 位有符号整型，表示范围为 [-2^7, 2^7 - 1]。

### extend Int8 <: Comparable\<Int8>

```cangjie
extend Int8 <: Comparable<Int8>
```

功能：为 [Int8](core_package_intrinsics.md#int8) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int8](core_package_intrinsics.md#int8)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Int8](#int8)>

#### func compare(Int8)

```cangjie
public func compare(rhs: Int8): Ordering
```

功能：判断当前 [Int8](core_package_intrinsics.md#int8) 值与指定 [Int8](core_package_intrinsics.md#int8) 值的大小关系。

参数：

- rhs: [Int8](core_package_intrinsics.md#int8) - 待比较的另一个 [Int8](core_package_intrinsics.md#int8) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Int8 <: Countable\<Int8>

```cangjie
extend Int8 <: Countable<Int8>
```

功能：为 [Int8](core_package_intrinsics.md#int8) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[Int8](core_package_intrinsics.md#int8)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[Int8](#int8)>

#### func next(Int64)

```cangjie
public func next(right: Int64): Int8
```

功能：获取当前 [Int8](core_package_intrinsics.md#int8) 值往右数 `right` 后所到位置的 [Int8](core_package_intrinsics.md#int8) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [Int8](core_package_intrinsics.md#int8) - 往右数 `right` 后所到位置的 [Int8](core_package_intrinsics.md#int8) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [Int8](core_package_intrinsics.md#int8) 值的位置信息，即将该 [Int8](core_package_intrinsics.md#int8) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [Int8](core_package_intrinsics.md#int8) 值的位置信息。

### extend Int8 <: Hashable

```cangjie
extend Int8 <: Hashable
```

功能：为 [Int8](core_package_intrinsics.md#int8) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Int8 <: ToString

```cangjie
extend Int8 <: ToString
```

功能：这里为 [Int8](core_package_intrinsics.md#int8) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Int8](core_package_intrinsics.md#int8) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## IntNative

功能：表示平台相关的有符号整型，其长度与当前系统的位宽一致。

### extend IntNative <: Comparable\<IntNative>

```cangjie
extend IntNative <: Comparable<IntNative>
```

功能：为 [IntNative](core_package_intrinsics.md#intnative) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[IntNative](core_package_intrinsics.md#intnative)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[IntNative](#intnative)>

#### func compare(IntNative)

```cangjie
public func compare(rhs: IntNative): Ordering
```

功能：判断当前 [IntNative](core_package_intrinsics.md#intnative) 值与指定 [IntNative](core_package_intrinsics.md#intnative) 值的大小关系。

参数：

- rhs: [IntNative](core_package_intrinsics.md#intnative) - 待比较的另一个 [IntNative](core_package_intrinsics.md#intnative) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend IntNative <: Countable\<IntNative>

```cangjie
extend IntNative <: Countable<IntNative>
```

功能：为 [IntNative](core_package_intrinsics.md#intnative) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[IntNative](core_package_intrinsics.md#intnative)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[IntNative](#intnative)>

#### func next(Int64)

```cangjie
public func next(right: Int64): IntNative
```

功能：获取当前 [IntNative](core_package_intrinsics.md#intnative) 值往右数 `right` 后所到位置的 [IntNative](core_package_intrinsics.md#intnative) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [IntNative](core_package_intrinsics.md#intnative) - 往右数 `right` 后所到位置的 [IntNative](core_package_intrinsics.md#intnative) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [IntNative](core_package_intrinsics.md#intnative) 值的位置信息，即将该 [IntNative](core_package_intrinsics.md#intnative) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [IntNative](core_package_intrinsics.md#intnative) 值的位置信息。

### extend IntNative <: Hashable

```cangjie
extend IntNative <: Hashable
```

功能：为 [IntNative](core_package_intrinsics.md#intnative) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend IntNative <: ToString

```cangjie
extend IntNative <: ToString
```

功能：这里为 [IntNative](core_package_intrinsics.md#intnative) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [IntNative](core_package_intrinsics.md#intnative) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Rune

功能：表示 unicode 字符集中的字符。

表示范围为 `Unicode scalar value`，即从 `\u{0000}` 到 `\u{D7FF}`，以及从 `\u{E000}` 到 `\u{10FFF}` 的字符。

### extend Rune <: RuneExtension

```cangjie
extend Rune <: RuneExtension
```

功能：为 [Rune](core_package_intrinsics.md#rune) 类型实现一系列扩展方法，主要为在 Ascii 字符集范围内的一些字符判断、转换等操作。

父类型：

- [RuneExtension](core_package_interfaces.md#interface-runeextension)

#### static func fromUtf8(Array\<UInt8>, Int64)

```cangjie
public static func fromUtf8(arr: Array<UInt8>, index: Int64): (Rune, Int64)
```

功能：将字节数组中的指定元素，根据 UTF-8 编码规则转换成字符，并告知字符占用字节长度。

参数：

- arr: [Array](core_package_structs.md#struct-arrayt)\<[UInt8](core_package_intrinsics.md#uint8)> - 待转换字节所在的字节数组。
- index: [Int64](core_package_intrinsics.md#int64) - 待转换字节在数组中的下标。

返回值：

- ([Rune](core_package_intrinsics.md#rune), [Int64](core_package_intrinsics.md#int64)) - 转换得到的字符，以及该字符占用的字节长度。

#### static func getPreviousFromUtf8(Array\<UInt8>, Int64)

```cangjie
public static func getPreviousFromUtf8(arr: Array<UInt8>, index: Int64): (Rune, Int64)
```

功能：获取字节数组中指定索引对应的字节所在的 UTF-8 编码字符，同时返回该字符首位字节码在数组中的索引。

当指定了一个索引，那么函数会找到数组对应索引位置并且根据 UTF-8 规则，查看该字节码是否是字符的首位字节码，如果不是就继续向前遍历，直到该字节码是首位字节码，然后利用字节码序列找到对应的字符。

参数：

- arr: [Array](core_package_structs.md#struct-arrayt)\<[UInt8](core_package_intrinsics.md#uint8)> - 待从中获取字符的字节数组。
- index: [Int64](core_package_intrinsics.md#int64) - 待查找字符在数组中的索引。

返回值：

- ([Rune](core_package_intrinsics.md#rune), [Int64](core_package_intrinsics.md#int64)) - 找到的字符，以及该字符首位字节码在数组中的索引。

异常：

- [IllegalArgumentException](core_package_exceptions.md#class-illegalargumentexception) - 如果找不到对应首位字节码，即指定字节所在位置的字节不符合 UTF-8 编码，抛出异常。

#### static func intoUtf8Array(Rune, Array\<UInt8>, Int64)

```cangjie
public static func intoUtf8Array(c: Rune, arr: Array<UInt8>, index: Int64): Int64
```

功能：该函数会把字符转成字节码序列然后覆盖 [Array](core_package_structs.md#struct-arrayt) 数组内指定位置的字节码。

参数：

- c: [Rune](core_package_intrinsics.md#rune) - 待转换的字符。
- arr: [Array](core_package_structs.md#struct-arrayt)\<[UInt8](core_package_intrinsics.md#uint8)> - 待覆盖的 [Array](core_package_structs.md#struct-arrayt) 数组。
- index: [Int64](core_package_intrinsics.md#int64) - 目标位置的起始索引。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 字符的字节码长度，例如中文是三个字节码长度。

#### static func utf8Size(Array\<UInt8>, Int64)

```cangjie
public static func utf8Size(arr: Array<UInt8>, index: Int64): Int64
```

功能：该函数会返回字节数组指定索引位置为起始的字符占用的字节数。

在 UTF-8 编码中，ASCII 码首位字节第一位不为 1，其他长度的字符首位字节开头 1 的个数表明了该字符对应的字节码长度，该函数通过扫描首位，判断字节码长度。如果索引对应的不是首位字节码，就会抛出异常。

参数：

- arr: [Array](core_package_structs.md#struct-arrayt)\<[UInt8](core_package_intrinsics.md#uint8)> - 待获取字符的字节数组。
- index: [Int64](core_package_intrinsics.md#int64) - 指定字符的索引。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 字符的字节码长度，例如中文是三个字节码长度。

异常：

- [IllegalArgumentException](core_package_exceptions.md#class-illegalargumentexception) - 如果索引位置的字节码不符合首位字节码规则，会抛出异常。

#### static func utf8Size(Rune)

```cangjie
public static func utf8Size(c: Rune): Int64
```

功能：返回字符对应的 UTF-8 编码的字节码长度，例如中文字符的字节码长度是 3。

参数：

- c: [Rune](core_package_intrinsics.md#rune) - 待计算 UTF-8 字节码长度的字符。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 字符的 UTF-8 字节码长度。

#### func isAscii()

```cangjie
public func isAscii(): Bool
```

功能：判断字符是否是 Ascii 中的字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 字符返回 true，否则返回 false。

#### func isAsciiControl()

```cangjie
public func isAsciiControl(): Bool
```

功能：判断字符是否是 Ascii 控制字符。其取值范围为 [00, 1F] 和 {7F} 的并集。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 控制字符返回 true，否则返回 false。

#### func isAsciiGraphic()

```cangjie
public func isAsciiGraphic(): Bool
```

功能：判断字符是否是 Ascii 图形字符。其取值范围为 [21, 7E]。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 图形字符返回 true，否则返回 false。

#### func isAsciiHex()

```cangjie
public func isAsciiHex(): Bool
```

功能：判断字符是否是 Ascii 十六进制字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 十六进制字符返回 true，否则返回 false。

#### func isAsciiLetter()

```cangjie
public func isAsciiLetter(): Bool
```

功能：判断字符是否是 Ascii 字母字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 字母字符返回 true，否则返回 false。

#### func isAsciiLowerCase()

```cangjie
public func isAsciiLowerCase(): Bool
```

功能：判断字符是否是 Ascii 小写字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 小写字符返回 true，否则返回 false。

#### func isAsciiNumber()

```cangjie
public func isAsciiNumber(): Bool
```

功能：判断字符是否是 Ascii 数字字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 数字字符返回 true，否则返回 false。

#### func isAsciiNumberOrLetter()

```cangjie
public func isAsciiNumberOrLetter(): Bool
```

功能：判断字符是否是 Ascii 数字或拉丁字母字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 数字或拉丁字母字符返回 true，否则返回 false。

#### func isAsciiOct()

```cangjie
public func isAsciiOct(): Bool
```

功能：判断字符是否是 Ascii 八进制字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 八进制字符返回 true，否则返回 false。

#### func isAsciiPunctuation()

```cangjie
public func isAsciiPunctuation(): Bool
```

功能：判断字符是否是 Ascii 标点符号字符。其取值范围为 [21, 2F]、[3A, 40]、[5B, 60] 和 [7B, 7E] 的并集。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 标点符号字符返回 true，否则返回 false。

#### func isAsciiUpperCase()

```cangjie
public func isAsciiUpperCase(): Bool
```

功能：判断字符是否是 Ascii 大写字符。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 大写字符返回 true，否则返回 false。

#### func isAsciiWhiteSpace()

```cangjie
public func isAsciiWhiteSpace(): Bool
```

功能：判断字符是否是 Ascii 空白字符。其取值范围为 [09, 0D] 和 {20} 的并集。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果是 Ascii 空白字符返回 true，否则返回 false。

#### func toAsciiLowerCase()

```cangjie
public func toAsciiLowerCase(): Rune
```

功能：将字符转换为 Ascii 小写字符，如果无法转换则保持现状。

返回值：

- [Rune](core_package_intrinsics.md#rune) - 转换后的字符，如果无法转换则返回原来的 [Rune](core_package_intrinsics.md#rune)。

#### func toAsciiUpperCase()

```cangjie
public func toAsciiUpperCase(): Rune
```

功能：将字符转换为 Ascii 大写字符，如果无法转换则保持现状。

返回值：

- [Rune](core_package_intrinsics.md#rune) - 转换后的字符，如果无法转换则返回原来的 [Rune](core_package_intrinsics.md#rune)。

### extend Rune <: Comparable\<Rune>

```cangjie
extend Rune <: Comparable<Rune>
```

功能：为 [Rune](core_package_intrinsics.md#rune) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[Rune](core_package_intrinsics.md#rune)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[Rune](#rune)>

#### func compare(Rune)

```cangjie
public func compare(rhs: Rune): Ordering
```

功能：判断当前 [Rune](core_package_intrinsics.md#rune) 实例与指定 [Rune](core_package_intrinsics.md#rune) 实例的大小关系。

[Rune](core_package_intrinsics.md#rune) 的大小关系指的是它们对应的 unicode 码点的大小关系。

参数：

- rhs: [Rune](core_package_intrinsics.md#rune) - 待比较的另一个 [Rune](core_package_intrinsics.md#rune) 实例。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend Rune <: Countable\<Rune>

```cangjie
extend Rune <: Countable<Rune>
```

功能：为 [Rune](core_package_intrinsics.md#rune) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[Rune](core_package_intrinsics.md#rune)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[Rune](#rune)>

#### func next(Int64)

```cangjie
public func next(right: Int64): Rune
```

功能：获取当前 [Rune](core_package_intrinsics.md#rune) 值往右数 `right` 后所到位置的 [Rune](core_package_intrinsics.md#rune) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [Rune](core_package_intrinsics.md#rune) - 往右数 `right` 后所到位置的 [Rune](core_package_intrinsics.md#rune) 值。

异常：

- [OverflowException](core_package_exceptions.md#class-overflowexception) - 如果与 [Int64](core_package_intrinsics.md#int64) 数进行加法运算后为不合法的 Unicode 值，抛出异常。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [Rune](core_package_intrinsics.md#rune) 值的位置信息，即将该 [Rune](core_package_intrinsics.md#rune) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [Rune](core_package_intrinsics.md#rune) 值的位置信息。

### extend Rune <: Hashable

```cangjie
extend Rune <: Hashable
```

功能：为 [Rune](core_package_intrinsics.md#rune) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Rune <: ToString

```cangjie
extend Rune <: ToString
```

功能：这里为 [Rune](core_package_intrinsics.md#rune) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Rune](core_package_intrinsics.md#rune) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## UInt16

功能：表示 16 位无符号整型，表示范围为 [0, 2^{16} - 1]。

### extend UInt16 <: Comparable\<UInt16>

```cangjie
extend UInt16 <: Comparable<UInt16>
```

功能：为 [UInt16](core_package_intrinsics.md#uint16) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt16](core_package_intrinsics.md#uint16)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt16](#uint16)>

#### func compare(UInt16)

```cangjie
public func compare(rhs: UInt16): Ordering
```

功能：判断当前 [UInt16](core_package_intrinsics.md#uint16) 值与指定 [UInt16](core_package_intrinsics.md#uint16) 值的大小关系。

参数：

- rhs: [UInt16](core_package_intrinsics.md#uint16) - 待比较的另一个 [UInt16](core_package_intrinsics.md#uint16) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend UInt16 <: Countable\<UInt16>

```cangjie
extend UInt16 <: Countable<UInt16>
```

功能：为 [UInt16](core_package_intrinsics.md#uint16) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[UInt16](core_package_intrinsics.md#uint16)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[UInt16](#uint16)>

#### func next(Int64)

```cangjie
public func next(right: Int64): UInt16
```

功能：获取当前 [UInt16](core_package_intrinsics.md#uint16) 值往右数 `right` 后所到位置的 [UInt16](core_package_intrinsics.md#uint16) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [UInt16](core_package_intrinsics.md#uint16) - 往右数 `right` 后所到位置的 [UInt16](core_package_intrinsics.md#uint16) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [UInt16](core_package_intrinsics.md#uint16) 值的位置信息，即将该 [UInt16](core_package_intrinsics.md#uint16) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [UInt16](core_package_intrinsics.md#uint16) 值的位置信息。

### extend UInt16 <: Hashable

```cangjie
extend UInt16 <: Hashable
```

功能：为 [UInt16](core_package_intrinsics.md#uint16) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend UInt16 <: ToString

```cangjie
extend UInt16 <: ToString
```

功能：这里为 [UInt16](core_package_intrinsics.md#uint16) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [UInt16](core_package_intrinsics.md#uint16) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## UInt32

功能：表示 32 位无符号整型，表示范围为 [0, 2^{32} - 1]。

### extend UInt32 <: Comparable\<UInt32>

```cangjie
extend UInt32 <: Comparable<UInt32>
```

功能：为 [UInt32](core_package_intrinsics.md#uint32) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt32](core_package_intrinsics.md#uint32)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt32](#uint32)>

#### func compare(UInt32)

```cangjie
public func compare(rhs: UInt32): Ordering
```

功能：判断当前 [UInt32](core_package_intrinsics.md#uint32) 值与指定 [UInt32](core_package_intrinsics.md#uint32) 值的大小关系。

参数：

- rhs: [UInt32](core_package_intrinsics.md#uint32) - 待比较的另一个 [UInt32](core_package_intrinsics.md#uint32) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend UInt32 <: Countable\<UInt32>

```cangjie
extend UInt32 <: Countable<UInt32>
```

功能：为 [UInt32](core_package_intrinsics.md#uint32) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[UInt32](core_package_intrinsics.md#uint32)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[UInt32](#uint32)>

#### func next(Int64)

```cangjie
public func next(right: Int64): UInt32
```

功能：获取当前 [UInt32](core_package_intrinsics.md#uint32) 值往右数 `right` 后所到位置的 [UInt32](core_package_intrinsics.md#uint32) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [UInt32](core_package_intrinsics.md#uint32) - 往右数 `right` 后所到位置的 [UInt32](core_package_intrinsics.md#uint32) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [UInt32](core_package_intrinsics.md#uint32) 值的位置信息，即将该 [UInt32](core_package_intrinsics.md#uint32) 转换为 [UInt64](core_package_intrinsics.md#uint64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [UInt32](core_package_intrinsics.md#uint32) 值的位置信息。

### extend UInt32 <: Hashable

```cangjie
extend UInt32 <: Hashable
```

功能：为 [UInt32](core_package_intrinsics.md#uint32) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend UInt32 <: ToString

```cangjie
extend UInt32 <: ToString
```

功能：这里为 [UInt32](core_package_intrinsics.md#uint32) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [UInt32](core_package_intrinsics.md#uint32) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## UInt64

功能：表示 64 位无符号整型，表示范围为 [0, 2^{64} - 1]。

### extend UInt64 <: Comparable\<UInt64>

```cangjie
extend UInt64 <: Comparable<UInt64>
```

功能：为 [UInt64](core_package_intrinsics.md#uint64) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt64](core_package_intrinsics.md#uint64)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt64](#uint64)>

#### func compare(UInt64)

```cangjie
public func compare(rhs: UInt64): Ordering
```

功能：判断当前 [UInt64](core_package_intrinsics.md#uint64) 值与指定 [UInt64](core_package_intrinsics.md#uint64) 值的大小关系。

参数：

- rhs: [UInt64](core_package_intrinsics.md#uint64) - 待比较的另一个 [UInt64](core_package_intrinsics.md#uint64) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend UInt64 <: Countable\<UInt64>

```cangjie
extend UInt64 <: Countable<UInt64>
```

功能：为 [UInt64](core_package_intrinsics.md#uint64) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[UInt64](core_package_intrinsics.md#uint64)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[UInt64](#uint64)>

#### func next(Int64)

```cangjie
public func next(right: Int64): UInt64
```

功能：获取当前 [UInt64](core_package_intrinsics.md#uint64) 值往右数 `right` 后所到位置的 [UInt64](core_package_intrinsics.md#uint64) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [UInt64](core_package_intrinsics.md#uint64) - 往右数 `right` 后所到位置的 [UInt64](core_package_intrinsics.md#uint64) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [UInt64](core_package_intrinsics.md#uint64) 值的位置信息，即将该 [UInt64](core_package_intrinsics.md#uint64) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [UInt64](core_package_intrinsics.md#uint64) 值的位置信息。

### extend UInt64 <: Hashable

```cangjie
extend UInt64 <: Hashable
```

功能：为 [UInt64](core_package_intrinsics.md#uint64) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend UInt64 <: ToString

```cangjie
extend UInt64 <: ToString
```

功能：这里为 [UInt64](core_package_intrinsics.md#uint64) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [UInt64](core_package_intrinsics.md#uint64) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## UInt8

功能：表示 8 位无符号整型，表示范围为 [0, 2^8 - 1]。

### extend UInt8 <: Comparable\<UInt8>

```cangjie
extend UInt8 <: Comparable<UInt8>
```

功能：为 [UInt8](core_package_intrinsics.md#uint8) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt8](core_package_intrinsics.md#uint8)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[UInt8](#uint8)>

#### func compare(UInt8)

```cangjie
public func compare(rhs: UInt8): Ordering
```

功能：判断当前 [UInt8](core_package_intrinsics.md#uint8) 值与指定 [UInt8](core_package_intrinsics.md#uint8) 值的大小关系。

参数：

- rhs: [UInt8](core_package_intrinsics.md#uint8) - 待比较的另一个 [UInt8](core_package_intrinsics.md#uint8) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend UInt8 <: Countable\<UInt8>

```cangjie
extend UInt8 <: Countable<UInt8>
```

功能：为 [UInt8](core_package_intrinsics.md#uint8) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[UInt8](core_package_intrinsics.md#uint8)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[UInt8](#uint8)>

#### func next(Int64)

```cangjie
public func next(right: Int64): UInt8
```

功能：获取当前 [UInt8](core_package_intrinsics.md#uint8) 值往右数 `right` 后所到位置的 [UInt8](core_package_intrinsics.md#uint8) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [UInt8](core_package_intrinsics.md#uint8) - 往右数 `right` 后所到位置的 [UInt8](core_package_intrinsics.md#uint8) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [UInt8](core_package_intrinsics.md#uint8) 值的位置信息，即将该 [UInt8](core_package_intrinsics.md#uint8) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [UInt8](core_package_intrinsics.md#uint8) 值的位置信息。

### extend UInt8 <: Hashable

```cangjie
extend UInt8 <: Hashable
```

功能：为 [UInt8](core_package_intrinsics.md#uint8) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend UInt8 <: ToString

```cangjie
extend UInt8 <: ToString
```

功能：这里为 [UInt8](core_package_intrinsics.md#uint8) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [UInt8](core_package_intrinsics.md#uint8) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## UIntNative

功能：表示平台相关的无符号整型，其长度与当前系统的位宽一致。

### extend UIntNative <: Comparable\<UIntNative>

```cangjie
extend UIntNative <: Comparable<UIntNative>
```

功能：为 [UIntNative](core_package_intrinsics.md#uintnative) 类型扩展 [Comparable](core_package_interfaces.md#interface-comparablet)\<[UIntNative](core_package_intrinsics.md#uintnative)> 接口，支持比较操作。

父类型：

- [Comparable](core_package_interfaces.md#interface-comparablet)\<[UIntNative](#uintnative)>

#### func compare(UIntNative)

```cangjie
public func compare(rhs: UIntNative): Ordering
```

功能：判断当前 [UIntNative](core_package_intrinsics.md#uintnative) 值与指定 [UIntNative](core_package_intrinsics.md#uintnative) 值的大小关系。

参数：

- rhs: [UIntNative](core_package_intrinsics.md#uintnative) - 待比较的另一个 [UIntNative](core_package_intrinsics.md#uintnative) 值。

返回值：

- [Ordering](core_package_enums.md#enum-ordering) - 如果大于，返回 [Ordering](core_package_enums.md#enum-ordering).GT，如果等于，返回 [Ordering](core_package_enums.md#enum-ordering).EQ，如果小于，返回 [Ordering](core_package_enums.md#enum-ordering).LT。

### extend UIntNative <: Countable

```cangjie
extend UIntNative <: Countable<UIntNative>
```

功能：为 [UIntNative](core_package_intrinsics.md#uintnative) 类型扩展 [Countable](core_package_interfaces.md#interface-countablet)\<[UIntNative](core_package_intrinsics.md#uintnative)> 接口，支持计数操作。

父类型：

- [Countable](core_package_interfaces.md#interface-countablet)\<[UIntNative](#uintnative)>

#### func next(Int64)

```cangjie
public func next(right: Int64): UIntNative
```

功能：获取当前 [UIntNative](core_package_intrinsics.md#uintnative) 值往右数 `right` 后所到位置的 [UIntNative](core_package_intrinsics.md#uintnative) 值。

参数：

- right: [Int64](core_package_intrinsics.md#int64) - 往右数的个数。

返回值：

- [UIntNative](core_package_intrinsics.md#uintnative) - 往右数 `right` 后所到位置的 [UIntNative](core_package_intrinsics.md#uintnative) 值。

#### func position()

```cangjie
public func position(): Int64
```

功能：获取当前 [UIntNative](core_package_intrinsics.md#uintnative) 值的位置信息，即将该 [UIntNative](core_package_intrinsics.md#uintnative) 转换为 [Int64](core_package_intrinsics.md#int64) 值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 当前 [UIntNative](core_package_intrinsics.md#uintnative) 值的位置信息。

### extend UIntNative <: Hashable

```cangjie
extend UIntNative <: Hashable
```

功能：为 [UIntNative](core_package_intrinsics.md#uintnative) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend UIntNative <: ToString

```cangjie
extend UIntNative <: ToString
```

功能：这里为 [UIntNative](core_package_intrinsics.md#uintnative) 类型扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [UIntNative](core_package_intrinsics.md#uintnative) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。

## Unit

功能：表示仓颉语言中只关心副作用而不关心值的表达式的类型。

例如，print 函数、赋值表达式、复合赋值表达式、自增和自减表达式、循环表达式，它们的类型都是 [Unit](core_package_intrinsics.md#unit)。

[Unit](core_package_intrinsics.md#unit) 类型只有一个值，也是它的字面量：()。除了赋值、判等和判不等外，[Unit](core_package_intrinsics.md#unit) 类型不支持其他操作。

### extend Unit <: Equatable\<Unit>

```cangjie
extend Unit <: Equatable<Unit>
```

功能：为 [Unit](core_package_intrinsics.md#unit) 类型扩展 [Equatable](core_package_interfaces.md#interface-equatablet)\<[Unit](core_package_intrinsics.md#unit)> 接口。

父类型：

- [Equatable](core_package_interfaces.md#interface-equatablet)\<[Unit](#unit)>

### extend Unit <: Hashable

```cangjie
extend Unit <: Hashable
```

功能：为 [Unit](core_package_intrinsics.md#unit) 类型扩展 [Hashable](core_package_interfaces.md#interface-hashable) 接口，支持计算哈希值。

父类型：

- [Hashable](core_package_interfaces.md#interface-hashable)

#### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取哈希值，[Unit](core_package_intrinsics.md#unit) 的哈希值为 0。

返回值：

- [Int64](core_package_intrinsics.md#int64) - 哈希值。

### extend Unit <: ToString

```cangjie
extend Unit <: ToString
```

功能：为 [Unit](core_package_intrinsics.md#unit) 类型其扩展 [ToString](core_package_interfaces.md#interface-tostring) 接口，实现向 [String](core_package_structs.md#struct-string) 类型的转换。

[Unit](core_package_intrinsics.md#unit) 的字符串表示是 "()"。

父类型：

- [ToString](core_package_interfaces.md#interface-tostring)

#### func toString()

```cangjie
public func toString(): String
```

功能：将 [Unit](core_package_intrinsics.md#unit) 值转换为可输出的字符串。

返回值：

- [String](core_package_structs.md#struct-string) - 转化后的字符串。
