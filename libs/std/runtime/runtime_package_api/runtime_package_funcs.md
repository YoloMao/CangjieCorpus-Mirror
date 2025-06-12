# 函数

## func GC(Bool)

```cangjie
public func GC(heavy!: Bool = false): Unit
```

功能：执行 [GC](runtime_package_funcs.md#func-gcbool)。

参数：

- heavy!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - [GC](runtime_package_funcs.md#func-gcbool) 执行程度，如果为 true，执行会慢，内存收集的多一些，默认值为 false。

## func SetGCThreshold(UInt64)

```cangjie
public func SetGCThreshold(value: UInt64): Unit
```

功能：修改用户期望触发 [GC](runtime_package_funcs.md#func-gcbool) 的内存阈值，当仓颉堆大小超过该值时，触发 [GC](runtime_package_funcs.md#func-gcbool)，单位为 KB。

参数：

- value: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 用户期望触发 [GC](runtime_package_funcs.md#func-gcbool) 的内存阈值。

示例：
设置用户期望的 [GC](runtime_package_funcs.md#func-gcbool) 的内存阈值为 2MB。

```cangjie
import std.runtime.*
main() {
  SetGCThreshold(2048)
}
```
