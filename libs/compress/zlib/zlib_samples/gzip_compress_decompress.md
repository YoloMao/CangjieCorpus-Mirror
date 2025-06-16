# Gzip 格式数据的压缩和解压
<!-- verify -->

```cangjie
import compress.zlib.*
import std.fs.*

main() {
    var arr: Array<Byte> = Array<Byte>(1024 * 1024, {i => UInt8(i % 256)})
    File.writeTo("./zlib.txt", arr, openOption: Create(false))

    if (compressFile("./zlib.txt", "./zlib_copmressed.zlib") <= 0) {
        println("Failed to compress file!")
    }

    if (decompressFile("./zlib_copmressed.zlib", "./zlib_decopmressed.txt") != arr.size) {
        println("Failed to decompress file!")
    }

    if (compareFile("./zlib.txt", "./zlib_decopmressed.txt")) {
        println("success")
    } else {
        println("failed")
    }

    File.delete("./zlib.txt")
    File.delete("./zlib_copmressed.zlib")
    File.delete("./zlib_decopmressed.txt")
    return 0
}

func compressFile(srcFileName: String, destFileName: String): Int64 {
    var count: Int64 = 0
    var srcFile: File = File(srcFileName, OpenOption.Open(true, false))
    var destFile: File = File(destFileName, OpenOption.Create(false))

    var tempBuf: Array<UInt8> = Array<UInt8>(1024, item: 0)
    var compressOutputStream: CompressOutputStream = CompressOutputStream(destFile, wrap: GzipFormat, bufLen: 10000)
    while (true) {
        var readNum = srcFile.read(tempBuf)
        if (readNum > 0) {
            compressOutputStream.write(tempBuf.slice(0, readNum).toArray())
            count += readNum
        } else {
            break
        }
    }
    compressOutputStream.flush()
    compressOutputStream.close()

    srcFile.close()
    destFile.close()
    return count
}

func decompressFile(srcFileName: String, destFileName: String): Int64 {
    var count: Int64 = 0
    var srcFile: File = File(srcFileName, OpenOption.Open(true, false))
    var destFile: File = File(destFileName, OpenOption.Create(false))

    var tempBuf: Array<UInt8> = Array<UInt8>(1024, item: 0)
    var decompressInputStream: DecompressInputStream = DecompressInputStream(srcFile, wrap: GzipFormat, bufLen: 10000)
    while (true) {
        var readNum = decompressInputStream.read(tempBuf)
        if (readNum <= 0) {
            break
        }
        destFile.write(tempBuf.slice(0, readNum).toArray())
        count += readNum
    }
    decompressInputStream.close()

    srcFile.close()
    destFile.close()
    return count
}

func compareFile(fileName1: String, fileName2: String): Bool {
    return File.readFrom(fileName1) == File.readFrom(fileName2)
}
```

运行结果：

```text
success
```
