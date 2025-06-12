## ArrayList

To use the ArrayList type, the collection package needs to be imported:

```
import std.collection.*
```

### Initialization

Ways to initialize an `ArrayList` include:

```
let a = ArrayList<Int64>([1, 2, 3])  // Initialize using a concrete list
let a = ArrayList<Int64>(3, item: 0)  // Length 3 and all elements are 0
let b = Array<Int64>(3, {i => i + 1})   // Initialize using lambda function, result is [1, 2, 3]
let a = ArrayList<String>()  // Created an empty ArrayList whose element type is String
let b = ArrayList<String>(100)  // Created an empty ArrayList whose element type is String, and allocate a space of 100
let c = ArrayList<Int64>([0, 1, 2])  // Created an ArrayList whose element type is Int64, containing elements 0, 1, 2
let d = ArrayList<Int64>(c)  // Use another Collection to initialize an ArrayList
let e = ArrayList<Int64>(2, {x: Int64 => x.toString()})  // Created an ArrayList whose element type is String and size is 2. All elements are initialized by specified rule function
```

### Visiting elements

When we need access to all the elements of the ArrayList, we can use a `for-in` loop to iterate through all the elements of the ArrayList.

```
import std.collection.*

main() {
    let list = ArrayList<Int64>([0, 1, 2])
    for (i in list) {
        println("The element is ${i}")
    }
}
```

When we want to access an element in a single specified location, we can use the subscript syntax to access it (the type of subscript must be Int64). The first element of a non-empty ArrayList always starts at position 0. We can access any element of the ArrayList from 0 up to the last position (`size - 1` of the ArrayList). Using a negative number or an index greater than or equal to size triggers a runtime exception.

```
let a = list[0]  // a == 0
let b = list[1]  // b == 1
let c = list[-1]  // Runtime Exceptions
```

### Size

To obtain the length of an `ArrayList`, use syntax of the form `arr.size`.

### Adding elements

To add an element `i` to the end of an `ArrayList` `arr`, use `arr.append(i)`.

### Slice of an `ArrayList`

The slice function on `ArrayList` has the following signature:

```
public func slice(range: Range<Int64>): ArrayList<T>
```

Note a range argument is taken (e.g. `l..r` for the closed-open interval `[l, r]`, or `l..=r`
for the closed interval `[l, r]`). This is different from the case for Arrays, which takes
the starting index and length as arguments.

### Inserting elements

We can use the `insert` and `insertAll` functions to insert a specified single element or a Collection value of the same element type into the location of the index we specify. The elements at the index and the elements behind them are moved back to make space.

```
let list = ArrayList<Int64>([]0, 1, 2)  // list contains elements 0, 1, 2
list.insert(1, 4)  // list contains elements 0, 4, 1, 2
```

### Deleting elements

To remove an element from an ArrayList, you can use the remove function, which requires you to specify the index to be remover, The elements that follow the index are moved forward to fill the space.

```
let list = ArrayList<String>(["a", "b", "c", "d"])  // list contains the elements "a", "b", "c", "d"
list.remove(1) // Delete the element at subscrip 1, now the list contains elements "a", "c", "d"
```

### Iteration

To iterate over elements of an ArrayList `arr`, use:

```
for (element in arr) {
    ...
}
```

Note there is no pattern matching before `in`. If the elements of an array are tuples,
access entries of the tuple individually, e.g.:

```
var a = ArrayList<(Int64, Int64)>([(2, 3), (3, 4)])
for (pair in a) {
    println("(${pair[0]}, {pair[1]})")
}
```