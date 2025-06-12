# BufferedOutputStream 示例

下面是 BufferedOutputStream 向流中写入数据示例。
<!-- verify -->

```cangjie
import std.io.*

main(): Unit {
    let arr1 = "01234".toArray()
    let byteArrayStream = ByteArrayStream()
    byteArrayStream.write(arr1)
    let bufferedInputStream = BufferedOutputStream(byteArrayStream)
    let arr2 = "56789".toArray()

    /* 向流中写入数据，此时数据在外部流的缓冲区中 */
    bufferedInputStream.write(arr2)

    /* 调用 flush 函数，真正将数据写入内部流中 */
    bufferedInputStream.flush()
    println(String.fromUtf8(byteArrayStream.readToEnd()))
}
```

运行结果

```text
0123456789
```
