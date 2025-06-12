# ref 包

## 介绍

ref 包提供了弱引用相关的能力，弱引用是一个相对“强引用”的概念，对于强引用，如果引用不为空并且运行时分析可达性成立，则 GC 不会回收它，但是对于弱引用，在一些情况下即使可达性成立，GC 依然可能会回收该引用。

## 主要接口

### class WeakRefBase

```cangjie
sealed abstract class WeakRefBase
```

此类不包含任何公开成员和公开函数，也不允许被继承、扩展， 仅作为 `WeakRef` 的基类。

### enum CleanupPolicy

```cangjie
public enum CleanupPolicy <: Equatable<CleanupPolicy> {
    | EAGER
    | DEFERRED
}
```

该枚举表示不同的弱引用清理策略，分别为 `EAGER` 和 `DEFERRED`。

在 `WeakRef` 类中可以指定对象的清理策略。

#### EAGER

```cangjie
EAGER
```

功能：用于指定 `WeakRef` 实例的清理策略为 `EAGER` ，在该清理策略下，GC 会尽快回收掉 `WeakRef` 中的对象。

#### DEFERRED

```cangjie
DEFERRED
```

功能：用于指定 `WeakRef` 实例的清理策略为 `DEFERRED` ，在该清理策略下，GC 会尽可能保证 `WeakRef` 中的对象存活，只有在例如可用内存不足时才回收它。

#### operator func ==

```cangjie
public operator func ==(that: CleanupPolicy): Bool
```

功能：对 `Enum CleanupPolicy` 判断是否相等。

参数：

- that：被比较的对象

返回值：当前回收策略与 `that` 回收策略相同时返回 `true`，否则返回 `false`

#### operator func !=

```cangjie
public operator func !=(that: CleanupPolicy): Bool
```

功能：判不等。

参数：

- that：被比较的对象

返回值：当前回收策略与 `that` 回收策略不同时返回 `true`，否则返回 `false`

### class WeakRef

```cangjie
public class WeakRef<T> <: WeakRefBase where T <: Object {
    public init(value: T, cleanupPolicy: CleanupPolicy)
}
```

此类提供弱引用相关的功能，如果一个对象的引用被标记为弱引用，那么即使引用不为空并且该对象的可达性成立， GC 也可以按照指定的回收策略回收它。

#### init

```cangjie
public init(value: T, cleanupPolicy: CleanupPolicy)
```

功能：为 `value` 对象创建弱引用。

参数：

- value：弱引用指向的对象
- cleanupPolicy：`value` 对象的清理策略

#### prop cleanupPolicy

```cangjie
public prop cleanupPolicy: CleanupPolicy
```

功能：获取该弱引用的清理策略。

#### prop value

```cangjie
public prop value: Option<T>
```

功能：读取弱引用指向的对象。如果弱引用为空或弱引用中的对象已被清理则返回 `None`。

#### func clear

```cangjie
public func clear(): Unit
```

功能：强制清理弱引用指向的对象，后续对 `value` 的访问将返回 `None`。

## 示例

### WeakRef 用于缓存

以下使用 `WeakRef` 实现了一个缓存，假设某个数据的计算非常耗时，我们希望将其计算结果缓存起来，但又不希望过量缓存导致 OOM ，那么我们可以使用弱引用。

```cangjie
import std.ref.{WeakRef, CleanupPolicy}

public interface Cacheable<T> {
    static func reCalculate() : T
}

public class Data <: Cacheable<Data> {
    public var number: Int64

    init(n : Int64) {
                number = n
    }

    public static func reCalculate(): Data {
        // 模拟运算
        println("re-calculations!")
        let data = Data(321)
        return data
    }
}

public class Cache<T> where T <: Object & Cacheable<T> {
    private var cache : WeakRef<T>

    public init(data: T) {
        cache = WeakRef<T>(data, CleanupPolicy.DEFERRED) // 这里我们选用 DEFERRED 策略，因为我们希望 Data 保存的尽量久。
    }

    public func getData(): T {
        match(cache.value) {
            case Some(x) => x
            case None =>
                // 如果 GC 释放了缓存中的数据则重新运算
                let data = T.reCalculate()
                cache = WeakRef<T>(data, CleanupPolicy.DEFERRED)
                data
        }
    }

    public func clear() : Unit {
        cache.clear()
    }
}

main () {
    let data = Data(123)
    var c = Cache<Data>(data)
    println(c.getData().number) // 直接从缓存中读取数据，不需要重新运算
    println(c.getData().number) // 直接从缓存中读取数据，不需要重新运算
    c.clear()                   // 清空缓存
    println(c.getData().number) // 重新运算
    return 0
}
```

运行结果如下：

```text
123
123
re-calculations!
321
```
