# 结构体

## struct BatchInputProvider

```cangjie
public struct BatchInputProvider<T> <: BenchInputProvider<T> {
    public BatchInputProvider(let builder: () -> T)
}
```

功能：输入提供程序，在执行之前在缓冲区中生成整个基准批次的输入。

父类型：

- [BenchInputProvider](unittest_package_interfaces.md#interface-benchinputprovider)\<T>

### init(() -> T)

```cangjie
public BatchInputProvider(let builder: () -> T)
```

功能： 默认构造函数。

参数：

- builder: () -> T - 用于生成基准测试输入的闭包。

### mut func get(Int64)

```cangjie
public mut func get(idx: Int64): T
```

功能：获取元素，该函数的执行时间包含在基准测量中，然后作为框架开销计算的一部分从结果中排除。

参数：

- idx : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  元素索引值。

返回值：

- T - 元素值。

### mut func reset(Int64)

```cangjie
public mut func reset(max: Int64)
```

功能：在基准测量之前调用。调用此函数后，后续的 `get(i)` 调用必须成功获取 [0, max) 中的 `i` 。

参数：

- max : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  最大值。

## struct BatchSizeOneInputProvider

```cangjie
public struct BatchSizeOneInputProvider<T> <: BenchInputProvider<T>{
    public BatchSizeOneInputProvider(let builder: () -> T)
}
```

功能：基准输入提供程序，在每次执行基准之前生成输入。
与 `GenerateEachInputProvider` 的区别在于，当批量大小为 1 时，我们可以测量。
每个基准测试调用都是独立的，因此输入生成永远不会包含在测量中。
如果 `GenerateEachInputProvider` 给出的结果质量较差，则应使用。 这种情况可能会发生，因为生成输入所需的时间比实际基准要多得多，或者如果输入生成的执行时间非常不稳定。

父类型：

- [BenchInputProvider](unittest_package_interfaces.md#interface-benchinputprovider)\<T>

### init(() -> T)

```cangjie
public BatchSizeOneInputProvider(let builder: () -> T)
```

功能： 默认构造函数。

参数：

- builder: () -> T - 用于生成基准测试输入的 lambda 。

### mut func get(Int64)

```cangjie
public mut func get(idx: Int64): T
```

功能：获取元素，该函数的执行时间包含在基准测量中，然后作为框架开销计算的一部分从结果中排除。

参数：

- idx : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  元素索引值。

返回值：

- T - 元素值。

### mut func reset(Int64)

```cangjie
public mut func reset(max: Int64)
```

功能：在基准测量之前调用。调用此函数后，后续的 `get(i)` 调用必须成功获取 [0, max) 中的 `i` 。

参数：

- max : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  最大值。

## struct GenerateEachInputProvider

```cangjie
public struct GenerateEachInputProvider<T> <: BenchInputProvider<T>{
    public GenerateEachInputProvider(let builder: () -> T)
}
```

功能：基准输入提供程序，在每次执行基准之前生成输入。
生成时间包含在基准测量中，然后作为框架开销计算的一部分从最终结果中排除。

父类型：

- [BenchInputProvider](unittest_package_interfaces.md#interface-benchinputprovider)\<T>

### init(() -> T)

```cangjie
public GenerateEachInputProvider(let builder: () -> T)
```

功能： 默认构造函数。

参数：

- builder: () -> T - 用于生成基准测试输入的闭包。

### mut func get(Int64)

```cangjie
public mut func get(idx: Int64): T
```

功能：获取元素，该函数的执行时间包含在基准测量中，然后作为框架开销计算的一部分从结果中排除。

参数：

- idx : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  元素索引值。

返回值：

- T - 元素值。

### mut func reset(Int64)

```cangjie
public mut func reset(max: Int64)
```

功能：在基准测量之前调用。调用此函数后，后续的 `get(i)` 调用必须成功获取 [0, max) 中的 `i` 。

参数：

- max : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  最大值。

## struct ImmutableInputProvider

```cangjie
public struct ImmutableInputProvider<T> <: BenchInputProvider<T> {
    public ImmutableInputProvider(let data: T)
}
```

功能：最简单的输入提供程序，只需为基准测试的每次调用复制数据。适用于基准测试不会改变输入的情况。它在框架内默认使用。

父类型：

- [BenchInputProvider](unittest_package_interfaces.md#interface-benchinputprovider)\<T>

### init(T)

```cangjie
public ImmutableInputProvider(let data: T)
```

功能： 默认构造函数。

参数：

- data: T - 基准测试的输入。

### mut func get(Int64)

```cangjie
public mut func get(idx: Int64): T
```

功能：获取元素，该函数的执行时间包含在基准测量中，然后作为框架开销计算的一部分从结果中排除。

参数：

- idx : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  元素索引值。

返回值：

- T - 元素值。

### static func createOrExisting(T, Int64)

```cangjie
public static func createOrExisting(arg: T, x!:Int64=0): ImmutableInputProvider<T>
```

功能：创建或获取一个 ImmutableInputProvider 对象。

参数：

- arg : T - 提供器需复制的参数。
- x!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  为实现重载而增加的参数。

返回值：

- ImmutableInputProvider\<T> - 输入提供器。

### static func createOrExisting\<U>(U): U where U <: BenchInputProvider\<T>

```cangjie
public static func createOrExisting<U>(arg: U): U where U <: BenchInputProvider<T>
```

功能：创建或获取一个 BenchInputProvider 的子类型对象。

参数：

- arg : T - 提供器需复制的参数。

返回值：

- U where U <: BenchInputProvider\<T> - 输入提供器。

## struct TimeNow

```cangjie
public struct TimeNow <: Measurement {
    public init()
    public init(unit: ?TimeUnit)
}
```

功能：[Measurement](unittest_package_interfaces.md#interface-measurement) 的实现，用于测量执行一个函数所花费的时间。

父类型：

- [Measurement](unittest_package_interfaces.md#interface-measurement)

### init()

```cangjie
public init()
```

功能：自动选择输出格式的默认构造函数。

### init(?TimeUnit)

```cangjie
public init(unit: ?TimeUnit) 
```

功能： `unit` 参数用于指定打印结果时将使用的时间单位。

参数：

- unit: ?[TimeUnit](unittest_package_enums.md#enum-timeunit) - 指定的时间单位。

### func measure(() -> Unit)

```cangjie
public func measure(f: () -> Unit): Float64
```

功能：计算将用于统计分析的对 f 的执行时长的测量数据。

参数：

- f: () -> [Unit](../../core/core_package_api/core_package_intrinsics.md#unit) - 被计算时间的执行体。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 计算得到的数据，用于统计分析。

### func measureIntermediate()

```cangjie
public func measureIntermediate(): Float64
```

功能：获取当前时间用于统计分析。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 计算得到的数据，用于统计分析。

### func toString(Float64)

```cangjie
public func toString(duration: Float64): String
```

功能：按时间单位打印传入的时间值。

参数：

- duration: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 需要被打印的时间数值。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 按指定单位输出的时间数字字符串。
