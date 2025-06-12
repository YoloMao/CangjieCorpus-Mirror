# Unittest concepts

## Test and test case

A **test** is an entity marked with the `@Test` macro that will be executed during the testing process. 
There are two kinds of tests in Cangjie unittest framework: test classes and test functions.
Test functions are simpler, each containing everything that's needed to run the testing code directly.
Test classes can be used if you want to introduce deeper structure for your tests, or override the behaviour of the [test lifecycle](#test-lifecycle).

Each test class consists of a number of **test cases** each marked with the `@TestCase` macro.
Each test case is a function inside the test class.
Returning to our example from the previous section, the same test could be rewritten into a test class like this:

```cangjie
@Test
class AddTests {
    @TestCase
    func addTest() {
        @Expect(add(2, 3), 5)
    }

    @TestCase
    func addZero() {
        @Expect(add(2, 0), 2)
    }
}
```

A test function is a test with a single test case contained in the function. No @TestCase macro is needed in this case.

Running this new test class with `cjpm test` will produce output similar to the following:

```
--------------------------------------------------------------------------------------------------
TP: example/example, time elapsed: 67369 ns, Result:
    TCS: AddTests, time elapsed: 31828 ns, RESULT:
    [ PASSED ] CASE: addTest (25650 ns)
    [ PASSED ] CASE: addZero (4312 ns)
    Summary: TOTAL: 2
    PASSED: 2, SKIPPED: 0, ERROR: 0
    FAILED: 0
--------------------------------------------------------------------------------------------------
cjpm test success
```

## Assertions

An **assertion** is a single condition check that can be done inside the test case function body to *assert* that the code works correctly.
There are two kinds of assertions: `@Expect` and `@Assert`.
Let's create a faulty test to illustrate the difference:

```cangjie
@Test
func testAddIncorrect() {
    @Expect(add(3, 3), 5)
}
```

Running this test would fail and produce the following result (only the part that is relevant to this test):

```
    TCS: TestCase_testAddIncorrect, time elapsed: 4236 ns, RESULT:
    [ FAILED ] CASE: testAddIncorrect (3491 ns)
    Expect Failed: `(add ( 3 , 3 ) == 5)`
       left: 6
      right: 5
```

Replacing `@Expect` with `@Assert` would not make a difference in this case, but let's add one more check and run it again:

```cangjie
@Test
func testAddIncorrect() {
    @Expect(add(3, 3), 5)
    @Expect(add(5, 3), 9)
}
```

Running this test would fail and produce the following result (only the part that is relevant to this test):

```
    TCS: TestCase_testAddIncorrect, time elapsed: 5058 ns, RESULT:
    [ FAILED ] CASE: testAddIncorrect (4212 ns)
    Expect Failed: `(add ( 3 , 3 ) == 5)`
       left: 6
      right: 5

    Expect Failed: `(add ( 5 , 3 ) == 9)`
       left: 8
      right: 9
```

You can see how both checks are displayed in the output.
However, if we replace `@Expect` with `@Assert`:

```cangjie
@Test
func testAddIncorrectAssert() {
    @Assert(add(3, 3), 5)
    @Assert(add(5, 3), 9)
}
```

We will get the following output:

```
    TCS: TestCase_testAddIncorrectAssert, time elapsed: 31653 ns, RESULT:
    [ FAILED ] CASE: testAddIncorrectAssert (30893 ns)
    Assert Failed: `(add ( 3 , 3 ) == 5)`
       left: 6
      right: 5
```

We can see here that only the first `@Assert` check failed, and the rest of the test was not even run.
This is because `@Assert` macro is *fail-fast*: the first time it fails, it fails the whole test case, without checking subsequent assertions.

This difference becomes important in bigger test where a lot of assertions are involved, especially, if they are used in a loop.
It may be undesireable to get all the possible failures where the first failure is enough for the user.

Choosing between `@Assert` and `@Expect` in every particular test depends on how complicated your testing scenario is and if you want a fail-fast behaviour or not.

Both kinds of assertion macros provided by `unittest` can be used in two different ways:

- The equality assertion illustrated above where `@Assert(a, b)` or `@Expect(a, b)` take two parameters: this checks that the values of parameters `a` and `b` are equal to each other and require that, assuming the type of `a` is `A` and the type of `b` is `B`, `A` implements Equatable\<B>
- The boolean assertion `@Assert(c)` or `@Expect(c)` with a single parameter: this parameter is treated as a boolean value `true` or `false` and is required to have `Bool` as its type.

One can view the second form of assertion `@Assert(c)` as a short form for `@Assert(c, true)`.

<!-- TODO: @PowerAssert -->

### `@Fail`/`@FailExpect`
`@Fail` fails test immediately. `@FailExpect` fails the test but continue execution, it has `@Expect` semantic. 

There macros has only one form of "calling" with string message which describes the reason of failure. `@Fail` return type is `Nothing` and `@FailExpect` is `Unit`.

The test:
```
@Test
func validate_even_number_generator() {
    let even = generateRandomEven()
    if (even % 2 == 1) {
        @Fail("Not even number was generated: ${even}")
    }
}
```
can produce following output:
```
    [ FAILED ] CASE: validate_even_number_generator (54313 ns)
    Assert Failed: `(Not even number was generated: 111)`
```

### `@AssertThrows`/`@ExpectThrows`
`@AssertThrows` immeditely fails the test if no one of specified exceptions was thrown. `@ExpectThrows` marks test as failed but continues the execution.

After macro name the list of exception types can be specified in square brackets. If no exception specified then common `Exception` type is expected. This should be followed by a separate expression or code block where the exception is expected to occur.

Examples:
```
// 1
@AssertThrows(throw Exception())

// Semantically same as 1
@AssertThrows[Exception](throw Exception())

@AssertThrows[IllegalStateException | NoneValueException](random.seed = 42u64)

@ExpectThrows[OutOfMemoryError](foo())

@ExpectThrows({
    foo()
    boo()
})

@ExpectThrows[OutOfMemoryError]({
    for (i in list) {
        foo(i)
    }
})
```

#### Return type of @AssertThrows
In case of no more than one specified exceptions the return type matched the type:
```
let e: NoneValueException = @AssertThrows[NoneValueException](foo())
```

In case of several exceptions result type is smallest common supertype:
```
// A <: C
// B <: C
let e: C = @AssertThrows[A | B](foo())
````

#### Return type of @ExpectThrows
@ExpectThrows continues execution even if exception was not thrown, so it return type is Option\<T> where `T` is expected exception type:
```
let e: ?NoneValueException = @ExpectThrows[NoneValueException](foo())
```
In case of several exceptions result type is ?Exception:
```
let e: ?Exception = @ExpectThrows[NoneValueException | IllegalMemoryException](foo())
```

## Test lifecycle

Sometimes it is useful to share setup or teardown code between test cases. Test framework supports 4 **lifecycle** steps that are used through corresponding macros. Lifecycle steps can only be specified for `@Test` classes but not `@Test` top level functions.

|  |  |
| ---  | --- |
| @BeforeAll  | runs before any of the test cases |
| @BeforeEach | runs once before each test case |
| @AfterEach  | runs once after each test case |
| @AfterAll   | runs after all test cases have finished |

These macros must be put on a member or static function of the `@Test` class. `@BeforeAll` and `@AfterAll` functions must not declare any parameters. `@BeforeEach` and `@AfterEach` functions can declare a single parameter of type `String` (or no parameters).

```cangjie
@Test
class FooTest {
    @BeforeAll
    func setup() {
        // this code will run before any of tests are executed.
    }
}
```

Each macro can be applied to several functions inside a single class. Several **lifecycle** macros can be put on a single function. **Lifecycle** macros cannot be put on a function marked with `@TestCase` or similar macro.

If several functions are marked as the same lifecycle step, they will be executed in the same order they are declared in the code (from top to bottom).

Test framework provides the following guarantees:

1. **Before all** step is run at least once before any of the test cases are run.
2. For each test case `TC` in the test class:
    1. **Before each** step is run once before `TC`.
    2. `TC` is run.
    3. **After each** is run once after `TC`.
3. **After all** step is run after all test cases in the class.

Note that this does not apply if no test cases are run.

For simple scenarios **before all** and **after all** steps will only be run once. However there are exceptions:

<!-- TODO: link parallel running -->
- For [type parametrized test](./unittest_parameterized_tests_en.md#type-parameterized-tests) **before/after all** steps will be run for each combination of type arguments.
- If several test cases are executed in separate processes in parallel, **before/after all** steps will be run once per process.

`@BeforeEach` and `@AfterEach` can access the name of the test case being set up or torn down. This is done by specifying a single `String` parameter to the corresponding functions.

```cangjie
@Test
class Foo {
    @BeforeEach
    func prepareData(testCaseName: String) {
        // name of the test case function will be provided as the argument
        // "bar" in this example
    }

    @AfterEach
    func cleanup() {
        // not specifying the parameter is also allowed
    }

    @TestCase
    func bar() {}
}
```

<!-- TODO: link parametrized benchmarks -->
When setting up lifecycle for [parametrized tests](./unittest_parameterized_tests_en.md) or **parametrized benchmarks** take note that **before each** and **after each** steps will be executed only once before/after a test case or benchmark is executed for all its arguments. In other words, test body executing several times with different arguments is considered a single test case for the purposes of the lifecycle discussion.

If dedicated setup and teardown is required per argument for a parametrized test, put the corresponding code inside test case body itself. This has an additional advantage of being able to access the argument itself.

<!-- TODO: mention and link how to do setup/teardown per parameter in benchmarks -->

## Test configuration

Some of the more advanced features that you can find in unit test framework may require additional configuration.
Configuration of a test can be set up in three different ways:

- Using the `@Configure` macro
- Using command-line parameters when running test directly or through `cjpm test`
- Using configuration file of `cjpm`

<!-- TODO: configuration conversion algorithm -->

<!-- TODO: translation of runtime options -->