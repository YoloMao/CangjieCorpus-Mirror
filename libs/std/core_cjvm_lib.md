# core 包

## 介绍

此包包括一些常用接口 ToString、 Hashable、 Equatable 等，以及 String、 Range、 Array、 Option 等常用数据结构，包括预定义的异常、错误类型等。

## 主要接口

### interface Any

```cangjie
public interface Any
```

`Any` 是所有类型的父类型，所有 `interface` 都默认继承它，所有非 `interface` 类型都默认实现它。

### class Object

```cangjie
public open class Object <: Any {
    public const init()
}
```

`Object` 是所有 `class` 的父类，所有 `class` 都默认继承它。

#### init

```cangjie
public const init()
```

功能：构造一个 `object` 实例。

### interface Hasher

```cangjie
public interface Hasher {
    func finish(): Int64
    mut func reset(): Unit
    mut func write(value: Bool): Unit
    mut func write(value: Int8): Unit
    mut func write(value: Int16): Unit
    mut func write(value: Int32): Unit
    mut func write(value: Int64): Unit
    mut func write(value: Rune): Unit
    mut func write(value: UInt8): Unit
    mut func write(value: UInt16): Unit
    mut func write(value: UInt32): Unit
    mut func write(value: UInt64): Unit
    mut func write(value: Float16): Unit
    mut func write(value: Float32): Unit
    mut func write(value: Float64): Unit
    mut func write(value: String): Unit
}
```

`Hasher` 是用来处理哈希组合运算的接口。

### interface RuneExtension

```cangjie
public interface RuneExtension
```

`RuneExtension` 是 `Rune` 相关的辅助接口。

#### func finish

```cangjie
func finish(): Int64
```

功能：返回哈希运算的结果。

返回值：经过计算后的哈希值

#### func reset

```cangjie
mut func reset(): Unit
```

功能：重置哈希值。

#### func write

```cangjie
mut func write(value: Bool): Unit
```

功能：通过该函数把想要哈希运算的 Bool 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Int8): Unit
```

功能：通过该函数把想要哈希运算的 Int8 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Int16): Unit
```

功能：通过该函数把想要哈希运算的 Int16 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Int32): Unit
```

功能：通过该函数把想要哈希运算的 Int32 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Int64): Unit
```

功能：通过该函数把想要哈希运算的 Int64 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Rune): Unit
```

功能：通过该函数把想要哈希运算的 Rune 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: UInt8): Unit
```

功能：通过该函数把想要哈希运算的 UInt8 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: UInt16): Unit
```

功能：通过该函数把想要哈希运算的 UInt16 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: UInt32): Unit
```

功能：通过该函数把想要哈希运算的 UInt32 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: UInt64): Unit
```

功能：通过该函数把想要哈希运算的 UInt64 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Float16): Unit
```

功能：通过该函数把想要哈希运算的 Float16 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Float32): Unit
```

功能：通过该函数把想要哈希运算的 Float32 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: Float64): Unit
```

