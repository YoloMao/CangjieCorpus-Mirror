## struct Array

Arrays have fixed length and can contain elements of any particular type `T`. Arrays with
element type `T` has type `Array<T>`. If arrays with dynamic length are needed, use `ArrayList`
(and import `std.collection.*`) instead.

### Initialization

Ways to initialize an `Array` include:

```
let a = Array<Int64>([1, 2, 3])   // Initialize using a concrete list
let a = Array<Int64>(3, item: 0)   // Length 3 and all elements are 0
let b = Array<Int64>(3, {i => i + 1})   // Initialize using lambda function, result is [1, 2, 3]
```

### Size

To obtain the length of an `Array`, use syntax of the form `arr.size`. Note `size` is a
property, so no parenthesis is needed afterwards.

### Comparing two arrays for equality

Two compare two arrays for equality, use `a == b`. Note `a.equals(b)` is not valid.

### Adding elements

To add an element `i` to the end of an array `arr`, use `arr.append(i)`.

### Slice of an `Array`

The slice function on `Array` has the following signature:

```
public func slice(start: Int64, len: Int64): Array<T>
```

Note carefully that the second argument is the *length* of the slice, rather than the ending
position. This is *different* form the case of `slice` in `ArrayList`, which takes a range
as argument.

### Iteration

To iterate over elements of an array, use:

```
for (element in arr) {
    ...
}
```

Note there is no pattern matching before `in`. If the elements of an array are tuples,
access entries of the tuple individually, e.g.:

```
var a = Array<(Int64, Int64)>([(2, 3), (3, 4)])
for (pair in a) {
    println("(${pair[0]}, {pair[1]})")
}
```

### Reversing an `Array`

To reverse an array in-place, call `reverse` method on the array, Note this function
modifies the input array and returns `Unit`. To obtain a new array that is the reverse
of an old array, first copy the old array and then call `reverse`. The following illustrates
the usage:

```
let a = [1, 1, 2, 3, 3]
let b = Array(a)  // make a copy of a
b.reverse()
println(a)   // [1, 1, 2, 3, 3]
println(b)   // [3, 3, 2, 1, 1]
```

As an application, the following checks whether the input string `s` is a palindrome:


```
func isPalindrome(s: String): Bool {
    let arr = s.toRuneArray()
    let arr2 = Array(arr)
    return arr == arr2
}

main() {
    println(isPalindrome("aba"))  // true
    println(isPalindrome("hello"))  // false
}
```