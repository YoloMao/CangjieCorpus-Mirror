# Parameterized tests

## Getting started with parameterized tests

Cangjie unittest framework supports parameterized tests in the form of the *data DSL* that allows tests to have input parameters automatically inserted by the framework.

Let's consider a more complicated code example, a function that sorts an array:

```cangjie
package example

func sort(array: Array<Int64>): Unit {
    for (i in 0..array.size) {
        var minIndex = i
        for (j in i..array.size) {
            if (array[j] < array[minIndex]) {
                minIndex = j
            }
        }
        (array[i], array[minIndex]) = (array[minIndex], array[i])
    }
}
```

While certainly not the best or the most efficient implementation of sorting, this function, however, may just work.
Let's test it.

```cangjie
package example

@Test
func testSort() {
    let arr = [45, 5, -1, 0, 1, 2]
    sort(arr)
    @Expect(arr, [-1, 0, 1, 2, 5, 45])
}
```

Good, this simple test works, but it only tests our functionality on a single input.
Let's try to test that our sorting function does not break if the array only contains equal elements.

```cangjie
@Test
func testAllEqual() {
    let arr = [0, 0, 0, 0]
    let expected = [0, 0, 0, 0]
    sort(arr)
    @Expect(expected, arr)
}
```

This is all good, but we cannot really be sure that it works on arrays of all sizes.
Let's make a test that is parameterized over the size of the array.

```cangjie
@Test[size in [0, 1, 50, 100, 1000]]
func testAllEqual(size: Int64) {
    let arr = Array(size, item: 0)
    let expected = Array(size, item: 0)
    sort(arr)
    @Expect(expected, arr)
}
```

Congratulations, we've just created our first parameterized test.
This is the simplest kind of a parameterized test: a **value-driven test** that lists the values on which the test should be run directly in the code.
Parameterized tests are not limited to just one parameter.
Let's specify our sorting function with not only size, but the element we're going to test on.

```cangjie
@Test[
    size in [0, 1, 50, 100, 1000],
    item in (-1..20)
]
func testAllEqual(size: Int64, item: Int64) {
    let arr = Array(size, item: item)
    let expected = Array(size, item: item)
    sort(arr)
    @Expect(expected, arr)
}
```

Note that instead of an array, we use range of values `-1..20` to provide our items.
What will happen if we run this test?
For each value of `size` and each value of `item`, the combination of corresponding values will be tested and reported.
This means that one needs to be careful when providing too many parameters to their test functions, as the number of combinations may become very big, making the tests slow.
In this particular case, we have 5 different sizes and 21 different items, making the number of combinations equal to 21 × 5 = 105.

Note that value-driven tests are not limited to integers or builtin types.
You can use it with any Cangjie type.
Consider the following test:

```cangjie
@Test[
    array in [
        [],
        [1, 2, 3],
        [1, 2, 3, 4, 5],
        [5, 4, 3, 2, 1],
        [-1, 0],
        [-20]
    ]
]
func testDifferentArrays(array: Array<Int64>) {
    // test the array is sorted
    for (i in 0..(array.size - 1)) {
        @Expect(array[i] <= array[i + 1])
    }
}
```

Here we just provide the data for test directly in the form of a parameter.

Of course, listing a number of arrays on which to test our code may also seem too cubersome.
Sometimes for such generic functions it's easier to just generated the data randomly, if you are feeling lucky today.
This brings us to a more advanced kind of parameterized tests: **randomized tests**.
Randomized tests are created by replacing the array or range of a value-driven test with the call to a small function called `unittest.random<T>()`:

```cangjie
@Test[
    array in random()
]
func testRandomArrays(array: Array<Int64>) {
    // test the array is sorted
    for (i in 0..(array.size - 1)) {
        @Expect(array[i] <= array[i + 1])
    }
}
```

What this test does, essentially, is generating a big number (default is 200) of completely random data values and tests your code on them.
This random data is not entirely random though: it is biased towards border values like zeroes, max and min values of your particular type, empty collections, etc.

On a serious note, it is generally recommended to **mix** randomized tests with tests written by hand of the programmer, because in practice they are complement to each other, not a replacement.

To illustrate the work of a randomized test, let's set aside our sorting function for a moment and write the following non-sensical test:

```cangjie
@Test[
    array in random()
]
func testNonsense(array: Array<Int64>) {
    if (array.size < 2) { return }
    @Expect(array[0] <= array[1] + 500)
}
```

Running this (hopefully) produces an output similar to the following:

```
[ FAILED ] CASE: testNonsense (1159229 ns)
    REASON: After 4 generation steps and 200 reduction steps:
        array = [0, -453923686263, 0]
    with randomSeed = 1702373121372171563

    Expect Failed: `(array [ 0 ] <= array [ 1 ] + 500 == true)`
       left: false
      right: true
```