功能：通过该函数把想要哈希运算的 Float64 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
mut func write(value: String): Unit
```

功能：通过该函数把想要哈希运算的 String 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

### class ArithmeticException

```cangjie
public open class ArithmeticException <: Exception {
    public init()
    public init(message: String)
}
```

`ArithmeticException` 为算术异常类，用于在发生算术异常时使用。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

#### func getClassName

```cangjie
protected open override func getClassName(): String
```

功能：获得类名。

返回值：类名字符串

### class ArrayIterator

```cangjie
public class ArrayIterator<T> <: Iterator<T> {
    public init(data: Array<T>)
}
```

数组迭代器。

#### init

```cangjie
public init(data: Array<T>)
```

功能：创建一个数组迭代器。

参数：

- data：数组

#### func next

```cangjie
public func next(): Option<T>
```

功能：返回迭代器中的下一个值。

返回值：Option\<T>，可以使用 match 解构

#### func iterator

```cangjie
public func iterator(): Iterator<T>
```

功能：返回迭代器。

返回值：Iterator\<T> 类型，可以使用迭代器进行遍历。

### class Box

```cangjie
public class Box<T> {
    public var value: T
    public init(v: T)
}
```

`Box` 泛型提供了将所有的类型包装成引用类型的能力。

#### value

```cangjie
public var value: T
```

功能：获取或修改被包装的值

#### init

```cangjie
public init(v: T)
```

功能：构造函数。

参数：

- v：任意仓颉支持的类型参数

### extend Box <: Hashable

```cangjie
extend<T> Box<T> <: Hashable where T <: Hashable
```

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：获取 Box 对象的 hashCode 值。

返回值：hashCode 值

### extend Box <: Comparable

```cangjie
extend<T> Box<T> <: Comparable<Box<T>> where T <: Comparable<T>
```

#### operator func >

```cangjie
public operator func >(that: Box<T>): Bool
```

功能：比较 Box 对象的大小。

参数：

- that：比较的另外一个 Box 对象

返回值：原 Box 对象大于 that Box 对象返回 true，否则返回 false

#### operator func <

```cangjie
public operator func <(that: Box<T>): Bool
```

功能：比较 Box 对象的大小。

参数：

- that：比较的另外一个 Box 对象

返回值：原 Box 对象小于 that Box 对象返回 true，否则返回 false

#### operator func >=

```cangjie
public operator func >=(that: Box<T>): Bool
```

功能：比较 Box 对象的大小。

参数：

- that：比较的另外一个 Box 对象

返回值：原 Box 对象大于等于 that Box 对象返回 true，否则返回 false

#### operator func <=

```cangjie
public operator func <=(that: Box<T>): Bool
```

功能：比较 Box 对象的大小。

参数：

- that：比较的另外一个 Box 对象

返回值：原 Box 对象小于等于 that Box 对象返回 true，否则返回 false

#### operator func ==

```cangjie
public operator func ==(that: Box<T>): Bool
```

功能：比较 Box 对象是否相等。

参数：

- that：比较的另外一个 Box 对象

返回值：相等返回 true，不相等返回 false

#### operator func !=

```cangjie
public operator func !=(that: Box<T>): Bool
```

功能：比较 Box 对象是否不相等。

参数：

- that：比较的另外一个 Box 对象

返回值：不相等返回 true，相等返回 false

#### func compare

```cangjie
public func compare(that: Box<T>): Ordering
```

功能：判断当前 Box 实例与另一个 Box 实例的大小关系。

参数：

- that：比较的另外一个 Box 对象

返回值：如果当前 Box 实例大于 that，返回 Ordering.GT，等于返回 Ordering.EQ，小于返回 Ordering.LT

### extend Box <: ToString

```cangjie
extend<T> Box<T> <: ToString where T <: ToString
```

#### func toString

```cangjie
public func toString(): String
```

功能：获取 Box 对象的字符串表示。

返回值：转换后的字符串

### class SpawnException

```cangjie
public class SpawnException <: Exception {
    public init()
    public init(message: String)
}
```

`SpawnException` 为线程异常类，用于在线程处理过程中发生异常时使用。

#### init

```cangjie
public init()
```

功能：得到一个 SpawnException 实例。

#### init

```cangjie
public init(message: String)
```

参数：

- message：预定义消息

### class Error

```cangjie
public open class Error <: ToString
```

`Error` 是所有错误类的基类。该类不可被继承，不可初始化，但是可以被捕获到。

#### prop message

```cangjie
public open prop message: String
```

功能：返回错误信息

返回值 String - 错误信息

#### func toString

```cangjie
public open func toString(): String
```

功能：返回用于打印的错误信息。

返回值：错误信息字符串

#### func printStackTrace

```cangjie
public open func printStackTrace(): Unit
```

功能：打印堆栈信息。

返回值：Unit

#### func getStackTrace

```cangjie
public func getStackTrace(): Array<StackTraceElement>
```

功能：得到堆栈信息数组。

返回值：堆栈信息数组

### class Exception

```cangjie
public open class Exception <: ToString {
    public init()
    public init(message: String)
}
```

`Exception` 是所有异常类的基类。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

#### prop message

```cangjie
public open prop message: String
```

功能：返回异常信息

#### func toString

```cangjie
public open func toString(): String
```

功能：返回用于打印的错误信息。

返回值：异常信息字符串

#### func printStackTrace

```cangjie
public func printStackTrace(): Unit
```

功能：打印堆栈信息。

#### func getStackTrace

```cangjie
public func getStackTrace(): Array<StackTraceElement>
```

功能：得到堆栈信息数组。

返回值：堆栈信息数组

#### func getClassName

```cangjie
protected open func getClassName(): String
```

功能：获得类名。

返回值：类名字符串

### class IllegalArgumentException

```cangjie
public class IllegalArgumentException <: Exception {
    public init()
    public init(message: String)
}
```

`IllegalArgumentException` 为参数非法异常。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

### class IllegalStateException

```cangjie
public class IllegalStateException <: Exception {
    public init()
    public init(message: String)
}
```

'IllegalStateException' 为非法状态异常。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

### class IndexOutOfBoundsException

```cangjie
public class IndexOutOfBoundsException <: Exception {
    public init()
    public init(message: String)
}
```

`IndexOutOfBoundsException` 为索引越界异常。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

### class NegativeArraySizeException

```cangjie
public class NegativeArraySizeException <: Exception {
    public init()
    public init(message: String)
}
```

`NegativeArraySizeException` 表示数组大小为负数的异常。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

### class NoneValueException

```cangjie
public class NoneValueException <: Exception {
    public init()
    public init(message: String)
}
```

`NoneValueException` 为值为 `None` 异常。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

### class UnsupportedException

```cangjie
public class UnsupportedException <: Exception {
    public init()
    public init(message: String)
}
```

未支持异常类。

#### init

```cangjie
public init()
```

功能：构造默认的 UnsupportedException 实例。

#### init

```cangjie
public init(message: String)
```

功能：根据指定异常信息构造 UnsupportedException 实例。

参数：

- message：预定义消息

### class InternalError

```cangjie
public class InternalError <: Error
```

`InternalError` 继承了 `Error`，表示内部错误，该类不可初始化，但是可以被捕获到

### class OutOfMemoryError

```cangjie
public class OutOfMemoryError <: Error
```

`OutOfMemoryError` 继承了 `Error`，表示内存不足错误，该类不可被继承，不可初始化，但是可以被捕获到

### class OverflowException

```cangjie
public class OverflowException <: ArithmeticException {
    public init()
    public init(message: String)
}
```

`OverflowException` 为算术运算溢出异常。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

### class IllegalMemoryException

```cangjie
public class IllegalMemoryException <: Exception {
    public init()
    public init(message: String)
}
```

`IllegalMemoryException` 为内存操作错误异常。

#### init

```cangjie
public init()
```

功能：无参构造函数。

#### init

```cangjie
public init(message: String)
```

参数：

- message：异常信息

### class FutureBase

```cangjie
sealed abstract class FutureBase {
    protected func execute(): Unit
}
```

此抽象类为 `Future<T>` 类型的基类。

#### func execute

```cangjie
protected func execute(): Unit
```

功能：执行函数。

### class Future

```cangjie
public class Future<T> <: FutureBase
```

`spawn` 表达式的返回类型是 `Future<T>` ，其中 T 是类型变元，其类型与闭包表达式的返回类型一致。当我们调用 `Future<T>` 的 get() 函数时，阻塞当前运行的线程，直到 `Future<T>` 实例所代表的线程运行结束。

#### prop thread

```cangjie
public prop thread: Thread
```

功能：获得当前线程的 Thread 实例

#### func get

```cangjie
public func get(): T
```

功能：阻塞当前线程，等待当前 Future 对象对应的线程的结果。

返回值：返回结果

#### func get

```cangjie
public func get(ns: Int64): Option<T>
```

功能：阻塞当前线程，等待当前 Future 对象对应的线程的结果如果相应的线程在 ns 纳秒内未完成执行，则该函数将返回 None。

参数：

- ns：传入等待时间纳秒为单位的 Int64 类型

返回值：若未完成返回 None，若 ns <= 0, 等同于 get(); 若线程以异常退出执行，在 get 调用处将继续抛出该异常

#### func tryGet

```cangjie
public func tryGet(): Option<T>
```

功能：尝试获取结果，不会阻塞当前线程如果相应的线程未执行完成，则该函数返回 None，否则返回 Some。

返回值：若未完成返回 None，否则返回 Some

#### func cancel

```cangjie
public func cancel(): Unit
```

功能：给当前 Future 对象对应的线程发送取消请求。该方法不会立即停止线程执行，仅发送请求，相应地，函数 hasPendingCancellation 可用于检查线程是否存在取消请求。

调用 `Future<T>` 的 `cancel` 方法会向对应线程发送取消请求，通过 `Thread` 类的属性 `hasPendingCancellation` 可以检查该仓颉线程是否存在取消请求。

### interface ThreadContext

```cangjie
public interface ThreadContext {
    func end(): Unit
    func hasEnded(): Bool
}
```

用户创建 `thread` 时，除了缺省 `spawn` 表达式入参，也可以通过传入不同 `ThreadContext` 类型的实例，选择不同的线程上下文，然后一定程度上控制并发行为。

目前不允许用户自行实现 `ThreadContext` 接口，仓颉语言根据使用场景，提供了`MainThreadContext`, 具体定义可在终端框架库中查阅。

#### func end

```cangjie
func end(): Unit
```

功能：结束方法,用于向当前 context 发送结束请求。

#### func hasEnded

```cangjie
func hasEnded(): Bool
```

功能：检查方法,用于检查当前 context 是否已结束。

返回值：若结束返回 true，否则返回 false

### class Thread

```cangjie
public class Thread
```

`Thread` 类为用户提供获取线程 ID 及名字、查询线程是否存在取消请求、注册线程未处理异常的处理函数等功能。

该类型实例无法通过构造得到，仅能通过 `Future` 对象的 `thread` 属性或是 `Thread` 类的 `currentThread` 静态属性获取。

#### prop currentThread

```cangjie
public static prop currentThread: Thread
```

功能：获取当前执行线程的 Thread 对象。

#### prop id

```cangjie
public prop id: Int64
```

功能：获取当前执行线程的标识，以 Int64 表示，所有存活的线程都有不同标识，但不保证当线程执行结束后复用它的标识。

#### prop name

```cangjie
public mut prop name: String
```

功能：获取或是设置线程的名称，获取设置都具有原子性。

#### prop hasPendingCancellation

```cangjie
public prop hasPendingCancellation: Bool
```

功能：线程是否存在取消请求，即是否通过 future.cancel() 发送过取消请求。

常见使用方法：Thread.currentThread.hasPendingCancellation。

#### func handleUncaughtExceptionBy

```cangjie
public static func handleUncaughtExceptionBy(exHandler: (Thread, Exception) -> Unit): Unit
```

功能：注册线程未处理异常的处理函数当某一线程因异常而提前终止后，如果全局的未处理异常函数被注册，那么将调用该函数并结束线程，在该函数内抛出异常时，将向终端打印提示信息并结束线程，但不会打印异常调用栈信息；如果没有注册全局异常处理函数，那么默认会向终端打印异常调用栈信息。多次注册处理函数时，后续的注册函数将覆盖之前的处理函数。当有多个线程同时因异常而终止时，处理函数将被并发执行，因而开发者需要在处理函数中确保并发正确性。处理函数的参数第一个参数类型为 Thread，是发生异常的线程第二个参数类型为 Exception，是线程未处理的异常。

### class ThreadLocal

```cangjie
public class ThreadLocal<T>
```

使用 `ThreadLocal` 可以在每个仓颉线程安全地访问他们各自的 “全局变量”。

#### func get

```cangjie
public func get(): ?T
```

功能：获得仓颉线程局部变量的值，如果值不存在，则返回 Option\<T>.None。

返回值：仓颉线程局部变量的值

#### func set

```cangjie
public func set(value: ?T): Unit
```

功能：通过 value 设置仓颉线程局部变量的值，如果传入 Option\<T>.None，该局部变量的值将被删除，在线程后续操作中将无法获取。

参数：

- value：需要设置的局部变量的值

### struct Range

```cangjie
public struct Range<T> <: Iterable<T> where T <: Countable<T> & Comparable<T> & Equatable<T> {
    public let start: T
    public let end: T
    public let step: Int64
    public let hasStart: Bool
    public let hasEnd: Bool
    public let isClosed: Bool
    public const init(start: T, end: T, step: Int64, hasStart: Bool, hasEnd: Bool, isClosed: Bool)
}
```

`Range` 类用于表示拥有固定步长的序列，区间类型是一个泛型，使用 `Range<T>`  表示。

#### start

```cangjie
public let start: T
```

#### end

```cangjie
public let end: T
```

#### step

```cangjie
public let step: Int64
```

#### hasStart

```cangjie
public let hasStart: Bool
```

#### hasEnd

```cangjie
public let hasEnd: Bool
```

#### isClosed

```cangjie
public let isClosed: Bool
```

#### init

```cangjie
public const init(start: T, end: T, step: Int64, hasStart: Bool, hasEnd: Bool, isClosed: Bool)
```

功能：使用该构造函数创建 Range 序列。

参数：

- start：T 开始值
- end：T 结束值
- step：Int64 步长
- hasStart：Bool 是否有开始值
- hasEnd：Bool 是否有结束值
- isClosed：Bool true，代表左闭右闭；false，代表左闭右开

异常：

- IllegalArgumentException：当 step 等于 0 时, 抛出异常

#### func iterator

```cangjie
public func iterator(): Iterator<T>
```

功能：返回当前序列的迭代器。

返回值：Iterator\<T>

#### func isEmpty

```cangjie
public const func isEmpty(): Bool
```

功能：判断该序列是否为空。

返回值：如果为空，返回 true，否则返回 false

### class RangeIterator

```cangjie
public class RangeIterator<T> <: Iterator<T> where T <: Countable<T> & Comparable<T> & Equatable<T>
```

`RangeIterator` 类为 `Range` 类型的迭代器。

#### func next

```cangjie
public func next(): Option<T>
```

功能：返回迭代器中的下一个值。

返回值：Option\<T>

#### func iterator

```cangjie
public func iterator(): Iterator<T>
```

功能：返回迭代器。

返回值：Iterator\<T>

### class StackOverflowError

```cangjie
public class StackOverflowError <: Error {}
```

`StackOverflowError` 类继承了 `Error`，表示堆栈溢出错误，该类不可被继承，不可初始化，但是可以被捕获到

#### func printStackTrace

```cangjie
public override func printStackTrace(): Unit
```

功能：打印堆栈信息。

### class StackTraceElement

```cangjie
public open class StackTraceElement {
    public let declaringClass: String
    public let methodName: String
    public let fileName: String
    public let lineNumber: Int64
    public init(declaringClass: String, methodName: String, fileName: String, lineNumber: Int64)
}
```

`StackTraceElement` 类用于提供具体的堆栈信息。

#### declaringClass

```cangjie
public let declaringClass: String
```

类名

#### methodName

```cangjie
public let methodName: String
```

函数名

#### fileName

```cangjie
public let fileName: String
```

文件名

#### lineNumber

```cangjie
public let lineNumber: Int64
```

行号

#### init

```cangjie
public init(declaringClass: String, methodName: String, fileName: String, lineNumber: Int64)
```

参数：

- declaringClass：类名
- methodName：函数名
- fileName：文件名
- lineNumber：行号

### struct Array

```cangjie
public struct Array<T> {
    public const init()
    public init(size: Int64, item!: T)
    public init(elements: Collection<T>)
    public init(size: Int64, initElement: (Int64) -> T)
}
```

`Array` 类为仓颉数组类型。

#### init

```cangjie
public const init()
```

功能：无参构造函数，创建一个空数组。

#### init

```cangjie
public init(size: Int64, item!: T)
```

功能：通过数组的长度和初始值创建一个数组。

> **注意：**
>
> 该构造函数不会拷贝 item， 如果 item 是一个引用类型，构造后数组的每一个元素都将指向相同的引用。

参数：

- size：数组大小
- item：数组初始值

异常：

- NegativeArraySizeException：当 size 小于 0，抛出异常

#### init

```cangjie
public init(elements: Collection<T>)
```

功能：根据 Collection 实例创建数组，把 Collection 实例中所有元素存入数组。

参数：

- elements：Collection 类型的元素

#### init

```cangjie
public init(size: Int64, initElement: (Int64) -> T)
```

功能：创建长度为 size ，元素类型为 (Int64) -> T 的数组。

参数：

- size：数组大小
- initElement：初始化函数

异常：

- NegativeArraySizeException：当 size 小于 0，抛出异常

#### func slice

```cangjie
public func slice(start: Int64, len: Int64): Array<T>
```

功能：返回切片后数组如果 start 小于 0 ，或者 len 小于 0 ，或者 （start + len）的值大于 Array 的长度则抛出异常 IndexOutOfBoundsException。

参数：

- start：切片的起始位置
- len：切片的长度

返回值：返回切片后的 Array\<T>(后面删除)

#### func get

```cangjie
public func get(index: Int64): Option<T>
```

功能：返回数组下标 index 对应的值。

参数：

- index：要获取值的下标

返回值：Option 类型的值，可以使用 match 解构

#### func set

```cangjie
public func set(index: Int64, element: T): Unit
```

功能：修改数组中下标 index 对应的值如果 index 小于 0 或者大于或等于 Array 的长度则抛出异常 IndexOutOfBoundsException。

参数：

- index：需要修改的值的下标
- element：修改的目标值

#### operator func []

```cangjie
public operator func [](index: Int64): T
```

功能：获取数组下标 index 对应的值。

参数：

- index：要获取值的下标

返回值：获取得到的值

异常：

- IndexOutOfBoundsException：如果 index 小于 0，或大于等于数组长度，抛出异常

#### operator func []

```cangjie
public operator func [](index: Int64, value!: T): Unit
```

功能：修改数组中下标 index 对应的值。

参数：

- index：需要修改值的下标
- value：修改的目标值

异常：

- IndexOutOfBoundsException：如果 index 小于 0，或大于等于数组长度，抛出异常

#### operator func []

```cangjie
public operator func [](range: Range<Int64>): Array<T>
```

功能：返回切片后的数组如果参数 range 是使用 Range 构造函数构造的 Range 实例，有如下行为：1）start 的值就是构造函数传入的值本身，不受构造时传入的 hashStart 的值的影响2）hasEnd 为 false 时，该 Range 实例为开区间，不受构造时传入的 isClosed 的值的影响。
参数：

- range：切片的范围，注意这里 range 的步长只能为 1

返回值：新的数组

异常：

- IllegalArgumentException：如果 range 的步长不等于 1，抛出异常
- IndexOutOfBoundsException：如果 range 表示的数组范围无效，抛出异常

#### operator func []

```cangjie
public operator func [](range: Range<Int64>, value!: T): Unit
```

功能：用指定的值对本数组一个连续范围的元素赋值如果参数 range 是使用 Range 构造函数构造的 Range 实例，有如下行为：1）start 的值就是构造函数传入的值本身，不受构造时传入的 hashStart 的值的影响2）hasEnd 为 false 时，该 Range 实例为开区间，不受构造时传入的 isClosed 的值的影响。
参数：

- range：数组范围，注意这里 range 的步长只能为 1
- value：修改的目标值

异常：

- IllegalArgumentException：如果 range 的步长不等于 1，抛出异常
- IndexOutOfBoundsException：如果 range 表示的数组范围无效，抛出异常

#### operator func []

```cangjie
public operator func [](range: Range<Int64>, value!: Array<T>): Unit
```

功能：用指定的数组对本数组一个连续范围的元素赋值如果参数 range 是使用 Range 构造函数构造的 Range 实例，有如下行为：1）start 的值就是构造函数传入的值本身，不受构造时传入的 hashStart 的值的影响2）hasEnd 为 false 时，该 Range 实例为开区间，不受构造时传入的 isClosed 的值的影响。
参数：

- range：数组范围，注意这里 range 的步长只能为 1
- value：修改的目标值

异常：

- IllegalArgumentException：如果 range 的步长不等于 1，或 range 长度不等于 value 长度，抛出异常
- IndexOutOfBoundsException：如果 range 表示的数组范围无效，抛出异常

#### func reverse

```cangjie
public func reverse(): Unit
```

功能：反转数组，将数组中元素的顺序进行反转。

#### func clone

```cangjie
public func clone(): Array<T>
```

功能：克隆数组。

返回值：新的数组

#### func clone

```cangjie
public func clone(range: Range<Int64>) : Array<T>
```

功能：按 Range 克隆数组如果参数 range 是使用 Range 构造函数构造的 Range 实例，有如下行为：1）start 的值就是构造函数传入的值本身，不受构造时传入的 hashStart 的值的影响2）hasEnd 为 false 时，该 Range 实例为开区间，不受构造时传入的 isClosed 的值的影响。
参数：

- range：切片的范围

返回值：新的数组

异常：

- IndexOutOfBoundsException：range 超出数组范围则抛出此异常

#### func copyTo

```cangjie
public func copyTo(dst: Array<T>, srcStart: Int64, dstStart: Int64, copyLen: Int64): Unit
```

功能：将数组中的一段数据拷贝到目标数组中或 dstStart 大于或等于目标数组大小，或 copyLen 超出范围则抛出此异常。

参数：

- dst：目标数组
- srcStart：从 this 数组的 srcStart 下标开始拷贝
- dstStart：从目标数组的 dstStart 下标开始拷贝
- copyLen：拷贝数组的长度

异常：

- IllegalArgumentException：copyLen 小于 0 则抛出此异常
- IndexOutOfBoundsException：如果 srcStart 或 dstStart 小于 0，或 srcStart 大于或等于 this 数组大小，

### struct DefaultHasher

```cangjie
public struct DefaultHasher <: Hasher {
 public init(res!: Int64 = 0)
}
```

`DefaultHasher` 是 struct 类型，提供了默认的哈希算法实现。

#### init

```cangjie
public init(res!: Int64 = 0)
```

功能：构造函数，创建一个 DefaultHasher。

参数：

- res：哈希结果，默认为 0

#### func reset

```cangjie
public mut func reset(): Unit
```

功能：重置哈希值为 0。

#### func finish

```cangjie
public func finish(): Int64
```

功能：返回哈希运算的结果。

返回值：经过计算后的哈希值

#### func write

```cangjie
public mut func write(value: Bool): Unit
```

功能：通过该函数把想要哈希运算的 Bool 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Int8): Unit
```

功能：通过该函数把想要哈希运算的 Int8 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Int16): Unit
```

功能：通过该函数把想要哈希运算的 Int16 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Int32): Unit
```

功能：通过该函数把想要哈希运算的 Int32 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Int64): Unit
```

功能：通过该函数把想要哈希运算的 Int64 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Rune): Unit
```

功能：通过该函数把想要哈希运算的 Rune 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: UInt8): Unit
```

功能：通过该函数把想要哈希运算的 UInt8 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: UInt16): Unit
```

功能：通过该函数把想要哈希运算的 UInt16 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: UInt32): Unit
```

功能：通过该函数把想要哈希运算的 UInt32 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: UInt64): Unit
```

功能：通过该函数把想要哈希运算的 UInt64 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Float16): Unit
```

功能：通过该函数把想要哈希运算的 Float16 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Float32): Unit
```

