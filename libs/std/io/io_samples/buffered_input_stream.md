# BufferedInputStream 示例

下面是 BufferedInputStream 从流中读取数据示例。
<!-- verify -->

```cangjie
import std.io.*

main(): Unit {
    let arr1 = "0123456789".toArray()
    let byteArrayStream = ByteArrayStream()
    byteArrayStream.write(arr1)
    let bufferedInputStream = BufferedInputStream(byteArrayStream)
    let arr2 = Array<Byte>(20, item: 0)

    /* 读取流中数据，返回读取到的数据的长度 */
    let readLen = bufferedInputStream.read(arr2)
    println(String.fromUtf8(arr2[..readLen]))
}
```

运行结果

```text
0123456789
```
