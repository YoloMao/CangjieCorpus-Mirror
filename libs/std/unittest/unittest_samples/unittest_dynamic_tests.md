# 动态测试

## 动态测试入门

仓颉测试框架支持动态测试，其支持在存在编译期未知的测试数据时构造测试用例。关键场景如下：

- 创建基于外部数据的测试套。
- 创建基于参数或配置文件的测试套。

通过与普通测试用例对比，可以看到如何通过 `@TestBuilder` 来构造动态测试用例。

如下是一个通过 `@Test/@TestCase` 构造的简单测试套：

```cangjie
@Test
class A {
    @TestCase
    func f() { @Assert(false) }

    @TestCase[x in [1, 2]]
    func g(x: Int) {
        @Assert( x >= 1 )
    }
}
```

通过 `@TestBuilder` 可以创建跟上述测试套相同逻辑的动态测试套 ：

```cangjie
@TestBuilder
public func buildCustomTestSuite(): TestSuite {
   let suiteBuilder = TestSuite.builder("A")
   let caseConfiguration = Configuration()
   suiteBuilder.add(
       UnitTestCase.create("f", configuration: caseConfiguration) { @Assert(false) })
   suiteBuilder.add(
       UnitTestCase.createParameterized("g", [1, 2]) { value => @Assert( value >= 1 ) })
   suiteBuilder.build()
}
```

`TestSuite` 创建了一个 `TestSuiteBuilder` 对象，该对象支持添加用例。用例通过 `UnitTestCase` 类中的静态函数构造。该类支持构造简单用例或者参数化用例。
`TestSuiteBuilder` 被配置完毕后，最终创建生成一个 `TestSuite` 对象，作为被 `@TestBuilder` 修饰的函数的返回值。

当上述代码通过 `--test` 编译后再执行，输出结果与 `@Test`/`@TestCase` 构造的测试套一致。

```text
--------------------------------------------------------------------------------------------------
TP: default, time elapsed: 121592 ns, RESULT:
    TCS: A, time elapsed: 121592 ns, RESULT:
    [ PASSED ] CASE: g (13969 ns)
    [ FAILED ] CASE: f (91641 ns)
    Assert Failed: `(false == true)`
       left: false
      right: true

Summary: TOTAL: 2
    PASSED: 1, SKIPPED: 0, ERROR: 0
    FAILED: 1, listed below:
            TCS: A, CASE: f
--------------------------------------------------------------------------------------------------
```

`@TestBuilder` 有如下约束:

- 它只能修饰顶层函数，且该函数不能是 `foreign` 函数。
- 它的返回值类型必须被显式指定，且必须为 `TestSuite` 类型。
- 它可以与 `@Configure` / `@Timeout` / `@Parallel` 宏组合使用，不允许与 unittest.testmacro 包中其他的宏组合。
