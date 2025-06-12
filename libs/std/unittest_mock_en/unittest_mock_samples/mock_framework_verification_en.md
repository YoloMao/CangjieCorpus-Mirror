# Mock framework Verification API

Verification API is a part of mock framework. It provides the following capabilites:

* Verifying certain calls were made
* Verifying the number invocations for particular calls
* Verifying that certain calls were made with specific arguments
* Verifying that calls were made in a certain order

Verification runs assertion by checking invocation log built during execution of the test. Invocation log is a listing that contains all the calls made on **mock** and **spy** objects accessible in the test. Only the calls that were made on mock/spy object can be verified.

`Verify` class is an entry point to Verification API.

<!-- link Verify class doc -->

**@Called** macro is used to build assertions about the code.

**@Called** macro invocation constructs a **verify statement**, a single assertion about the code that will be checked against the invocation log.
**Verify** class itself is a collection of static methods. Methods such as `that`, `ordered` and `unordered` construct **verification blocks**.

## Example

```cangjie
let foo = mock<Foo>()
// configure foo
@On(foo.bar()).returns()
foo.bar()
Verify.that(@Called(foo.bar())) // verifies that bar was called at least once
```

## Verify statements and `@Called` macro

Verify statements are represented by `VerifyStatement` class. Instances of `VerifyStatement` are created using `@Called` macro.

