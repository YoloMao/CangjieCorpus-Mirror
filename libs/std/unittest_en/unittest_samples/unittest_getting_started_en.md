# Overview

Unittest library serves as the foundation for writing unit tests in Cangjie projects.
It provides basic facilities for writing, running and debugging tests, as well as several advanced features for more experienced users.
Cangjie unit tests can be used from both cjc compiler (standalone compilation mode) and cjpm package manager (cjpm mode).

## Getting started

Let's write a simple Cangjie function:

```cangjie
package example

func add(left: Int64, right: Int64) {
    return left + right
}
```

Let's save this function in a file called `add.cj`.
Now let's write a test for it.

```cangjie
package example

@Test
func addTest() {
    @Expect(add(2, 3), 5)
}
```

This tests is built from the following components:

- `@Test` macro put on the `addTest` function signifies that this function is now a test;
- `@Expect` macro is an **assertion** --- it checks that the two parameters provided to it are equal. In this particular case, the parameters are the result of the `add` function `add(2, 3)` and the expected value, `5`.

Let's save this test in a file called `add_test.cj` and try to run it together with the code function in `add.cj`:

```bash
cjc add.cj add_test.cj --test -o add_test
./add_test
```

If everything is done correctly, we get an output similar to the following:

```
-------------------------------------------------------------------------------------------------
TP: default, time elapsed: 59363 ns, Result:
    TCS: TestCase_addTest, time elapsed: 32231 ns, RESULT:
    [ PASSED ] CASE: addTest (28473 ns)
    Summary: TOTAL: 1
    PASSED: 1, SKIPPED: 0, ERROR: 0
    FAILED: 0
--------------------------------------------------------------------------------------------------
```

Congratulations! We've built and run our first test.
Let's talk about the `cjc` command we used to build the test in detail.

```
    here we have our code file that we want to test
    ↓
cjc add.cj add_test.cj --test -o add_test
           ↑           ↑
           |           --test signifies that the resulting binary is built in test mode
           here we have our test file
```

Note, however, that for more complicated projects running the `cjc` compiler directly may not be the best option.
For larger projects with big structure you should probably use the `cjpm` package manager.
So let's try to introduce tests to a `cjpm` project instead.

Let's create a simple `cjpm` project with a single package called `example`.
The file structure of this project may look like this (assuming we copied over the files from the `cjc` example):

```
- src
  |
  +- example
     |
     +- add.cj
     +- add_test.cj
```

As our original files already specified that they belong to the `example` package, we can now initialize a `cjpm` project by simply running:

```bash
cjpm init example example
```

`cjpm` package manager has built-in support for running unit tests, so everything we need to do now is just run:

```bash
cjpm test
```

This command runs all the tests in all the packages of the project, producing a unified output similar to the following:

```
--------------------------------------------------------------------------------------------------
TP: example/example, time elapsed: 60989 ns, Result:
    TCS: TestCase_addTest, time elapsed: 32804 ns, RESULT:
    [ PASSED ] CASE: addTest (29195 ns)
    Summary: TOTAL: 1
    PASSED: 1, SKIPPED: 0, ERROR: 0
    FAILED: 0
--------------------------------------------------------------------------------------------------
```

Note that we don't need to specify `--test` or any other special options.
By default, `cjpm` uses the names of the files in the project to decide whether the file should be compiled in test mode or normal mode.
In our example package, `add_test.cj` is a test file because its name ends in `_test.cj`.
Such files will not be included in the build of the binary or library during normal build process.

While the API of the unit test framework resides in the `unittest` package of the `std` module and the macros can be found in the `unittest.testmacro` package of the `std` module, they do not need to be explicitly imported in test files.

To get more information about the basic concepts of unittest framework, please refer to [unit test basics](./unittest_basics_en.md)
