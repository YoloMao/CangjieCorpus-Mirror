# 结构体

## struct EntryView\<K, V>  where K <: Hashable & Equatable\<K>

```cangjie
public struct EntryView<K, V>  where K <: Hashable & Equatable<K>
```

功能：[HashMap](collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 中某一个 [Key](../../../crypto/x509/x509_package_api/x509_package_interfaces.md#interface-key) 的视图。

通过对视图的修改，可以实现快速的获取或者修改 [HashMap](collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 中与 [Key](../../../crypto/x509/x509_package_api/x509_package_interfaces.md#interface-key) 对应的 `Value` 的值，在使用视图的过程中，如果集合修改、增加、删除了某些元素，视图会无效并抛出 [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception)。

该结构体的实例只能通过对应 [HashMap](collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 的 `func entryView(K)` 方法获得。

### func getKey()

```cangjie
public func getKey(): K
```

功能：获取视图中的键，时间复杂度为 O(1)。

返回值：

- K - 视图的键。

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此视图在使用的过程中，对应的 [HashMap](collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 被其它操作修改时，抛此异常。

### func getValue()

```cangjie
public func getValue(): ?V
```

功能：获取视图中的值，时间复杂度为 O(1)。

如果视图为空，返回 None；否则，返回键对应的值。

返回值：

- ?V - 视图的值。

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此视图在使用的过程中，对应的 [HashMap](collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 被其它操作修改时，抛此异常。

### func isAbsent()

```cangjie
public func isAbsent(): Bool
```

功能：判断视图是否为空。

如果视图为空，说明对应的 [HashMap](collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 中不存在 [Key](../../../crypto/x509/x509_package_api/x509_package_interfaces.md#interface-key) 值和此视图的 [Key](../../../crypto/x509/x509_package_api/x509_package_interfaces.md#interface-key)值相同的 ([Key](../../../crypto/x509/x509_package_api/x509_package_interfaces.md#interface-key), Value) 组合。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果视图为空，则返回 true；否则，返回 false。

### func setValue(V)

```cangjie
public mut func setValue(v: V): V
```

功能：设置视图中的值，时间复杂度为 O(1)。

如果视图为空，则插入指定的键值对，并返回插入的值；否则，返回设置前的值。

参数：

- v: V - 指定的值。

返回值：

- V - 视图的值或者新插入的值。

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此视图在使用的过程中，对应的 [HashMap](collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 被其它操作修改时，抛此异常。

## struct TreeMapNode\<K, V> where K <: Comparable\<K>

```cangjie
public struct TreeMapNode<K, V> where K <: Comparable<K>
```

功能：[TreeMap](collection_package_class.md#class-treemapk-v-where-k--comparablek) 的节点结构。

> **注意：**
>
> 在使用 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 实例进行节点操作时，如果此时对对应的 [TreeMap](collection_package_class.md#class-treemapk-v-where-k--comparablek) 进行插入或删除操作，将会导致 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 失效，对失效的 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 进行操作将会抛出异常 [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception)。

### prop key

```cangjie
public prop key: K
```

功能：获取当前节点的键。

类型：K

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 失效时，抛出异常。

### prop value

```cangjie
public mut prop value: V
```

功能：获取或设置当前节点的值。

类型：V

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 失效时，抛出异常。

### func backward(K, Bool)

```cangjie
public func backward(bound: K, inclusive!:Bool = true): Iterator<(K, V)>
```

功能：从当前节点开始，到 bound 结束，生成一个正序的迭代器。

参数：

- bound: K - 传入的键。
- inclusive!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否包含传入的键本身，默认为 true ，即包含传入的键本身。

返回值：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort) <(K, V) > - 返回从当前节点开始，到 bound 结束的一个正序的迭代器。

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 失效时，抛出异常。

### func forward(K, Bool)

```cangjie
public func forward(bound: K, inclusive!:Bool = true): Iterator<(K, V)>
```

功能：从当前节点开始，到 bound 结束，生成一个逆序的迭代器。

参数：

- bound: K - 传入的键。
- inclusive!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否包含传入的键本身，默认为 true ，即包含传入的键本身。

返回值：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort) <(K, V) > - 返回从当前节点开始，到 bound 结束的一个逆序的迭代器。

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 失效时，抛出异常

### func next()

```cangjie
public func next(): Option<TreeMapNode<K, V>>
```

功能：访问后继节点。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) < [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) < K, V >> - 如果存在后继节点，用 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek)\<K, V>> 封装并返回；否则，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek)\<K, V>>.None。

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 失效时，抛出异常。

### func prev()

```cangjie
public func prev(): Option<TreeMapNode<K, V>>
```

功能：访问前继节点。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) < [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) < K, V >> - 如果存在前继节点，用 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek)\<K, V>> 封装并返回；否则，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek)\<K, V>>.None。

异常：

- [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception) - 当此 [TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 失效时，抛出异常。
