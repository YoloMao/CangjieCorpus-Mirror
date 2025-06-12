# Getting started with mock framework

**Mock framework** is a part of unittest framework for Cangjie. It provides an API to create and configure **mock objects** - skeleton objects that have the same API as the real ones. Mocking is testing technique that allows to isolate the code being tested and replacing external dependencies with mock objects.

This document outlines how to start using mock framework in your tests and explains the core APIs required to use mocks in your tests.

## Overview

**Mock framework** provides the following features:

* Creating mock and spy objects: no need to modify your production code for testing purposes
* Concise configuration API: configure behaviour of mock/spy objects
* Part of the unittest framework: seemless integration with the rest of unittest framework features and readable error output
* Automatic verification of configured behaviour: no boilerplate for most common cases
* [Verification API](./mock_framework_verification_en.md#mock-framework-verification-api) to test complex interactions between parts of the system

Usecases include:

* Simplify test setup and code
* Test exceptional scenarios
* Improve test performance by replacing *expensive* dependency with lightweight mocks
* Use verification to test complex scenarios i.e. order and/or number of certain invocations

## Using mock framework

Mock framework itself is a part of **unittest** in Cangjie standard library. To use mock framework import `unittest.mock.*` and `unittest.mock.mockmacro.*` to your test files.

If you are using **cjpm** tool, it will enable mock framework automatically. A simple `cjpm test` command will just work.

If you want to use **cjc** directly, see [this section](#using-cjc).

## Example

Typically test case using mocks consists of the following parts:

* Create mock/spy objects using [mock constuctors](#creating-mock-objects)
* Set up mock behaviour using [configuration API](#configuration-api)
* Use mocks as dependencies for code under test
* Optionally, use Verification API to verify interaction between the code under test and mock/spy objects

Let's look at an example. Say we have a simple API:

```cangjie
public interface Repository {
    func requestData(id: UInt64, timeoutMs: Int): String
}

public class Controller {
    public Controller(
        private let repo: Repository
    ) {}

    public func findData(id: UInt64): ?String {
        try {
            return repo.requestData(id, 100)
        }
        catch (e: TimeoutException) {
            return None
        }
    }
}

public class TimeoutException <: Exception {}
```

For the purpose of this example, assume that actual `Repository` implementation is not easy to create: it might have complex dependencies, its implementation could be in some other package or it could simply make the test too slow. Mock framework allows to test `Controller` without creating its dependencies.

Let's test `findData` method.

```cangjie
// importing mock framework packages
import std.unittest.mock.*
import std.unittest.mock.mockmacro.*

@Test
class ControllerTest {
    let testId: UInt64 = 100
    let testResponse = "foo"

    @TestCase
    func testFindSuccessfully() {
        // create mock instead of a real Repository
        let repository = mock<Repository>()

        // configure behaviour of testData using @On macro
        @On(repository.requestData(testId, _)).returns(testResponse)

        // create real Controller, we want to test the real implementation
        let controller = Controller(repository)

        // run test code
        let result = controller.findData(testId)

        // run assertion on the result
        @Assert(result == Some(testResponse))
    }

    @TestCase
    func testTimeout() {
        let repository = mock<Repository>()

        // configure getData to throw exception instead
        @On(repository.requestData(testId, _)).throws(TimeoutException())

        let controller = Controller(repository)

        // test behaviour when underlying implementation actually throws exception
        let result = controller.findData(testId)

        // run assertion on the result
        @Assert(result == None)
    }
}
```

## Creating mock objects

**Mock constructors** allow to create two different types of objects: **mocks** and **spies**. They are created by calling `mock<T>` and `spy<T>` functions where `T` is the class or interface being mocked.

```cangjie
public func mock<T>(): T
public func spy<T>(objectToSpyOn: T): T
```

<!-- link mock/spy constructors -->

**Mocks** are pure skeleton objects with no behaviour attached to any of their members by default.
**Spies** are a special kind of mock objects that wrap an existing instance of certain class or interface. Spies delegate their member calls to the underlying object by default.
Spies and mocks are very similar in other aspects.

Only **classes** (including final and sealed classes) and **interfaces** can be mocked.

See other sections to learn [how to use mock/spy objects](#using-spy-and-mock-objects).

## Configuration API

**Configuration API** is the central part of the framework. It allows to define (or redefine in case of spies) behaviour for members of mock/spy objects.
The entry point to **Configuration API** is `@On` macro invocation.

```cangjie
@On(storage.getComments(testId)).returns(testComments)
```

This example should be read as follows "if mock object `storage` *receives* an invocation of `getComments` method and the argument is `testId`, it returns `testComment`".

A single behaviour specification such as above is called a **stub**. Stubs must be defined inside test case body.

Only instance members (including final members) of classes and interfaces **can** be stubbed. The following entities **cannot** be stubbed:

* static members
* members in extends
* top level functions including foreign functions

We say that `@On` macro invocation defines a **stub signature**. While the full **stub declaration** consists of the following parts:

1. **Stub signature** described inside `@On` macro invocation.
2. [Action](#actions-api) that describes the behaviour of the stub.
3. Optionally, a cardinality specifier that sets an [expectation](#expectations).
4. Optionally, a [continuation](#stub-chains).

Mock framework will intercept invocations that match the stub signature and perform actions specified in stub declaration. Only members of spy and mock objects can be intercepted.

### Stub signature

**Stub signature** defines a set of conditions that match a particular subset of invocations. It consists of the following parts:

* A reference to mock/spy object. It must be a single identifier.
* An invocation of some member.
* All of the arguments of that invocation must be of special form - [argument matcher](#argument-matchers).

Signature can match the following entities:

* Methods
* Property getters
* Property setters
* Field read operations
* Field write operations

Stub signature matches an invocation whenever a corresponding member is invoked on corresponding mock/spy object and all arguments (if any) match the respective argument matchers.

Signatures for method stubs have the following structure: `<mock object name>.<method name>(<argument matcher>*)`.

```cangjie
@On(foo.method(0, 1))                 // method invocation with arguments 0 and 1
@On(foo.method(param1: 0, param2: 1)) // method invocation with named arguments
```

When stubbing property getters/setters or field read/write operations use:  `<mock object name>.<property name>` or `<mock object name>.<property name> = <argument matcher>`.

```cangjie
@On(foo.prop)      // property getter
@On(foo.prop = 3)  // property setter with argument 3
```

When stubbing operator functions, the receiver of the operator must be a single reference to a mock/spy object while the arguments of the operator must be argument matchers.

```cangjie
@On(foo + 3)  // 'operator func +' with argument 3
@On(foo[0])   // 'operator func []' with argument 0
```

### Argument matchers

Each stub signature must contain **argument matchers** for all the arguments. A single argument matcher defines a condition that accepts a certain subset of all possible argument values.
Each matcher is defined by an invocation of a static method of `Matchers` class.
For example Matchers.any() is a valid matcher that allows any argument. For convenience you can omit the `Matcher.` prefix and some other syntax sugar is provided.

Predefined matchers include:

| matcher | description | syntax sugar |
| ---               | ---         | ---          |
| any() | any argument | `_` symbol |
| `eq(value: Equatable)` | structural equality to **value** | single `identifier` allowed, some constant literals are allowed |
| `same(reference: Object)` | referential equality to **reference** | single `identifier` allowed |
| `ofType<T>()` | only values of type **T** | |
| `argThat(predicate: (T) -> Bool)` | only matches values of type **T** filtered by **predicate** | |
| none()   | matches **None** value of an option type |  |

If a single identifier is used as an argument matcher, structural equality will be preferred.

If a method has a default argument and it is not specified explicitly then any() matcher will be used.

Example:

```cangjie
let p = mock<Printer>()         // suppose print takes a single argument of type ToString

@On(p.print(_))                 // '_' special character can be used instead of any()

@On(p.print(eq("foo")))         // only match "foo" argument
@On(p.print("foo"))             // omitting explicit matcher is allowed for constant strings

let predefined = "foo"          // a single identifier can be passed instead of argument matcher
@On(p.print(predefined))        // structural equality is used to match if the type is equatable

@On(p.print(ofType<Bar>()))     // only match arguments of type Bar

// for more complex matchers, the following pattern is encouraged
let hasQuestionMark = { arg: String => arg.contains("?") }
@On(p.print(argThat(hasQuestionMark)))  // only match strings that contain question mark
```

Choosing correct function overloads depends on Cangjie type inference mechanism. Use **ofType** to resolve any compile time issues with typing.
<!-- TODO: move that to advanced and add stubbing overloaded section -->

Important rule: whenever a function invocation is used as an **argument matcher**, it will be treated as a call to a matcher and never literally.

```cangjie
@On(foo.bar(calculateArgument())) // incorrect, calculateArgument() is not a matcher

let expectedArgument = calculateArgument()
@On(foo.bar(expectedArgument))    // correct, as long as 'expectedArgument' is equatable and/or a reference type
```

### Actions API

Mock framework provides API that allows to specify stub actions. Stubbed member will behave based on the specified action whenever the specified stub is triggered. The stub is triggered if an invocation matches the signature specified by the corresponding `@On` macro invocation.

Each stub **must** specify an action.
`@On` macro invocation returns a subtype of `ActionSelector` that defines available actions. List of actions depends on the exact entity being stubbed.

<!-- link actions docs -->

#### Common

Actions available for all stubs.

* `throws(exception: Exception)` - throw **exception**.
* `throws(exceptionFactory: () -> Exception)` - **exceptionFactory** is invoked whenever the stub is triggered to construct a new exception to be thrown.
* `fails()` - the test will fail if the stub is triggered.

Note: **throws** is used to test behaviour of the system whenever stubbed member throws an exception. **fails** is used to test that stubbed member is not invoked.

```cangjie
@On(service.request()).throws(TimeoutException())
```

#### Methods and property/field getters

**R** denotes return type of the corresponding member.

* `returns()` - do nothing and return (), only available if 'R' is Unit.
* `returns(value: R)` - return **value**.
* `returns(valueFactory: () -> R)` - **valueFactory** is invoked whenever the stub triggered to construct a new exception to be returned.
* `returnsConsecutively(values: Array<R>)`, `returnsConsecutively(values: ArrayList<R>)` - return next element in **values** whenever the stub is triggered.

```cangjie
@On(foo.bar()).returns(2) // always return 0
@On(foo.bar()).returnsConsecutively(1, 2, 3) // return 1, then 2, then 3
```

#### Property/field setters

* `doesNothing()` - ignore the call and do nothing. Similar to `returns()` for functions returning Unit.

See more details [here](./mock_framework_advanced.md#stubbing-properties-and-fields).

#### Spy actions

For spies additional actions are available that delegate to spied on instance.

* `callsOriginal()` - calls original method.
* `getsOriginal()`  - calls original property getter or gets value of the field in the original instance.
* `setsOriginal()`  - calls original property setter or sets value of the field in the original instance.

### Expectations

Whenever a stub is defined, some expectations are attached to it implicitly or explicitly. Stub **may** define expected cardinality. Action selectors (except **fails** and **returnsConcesecutively**) return an instance of **CardinalitySelector** that allows setting up custom expectations using **cardinality specifier** functions.

**CardinalitySelector** defines the following functions:

* `once()`
* `atLeastOnce()`
* `anyTimes()`
* `times(expectedTimes: Int64)`
* `times(min!: Int64, max!: Int64)`
* `atLeastTimes(minTimesExpected: Int64)`

`anyTimes` specifier lifts expectations i.e. the test will not fail if the stub is never triggered. All other specifiers imply lower and upper limits on number of invocations of a particular stub inside test code. Whenever a stub is triggered more times than expected, then the test will fail immediately. Lower limit will be checked after the test code finished executing.

Example:

```cangjie
// example_test.cj
@Test
func tooFewInvocations() {
    let foo = mock<Foo>()
    @On(foo.bar()).returns().times(2)
    foo.bar()
}
```

Output:

```text
Expectation failed
    Too few invocations for stub foo.bar() declared at example_test.cj:9.
        Required: exactly 2 times
        Actual: 1
        Invocations handled by this stub occured at:
            example_test.cj:6
```

If no custom expectations are set up, mock framework will use default expectations:

| Action | default expected cardinality | custom cardinality allowed |
| ----   |  ---                |  ---                      |
| fails | should not be invoked | No                       |
| returns | atLeastOnce        | Yes                       |
| returnsConsecutively | times(values.size)        | No           |
| throws | atLeastOnce        | Yes                        |
| doesNothing | atLeastOnce        | Yes                   |
| (calls/gets/sets)Original | atLeastOnce        | Yes     |

### Stub chains

**returnsConsecutively** action, **once** and **times(n)** cardinality specifiers return an instance of **Continuation**. As the name implies **Continuation** allows to continue the chain. More precisely it allows to specify an action that will occur whenever the previous action is completed fully.

<!-- link Continuation -->

The **Continuation** itself only provides a single function `then()` that returns a new **ActionSelector**. For each action in the chain the same rules apply. If `then()` was invoked, a new action **must** be specified.

Total expectation is the sum of expectations of all parts of the chain. If a complex chain is specified in the test, then all parts of the chain are expected to be triggered.

```cangjie
@On(foo.bar()).returnsConsecutively(1, 2, 3, 4)
// same as
@On(foo.bar()).returnsConsecutively(1, 2).then().returnsConsecutively(3, 4)
```

```cangjie
// this specifies a stub that must be called NUM_OF_RETRIES times in total
@On(service.request()).throws(TimeoutException()).times(NUM_OF_RETRIES - 1). // request will timeout several times first
    then().returns(response).once() // after the first successful response more requests should not be sent
```

## Using spy and mock objects

**Spies** and **mocks** are similar in terms of configuration. However a spy requires an existing instance to spy on.

Main distinction is the following: whenever a member invocation does not trigger any stub, spy object will invoke the original implementation on the underlying instance, mock object will throw a runtime error (and the test will fail).

Mocks allow to test APIs without creating real dependencies and just configuring whatever behaviour is required for a particular test scenario.

Spies allow to override observable behaviour of a real instance. Only invocations that go through spy object reference will be intercepted. References to original spied on instance will not be affected by the creation of a spy. Spy calling its own methods will not be intercepted.

```cangjie
let serviceSpy = spy(service)
// emulate timeout and then keep using the real implementation
@On(serviceSpy.request()).throws(TimeoutException()).once().then().callsOriginal()
// code under test has to use 'serviceSpy' reference
```

## Mocking dependencies

Interfaces can always be mocked. To mock a class from another package the class itself and its superclasses have to be compiled in a special way.
In particular that means you can only mock interfaces from precompiled libraries (such as **stdlib**), but not classes.

### Using cjc

For **cjc** mocking is controlled via `--mock` flag.
If you want to mock classes from a particular package `p` add `--mock=on` flag to cjc invocation.
Note that you have to add this flag when compiling packages that depend on `p` as well.

To use mocks in tests themselves (`cjc --test`) no extra flags are required.

### Using cjpm

**cjpm** will detect mock usages automatically and generate correct **cjc** invocations. This enables mocking classes from any package that is compiled from the source.

To have more fine-grained control over which packages should support mocking use cjpm configuration files.

<!-- Add section about default mock behaviour when it is ready. -->

<!-- Add references to other docs when it is possible. -->