功能：通过该函数把想要哈希运算的 Float32 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: Float64): Unit
```

功能：通过该函数把想要哈希运算的 Float64 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

#### func write

```cangjie
public mut func write(value: String): Unit
```

功能：通过该函数把想要哈希运算的 String 值传入，然后进行哈希组合运算。

参数：

- value：待运算的值

### struct LibC

```cangjie
public struct LibC
```

`LibC` 是一个 `struct` 类型，提供了仓颉中较为高频使用的 C 接口。

#### func malloc

```cangjie
public static func malloc<T>(count!: Int64 = 1): CPointer<T> where T <: CType
```

功能：在堆中申请对应长度的内存。泛型参数 T 需要是 CType 的子类型。

参数：

- count：为可选参数，默认为1，表示申请 T 类型的个数

返回值：如果申请成功返回非空指针，内存长度为 sizeOf\<T>() * count

#### func free

```cangjie
public static unsafe func free<T>(p: CPointer<T>): Unit where T <: CType
```

功能：释放堆内存。

参数：

- p：表示被释放的内存地址

#### func mallocCString

```cangjie
public static unsafe func mallocCString(str: String): CString
```

功能：通过 String 申请与之字符内容相同的 C 风格字符串。

参数：

- str：仓颉 String 类型

返回值：返回 C 风格字符串，以 '\0' 结束

#### func free

```cangjie
public static unsafe func free(cstr: CString): Unit
```

功能：释放 C 风格字符串。

参数：

- cstr：需要释放的 C 风格字符串

### enum Ordering

```cangjie
public enum Ordering {
    | LT
    | GT
    | EQ
}
```

`Ordering` 表示一个比较结果的 `enum` 类型，它包含三种情况小于，大于和等于。

#### LT

```cangjie
LT
```

功能：构造一个 Ordering 实例，表示小于。

#### GT

```cangjie
GT
```

功能：构造一个 Ordering 实例，表示大于。

#### EQ

```cangjie
EQ
```

功能：构造一个 Ordering 实例，表示等于。

### enum Option

```cangjie
public enum Option<T> {
    | Some<T>
    | None
}
```

`Option` 是一个泛型 `enum` 类型，它包含两个构造器：`Some` 和 `None`。其中，`Some` 会携带一个参数，表示有值，`None` 不带参数，表示无值。当需要表示某个类型可能有值，也可能没有值的时候，可选择使用 `Option` 类型。

#### Some

```cangjie
Some(T)
```

#### None

```cangjie
None
```

#### func getOrThrow

```cangjie
public func getOrThrow(): T
```

功能：获得值或抛出异常如果 `Option` 值是 `Some`，则返回类型 `T` 的值如果 `Option` 值是 `None`，则抛出异常。

返回值：返回相应类型的值

#### func getOrThrow

```cangjie
public func getOrThrow(exception: ()->Exception): T
```

功能：获得值或抛出指定异常如果 `Option` 值是 `Some`，则返回类型 `T` 的值如果 `Option` 值是 `None`，则调用入参，抛出异常。

参数：

- exception：类型为 () -> Exception 的 Lambda

返回值：返回相应类型的值

#### func getOrDefault

```cangjie
public func getOrDefault(other: ()->T): T
```

功能：获得值或返回默认值如果 `Option` 值是 `Some`，则返回类型 `T` 的值如果 `Option` 值是 `None`，则调用入参，返回类型 `T` 的值。

参数：

- other：类型为 () -> T 的 Lambda

返回值：返回相应类型的值

#### func isNone

```cangjie
public func isNone(): Bool
```

功能：判断 `Option` 值是否为 `None`。

返回值：如果 `Option` 值是 `None`，则返回 true，否则返回 false

#### func isSome

```cangjie
public func isSome(): Bool
```

功能：判断 `Option` 值是否为 `Some`。

返回值：如果 `Option` 值是 `Some`，则返回 true，否则返回 false

### extend Option <: ToString

```cangjie
extend<T> Option<T> <: ToString where T <: ToString
```

#### func toString

```cangjie
public func toString(): String
```

功能：将 Option 转换为可输出的 String。

返回值：转化后的 String

### extend Option <: Equatable

```cangjie
extend<T> Option<T> <: Equatable<Option<T>> where T <: Equatable<T>
```

#### operator func ==

```cangjie
public operator func ==(that: Option<T>): Bool
```

功能：判断两个 Option 是否相等。

参数：

- that：传入 Option\<T>

返回值：如果相等，则返回 true，否则返回 false

#### operator func !=

```cangjie
public operator func !=(that: Option<T>): Bool
```

功能：判断两个 Option 是否不相等。

参数：

- that：传入 Option\<T>

返回值：如果不相等，则返回 true，否则返回 false

### extend Option <: Hashable

```cangjie
extend<T> Option<T> <: Hashable where T <: Hashable
```

为 `Option` 类型扩展 `Hashable`。
其中， `Some(T)` 的 hashCode 等于 `T` 的值对应的 hashCode，`None` 的 hashCode 等于 `Int64(0)`。

#### func hashCode

```cangjie
public func hashCode(): Int64
```

### extend Array <: ToString

```cangjie
extend<T> Array<T> <: ToString where T <: ToString
```

`Array` 类型为 `struct` 类型，这里为其扩展一些接口实现。

#### func toString

```cangjie
public func toString(): String
```

功能：将数组转换为可输出的 String。

返回值：转化后的 String

### extend Array <: Equatable

```cangjie
extend<T> Array<T> <: Equatable<Array<T>> where T <: Equatable<T>
```

#### operator func ==

```cangjie
public const operator func ==(that: Array<T>): Bool
```

功能：判断两个 Array 是否相等。

参数：

- that：传入 Array\<T>

返回值：如果相等，则返回 true，否则返回 false

#### operator func !=

```cangjie
public const operator func !=(that: Array<T>): Bool
```

功能：判断两个 Array 是否不相等。

参数：

- that：传入 Array\<T>

返回值：如果不相等，则返回 true；相等则返回 false

#### func contains

```cangjie
public func contains(element: T): Bool
```

功能：判断 Array 是否包含指定元素。

参数：

- element：需要判断的元素

返回值：如果存在，则返回 true，否则返回 false

### extend Array <: Collection

```cangjie
extend<T> Array<T> <: Collection<T>
```

#### func iterator

```cangjie
public func iterator(): Iterator<T>
```

功能：按正确的顺序在此数组中的元素上返回迭代器。

返回值：迭代器

#### prop size

```cangjie
public prop size: Int64
```

功能：获取元素数量

#### func isEmpty

```cangjie
public func isEmpty(): Bool
```

功能：判断数组是否为空。

返回值：空，返回 true，否则返回 false

#### func toArray

```cangjie
public func toArray(): Array<T>
```

功能：根据当前 Array 生成新 Array 实例。

返回值：与原 Array 完全相同的另一个 Array 对象

### struct CPointerHandle

```cangjie
public struct CPointerHandle<T> where T <: CType {
 public let pointer: CPointer<T>
 public let array: Array<T>
 public init()
 public init(ptr: CPointer<T>, arr: Array<T>)
}
```

`CPointerHandle` 用来表示获取 `Array` 原始指针的实例；该类型中的泛型参数应该满足 `CType` 约束。

#### pointer

```cangjie
public let pointer: CPointer<T>
```

功能：获取 Array 对应的原始指针

#### array

```cangjie
public let array: Array<T>
```

功能：原始指针对应的 Array

#### init

```cangjie
public init()
```

功能：默认初始化函数，初始化一个空指针和空数组。

#### init

```cangjie
public init(ptr: CPointer<T>, arr: Array<T>)
```

功能：通过传入的 CPointer 和 Array 初始化一个 CPointerHandle。

参数：

- ptr：CPointer 指针
- arr：指针对应的 Array

### interface ByteExtension

```cangjie
public interface ByteExtension
```

此接口用于扩展 `Byte` 类型

### extend Byte <: ByteExtension

```cangjie
extend Byte <: ByteExtension
```

`Byte` 类型为内置类型，这里是对其添加的一些在 Ascii 字符集范围内的函数。

#### func isAscii

```cangjie
public func isAscii(): Bool
```

功能：判断 Byte 是否是在 Ascii 范围内。

返回值：如果 Byte 在 Ascii 范围内返回 true，否则返回 false

#### func isAsciiLetter

```cangjie
public func isAsciiLetter(): Bool
```

功能：判断 Byte 是否是在 Ascii 拉丁字母范围内。

返回值：如果 Byte 在 Ascii 拉丁字母范围内返回 true，否则返回 false

#### func isAsciiNumber

```cangjie
public func isAsciiNumber(): Bool
```

功能：判断 Byte 是否是在 Ascii 十进制数字范围内。

返回值：如果 Byte 在 Ascii 十进制数字范围内返回 true，否则返回 false

#### func isAsciiLowerCase

```cangjie
public func isAsciiLowerCase(): Bool
```

功能：判断 Byte 是否是在 Ascii 小写拉丁字母范围内。

返回值：如果 Byte 在 Ascii 小写拉丁字母范围内返回 true，否则返回 false

#### func isAsciiUpperCase

```cangjie
public func isAsciiUpperCase(): Bool
```

功能：判断 Byte 是否是在 Ascii 大写拉丁字母范围内。

返回值：如果 Byte 在 Ascii 大写拉丁字母范围内返回 true，否则返回 false

#### func isAsciiWhiteSpace

```cangjie
public func isAsciiWhiteSpace(): Bool
```

功能：判断 Byte 是否是在 Ascii 空白字符范围内。其取值范围为 $[09, 0D] \cup 20$。

返回值：如果 Byte 在 Ascii 空白字符范围内返回 true，否则返回 false

#### func isAsciiHex

```cangjie
public func isAsciiHex(): Bool
```

功能：判断 Byte 是否是在 Ascii 十六进制数字范围内。

返回值：如果 Byte 在 Ascii 十六进制数字范围内返回 true，否则返回 false

#### func isAsciiOct

```cangjie
public func isAsciiOct(): Bool
```

功能：判断 Byte 是否是在 Ascii 八进制数字范围内。

返回值：如果 Byte 在 Ascii 八进制数字范围内返回 true，否则返回 false

#### func isAsciiPunctuation

```cangjie
public func isAsciiPunctuation(): Bool
```

功能：判断 Byte 是否是在 Ascii 标点符号范围内。其取值范围为 $[21, 2F] \cup [3A, 40] \cup [5B, 60] \cup [7B, 7E]$。

返回值：如果 Byte 在 Ascii 标点符号范围内返回 true，否则返回 false

#### func isAsciiGraphic

```cangjie
public func isAsciiGraphic(): Bool
```

功能：判断 Byte 是否是在 Ascii 图形字符范围内。其取值范围为 $[21, 7E]$。

返回值：如果 Byte 在 Ascii 图形字符范围内返回 true，否则返回 false

#### func isAsciiControl

```cangjie
public func isAsciiControl(): Bool
```

功能：判断 Byte 是否是在 Ascii 控制字符范围内。其取值范围为 $[00, 1F] \cup 7F$。

返回值：如果 Byte 在 Ascii 控制字符范围内返回 true，否则返回 false

#### func isAsciiNumberOrLetter

```cangjie
public func isAsciiNumberOrLetter(): Bool
```

功能：判断 Byte 是否是在 Ascii 十进制数字和拉丁字母范围内。

返回值：如果 Byte 在 Ascii 十进制数字和拉丁字母范围内返回 true，否则返回 false

#### func toAsciiUpperCase

```cangjie
public func toAsciiUpperCase(): Byte
```

功能：将 Byte 换为对应的 Ascii 大写字符 Byte，如果无法转换则保持现状。

返回值：转换后的 Byte，如果无法转换则返回原来的 Byte

#### func toAsciiLowerCase

```cangjie
public func toAsciiLowerCase(): Byte
```

功能：将 Byte 换为对应的 Ascii 小写字符 Byte，如果无法转换则保持现状。

返回值：转换后的 Byte，如果无法转换则返回原来的 Byte

### extend Rune <: RuneExtension

```cangjie
extend Rune <: RuneExtension
```

`Rune` 类型为内置类型，这里是对其添加的一些在 Ascii 字符集范围内的函数。

#### func isAscii

```cangjie
public func isAscii(): Bool
```

功能：判断字符是否是 Ascii 中的字符。

返回值：如果是 Ascii 字符返回 true，否则返回 false

#### func isAsciiLetter

```cangjie
public func isAsciiLetter(): Bool
```

功能：判断字符是否是 Ascii 字母字符。

返回值：如果是 Ascii 字母字符返回 true，否则返回 false

#### func isAsciiNumber

```cangjie
public func isAsciiNumber(): Bool
```

功能：判断字符是否是 Ascii 数字字符。

返回值：如果是 Ascii 数字字符返回 true，否则返回 false

#### func isAsciiLowerCase

```cangjie
public func isAsciiLowerCase(): Bool
```

功能：判断字符是否是 Ascii 小写字符。

返回值：如果是 Ascii 小写字符返回 true，否则返回 false

#### func isAsciiUpperCase

```cangjie
public func isAsciiUpperCase(): Bool
```

功能：判断字符是否是 Ascii 大写字符。

返回值：如果是 Ascii 大写字符返回 true，否则返回 false

#### func isAsciiWhiteSpace

```cangjie
public func isAsciiWhiteSpace(): Bool
```

功能：判断字符是否是 Ascii 空白字符。其取值范围为 $[09, 0D] \cup 20$。

返回值：如果是 Ascii 空白字符返回 true，否则返回 false

#### func toAsciiUpperCase

```cangjie
public func toAsciiUpperCase(): Rune
```

功能：将字符转换为 Ascii 大写字符，如果无法转换则保持现状。

返回值：转换后的字符，如果无法转换则返回原来的 Rune

#### func toAsciiLowerCase

```cangjie
public func toAsciiLowerCase(): Rune
```

功能：将字符转换为 Ascii 小写字符，如果无法转换则保持现状。

返回值：转换后的字符，如果无法转换则返回原来的 Rune

#### func isAsciiHex

```cangjie
public func isAsciiHex(): Bool
```

功能：判断字符是否是 Ascii 十六进制字符。

返回值：如果是 Ascii 十六进制字符返回 true，否则返回 false

#### func isAsciiOct

```cangjie
public func isAsciiOct(): Bool
```

功能：判断字符是否是 Ascii 八进制字符。

返回值：如果是 Ascii 八进制字符返回 true，否则返回 false

#### func isAsciiPunctuation

```cangjie
public func isAsciiPunctuation(): Bool
```

功能：判断字符是否是 Ascii 标点符号字符。其取值范围为 $[21, 2F] \cup [3A, 40] \cup [5B, 60] \cup [7B, 7E]$。

返回值：如果是 Ascii 标点符号字符返回 true，否则返回 false

#### func isAsciiGraphic

```cangjie
public func isAsciiGraphic(): Bool
```

功能：判断字符是否是 Ascii 图形字符。其取值范围为 $[21, 7E]$。

返回值：如果是 Ascii 图形字符返回 true，否则返回 false

#### func isAsciiControl

```cangjie
public func isAsciiControl(): Bool
```

功能：判断字符是否是 Ascii 控制字符。其取值范围为 $[00, 1F] \cup 7F$。

返回值：如果是 Ascii 控制字符返回 true，否则返回 false

#### func isAsciiNumberOrLetter

```cangjie
public func isAsciiNumberOrLetter(): Bool
```

功能：判断字符是否是 Ascii 数字或拉丁字母字符。

返回值：如果是 Ascii 数字或拉丁字母字符返回 true，否则返回 false

#### func fromUtf8

```cangjie
public static func fromUtf8(arr: Array<UInt8>, index: Int64): (Rune, Int64)
```

功能：将 UInt8 数组中的某个元素，通过 UTF-8 转换成字符，并告知字符占用字节长度。

参数：

- arr：UInt8 数组
- index：UInt8 数组的下标

返回值：数组中 index 下标元素对应于 UTF-8 所表示的字符
字符字节所占的大小

#### func intoUtf8Array

```cangjie
public static func intoUtf8Array(c: Rune, arr: Array<UInt8>, index: Int64): Int64
```

功能：该函数会把字符转成字节码序列然后覆盖 Array 数组内指定位置的字节码。

参数：

- c：字符
- arr：待覆盖的 Array 数组
- index：目标位置的起始索引

返回值：字符的字节码长度，例如中文是三个字节码长度

#### func utf8Size

```cangjie
public static func utf8Size(arr: Array<UInt8>, index: Int64): Int64
```

功能：该函数会返回指定索引位置字节码对应 UTF-8 字符字节码应有的长度，准确来说，除了 ASCII 码，其他长度的字节码都有首位字节码，首位字节码开头 1 的个数表明了该字符对应的字节码长度，这个函数就用来扫描这个字节码的，如果不是首位字节码，就会抛出异常。

参数：

- arr：Array 数组
- index：指定字符的索引

返回值：字符的字节码长度，例如中文是三个字节码长度

异常：

- IllegalArgumentException：如果索引位置的字节码不符合首位字节码规则，会抛出异常

#### func utf8Size

```cangjie
public static func utf8Size(c: Rune): Int64
```

功能：返回字符对应的 UTF-8 的字节码长度，例如中文字符是 3 个长度。

参数：

- c：字符

返回值：字符的字节码长度

#### func getPreviousFromUtf8

```cangjie
public static func getPreviousFromUtf8(arr: Array<UInt8>, index: Int64): (Rune, Int64)
```

功能：当指定了一个索引，那么函数会找到数组对应索引位置并且根据 UTF-8 规则，查看该字节码是否是字符的首位字节码，如果不是就继续向前遍历，直到该字节码是首位字节码，然后利用字节码序列找到对应的字符。

参数：

- arr：Array 数组
- index：指定的索引

返回值：找到的字符
该字符首位字节码在数组中的索引

异常：

- IllegalArgumentException：如果找不到首位字节码，就会抛出异常

### extend Rune <: Comparable

```cangjie
extend Rune <: Comparable<Rune>
```

#### func compare

```cangjie
public func compare(rhs: Rune): Ordering
```

功能：判断 Rune 与另一个 Rune 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Rune 对象

返回值：如果大于，返回 Ordering.GT

### extend Rune <: ToString

`Rune` 类型为内置类型，这里为其扩展向 String 类型的转换。

```cangjie
extend Rune <: ToString
```

#### func toString

```cangjie
public func toString(): String
```

功能：将 Rune 转换为可输出的 String。

返回值：转化后的 String

### extend Rune <: Hashable

`Rune` 类型为内置类型，这里为其扩展 Hashable

```cangjie
extend Rune <: Hashable
```

#### func hashCode

```cangjie
public func hashCode(): Int64
```

### extend Rune <: Countable

`Rune` 类型为内置类型，这里为其扩展 Countable

```cangjie
extend Rune <: Countable<Rune>
```

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): Rune
```

