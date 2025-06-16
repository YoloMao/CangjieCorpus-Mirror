# Directory 示例

## Directory 一些基础操作演示

代码如下：
<!-- verify -->

```cangjie
import std.fs.*

main() {
    let testDirPath: Path = Path("./testDir")
    let subDirPath: Path = Path("./testDir/subDir")
    if (Directory.exists(testDirPath)) {
        Directory.delete(testDirPath, recursive: true)
    }

    /* 递归创建目录 和 "./testDir/subDir" */
    let subDir: Directory = Directory.create(subDirPath, recursive: true)
    if (Directory.exists(subDirPath)) {
        println("The directory './testDir/subDir' is successfully created recursively in current directory.")
    }

    /* 在 "./testDir/subDir" 下创建子目录 "dir1" */
    subDir.createSubDirectory("dir1")
    if (Directory.exists("./testDir/subDir/dir1")) {
        println("The directory 'dir1' is created successfully in directory './testDir/subDir'.")
    }

    /* 在 "./testDir/subDir" 下创建子文件 "file1" */
    subDir.createFile("file1")
    if (File.exists("./testDir/subDir/file1")) {
        println("The file 'file1' is created successfully in directory './testDir/subDir'.")
    }

    /* 在 "./testDir" 下创建临时目录 */
    let tempDir: Directory = Directory.createTemp(testDirPath)
    let tempDirPath: Path = tempDir.info.path
    if (Directory.exists(tempDirPath)) {
        println("The temporary directory is created successfully in directory './testDir'.")
    }

    /* 将 "subDir" 移动到临时目录下并重命名为 "subDir_new" */
    let newSubDirPath: Path = tempDirPath.join("subDir_new")
    Directory.move(subDirPath, newSubDirPath, false)
    if (Directory.exists(newSubDirPath) && !Directory.exists(subDirPath)) {
        println("The directory './testDir/subDir' is moved successfully to the temporary directory and renamed 'subDir_new'.")
    }

    /* 将 "subDir_new" 拷贝到 "./testDir" 下并重命名为 "subDir" */
    Directory.copy(newSubDirPath, subDirPath, false)
    if (Directory.exists(subDirPath) && Directory.exists(newSubDirPath)) {
        println("The directory 'subDir_new' is copied successfully to directory './testDir' and renamed 'subDir'.")
    }

    Directory.delete(testDirPath, recursive: true)
    return 0
}
```

运行结果如下：

```text
The directory './testDir/subDir' is successfully created recursively in current directory.
The directory 'dir1' is created successfully in directory './testDir/subDir'.
The file 'file1' is created successfully in directory './testDir/subDir'.
The temporary directory is created successfully in directory './testDir'.
The directory './testDir/subDir' is moved successfully to the temporary directory and renamed 'subDir_new'.
The directory 'subDir_new' is copied successfully to directory './testDir' and renamed 'subDir'.
```
