# 接口

## interface SortByExtension

```cangjie
public interface SortByExtension
```

功能： 此接口作为排序相关的辅助接口，内部为空。

### extend\<T> Array\<T> <: SortByExtension

```cangjie
extend<T> Array<T> <: SortByExtension
```

功能： 此扩展用于实现 [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt) 的 `sortBy` 函数。

父类型：

- [SortByExtension](#interface-sortbyextension)

#### func sortBy(Bool, (T, T) -> Ordering)

```cangjie
public func sortBy(stable!: Bool = false, comparator!: (T, T) -> Ordering): Unit
```

功能：通过传入的比较函数，根据其返回值 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering) 类型的结果，可对数组进行自定义排序。

参数：

- stable!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否使用稳定排序。
- comparator!: (T, T) ->[Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering) - 用户传入的比较函数，如，comparator: (t1: T, t2: T) -> [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering)，如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).GT，排序后 `t1` 在 `t2` 后；如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).LT，排序后 `t1` 在 `t2` 前；如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).EQ，且为稳定排序那么 `t1` 与 `t2` 的位置较排序前保持不变； 如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).EQ，且为不稳定排序，那么 `t1`，`t2` 顺序不确定

## interface SortExtension

```cangjie
public interface SortExtension
```

功能： 此接口作为排序相关的辅助接口，内部为空。

### extend\<T> Array\<T> <: SortExtension where T <: Comparable\<T>

```cangjie
extend<T> Array<T> <: SortExtension where T <: Comparable<T>
```

功能： 此扩展用于实现 [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt) 的 `sort/sortDescending` 函数。

父类型：

- [SortExtension](#interface-sortextension)

#### func sort(Bool)

```cangjie
public func sort(stable!: Bool = false): Unit
```

功能：以升序的方式排序 [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)。

参数：

- stable!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否使用稳定排序。

#### func sortDescending(Bool)

```cangjie
public func sortDescending(stable!: Bool = false): Unit
```

功能：以降序的方式排序 [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)。

参数：

- stable!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否使用稳定排序。

