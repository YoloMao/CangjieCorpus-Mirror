# Dynamic Tests

## Getting Started with dynamic Tests

Cangjie Unittest framework supports dynamic tests, which could create test structures that are **NOT** known at compile time. This include:

- Creating test suites based on data from outside source.
- Creating test suite based on run parameters/configuration files.

To show how to use TestBuilder, We compare it with normal testsuite.

So here is a testsuite created by @Test/@TestCase:

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

Create the same testsuite with TestBuilder is as below:

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

TestSuite build a TestSuiteBuilder which could add testcases. The testcase is created by UnitTestCase, which could create simple cases or parameterized tests.
TestSuiteBuilder builds a TestSuite, as the result of function with @TestBuilder.

when it's compiled with `--test`, and run, the output of it is the same as the cases built with @Test/@TestCase.

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

@TestBuilder has the following rules:

- It must be put on a top level function. This function cannot be foreign.
- The return type of the function must be specified explicitly and be `TestSuite`.
- It is allowed to be combined with @Configure, @Timeout, @Parallel macro, but not other macros in std.unittest.testmacro package.