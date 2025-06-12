# 函数

## func CJ_CORE_AddAtexitCallback(() -> Unit)

```cangjie
public func CJ_CORE_AddAtexitCallback(callback: () -> Unit): Unit
```

功能：注册退出函数，当前进程退出时执行该函数。

> **说明：**
>
> 此处建议使用 os 库内 [Process](../../os_process/os_process_package_api/os_process_package_classes.md#class-process).atexit 函数，除非有制作进程管理框架的需要，否则不建议使用。

参数：

- callback: () ->[Unit](core_package_intrinsics.md#unit) - 注册的退出函数。

## func CJ_CORE_ExecAtexitCallbacks()

```cangjie
public func CJ_CORE_ExecAtexitCallbacks(): Unit
```

功能：执行注册的退出函数，执行到此函数直接结束当前进程。

> **说明：**
>
> 此处建议使用 os 库内 [Process](../../os_process/os_process_package_api/os_process_package_classes.md#class-process).exit 函数，除非有制作进程管理框架的需要，否则不建议使用。

## func acquireArrayRawData\<T>(Array\<T>) where T <: CType

```cangjie
public unsafe func acquireArrayRawData<T>(arr: Array<T>): CPointerHandle<T> where T <: CType
```

功能：获取 [Array](core_package_structs.md#struct-arrayt)\<T> 中数据的原始指针实例，T 需要满足 [CType](core_package_interfaces.md#interface-ctype) 约束。

> **注意：**
>
> 指针使用完后需要及时用 [releaseArrayRawData](core_package_funcs.md#func-releasearrayrawdatatcpointerhandlet-where-t--ctype) 函数释放该指针。
> 指针的获取和释放之间仅可包含简单的 foreign C 函数调用等逻辑，不构造例如 [CString](core_package_intrinsics.md#cstring) 等的仓颉对象，否则可能造成不可预期现象。

参数：

- arr: [Array](./core_package_structs.md#struct-arrayt)\<T> - 待获取原始指针的数组。

返回值：

- [CPointerHandle](core_package_structs.md#struct-cpointerhandlet-where-t--ctype)\<T> - 数组的原始指针实例。

## func alignOf\<T>() where T <: CType

```cangjie
public func alignOf<T>(): UIntNative where T <: CType
```

功能：获取类型 T 的内存对齐值。

返回值：

- [UIntNative](core_package_intrinsics.md#uintnative) - 对类型 T 做内存对齐的字节数。

## func eprint(String, Bool)

```cangjie
public func eprint(str: String, flush!: Bool = true): Unit
```

功能：用于打印错误消息。

如抛出异常时，消息将打印到标准错误文本流（stderr），而不是标准输出（stdout）。

参数：

- str: [String](core_package_structs.md#struct-string) - 待输出的字符串。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func eprintln(String)

```cangjie
public func eprintln(str: String): Unit
```

功能：用于打印错误消息，末尾添加换行。

如抛出异常时，消息将打印到标准错误文本流（stderr），而不是标准输出（stdout）。

参数：

- str: [String](core_package_structs.md#struct-string) - 待输出的字符串。

## func ifNone\<T>(Option\<T>, () -> Unit)

```cangjie
public func ifNone<T>(o: Option<T>, action: () -> Unit): Unit
```

功能：如果输入是 [Option](core_package_enums.md#enum-optiont).None 类型数据，则执行 action 函数。

参数：

- o: [Option](core_package_enums.md#enum-optiont)\<T> - 待判断是否为 [Option](core_package_enums.md#enum-optiont).None 的 [Option](core_package_enums.md#enum-optiont)\<T> 类型实例。
- action: () ->[Unit](core_package_intrinsics.md#unit) - 待执行函数。

## func ifSome\<T>(Option\<T>, (T) -> Unit)

```cangjie
public func ifSome<T>(o: Option<T>, action: (T) -> Unit): Unit
```

功能：如果输入是 [Option](core_package_enums.md#enum-optiont).Some 类型数据，则执行 action 函数。

参数：

- o: [Option](core_package_enums.md#enum-optiont)\<T> - 待判断是否为 [Option](core_package_enums.md#enum-optiont).Some 的 [Option](core_package_enums.md#enum-optiont)\<T> 类型实例，同时其封装的 `T` 类型实例将作为 action 函数的输入。
- action: (T) ->[Unit](core_package_intrinsics.md#unit) - 待执行函数。

## func print(Bool, Bool)

```cangjie
public func print(b: Bool, flush!: Bool = false): Unit
```

功能：向控制台输出 [Bool](core_package_intrinsics.md#bool) 类型数据的字符串表达。

> **注意：**
>
> 下列 [print](core_package_funcs.md#func-printbool-bool)、 [println](core_package_funcs.md#func-println)、 [eprint](core_package_funcs.md#func-eprintstring-bool)、 [eprintln](core_package_funcs.md#func-eprintlnstring) 函数默认为 UTF-8 编码。
> windows 环境需手动执行命令 chcp 65001（将 cmd 更改为 UTF-8 编码）。

参数：

- b: [Bool](core_package_intrinsics.md#bool) - 待输出的 [Bool](core_package_intrinsics.md#bool) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Float16, Bool)

```cangjie
public func print(f: Float16, flush!: Bool = false): Unit
```

功能：向控制台输出 [Float16](core_package_intrinsics.md#float16) 类型数据的字符串表达。

参数：

- f: [Float16](core_package_intrinsics.md#float16) - 待输出的 [Float16](core_package_intrinsics.md#float16) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Float32, Bool)

```cangjie
public func print(f: Float32, flush!: Bool = false): Unit
```

功能：向控制台输出 [Float32](core_package_intrinsics.md#float32) 类型数据的字符串表达。

参数：

- f: [Float32](core_package_intrinsics.md#float32) - 待输出的 [Float32](core_package_intrinsics.md#float32) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Float64, Bool)

```cangjie
public func print(f: Float64, flush!: Bool = false): Unit
```

功能：向控制台输出 [Float64](core_package_intrinsics.md#float64) 类型数据的字符串表达。

参数：

- f: [Float64](core_package_intrinsics.md#float64) - 待输出的 [Float64](core_package_intrinsics.md#float64) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Int16, Bool)

```cangjie
public func print(i: Int16, flush!: Bool = false): Unit
```

功能：向控制台输出 [Int16](core_package_intrinsics.md#int16) 类型数据的字符串表达。

参数：

- i: [Int16](core_package_intrinsics.md#int16) - 待输出的 [Int16](core_package_intrinsics.md#int16) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Int32, Bool)

```cangjie
public func print(i: Int32, flush!: Bool = false): Unit
```

功能：向控制台输出 [Int32](core_package_intrinsics.md#int32) 类型数据的字符串表达。

参数：

- i: [Int32](core_package_intrinsics.md#int32) - 待输出的 [Int32](core_package_intrinsics.md#int32) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Int64, Bool)

```cangjie
public func print(i: Int64, flush!: Bool = false): Unit
```

功能：向控制台输出 [Int64](core_package_intrinsics.md#int64) 类型数据的字符串表达。

参数：

- i: [Int64](core_package_intrinsics.md#int64) - 待输出的 [Int64](core_package_intrinsics.md#int64) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Int8, Bool)

```cangjie
public func print(i: Int8, flush!: Bool = false): Unit
```

功能：向控制台输出 [Int8](core_package_intrinsics.md#int8) 类型数据的字符串表达。

参数：

- i: [Int8](core_package_intrinsics.md#int8) - 待输出的 [Int8](core_package_intrinsics.md#int8) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(Rune, Bool)

```cangjie
public func print(c: Rune, flush!: Bool = false): Unit
```

功能：向控制台输出 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 类型数据的字符串表达。

参数：

- c: [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 待输出的 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(String, Bool)

```cangjie
public func print(str: String, flush!: Bool = false): Unit
```

功能：向控制台输出指定字符串。

参数：

- str: [String](core_package_structs.md#struct-string) - 待输出的字符串。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(UInt16, Bool)

```cangjie
public func print(i: UInt16, flush!: Bool = false): Unit
```

功能：向控制台输出 [UInt16](core_package_intrinsics.md#uint16) 类型数据的字符串表达。

参数：

- i: [UInt16](core_package_intrinsics.md#uint16) - 待输出的 [UInt16](core_package_intrinsics.md#uint16) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(UInt32, Bool)

```cangjie
public func print(i: UInt32, flush!: Bool = false): Unit
```

功能：向控制台输出 [UInt32](core_package_intrinsics.md#uint32) 类型数据的字符串表达。

参数：

- i: [UInt32](core_package_intrinsics.md#uint32) - 待输出的 [UInt32](core_package_intrinsics.md#uint32) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(UInt64, Bool)

```cangjie
public func print(i: UInt64, flush!: Bool = false): Unit
```

功能：向控制台输出 [UInt64](core_package_intrinsics.md#uint64) 类型数据的字符串表达。

参数：

- i: [UInt64](core_package_intrinsics.md#uint64) - 待输出的 [UInt64](core_package_intrinsics.md#uint64) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print(UInt8, Bool)

```cangjie
public func print(i: UInt8, flush!: Bool = false): Unit
```

功能：向控制台输出 [UInt8](core_package_intrinsics.md#uint8) 类型数据的字符串表达。

参数：

- i: [UInt8](core_package_intrinsics.md#uint8) - 待输出的 [UInt8](core_package_intrinsics.md#uint8) 类型数据。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func print\<T>(T, Bool) where T <: ToString

```cangjie
public func print<T>(arg: T, flush!: Bool = false): Unit where T <: ToString
```

功能：向控制台输出 `T` 类型实例的字符串表示。

参数：

- arg: T - 待输出的数据，支持实现了 [ToString](core_package_interfaces.md#interface-tostring) 接口的类型。
- flush!: [Bool](core_package_intrinsics.md#bool) - 是否清空缓存，true 清空，false 不清空，默认 false。

## func println()

```cangjie
public func println(): Unit
```

功能：向标准输出（stdout）输出换行符。

## func println(Bool)

```cangjie
public func println(b: Bool): Unit
```

功能：向控制台输出 [Bool](core_package_intrinsics.md#bool) 类型数据的字符串表达，末尾添加换行。

参数：

- b: [Bool](core_package_intrinsics.md#bool) - 待输出的 [Bool](core_package_intrinsics.md#bool) 类型数据。

## func println(Float16)

```cangjie
public func println(f: Float16): Unit
```

功能：向控制台输出 [Float16](core_package_intrinsics.md#float16) 类型数据的字符串表达，末尾添加换行。

参数：

- f: [Float16](core_package_intrinsics.md#float16) - 待输出的 [Float16](core_package_intrinsics.md#float16) 类型数据。

## func println(Float32)

```cangjie
public func println(f: Float32): Unit
```

功能：向控制台输出 [Float32](core_package_intrinsics.md#float32) 类型数据的字符串表达，末尾添加换行。

参数：

- f: [Float32](core_package_intrinsics.md#float32) - 待输出的 [Float32](core_package_intrinsics.md#float32) 类型数据。

## func println(Float64)

```cangjie
public func println(f: Float64): Unit
```

功能：向控制台输出 [Float64](core_package_intrinsics.md#float64) 类型数据的字符串表达，末尾添加换行。

参数：

- f: [Float64](core_package_intrinsics.md#float64) - 待输出的 [Float64](core_package_intrinsics.md#float64) 类型数据。

## func println(Int16)

```cangjie
public func println(i: Int16): Unit
```

功能：向控制台输出 [Int16](core_package_intrinsics.md#int16) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [Int16](core_package_intrinsics.md#int16) - 待输出的 [Int16](core_package_intrinsics.md#int16) 类型数据。

## func println(Int32)

```cangjie
public func println(i: Int32): Unit
```

功能：向控制台输出 [Int32](core_package_intrinsics.md#int32) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [Int32](core_package_intrinsics.md#int32) - 待输出的 [Int32](core_package_intrinsics.md#int32) 类型数据。

## func println(Int64)

```cangjie
public func println(i: Int64): Unit
```

功能：向控制台输出 [Int64](core_package_intrinsics.md#int64) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [Int64](core_package_intrinsics.md#int64) - 待输出的 [Int64](core_package_intrinsics.md#int64) 类型数据。

## func println(Int8)

```cangjie
public func println(i: Int8): Unit
```

功能：向控制台输出 [Int8](core_package_intrinsics.md#int8) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [Int8](core_package_intrinsics.md#int8) - 待输出的 [Int8](core_package_intrinsics.md#int8) 类型数据。

## func println(Rune)

```cangjie
public func println(c: Rune): Unit
```

功能：向控制台输出 [Rune](core_package_intrinsics.md#rune) 类型数据的字符串表达，末尾添加换行。

参数：

- c: [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 待输出的 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 类型数据。

## func println(String)

```cangjie
public func println(str: String): Unit
```

功能：向控制台输出指定字符串，末尾添加换行。

参数：

- str: [String](core_package_structs.md#struct-string) - 待输出的字符串。

## func println(UInt16)

```cangjie
public func println(i: UInt16): Unit
```

功能：向控制台输出 [UInt16](core_package_intrinsics.md#uint16) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [UInt16](core_package_intrinsics.md#uint16) - 待输出的 [UInt16](core_package_intrinsics.md#uint16) 类型数据。

## func println(UInt32)

```cangjie
public func println(i: UInt32): Unit
```

功能：向控制台输出 [UInt32](core_package_intrinsics.md#uint32) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [UInt32](core_package_intrinsics.md#uint32) - 待输出的 [UInt32](core_package_intrinsics.md#uint32) 类型数据。

## func println(UInt64)

```cangjie
public func println(i: UInt64): Unit
```

功能：向控制台输出 [UInt64](core_package_intrinsics.md#uint64) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [UInt64](core_package_intrinsics.md#uint64) - 待输出的 [UInt64](core_package_intrinsics.md#uint64) 类型数据。

## func println(UInt8)

```cangjie
public func println(i: UInt8): Unit
```

功能：向控制台输出 [UInt8](core_package_intrinsics.md#uint8) 类型数据的字符串表达，末尾添加换行。

参数：

- i: [UInt8](core_package_intrinsics.md#uint8) - 待输出的 [UInt8](core_package_intrinsics.md#uint8) 类型数据。

## func println\<T>(T) where T <: ToString

```cangjie
public func println<T>(arg: T): Unit where T <: ToString
```

功能：向控制台输出 `T` 类型实例的字符串表示，末尾添加换行。

参数：

- arg: T - 待输出的数据，支持实现了 [ToString](core_package_interfaces.md#interface-tostring) 接口的类型。

## func refEq(Object, Object)

```cangjie
public func refEq(a: Object, b: Object): Bool
```

功能：判断两个 [Object](core_package_classes.md#class-object) 实例的内存地址是否相同。

参数：

- a: [Object](core_package_classes.md#class-object) - 一个 [Object](core_package_classes.md#class-object) 实例。
- b: [Object](core_package_classes.md#class-object) - 另一个 [Object](core_package_classes.md#class-object) 实例。

返回值：

- [Bool](core_package_intrinsics.md#bool) - 如果两个 [Object](core_package_classes.md#class-object) 实例的内存地址相同，返回 true，否则返回 false。

## func releaseArrayRawData\<T>(CPointerHandle\<T>) where T <: CType

```cangjie
public unsafe func releaseArrayRawData<T>(handle: CPointerHandle<T>): Unit where T <: CType
```

功能：释放原始指针实例，该实例通过 [acquireArrayRawData](core_package_funcs.md#func-acquirearrayrawdatatarrayt-where-t--ctype) 获取。

参数：

- handle: [CPointerHandle](core_package_structs.md#struct-cpointerhandlet-where-t--ctype)\<T> - 待释放的指针实例。

## func sizeOf\<T>() where T <: CType

```cangjie
public func sizeOf<T>(): UIntNative where T <: CType
```

功能：获取类型 T 所占用的内存空间大小。

返回值：

- [UIntNative](core_package_intrinsics.md#uintnative) - 类型 T 所占用内存空间的字节数。

## func zeroValue\<T>()

```cangjie
public unsafe func zeroValue<T>(): T
```

功能：获取一个已全零初始化的 T 类型实例。

> **注意：**
>
> 这个实例一定要赋值为正常初始化的值再使用，否则将引发程序崩溃。

返回值：

- T - 一个已全零初始化的 T 类型实例。