As you can see, we successfully failed the test with an array `[0, -453923686263, 0]`.
Let's run it again.

```
[ FAILED ] CASE: testNonsense (1904718 ns)
    REASON: After 5 generation steps and 200 reduction steps:
        array = [0, -1196768422]
    with randomSeed = 1702373320782980551

    Expect Failed: `(array [ 0 ] <= array [ 1 ] + 500 == true)`
       left: false
      right: true
```

Again, the test failed, but the values are all different.
Why is that so?
Because randomized tests are randomized by nature, they produce new random values each time.
This may be a good thing if you want to test your function on all kinds of different data, but for some tests, this means that they may run successfully in one run and fail at another run, which is not really convenient when sharing the results.
Randomized tests are a powerful tool, but the user must understand these drawbacks when using them.

But one may ask, how do I show results to other developers if they are different each time?
The answer to that is simple and lies in the output you get when running the test, this line:

```
with randomSeed = 1702373320782980551
```

provides you with a *random seed* that can be used as a configuration option in the test.
Let's rewrite our test as follows.

```cangjie
@Test[
    array in random()
]
@Configure[randomSeed: 1702373320782980551]
func testNonsense(array: Array<Int64>) {
    if (array.size < 2) { return }
    @Expect(array[0] <= array[1] + 500)
}
```

Let's run it.

```
[ FAILED ] CASE: testNonsense (1910109 ns)
    REASON: After 5 generation steps and 200 reduction steps:
        array = [0, -1196768422]
    with randomSeed = 1702373320782980551

    Expect Failed: `(array [ 0 ] <= array [ 1 ] + 500 == true)`
       left: false
      right: true
```

Notice that the values generated, the steps it took to generate the values and the random seed are exactly the same as in our last run.
This mechanism allows you to have randomized tests that are *reproducible* and you can indeed save them in your test suite and share them with other developers.
Alternatively, you can just take the data from the random test (in this case, the array values `[0, -1196768422]`) and write a new test using those values.

Let's have a quick look at other output produced by our failing test.

```
    REASON: After 5 generation steps and 200 reduction steps:
        array = [0, -1196768422]
    with randomSeed = 1702373320782980551
```

There are several important pieces of information in this output:

- The number of generation steps it took to fail the test: this is the amount of iterations the test was run before failing
- The number of reduction steps: for random tests, there is a mechanism called reduction of test data that tries to make the data *smaller* for your convenience and readability
- The actual data that fails the test: this lists all the parameters in order (in this case, there is only one parameter `array`) with their values that actually lead to test failure. The type of the parameters should implement the `ToString` interface, if not, a placeholder will be printed
- The random seed, as mentioned before, to reproduce this random test run

Some tests are trickier than others, so sometimes you may want to increase the amount of random generation or reduction your tests do.
This is controlled by two configuration options: `generationSteps` and `reductionSteps`.
One of the appealing factors of randomized testing is that it can be left running for a long time, checking millions of values if you provide it with a sufficient number of steps.

Default maximum value of both `generationSteps` and `reductionSteps` are 200 to not make the testing too time-consuming.
Note that this configuration parameters set up the *maximum* amount of steps the framework may take.
For example, for our non-sensical test above, it probably doesn't make much sense to set up this parameter to a big number because our previous runs show that it usually takes less than 10 steps to fail.

## Type-parameterized tests

While our sort implementation is fine sorting arrays of integers, it is just natural to allow it to sort anything.
Let's rewrite our `sort` function to be generic and allow sorting arbitrary types.
Note that we need the elements to be comparable for sorting to work properly.

```cangjie
package example

func sort<T>(array: Array<T>): Unit where T <: Comparable<T> {
    for (i in 0..array.size) {
        var minIndex = i
        for (j in i..array.size) {
            if (array[j] < array[minIndex]) {
                minIndex = j
            }
        }
        (array[i], array[minIndex]) = (array[minIndex], array[i])
    }
}
```

Okay, great. Note that all of our tests continue running properly because we made the sort function more general.
But does it really work on things different from integers?

Let's write a new test, but on something different, like strings, using our `testDifferentArrays` example:

```cangjie
@Test[
    array in [
        [],
        ["1","2","3"],
        ["1","2","3","4","5"],
        ["5","4","3","2","1"]
    ]
]
func testDifferentArraysString(array: Array<String>) {
    // test the array is sorted
    let sorted = array.clone()
    sort(sorted)
    for (i in 0..(sorted.size - 1)) {
        @Expect(sorted[i] <= sorted[i + 1])
    }
}
```

If we now run this test, we will find out that it works fine.
Note though that now we have two tests with two exact same bodies and assertions.
Wouldn't it be more convenient if tests for generic functions could also be generic?

