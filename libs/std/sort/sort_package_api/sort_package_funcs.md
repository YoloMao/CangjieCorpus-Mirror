# 函数

## func stableSort\<T>(Array\<T>) where T <: Comparable\<T>

```cangjie
public func stableSort<T>(data: Array<T>): Unit where T <: Comparable<T>
```

功能：对数组进行稳定升序排序。

参数：

- data: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<T> - 需要排序的数组。

## func stableSort\<T>(Array\<T>, (T, T) -> Ordering)

```cangjie
public func stableSort<T>(data: Array<T>, comparator: (T, T) -> Ordering): Unit
```

功能：对数组进行稳定排序。

用户可传入自定义的比较函数 `comparator`，如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).GT，排序后 `t1` 在 `t2` 后；如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).LT，排序后 `t1` 在 `t2` 前；如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).EQ，排序后 `t1` 与 `t2` 的位置较排序前保持不变。

参数：

- data: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<T> - 需要排序的数组。
- comparator: (T, T) ->[Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering) - 用户传入的比较函数。

## func unstableSort\<T>(Array\<T>) where T <: Comparable\<T>

```cangjie
public func unstableSort<T>(data: Array<T>): Unit where T <: Comparable<T>
```

功能：对数组进行不稳定升序排序。

参数：

- data: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<T> - 需要排序的数组。

## func unstableSort\<T>(Array\<T>, (T, T) -> Ordering)

```cangjie
public func unstableSort<T>(data: Array<T>, comparator: (T, T) -> Ordering): Unit
```

功能：对数组进行不稳定排序。

用户可传入自定义的比较函数 `comparator`，如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).GT，排序后 `t1` 在 `t2` 后；如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).LT，排序后 `t1` 在 `t2` 前；如果 `comparator` 的返回值为 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).EQ，排序后 `t1` 与 `t2` 的位置较排序前保持不变。

参数：

- data: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<T> - 需要排序的数组。
- comparator: (T, T) ->[Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering) - 用户传入的比较函数。

