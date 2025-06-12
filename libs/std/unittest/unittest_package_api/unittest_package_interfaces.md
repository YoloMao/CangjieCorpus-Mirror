# 接口

## interface BenchInputProvider

```cangjie
public interface BenchInputProvider<T> <: BenchmarkInputMarker  {
    mut func get(idx: Int64): T
    mut func reset(max: Int64)
}
```

功能：用于处理性能测试的接口，其中需要在每次性能测试调用之前执行一些代码或者性能测试的输入发生了变化，并且每次都必须从头开始生成。
要使用此功能，您的 [DataStrategy](../../unittest_common/unittest_common_package_api/unittest_common_package_interfaces.md#interface-datastrategy) 实现应返回此接口的实现者。
推荐的方法是使用 [@Strategy](../../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#strategy-宏) 宏。

父类型：

- [BenchmarkInputMarker](#interface-benchmarkinputmarker)

### mut func get(Int64)

```cangjie
mut func get(idx: Int64): T
```

功能：获取元素，该函数的执行时间包含在基准测量中，然后作为框架开销计算的一部分从结果中排除。

参数：

- idx : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  元素索引值。

返回值：

- T - 元素值。

### mut func reset(Int64)

```cangjie
mut func reset(max: Int64)
```

功能：在基准测量之前调用。调用此函数后，后续的 `get(i)` 调用必须成功获取 [0, max) 中的 `i` 。

参数：

- max : [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  最大值。

## interface BenchmarkConfig

```cangjie
public interface BenchmarkConfig{}
```

功能：空接口，区分部分 [Configuration](../../unittest_common/unittest_common_package_api/unittest_common_package_classes.md#class-configuration) 函数为性能相关配置。

## interface BenchmarkInputMarker

```cangjie
public interface BenchmarkInputMarker
```

功能：当我们不知道 `T` 时，该接口能够检测 `BenchInputProvider<T>` 。

## interface Generator\<T>

```cangjie
public interface Generator<T> {
    func next(): T
}
```

功能：生成器生成 T 类型的值。

### func next()

```cangjie
func next(): T
```

功能：获取生成出来的 T 类型的值。

返回值：

- T - 生成的 T 类型的值。

## interface Measurement

```cangjie
public interface Measurement {
    func measure(f: () -> Unit): Float64
    func measureIntermediate(): Float64 { 0.0 }
    func toString(f: Float64): String
}
```

功能：在性能测试过程中可以收集和分析各种数据的接口。性能测试框架使用的特定实例由 `@Configure` 宏的 `measurement` 参数指定。

### func measure(() -> Unit)

```cangjie
func measure(f: () -> Unit): Float64
```

功能： 返回将用于统计分析的测量 `f` 执行时长的数据。

参数：

- f: () -> [Unit](../../core/core_package_api/core_package_intrinsics.md#unit) - 是一个 lambda，应该测量它的执行信息。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 测量得到的数据。

### func measureIntermediate()

```cangjie
func measureIntermediate(): Float64
```

功能：将用于统计分析的测量运行时间的方法。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 测量得到的数据。

### func toString(Float64)

```cangjie
func toString(f: Float64): String
```

功能：将测量数据的浮点表示转换为将在性能测试输出中使用的字符串。

参数：

- f: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 测量数据的浮点表示。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 按规则转换后的字符串。

## interface Reporter

```cangjie
sealed interface Reporter <TReport, TReturn>
```

功能：报告器基础接口。

## interface TestClass

```cangjie
public interface TestClass {
    func asTestSuite(): TestSuite
}
```

功能：提供创建 [TestSuite](./unittest_package_classes.md#class-testsuite) 的方法。

### func asTestSuite()

```cangjie
func asTestSuite(): TestSuite
```

功能：创建 [TestSuite](./unittest_package_classes.md#class-testsuite) 的方法。

返回值：

- [TestSuite](./unittest_package_classes.md#class-testsuite) - 测试套对象。
