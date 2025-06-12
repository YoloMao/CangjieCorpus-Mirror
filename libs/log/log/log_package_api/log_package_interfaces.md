# 接口

## interface LogValue

```cangjie
public interface LogValue {
    func writeTo(w: LogWriter): Unit
}
```

功能：为类型提供序列化到日志输出目标的接口。

与 [LogWriter](log_package_classes.md#class-logwriter) 搭配使用， [LogWriter](log_package_classes.md#class-logwriter) 可以通过 writeValue 来将实现了 [LogValue](log_package_interfaces.md#interface-logvalue) 接口的类型写入到日志输出目标中。

### func writeTo(LogWriter)

```cangjie
func writeTo(w: LogWriter): Unit
```

功能：将实现了 [LogValue](log_package_interfaces.md#interface-logvalue) 接口的类型写入参数 `w` 指定的 [LogWriter](log_package_classes.md#class-logwriter) 实例中。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend Bool <: LogValue

```cangjie
extend Bool <: LogValue
```

功能：为 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend Exception <: LogValue

```cangjie
extend Exception <: LogValue
```

功能：为 [Exception](../../../std/core/core_package_api/core_package_exceptions.md#class-exception) 类型实现 [LogValue](./log_package_interfaces.md#interface-logvalue) 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [Exception](../../../std/core/core_package_api/core_package_exceptions.md#class-exception) 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend Int64 <: LogValue

```cangjie
extend Int64 <: LogValue
```

功能：为 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend Float64 <: LogValue

```cangjie
extend Float64 <: LogValue
```

功能：为 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend String <: LogValue

```cangjie
extend String <: LogValue
```

功能：为 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend DateTime <: LogValue

```cangjie
extend DateTime <: LogValue
```

功能：为 [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [DateTime](../../../std/time/time_package_api/time_package_structs.md#struct-datetime) 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend Duration <: LogValue

```cangjie
extend Duration <: LogValue
```

功能：为 [Duration](../../../std/time/time_package_api/time_package_structs.md#struct-duration) 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [Duration](../../../std/time/time_package_api/time_package_structs.md#struct-duration) 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend Array <: LogValue

```cangjie
extend<T> Array<T> <: LogValue where T <: LogValue
```

功能：为 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T> 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T> 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend HashMap <: LogValue

```cangjie
extend<K, V> HashMap<K, V> <: LogValue where K <: String, V <: LogValue
```

功能：为 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V> 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V> 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend TreeMap <: LogValue

```cangjie
extend<K, V> TreeMap<K, V> <: LogValue where K <: String, V <: LogValue
```

功能：为 [TreeMap](../../../std/collection/collection_package_api/collection_package_class.md#class-treemapk-v-where-k--comparablek)\<K, V> 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [TreeMap](../../../std/collection/collection_package_api/collection_package_class.md#class-treemapk-v-where-k--comparablek)\<K, V> 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。

### extend Option <: LogValue

```cangjie
extend<T> Option<T> <: LogValue where T <: LogValue
```

功能：为 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T> 类型实现 LogValue 接口。

父类型：

- [LogValue](#interface-logvalue)

#### func writeTo(LogWriter)

```cangjie
public func writeTo(w: LogWriter): Unit
```

功能：提供 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T> 类型序列化到流的功能。

参数：

- w:  [LogWriter](log_package_classes.md#class-logwriter) - 写入序列化结果的 [LogWriter](log_package_classes.md#class-logwriter) 实例。