功能：与 Int64 数进行加法运算，返回值是 Rune 类型。

参数：

- right：Int64 数

返回值：算数结果

异常：

- OverflowException：如果与 Int64 数进行加法运算后为不合法的 Unicode 值，抛出异常

### extend Int64 <: ToString

```cangjie
extend Int64 <: ToString
```

`Int64` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Int64 转换为可输出的 String。

返回值：转化后的 String

### extend Int64 <: Comparable

`Int64` 类型为内置类型，这里为其扩展 Comparable。

```cangjie
extend Int64 <: Comparable<Int64>
```

#### func compare

```cangjie
public func compare(rhs: Int64): Ordering
```

功能：判断 Int64 与另一个 Int64 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Int64 对象

返回值：如果大于，返回 Ordering.GT

### extend Int64 <: Hashable

`Int64` 类型为内置类型，这里为其扩展 Hashable

```cangjie
extend Int64 <: Hashable
```

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Int64 <: Countable

`Int64` 类型为内置类型，这里为其扩展 Countable

```cangjie
extend Int64 <: Countable<Int64>
```

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): Int64
```

功能：与 Int64 数进行加法运算，返回值是 Int64 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend Int32 <: ToString

```cangjie
extend Int32 <: ToString
```

`Int32` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Int32 转换为可输出的 String。

返回值：转化后的 String

### extend Int32 <: Comparable

`Int32` 类型为内置类型，这里为其扩展 Comparable。

```cangjie
extend Int32 <: Comparable<Int32>
```

#### func compare

```cangjie
public func compare(rhs: Int32): Ordering
```

功能：判断 Int32 与另一个 Int32 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Int32 对象

返回值：如果大于，返回 Ordering.GT

### extend Int32 <: Hashable

`Int32` 类型为内置类型，这里为其扩展 Hashable

```cangjie
extend Int32 <: Hashable
```

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Int32 <: Countable

```cangjie
extend Int32 <: Countable<Int32>
```

`Int32` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): Int32
```

功能：与 Int64 数进行加法运算，返回值是 Int32 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend Int16 <: ToString

```cangjie
extend Int16 <: ToString
```

`Int16` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Int16 转换为可输出的 String。

返回值：转化后的 String

### extend Int16 <: Comparable

`Int16` 类型为内置类型，这里为其扩展 Comparable。

```cangjie
extend Int16 <: Comparable<Int16>
```

#### func compare

```cangjie
public func compare(rhs: Int16): Ordering
```

功能：判断 Int16 与另一个 Int16 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Int16 对象

返回值：如果大于，返回 Ordering.GT

### extend Int16 <: Hashable

```cangjie
extend Int16 <: Hashable
```

`Int16` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Int16 <: Countable

```cangjie
extend Int16 <: Countable<Int16>
```

`Int16` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): Int16
```

功能：与 Int64 数进行加法运算，返回值是 Int16 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend Int8 <: ToString

```cangjie
extend Int8 <: ToString
```

`Int8` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Int8 转换为可输出的 String。

返回值：转化后的 String

### extend Int8 <: Comparable

```cangjie
extend Int8 <: Comparable<Int8>
```

`Int8` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: Int8): Ordering
```

功能：判断 Int8 与另一个 Int8 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Int8 对象

返回值：如果大于，返回 Ordering.GT

### extend Int8 <: Hashable

```cangjie
extend Int8 <: Hashable
```

`Int8` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Int8 <: Countable

```cangjie
extend Int8 <: Countable<Int8>
```

`Int8` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): Int8
```

功能：与 Int64 数进行加法运算，返回值是 Int8 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend IntNative <: ToString

```cangjie
extend IntNative <: ToString
```

`IntNative` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 IntNative 转换为可输出的 String。

返回值：转化后的 String

### extend IntNative <: Comparable

```cangjie
extend IntNative <: Comparable<IntNative>
```

`IntNative` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: IntNative): Ordering
```

功能：判断 IntNative 与另一个 IntNative 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 IntNative 对象

返回值：如果大于，返回 Ordering.GT

### extend IntNative <: Hashable

```cangjie
extend IntNative <: Hashable
```

`IntNative` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend IntNative <: Countable

```cangjie
extend IntNative <: Countable<IntNative>
```

`IntNative` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): IntNative
```

功能：与 Int64 数进行加法运算，返回值是 IntNative 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend UInt64 <: ToString

```cangjie
extend UInt64 <: ToString
```

`UInt64` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 UInt64 转换为可输出的 String。

返回值：转化后的 String

### extend UInt64 <: Comparable

```cangjie
extend UInt64 <: Comparable<UInt64>
```

`UInt64` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: UInt64): Ordering
```

功能：判断 UInt64 与另一个 UInt64 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 UInt64 对象

返回值：如果大于，返回 Ordering.GT

### extend UInt64 <: Hashable

```cangjie
extend UInt64 <: Hashable
```

`UInt64` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend UInt64 <: Countable

```cangjie
extend UInt64 <: Countable<UInt64>
```

`UInt64` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): UInt64
```

功能：与 Int64 数进行加法运算，返回值是 UInt64 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend UInt32 <: ToString

```cangjie
extend UInt32 <: ToString
```

`UInt32` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 UInt32 转换为可输出的 String。

返回值：转化后的 String

### extend UInt32 <: Comparable

```cangjie
extend UInt32 <: Comparable<UInt32>
```

`UInt32` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: UInt32): Ordering
```

功能：判断 UInt32 与另一个 UInt32 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 UInt32 对象

返回值：如果大于，返回 Ordering.GT

### extend UInt32 <: Hashable

```cangjie
extend UInt32 <: Hashable
```

`UInt32` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend UInt32 <: Countable

```cangjie
extend UInt32 <: Countable<UInt32>
```

`UInt32` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): UInt32
```

功能：与 Int64 数进行加法运算，返回值是 UInt32 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend UInt16 <: ToString

```cangjie
extend UInt16 <: ToString
```

`UInt16` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 UInt16 转换为可输出的 String。

返回值：转化后的 String

### extend UInt16 <: Comparable

```cangjie
extend UInt16 <: Comparable<UInt16>
```

`UInt16` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: UInt16): Ordering
```

功能：判断 UInt16 与另一个 UInt16 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 UInt16 对象

返回值：如果大于，返回 Ordering.GT

### extend UInt16 <: Hashable

```cangjie
extend UInt16 <: Hashable
```

`UInt16` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend UInt16 <: Countable

```cangjie
extend UInt16 <: Countable<UInt16>
```

`UInt16` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): UInt16
```

功能：与 Int64 数进行加法运算，返回值是 UInt16 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend UInt8 <: ToString

```cangjie
extend UInt8 <: ToString
```

`UInt8` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 UInt8 转换为可输出的 String。

返回值：转化后的 String

### extend UInt8 <: Comparable

```cangjie
extend UInt8 <: Comparable<UInt8>
```

`UInt8` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: UInt8): Ordering
```

功能：判断 UInt8 与另一个 UInt8 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 UInt8 对象

返回值：如果大于，返回 Ordering.GT

### extend UInt8 <: Hashable

```cangjie
extend UInt8 <: Hashable
```

`UInt8` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend UInt8 <: Countable

```cangjie
extend UInt8 <: Countable<UInt8>
```

`UInt8` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): UInt8
```

功能：与 Int64 数进行加法运算，返回值是 UInt8 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend UIntNative <: ToString

```cangjie
extend UIntNative <: ToString
```

`UIntNative` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 UIntNative 转换为可输出的 String。

返回值：转化后的 String

### extend UIntNative <: Comparable

```cangjie
extend UIntNative <: Comparable<UIntNative>
```

`UIntNative` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: UIntNative): Ordering
```

功能：判断 UIntNative 与另一个 UIntNative 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 UIntNative 对象

返回值：如果大于，返回 Ordering.GT

### extend UIntNative <: Hashable

```cangjie
extend UIntNative <: Hashable
```

`UIntNative` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend UIntNative <: Countable

```cangjie
extend UIntNative <: Countable<UIntNative>
```

`UIntNative` 类型为内置类型，这里为其扩展 Countable

#### func position

```cangjie
public func position(): Int64
```

功能：转成 Int64 类型。

返回值：转换后的 Int64 值

#### func next

```cangjie
public func next(right: Int64): UIntNative
```

功能：与 Int64 数进行加法运算，返回值是 UIntNative 类型。

参数：

- right：Int64 数

返回值：算数结果

### extend Float64 <: ToString

```cangjie
extend Float64 <: ToString
```

`Float64` 类型为内置类型，这里为其扩展向 String 类型的转换，默认保留 6 位小数，如需其他精度 String 请参考 Formatter 扩展。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Float64 转换为可输出的 String。

返回值：转化后的 String

### extend Float64 <: Comparable

```cangjie
extend Float64 <: Comparable<Float64>
```

`Float64` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: Float64): Ordering
```

功能：判断 Float64 与另一个 Float64 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Float64 对象

返回值：如果大于，返回 Ordering.GT

### extend Float64 <: Hashable

```cangjie
extend Float64 <: Hashable
```

`Float64` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Float32 <: ToString

```cangjie
extend Float32 <: ToString
```

`Float32` 类型为内置类型，这里为其扩展向 String 类型的转换，默认保留 6 位小数，如需其他精度 String 请参考 Formatter 扩展。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Float32 转换为可输出的 String。

返回值：转化后的 String

### extend Float32 <: Comparable

```cangjie
extend Float32 <: Comparable<Float32>
```

`Float32` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: Float32): Ordering
```

功能：判断 Float32 与另一个 Float32 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Float32 对象

返回值：如果大于，返回 Ordering.GT

### extend Float32 <: Hashable

```cangjie
extend Float32 <: Hashable
```

`Float32` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Float16 <: ToString

```cangjie
extend Float16 <: ToString
```

`Float16` 类型为内置类型，这里为其扩展向 String 类型的转换，默认保留 6 位小数，如需其他精度 String 请参考 Formatter 扩展。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Float16 转换为可输出的 String。

返回值：转化后的 String

### extend Float16 <: Comparable

```cangjie
extend Float16 <: Comparable<Float16>
```

