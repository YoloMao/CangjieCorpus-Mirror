# 接口

## interface JsonDeserializable\<T>

```cangjie
public interface JsonDeserializable<T> {
    static func fromJson(r: JsonReader): T
}
```

功能：此接口用于实现从 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个仓颉对象。

支持的对象类型包括：

- 基本数据类型：整数类型、浮点类型、布尔类型、字符串类型。

- [Collection](../../../std/core/core_package_api/core_package_interfaces.md#interface-collectiont) 类型：[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)、[ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)、[HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)、[Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)。

- [BigInt](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-bigint)、[Decimal](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-decimal) 类型。

- [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 类型。

### static func fromJson(JsonReader)

```cangjie
static func fromJson(r: JsonReader): T
```

功能：从参数 `r` 指定的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例中读取一个 `T` 类型对象。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- T - `T` 类型的实例。

异常：

- [IllegalStateException](../../../std/core/core_package_api/core_package_exceptions.md#class-illegalstateexception) - 如果输入流的 JSON 数据不符合格式，抛出异常。

### extend BigInt <: JsonDeserializable\<BigInt>

```cangjie
extend BigInt <: JsonDeserializable<BigInt>
```

功能：为 [BigInt](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-bigint) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[BigInt](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-bigint)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): BigInt
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [BigInt](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-bigint)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- BigInt - [BigInt](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-bigint) 类型的实例。

### extend Bool <: JsonDeserializable\<Bool>

```cangjie
extend Bool <: JsonDeserializable<Bool>
```

功能：为 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Bool
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Bool - [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型的实例。

### extend DateTime <: JsonDeserializable\<DateTime>

```cangjie
extend DateTime <: JsonDeserializable<DateTime>
```

功能：为 [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): DateTime
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 实例。

该函数将会把读取到的字符串按照 `RFC3339` 的规范解析，可包含小数秒格式，函数的行为参考[DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime)的[func parse(String)](../../../std/time/time_package_api/time_package_structs.md#static-func-parsestring)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- DateTime - [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 类型的实例。

异常：

- [TimeParseException](../../../std/time/time_package_api/time_package_exceptions.md#class-timeparseexception) - 无法正常解析时，抛出异常。

### extend Float16 <: JsonDeserializable\<Float16>

```cangjie
extend Float16 <: JsonDeserializable<Float16>
```

功能：为 [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Float16
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Float16 - [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend Float32 <: JsonDeserializable\<Float32>

```cangjie
extend Float32 <: JsonDeserializable<Float32>
```

功能：为 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Float32
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Float32 - [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend Float64 <: JsonDeserializable\<Float64>

```cangjie
extend Float64 <: JsonDeserializable<Float64>
```

功能：为 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Float64
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Float64 - [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend String <: JsonDeserializable\<String>

```cangjie
extend String <: JsonDeserializable<String>
```

功能：为 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): String
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)。

根据下一个 `JsonToken` 的不同，`String` 的反序列化结果将会不同：

- 当下一个 `JsonToken` 是 `JsonString` 时， 反序列化过程会按照标准[ECMA-404 The JSON Data Interchange Standard](https://www.ecma-international.org/publications-and-standards/standards/ecma-404/)对读到的 `String` 进行转义。
- 当下一个 `JsonToken` 是 `JsonNumber` `JsonBool` `JsonNull` 其中一个时，将会读取下一个 `value` 字段的原始字符串并返回。
- 当下一个 `JsonToken` 是其它类型时，调用此接口会抛异常。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- String - [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型的实例。

### extend Int16 <: JsonDeserializable\<Int16>

```cangjie
extend Int16 <: JsonDeserializable<Int16>
```

功能：为 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Int16
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Int16 - [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend Int32 <: JsonDeserializable\<Int32>

```cangjie
extend Int32 <: JsonDeserializable<Int32>
```

功能：为 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Int32
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Int32 - [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend Int64 <: JsonDeserializable\<Int64>

```cangjie
extend Int64 <: JsonDeserializable<Int64>
```

功能：为 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Int64
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Int64 - [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend Int8 <: JsonDeserializable\<Int8>

```cangjie
extend Int8 <: JsonDeserializable<Int8>
```

功能：为 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Int8
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Int8 - [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend IntNative <: JsonDeserializable\<IntNative>

```cangjie
extend IntNative <: JsonDeserializable<IntNative>
```

功能：为 [IntNative](../../../std/core/core_package_api/core_package_intrinsics.md#intnative) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[IntNative](../../../std/core/core_package_api/core_package_intrinsics.md#intnative)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): IntNative
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [IntNative](../../../std/core/core_package_api/core_package_intrinsics.md#intnative)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- IntNative - [IntNative](../../../std/core/core_package_api/core_package_intrinsics.md#intnative) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend UInt16 <: JsonDeserializable\<UInt16>

```cangjie
extend UInt16 <: JsonDeserializable<UInt16>
```

功能：为 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): UInt16
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- UInt16 - [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend UInt32 <: JsonDeserializable\<UInt32>

```cangjie
extend UInt32 <: JsonDeserializable<UInt32>
```

功能：为 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): UInt32
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- UInt32 - [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend UInt64 <: JsonDeserializable\<UInt64 >

```cangjie
extend UInt64 <: JsonDeserializable<UInt64>
```

功能：为 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): UInt64
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- UInt64 - [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend UInt8 <: JsonDeserializable\<UInt8>

```cangjie
extend UInt8 <: JsonDeserializable<UInt8>
```

功能：为 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): UInt8
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- UInt8 - [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend UIntNative <: JsonDeserializable\<UIntNative>

```cangjie
extend UIntNative <: JsonDeserializable<UIntNative>
```

功能：为 [UIntNative](../../../std/core/core_package_api/core_package_intrinsics.md#uintnative) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[UIntNative](../../../std/core/core_package_api/core_package_intrinsics.md#uintnative)>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): UIntNative
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [UIntNative](../../../std/core/core_package_api/core_package_intrinsics.md#uintnative)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- UIntNative - [UIntNative](../../../std/core/core_package_api/core_package_intrinsics.md#uintnative) 类型的实例。

异常：

- [OverflowException](../../../std/core/core_package_api/core_package_exceptions.md#class-overflowexception) - 读取的数据超过范围时，抛出异常。

### extend\<T> Array\<T> <: JsonDeserializable\<Array\<T>> where T <: JsonSerializable

```cangjie
extend<T> Array<T> <: JsonDeserializable<Array<T>> where T <: JsonDeserializable<T>
```

功能：为 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T> 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T>>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Array<T>
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Array\<T> - [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt) 类型的实例。

### extend\<T> ArrayList\<T> <: JsonDeserializable\<ArrayList\<T>> where T <: JsonSerializable

```cangjie
extend<T> ArrayList<T> <: JsonDeserializable<ArrayList<T>> where T <: JsonDeserializable<T>
```

功能：为 [ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T>>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): ArrayList<T>
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- ArrayList \<T> - [ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt) 类型的实例。

### extend\<T> Option \<T> <: JsonDeserializable\<Option\<T>> where T <: JsonSerializable

```cangjie
extend<T> Option<T> <: JsonDeserializable<Option<T>> where T <: JsonDeserializable<T>
```

功能：为 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T>>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): Option<T>
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个[Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- Option\<T> - [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont) 类型的实例。

### extend\<K, V> HashMap\<K, V> <: JsonDeserializable\<HashMap\<K, V>> where V <: JsonDeserializable\<V>, K <: String

```cangjie
extend<K, V> HashMap<K, V> <: JsonDeserializable<HashMap<K, V>> where V <: JsonDeserializable<V>, K <: String
```

功能：为 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 类型实现 JsonDeserializable 接口。

父类型：

- [JsonDeserializable](#interface-jsondeserializablet)\<[HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V>>

#### static func fromJson(JsonReader)

```cangjie
public static func fromJson(r: JsonReader): HashMap<K, V>
```

功能：从 [JsonReader](../json_stream_package_api/encoding_json_stream_package_classes.md#class-jsonreader) 中读取一个 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)。

参数：

- r: [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) - 读取反序列化结果的 [JsonReader](encoding_json_stream_package_classes.md#class-jsonreader) 实例。

返回值：

- HashMap\<K, V> - [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V> 类型的实例。

## interface JsonSerializable

```cangjie
public interface JsonSerializable {
    func toJson(w: JsonWriter): Unit
}
```

功能：为类型提供序列化到 JSON 数据流的接口。

与 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 搭配使用，[JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 可以将实现了 [JsonSerializable](encoding_json_stream_package_interfaces.md#interface-jsonserializable) 接口的类型写入到 Stream 中。

### func toJson(JsonWriter)

```cangjie
func toJson(w: JsonWriter): Unit
```

功能：将实现了 [JsonSerializable](encoding_json_stream_package_interfaces.md#interface-jsonserializable) 接口的类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend BigInt <: JsonSerializable

```cangjie
extend BigInt <: JsonSerializable
```

功能：为[BigInt](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-bigint)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[BigInt](../../../std/math_numeric/math_numeric_package_api/math_numeric_package_structs.md#struct-bigint)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Bool <: JsonSerializable

```cangjie
extend Bool <: JsonSerializable
```

功能：为[Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend DateTime <: JsonSerializable

```cangjie
extend DateTime <: JsonSerializable
```

功能：为 [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 类型实现 JsonSerializable 接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：提供 [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 类型序列化到流的功能。

该接口的功能与 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 的 [writeConfig](./encoding_json_stream_package_classes.md#var-writeconfig)中的属性 [dateTimeFormat](./encoding_json_stream_package_structs.md#prop-datetimeformat)有关联，将会把 [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 按照[dateTimeFormat](./encoding_json_stream_package_structs.md#prop-datetimeformat)中的格式输出到目标流中，可以通过修改[dateTimeFormat](./encoding_json_stream_package_structs.md#prop-datetimeformat)实现不同的格式控制。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Float16 <: JsonSerializable

```cangjie
extend Float16 <: JsonSerializable
```

功能：为[Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Float32 <: JsonSerializable

```cangjie
extend Float32 <: JsonSerializable
```

功能：为[Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Float64 <: JsonSerializable

```cangjie
extend Float64 <: JsonSerializable
```

功能：为[Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend String <: JsonSerializable

```cangjie
extend String <: JsonSerializable
```

功能：为[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。写入的String

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Int16 <: JsonSerializable

```cangjie
extend Int16 <: JsonSerializable
```

功能：为[Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Int32 <: JsonSerializable

```cangjie
extend Int32 <: JsonSerializable
```

功能：为[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Int64 <: JsonSerializable

```cangjie
extend Int64 <: JsonSerializable
```

功能：为[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend Int8 <: JsonSerializable

```cangjie
extend Int8 <: JsonSerializable
```

功能：为[Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend IntNative <: JsonSerializable

```cangjie
extend IntNative <: JsonSerializable
```

功能：为[IntNative](../../../std/core/core_package_api/core_package_intrinsics.md#intnative)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[IntNative](../../../std/core/core_package_api/core_package_intrinsics.md#intnative)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend UInt16 <: JsonSerializable

```cangjie
extend UInt16 <: JsonSerializable
```

功能：为[UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend UInt32 <: JsonSerializable

```cangjie
extend UInt32 <: JsonSerializable
```

功能：为[UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。


### extend UInt64 <: JsonSerializable

```cangjie
extend UInt64 <: JsonSerializable
```

功能：为[UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend UInt8 <: JsonSerializable

```cangjie
extend UInt8 <: JsonSerializable
```

功能：为[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend UIntNative <: JsonSerializable

```cangjie
extend UIntNative <: JsonSerializable
```

功能：为[UIntNative](../../../std/core/core_package_api/core_package_intrinsics.md#uintnative)类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[UIntNative](../../../std/core/core_package_api/core_package_intrinsics.md#uintnative)类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend\<T> Array\<T> <: JsonSerializable where T <: JsonSerializable

```cangjie
extend<T> Array<T> <: JsonSerializable where T <: JsonSerializable
```

功能：为[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T>类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T>类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend\<T> ArrayList\<T> <: JsonSerializable where T <: JsonSerializable

```cangjie
extend<T> ArrayList<T> <: JsonSerializable where T <: JsonSerializable
```

功能：为[ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T>类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T>类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend\<T> Option\<T> <: JsonSerializable where T <: JsonSerializable

```cangjie
extend<T> Option<T> <: JsonSerializable where T <: JsonSerializable
```

功能：为[Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T>类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T>类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。

### extend\<K, V> HashMap\<K, V> <: JsonSerializable where V <: JsonSerializable, K <: String

```cangjie
extend<K, V> HashMap<K, V> <: JsonSerializable where V <: JsonSerializable, K <: String
```

功能：为[HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V>类型提供序列化到 JSON 数据流的接口。

父类型：

- [JsonSerializable](#interface-jsonserializable)

#### func toJson(JsonWriter)

```cangjie
public func toJson(w: JsonWriter): Unit
```

功能：将[HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V>类型写入参数 `w` 指定的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例中。

参数：

- w: [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) - 写入序列化结果的 [JsonWriter](encoding_json_stream_package_classes.md#class-jsonwriter) 实例。
