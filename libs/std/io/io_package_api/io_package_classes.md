# 类

## class BufferedInputStream\<T> where T <: InputStream

```cangjie
public class BufferedInputStream<T> <: InputStream where T <: InputStream {
    public init(input: T)
    public init(input: T, buffer: Array<Byte>)
    public init(input: T, capacity: Int64)
}
```

功能：提供带缓冲区的输入流。

可将其他 [InputStream](io_package_interfaces.md#interface-inputstream) 类型的输入流（如 [ByteArrayStream](io_package_classes.md#class-bytearraystream)）绑定到 [BufferedInputStream](io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 实例，从该实例读取数据时，先把数据从被绑定的流读入缓冲区暂存，再从缓冲区读取用户需要的数据。

父类型：

- [InputStream](io_package_interfaces.md#interface-inputstream)

### init(T)

```cangjie
public init(input: T)
```

功能：创建 [BufferedInputStream](io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 实例，缓冲区容量取默认值 4096。

参数：

- input: T - 绑定指定输入流。

### init(T, Array\<Byte>)

```cangjie
public init(input: T, buffer: Array<Byte>)
```

功能：创建 [BufferedInputStream](io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 实例。

其内部使用的缓存区由入参决定，在注重性能的场景下，通过复用传入的 `buffer`，可以减少内存分配次数，提高性能。

参数：

- input: T - 绑定一个输入流。
- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - [BufferedInputStream](io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 使用的内部缓存区。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 buffer 大小等于 0 时，抛出异常。

### init(T, Int64)

```cangjie
public init(input: T, capacity: Int64)
```

功能：创建 [BufferedInputStream](io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 实例。

参数：

- input: T - 绑定指定输入流。
- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 内部缓冲区容量。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 capacity 小于等于 0 时，抛出异常。

### func read(Array\<Byte>)

```cangjie
public func read(buffer: Array<Byte>): Int64
```

功能：从绑定的输入流读出数据到 `buffer` 中。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存放读取的数据的缓冲区。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 读取数据的字节数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 buffer 为空时，抛出异常。

### func reset(T)

```cangjie
public func reset(input: T): Unit
```

功能：绑定新的输入流，重置状态，但不重置 `capacity`。

参数：

- input: T - 待绑定的输入流。

### extend\<T> BufferedInputStream\<T> <: Resource where T <: Resource

```cangjie
extend<T> BufferedInputStream<T> <: Resource where T <: Resource
```

功能：为 [BufferedInputStream](./io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 实现 [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource) 接口，该类型对象可在 `try-with-resource` 语法上下文中实现自动资源释放。

父类型：

- [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource)

#### func close()

```cangjie
public func close(): Unit
```

功能：关闭当前流。

> **注意：**
>
> - 调用此方法后不可再调用 [BufferedInputStream](io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 的其他接口，否则会造成不可期现象。

#### func isClosed()

```cangjie
public func isClosed(): Bool
```

功能：判断当前流是否关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果当前流已经被关闭，返回 true，否则返回 false。

### extend\<T> BufferedInputStream\<T> <: Seekable where T <: Seekable

```cangjie
extend<T> BufferedInputStream<T> <: Seekable where T <: Seekable
```

功能：为 [BufferedInputStream](./io_package_classes.md#class-bufferedinputstreamt-where-t--inputstream) 实现 [Seekable](./io_package_interfaces.md#interface-seekable) 接口，支持查询数据长度，移动光标等操作。

父类型：

- [Seekable](io_package_interfaces.md#interface-seekable)

#### prop length

```cangjie
public prop length: Int64
```

功能：返回当前流中的总数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop position

```cangjie
public prop position: Int64
```

功能：返回当前光标位置。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop remainLength

```cangjie
public prop remainLength: Int64
```

功能：返回当前流中未读的数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### func seek(SeekPosition)

```cangjie
public func seek(sp: SeekPosition): Int64
```

功能：移动光标到指定的位置。

> **说明：**
>
> - 指定的位置不能位于流中数据头部之前。
> - 指定位置可以超过流中数据末尾。
> - 调用该函数会先清空缓存区，再移动光标的位置。

参数：

- sp: [SeekPosition](io_package_enums.md#enum-seekposition) - 指定光标移动后的位置。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 返回流中数据的起点到移动后位置的偏移量（以字节为单位）。

## class BufferedOutputStream\<T> where T <: OutputStream

```cangjie
public class BufferedOutputStream<T> <: OutputStream where T <: OutputStream {
    public init(output: T)
    public init(output: T, buffer: Array<Byte>)
    public init(output: T, capacity: Int64)
}
```

功能：提供带缓冲区的输出流。

可将其他 [OutputStream](io_package_interfaces.md#interface-outputstream) 类型的输入流（如 [ByteArrayStream](io_package_classes.md#class-bytearraystream)）绑定到 [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 实例，从该实例写入数据时，先把数据写入缓冲区暂存，再从缓冲区写入数据到流中。

父类型：

- [OutputStream](io_package_interfaces.md#interface-outputstream)

### init(T)

```cangjie
public init(output: T)
```

功能：创建 [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 实例，缓冲区容量取默认值 4096。

参数：

- output: T - 绑定指定输出流。

### init(T, Array\<Byte>)

```cangjie
public init(output: T, buffer: Array<Byte>)
```

功能：创建 [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 实例。

其内部使用的缓存区由入参决定，在注重性能的场景下，通过复用传入的 `buffer`，可以减少内存分配次数，提高性能。

参数：

- output: T - 绑定一个输出流。
- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 使用的内部缓存区。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 buffer 大小等于 0 时，抛出异常。

### init(T, Int64)

```cangjie
public init(output: T, capacity: Int64)
```

功能：创建 [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 实例。

参数：

- output: T - 绑定指定输出流。
- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 内部缓冲区容量。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 capacity 小于等于 0 时，抛出异常。

### func flush()

```cangjie
public func flush(): Unit
```

功能：刷新 [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream)：将内部缓冲区的剩余数据写入绑定的输出流，并刷新 [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream)。

### func reset(T)

```cangjie
public func reset(output: T): Unit
```

功能：绑定新的输出流，重置状态，但不重置 `capacity`。

参数：

- output: T - 待绑定的输出流。

### func write(Array\<Byte>)

```cangjie
public func write(buffer: Array<Byte>): Unit
```

功能：将 `buffer` 中的数据写入到绑定的输出流中。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 待写入数据的缓冲区。

### extend\<T> BufferedOutputStream\<T> <: Resource where T <: Resource

```cangjie
extend<T> BufferedOutputStream<T> <: Resource where T <: Resource
```

功能：为 [BufferedOutputStream](./io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 实现 [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource) 接口，该类型对象可在 `try-with-resource` 语法上下文中实现自动资源释放。

父类型：

- [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource)

#### func close()

```cangjie
public func close(): Unit
```

功能：关闭当前流。

> **注意：**
>
> - 调用此方法后不可再调用 [BufferedOutputStream](io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 的其他接口，否则会造成不可期现象。

#### func isClosed()

```cangjie
public func isClosed(): Bool
```

功能：判断当前流是否关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果当前流已经被关闭，返回 true，否则返回 false。

### extend\<T> BufferedOutputStream\<T> <: Seekable where T <: Seekable

```cangjie
extend<T> BufferedOutputStream<T> <: Seekable where T <: Seekable
```

功能：为 [BufferedOutputStream](./io_package_classes.md#class-bufferedoutputstreamt-where-t--outputstream) 实现 [Seekable](./io_package_interfaces.md#interface-seekable) 接口，支持查询数据长度，移动光标等操作。

父类型：

- [Seekable](io_package_interfaces.md#interface-seekable)

#### prop length

```cangjie
public prop length: Int64
```

功能：返回当前流中的总数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop position

```cangjie
public prop position: Int64
```

功能：返回当前光标位置。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop remainLength

```cangjie
public prop remainLength: Int64
```

功能：返回当前流中未读的数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### func seek(SeekPosition)

```cangjie
public func seek(sp: SeekPosition): Int64
```

功能：移动光标到指定的位置。

> **说明：**
>
> - 指定的位置不能位于流中数据头部之前。
> - 指定位置可以超过流中数据末尾。
> - 调用该函数会先将缓存区内的数据写到绑定的输出流里，再移动光标的位置。

参数：

- sp: [SeekPosition](io_package_enums.md#enum-seekposition) - 指定光标移动后的位置。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 返回流中数据的起点到移动后位置的偏移量（以字节为单位）。

## class ByteArrayStream

```cangjie
public class ByteArrayStream <: IOStream & Seekable {
    public init()
    public init(capacity: Int64)
}
```

功能：基于 [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> 数据类型，提供对字节流的写入、读取等操作。

父类型：

- [IOStream](io_package_interfaces.md#interface-iostream)
- [Seekable](io_package_interfaces.md#interface-seekable)

### prop length

```cangjie
public prop length: Int64
```

功能：返回当前流中的总数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop position

```cangjie
public prop position: Int64
```

功能：获取当前光标位置。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop remainLength

```cangjie
public prop remainLength: Int64
```

功能：获取当前流中未读的数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### init()

```cangjie
public init()
```

功能：创建 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 实例，默认的初始容量是 32。

### init(Int64)

```cangjie
public init(capacity: Int64)
```

功能：创建 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 实例。

参数：

- capacity: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 指定的初始容量。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 capacity 小于 0 时，抛出异常。

### static func fromString(String)

```cangjie
public static func fromString(data: String): ByteArrayStream
```

功能：通过 [String](../../core/core_package_api/core_package_structs.md#struct-string) 类型构造一个 [ByteArrayStream](io_package_classes.md#class-bytearraystream)。

参数：

- data: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 构造一个新 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 的初始数据。

返回值：

- [ByteArrayStream](io_package_classes.md#class-bytearraystream) - 由 data 构造的 [ByteArrayStream](io_package_classes.md#class-bytearraystream)。

### func bytes()

```cangjie
public func bytes(): Array<Byte>
```

功能：获取当前 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 中未被读取的数据的切片。

> **注意：**
>
> - 缓冲区进行读取，写入或重置等修改操作会导致这个切片失效。
> - 对切片的修改会影响缓冲区的内容。

返回值：

- [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 当前流中未被读取的数据的切片。

### func capacity()

```cangjie
public func capacity(): Int64
```

功能：获取当前缓冲区容量。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前缓冲区容量。

### func clear()

```cangjie
public func clear(): Unit
```

功能：清除当前 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 中所有数据。

### func clone()

```cangjie
public func clone(): ByteArrayStream
```

功能：用当前 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 中的数据来构造一个新的 [ByteArrayStream](io_package_classes.md#class-bytearraystream)。

返回值：

- [ByteArrayStream](io_package_classes.md#class-bytearraystream) - 新构造的 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 对象。

### func copyTo(OutputStream)

```cangjie
public func copyTo(output: OutputStream): Unit
```

功能：将当前 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 中未被读取的所有数据拷贝到 output 流中。

参数：

- output: [OutputStream](io_package_interfaces.md#interface-outputstream) - 数据将要拷贝到的流。

### func read(Array\<Byte>)

```cangjie
public func read(buffer: Array<Byte>): Int64
```

功能：从输入流中读取数据放到 buffer 中。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存放读取的数据的缓冲区。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 读取数据的字节数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 buffer 为空时，抛出异常。

### func readString()

```cangjie
public func readString(): String
```

功能：读取流中的剩余数据，并转换为 [String](../../core/core_package_api/core_package_structs.md#struct-string) 类型，做 UTF-8 编码检查。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 流中剩余字节组成的 [String](../../core/core_package_api/core_package_structs.md#struct-string)。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当剩余字节不符合 UTF-8 编码规则时，抛出异常。

### func readStringUnchecked()

```cangjie
public unsafe func readStringUnchecked(): String
```

功能：读取流中的剩余数据，并转换为 [String](../../core/core_package_api/core_package_structs.md#struct-string) 类型，不做 UTF-8 编码检查。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 流中剩余字节组成的 [String](../../core/core_package_api/core_package_structs.md#struct-string)。

### func readToEnd()

```cangjie
public func readToEnd(): Array<Byte>
```

功能：获取当前 [ByteArrayStream](io_package_classes.md#class-bytearraystream) 中未被读取的数据。

返回值：

- [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 未被读取的数据的拷贝。

### func reserve(Int64)

```cangjie
public func reserve(additional: Int64): Unit
```

功能：将缓冲区扩容指定大小。

> **说明：**
>
> - 当缓冲区剩余字节数大于等于 `additional` 时不发生扩容。
> - 当缓冲区剩余字节数量小于 `additional` 时，取（`additional` + `capacity`）与（`capacity`的1.5倍向下取整）两个值中的最大值进行扩容。

参数：

- additional: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 将要扩容的大小。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 additional 小于 0 时，抛出异常。
- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当扩容后的缓冲区大小超过 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 的最大值时，抛出异常。

### func seek(SeekPosition)

```cangjie
public func seek(sp: SeekPosition): Int64
```

功能：将光标跳转到指定位置。

> **说明：**
>
> - 指定的位置不能位于流中数据头部之前。
> - 指定位置可以超过流中数据末尾。

参数：

- sp: [SeekPosition](io_package_enums.md#enum-seekposition) - 指定光标跳转后的位置。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 流中数据的头部到跳转后位置的偏移量（以字节为单位）。

异常：

- [IOException](io_package_exceptions.md#class-ioexception) - 当指定的位置位于流中数据头部之前时，抛出异常。

### func write(Array\<Byte>)

```cangjie
public func write(buffer: Array<Byte>): Unit
```

功能：将 `buffer` 中的数据写入到输出流中。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 待写入数据的缓冲区。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当数据写入失败或者只写入了部分数据时，抛出异常。

## class ChainedInputStream\<T> where T <: InputStream

```cangjie
public class ChainedInputStream<T> <: InputStream where T <: InputStream {
    public init(input: Array<T>)
}
```

功能：提供顺序从 [InputStream](io_package_interfaces.md#interface-inputstream) 数组中读取数据的能力。

父类型：

- [InputStream](io_package_interfaces.md#interface-inputstream)

### init(Array\<T>)

```cangjie
public init(input: Array<T>)
```

功能：创建 [ChainedInputStream](io_package_classes.md#class-chainedinputstreamt-where-t--inputstream) 实例。

参数：

- input: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<T> - 绑定指定输入流数组。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 input 为空时，抛出异常。

### func read(Array\<Byte>)

```cangjie
public func read(buffer: Array<Byte>): Int64
```

功能：依次从绑定 [InputStream](io_package_interfaces.md#interface-inputstream) 数组中读出数据到 buffer 中。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储读出数据的缓冲区。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 读取字节数。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 buffer 为空时，抛出异常。

## class MultiOutputStream\<T> where T <: OutputStream

```cangjie
public class MultiOutputStream<T> <: OutputStream where T <: OutputStream {
    public init(output: Array<T>)
}
```

功能：提供将数据同时写入到 [OutputStream](io_package_interfaces.md#interface-outputstream) 数组中每个输出流中的能力。

父类型：

- [OutputStream](io_package_interfaces.md#interface-outputstream)

### init(Array\<T>)

```cangjie
public init(output: Array<T>)
```

功能：创建 [MultiOutputStream](io_package_classes.md#class-multioutputstreamt-where-t--outputstream) 实例。

参数：

- output: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<T> - 绑定指定输出流数组。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 output 为空时，抛出异常。

### func flush()

```cangjie
public func flush(): Unit
```

功能：刷新绑定的输出流数组里的每个输出流。

### func write(Array\<Byte>)

```cangjie
public func write(buffer: Array<Byte>): Unit
```

功能：将 buffer 同时写入到绑定的 [OutputStream](io_package_interfaces.md#interface-outputstream) 数组里的每个输出流中。

参数：

- buffer: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[Byte](../../core/core_package_api/core_package_types.md#type-byte)> - 存储待写入数据的缓冲区。

## class StringReader\<T> where T <: InputStream

```cangjie
public class StringReader<T> where T <: InputStream {
    public init(input: T)
}
```

功能：提供从 [InputStream](io_package_interfaces.md#interface-inputstream) 输入流中读出数据并转换成字符或字符串的能力。

> **说明：**
>
> - [StringReader](io_package_classes.md#class-stringreadert-where-t--inputstream) 内部默认有缓冲区，缓冲区容量 4096 个字节。
> - [StringReader](io_package_classes.md#class-stringreadert-where-t--inputstream) 目前仅支持 UTF-8 编码，暂不支持 UTF-16、UTF-32。

### init(T)

```cangjie
public init(input: T)
```

功能：创建 [StringReader](io_package_classes.md#class-stringreadert-where-t--inputstream) 实例。

参数：

- input: T - 待读取数据的输入流。

### func lines()

```cangjie
public func lines(): Iterator<String>
```

功能：获得 [StringReader](io_package_classes.md#class-stringreadert-where-t--inputstream) 的行迭代器。

相当于循环调用 `func readln()`，内部遇到非法字符时也会抛出异常。

> **说明：**
>
> - 每行都由换行符进行分隔。
> - 换行符是 `\n` `\r` `\r\n` 之一。
> - 每行不包括换行符。

返回值：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 字符串的行迭代器。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当`for-in`或者调用`next()`方法时读取到非法字符，抛出异常。

### func read()

```cangjie
public func read(): ?Rune
```

功能：按字符读取流中的数据。

返回值：

- ?[Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) - 读取成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune)>.Some(c)，c 为该次读出的字符；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune)>.None。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当读取到非法字符时，抛出异常。

### func readToEnd()

```cangjie
public func readToEnd(): String
```

功能：读取流中所有剩余数据。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 流中所有剩余数据。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当读取到非法字符时，抛出异常。

### func readUntil((Rune)->Bool)

```cangjie
public func readUntil(predicate: (Rune)->Bool): Option<String>
```

功能：从流内读取到使 `predicate` 返回 true 的字符位置（包含这个字符）或者流结束位置的数据。

参数：

- predicate: ([Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune))->Bool - 满足一定条件返回 `true` 的表达式。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 读取成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.Some(str)，str 为该次读出的字符串；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.None。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当读取到非法字符时，抛出异常。

### func readUntil(Rune)

```cangjie
public func readUntil(v: Rune): Option<String>
```

功能：从流内读取到指定字符（包含指定字符）或者流结束位置的数据。

参数：

- v: [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) - 指定字符。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 读取成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.Some(str)，str 为该次读出的字符串；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.None。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当读取到非法字符时，抛出异常。

### func readln()

```cangjie
public func readln(): Option<String>
```

功能：按行读取流中的数据。

> **说明：**
>
> - 读取的数据会去掉原换行符。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 读取成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.Some(str)，str 为该次读出的字符串；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.None。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当读取到非法字符时，抛出异常。

### func runes()

```cangjie
public func runes(): Iterator<Rune>
```

功能：获得 [StringReader](io_package_classes.md#class-stringreadert-where-t--inputstream) 的 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 迭代器。

返回值：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort)\<[Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune)> - 字符串的 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 迭代器。

异常：

- [ContentFormatException](io_package_exceptions.md#class-contentformatexception) - 当`for-in`或者调用`next()`方法时读取到非法字符，抛出异常。

### extend\<T> StringReader\<T> <: Resource where T <: Resource

```cangjie
extend<T> StringReader<T> <: Resource where T <: Resource
```

功能：为 [StringReader](./io_package_classes.md#class-stringreadert-where-t--inputstream) 实现 [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource) 接口，该类型对象可在 `try-with-resource` 语法上下文中实现自动资源释放。

父类型：

- [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource)

#### func close()

```cangjie
public func close(): Unit
```

功能：关闭当前流。

> **注意：**
>
> - 调用此方法后不可再调用 [StringReader](io_package_classes.md#class-stringreadert-where-t--inputstream) 的其他接口，否则会造成不可期现象。

#### func isClosed()

```cangjie
public func isClosed(): Bool
```

功能：判断当前流是否关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果当前流已经被关闭，返回 true，否则返回 false。

### extend\<T> StringReader\<T> <: Seekable where T <: Seekable

```cangjie
extend<T> StringReader<T> <: Seekable where T <: Seekable
```

功能：为 [StringReader](./io_package_classes.md#class-stringreadert-where-t--inputstream) 实现 [Seekable](./io_package_interfaces.md#interface-seekable) 接口，支持查询数据长度，移动光标等操作。

父类型：

- [Seekable](io_package_interfaces.md#interface-seekable)

#### prop length

```cangjie
public prop length: Int64
```

功能：返回当前流中的总数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop position

```cangjie
public prop position: Int64
```

功能：返回当前光标位置。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop remainLength

```cangjie
public prop remainLength: Int64
```

功能：返回当前流中未读的数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### func seek(SeekPosition)

```cangjie
public func seek(sp: SeekPosition): Int64
```

功能：移动光标到指定的位置。

> **说明：**
>
> - 指定的位置不能位于流中数据头部之前。
> - 指定位置可以超过流中数据末尾。

参数：

- sp: [SeekPosition](io_package_enums.md#enum-seekposition) - 指定光标移动后的位置。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 返回流中数据的起点到移动后位置的偏移量（以字节为单位）。

## class StringWriter\<T> where T <: OutputStream

```cangjie
public class StringWriter<T> where T <: OutputStream {
    public init(output: T)
}
```

功能：提供将 [String](../../core/core_package_api/core_package_structs.md#struct-string) 以及一些 [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring) 类型转换成指定编码格式和字节序配置的字符串并写入到输出流的能力。

> **说明：**
>
> - [StringWriter](io_package_classes.md#class-stringwritert-where-t--outputstream) 内部默认有缓冲区，缓冲区容量 4096 个字节。
> - [StringWriter](io_package_classes.md#class-stringwritert-where-t--outputstream) 目前仅支持 UTF-8 编码，暂不支持 UTF-16、UTF-32。

### init(T)

```cangjie
public init(output: T)
```

功能：创建 [StringWriter](io_package_classes.md#class-stringwritert-where-t--outputstream) 实例。

参数：

- output: T - 待写入数据的输出流。

### func flush()

```cangjie
public func flush(): Unit
```

功能：刷新内部缓冲区，将缓冲区数据写入 output 中，并刷新 output。

### func write(Bool)

```cangjie
public func write(v: Bool): Unit
```

功能：写入 [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) 类型。

参数：

- v: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) 类型的实例。

### func write(Float16)

```cangjie
public func write(v: Float16): Unit
```

功能：写入 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型。

参数：

- v: [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的实例。

### func write(Float32)

```cangjie
public func write(v: Float32): Unit
```

功能：写入 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型。

参数：

- v: [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的实例。

### func write(Float64)

```cangjie
public func write(v: Float64): Unit
```

功能：写入 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型。

参数：

- v: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的实例。

### func write(Int16)

```cangjie
public func write(v: Int16): Unit
```

功能：写入 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型。

参数：

- v: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型的实例。

### func write(Int32)

```cangjie
public func write(v: Int32): Unit
```

功能：写入 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型。

参数：

- v: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型的实例。

### func write(Int64)

```cangjie
public func write(v: Int64): Unit
```

功能：写入 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型。

参数：

- v: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的实例。

### func write(Int8)

```cangjie
public func write(v: Int8): Unit
```

功能：写入 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型。

参数：

- v: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的实例。

### func write(Rune)

```cangjie
public func write(v: Rune): Unit
```

功能：写入 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型。

参数：

- v: [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) - [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型的实例。

### func write(String)

```cangjie
public func write(v: String): Unit
```

功能：写入字符串。

参数：

- v: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 待写入的字符串。

### func write(UInt16)

```cangjie
public func write(v: UInt16): Unit
```

功能：写入 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型。

参数：

- v: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型的实例。

### func write(UInt32)

```cangjie
public func write(v: UInt32): Unit
```

功能：写入 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型。

参数：

- v: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型的实例。

### func write(UInt64)

```cangjie
public func write(v: UInt64): Unit
```

功能：写入 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型。

参数：

- v: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型的实例。

### func write(UInt8)

```cangjie
public func write(v: UInt8): Unit
```

功能：写入 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型。

参数：

- v: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型的实例。

### func write\<T>(T) where T <: ToString

```cangjie
public func write<T>(v: T): Unit where T <: ToString
```

功能：写入 [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring) 类型。

参数：

- v: T - [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring) 类型的实例。

### func writeln()

```cangjie
public func writeln(): Unit
```

功能：写入换行符。

### func writeln(Bool)

```cangjie
public func writeln(v: Bool): Unit
```

功能：写入 [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) 类型 + 换行符。

参数：

- v: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) 类型的实例。

### func writeln(Float16)

```cangjie
public func writeln(v: Float16): Unit
```

功能：写入 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型 + 换行符。

参数：

- v: [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) - [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 类型的实例。

### func writeln(Float32)

```cangjie
public func writeln(v: Float32): Unit
```

功能：写入 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型 + 换行符。

参数：

- v: [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) - [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 类型的实例。

### func writeln(Float64)

```cangjie
public func writeln(v: Float64): Unit
```

功能：写入 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型 + 换行符。

参数：

- v: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的实例。

### func writeln(Int16)

```cangjie
public func writeln(v: Int16): Unit
```

功能：写入 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型 + 换行符。

参数：

- v: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 类型的实例。

### func writeln(Int32)

```cangjie
public func writeln(v: Int32): Unit
```

功能：写入 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型 + 换行符。

参数：

- v: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 类型的实例。

### func writeln(Int64)

```cangjie
public func writeln(v: Int64): Unit
```

功能：写入 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型 + 换行符。

参数：

- v: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的实例。

### func writeln(Int8)

```cangjie
public func writeln(v: Int8): Unit
```

功能：写入 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型 + 换行符。

参数：

- v: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的实例。

### func writeln(Rune)

```cangjie
public func writeln(v: Rune): Unit
```

功能：写入 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型 + 换行符。

参数：

- v: [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) - [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型的实例。

### func writeln(String)

```cangjie
public func writeln(v: String): Unit
```

功能：写入字符串 + 换行符。

参数：

- v: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 待写入的字符串。

### func writeln(UInt16)

```cangjie
public func writeln(v: UInt16): Unit
```

功能：写入 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型 + 换行符。

参数：

- v: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 类型的实例。

### func writeln(UInt32)

```cangjie
public func writeln(v: UInt32): Unit
```

功能：写入 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型 + 换行符。

参数：

- v: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 类型的实例。

### func writeln(UInt64)

```cangjie
public func writeln(v: UInt64): Unit
```

功能：写入 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型 + 换行符。

参数：

- v: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 类型的实例。

### func writeln(UInt8)

```cangjie
public func writeln(v: UInt8): Unit
```

功能：写入 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型 + 换行符。

参数：

- v: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 类型的实例。

### func writeln\<T>(T) where T <: ToString

```cangjie
public func writeln<T>(v: T): Unit where T <: ToString
```

功能：写入 [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring) 类型 + 换行符。

参数：

- v: T - [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring) 类型的实例。

### extend\<T> StringWriter\<T> <: Resource where T <: Resource

```cangjie
extend<T> StringWriter<T> <: Resource where T <: Resource
```

功能：为 [StringWriter](./io_package_classes.md#class-stringwritert-where-t--outputstream) 实现 [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource) 接口，该类型对象可在 `try-with-resource` 语法上下文中实现自动资源释放。

父类型：

- [Resource](../../core/core_package_api/core_package_interfaces.md#interface-resource)

#### func close()

```cangjie
public func close(): Unit
```

功能：关闭当前流。

> **注意：**
>
> - 调用此方法后不可再调用 [StringWriter](io_package_classes.md#class-stringwritert-where-t--outputstream) 的其他接口，否则会造成不可期现象。

#### func isClosed()

```cangjie
public func isClosed(): Bool
```

功能：判断当前流是否关闭。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果当前流已经被关闭，返回 true，否则返回 false。

### extend\<T> StringWriter\<T> <: Seekable where T <: Seekable

```cangjie
extend<T> StringWriter<T> <: Seekable where T <: Seekable
```

功能：为 [StringWriter](./io_package_classes.md#class-stringwritert-where-t--outputstream) 实现 [Seekable](./io_package_interfaces.md#interface-seekable) 接口，支持查询数据长度，移动光标等操作。

父类型：

- [Seekable](io_package_interfaces.md#interface-seekable)

#### prop length

```cangjie
public prop length: Int64
```

功能：返回当前流中的总数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop position

```cangjie
public prop position: Int64
```

功能：返回当前光标位置。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### prop remainLength

```cangjie
public prop remainLength: Int64
```

功能：返回当前流中未读的数据量。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### func seek(SeekPosition)

```cangjie
public func seek(sp: SeekPosition): Int64
```

功能：移动光标到指定的位置。

> **说明：**
>
> - 指定的位置不能位于流中数据头部之前。
> - 指定位置可以超过流中数据末尾。

参数：

- sp: [SeekPosition](io_package_enums.md#enum-seekposition) - 指定光标移动后的位置。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 返回流中数据的起点到移动后位置的偏移量（以字节为单位）。