`@Called` macro invocation accepts a [stub signature](./mock_framework_basics_en.md#stub-signature). It is similar to `@On` macro and the same rules for [argument matchers](./mock_framework_basics_en.md#argument-matchers) apply.

Example:

```cangjie
@Called(foo.bar(1, _)) // verify statement that matches calls of method bar where first argument is '1'
@Called(foo.baz)       // verify statement that matches getter invocations of property baz
```

class `VerifyStatement` provides API similar to cardinality specifiers available during stub configuration.

The cardinality functions are:

* `once()`
* `atLeastOnce()`
* `times(expectedTimes: Int64)`
* `times(min!: Int64, max!: Int64)`
* `atLeastTimes(minTimesExpected: Int64)`
* `never()`

Invocations of these functions return the same `VerifyStatement` instance. Cardinality cannot be reset for the same statement and must be set before the statement is passed into a verification block builder functions. If cardinality is not set explicitly, default cardinality will be used instead.

```cangjie
Verify.that(@Called(foo.bar()).atLeastOnce())
Verify.that(@Called(foo.bar()).once())
```

## Verification blocks

Verification blocks generally contain one or more verification statements. Statements in a block are checked together composing a more complex assertion.

Verification happens immediately when the verification block is invoked i.e. any calls that happened after are not taken into account.
Verification blocks do not change the state of the invocation log: each invocation in the log can be checked by any number of blocks (zero, one or more). Different blocks are checked independently, consecutive blocks do not depend on each other. Unless some calls happened between the blocks or the invocation log was cleared manually, the order in which verification blocks are invoked does not matter.

Verification statements do not perform any kind of verification by themselves. They must be passed into a verification block for verification to take place.

A single verification block will only check invocations on mock/spy objects that are mentioned in verification statements inside the block. Calls on other objects will be ignored by this particular block.

Class `Verify` contains several static methods that build verification blocks. **ordered** verification block is used to check the exact order of invocations. **unordered** verification block only verifies the number of invocations.

### Ordered

To check exact order of invocations on one or more objects use `ordered` verification block builder.

The `ordered` static function acceepts an array of verify statements.

```cangjie
for (i in 0..4) {
    foo.bar(i % 2)
}

Verify.ordered(
    @Called(foo.bar(0)),
    @Called(foo.bar(1)),
    @Called(foo.bar(0)),
    @Called(foo.bar(1))
)
```

Checking order of invocations on several objects is allowed.

```cangjie
for (i in 0..4) {
    if (i % 2 == 0) {
        fooEven.bar(i)
    }
    else {
        forOdd.bar(i)
    }
}

Verify.ordered(
    @Called(fooEven.bar(0)),
    @Called(fooOdd.bar(1)),
    @Called(fooEven.bar(2)),
    @Called(fooOdd.bar(3)),
)
```

The default cardinality specifier for **ordered** verification is `once()`. Use other cardinality specifiers if necessary.

```cangjie
for (i in 0..4) {
    foo1.bar(i)
}

for (i in 0..4) {
    foo2.bar(i)
}

Verify.ordered(
    @Called(foo1.bar(_).times(4)),
    @Called(foo2.bar(_).times(4))
)
```

For **ordered** verification all calls on mock/spy objects (that are mentioned in the block) must be listed. Any unlisted calls will cause verification failure.

```cangjie
foo.bar(0)
foo.bar(10)
foo.bar(1000)

Verify.ordered(
    @Called(foo.bar(0)),
    @Called(foo.bar(10))
)
```

Output:

```text
Verification failed
    The following invocations were not matched by any statement:
        foo.bar(...) at example_test.cj:6
```

### Unordered

Unordered verification only checks the number of invocations for its verify statements.

For **unordered** verification `atLeastOnce()` cardinality is assumed unless specified explicitly i.e. it would only check that call was made at least once.

```cangjie
for (i in 0..4) {
    foo.bar(i % 2)
}

// verifies that bar was called with argument 0 and argument 1 at least once
Verify.unordered(
    @Called(foo.bar(0)),
    @Called(foo.bar(1))
)

// verifies that bar was called with argument 0 and argument 1 exactly two times
Verify.unordered(
    @Called(foo.bar(0)).times(2),
    @Called(foo.bar(1)).times(2)
)

// verifies that bar was called exactly 4 times in total
Verify.unordered(
    @Called(foo.bar(_)).times(4)
)
```

**Unordered** verification allows to specify two different modes **Partial** and **Exhaustive**.

**Exhaustive** which is the default requires to list all invocations for mock/spy objects mentioned by verify statements.
**Partial** allows to only list **some** invocations.

```cangjie
for (i in 0..4) {
    foo.bar(i)
}

// fails, two invocations of foo.bar() were not listed in the block
Verify.unordered(
    @Called(foo.bar(0)).once(),
    @Called(foo.bar(1)).once()
)

// okay, ignore invocations that are not interesting
Verify.unordered(Partial,
    @Called(foo.bar(0)).once(),
    @Called(foo.bar(1)).once()
)
```

### Building verification blocks dynamically

`ordered` and `unordered` functions provide overloads that accept a lambda. Use `checkThat(statement: VerifyStatement)` function to add statements dynamically.

Example:

```cangjie
let totalTimes = 40
for (i in 0..totalTimes) {
    foo.bar(i % 2)
}

Verify.ordered { v =>
    for (j in 0..totalTimes) {
        v.checkThat(@Called(foo.bar(eq(j % 2))))
    }
}
```

## Other API

Additionally `Verify` class provides the following utilities.

* that(statement: VerifyStatement) is an alias for `Verify.unordered(Paritial, statement)` - checks a single statement and does not require to list all calls for corresponding mock/spy object.
* `noInteractions(mocks: Array<Object>)` allows to check that no calls were made on specified mock/spy objects.
* `clearInvocationLog()` resets the log to an empty state. That affects all the verification blocks that follow. This does not affect stub expectations.

Example:

```cangjie
foo.bar()
Verify.that(@Called(foo.bar())) // okay
Verify.noInteractions(foo)      // fails, invocation foo.bar() is in the log
Verify.clearInvocationLog()     // clears log
Verify.noInteractions(foo)      // all interactions with foo were cleared from the log
Verify.that(@Called(foo.bar())) // now fails
```

## `Verify` class API

```cangjie
public static func that(statement: VerifyStatement): Unit

public static func unordered(
    exhaustive: Exhaustiveness,
    collectStatements: (UnorderedVerifier) -> Unit
): Unit

public static func unordered(
    collectStatements: (UnorderedVerifier) -> Unit
): Unit

public static func unordered(statements: Array<VerifyStatement>): Unit

public static func unordered(
    exhaustive: Exhaustiveness,
    statements: Array<VerifyStatement>
): Unit

public static func ordered(
    collectStatements: (OrderedVerifier) -> Unit
): Unit

public static func ordered(statements: Array<VerifyStatement>): Unit

public static func clearInvocationLog(): Unit

public static func noInteractions(mocks: Array<Object>): Unit
```

## Verification errors

Whenever verification fails `VerificationFailedException` will be thrown and report will be presented by mock framework. You should not catch this exception.

The following failure types can be presented:

* **Too few invocations** or **too many invocations** - number of invocations does not match one of the statements in the block.
* **Unmatched statements** - there are statements in the block that were not matched by any invocations in the log.
* **Unmatched invocations** - there are invocations in the log that were not matched by any statement in the block.
* **Unexpected invocation** - **ordered** verification block expects a different invocation.
* **Unwanted interaction** - **noInteractions** detected an unexpected invocation.

There is another type of failure - **non disjoint statements** that does not necessarily signify an issue with the code under test itself. This type of failure is reported whenever an invocation was matched by several statements. Using statements with non-disjoint argument matchers in a single verification block can lead to this error. Ambigous matching between statements and invocations is not allowed.

## Examples and patterns

A common pattern to use verification API is verifying interaction between the code under test (be it a function, class or a whole package) and outside objects.
This would go as follows:

* Create **spy** objects
* Pass these spies to code under test
* Verify interactions between the code and the spies

### Verifying number of calls

```cangjie
func testDataCaching() {
    // create necessary spies or mocks
    let uncachedRepo = spy(Repository())
    let invalidationTracker = mock<InvalidationTracker>()
    @On(invalidationTracker.getTimestamp()).returns(0)

    // prepare data to test
    let cachedRepo = CachedRepistory(uncachedRepo, invalidationTracker)

    // run test code
    for (i in 0..10) {
        cachedRepo.get(TEST_ID)
    }

    // verify that underlying repo was only queried once and there were no other calls to uncached repo
    Verify.unordered(Exhaustive,
        @Called(uncachedRepo.get(TEST_ID)).once()
    )

    // clear log
    Verify.clearInvocationLog()

    // setup a different behaviour
    @On(invalidationTracker.getTimestamp()).returns(1)

    for (i in 0..10) {
        cachedRepo.get(TEST_ID)
    }

    // only a single new call was made since last clear
    Verify.unordered(Exhaustive,
        @Called(uncachedRepo.get(TEST_ID)).once()
    )
}
```

### Verifying calls with specific arguments

```cangjie
func testDrawingTriangle() {
    // create necessary spies or mocks
    let canvas = spy(Canvas())

    // run the code
    canvas.draw(Triangle())

    // test that triangle consists of 3 lines and 3 dots

    // use 'that' blocks
    Verify.that(
        @Called(canvas.draw(ofType<Dot>())).times(3)
    )
    Verify.that(
        @Called(canvas.draw(ofType<Line>())).times(3)
    )

    // alternatively use partial unordered vefication block
    Verify.unordered(Partial, // we don't know the exact order in which lines and dots are actually drawn
        @Called(canvas.draw(ofType<Dot>())).times(3),
        @Called(canvas.draw(ofType<Line>())).times(3)
    )

    // when using exhaustive block all calls must be listed
    Verify.unordered(Exhaustive,
        @Called(canvas.draw(ofType<Triangle>())).once(),
        @Called(canvas.draw(ofType<Dot>())).times(3),
        @Called(canvas.draw(ofType<Line>())).times(3)
    )

    // verify that we never drew a square
    Verify.that(
        @Called(canvas.draw(ofType<Square>)).never()
    )

    // if we want to distinguish arguments by a more complex condition
    // the following pattern can be used
    let isDot = { f: Figure =>
        f is Dot // more complex logic can go here
    }
    Verify.that(
        @Called(canvas.draw(argThat(isDot))).times(3)
    )

    // Note that statements that belong to the same block must unambiguosly match only one invocation
    // the following is not correct, some of the invocations match both statements
    Verify.unordered(
        @Called(canvas.draw(_)).times(7),
        @Called(canvas.draw(ofType<Dot>())).times(3)
    )
}
```

### Verifying order of invocations

```cangjie
func testBuildFlight() {
    let plane = spy(Plane())

    FlightBuilder(plane).planFlight(Shenzhen, Shanghai, Beijing).execute()

    Verify.ordered(
        @Called(plane.takeOffAt(Shenzhen)),
        @Called(plane.landAt(Shanghai)),
        @Called(plane.takeOffAt(Shanghai)),
        @Called(plane.landAt(Beijing))
    )
}
```

## Expectations vs Verification API

Some of the assertions about the test code can be covered by both **expectations** set during stub configuration and Verification API. There is no preferred approach to such cases. Choose the approach that better reflects the intention of the test.

However in simple cases it is advised to avoid repeating configuration steps in verification blocks.

```cangjie
let foo = mock<Foo>()
@On(foo.bar(_)).returns() // the test will fail if this stub is never used

foo.bar(1)
foo.bar(2)

Verify.that(
    // unnecessary, verified automatically
    @Called(foo.bar(_)).atLeastOnce()
)

// however, we could check number of invocation and concrete arguments
Verify.unordered(
    @Called(foo.bar(1)).once(),
    @Called(foo.bar(2)).once()
)
```

Example above can be rewritten using expectations:

```cangjie
let foo = mock<Foo>()
@On(foo.bar(1)).returns().once() // expected to only be called once with argument `1`
@On(foo.bar(2)).returns().once() // expected to only be called once with argument `2`

foo.bar(1)
foo.bar(2)

// the test will fail if any of the stubs were never triggered
```