Let's go back to our random testing example:

```cangjie
@Test[array in random()]
func testRandomArrays(array: Array<Int64>) {
    let sorted = array.clone()
    sort(sorted)
    for (i in 0..(sorted.size - 1)) {
        @Expect(sorted[i] <= sorted[i + 1])
    }
}
```

This test is very general, we can see that it doesn't need to have `Int64` as element type, but it could work with any type `T` such as:

- It can be compared: it needs to implement `Comparable<T>`
- The random generation can generate an instance of it: it needs to implement Arbitrary\<T>

Let's rewrite this test to a generic function:

```cangjie
@Test[array in random()]
func testRandomArrays<T>(array: Array<T>) where T <: Comparable<T> & Arbitrary<T> {
    let sorted = array.clone()
    sort(sorted)
    for (i in 0..(sorted.size - 1)) {
        @Expect(sorted[i] <= sorted[i + 1])
    }
}
```

Let's try to compile and run it, but now we have a problem:

```shell
An exception has occurred:
MacroException: Generic function testRandomArrays requires a @Types macro to set up generic arguments
```

Of course, to run a test on some types, we need to have these types first!
Let's set up our test so it runs on `Int64`, `Float64` and `String` using the new `@Types` macro:

```cangjie
@Test[array in random()]
@Types[T in <Int64, Float64, String>]
func testRandomArrays<T>(array: Array<T>) where T <: Comparable<T> & Arbitrary<T> {
    let sorted = array.clone()
    sort(sorted)
    for (i in 0..(sorted.size - 1)) {
        @Expect(sorted[i] <= sorted[i + 1])
    }
}
```

Now this test will compile and produce the following output:

```
    TCS: TestCase_testRandomArrays, time elapsed: 2491737752 ns, RESULT:
    [ PASSED ] CASE: testRandomArrays<Int64> (208846446 ns)
    [ PASSED ] CASE: testRandomArrays<Float64> (172845910 ns)
    [ PASSED ] CASE: testRandomArrays<String> (2110037787 ns)
```

Note that for each provided type, the test is run separately because the behaviour may be very different.
The `@Types` macro can be used on any parameterized test case, both in test functions and classes.

## Reusing, combining and mapping parameter strategies

Now lets consider `HashSet`. And we want to test its api. Lets start from `contains`.

```cangjie
@Test[data in random()]
func testHashSetContains(data: Array<Int64>) {
    let hashSet = HashSet(len)
    hashSet.putAll(data)

    for (element in data){
        @Assert(hashSet.contains(element))
    }
}
```

It works fine. Now lets try to test `remove`.

```cangjie
@Test[data in random()]
func testHashSetRemove(data: Array<Int64>) {
    let hashSet = HashSet(len)
    hashSet.putAll(data)

    for (element in data){
        @Assert(hashSet.remove(element))
    }
}
```

At first glance it should work fine. However very soon we will notice that it doesn't work correctly because our random generated array can contain duplicates which causes second remove call to fail. So what we want is to generate some array without duplicates.

```cangjie
var counter = 0
@OverflowWrapping
func generateUniqArray(len: Int64, start: Int64){
    let rng = Random(start)
    let step = Int64.Max / len
    counter = 0
    Array(len, { _ => 
        counter += rng.nextInt64()%step 
        counter
    } )
}

@Test[len in random(), start in random()]
func testHashSetRemove(len: Int64, start: Int64) {
    let data = generateUniqArray(len,start)
    let hashSet = HashSet(len)
    hashSet.putAll(data)

    for (element in data){
        @Assert(hashSet.remove(element))
    }
}
```

However even though we moved generation into a separate function it will still have quite a lot of duplication if we would like to reuse that between multiple different tests. Moreover we will have quite unclear separation between preparation code and test code. So to help with that our test framework provides convenience api in a form of `@Strategy` macro that allows us to combine and map existing strategies.

```cangjie
var counter = 0
@Strategy[len in random(), start in random()]
@OverflowWrapping
func generateUniqArray(len: Int64, start: Int64): Array<Int64>{
    let rng = Random(start)
    let step = Int64.Max / len
    counter = 0
    Array(len, { _ => 
        counter += rng.nextInt64()%step 
        counter
    } )
}
```

And now we can use that strategy whenever we need such input:

```cangjie
@Test[data in generateUniqArray]
func testHashSetRemove(data: Array<Int64>) {
    let hashSet = HashSet()
    hashSet.putAll(data)

    for (element in data){
        @Assert(hashSet.remove(element))
    }
}

@Test[data in generateUniqArray]
func testHashSetToArray(data: Array<Int64>) {
    let hashSet = HashSet()
    hashSet.putAll(data)

    let result = hashSet.toArray()
    result.sort()
    data.sort()
    @Assert(result == data)
}
```