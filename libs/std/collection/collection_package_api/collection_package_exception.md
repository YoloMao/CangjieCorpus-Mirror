# 异常

## class ConcurrentModificationException

```cangjie
public class ConcurrentModificationException <: Exception {
    public init()
    public init(message: String)
}
```

功能：并发修改异常类。当函数检测到不同步的并发修改，抛出异常。

由于 collection 包提供的容器类都不支持并发修改，因此在执行某些操作时，会抛出 [ConcurrentModificationException](collection_package_exception.md#class-concurrentmodificationexception)。

典型的抛异常场景有：

- 使用 for-in 遍历一个容器过程中对容器进行修改时([HashMapIterator](collection_package_class.md#class-hashmapiteratork-v-where-k--hashable--equatablek)的[remove](../../os_posix/os_posix_package_api/os_posix_package_funcs.md#func-removestring)() 方法除外)。
- 在使用声明周期较短的类型，如 [EntryView](colleciton_package_struct.md#struct-entryviewk-v-where-k--hashable--equatablek)、[TreeMapNode](colleciton_package_struct.md#struct-treemapnodek-v-where-k--comparablek) 时，如果其所在的容器内容被修改，也会抛出异常。

父类型：

- [Exception](../../core/core_package_api/core_package_exceptions.md#class-exception)

### init()

```cangjie
public init()
```

功能：构造一个不带异常信息的实例。

### init(String)

```cangjie
public init(message: String)
```

功能：根据异常信息构造异常实例。

参数：

- message: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 异常信息。
