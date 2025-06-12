# 接口

## interface Formatter

```cangjie
public interface Formatter {
    func format(fmt: String): String
}
```

功能：该接口定义了格式化函数，即根据格式化参数将指定类型实例转换为对应格式的字符串。

格式化参数相关的说明详见 format 包中[功能介绍](./../format_package_overview.md#功能介绍)一节。

其他类型可通过实现该接口提供格式化功能。

### func format(String)

```cangjie
func format(fmt: String): String
```

功能：根据格式化参数将当前实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前实例格式化后得到的字符串。

### extend Float16 <: Formatter

```cangjie
extend Float16 <: Formatter
```

功能：为 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend Float32 <: Formatter

```cangjie
extend Float32 <: Formatter
```

功能：为 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend Float64 <: Formatter

```cangjie
extend Float64 <: Formatter
```

功能：为 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend Int16 <: Formatter

```cangjie
extend Int16 <: Formatter
```

功能：为 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend Int32 <: Formatter

```cangjie
extend Int32 <: Formatter
```

功能：为 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend Int64 <: Formatter

```cangjie
extend Int64 <: Formatter
```

功能：为 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend Int8 <: Formatter

```cangjie
extend Int8 <: Formatter
```

功能：为 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend Rune <: Formatter

```cangjie
extend Rune <: Formatter
```

功能：为 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend UInt16 <: Formatter

```cangjie
extend UInt16 <: Formatter
```

功能：为 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend UInt32 <: Formatter

```cangjie
extend UInt32 <: Formatter
```

功能：为 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend UInt64 <: Formatter

```cangjie
extend UInt64 <: Formatter
```

功能：为 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。

### extend UInt8 <: Formatter

```cangjie
extend UInt8 <: Formatter
```

功能：为 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 扩展 [Formatter](format_package_interfaces.md#interface-formatter) 接口，以实现将 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 实例转换为格式化字符串。

父类型：

- [Formatter](#interface-formatter)

#### func format(String)

```cangjie
public func format(fmt: String): String
```

功能：根据格式化参数将当前 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型实例格式化为对应格式的字符串。

参数：

- fmt: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 格式化参数。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 将当前 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型实例格式化后得到的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 fmt 不合法时抛出异常。
