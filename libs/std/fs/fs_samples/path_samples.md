# Path 示例

## 不同 Path 实例的属性信息展示

打印 Path 实例的目录部分、文件全名（有扩展名）、扩展名、文件名（无扩展名），并判断 Path 实例是绝对路径还是相对路径

代码如下：
<!-- verify -->

```cangjie
import std.fs.Path

main() {
    let pathStrArr: Array<String> = [
        // 绝对路径
        "/a/b/c",
        "/a/b/",
        "/a/b/c.cj",
        "/a",
        "/",
        // 相对路径
        "./a/b/c",
        "./a/b/",
        "./a/b/c.cj",
        "./",
        ".",
        "123."
    ]

    for (i in 0..pathStrArr.size) {
        let path: Path = Path(pathStrArr[i])
        // 打印 path 的整个路径字符串
        println("Path${i}: ${path.toString()}")
        // 打印 path 的目录路径
        println("Path.directoryName: ${path.directoryName}")
        // 打印 path 的文件全名（有扩展名）
        println("Path.fileName: ${path.fileName}")
        // 打印 path 的扩展名
        println("Path.extensionName: ${path.extensionName}")
        // 打印 path 的文件名（无扩展名）
        println("Path.fileNameWithoutExtension: ${path.fileNameWithoutExtension}")
        // 打印 path 的拆分成的目录路径和文件全名
        var (directoryName, fileName): (Option<Path>, Option<String>) = path.split()
        println("Path.split: (${directoryName}, ${fileName})")
        // 打印 path 是否是绝对路径、相对路径
        println("Path.isAbsolute: ${path.isAbsolute()}; Path.isRelative: ${path.isRelative()}")
        println()
    }

    return 0
}
```

运行结果如下：

```text
Path0: /a/b/c
Path.directoryName: Some(/a/b)
Path.fileName: Some(c)
Path.extensionName: None
Path.fileNameWithoutExtension: Some(c)
Path.split: (Some(/a/b), Some(c))
Path.isAbsolute: true; Path.isRelative: false

Path1: /a/b/
Path.directoryName: Some(/a/b)
Path.fileName: None
Path.extensionName: None
Path.fileNameWithoutExtension: None
Path.split: (Some(/a/b), None)
Path.isAbsolute: true; Path.isRelative: false

Path2: /a/b/c.cj
Path.directoryName: Some(/a/b)
Path.fileName: Some(c.cj)
Path.extensionName: Some(cj)
Path.fileNameWithoutExtension: Some(c)
Path.split: (Some(/a/b), Some(c.cj))
Path.isAbsolute: true; Path.isRelative: false

Path3: /a
Path.directoryName: Some(/)
Path.fileName: Some(a)
Path.extensionName: None
Path.fileNameWithoutExtension: Some(a)
Path.split: (Some(/), Some(a))
Path.isAbsolute: true; Path.isRelative: false

Path4: /
Path.directoryName: Some(/)
Path.fileName: None
Path.extensionName: None
Path.fileNameWithoutExtension: None
Path.split: (Some(/), None)
Path.isAbsolute: true; Path.isRelative: false

Path5: ./a/b/c
Path.directoryName: Some(./a/b)
Path.fileName: Some(c)
Path.extensionName: None
Path.fileNameWithoutExtension: Some(c)
Path.split: (Some(./a/b), Some(c))
Path.isAbsolute: false; Path.isRelative: true

Path6: ./a/b/
Path.directoryName: Some(./a/b)
Path.fileName: None
Path.extensionName: None
Path.fileNameWithoutExtension: None
Path.split: (Some(./a/b), None)
Path.isAbsolute: false; Path.isRelative: true

Path7: ./a/b/c.cj
Path.directoryName: Some(./a/b)
Path.fileName: Some(c.cj)
Path.extensionName: Some(cj)
Path.fileNameWithoutExtension: Some(c)
Path.split: (Some(./a/b), Some(c.cj))
Path.isAbsolute: false; Path.isRelative: true

Path8: ./
Path.directoryName: Some(.)
Path.fileName: None
Path.extensionName: None
Path.fileNameWithoutExtension: None
Path.split: (Some(.), None)
Path.isAbsolute: false; Path.isRelative: true

Path9: .
Path.directoryName: None
Path.fileName: Some(.)
Path.extensionName: None
Path.fileNameWithoutExtension: None
Path.split: (None, Some(.))
Path.isAbsolute: false; Path.isRelative: true

Path10: 123.
Path.directoryName: None
Path.fileName: Some(123.)
Path.extensionName: None
Path.fileNameWithoutExtension: Some(123)
Path.split: (None, Some(123.))
Path.isAbsolute: false; Path.isRelative: true

```

## Path 的拼接、判等、转规范化路径等操作

代码如下：
<!-- verify -->

```cangjie
import std.fs.*

main() {
    let dirPath: Path = Path("./a/b/c")
    if (!Directory.exists(dirPath)) {
        Directory.create(dirPath, recursive: true)
    }

    let filePath: Path = dirPath.join("d.cj") // ./a/b/c/d.cj
    if (filePath == Path("./a/b/c/d.cj")) {
        println("filePath.join: success")
    }
    if (!File.exists(filePath)) {
        File.create(filePath).close()
    }

    let curNormalizedPath: Path = Path(".").toCanonical()
    let fileNormalizedPath: Path = Path("././././a/./../a/b/../../a/b/c/.././../../a/b/c/d.cj").toCanonical()
    if (fileNormalizedPath == filePath &&
        fileNormalizedPath.toString() == curNormalizedPath.toString() + "/a/b/c/d.cj") {
        println("filePath.toCanonical: success")
    }

    Directory.delete(dirPath, recursive: true)
    return 0
}
```

运行结果如下：

```text
filePath.join: success
filePath.toCanonical: success
```

## 通过 Path 创建文件和目录

代码如下：
<!-- verify -->

```cangjie
import std.fs.*

main() {
    let curPath: Path = Path("./")
    let dirPath: Path = curPath.join("tempDir")
    let filePath: Path = dirPath.join("tempFile.txt")
    if (Directory.exists(dirPath)) {
        Directory.delete(dirPath, recursive: true)
    }

    Directory.create(dirPath)
    if (Directory.exists(dirPath)) {
        println("Directory 'tempDir' is created successfully.")
    }

    File.create(filePath).close()
    if (File.exists(filePath)) {
        println("File 'tempFile.txt' is created successfully in directory 'tempDir'.")
    }

    Directory.delete(dirPath, recursive: true)
    return 0
}
```

运行结果如下：

```text
Directory 'tempDir' is created successfully.
File 'tempFile.txt' is created successfully in directory 'tempDir'.
```
