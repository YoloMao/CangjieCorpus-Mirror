# Using stubs

There are different ways in which you might want to use mock/spy objects and stubs. This guideline describes different patterns and usecases that help writing maintable and concise tests that use **mock framework**.

## How stubs work

[Stubs](./mock_framework_basics_en.md#configuration-api) are declared by invoking `@On` macro inside a test case. A stub is only effective since it was declared and until this particular test case finished execution. Stubs can be [shared](#sharing-mocks-and-stubs) between several test cases.

When mock framework tries to handle an invocation of a member of a mock/spy object it goes through the following sequence:

* Lookup stubs for this particular member. Stubs that are declared later take precedence over stubs that are declared earlier. Stubs declared inside test case body take precedence over shared stubs.
* Apply **arguments matcher** of each stub. If all arguments were matched successfully then execute the action defined by that stub.
* If no stubs were found or none matched the actual arguments then default behaviour will be applied: for mock objects is to report an **unstubbed invocation** error, for spy objects invoke the original member of the spied on instance.

Regardless of whether several stubs were defined for a single member, each stub has its own [expectations](./mock_framework_basics_en.md#expectations) that need to be met for the test to pass.

```cangjie
@On(foo.bar(1)).returns(1)
@On(foo.bar(2)).returns(2)

foo.bar(2)
// the first stub was defined but never used, the test will fail
```

## Redefining stubs

Stubs can be redefined. Use this if you want behaviour of the stub to change inside the test.

```cangjie
@On(service.request()).returns(testData)
// use service

@On(service.request()).throws(Exception())
// test what happens if the service starts failing
```

## Several stubs for the same member

Multiple stubs can be used to define different behaviour depending on the argument.

Let's look at the following example:

```cangjie
@On(storage.get(_)).returns(None)                  // 1
@On(storage.get(TEST_ID)).returns(Some(TEST_DATA)) // 2
```

This would mean the following: `storage` should return `None` for all arguments but `TEST_ID`.
The test will fail if `get` is never called with `TEST_ID` argument as stub **2** would be unused. The test will fail if `get` is always called with `TEST_ID` argument as stub **1** would be unused. These restrictions help to keep the test code cleaner letting the developer know whenever the stub becomes unused. If this is undesirable for some particular usecase, `anyTimes()` cardinality specifier should be used to lift these expectations.

```cangjie
// implementation changes frequently and we do not want the test to break
// using anyTimes to lift expectations unrelated to the test itself
@On(storage.get(_)).returns(None).anyTimes()
@On(storage.get(TEST_ID)).returns(Some(TEST_DATA)) // the test must call this because this is what is being tested
```

Because stub priority is **bottom to top**, the following usage would **not** be correct.

```cangjie
@On(storage.get(TEST_ID)).returns(Some(TEST_DATA)) // incorrect, this stub can never be triggered
@On(storage.get(_)).returns(None)                  // this will always shadow the stub above
```

You can also use expectation to check the arguments of the call.

```cangjie
let renderer = spy(Renderer())

@On(renderer.render(_)).fails()
let isVisible = { c: Component => c.isVisible }
@On(renderer.render(argThat(isVisible))).callsOriginal() // only components that are visible allowed
```

## Sharing mocks and stubs

Tests that use mock objects extensively can benefit from sharing mock objects and/or stubs between test cases.
There are no limitations on where mocks or spies can be created. However accidentally leaking mock object from one test case to another can lead to order dependent and otherwise unstable tests. Such usages should be avoided, mock framework will make best effort to detect such cases.
To share a single mock or spy between test cases in a test class they can be put in a instance variable of that class.

Sharing stubs is trickier because stub declarations imply expectations. Expectations cannot be shared between test cases.
There are only 2 correct places to declare stubs:

* Test case body (be it a `@Test` func or a `@TestCase` in a `@Test` class) - expectations will be checked.
* `beforeAll` in a `@Test` class - the stub will be shared between test cases. Such stubs cannot declare expectations and expectations will not be checked. Cardinality specifiers are not allowed. Only *stateless* actions such as `returns(value)`, `throws(exception)`, `fails()`, `callsOriginal()` are allowed. You can think of these stubs as having `anyTimes()` cardinality implicitly.

If test cases share the same expectations, utility function can be extracted and invoked in test case body.

Using `beforeAll`:

```cangjie
@Test
class TestFoo {
    let foo = mock<Foo>()

    // unittest framework will call this before executing test cases
    public func beforeAll(): Unit {
        // share default behaviour between all test cases
        // this stub does not have to be used in every test case
        @On(foo.bar(_)).returns("default")
    }

    @TestCase
    func testZero() {
        @On(foo.bar(0)).returns("zero") // this stub is specific to this test case and is expected to be used
        foo.bar(0) // returns "zero"
        foo.bar(1) // returns "default"
    }

    @TestCase
    func testOne() {
        @On(foo.bar(0)).returns("one")
        foo.bar(0) // returns "one"
    }
}
```

Using utility function:

```cangjie
@Test
class TestFoo {
    let foo = mock<Foo>()

    func setupDefaultStubs() {
        @On(foo.bar(_)).returns("default")
    }

    @TestCase
    func testZero() {
        setupDefaultStubs()
        @On(foo.bar(0)).returns("zero")

        foo.bar(0) // returns "zero"
        foo.bar(1) // returns "default"
    }

    @TestCase
    func testOne() {
        setupDefaultStubs()
        @On(foo.bar(0)).returns("zero")
        foo.bar(0) // returns "zero"

        // expectation failed, stub was declared but never used
    }
}
```

Note: do **not** declare stubs in test class constructors. There are no guarantees about when the test consructor is invoked.

## Capturing arguments
<!-- link value listener api for this section -->

Mock framework allows to inspect actual arguments passed into a stubbed member. This is done by **capturing** arguments using `captor(ValueListener)` argument matcher. `ValueListener` intercept corresponding arguments whenever the stub is triggered and allows to inspect the arguments and/or add validate the arguments.

To validate a certain condition on every call use ValueListener.onEach static function. It accepts a lambda that will be invoked whenever the stub is triggered. The lambda receives the value of the argument.

```cangjie
let renderer = spy(TextRenderer())
let markUpRenderer = MarkupRenderer(renderer)

// create validator
let validator = ValueListener.onEach { str: String =>
    @Assert(str == "must be bold")
}

// use 'capture' argument matcher to bind arguments to the validator
@On(renderer.renderBold(capture(validator))).callsOriginal() // note that the test will fail if this is never invoked

markUpRenderer.render("text inside tag <b>must be bold</b>")
```

Additionally `ValueListener` provides `allValues()` and `lastValue()` functions to inspect the arguments. Use the following pattern:

```cangjie
// create captor
let captor = ValueListener<String>.new()

// use 'capture' argument matcher to bind arguments to the captor
@On(renderer.renderBold(capture(captor))).callsOriginal()

markUpRenderer.render("text inside tag <b>must be bold</b>")

let argumentValues = captor.allValues()
@Assert(argumentValues.size == 1 && argumentValues[0] == "must be bold")
```

`argThat` matcher has an overload that combines argument filtering and capturing. `argThat(listener, filter)` accepts a `ValueListener` instance and a `filter` predicate. `listener` will only collect arguments which pass the `filter` check.

<!-- link argThat matcher -->

```cangjie
let filter = { arg: String => arg.contains("bold") }
let captor = ValueListener<String>.new()

// fail unless the argument is intercepted but the stub declared below
@On(renderer.renderBold(_)).fails()
// only allow strings that contain "bold" substring and collect them
@On(renderer.renderBold(argThat(captor, filter))).callsOriginal()

markUpRenderer.render("text inside tag <b>must be bold</b>")

// we can inspect all the filtered arguments using 'captor' object
@Assert(captor.lastValue() == "must be bold")
```

Argument captors can be used together with both mocks and spies. However usage of such argument matchers is disallowed in [@Called](./mock_framework_verification_en.md#verify-statements-and-called-macro) macro.

## Defining and using custom argument matchers

To avoid repeating the same **argument matcher** custom argument matcher can be defined.

Suppose we want to share the following matchers between our test cases:

```cangjie
@On(foo.bar(oddNumbers())).returns("Odd")
@On(foo.bar(evenNumbers())).returns("Even")
foo.bar(0) // "Even"
foo.bar(1) // "Odd"
```

Since every matcher is just a static function of `Matchers` class, custom argument matchers can be defined using **extend**. New argument matchers should call existing ones.

<!-- link Matchers class -->

```cangjie
extend Matchers {
    static func evenNumbers(): TypedMatcher<Int> {
        argThat { arg: Int => arg % 2 == 0}
    }

    static func oddNumbers(): TypedMatcher<Int> {
        argThat { arg: Int => arg % 2 == 1}
    }
}
```

As any other function argument matchers can have arguments.

```cangjie
extend Matchers {
    // will only accept Int arguments.
    static func isDivisibleBy(n: Int): TypedMatcher<Int> {
        argThat { arg: Int => arg % n == 0}
    }
}
```

Most matcher functions have `TypedMatcher<T>` return type. Such matcher will only accept values of type `T`. Whenever an argument matcher invocation is used in a stub declaration, values of type `T` should be a valid argument to the function/setter being stubbed. In other words type `T` should be a subtype of or the same as the actual type of the argument.

## Stubbing properties and fields

Fields and properties can be stubbed in the same way that methods can. The [same actions](./mock_framework_basics_en.md#actions-api) can be used to configure the return value.

Setters are similar to functions returning `Unit`. Special action `doesNothing()` is available for setters.

The usual pattern for stubbing mutable properties is:

```cangjie
@On(foo.prop).returns("value")  // configure getter
@On(foo.prop = _).doesNothing() // ignore setter calls
```

In rare cases we want mutable properties to behave in the same manner as fields would. To create **synthetic fields** use `SyntheticField.create` static function. Synthetic field is a storage managed by mock framework. Use it when mocking interfaces or abstract classes that have mutable fields or properties.

<!-- link SyntheticField class -->

Use `getsField` and `setsField` stub actions to bind the field to specific invocations. These actions can configure expectations as any other action.

<!-- link field actions doc -->

```cangjie
interface Foo {
    mut prop bar: String
}

@Test
func test() {
    let foo = mock<Foo>()
    let syntheticField = SyntheticField.create(initialValue: "initial")
    @On(foo.bar).getsField(syntheticField)     // read access to the property should read synthetic field
    @On(foo.bar = _).setsField(syntheticField) // writes should set new value to the property

    // from now on 'bar' property will behave field would
}
```

Note that if `SyntheticField` object is shared between several test cases, the value of the field itself will be reset to the `initialValue` before each test case to avoid sharing mutable state between the tests.

If the stubs for mutable properties or fields do not need to specify any expectations, [SyntheticFields mode](#syntheticfields-mode) can be used to simplify the setup.

## Using stub modes

Ordinarily if some invocation does not match any stubs, an **unstubbed invocation** exception will be thrown. However mock objects can be configured to add default behaviour for some common cases. So when a particular invocation would not be handled by any of the stubs, some fallback behaviour is applied. This is done via **stub modes**.

There are two modes available `ReturnsDefaults` and `SyntheticFields`. These modes are represented as enum `StubMode`.
Stub modes can be enabled for a particular mock object by passing them to `mock` function when creating mock objects.

```cangjie
public func mock<T>(modes: Array<StubMode>): T
```

Stub modes can be used to reduce boilerplate when configuring mock objects and they can be freely combined with explicit stubs. Explicit stubs always take precedence over default behaviour.

Take note that using stub modes does not impose any expectations on members of mock object. If the intention of the test is to check that only specific members of a particular mock object are invoked, stub modes should be used with care. The behaviour of the system might change in an undesired way and the test might still pass.

### ReturnsDefaults mode

In this mode members returning one of the predefined types (listed below) can be used without explicit configuration.

```cangjie
let foo = mock<Foo>(ReturnsDefaults)
@Assert(foo.isPretty(), false)
```

Such members would return *negative* or *empty* values by default. The following types are supported.

| types | default value |
| ---  | --- |
| Bool | false |
| numbers | 0 |
| String | empty string |
| Option | None |
| ArrayList, HashSet, Array | new empty collection |
| HashMap | new empty map |

`ReturnsDefaults` mode affects the following members:

* Member functions returning one of the supported types.
* Getters of properties and fields of the supported types.

### SyntheticFields mode

`SyntheticFields` mode allows to simplify manual setup of `SyntheticField` objects described in [stubbing properties and fields](#stubbing-properties-and-fields) section.

`SyntheticFields` will create hidden fields managed by mock framework for all properties and fields of the corresponding type. However these fields can only be read after they were assigned some value. This is only useful for **mutable** properties and fields.

```cangjie
let foo = mock<Foo>(SyntheticFields)
// can simply assign a value to a mutable property
foo.bar = "Hello"
@Assert(foo.bar, "Hello")
```

Changes made to these hidden synthetic fields are only visible inside a corresponding test case.

When both `SyntheticFields` and `ReturnsDefaults` are enabled, assigned values take precedence over default values. However default values can be used whenever the field or property was not yet assigned any value.

```cangjie
let foo = mock<Foo>(ReturnsDefaults, SyntheticFields)
@Assert(foo.bar, "")
foo.bar = "Hello"
@Assert(foo.bar, "Hello")
```
