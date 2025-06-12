# 结构体

## struct MemoryInfo

```cangjie
public struct MemoryInfo
```

功能：提供获取一些堆内存统计数据的接口。

### static prop allocatedHeapSize

```cangjie
public static prop allocatedHeapSize: Int64
```

功能：获取仓颉堆已被使用的大小，单位为 byte。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### static prop heapPhysicalMemory

```cangjie
public static prop heapPhysicalMemory: Int64
```

功能：获取仓颉堆实际占用的物理内存大小，单位为 byte。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### static prop maxHeapSize

```cangjie
public static prop maxHeapSize: Int64
```

功能：获取仓颉堆可以使用的最大值，单位为 byte。

实例：

```cangjie
import std.runtime.*
main() {
  println(MemoryInfo.maxHeapSize)
}
```

运行结果（以实际环境为准）：

```text
268435456
```

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)