`Float16` 类型为内置类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(rhs: Float16): Ordering
```

功能：判断 Float16 与另一个 Float16 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- rhs：另一个 Float16 对象

返回值：如果大于，返回 Ordering.GT

### extend Float16 <: Hashable

```cangjie
extend Float16 <: Hashable
```

`Float16` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Ordering <: ToString

```cangjie
extend Ordering <: ToString
```

`Ordering` 类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Ordering 转换为可输出的 String。

返回值：转化后的 String

### extend Ordering <: Comparable

```cangjie
extend Ordering <: Comparable<Ordering>
```

`Ordering` 类型，这里为其扩展 Comparable。

#### func compare

```cangjie
public func compare(that: Ordering): Ordering
```

功能：判断 Ordering 与另一个 Ordering 的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- that：另一个 Ordering 对象

返回值：如果大于，返回 Ordering.GT

#### operator func ==

```cangjie
public operator func ==(that: Ordering): Bool
```

功能：判断两个 Ordering 是否相等。

参数：

- that：传入 Ordering

返回值：如果相等，则返回 true，否则返回 false

#### operator func !=

```cangjie
public operator func !=(that: Ordering): Bool
```

功能：判断两个 Ordering 是否不相等。

参数：

- that：传入 Ordering

返回值：如果不相等，则返回 true，否则返回 false

#### operator func <=

```cangjie
public operator func <=(that: Ordering): Bool
```

功能：判断两个 Ordering 是否为小于等于关系。

参数：

- that：传入 Ordering

返回值：如果为小于等于关系，则返回 true，否则返回 false

#### operator func <

```cangjie
public operator func <(that: Ordering): Bool
```

功能：判断两个 Ordering 是否为小于关系。

参数：

- that：传入 Ordering

返回值：如果为小于关系，则返回 true，否则返回 false

#### operator func >=

```cangjie
public operator func >=(that: Ordering): Bool
```

功能：判断两个 Ordering 是否为大于等于关系。

参数：

- that：传入 Ordering

返回值：如果为大于等于关系，则返回 true，否则返回 false

#### operator func >

```cangjie
public operator func >(that: Ordering): Bool
```

功能：判断两个 Ordering 是否为大于关系。

参数：

- that：传入 Ordering

返回值：如果为大于关系，则返回 true，否则返回 false

### extend Ordering <: Hashable

```cangjie
extend Ordering <: Hashable
```

`Ordering` 类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：获取哈希码。

返回值：3 表示 Ordering.GT, 2 表示 Ordering.EQ, 1 表示 Ordering.LT

### extend Range <: Hashable

```cangjie
extend<T> Range<T> <: Hashable where T <: Hashable & Countable<T> & Comparable<T> & Equatable<T>
```

`Range` 类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Range <: Equatable

```cangjie
extend<T> Range<T> <: Equatable<Range<T>> where T <: Countable<T> & Comparable<T> & Equatable<T>
```

`Range` 类型，这里为其扩展 Equatable

#### operator func ==

```cangjie
public operator func ==(that: Range<T>): Bool
```

功能：判断两个 Range 是否相等。

返回值：true 代表相等，false 代表不相等

#### operator func !=

```cangjie
public operator func !=(that: Range<T>): Bool
```

功能：判断两个 Range 是否不相等。

返回值：true 代表不相等，false 代表相等

### extend Bool <: ToString

```cangjie
extend Bool <: ToString
```

`Bool` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Bool 转换为可输出的 String。

返回值：转化后的 String

### extend Bool <: Hashable

```cangjie
extend Bool <: Hashable
```

`Bool` 类型为内置类型，这里为其扩展 Hashable

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend Bool <: Equatable

```cangjie
extend Bool <: Equatable<Bool>
```

`Bool` 类型为内置类型，这里为其扩展 Equatable

### extend Unit <: ToString

```cangjie
extend Unit <: ToString
```

`Unit` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func toString

```cangjie
public func toString(): String
```

功能：将 Unit 转换为可输出的 String，其值为 "()"。

返回值：转化后的 String

### extend Unit <: Hashable

```cangjie
extend Unit <: Hashable
```

`Unit` 类型为内置类型，这里为其扩展 Hashable，其函数返回值为 0

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：返回哈希值。

### extend CPointer

```cangjie
extend<T> CPointer<T>
```

`CPointer` 类型为内置类型，在与 C 互操作中，该数据类型映射为 C 语言中的指针类型。这里扩展一些必要的指针使用相关接口，包含判空、读写数据等接口。其中泛型 `T` 为指针类型，其满足 `CType` 约束（ `CType` 接口描述见后面 `interface CType` 章节）。对 `CPointer` 做运算需要在 `unsafe` 上下文中进行。

#### func isNull

```cangjie
public func isNull(): Bool
```

功能：判断指针是否是空。

返回值：若是空返回 true，否则返回 false

#### func isNotNull

```cangjie
public func isNotNull(): Bool
```

功能：判断指针是否不是空。

返回值：若不是空返回 true，否则返回 false

#### func toUIntNative

```cangjie
public func toUIntNative(): UIntNative
```

功能：获取该指针的整型形式。

返回值：返回该指针的整型形式

#### func read

```cangjie
public unsafe func read(): T
```

功能：读取第一个数据，该接口需要用户保证指针的合法性，否则发生未定义行为。

返回值：返回该对象类型的第一个数据

#### func write

```cangjie
public unsafe func write(value: T): Unit
```

功能：写入一个数据，该数据总是在第一个，该接口需要用户保证指针的合法性，否则发生未定义行为。

参数：

- value：要写入的数据

#### func read

```cangjie
public unsafe func read(idx: Int64): T
```

功能：根据下标读取对应的数据，该接口需要用户保证指针的合法性，否则发生未定义行为。

参数：

- idx：要获取数据的下标

返回值：输入下标对应的数据

#### func write

```cangjie
public unsafe func write(idx: Int64, value: T): Unit
```

功能：在指定下标位置写入一个数据，该接口需要用户保证指针的合法性，否则发生未定义行为。

参数：

- idx：指定的下标位置
- value：写入的数据

#### operator func +

```cangjie
public unsafe operator func +(offset: Int64): CPointer<T>
```

功能：CPointer 对象指针后移，同 C 语言的指针加法操作。

参数：

- offset：偏移量

返回值：返回地址变动后的对象

#### operator func -

```cangjie
public unsafe operator func -(offset: Int64): CPointer<T>
```

功能：CPointer 对象指针前移，同 C 语言的指针减法操作。

参数：

- offset：偏移量

返回值：返回地址变动后的对象

#### func asResource

```cangjie
public func asResource(): CPointerResource<T>
```

功能：获取 CPointerResource 对象。

返回值：表示 CPointerResource 对象

### struct CPointerResource

```cangjie
public struct CPointerResource<T> <: Resource where T <: CType {
 public var value: CPointer<T>
}
```

`CPointer` 提供其对应的资源管理类型，可以通过 `CPointer` 的成员函数 `asResource` 获取：

#### value

```cangjie
public var value: CPointer<T>
```

#### func isClosed

```cangjie
public func isClosed(): Bool
```

功能：判断该指针内容是否已被释放。

返回值：返回 true 为已释放。

#### func close

```cangjie
public func close(): Unit
```

功能：关闭资源，对于 CPointer 类型为释放其指向的内容。

### extend CString

```cangjie
extend CString
```

`CString` 类型是内置类型，在与 C 互操作中，该数据类型映射为 C 语言中的字符串 `char*` 类型。这里扩展一些必要的字符串使用相关接口，包含判空、获取长度、截取等接口。 `CString` 提供了一个内建构造函数，接受 `CPointer<UInt8>` 类型的参数。

> **注意：**
>
> 若使用 CString 需要将 `\0` 当做结束符。

### init

```cangjie
public init(p: CPointer<UInt8>)
```

功能：通过字符串指针进行构造 CString ，该接口需要用户保证指针的合法性。

参数：

- p：使用已有的 UInt8 类型字符串指针进行构造

### extend CString <: ToString

```cangjie
extend CString <: ToString
```

`CString` 类型为内置类型，这里为其扩展向 String 类型的转换。

#### func getChars

```cangjie
public func getChars(): CPointer<UInt8>
```

功能：获取字符串的指针。

返回值：该字符串的指针

#### func isNull

```cangjie
public func isNull(): Bool
```

功能：判断字符串指针是否为空。

返回值：如果字符串指针为空，返回 true

#### func size

```cangjie
public func size(): Int64
```

功能：返回该字符串长度，同 C 语言中的 strlen。

返回值：字符串长度

#### func isEmpty

```cangjie
public func isEmpty(): Bool
```

功能：判断字符串是否为空字符串。

返回值：如果为空字符串或字符串指针为空，返回 true

#### func isNotEmpty

```cangjie
public func isNotEmpty(): Bool
```

功能：判断字符串是否不为空字符串。

返回值：如果不为空字符串，返回 true，如果字符串指针为空，返回 false

#### func startsWith

```cangjie
public func startsWith(prefix: CString): Bool
```

功能：判断字符串是否包含指定前缀如果原字符串或者 prefix 前缀字符串指针为空，均返回 false。

参数：

- prefix：匹配的目标前缀字符串

返回值：如果该字符串包含 prefix 前缀，返回 true

#### func endsWith

```cangjie
public func endsWith(suffix: CString): Bool
```

功能：判断字符串是否包含指定后缀如果原字符串或者 suffix 后缀字符串指针为空，均返回 false。

参数：

- suffix：匹配的目标后缀字符串

返回值：如果该字符串包含 suffix 后缀，返回 true

#### func equals

```cangjie
public func equals(rhs: CString): Bool
```

功能：判断字符串两个字符串是否相等。

参数：

- rhs：比较的目标字符串

返回值：如果两个字符串相等，返回 true

#### func equalsLower

```cangjie
public func equalsLower(rhs: CString): Bool
```

功能：判断字符串两个字符串是否相等，且忽略大小写。

参数：

- rhs：匹配的目标字符串

返回值：如果两个字符串忽略大小写相等，返回 true

#### func subCString

```cangjie
public func subCString(beginIndex: UIntNative): CString
```

功能：截取指定位置开始至字符串结束的子串，需要注意，该接口返回为字符串的副本，返回的子串使用完后需要手动 free。

参数：

- beginIndex：截取的起始位置

返回值：截取的子串，如果 beginIndex 与字符串长度相等，返回空字符串（空指针）

异常：

- IndexOutOfBoundsException：如果 beginIndex 大于字符串长度，抛出异常
- IllegalMemoryException：如果内存申请失败或内存拷贝失败时，抛出异常

#### func subCString

```cangjie
public func subCString(beginIndex: UIntNative, subLen: UIntNative): CString
```

功能：截取字符串的子串，指定起始位置和截取长度，如果截取的末尾位置超出字符串长度，截取至字符串末尾，需要注意，该接口返回为字符串的副本，返回的子串使用完后需要手动 free。

参数：

- beginIndex：截取的起始位置
- subLen：截取长度

返回值：截取的子串，如果 beginIndex 与字符串长度相等，返回空字符串（空指针）

异常：

- IndexOutOfBoundsException：如果 beginIndex 大于字符串长度，抛出异常
- IllegalMemoryException：如果内存申请失败或内存拷贝失败时，抛出异常

#### func compare

```cangjie
public func compare(str: CString): Int32
```

功能：按字典序比较两个字符串，同 C 语言中的 strcmp ，如果被比较的两个 CString 中存在空指针，该接口会抛出异常。

参数：

- str：比较的目标字符串

返回值：整数结果，相等时返回0，当该字符串比 str 小时，返回 -1，否则返回 1

异常：

- Exception：如果自身的数据指针或 str 为 null，抛出异常

#### func toString

```cangjie
public func toString(): String
```

功能：将 CString 类型转为仓颉的 String 类型。

返回值：转换后的字符串

#### func asResource

```cangjie
public func asResource(): CStringResource
```

功能：获取 CStringResource 对象。

返回值：表示 CStringResource 对象

### struct CStringResource

```cangjie
public struct CStringResource <: Resource {
 public let value: CString
}
```

`CString` 提供其对应的资源管理类型，可以通过 `CString` 的成员函数 `asResource` 获取：

#### value

```cangjie
public let value: CString
```

#### func isClosed

```cangjie
public func isClosed(): Bool
```

功能：判断该字符串是否被释放。

返回值：返回 true 为已释放。

#### func close

```cangjie
public func close(): Unit
```

功能：关闭资源，对于 CString 类型为释放其指向的内容。

### type Byte

```cangjie
public type Byte = UInt8
```

`Byte` 类型是内置类型 `UInt8` 的别名。

### type Int

```cangjie
public type Int = Int64
```

`Int` 类型是内置类型 `Int64` 的别名。

### type UInt

```cangjie
public type UInt = UInt64
```

`UInt` 类型是内置类型 `UInt64` 的别名。

### func print

```cangjie
public func print(str: String, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

> **注意：**
>
> 下列 print、 println、 eprint、 eprintln 函数默认为 UTF-8 编码，windows 环境需手动执行命令 chcp 65001（将 cmd 更改为 UTF-8 编码）。

参数：

- str：待输出的 String 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(str: String): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- str：待输出的 String 类型

### func print

```cangjie
public func print<T>(arg: T, flush!: Bool = false): Unit where T <: ToString
```

功能：向控制台输出数据。

参数：

- arg：待输出的数据，支持实现了 ToString 接口的类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println<T>(arg: T): Unit where T <: ToString
```

功能：向控制台输出数据，输出末尾换行。

参数：

- arg：待输出的数据，支持实现了 ToString 接口的类型

### func print

```cangjie
public func print(b: Bool, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- b：待输出的 Bool 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(b: Bool): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- b：待输出的 Bool 类型

### func print

```cangjie
public func print(c: Rune, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- c：待输出的 Rune 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(c: Rune): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- c：待输出的 Rune 类型

### func print

```cangjie
public func print(f: Float16, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- f：待输出的 Float16 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(f: Float16): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- f：待输出的 Float16 类型

### func print

```cangjie
public func print(f: Float32, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- f：待输出的 Float32 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(f: Float32): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- f：待输出的 Float32 类型

### func print

```cangjie
public func print(f: Float64, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- f：待输出的 Float64 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(f: Float64): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- f：待输出的 Float64 类型

### func print

```cangjie
public func print(i: Int8, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 Int8 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: Int8): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 Int8 类型

### func print

```cangjie
public func print(i: Int16, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 Int16 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: Int16): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 Int16 类型

### func print

```cangjie
public func print(i: Int32, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 Int32 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: Int32): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 Int32 类型

### func print

```cangjie
public func print(i: Int64, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 Int64 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: Int64): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 Int64 类型

### func print

```cangjie
public func print(i: UInt8, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 UInt8 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: UInt8): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 UInt8 类型

### func print

```cangjie
public func print(i: UInt16, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 UInt16 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: UInt16): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 UInt16 类型

### func print

```cangjie
public func print(i: UInt32, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 UInt32 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: UInt32): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 UInt32 类型

### func print

```cangjie
public func print(i: UInt64, flush!: Bool = false): Unit
```

功能：向控制台输出数据。

参数：

- i：待输出的 UInt64 类型
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(i: UInt64): Unit
```

功能：向控制台输出数据，输出末尾换行。

参数：

- i：待输出的 UInt64 类型

### func eprintln

```cangjie
public func eprintln(str: String): Unit
```

功能：eprintln 用于打印错误消息，如抛出异常, 消息将打印到标准错误文本流，而不是标准输出, 输出末尾换行。

参数：

- str：待输出的字符串

### func eprint

```cangjie
public func eprint(str: String, flush!: Bool = true): Unit
```

功能：eprint 用于打印错误消息，如抛出异常, 消息将打印到标准错误文本流，而不是标准输出。

参数：

- str：待输出的字符串
- flush：是否清空缓存，true 清空，false 不清空，默认 false

### func println

```cangjie
public func println(): Unit
```

功能：向标准输出（stdout）输出换行字符。

### func ifSome

```cangjie
public func ifSome<T>(o: Option<T>, action: (T) -> Unit): Unit
```

功能：如果输入是 Option.Some 类型数据，则执行 action 函数。

参数：

- o：Option 类型输入
- action：待执行函数

### func ifNone

```cangjie
public func ifNone<T>(o: Option<T>, action: () -> Unit): Unit
```

功能：如果输入是 Option.None 类型数据，则执行 action 函数。

参数：

- o：Option 类型输入
- action：待执行函数

### func acquireArrayRawData

```cangjie
public unsafe func acquireArrayRawData<T>(arr: Array<T>): CPointerHandle<T> where T <: CType
```

功能：获取 Array\<T> 中数据的原始指针实例，T 需要满足 CType 约束，指针使用完后需要及时用 releaseArrayRawData 函数释放该指针约束：getRaw() 与 releaseRaw() 之间仅可包含简单的 foreign C 函数调用等逻辑，不构造例如 CString 等的仓颉对象，否则可能造成不可期现象。

返回值：返回的原始指针实例

### func releaseArrayRawData

```cangjie
public unsafe func releaseArrayRawData<T>(handle: CPointerHandle<T>): Unit where T <: CType
```

功能：释放 acquireArrayRawData 获取的原始指针实例。

参数：

- handle：待释放的指针实例

### func refEq

```cangjie
public func refEq(a: Object, b: Object): Bool
```

功能：判断两个 Object 对象的内存地址是否是同一个。

参数：

- a：一个 Object 对象
- b：另一个 Object 对象

返回值：同一个返回 true，否则返回 false

### func CJ_CORE_AddAtexitCallback

```cangjie
public func CJ_CORE_AddAtexitCallback(callback: () -> Unit): Unit
```

功能：注册退出函数，此处建议使用 os 库内 Process.atexit 函数，除非有制作进程管理框架的需要, 否则不建议使用！。

参数：

- callback：回调函数

### func CJ_CORE_ExecAtexitCallbacks

```cangjie
public func CJ_CORE_ExecAtexitCallbacks(): Unit
```

功能：执行注册函数, 此处建议使用 os 库内 Process.exit 函数，除非有制作进程管理框架的需要, 否则不建议使用！。

### func zeroValue

```cangjie
public unsafe func zeroValue<T>(): T
```

功能：返回一个已全零初始化的 T 类型实例，这个实例一定要赋值为正常初始化的值，再使用。

### func sizeOf

```cangjie
public func sizeOf<T>(): UIntNative where T <: CType
```

功能：获取类型 T 所占用的内存空间大小。

返回值：类型 T 所占用内存空间的字节数

### func alignOf

```cangjie
public func alignOf<T>(): UIntNative where T <: CType
```

功能：获取类型 T 的内存对齐值。

返回值：对类型 T 做内存对齐的字节数

### interface Countable

```cangjie
public interface Countable<T> {
    func next(right: Int64): T
    func position(): Int64
}
```

#### func next

```cangjie
func next(right: Int64): T
```

功能：返回两个实例的和。

参数：

- right：另一个为 Int64 类型的实例

返回值：返回两个实例和的 T 类型

#### func position

```cangjie
func position(): Int64
```

功能：将对象转为 Int64 类型。

返回值：转换后的 Int64 整型

### interface Collection

```cangjie
public interface Collection<T> <: Iterable<T> {
    prop size: Int64
    func isEmpty(): Bool
    func toArray(): Array<T>
}
```

该接口用来表示集合。

#### prop size

```cangjie
prop size: Int64
```

功能：返回对象的长度
返回值 Int64 - 列表的容量

#### func isEmpty

```cangjie
func isEmpty(): Bool
```

功能：判断对象是否为空。

返回值：若为空返回 true，否则返回 false

#### func toArray

```cangjie
func toArray(): Array<T>
```

功能：将对象转为数组类型。

返回值：转换后的数组

### interface Less

```cangjie
public interface Less<T> {
    operator func <(rhs: T): Bool
}
```

#### operator func <

```cangjie
operator func <(rhs: T): Bool
```

功能：判断一个实例是否小于另一个实例。

参数：

- rhs：另一个实例

返回值：如果小于，返回 true，否则返回 false

### interface Greater

```cangjie
public interface Greater<T> {
    operator func >(rhs: T): Bool
}
```

#### operator func >

```cangjie
operator func >(rhs: T): Bool
```

功能：判断一个实例是否大于另一个实例。

参数：

- rhs：另一个实例

返回值：如果大于，返回 true，否则返回 false

### interface LessOrEqual

```cangjie
public interface LessOrEqual<T> {
    operator func <=(rhs: T): Bool
}
```

#### operator func <=

```cangjie
operator func <=(rhs: T): Bool
```

功能：判断一个实例是否小于等于另一个实例。

参数：

- rhs：另一个实例

返回值：如果小于等于，返回 true，否则返回 false

### interface GreaterOrEqual

```cangjie
public interface GreaterOrEqual<T> {
    operator func >=(rhs: T): Bool
}
```

#### operator func >=

```cangjie
operator func >=(rhs: T): Bool
```

功能：判断一个实例是否大于等于另一个实例。

参数：

- rhs：另一个实例

返回值：如果大于等于，返回 true，否则返回 false

### interface Comparable

```cangjie
public interface Comparable<T> <: Equatable<T> & Less<T> & Greater<T> & LessOrEqual<T> & GreaterOrEqual<T> {
    func compare(that: T): Ordering
}
```

#### func compare

```cangjie
func compare(that: T): Ordering
```

功能：判断一个实例与另一个实例的关系如果等于，返回 Ordering.EQ如果小于，返回 Ordering.LT。

参数：

- that：另一个实例

返回值：如果大于，返回 Ordering.GT

### interface Equal

```cangjie
public interface Equal<T> {
    operator func ==(rhs: T): Bool
}
```

该接口用来提供 Bool 、Rune、Int64、Int32、Int16、Int8、UIntNative、UInt64、UInt32、UInt16、UInt8、Float64、Float32、Float16、String、Array、Box、ArrayList、HashSet 的直接判等操作。

#### operator func ==

```cangjie
operator func ==(rhs: T): Bool
```

功能：判断两个实例是否相等。

参数：

- rhs：另一个实例

返回值：如果相等，返回 true，否则返回 false

### interface NotEqual

```cangjie
public interface NotEqual<T> {
    operator func !=(rhs: T): Bool
}
```

#### operator func !=

```cangjie
operator func !=(rhs: T): Bool
```

功能：判断两个实例是否不相等。

参数：

- rhs：另一个实例

返回值：如果不相等，返回 true，否则返回 false

### interface Equatable

```cangjie
public interface Equatable<T> <: Equal<T> & NotEqual<T>
```

### interface Hashable

```cangjie
public interface Hashable {
    func hashCode(): Int64
}
```

该接口用来提供 Bool、Rune、IntNative、Int64、Int32、Int16、Int8、UIntNative、UInt64、UInt32、UInt16、UInt8、Float64、Float32、Float16、String、Box 的哈希值。

#### func hashCode

```cangjie
func hashCode(): Int64
```

功能：获得实例类型的哈希值。

返回值：返回实例类型的哈希值

### interface Iterable

```cangjie
public interface Iterable<E> {
    func iterator(): Iterator<E>
}
```

该接口用来提供具体类型的迭代器。

#### func iterator

```cangjie
func iterator(): Iterator<E>
```

功能：返回实例类型的迭代器。

返回值：返回实例类型的迭代器

### interface Iterator

```cangjie
public interface Iterator<E> <: Iterable<E> {
    func next(): Option<E>
}
```

该接口用来返回迭代过程中的下一个元素。

#### func next

```cangjie
func next(): Option<E>
```

功能：返回迭代过程中的下一个元素。

返回值：迭代过程中的下一个元素

### interface Resource

```cangjie
public interface Resource {
    func isClosed(): Bool
    func close(): Unit
}
```

该接口表示资源的信息

#### func isClosed

```cangjie
func isClosed(): Bool
```

功能：判断资源是否关闭。

返回值：如果已经关闭返回 true，否则返回 false

#### func close

```cangjie
func close(): Unit
```

功能：关闭资源。

### interface ToString

```cangjie
public interface ToString {
    func toString(): String
}
```

该接口用来提供具体类型的字符串表示。

#### func toString

```cangjie
func toString(): String
```

功能：返回实例类型的字符串表示。

返回值：返回实例类型的字符串表示

### interface CType

```cangjie
sealed interface CType
```

此接口不包含任何函数，它可以作为所有 C 互操作支持的类型的父类型，便于在泛型约束中使用。

> **注意：**
>
> - `CType` 接口是仓颉中的一个接口类型，它本身不满足 `CType` 约束；
> - `CType` 接口不允许被继承、扩展；
> - `CType` 接口不会突破子类型的使用限制。

### struct String

```cangjie
public struct String <: Collection<Byte> & Equatable<String> & Comparable<String> & Hashable & ToString {
 public static let empty: String
 public init()
 public init(value: Array<Rune>)
 public init(value: Collection<Rune>)
}
```

此类主要用于实现 `String` 数据结构及相关操作函数。

#### empty

```cangjie
public static let empty: String
```

#### init

```cangjie
public init()
```

功能：无参构造函数，创建一个空的字符串。

#### init

```cangjie
public init(value: Array<Rune>)
```

功能：通过 Rune 数组创建一个字符串。

参数：

- value：Rune 数组

#### init

```cangjie
public init(value: Collection<Rune>)
```

功能：通过 Rune 列表创建一个字符串。

参数：

- value：Rune 列表

#### func getRaw

```cangjie
public unsafe func getRaw(): CPointerHandle<UInt8>
```

功能：返回当前 String 的原始指针，用于和C语言交互，使用完后需要 releaseRaw 函数释放该指针约束：getRaw() 与 releaseRaw() 之间仅可包含简单的 foreign C 函数调用等逻辑，不构造例如 CString 等的仓颉对象，否则可能造成不可期现象。

返回值：返回的原始指针实例

#### func releaseRaw

```cangjie
public unsafe func releaseRaw(cp: CPointerHandle<UInt8>): Unit
```

功能：释放 getRaw 函数获取的指针，释放时只能释放同一个 String 获取的指针，如果释放了其他 String 获取的指针，会出现不可预知的错误。

参数：

- cp：待释放的指针实例

#### func iterator

```cangjie
public func iterator(): Iterator<Byte>
```

功能：获得字符串的 UTF-8 编码字节迭代器。

返回值：实现了 Iterator 接口的 UTF-8 编码字节迭代器，支持 for-in 循环

#### func runes

```cangjie
public func runes(): Iterator<Rune>
```

功能：获得字符串的 Rune 迭代器。

返回值：字符串的 Rune 迭代器。

异常：

- IllegalArgumentException：迭代器在使用的过程中，如果读到非法字符抛出异常。

#### func lines

```cangjie
public func lines(): Iterator<String>
```

功能：获得字符串的行迭代器，每行都由换行符进行分隔，换行符是 `\n` `\r` `\r\n` 之一，结果中每行不包括换行符。

返回值：字符串的 lines 迭代器。

#### func tryGet

```cangjie
public func tryGet(index: Int64): Option<Byte>
```

功能：返回字符串下标 index 对应的 UTF-8 编码字节值。

参数：

- index：要获取的字节值的下标

返回值：获取得到下标对应的 UTF-8 编码字节值，当 index 小于 0 或者大于等于字符串长度，则返回 Option\<Byte>.None

#### func toRuneArray

```cangjie
public func toRuneArray(): Array<Rune>
```

功能：返回字符串的 Rune 数组。如果原字符串为空字符串，则返回空数组。

返回值：字符串的 Rune 数组

#### func toString

```cangjie
public func toString(): String
```

功能：获得字符串本身。

返回值：返回字符串本身

#### func clone

```cangjie
public func clone(): String
```

功能：返回原字符串的拷贝。

返回值：拷贝得到的新字符串

#### prop size

```cangjie
public prop size: Int64
```

功能：返回字符串 UTF-8 编码后的字节长度
返回值：字符串 UTF-8 编码后的字节长度

#### func isEmpty

```cangjie
public func isEmpty(): Bool
```

功能：判断原字符串是否为空字符串。

返回值：若为空返回 true，否则返回 false

#### func isAsciiBlank

```cangjie
public func isAsciiBlank(): Bool
```

功能：判断字符串是否为空或者字符串中的所有 Rune 都是 ascii 码的空白字符（包括：0x09、0x10、0x11、0x12、0x13、0x20）。

返回值：如果是返回 true，否则返回 false

#### func hashCode

```cangjie
public func hashCode(): Int64
```

功能：获得字符串的哈希值。

返回值：返回字符串的哈希值

#### func indexOf

```cangjie
public func indexOf(b: Byte): Option<Int64>
```

功能：返回指定字节 b 第一次出现的在原字符串内的索引。

参数：

- b：搜索的 UTF-8 编码字节

返回值：如果原字符串中没有此字节，则返回 Option\<Int64>.None

#### func indexOf

```cangjie
public func indexOf(b: Byte, fromIndex: Int64): Option<Int64>
```

功能：返回指定 UTF-8 编码字节 b 第一次出现的在原字符串内的索引。

参数：

- b：搜索的 UTF-8 编码字节
- fromIndex：以指定的索引 fromIndex 开始搜索，当 fromIndex 小于零正常返回，当 fromIndex 大于等于原字符串长度返回 Option\<Int64>.None

返回值：如果这个字节在下标 fromIndex 及其之后没有出现，则返回 Option\<Int64>.None

#### func indexOf

```cangjie
public func indexOf(str: String): Option<Int64>
```

功能：返回指定字符串 str 第一次出现的在原字符串的起始索引。

参数：

- str：搜索的字符串

返回值：如果原字符串中没有 str 字符串，则返回Option\<Int64>.None

#### func indexOf

```cangjie
public func indexOf(str: String, fromIndex: Int64): Option<Int64>
```

功能：返回指定字符串 str 第一次出现的在原字符串的起始索引当 str 是空字符串时，如果fromIndex 大于 0，返回 Option\<Int64>.None，否则返回 Option\<Int64>.Some(0)。

参数：

- str：待搜索的字符串
- fromIndex：以指定的索引 fromIndex 开始搜索，当 fromIndex 小于零正常返回，当 fromIndex 大于等于原字符串长度返回 Option\<Int64>.None

返回值：如果 str 字符串在下标 fromIndex 及其之后没有出现，则返回 Option\<Int64>.None，

#### func lastIndexOf

```cangjie
public func lastIndexOf(b: Byte): Option<Int64>
```

功能：返回指定 UTF-8 编码字节 b 最后一次出现的在原字符串内的索引。

参数：

- b：搜索的 UTF-8 编码字节

返回值：如果原字符串中没有此字节，则返回 Option\<Int64>.None

#### func lastIndexOf

```cangjie
public func lastIndexOf(b: Byte, fromIndex: Int64): Option<Int64>
```

功能：返回指定 UTF-8 编码字节 b 最后一次出现的在原字符串内的索引。

参数：

- b：搜索的 UTF-8 编码字节
- fromIndex：以指定的索引 fromIndex 开始搜索，当 fromIndex 小于零正常返回，当 fromIndex 大于等于原字符串长度返回 Option\<Int64>.None

返回值：如果这个字节在位置 fromIndex 及其之后没有出现，则返回 Option\<Int64>.None

#### func lastIndexOf

```cangjie
public func lastIndexOf(str: String): Option<Int64>
```

功能：返回指定字符串 str 最后一次出现的在原字符串的起始索引。

参数：

- str：搜索的字符串

返回值：如果原字符串中没有 str 字符串，则返回Option\<Int64>.None

#### func lastIndexOf

```cangjie
public func lastIndexOf(str: String, fromIndex: Int64): Option<Int64>
```

功能：返回指定字符串 str 最后一次出现的在原字符串的起始索引当 str 是空字符串时，如果 fromIndex 大于 0，返回 Option\<Int64>.None，否则返回 Option\<Int64>.Some(0)。

参数：

- str：待搜索的字符串
- fromIndex：以指定的索引 fromIndex 开始搜索，当 fromIndex 小于零正常返回，当 fromIndex 大于等于原字符串长度返回 Option\<Int64>.None

返回值：如果这个字符串在位置 fromIndex 及其之后没有出现，则返回 Option\<Int64>.None，

#### func isAscii

```cangjie
public func isAscii(): Bool
```

功能：判断字符串是否是一个 Ascii 字符串，如果字符串为空或没有 Ascii 以外的字符，则返回 true。

返回值：是则返回 true，不是则返回 false

#### func toArray

```cangjie
public func toArray(): Array<Byte>
```

功能：返回字符串的 UTF-8 编码的字节数组。

返回值：Byte 类型的 Array

#### func count

```cangjie
public func count(str: String): Int64
```

功能：返回子字符串 str 在原字符串中出现的次数。

参数：

- str：被搜索的子字符串

返回值：出现的次数，当 str 为空字符串时，返回原字符串中 Rune 的数量加一

#### func split

```cangjie
public func split(str: String, removeEmpty!: Bool = false): Array<String>
```

功能：对原字符串按照字符串 str 分隔符分割当 str 未出现在原字符串中，返回长度为 1 的字符串数组，唯一的元素为原字符串。

参数：

- str：字符串分隔符
- removeEmpty：移除分割结果中的空字符串，默认值为 false

返回值：分割后的字符串数组

#### func split

```cangjie
public func split(str: String, maxSplits: Int64, removeEmpty!: Bool = false): Array<String>
```

功能：对原字符串按照字符串 str 分隔符分割当 maxSplit 为 0 时，返回空的字符串数组；当 maxSplit 为 1 时，返回长度为 1 的字符串数组，唯一的元素为原字符串；当 maxSplit 为负数时，返回完整分割后的字符串数组；当 maxSplit 大于完整分割出来的子字符串数量时，返回完整分割的字符串数组当 str 未出现在原字符串中，返回长度为 1 的字符串数组，唯一的元素为原字符串；当 str 为空时，对每个字符进行分割；当原字符串和分隔符都为空时，返回空字符串数组。

参数：

- str：字符串分隔符
- maxSplit：最多分割为 maxSplit 个子字符串
- removeEmpty：移除分割结果中的空字符串，默认值为 false

返回值：分割后的字符串数组

#### func lazySplit

```cangjie
public func lazySplit(str: String, removeEmpty!: Bool = false): Iterator<String>
```

功能：对原字符串按照字符串 str 分隔符分割当 str 未出现在原字符串中，返回大小为 1 的字符串迭代器，唯一的元素为原字符串。

参数：

- str：字符串分隔符
- removeEmpty：移除分割结果中的空字符串，默认值为 false

返回值：分割后的字符串迭代器

#### func lazySplit

```cangjie
public func lazySplit(str: String, maxSplits: Int64, removeEmpty!: Bool = false): Iterator<String>
```

功能：对原字符串按照字符串 str 分隔符分割当 maxSplit 为 0 时，返回空的字符串迭代器；当 maxSplit 为 1 时，返回大小为 1 的字符串迭代器，唯一的元素为原字符串；当 maxSplit 为负数时，直接返回分割后的字符串迭代器；当 maxSplit 大于完整分割出来的子字符串数量时，返回完整分割的字符串迭代器当 str 未出现在原字符串中，返回大小为 1 的字符串迭代器，唯一的元素为原字符串；当 str 为空时，对每个字符进行分割；当原字符串和分隔符都为空时，返回空字符串迭代器。

参数：

- str：字符串分隔符
- maxSplit：最多分割为 maxSplit 个子字符串
- removeEmpty：移除分割结果中的空字符串，默认值为 false

返回值：分割后的字符串迭代器

#### func replace

```cangjie
public func replace(old: String, new: String): String
```

功能：使用新字符串替换原字符串中旧字符串。

参数：

- old：旧字符串
- new：新字符串

返回值：替换后的新字符串

异常：

- OutOfMemoryError：如果此函数分配内存时产生错误，抛出异常

#### func toAsciiLower

```cangjie
public func toAsciiLower(): String
```

功能：将该字符串中所有 Ascii 大写字母转化为 Ascii 小写字母。

返回值：转换后的新字符串

#### func toAsciiUpper

```cangjie
public func toAsciiUpper(): String
```

功能：将该字符串中所有 Ascii 小写字母转化为 Ascii 大写字母。

返回值：转换后的新字符串

#### func toAsciiTitle

```cangjie
public func toAsciiTitle(): String
```

功能：将该字符串标题化，只转换 Ascii 字符，当该英文字符是字符串中第一个字符或者该字符的前一个字符不是英文字符，则该字符大写，其他英文字符小写，非英文字符不变。

返回值：转换后的新字符串

#### func trimAscii

```cangjie
public func trimAscii(): String
```

功能：去除原字符串开头结尾以 whitespace 字符组成的子字符串（Ascii whitespace）。

返回值：转换后的新字符串

#### func trimAsciiLeft

```cangjie
public func trimAsciiLeft(): String
```

功能：去除原字符串开头以 whitespace 字符组成的子字符串（Ascii whitespace）。

返回值：转换后的新字符串

#### func trimAsciiRight

```cangjie
public func trimAsciiRight(): String
```

功能：去除原字符串结尾以 whitespace 字符组成的子字符串（Ascii whitespace）。

返回值：转换后的新字符串

#### func trimLeft

```cangjie
public func trimLeft(prefix: String): String
```

功能：去除前缀是 prefix 的字符串。

参数：

- prefix：若字符串的前缀是 prefix，则去除

返回值：转换后的新字符串

#### func trimRight

```cangjie
public func trimRight(suffix: String): String
```

功能：去除后缀是 suffix 的字符串。

参数：

- suffix：若字符串的后缀是 suffix，则去除

返回值：转换后的新字符串

#### func contains

```cangjie
public func contains(str: String): Bool
```

功能：判断原字符串中是否包含字符串 str。

参数：

- str：被判断的字符串，如果 str 字符串长度为 0，返回 true

返回值：如果字符串 str 在原字符串中，返回 true，否则返回 false

#### func startsWith

```cangjie
public func startsWith(prefix: String): Bool
```

功能：判断原字符串是否以 prefix 字符串为前缀开始。

参数：

- str：被判断的前缀字符串，当 str 长度为 0 时，返回 true

返回值：如果字符串 str 是原字符串的前缀，返回 true，否则返回 false

#### func endsWith

```cangjie
public func endsWith(suffix: String): Bool
```

功能：判断原字符串是否以 suffix 字符串为后缀结尾。

参数：

- str：被判断的后缀字符串，当 str 长度为 0 时，返回 true

返回值：如果字符串 str 是原字符串的后缀，返回 true，否则返回 false

#### func padLeft

```cangjie
public func padLeft(totalWidth: Int64, padding!: String = " "): String
```

功能：按指定长度右对齐原字符串。

参数：

- totalWidth：按指定长度 totalWidth 右对齐
- padding：当长度不够时，在左侧用指定的字符串 padding 进行填充

返回值：填充后的字符串，当指定长度小于字符串长度时，返回字符串本身，不会发生截断；当指定长度大于字符串长度时，在左侧添加 padding 字符串，当 padding 长度大于 1 时，返回字符串的长度可能大于指定长度

异常：

- IllegalArgumentException：如果 totalWidth 小于 0，抛出异常

#### func padRight

```cangjie
public func padRight(totalWidth: Int64, padding!: String = " "): String
```

功能：按指定长度左对齐原字符串。

参数：

- totalWidth：按指定长度 totalWidth 左对齐
- padding：当长度不够时，在右侧用指定的字符串 padding 进行填充

返回值：填充后的字符串，当指定长度小于字符串长度时，返回字符串本身，不会发生截断；当指定长度大于字符串长度时，在右侧添加 padding 字符串，当 padding 长度大于 1 时，返回字符串的长度可能大于指定长度

异常：

- IllegalArgumentException：如果 totalWidth 小于 0，抛出异常

#### func compare

```cangjie
public func compare(str: String): Ordering
```

功能：按字典序比较原字符串和 str 字符串，比较基于每个byte，按照UTF-8编码的byte进行比较。Ordering.GT 表示原字符串字典序大于 str 字符串，Ordering.LT 表示原字符串字典序小于 str 字符串，Ordering.EQ 表示两个字符串字典序相等。

参数：

- str：被比较的字符串

返回值：返回 enum 值 Ordering 表示结果，

异常：

- IllegalArgumentException：如果两个字符串的原始数据中存在无效的 UTF-8 编码，抛出异常

#### operator func ==

```cangjie
public operator func ==(right: String): Bool
```

功能：判断两个字符串是否相等。

返回值：相等返回 true，不相等返回 false

#### operator func !=

```cangjie
public operator func !=(right: String): Bool
```

功能：判断两个字符串是否不相等。

返回值：不相等返回 true，相等返回 false

#### operator func >

```cangjie
public operator func >(right: String): Bool
```

功能：判断两个字符串大小。

返回值：原字符串字典序大于 right 时，返回 true，否则返回 false

#### operator func >

```cangjie
public operator func >=(right: String): Bool
```

功能：判断两个字符串大小。

返回值：原字符串字典序大于或等于 right 时，返回 true，否则返回 false

#### operator func <

```cangjie
public operator func <(right: String): Bool
```

功能：判断两个字符串大小。

返回值：原字符串字典序小于 right 时，返回 true，否则返回 false

#### operator func <

```cangjie
public operator func <=(right: String): Bool
```

功能：判断两个字符串大小。

返回值：原字符串字典序小于或等于 right 时，返回 true，否则返回 false

#### operator func +

```cangjie
public operator func +(right: String): String
```

功能：两个字符串相加，将 right 字符串拼接在原字符串的末尾。

返回值：返回拼接后的字符串

#### operator func *

```cangjie
public operator func *(count: Int64): String
```

功能：原字符串重复 count 次。

返回值：返回重复 count 次后的新字符串

#### operator func []

```cangjie
public operator func [](index: Int64): Byte
```

功能：返回指定索引 index 处的 UTF-8 编码字节。

参数：

- index：要获取 UTF-8 编码字节的下标

返回值：获取得到下标对应的 UTF-8 编码字节

异常：

- IndexOutOfBoundsException：如果 index 小于 0 或大于等于字符串长度，抛出异常

#### operator func []

```cangjie
public operator func [](range: Range<Int64>): String
```

功能：获取切片后的字符串需要注意的是：如果参数 range 是使用 Range 构造函数构造的 Range 实例，有如下行为：1）start 的值就是构造函数传入的值本身，不受构造时传入的 hashStart 的值的影响2）hasEnd 为 false 时，该 Range 实例为开区间，不受构造时传入的 isClosed 的值的影响。

参数：

- range：切片的范围

返回值：新的字符串

异常：

- IndexOutOfBoundsException：如果切片范围超过原字符串边界，抛出异常
- IllegalArgumentException：如果 range.step 不等于 1，抛出异常
- IllegalArgumentException：如果范围起止点不是字符边界，抛出异常

#### func join

```cangjie
public static func join(strArray: Array<String>, delimiter!: String = String.empty): String
```

功能：连接字符串列表中的所有字符串。

参数：

- value：需要被连接的字符串数组，当数组为空时，返回空字符串
- delimiter：用于连接的中间字符串

返回值：连接后的新字符串

#### func rawData

```cangjie
public unsafe func rawData(): Array<Byte>
```

功能：返回字符串的 UTF-8 编码的原始字节数组，开发者如果对该数组修改会破坏字符串的并发安全

返回值：Byte 类型的 Array

#### func fromUtf8

```cangjie
public static func fromUtf8(utf8Data: Array<UInt8>): String
```

功能：根据 UTF-8 数组创建一个字符串。

参数：

- utf8Data：需要构造字符串的 UTF-8 数组

返回值：创建的字符串

异常：

- IllegalArgumentException：入参不符合 utf-8 序列规则，抛出异常

#### func fromUtf8Unchecked

```cangjie
public static unsafe func fromUtf8Unchecked(utf8Data: Array<UInt8>): String
```

功能：根据 UTF-8 数组创建一个字符串, 相较于 fromUtf8 函数，它并没有针对于字节数组进行 UTF-8 相关规则的检查，所以它所构建的字符串并不一定保证是合法的，甚至出现非预期的异常，如果不是某些场景下的速度考虑，请优先使用安全的 fromUtf8 函数。

参数：

- utf8Data：需要构造字符串的 UTF-8 数组

返回值：创建的字符串

### class StringBuilder

```cangjie
public class StringBuilder <: ToString {
    public init()
    public init(str: String)
    public init(r: Rune, n: Int64)
    public init(value: Array<Rune>)
    public init(capacity: Int64)
}
```

该类主要用于字符串的构建，其中实现了 `StringBuilder` 相关接口；`StringBuilder` 在字符串的构建上效率高于 `String`，当需要多种类型和多个值构建 `String` 时推荐使用 `StringBuilder`。

#### init

```cangjie
public init()
```

功能：构造一个初始容量为 32 的空 `StringBuilder` 实例。

#### init

```cangjie
public init(str: String)
```

功能：使用参数 `str` 指定的字符串初始化 `StringBuilder` 实例。

参数：

- str：初始化 `StringBuilder` 实例的字符串

#### init

```cangjie
public init(r: Rune, n: Int64)
```

功能：使用 `n` 个 `r` 字符初始化 `StringBuilder` 实例。

参数：

- r：初始化 `StringBuilder` 实例的字符
- n：字符 `r` 的数量

异常：

- IllegalArgumentException: 当参数 `n` 小于 0 时，抛出异常

#### init

```cangjie
public init(value: Array<Rune>)
```

功能：使用参数 `value` 指定的字符数组初始化一个 `StringBuilder` 实例。

参数：

- value：初始化 `StringBuilder` 实例的字符数组

#### init

```cangjie
public init(capacity: Int64)
```

功能：使用参数 `capacity` 指定的容量初始化一个空 `StringBuilder` 实例。

参数：

- capacity：初始化 `StringBuilder` 的字节容量

异常：

- IllegalArgumentException: 当参数 `capacity` 的值小于等于 0 时，抛出异常

#### prop size

```cangjie
public prop size: Int64
```

功能：返回 `StringBuilder` 实例中字符串 UTF-8 编码后的字节长度。

返回值 Int64 - `StringBuilder` 实例中字符串 UTF-8 编码后的字节长度

#### prop capacity

```cangjie
public prop capacity: Int64
```

功能：返回 `StringBuilder` 实例能容纳字符串 UTF-8 编码后的字节长度。

返回值 Int64 - `StringBuilder` 实例中能容纳字符串 UTF-8 编码后的字节长度

#### func reserve

```cangjie
public func reserve(additional: Int64): Unit
```

功能：将 `StringBuilder` 扩容 `additional` 大小。当 `additional` 小于等于零，或剩余容量大于等于 `additional` 时，不发生扩容；当剩余容量小于 `additional` 时，扩容至当前容量的 1.5 倍（向下取整）与 `size` + `additional` 的最大值。

参数：

- additional：指定 `StringBuilder` 的扩容大小

#### func reset

```cangjie
public func reset(capacity!: Option<Int64> = None): Unit
```

功能：清空当前 `StringBuilder`，并将容量重置为 `capacity` 指定的值。

参数：

- capacity：重置后 `StringBuilder` 实例的容量大小，默认值 `None` 表示采用默认大小容量（32）。

异常：

- IllegalArgumentException: 当参数 `capacity` 的值小于等于 0 时，抛出异常

#### func toString

```cangjie
public func toString(): String
```

功能：返回 `StringBuilder` 实例中的字符串。

返回值：`StringBuilder` 实例中的字符串

#### func append

```cangjie
public func append(r: Rune): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `r` 指定的字符。

参数：

- r：插入的字符

#### func append

```cangjie
public func append(str: String): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `str` 指定的字符串。

参数：

- str：插入的字符串

#### func append

```cangjie
public func append(sb: StringBuilder): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `sb` 指定的 `StringBuilder` 中的内容。

参数：

- sb：插入的 `StringBuilder` 实例

#### func append

```cangjie
public func append(runeArr: Array<Rune>): Unit
```

功能：在 `StringBuilder` 末尾插入一个 `Rune` 数组中所有字符。

参数：

- runeArr：插入的 `Rune` 数组

#### func append

```cangjie
public func append(cstr: CString): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `cstr` 指定 `CString` 中的内容。

参数：

- cstr：插入的 `CString`

#### func append

```cangjie
public func append<T>(v: T): Unit where T <: ToString
```

功能：在 `StringBuilder` 末尾插入参数 `v` 指定 `T` 类型的字符串表示，类型 `T` 需要实现 `ToString` 接口。

参数：

- v：插入的 `T` 类型实例

#### func append

```cangjie
public func append<T>(val: Array<T>): Unit where T <: ToString
```

功能：在 `StringBuilder` 末尾插入参数 `val` 指定的 `Array<T>` 的字符串表示，类型 `T` 需要实现 `ToString` 接口。

参数：

- val：插入的 `Array<T>` 类型实例

#### func append

```cangjie
public func append(b: Bool): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `b` 的字符串表示。

参数：

- b：插入的 `Bool` 类型的值，取值 "true" 或者 "false"

#### func append

```cangjie
public func append(n: Int64): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `Int64` 类型的值

#### func append

```cangjie
public func append(n: Int32): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `Int32` 类型的值

#### func append

```cangjie
public func append(n: Int16): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `Int16` 类型的值

#### func append

```cangjie
public func append(n: Int8): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `Int8` 类型的值

#### func append

```cangjie
public func append(n: UInt64): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `UInt64` 类型的值

#### func append

```cangjie
public func append(n: UInt32): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `UInt32` 类型的值

#### func append

```cangjie
public func append(n: UInt16): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `UInt16` 类型的值

#### func append

```cangjie
public func append(n: UInt8): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `UInt8` 类型的值

#### func append

```cangjie
public func append(n: Float64): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `Float64` 类型的值

#### func append

```cangjie
public func append(n: Float32): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `Float32` 类型的值

#### func append

```cangjie
public func append(n: Float16): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `n` 的字符串表示。

参数：

- n：插入的 `Float16` 类型的值

#### func appendFromUtf8

```cangjie
public func appendFromUtf8(arr: Array<Byte>): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `arr` 指定 utf8 编码的字节数组。

参数：

- arr：插入的 utf8 字节数组

异常：

- IllegalArgumentException：当字节数组不符合 utf8 编码规则时，抛出异常

#### func appendFromUtf8Unchecked

```cangjie
public unsafe func appendFromUtf8Unchecked(arr: Array<Byte>): Unit
```

功能：在 `StringBuilder` 末尾插入参数 `arr` 指定 utf8 编码的字节数组, 相较于 `appendFromUtf8` 函数，它并没有针对于字节数组进行 utf8 相关规则的检查，所以它所构建的字符串并不一定保证是合法的，甚至出现非预期的异常，如果不是某些场景下的速度考虑，请优先使用安全的 `appendFromUtf8` 函数。

参数：

- arr：插入的 utf8 字节数组

### enum AnnotationKind

```cangjie
public enum AnnotationKind {
    | Type
    | Parameter
    | Init
    | MemberProperty
    | MemberFunction
    | MemberVariable
}
```

枚举类型 `AnnotationKind` 表示自定义注解希望支持的位置。

#### Type

```cangjie
Type
```

功能：类型声明（class、struct、enum、interface）。

#### Parameter

```cangjie
Parameter
```

功能：成员函数/构造函数中的参数。

#### Init

```cangjie
Init
```

功能：构造函数声明。

#### MemberProperty

```cangjie
MemberProperty
```

功能：成员属性声明

#### MemberFunction

```cangjie
MemberFunction
```

功能：成员函数声明

#### MemberVariable

```cangjie
MemberVariable
```

功能：成员变量声明

### enum Endian

```cangjie
public enum Endian {
    | Big
    | Little
}
```

枚举类型 `Endian` 表示运行平台的端序，分为大端序和小端序。

#### Big

```cangjie
Big
```

功能：表示大端序。

#### Little

```cangjie
Little
```

功能：表示小端序。

#### public static prop Platform

```cangjie
public static prop Platform: Endian
```

功能：获取所在运行平台的端序。

返回值：

- 端序枚举。

异常：

- UnsupportedException：当所运行平台返回的端序无法识别时，抛出异常。

示例：

```cangjie
main() {
    let e = Endian.Platform
    match (e) {
        case Big => println("BigEndian")
        case Little => println("LittleEndian")
    }
}
```

### interface FloatToBits

```cangjie
public interface FloatToBits
```

### extend Float64 <: FloatToBits

#### func toBits()

```cangjie
public func toBits(): UInt64
```

功能：将指定的 Float64 数转换为以位表示的对应 UInt64 数。

返回值：UInt64 数，其值与 Float64 的位表示相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
 @Assert(12.5f64.toBits(), 0x4029000000000000)
}
```

#### static func fromBits(UInt64)

```cangjie
public static func fromBits(bits: UInt64): Float64
```

功能：将指定的 UInt64 数转换为 Float64 数。

参数：

- bits：要转换的数字。

返回值：Float64 数，其位与参数 bits 值相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    let v = Float64.fromBits(0x4029000000000000)
    @Assert(v, 12.5)
}
```

### extend Float32 <: FloatToBits

#### func toBits()

```cangjie
public func toBits(): UInt32
```

功能：将指定的 Float32 数转换为以位表示的对应 UInt32 数。

返回值：UInt32 数，其值与 Float32 的位表示相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
 @Assert(12.5f32.toBits(), 0x41480000)
}
```

#### static func fromBits(UInt32)

```cangjie
public static func fromBits(bits: UInt32): Float32
```

功能：将指定的 UInt32 数转换为 Float32 数。

参数：

- bits：要转换的数字。

返回值：Float32 数，其位与参数 bits 值相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    let v = Float32.fromBits(0x41480000)
    @Assert(v, 12.5)
}
```

### extend Float16 <: FloatToBits

#### func toBits()

```cangjie
public func toBits(): UInt16
```

功能：将指定的 Float16 数转换为以位表示的对应 UInt16 数。

返回值：UInt16 数，其值与 Float16 的位表示相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
 @Assert(12.5f16.toBits(), 0x4A40)
}
```

#### static func fromBits(UInt16)

```cangjie
public static func fromBits(bits: UInt16): Float16
```

功能：将指定的 UInt16 数转换为 Float16 数。

参数：

- bits：要转换的数字。

返回值：Float16 数，其位与参数 bits 值相同。

示例：

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

main() {
    let v = Float16.fromBits(0x4A40)
    @Assert(v, 12.5)
}
```

## 示例

### Future 的使用

主线程和新线程同时尝试打印一些文本。

代码如下：

```cangjie
import std.sync.sleep
import std.time.{Duration, DurationExtension}

main(): Int64 {
    spawn { =>
        for (i in 0..10) {
            println("New thread, number = ${i}")
            sleep(100 * Duration.millisecond) /* 睡眠 100 毫秒 */
        }
    }

    for (i in 0..5) {
        println("Main thread, number = ${i}")
        sleep(100 * Duration.millisecond) /* 睡眠 100 毫秒 */
    }
    return 0
}
```

运行结果如下：

```text
Main thread, number = 0
New thread, number = 0
Main thread, number = 1
New thread, number = 1
Main thread, number = 2
New thread, number = 2
Main thread, number = 3
New thread, number = 3
Main thread, number = 4
New thread, number = 4
New thread, number = 5
```

> **注意：**
>
> 上述打印信息仅做参考。

### Future 的 get 的使用

主线程等待创建线程执行完再执行。

代码如下：

```cangjie
import std.sync.sleep
import std.time.{Duration, DurationExtension}

main(): Int64 {
    let fut: Future<Unit> = spawn { =>
        for (i in 0..10) {
            println("New thread, number = ${i}")
            sleep(100 * Duration.millisecond) /* 睡眠 100 毫秒 */
        }
    }

    fut.get() /* 等待线程完成 */

    for (i in 0..5) {
        println("Main thread, number = ${i}")
        sleep(100 * Duration.millisecond) /* 睡眠 100 毫秒 */
    }
    return 0
}
```

运行结果如下：

```text
New thread, number = 0
New thread, number = 1
New thread, number = 2
New thread, number = 3
New thread, number = 4
New thread, number = 5
New thread, number = 6
New thread, number = 7
New thread, number = 8
New thread, number = 9
Main thread, number = 0
Main thread, number = 1
Main thread, number = 2
Main thread, number = 3
Main thread, number = 4
```

### 创建 Array 并取值

下面是创建 `Array`，使用下标取值的示例。

代码如下：

```cangjie
main() {
    var array: Array<Int64> = [1, 2, 3, 4, 5]
    println("array[1] = ${array[1]}")
    return 0
}
```

运行结果如下：

```text
array[1] = 2
```

### 创建 String 并访问每个字符

下面是创建 `String` 并且通过 `for-in` 访问每个 UTF-8 编码字节的示例。

代码如下：

```cangjie
main() {
    var str = "仓颉"    // E4BB93 E9A289
    for (c in str) {
        println(c)
    }
}
```

运行结果如下：

```text
228
187
147
233
162
137
```

### CString 与 C 代码交互

C 代码中分别提供两个函数： `getCString` 函数，用于返回一个 C 侧的字符串指针； `printCString` 函数，用于打印来自仓颉侧 CString 。

```c
#include <stdio.h>

char *str = "CString in C code.";

char *getCString() { return str; }

void printCString(char *s) { printf("%s\n", s); }
```

在仓颉代码中，创建一个 CString 对象，传递给 C 侧打印。并且获取 C 侧字符串，在仓颉侧打印：

```cangjie
foreign func getCString(): CString
foreign func printCString(s: CString): Unit

main() {
    // Construct by a Cangjie String.
    unsafe {
        let s: CString = LibC.mallocCString("CString in Cangjie code.")
        printCString(s)
        LibC.free(s)
    }

    unsafe {
        // Get a CString from C code and use `toString` convert to cangjie String.
        let cs = getCString()
        println(cs.toString())
    }

    // Use CStringResource by try-with-resource
    let cs = unsafe { LibC.mallocCString("CString in Cangjie code.") }
    try (csr = cs.asResource()) {
        unsafe { printCString(csr.value) }
    }

    0
}
```

示例输出：

```text
CString in Cangjie code.
CString in C code.
CString in Cangjie code.
```
