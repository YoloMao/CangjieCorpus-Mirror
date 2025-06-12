# 接口

## interface Serializable

```cangjie
public interface Serializable<T> {
    func serialize(): DataModel
    static func deserialize(dm: DataModel): T
}
```

功能：用于规范序列化。

### func deserialize(DataModel)

```cangjie
static func deserialize(dm: DataModel): T
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为对象。

> **说明：**
>
> 支持实现 [Serializable](serialization_package_interfaces.md#interface-serializable) 的类型包括:
>
> - 基本数据类型：整数类型、浮点类型、布尔类型、字符类型、字符串类型。
> - [Collection](../../../std/core/core_package_api/core_package_interfaces.md#interface-collectiont) 类型：[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)、[ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)、[HashSet](../../../std/collection/collection_package_api/collection_package_class.md#class-hashsett-where-t--hashable--equatablet)、[HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)、[Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)。
> - 用户自定义的实现了 [Serializable](serialization_package_interfaces.md#interface-serializable)\<T> 的类型。

返回值：

- T - 反序列化的对象。

### func serialize()

```cangjie
func serialize(): DataModel
```

功能：将自身序列化为 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

### extend\<T> Array\<T> <: Serializable\<Array\<T>> where T <: Serializable\<T>

```cangjie
extend<T> Array<T> <: Serializable<Array<T>> where T <: Serializable<T>
```

父类型：

- [Serializable](#interface-serializable)\<[Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T>>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Array<T>
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T>。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T> - 反序列化后的 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T>。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelSeq](serialization_package_classes.md#class-datamodelseq) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Array](../../../std/core/core_package_api/core_package_structs.md#struct-arrayt)\<T> 序列化为 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

### extend\<T> ArrayList\<T> <: Serializable\<ArrayLis\<T>> where T <: Serializable\<T>

```cangjie
extend<T> ArrayList<T> <: Serializable<ArrayList<T>> where T <: Serializable<T>
```

父类型：

- [Serializable](#interface-serializable)\<[ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T>>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): ArrayList<T>
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T>。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T> - 反序列化后的 [ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T>。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelSeq](serialization_package_classes.md#class-datamodelseq) 时，抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [ArrayList](../../../std/collection/collection_package_api/collection_package_class.md#class-arraylistt)\<T> 序列化为 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

### extend Bool <: Serializable

```cangjie
extend Bool <: Serializable<Bool>
```

父类型：

- [Serializable](#interface-serializable)\<[Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Bool
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) - 反序列化后的 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelBool](serialization_package_classes.md#class-datamodelbool) 时，抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Bool](../../../std/core/core_package_api/core_package_intrinsics.md#bool) 序列化为 [DataModelBool](serialization_package_classes.md#class-datamodelbool)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelBool](serialization_package_classes.md#class-datamodelbool)。

### extend Float16 <: Serializable

```cangjie
extend Float16 <: Serializable<Float16>
```

拓展 [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16) 以实现 [Serializable](serialization_package_interfaces.md#interface-serializable)。

父类型：

- [Serializable](#interface-serializable)\<[Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Float16
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16) - 反序列化后的 [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Float16](../../../std/core/core_package_api/core_package_intrinsics.md#float16) 序列化为 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat)。

### extend Float32 <: Serializable

```cangjie
extend Float32 <: Serializable<Float32>
```

父类型：

- [Serializable](#interface-serializable)\<[Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Float32
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) - 反序列化后的 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Float32](../../../std/core/core_package_api/core_package_intrinsics.md#float32) 序列化为 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat)。

### extend Float64 <: Serializable

```cangjie
extend Float64 <: Serializable<Float64>
```

父类型：

- [Serializable](#interface-serializable)\<[Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Float64
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) - 反序列化后的 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Float64](../../../std/core/core_package_api/core_package_intrinsics.md#float64) 序列化为 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelFloat](serialization_package_classes.md#class-datamodelfloat)。

### extend HashMap <: Serializable

```cangjie
extend<K, V> HashMap<K, V> <: Serializable<HashMap<K, V>> where K <: Serializable<K> & Hashable & Equatable<K>, V <: Serializable<V>
```

父类型：

- [Serializable](#interface-serializable)\<[HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V>>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): HashMap<K, V>
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V>。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) < K, V > - 反序列化后的 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V>。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 不是 [DataModelStruct](serialization_package_classes.md#class-datamodelstruct) 类型，或者 [DataModelStruct](serialization_package_classes.md#class-datamodelstruct) 类型的 `dm` 中的 [Field](serialization_package_classes.md#class-field) 不是 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型时，抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<K, V> 序列化为 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当前 [HashMap](../../../std/collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 实例中的 [Key](../../../crypto/x509/x509_package_api/x509_package_interfaces.md#interface-key) 不是 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 类型时，抛出异常。

### extend\<T> HashSet\<T> <: Serializable\<HashSet\<T>> where T <: Serializable\<T> & Hashable & Equatable\<T>

```cangjie
extend<T> HashSet<T> <: Serializable<HashSet<T>> where T <: Serializable<T> & Hashable & Equatable<T>
```

父类型：

- [Serializable](#interface-serializable)\<[HashSet](../../../std/collection/collection_package_api/collection_package_class.md#class-hashsett-where-t--hashable--equatablet)\<T>>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): HashSet<T>
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [HashSet](../../../std/collection/collection_package_api/collection_package_class.md#class-hashsett-where-t--hashable--equatablet)\<T>。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [HashSet](../../../std/collection/collection_package_api/collection_package_class.md#class-hashsett-where-t--hashable--equatablet)\<T> - 反序列化后的 [HashSet](../../../std/collection/collection_package_api/collection_package_class.md#class-hashsett-where-t--hashable--equatablet)\<T>。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelSeq](serialization_package_classes.md#class-datamodelseq) 时，抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [HashSet](../../../std/collection/collection_package_api/collection_package_class.md#class-hashsett-where-t--hashable--equatablet)\<T> 序列化为 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelSeq](serialization_package_classes.md#class-datamodelseq)。

### extend Int16 <: Serializable

```cangjie
extend Int16 <: Serializable<Int16>
```

父类型：

- [Serializable](#interface-serializable)\<[Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Int16
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) - 反序列化后的 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Int16](../../../std/core/core_package_api/core_package_intrinsics.md#int16) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

### extend Int32 <: Serializable

```cangjie
extend Int32 <: Serializable<Int32>
```

父类型：

- [Serializable](#interface-serializable)\<[Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Int32
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) - 反序列化后的 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，抛出异常

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Int32](../../../std/core/core_package_api/core_package_intrinsics.md#int32) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

### extend Int64 <: Serializable

```cangjie
extend Int64 <: Serializable<Int64>
```

父类型：

- [Serializable](#interface-serializable)\<[Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Int64
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) - 反序列化后的 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Int64](../../../std/core/core_package_api/core_package_intrinsics.md#int64) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

### extend Int8 <: Serializable

```cangjie
extend Int8 <: Serializable<Int8>
```

父类型：

- [Serializable](#interface-serializable)\<[Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Int8
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) - 反序列化后的 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Int8](../../../std/core/core_package_api/core_package_intrinsics.md#int8) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

### extend\<T> Option\<T> <: Serializable\<Option\<T>> where T <: Serializable\<T>

```cangjie
extend<T> Option<T> <: Serializable<Option<T>> where T <: Serializable<T>
```

父类型：

- [Serializable](#interface-serializable)\<[Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T>>

#### func deserialize()

```cangjie
static public func deserialize(dm: DataModel): Option<T>
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T>。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 反序列化后的 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T>。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Option](../../../std/core/core_package_api/core_package_enums.md#enum-optiont)\<T> 中的 `T` 序列化为 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

### extend Rune <: Serializable

```cangjie
extend Rune <: Serializable<Rune>
```

父类型：

- [Serializable](#interface-serializable)\<[Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): Rune
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) - 反序列化后的字符。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelString](serialization_package_classes.md#class-datamodelstring) 时，则抛出此异常。
- [Exception](../../../std/core/core_package_api/core_package_exceptions.md#class-exception) - 当 `dm` 的类型不是 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 时，则抛出此异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 序列化为 [DataModelString](serialization_package_classes.md#class-datamodelstring)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelString](serialization_package_classes.md#class-datamodelstring)。

### extend String <: Serializable

```cangjie
extend String <: Serializable<String>
```

父类型：

- [Serializable](#interface-serializable)\<[String](../../../std/core/core_package_api/core_package_structs.md#struct-string)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): String
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - 反序列化后的 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelString](serialization_package_classes.md#class-datamodelstring) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) 序列化为 [DataModelString](serialization_package_classes.md#class-datamodelstring)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelString](serialization_package_classes.md#class-datamodelstring)。

### extend UInt16 <: Serializable

```cangjie
extend UInt16 <: Serializable<UInt16>
```

父类型：

- [Serializable](#interface-serializable)\<[UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): UInt16
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) - 反序列化后的 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [UInt16](../../../std/core/core_package_api/core_package_intrinsics.md#uint16) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

### extend UInt32 <: Serializable

```cangjie
extend UInt32 <: Serializable<UInt32>
```

父类型：

- [Serializable](#interface-serializable)\<[UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): UInt32
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) - 反序列化后的 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [UInt32](../../../std/core/core_package_api/core_package_intrinsics.md#uint32) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

### extend UInt64 <: Serializable

```cangjie
extend UInt64 <: Serializable<UInt64>
```

父类型：

- [Serializable](#interface-serializable)\<[UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): UInt64
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) - 反序列化后的 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [UInt64](../../../std/core/core_package_api/core_package_intrinsics.md#uint64) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

### extend UInt8 <: Serializable

```cangjie
extend UInt8 <: Serializable<UInt8>
```

父类型：

- [Serializable](#interface-serializable)\<[UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)>

#### func deserialize(DataModel)

```cangjie
static public func deserialize(dm: DataModel): UInt8
```

功能：将 [DataModel](serialization_package_classes.md#class-datamodel) 反序列化为 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)。

参数：

- dm: [DataModel](serialization_package_classes.md#class-datamodel) - 需要被反序列化的 [DataModel](serialization_package_classes.md#class-datamodel)。

返回值：

- [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) - 反序列化后的 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8)。

异常：

- [DataModelException](serialization_package_exceptions.md#class-datamodelexception) - 当 `dm` 的类型不是 [DataModelInt](serialization_package_classes.md#class-datamodelint) 时，则抛出异常。

#### func serialize()

```cangjie
public func serialize(): DataModel
```

功能：将 [UInt8](../../../std/core/core_package_api/core_package_intrinsics.md#uint8) 序列化为 [DataModelInt](serialization_package_classes.md#class-datamodelint)。

返回值：

- [DataModel](serialization_package_classes.md#class-datamodel) - 序列化的 [DataModelInt](serialization_package_classes.md#class-datamodelint)。
