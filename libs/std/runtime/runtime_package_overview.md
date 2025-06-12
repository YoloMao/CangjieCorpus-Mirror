# std.runtime 包

## 功能介绍

runtime 包的作用是与程序的运行时环境进行交互，提供了一系列函数和变量，用于控制、管理和监视程序的执行。

CangJie 语言使用自动垃圾回收机制来管理内存，runtime 包提供了手动触发垃圾回收、设置垃圾回收的阈值、获取内存统计信息等功能，用于对垃圾回收进行调控和监测。

## API 列表

### 函数

|              函数名          |           功能           |
| --------------------------- | ------------------------ |
| [GC(Bool)](./runtime_package_api/runtime_package_funcs.md#func-gcbool) | 执行 GC。 |
| [SetGCThreshold(UInt64)](./runtime_package_api/runtime_package_funcs.md#func-setgcthresholduint64) | 修改用户期望触发 GC 的内存阈值，当仓颉堆大小超过该值时，触发 GC，单位为 KB。 |

### 结构体

|              结构体名              |                功能                 |
| --------------------------------- | ---------------------------------- |
| [MemoryInfo](./runtime_package_api/runtime_package_structs.md#struct-memoryinfo) | 提供获取一些堆内存统计数据的接口。 |
| [ThreadInfo](./runtime_package_api/runtime_package_structs.md#struct-threadinfo) | 提供获取一些仓颉线程统计数据的接口。 |
