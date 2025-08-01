# std.unittest

## 功能介绍

unittest 包用于编写仓颉项目单元测试代码，提供包括代码编写、运行和调测在内的基本功能，并为有经验的用户提供的一些高级功能。

仓颉单元测试支持 cjc 编译器（单包编译模式）和 cjpm 包管理器（ 多包模式）。

用户可通过[快速入门](./unittest_samples/unittest_getting_started.md#unittest-快速入门)写出第一个单元测试程序。同时文档对于一些[基础概念及用法](./unittest_samples/unittest_basics.md#unittest-基础概念及用法)做了说明并附有示例代码，另外，对于一些高阶特性例如[参数化测试](./unittest_samples/unittest_parameterized_tests.md#参数化测试入门)等做了进一步说明。

如下 API 从其他包中重导出，因此用户亦可以只导入 unittest 即可使用。

### 从 unittest.common 包中重导出

#### 接口

|              接口名          |           功能           |
| --------------------------- | ------------------------ |
| [DataProvider](../unittest_common/unittest_common_package_api/unittest_common_package_interfaces.md#interface-dataprovider) | DataStrategy 的组件，用于提供测试数据， T 指定提供者提供的数据类型。 |
| [DataShrinker](../unittest_common/unittest_common_package_api/unittest_common_package_interfaces.md#interface-datashrinkert) | DataStrategy 的组件，用于在测试期间缩减数据，T 指定该收缩器处理的数据类型。 |
| [DataStrategy](../unittest_common/unittest_common_package_api/unittest_common_package_interfaces.md#interface-datastrategy) | 为参数化测试提供数据的策略，T 指定该策略操作的数据类型。 |

#### 类

|              类名          |           功能           |
| --------------------------- | ------------------------ |
| [Configuration](../unittest_common/unittest_common_package_api/unittest_common_package_classes.md#class-configuration) | 存储 `@Configure` 宏生成的 `unittest` 配置数据的对象。`Configuration` 是一个类似 `HashMap` 的类，但它的键不是键和值类型，而是 `String` 类型，和任何给定类型的值。 |
| [ConfigurationKey](../unittest_common/unittest_common_package_api/unittest_common_package_classes.md#class-configurationkey) | 配置项的键值对象。提供判等及 hashCode 方法。 |

### 从 unittest.prop_test 包中重导出

#### 函数

|              函数名          |           功能           |
| --------------------------- | ------------------------ |
| [random\<T>()](../unittest_prop_test/unittest_prop_test_package_api/unittest_prop_test_package_functions.md#func-randomt-where-t--arbitraryt) | 该函数生成 T 类型的随机数据，其中 T 必须实现接口 Arbitrary\<T> 。该函数的返回值是参数化测试的一种参数源。 |

#### 接口

|              接口名          |           功能           |
| --------------------------- | ------------------------ |
| [Arbitrary](../unittest_prop_test/unittest_prop_test_package_api/unittest_prop_test_package_interfaces.md#interface-arbitrary) | 生成 T 类型随机值的接口。 |
| [Shrink](../unittest_prop_test/unittest_prop_test_package_api/unittest_prop_test_package_interfaces.md#interface-shrinkt) | 将 T 类型的值缩减到多个“更小”的值。 |

## API 列表

### 函数

|              函数名          |           功能           |
| --------------------------- | ------------------------ |
| [assertCaughtUnexpectedE(String, String, String, Option\<AssertionCtx>)](./unittest_package_api/unittest_package_functions.md#func-assertcaughtunexpectedestring-string-string-optionassertionctx) | 捕获的异常不符合预期，记录信息，抛出异常。 |
| [assertEqual\<T>(String, String, T, T, Option\<AssertionCtx>)](./unittest_package_api/unittest_package_functions.md#func-assertequaltstring-string-t-t-optionassertionctx-unit-where-t--equatablet) | 比较 `expected` 和 `actual` 值是否相等。若不等，直接抛出异常。 |
| [defaultConfiguration()](./unittest_package_api/unittest_package_functions.md#func-defaultconfiguration) | 生成默认的配置信息。 |
| [entryMain(TestPackage)](./unittest_package_api/unittest_package_functions.md#func-entrymaintestpackage) | 提供给 `cjc --test` 使用，框架执行测试用例的入口函数。 |
| [expectCaughtUnexpectedE(String,String,String, Option\<AssertionCtx>)](./unittest_package_api/unittest_package_functions.md#func-expectcaughtunexpectedestring-string-string-optionassertionctx) | 捕获的异常不符合预期，记录信息，不抛出异常。 |
| [expectEqual(String, String, T, T, Option\<AssertionCtx>)](./unittest_package_api/unittest_package_functions.md#func-expectequaltstring-string-t-t-optionassertionctx-unit-where-t--equatablet) | 比较 `expected` 和 `actual` 值是否相等。记录比较结果，不抛出异常。 |
| [fail(String)](./unittest_package_api/unittest_package_functions.md#func-failstring) | 使该用例失败，直接抛出异常。 |
| [failExpect(String)](./unittest_package_api/unittest_package_functions.md#func-failexpectstring) | 使该用例失败，记录信息，不抛出异常。 |
| [invokeCustomAssert\<T>(Array\<String>, String, (AssertionCtx) -> T, Option\<AssertionCtx>)](./unittest_package_api/unittest_package_functions.md#func-invokecustomasserttarraystring-string-assertionctx---t-optionassertionctx) | 运行在 [`@Test`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#test-宏), [`@TestCase`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#testcase-宏), 或 [`@CustomAssertion`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#customassertion-宏) 宏中使用的 [`@Assert[caller](passerArgs)`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#assert-宏) 指定的用户定义断言函数。 |
| [invokeCustomExpect\<T>(Array\<String>, String, (AssertionCtx) -> Any, Option\<AssertionCtx>)](./unittest_package_api/unittest_package_functions.md#func-invokecustomexpectarraystring-string-assertionctx---any-optionassertionctx) | 运行在 [`@Test`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#test-宏), [`@TestCase`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#testcase-宏), 或 [`@CustomAssertion`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#customassertion-宏) 宏中使用的 [`@Expect[caller](passerArgs)`](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#expect-宏) 指定的用户定义断言函数。 |

### 类型别名

|  类型别名 | 功能  |
| ------------ | ------------ |
| [MeasurementUnitTable](./unittest_package_api/unittest_package_types.md#type-measurementunittable) | 用于为性能测试指定 [Measurement](./unittest_package_api/unittest_package_interfaces.md#interface-measurement) 实例。|

### 接口

|              接口名          |           功能           |
| --------------------------- | ------------------------ |
| [BenchInputProvider](./unittest_package_api/unittest_package_interfaces.md#interface-benchinputprovider) | 用于处理性能测试的接口，其中需要在每次性能测试调用之前执行一些代码或者性能测试的输入发生了变化，并且每次都必须从头开始生成。|
| [BenchmarkConfig](./unittest_package_api/unittest_package_interfaces.md#interface-benchmarkconfig) | 空接口，区分部分 [Configuration](../unittest_common/unittest_common_package_api/unittest_common_package_classes.md#class-configuration) 函数为性能相关配置。|
| [BenchmarkInputMarker](./unittest_package_api/unittest_package_interfaces.md#interface-benchmarkinputmarker) | 当我们不知道 `T` 时，该接口能够检测 `BenchInputProvider<T>` 。|
| [Generator](./unittest_package_api/unittest_package_interfaces.md#interface-generatort) | 生成器生成 T 类型的值。 |
| [Measurement](./unittest_package_api/unittest_package_interfaces.md#interface-measurement) | 在性能测试过程中可以收集和分析各种数据的接口。性能测试期间使用的 `Measurement` 的具体实例在 `@Measure` 宏中指定（例如在类声明中）。|
| [TestClass](./unittest_package_api/unittest_package_interfaces.md#interface-testclass) | 提供创建 [TestSuite](./unittest_package_api/unittest_package_classes.md#class-testsuite) 的方法。|

### 类

|              类名          |           功能           |
| --------------------------- | ------------------------ |
|[AssertionCtx](./unittest_package_api/unittest_package_classes.md#class-assertionctx)|存储用户定义的断言的状态。提供用于编写​​用户定义断言的方法。|
| [Benchmark](./unittest_package_api/unittest_package_classes.md#class-benchmark) | 该类提供创建和运行单个性能测试用例的方法。 |
| [BenchReport](./unittest_package_api/unittest_package_classes.md#class-benchreport) | 提供性能用例执行结果报告处理能力。 |
| [CartesianProductProcessor\<T0,T1>](./unittest_package_api/unittest_package_classes.md#class-cartesianproductprocessort0t1) | 笛卡尔积处理器。 |
| [ConsoleReporter](./unittest_package_api/unittest_package_classes.md#class-consolereporter) | 打印单元测试用例结果或者性能测试用例结果到控制台。 |
| [CsvReporter](./unittest_package_api/unittest_package_classes.md#class-csvreporter) | 打印性能测试用例结果数据到 Csv 文件上。 |
| [CsvRawReporter](./unittest_package_api/unittest_package_classes.md#class-csvrawreporter) | 打印性能测试用例结果数据，该数据只有批次的原始测量值，到 Csv 文件上。 |
| [CsvStrategy\<T>](./unittest_package_api/unittest_package_classes.md#class-csvstrategyt) | `DataStrategy` 对 CSV 数据格式的序列化实现。 |
|[DataStrategyProcessor\<T>](./unittest_package_api/unittest_package_classes.md#class-datastrategyprocessort)| 所有 [DataStrategy](../unittest_common/unittest_common_package_api/unittest_common_package_interfaces.md#interface-datastrategy) 组件的基类。该类的实例由 [@Strategy](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#strategy-宏) 宏或成员函数创建。|
|[FlatMapProcessor\<T,R>](./unittest_package_api/unittest_package_classes.md#class-flatmapprocessortr)| 对参数数据进行 [FlatMap](../collection/collection_package_api/collection_package_function.md#func-flatmapt-r-t---iterabler) 的处理器。 |
|[FlatMapStrategyProcessor\<T,R>](./unittest_package_api/unittest_package_classes.md#class-flatmapstrategyprocessorTR)| 对参数数据进行 [FlatMap](../collection/collection_package_api/collection_package_function.md#func-flatmapt-r-t---iterabler) 的处理器。 |
| [InputParameter](./unittest_package_api/unittest_package_classes.md#class-inputparameter) | 入参对象类型。 |
| [JsonStrategy\<T>](./unittest_package_api/unittest_package_classes.md#class-jsonstrategyt) | `DataStrategy` 对 JSON 数据格式的序列化实现。 |
| [LazyCyclicNode](./unittest_package_api/unittest_package_classes.md#class-lazycyclicnode) | 用于在一个循环中一个接一个地推进类型擦除的内部惰性迭代器。 |
| [MapProcessor\<T,R>](./unittest_package_api/unittest_package_classes.md#class-mapprocessortr) | 对参数数据进行 [Map](../collection/collection_package_api/collection_package_function.md#func-mapt-rt---r) 的处理器。 |
| [PowerAssertDiagramBuilder](./unittest_package_api/unittest_package_classes.md#class-powerassertdiagrambuilder) | [PowerAssert](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#powerassert-宏) 输出结果构造器。 |
| [RandomDataProvider\<T>](./unittest_package_api/unittest_package_classes.md#class-randomdataprovidert) | 使用随机数据生成的 DataProvider 接口的实现。 |
| [RandomDataShrinker\<T>](./unittest_package_api/unittest_package_classes.md#class-randomdatashrinkert) | 使用随机数据生成的 DataShrinker 接口的实现。 |
| [RandomDataStrategy\<T>](./unittest_package_api/unittest_package_classes.md#class-randomdatastrategyt) | 使用随机数据生成的 DataStrategy 接口的实现。 |
| [RawStatsReporter](./unittest_package_api/unittest_package_classes.md#class-rawstatsreporter) | 未处理的性能测试数据报告器。仅给框架内部使用。 |
| [Report](./unittest_package_api/unittest_package_classes.md#class-report) | 打印测试用例结果报告的基类。 |
| [SerializableProvider\<T>](./unittest_package_api/unittest_package_classes.md#class-serializableprovidert) | 获取序列化数据 [DataProvider](../unittest_common/unittest_common_package_api/unittest_common_package_interfaces.md#interface-dataprovider) 接口的实现。 |
| [SimpleProcessor\<T>](./unittest_package_api/unittest_package_classes.md#class-simpleprocessort) | 简单的数据策略处理器。对 [DataStrategyProcessor](./unittest_package_api/unittest_package_classes.md#class-datastrategyprocessort) 的一种实现。 |
| [TestGroup](./unittest_package_api/unittest_package_classes.md#class-testgroup) | 提供构建和运行测试组合方法的类。 |
| [TestGroupBuilder](./unittest_package_api/unittest_package_classes.md#class-testgroupbuilder) | 提供配置测试组合的方法的构造器。 |
| [TestPackage](./unittest_package_api/unittest_package_classes.md#class-testpackage) | 用例包对象。|
| [TestReport](./unittest_package_api/unittest_package_classes.md#class-testreport) | 单元测试执行结果报告。 |
| [TestSuite](./unittest_package_api/unittest_package_classes.md#class-testsuite) | 提供构建和执行测试套方法的类。 |
| [TestSuiteBuilder](./unittest_package_api/unittest_package_classes.md#class-testsuitebuilder) | 提供配置测试套方法的测试套构造器。 |
| [UnitTestCase](./unittest_package_api/unittest_package_classes.md#class-unittestcase) | 提供创建和执行单元测试用例的方法的类。 |
| [XmlReporter](./unittest_package_api/unittest_package_classes.md#class-xmlreporter) | 打印单元测试用例结果数据到 Xml 文件上。 |

### 枚举

|              枚举名          |           功能           |
| --------------------------- | ------------------------ |
| [ExplicitGcType](./unittest_package_api/unittest_package_enums.md#enum-explicitgctype) | 用于指定 `@Configure` 宏的 `explicitGC` 配置参数。表示 GC 执行的三种不同方式。 |
| [TimeUnit](./unittest_package_api/unittest_package_enums.md#enum-timeunit) | 可以在 `TimeNow` 类构造函数中使用的时间单位。 |
| [PerfCounter](./unittest_package_api/unittest_package_enums.md#enum-perfcounter) | 枚举 [Perf](./unittest_package_api/unittest_package_structs.md#struct-perf) 构造器支持的 CPU 计数器。|

### 结构体

|              结构体名          |           功能           |
| --------------------------- | ------------------------ |
| [BatchInputProvider\<T>](./unittest_package_api/unittest_package_structs.md#struct-batchinputprovidert) | 输入提供程序，在执行之前在缓冲区中生成整个基准批次的输入。 |
| [BatchSizeOneInputProvider\<T>](./unittest_package_api/unittest_package_structs.md#struct-batchsizeoneinputprovidert) | 基准输入提供程序，在每次执行基准之前生成输入。 |
| [CpuCycles](./unittest_package_api/unittest_package_structs.md#struct-cpucycles) | 使用本机 `rdtscp` 指令测量 CPU 周期数。仅适用于 x86 平台。 |
| [GenerateEachInputProvider\<T>](./unittest_package_api/unittest_package_structs.md#struct-generateeachinputprovidert) | 基准输入提供程序，在每次执行基准之前生成输入。 |
| [ImmutableInputProvider\<T>](./unittest_package_api/unittest_package_structs.md#struct-immutableinputprovidert) | 最简单的输入提供程序，只需为基准测试的每次调用复制数据。适用于基准测试不会改变输入的情况。它在框架内默认使用。 |
| [Perf](./unittest_package_api/unittest_package_structs.md#struct-perf) | 使用linux 系统调用 `perf_event_open` 测量各种硬件和软件 CPU 计数器。仅在 Linux 上可用。 |
| [TimeNow](./unittest_package_api/unittest_package_structs.md#struct-timenow) | [Measurement](./unittest_package_api/unittest_package_interfaces.md#interface-measurement) 的实现，用于测量执行一个函数所花费的时间。 |

### 异常类

|              异常名          |           功能           |
| --------------------------- | ------------------------ |
| [AssertException](./unittest_package_api/unittest_package_exceptions.md#class-assertexception) | [@Expect](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#expect-宏) / [@Assert](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#assert-宏) 检查失败时所抛出的异常。 |
| [AssertIntermediateException](./unittest_package_api/unittest_package_exceptions.md#class-assertintermediateexception) |[@PowerAssert](../unittest_testmacro/unittest_testmacro_package_api/unittest_testmacro_package_macros.md#powerassert-宏) 检查失败时所抛出的异常。 |
| [UnittestCliOptionsFormatException](./unittest_package_api/unittest_package_exceptions.md#class-unittestclioptionsformatexception) | 控制台选项格式错误抛出的异常。 |
| [UnittestException](./unittest_package_api/unittest_package_exceptions.md#class-unittestexception) | 框架通用异常。 |
