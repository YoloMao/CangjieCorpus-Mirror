# 接口

## interface EquatableCollection\<T> where T <: Equatable\<T>

```cangjie
public interface EquatableCollection<T> <: Collection<T> where T <: Equatable<T> {
    func contains(element: T): Bool
    func containsAll(elements: Collection<T>): Bool
}
```

功能：定义了可以进行比较的集合类型。

父类型：

- [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<T>

### func contains(T)

```cangjie
func contains(element: T): Bool
```

功能：判断 Keys 是否包含指定元素。

参数：

- element: T - 指定元素，待判断 Keys 是否包含该元素。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 包含返回 true，否则返回 false。

### func containsAll(Collection\<T>)

```cangjie
func containsAll(elements: Collection<T>): Bool
```

功能：判断 Keys 是否包含指定集合的所有元素。

参数：

- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<T> - 待判断的集合 elements。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 包含则返回 true，否则返回 false。

## interface Map\<K, V> where K <: Equatable\<K>

功能：[Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 接口提供了一种将键映射到值的方式。它允许我们使用键来查找值，因此可以用于存储和操作键值对。

[map](collection_package_function.md#func-mapt-rt---r)不能包含重复的key，每个key最多只能映射到一个value。

```cangjie
public interface Map<K, V> <: Collection<(K, V)> where K <: Equatable<K> {
    func get(key: K): Option<V>
    func contains(key: K): Bool
    func containsAll(keys: Collection<K>): Bool
    mut func put(key: K, value: V): Option<V>
    mut func putAll(elements: Collection<(K, V)>): Unit
    mut func remove(key: K): Option<V>
    mut func removeAll(keys: Collection<K>): Unit
    mut func removeIf(predicate: (K, V) -> Bool): Unit
    mut func clear(): Unit
    func clone(): Map<K, V>
    operator func [](key: K): V
    operator func [](key: K, value!: V): Unit
    func keys(): EquatableCollection<K>
    func values(): Collection<V>
    prop size: Int64
    func isEmpty(): Bool
    func iterator(): Iterator<(K, V)>
}
```

父类型：

- [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<(K, V)>

### prop size

```cangjie
prop size: Int64
```

功能：返回 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中所有的键值对的个数。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### func clear()

```cangjie
mut func clear(): Unit
```

功能：清除所有键值对。

### func clone()

```cangjie
func clone(): Map<K, V>
```

功能：克隆 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek)。

返回值：

- [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) < K, V > - 返回一个 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek)\<K, V>。

### func contains(K)

```cangjie
func contains(key: K): Bool
```

功能：判断是否包含指定键的映射。

参数：

- key: K - 传递要判断的 key。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果存在，则返回 true；否则，返回 false。

### func containsAll(Collection\<K>)

```cangjie
func containsAll(keys: Collection<K>): Bool
```

功能：判断是否包含指定集合键的映射。

参数：

- keys: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<K> - 传递待判断的 key 的集合。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果存在，则返回 true；否则，返回 false。

### func get(K)

```cangjie
func get(key: K): Option<V>
```

功能：根据 key 得到 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中映射的值。

参数：

- key: K - 传递 key，获取 value。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中与 [Key](../../../crypto/x509/x509_package_api/x509_package_interfaces.md#interface-key) 对应的值。

### func isEmpty()

```cangjie
func isEmpty(): Bool
```

功能：检查 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 是否为空。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 为空，返回 `true`; 否则，返回 `false`。

### func iterator()

```cangjie
func iterator(): Iterator<(K, V)>
```

功能：返回 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 的迭代器。

返回值：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort) <(K, V) > - [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 的迭代器。

### func keys()

```cangjie
func keys(): EquatableCollection<K>
```

功能：返回 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中所有的 key，并将所有 key 存储在一个 [EquatableCollection](collection_package_interface.md#interface-equatablecollectiont-where-t--equatablet)\<K> 容器中。

返回值：

- [EquatableCollection](collection_package_interface.md#interface-equatablecollectiont-where-t--equatablet)\<K> - 保存所有返回的 key。

### func put(K, V)

```cangjie
mut func put(key: K, value: V): Option<V>
```

功能：将传入的键值对放入该 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中。对于 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中已有的键，该键映射的值将被新值替换。

参数：

- key: K - 要放置的键。
- value: V - 要分配的值。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果赋值之前 key 存在，旧的 value 用 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 封装；否则，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V>.None。

### func putAll(Collection\<(K, V)>)

```cangjie
mut func putAll(elements: Collection<(K, V)>): Unit
```

功能：将新的键值对放入 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中。对于 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中已有的键，该键映射的值将被新值替换。

参数：

- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<(K, V)> - 需要放入到 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中的键值对集合。

### func remove(K)

```cangjie
mut func remove(key: K): Option<V>
```

功能：从此 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中删除指定键的映射（如果存在）。

参数：

- key: K - 传入要删除的 key。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 从 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中移除的键对应的值。用 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 封装。

### func removeAll(Collection\<K>)

```cangjie
mut func removeAll(keys: Collection<K>): Unit
```

功能：从此映射中删除指定集合的映射（如果存在）。

参数：

- keys: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<K> - 传入要删除的集合。

### func removeIf((K, V) -> Bool)

```cangjie
mut func removeIf(predicate: (K, V) -> Bool): Unit
```

功能：传入 lambda 表达式，如果满足条件，则删除对应的键值对。

参数：

- predicate: (K, V) ->[Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 传递一个 lambda 表达式进行判断。

### func values()

```cangjie
func values(): Collection<V>
```

功能：返回 [Map](collection_package_interface.md#interface-mapk-v-where-k--equatablek) 中所有的 value，并将所有 value 存储在一个 [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<V> 容器中。

返回值：

- [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<V> - 保存所有返回的 value。

### operator func []\(K)

```cangjie
operator func [](key: K): V
```

功能：运算符重载集合，如果键存在，返回键对应的值，如果不存在，抛出异常。

参数：

- key: K - 需要进行查找的键。

返回值：

- V - 与键对应的值。

### operator func []\(K, V)

```cangjie
operator func [](key: K, value!: V): Unit
```

功能：运算符重载集合，如果键存在，新 value 覆盖旧 value，如果键不存在，添加此键值对。

参数：

- key: K - 需要进行设置的键。
- value!: V - 传递要设置的值。

## interface Set\<T> where T <: Equatable\<T>

```cangjie
public interface Set<T> <: Collection<T> where T <: Equatable<T> {
    func contains(element: T): Bool
    func subsetOf(other: Set<T>): Bool
    func containsAll(elements: Collection<T>): Bool
    mut func put(element: T): Bool
    mut func putAll(elements: Collection<T>): Unit
    mut func remove(element: T): Bool
    mut func removeAll(elements: Collection<T>): Unit
    mut func removeIf(predicate: (T) -> Bool): Unit
    mut func clear(): Unit
    mut func retainAll(elements: Set<T>): Unit
    func clone(): Set<T>
}
```

功能：不包含重复元素的集合。

[Set](collection_package_interface.md#interface-sett-where-t--equatablet) 接口不规定内部的实现方式，在 [Set](collection_package_interface.md#interface-sett-where-t--equatablet) 接口的实例中，其内部的元素通常是无序的，不能通过索引访问，也不能保证元素的插入顺序。

父类型：

- [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<T>

### func clear()

```cangjie
mut func clear(): Unit
```

功能：清除所有键值对。

### func clone()

```cangjie
func clone(): Set<T>
```

功能：克隆此 [Set](collection_package_interface.md#interface-sett-where-t--equatablet)，并返回克隆出的新的 [Set](collection_package_interface.md#interface-sett-where-t--equatablet)。

返回值：

- [Set](collection_package_interface.md#interface-sett-where-t--equatablet)\<T> - 新的 [Set](collection_package_interface.md#interface-sett-where-t--equatablet)\<T>。

### func contains(T)

```cangjie
func contains(element: T): Bool
```

功能：如果该集合包含指定元素，则返回 true。

参数：

- element: T - 需要判断的元素。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果包含，则返回 true；否则，返回 false。

### func containsAll(Collection\<T>)

```cangjie
func containsAll(elements: Collection<T>): Bool
```

功能：检查该集合是否包含其他集合。

参数：

- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<T> - 其他集合。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该集合包含指定集合，则返回 true；否则，返回 false。

### func put(T)

```cangjie
mut func put(element: T): Bool
```

功能：添加元素操作。如果元素已经存在，则不会添加它。

参数：

- element: T - 要添加的元素。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果添加成功，则返回 true；否则，返回 false。

### func putAll(Collection\<T>)

```cangjie
mut func putAll(elements: Collection<T>): Unit
```

功能：添加 [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont) 中的所有元素至此 [Set](collection_package_interface.md#interface-sett-where-t--equatablet) 中，如果元素存在，则不添加。

参数：

- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<T> - 需要被添加的元素的集合。

### func remove(T)

```cangjie
mut func remove(element: T): Bool
```

功能：从该集合中移除指定元素（如果存在）。

参数：

- element: T - 要删除的元素。

返回值：

- Bool - 集合中存在指定的元素并且删除成功返回 `true`，否则返回 `false` 。

### func removeAll(Collection\<T>)

```cangjie
mut func removeAll(elements: Collection<T>): Unit
```

功能：移除此 [Set](collection_package_interface.md#interface-sett-where-t--equatablet) 中那些也包含在指定 [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont) 中的所有元素。

参数：

- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<T> - 传入 [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<T>。

### func removeIf((T) -> Bool)

```cangjie
mut func removeIf(predicate: (T) -> Bool): Unit
```

功能：传入 lambda 表达式，如果满足 `true` 条件，则删除对应的元素。

参数：

- predicate: (T) ->[Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 传入一个 lambda 表达式进行判断。

### func retainAll(Set\<T>)

```cangjie
mut func retainAll(elements: Set<T>): Unit
```

功能：仅保留该 [Set](collection_package_interface.md#interface-sett-where-t--equatablet) 与入参 [Set](collection_package_interface.md#interface-sett-where-t--equatablet) 中重复的元素。

参数：

- elements: [Set](collection_package_interface.md#interface-sett-where-t--equatablet)\<T> - 要保存的元素集合。

### func subsetOf(Set\<T>)

```cangjie
func subsetOf(other: Set<T>): Bool
```

功能：检查该集合是否为其他集合的子集。

参数：

- other: [Set](collection_package_interface.md#interface-sett-where-t--equatablet)\<T> - 其他集合。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 果该集合是指定集合的子集，则返回 true；否则，返回 false。
