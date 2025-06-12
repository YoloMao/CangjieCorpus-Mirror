# 类

## class ArrayBlockingQueue\<E>

```cangjie
public class ArrayBlockingQueue<E> {
    public init(capacity: Int64)
    public init(capacity: Int64, elements: Collection<E>)
}
```

功能：基于数组实现的 Blocking Queue 数据结构及相关操作函数。

[ArrayBlockingQueue](collection_concurrent_class.md#class-arrayblockingqueuee) 是带阻塞机制且需要用户指定容量上界的并发队列。

### prop size

```cangjie
public prop size: Int64
```

功能：返回此 [ArrayBlockingQueue](collection_concurrent_class.md#class-arrayblockingqueuee) 的元素个数。

> **注意：**
>
> 此方法不保证并发场景下的原子性，建议在环境中没有其它线程并发地修改 [ArrayBlockingQueue](collection_concurrent_class.md#class-arrayblockingqueuee) 时调用。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### capacity

```cangjie
public let capacity: Int64
```

功能：此 [ArrayBlockingQueue](collection_concurrent_class.md#class-arrayblockingqueuee) 的容量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### init(Int64)

```cangjie
public init(capacity: Int64)
```

功能：构造一个带有传入容量大小的 [ArrayBlockingQueue](collection_concurrent_class.md#class-arrayblockingqueuee)。

参数：

- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 初始化容量大小。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 capacity 小于等于 0 则抛出异常。

### init(Int64, Collection\<E>)

```cangjie
public init(capacity: Int64, elements: Collection<E>)
```

功能：构造一个带有传入容量大小，并带有传入迭代器的 [ArrayBlockingQueue](collection_concurrent_class.md#class-arrayblockingqueuee)。

参数：

- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 初始化容量大小。
- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<E> - 初始化迭代器元素。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 capacity 小于等于 0 或小于迭代器元素 elements 的 size 则抛出异常。

### func dequeue()

```cangjie
public func dequeue(): E
```

功能：阻塞的出队操作，获得队首元素并删除。

返回值：

- E - 返回队首元素。

### func dequeue(Duration)

```cangjie
public func dequeue(timeout: Duration): Option<E>
```

功能：阻塞的出队操作，获得队首元素并删除，如果队列为空，将等待指定的时间。如果 timeout 为负，则会立即执行出队操作并且返回操作结果。

参数：

- timeout: [Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 等待时间。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 返回队首元素。如果超出等待时间还未成功获取队首元素，则返回 None。

### func enqueue(E)

```cangjie
public func enqueue(element: E): Unit
```

功能：阻塞的入队操作，将元素添加到队列尾部。

参数：

- element: E - 要添加的元素。

### func enqueue(E, Duration)

```cangjie
public func enqueue(element: E, timeout: Duration): Bool
```

功能：阻塞的入队操作，将元素添加到队列尾部，如果队列满了，将等待指定的时间。如果 timeout 为负，则会立即执行入队操作并且返回操作结果。

参数：

- element: E - 要添加的元素。
- timeout: [Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 等待时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 成功添加元素返回 true，超出等待时间还未成功添加元素返回 false。

### func head()

```cangjie
public func head(): Option<E>
```

功能：获取队首元素。

> **注意：**
>
> 该函数是非阻塞的。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 返回队首元素，队列为空时返回 None。

### func tryDequeue()

```cangjie
public func tryDequeue(): Option<E>
```

功能：非阻塞的出队操作，获得队首元素并删除。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 返回队首元素，队列为空时返回 None。

### func tryEnqueue(E)

```cangjie
public func tryEnqueue(element: E): Bool
```

功能：非阻塞的入队操作，将元素添加到队列尾部。

参数：

- element: E - 要添加的元素。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 成功添加返回 true；如果队列满了，添加失败返回 false。

## class BlockingQueue\<E>

```cangjie
public class BlockingQueue<E> {
    public init()
    public init(capacity: Int64)
    public init(capacity: Int64, elements: Array<E>)
    public init(capacity: Int64, elements: Collection<E>)
}
```

功能：实现是带阻塞机制并支持用户指定容量上界的并发队列。

阻塞队列的特点是，当队列满时，尝试向队列中添加元素的线程会被阻塞，直到队列有空余位置；当队列空时，尝试从队列中获取元素的线程会被阻塞，直到队列有可取元素。

### let capacity

```cangjie
public let capacity: Int64
```

功能：返回此 [BlockingQueue](collection_concurrent_class.md#class-blockingqueuee) 的容量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop size

```cangjie
public prop size: Int64
```

功能：返回此 [BlockingQueue](collection_concurrent_class.md#class-blockingqueuee) 的元素个数。

> **注意：**
>
> 此方法不保证并发场景下的原子性，建议在环境中没有其它线程并发地修改 [BlockingQueue](collection_concurrent_class.md#class-blockingqueuee) 时调用。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### init()

```cangjie
public init()
```

功能：构造一个具有默认初始容量（[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).Max）的 [BlockingQueue](collection_concurrent_class.md#class-blockingqueuee)。

### init(Int64)

```cangjie
public init(capacity: Int64)
```

功能：构造一个带有传入容量大小的 [BlockingQueue](collection_concurrent_class.md#class-blockingqueuee)。

参数：

- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 初始化容量大小。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 capacity 小于等于 0 则抛出异常。

### init(Int64, Array\<E>)

```cangjie
public init(capacity: Int64, elements: Array<E>)
```

功能：构造一个带有传入容量大小，并带有传入数组元素的 [BlockingQueue](collection_concurrent_class.md#class-blockingqueuee)。

参数：

- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 初始化容量大小。
- elements: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<E> - 初始化数组元素。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 capacity 小于等于 0 或小于数组元素elements 的 size 则抛出异常。

### init(Int64, Collection\<E>)

```cangjie
public init(capacity: Int64, elements: Collection<E>)
```

功能：构造一个带有传入容量大小，并带有传入迭代器的 [BlockingQueue](collection_concurrent_class.md#class-blockingqueuee)。

参数：

- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 初始化容量大小。
- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<E> - 初始化迭代器元素。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 capacity 小于等于 0 或小于迭代器元素elements 的 size 则抛出异常。

### func dequeue()

```cangjie
public func dequeue(): E
```

功能：阻塞的出队操作，获得队首元素并删除。

返回值：

- E - 返回队首元素。

### func dequeue(Duration)

```cangjie
public func dequeue(timeout: Duration): Option<E>
```

功能：阻塞的出队操作，获得队首元素并删除。如果队列为空，将等待指定的时间。如果 timeout 为负，则会立即执行出队操作并且返回操作结果。

参数：

- timeout: [Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 等待时间。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 返回队首元素。如果超出等待时间还未成功获取队首元素，则返回 None。

### func enqueue(E)

```cangjie
public func enqueue(element: E): Unit
```

功能：阻塞的入队操作，将元素添加到队列尾部。

参数：

- element: E - 要添加的元素。

### func enqueue(E, Dureation)

```cangjie
public func enqueue(element: E, timeout: Duration): Bool
```

功能：阻塞的入队操作，将元素添加到队列尾部，如果队列满了，将等待指定的时间。如果 timeout 为负，则会立即执行入队操作并且返回操作结果。

参数：

- element: E - 要添加的元素。
- timeout: [Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 等待时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 成功添加元素返回 true。超出等待时间还未成功添加元素返回 false。

### func head()

```cangjie
public func head(): Option<E>
```

功能：获取队首元素。

> **注意：**
>
> 该函数是非阻塞的。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 返回队首元素，队列为空时返回 None。

### func tryDequeue()

```cangjie
public func tryDequeue(): Option<E>
```

功能：非阻塞的出队操作，获得队首元素并删除。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 返回队首元素，队列为空时返回 None。

### func tryEnqueue(E)

```cangjie
public func tryEnqueue(element: E): Bool
```

功能：非阻塞的入队操作，将元素添加到队列尾部。

参数：

- element: E - 要添加的元素。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 成功添加返回 true；如果队列满了，添加失败返回 false。

## class ConcurrentHashMapIterator\<K, V> where K \<: Hashable & Equatable\<K>

```cangjie
public class ConcurrentHashMapIterator<K, V> <: Iterator<(K, V)> where K <: Hashable & Equatable<K> {
    public init(cmap: ConcurrentHashMap<K, V>)
}
```

功能：此类主要实现 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 的迭代器功能。

> **注意：**
>
> 这里定义的  [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 迭代器：
>
>1. 不保证迭代结果为并发 [HashMap](../../collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) 某一时刻的 “快照”，建议在环境中没有其它线程并发地修改  [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 时调用；
>2. 迭代器在迭代过程中，不保证可以感知环境线程对目标  [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 的修改。

父类型：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort)\<(K, V)>

### init(ConcurrentHashMap\<K, V>)

```cangjie
public init(cmap: ConcurrentHashMap<K, V>)
```

功能：创建 [ConcurrentHashMapIterator](collection_concurrent_class.md#class-concurrenthashmapiteratork-v-where-k--hashable--equatablek)\<K, V> 实例。

参数：

- cmap: [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)\<K, V> - 待获取其迭代器的 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)\<K, V> 实例。

### func iterator()

```cangjie
public func iterator(): Iterator<(K, V)>
```

功能：获取 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)\<K, V> 迭代器自身。

返回值：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort) <(K, V) > - 迭代器自身。

### func next()

```cangjie
public func next(): Option<(K, V)>
```

功能：返回迭代中的下一个元素。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) <(K, V) > - [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<(K,V)> 类型。

## class ConcurrentHashMap\<K, V> where K \<: Hashable & Equatable\<K>

```cangjie
public class ConcurrentHashMap<K, V> <: ConcurrentMap<K, V> & Collection<(K, V)> where K <: Hashable & Equatable<K> {
    public init(concurrencyLevel!: Int64 = 16)
    public init(capacity: Int64, concurrencyLevel!: Int64 = 16)
    public init(elements: Collection<(K, V)>, concurrencyLevel!: Int64 = 16)
    public init(size: Int64, initElement: (Int64) -> (K, V), concurrencyLevel!: Int64 = 16)
}
```

功能：此类用于实现并发场景下线程安全的哈希表 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 数据结构及相关操作函数。

当 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中出现键值对数量大于“桶”数量的情况时，会进行“扩容”。

构造函数中的参数 concurrencyLevel 表示“并发度”，即：最多允许多少个线程并发修改 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)。查询键值对的操作是非阻塞的，不受所指定的并发度 concurrencyLevel 的限制。参数 concurrencyLevel 默认等于 16。它只影响 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 在并发场景下的性能，不影响功能。

> **注意：**
>
> 如果用户传入的 concurrencyLevel 小于 16，则并发度会被设置为 16。
>
> concurrencyLevel 并非越大越好，更大的 concurrencyLevel 会导致更大的内存开销（甚至可能导致 out of memory 异常），用户需要在内存开销和运行效率之间进行平衡。

使用父类型：

- [ConcurrentMap](collection_concurrent_interface.md#interface-concurrentmapk-v-where-k--equatablek)\<K, V>
- [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<(K, V)>

示例：

使用示例见 [ConcurrentHashMap 使用示例](../collection_concurrent_samples/sample_concurrenthashmap.md)。

### prop size

```cangjie
public prop size: Int64
```

功能：返回键值的个数。

> **注意：**
>
> 此方法不保证并发场景下的原子性，建议在环境中没有其它线程并发地修改 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 时调用。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### init(Collection\<(K, V)>, Int64)

```cangjie
public init(elements: Collection<(K, V)>, concurrencyLevel!: Int64 = 16)
```

功能：构造一个带有传入迭代器和指定并发度的 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)。该构造函数根据传入迭代器元素 elements 的 size 设置 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 的容量。

参数：

- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<(K, V)> - 初始化迭代器元素。
- concurrencyLevel!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 用户指定的并发度。

### init(Int64)

```cangjie
public init(concurrencyLevel!: Int64 = 16)
```

功能：构造一个具有默认初始容量（16）和指定并发度（默认等于 16）的 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)。

参数：

- concurrencyLevel!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 用户指定的并发度。

### init(Int64, (Int64) -> (K, V), Int64)

```cangjie
public init(size: Int64, initElement: (Int64) -> (K, V), concurrencyLevel!: Int64 = 16)
```

功能：构造具有传入大小和初始化函数元素以及指定并发度的 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)。该构造函数根据参数 size 设置 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek) 的容量。

参数：

- size: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 初始化函数元素的大小。
- initElement: ([Int64](../../core/core_package_api/core_package_intrinsics.md#int64)) ->(K, V) - 初始化函数元素。
- concurrencyLevel!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 用户指定并发度。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 size 小于 0 则抛出异常。

### init(Int64, Int64)

```cangjie
public init(capacity: Int64, concurrencyLevel!: Int64 = 16)
```

功能：构造一个带有传入容量大小和指定并发度（默认等于 16）的 [ConcurrentHashMap](collection_concurrent_class.md#class-concurrenthashmapk-v-where-k--hashable--equatablek)。

参数：

- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 初始化容量大小。
- concurrencyLevel!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 用户指定的并发度。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果 capacity 小于 0 则抛出异常。

### func contains(K)

```cangjie
public func contains(key: K): Bool
```

功能：判断此映射中是否包含指定键 key 的映射。

参数：

- key: K - 传递要判断的 key。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否包含指定键 key 的映射，包含为true，不包含为false。

### func get(K)

```cangjie
public func get(key: K): ?V
```

功能：返回此映射中键 key 所关联的值。

参数：

- key: K - 传递 key，获取 value。

返回值:

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 此映射中键 key 所关联的值。

### func isEmpty()

```cangjie
public func isEmpty(): Bool
```

功能：判断 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 是否为空。

> **注意：**
>
> 此方法不保证并发场景下的原子性，建议在环境中没有其它线程并发地修改 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 时调用。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果是，则返回 true，否则，返回 false。

### func iterator()

```cangjie
public func iterator(): ConcurrentHashMapIterator<K, V>
```

功能：获取 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 的迭代器。

返回值：

- [ConcurrentHashMapIterator](collection_concurrent_class.md#class-concurrenthashmapiteratork-v-where-k--hashable--equatablek) < K, V > -[ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 的迭代器

### func put(K, V)

```cangjie
public func put(key: K, value: V): ?V
```

功能：将指定的值 value 与此 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek)中指定的键 key 关联。如果  [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中已经包含键 key 的关联，则旧值将被替换；如果 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中不包含键 key 的关联，则添加键 key 与值 value 的关联。

参数：

- key: K - 要放置的键。
- value: V - 要关联的值。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果赋值之前 key 存在，则返回旧的值 Some(V)；当赋值前 key 不存在时，返回 None。

### func putIfAbsent(K, V)

```cangjie
public func putIfAbsent(key: K, value: V): ?V
```

功能：当此 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek)中不存在键 key 时，在 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中添加指定的值 value 与指定的键 key 的关联。如果 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 已经包含键 key，则不执行赋值操作。

参数：

- key: K - 要放置的键。
- value: V - 要分配的值。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果赋值之前 key 存在，则返回当前 key 对应的值 Some(V)，且不执行赋值操作；当赋值前 key 不存在时，返回 None。

### func remove((K, (V) -> Bool))

```cangjie
public func remove(key: K, predicate: (V) -> Bool): ?V
```

功能：如果此映射中存在键 key 且 key 所映射的值 v 满足条件 predicate，则从此映射中删除 key 的映射。

参数：

- key: K - 传入要删除的 key。
- predicate: (V) ->[Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 传递一个 lambda 表达式进行判断。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果映射中存在 key，则返回 key 对应的旧值；当映射中不存在 key 时，或者 key 关联的值不满足 predicate 时，返回 None。

### func remove(K)

```cangjie
public func remove(key: K): ?V
```

功能：从此映射中删除指定键 key 的映射（如果存在）。

参数：

- key: K - 传入要删除的 key。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果移除之前 key 存在，则返回 key 对应的值 Some(V)；当移除时 key 不存在时，返回 None。

### func replace(K, (V) -> Bool, (V) -> V)

```cangjie
public func replace(key: K, predicate: (V) -> Bool, eval: (V) -> V): ?V
```

功能：如果 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中存在键 key（假设其关联的值为 v），且 v 满足条件 predicate，则将 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中键 key 关联的值替换为 eval(v) 的计算结果；如果 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中不存在键 key，或者存在键 key 但关联的值不满足 predicate，则不对 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 做任何修改。
参数：

- key: K - 传入要替换所关联值的键。
- predicate: (V) ->[Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 传递一个 lambda 表达式进行判断。
- eval: (V) ->V - 传入计算用于替换的新值的函数。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果 key 存在，则返回 key 对应的旧值 Some(V)；当 key 不存在时，或者 key 关联的值不满足 predicate 时，返回 None。

### func replace(K, (V) -> V)

```cangjie
public func replace(key: K, eval: (V) -> V): ?V
```

功能：如果 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中存在键 key（假设其关联的值为 v），则将 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中键 key 关联的值替换为 eval(v) 的计算结果；如果 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek)中不存在键 key，则不对 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 做任何修改。

参数：

- key: K - 传入要替换所关联值的键。
- eval: (V) ->V - 传入计算用于替换的新值的函数。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果 key 存在，则返回 key 对应的旧值 Some(V)；当 key 不存在时，返回 None。

### func replace(K, V)

```cangjie
public func replace(key: K, value: V): ?V
```

功能：如果 [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中存在 key，则将  [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中键 key 关联的值替换为 value；如果  [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 中不存在 key，则不对  [ConcurrentHashMap](#class-concurrenthashmapk-v-where-k--hashable--equatablek) 做任何修改。

参数：

- key: K - 传入要替换所关联值的键。
- value: V - 传入要替换成的新值。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<V> - 如果 key 存在，则返回 key 对应的旧值 Some(V)；当 key 不存在时，返回 None。

### operator func \[](K)

```cangjie
public operator func [](key: K): V
```

功能：运算符重载集合，如果键存在，返回键对应的值；如果不存在，抛出异常。

参数：

- key: K - 传递值进行判断。

返回值：

- V - 与键对应的值。

异常：

- [NoneValueException](../../core/core_package_api/core_package_exceptions.md#class-nonevalueexception) - 关联中不存在键 key。

### operator func \[](K, V)

```cangjie
public operator func [](key: K, value!: V): Unit
```

功能：运算符重载集合，如果键 key 存在，新 value 覆盖旧 value；如果键不存在，添加此键值对。

参数：

- key: K - 传递值进行判断。
- value!: V - 传递要设置的值。

## class NonBlockingQueue\<E>

```cangjie
public class NonBlockingQueue<E> {
    public init()
    public init(elements: Collection<E>)
}
```

功能：提供一个线程安全的队列，可以在多线程环境下安全地进行元素的添加和删除操作。

非阻塞队列的目的是为了解决多线程环境下的同步问题，使得多个线程可以并发地进行队列的操作，而不会出现数据冲突或者死锁的问题。

非阻塞队列在多线程编程中非常常见，它可以用于任何需要线程安全队列的场景，例如生产者消费者模型、任务调度、线程池等。

使用示例：

使用示例见 [NonBlockingQueue 使用示例](../collection_concurrent_samples/sample_noblocking_queue.md)。

### prop size

```cangjie
public prop size: Int64
```

功能：获取此 [NonBlockingQueue](collection_concurrent_class.md#class-nonblockingqueuee) 的元素个数。

> **注意：**
>
> 此方法不保证并发场景下的原子性，建议在环境中没有其它线程并发地修改 [NonBlockingQueue](collection_concurrent_class.md#class-nonblockingqueuee) 时调用。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### init()

```cangjie
public init()
```

功能：构造一个默认的 [NonBlockingQueue](collection_concurrent_class.md#class-nonblockingqueuee) 实例。

### init(Collection\<E>)

```cangjie
public init(elements: Collection<E>)
```

功能：根据 [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<E> 实例构造一个 [NonBlockingQueue](collection_concurrent_class.md#class-nonblockingqueuee) 实例。

参数：

- elements: [Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<E> - 将该容器中元素放入新构造的 [NonBlockingQueue](collection_concurrent_class.md#class-nonblockingqueuee) 实例中。

### func dequeue()

```cangjie
public func dequeue(): Option<E>
```

功能：获取并删除队首元素。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 成功删除则返回队首元素，队列为空则返回 None。

### func enqueue(E)

```cangjie
public func enqueue(element: E): Bool
```

功能：非阻塞的入队操作，将元素添加到队列尾部。

>**注意：**
>
>该函数不会返回 false。

参数：

- element: E - 要添加的元素。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 成功添加元素则返回 true。

### func head()

```cangjie
public func head(): Option<E>
```

功能：获取队首元素，不会删除该元素。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<E> - 成功获取则返回队首元素，队列为空则返回 None。
