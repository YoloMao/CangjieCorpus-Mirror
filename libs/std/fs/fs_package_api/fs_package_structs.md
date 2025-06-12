# 结构体

## struct FileDescriptor

```cangjie
public struct FileDescriptor
```

功能：用于获取文件句柄信息。

> **说明：**
>
> 文件句柄（File Handle）是操作系统为了跟踪文件而分配的一种数据结构，用于标识一个打开文件的实例。文件句柄包含了文件的元数据信息（如文件名、路径、大小、修改时间等）以及文件数据在磁盘上的物理位置等信息。
> 在不同的操作系统中，文件句柄的形式可能会有所不同。在 Unix 和 Linux 系统中，文件句柄通常是一个非负整数，由操作系统内核分配，并在打开文件时返回给应用程序。在 Windows 系统中，文件句柄通常是一个指向文件对象的指针，由操作系统内核分配，并在打开文件时返回给应用程序。无论文件句柄的形式是什么，应用程序都可以使用它来执行文件的读取、写入、修改等操作。

### prop fileHandle

```cangjie
public prop fileHandle: CPointer<Unit>
```

功能：Windows 下获取文件句柄信息。

类型：[CPointer](../../core/core_package_api/core_package_intrinsics.md#cpointert)\<[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)>

### prop fileHandle

```cangjie
public prop fileHandle: Int32
```

功能：Linux 下获取文件句柄信息。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## struct FileInfo

```cangjie
public struct FileInfo <: Equatable<FileInfo> {
    public init(path: Path)
    public init(path: String)
}
```

功能：对应文件系统中的文件元数据。

> **说明：**
>
> 文件元数据是指文件系统中与文件相关的信息，包括文件名、文件大小、创建时间、修改时间、访问时间、文件权限、文件所有者等。
>
> [FileInfo](fs_package_structs.md#struct-fileinfo) 的底层实现是没有直接缓存文件属性的，每次通过 [FileInfo](fs_package_structs.md#struct-fileinfo) 的 API 都是现场获取的最新的文件属性。
>
> 因此这里有需要注意的情况，对于创建的同一 [FileInfo](fs_package_structs.md#struct-fileinfo) 实例，如果在两次获取其文件属性操作期间，对应的文件实体可能会被其他用户或进程做了修改或者替换等不期望的操作，就会导致后一次获取的可能不是期望的文件属性。
> 如果有特殊文件操作需求需要避免上述情况的产生，可以采用设置文件权限或者给关键文件操作加锁的方式来保证。

父类型：

- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[FileInfo](#struct-fileinfo)>

### prop creationTime

```cangjie
public prop creationTime: DateTime
```

功能：获取创建时间。

类型：[DateTime](../../time/time_package_api/time_package_structs.md#struct-datetime)

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### prop lastAccessTime

```cangjie
public prop lastAccessTime: DateTime
```

功能：获取最后访问时间。

类型：[DateTime](../../time/time_package_api/time_package_structs.md#struct-datetime)

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### prop lastModificationTime

```cangjie
public prop lastModificationTime: DateTime
```

功能：获取最后修改时间。

类型：[DateTime](../../time/time_package_api/time_package_structs.md#struct-datetime)

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### prop length

```cangjie
public prop length: Int64
```

功能：返回当前文件大小。

- 当前是文件时，表示单个文件占用磁盘空间的大小。
- 当前是目录时，表示当前目录的所有文件占用磁盘空间的大小。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### prop parentDirectory

```cangjie
public prop parentDirectory: Option<FileInfo>
```

功能：获得父级目录元数据，以 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[FileInfo](fs_package_structs.md#struct-fileinfo)> 形式返回，有父级返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[FileInfo](fs_package_structs.md#struct-fileinfo)>.Some(v)；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[FileInfo](fs_package_structs.md#struct-fileinfo)>.None。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[FileInfo](fs_package_structs.md#struct-fileinfo)>

### prop path

```cangjie
public prop path: Path
```

功能：获得当前文件路径，以 [Path](fs_package_structs.md#struct-path) 形式返回。

类型：[Path](fs_package_structs.md#struct-path)

### prop symbolicLinkTarget

```cangjie
public prop symbolicLinkTarget: Option<Path>
```

功能：获得链接目标路径，以 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)> 形式返回，当前是符号链接返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)>.Some(v)；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)>.None。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)>

### init(Path)

```cangjie
public init(path: Path)
```

功能：创建 [FileInfo](fs_package_structs.md#struct-fileinfo) 实例。

参数：

- path: [Path](fs_package_structs.md#struct-path) - [Path](fs_package_structs.md#struct-path) 形式的目录路径。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 当路径非法时，抛出异常。

### init(String)

```cangjie
public init(path: String)
```

功能：创建 [FileInfo](fs_package_structs.md#struct-fileinfo) 实例。

参数：

- path: [String](../../core/core_package_api/core_package_structs.md#struct-string) - [String](../../core/core_package_api/core_package_structs.md#struct-string) 形式的目录路径。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 当路径非法时，抛出异常。

### func canExecute()

```cangjie
public func canExecute(): Bool
```

功能：判断当前用户是否有权限执行该实例对应的文件。

- 对文件而言，判断用户是否有执行文件的权限。
- 对目录而言，判断用户是否有进入目录的权限。
- 在 Windows 环境下，用户对于文件的执行权限由文件扩展名决定；用户始终拥有对于目录的执行权限，该函数不生效，返回 true。
- 在 Linux 和 macOS 环境下，该函数正常使用。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示有权限；false 表示无权限。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### func canRead()

```cangjie
public func canRead(): Bool
```

功能：判断当前用户是否有权限读取该实例对应的文件。

- 对文件而言，判断用户是否有读取文件的权限。
- 对目录而言，判断用户是否有浏览目录的权限。
- 在 windows 环境下，用户始终拥有对于文件和目录的可读权限，该函数不生效，返回 true。
- 在 Linux 和 macOS 环境下，该函数正常使用。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示有权限；false 表示无权限。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### func canWrite()

```cangjie
public func canWrite(): Bool
```

功能：判断当前用户是否有权限写入该实例对应的文件。

- 对文件而言，判断用户是否有写入文件的权限。
- 对目录而言，判断用户是否有删除、移动、创建目录内文件的权限。
- 在 Windows 环境下，用户对于文件的可写权限正常使用，用户始终拥有对于目录的可写权限，该函数不生效，返回 true。
- 在 Linux 和 macOS 环境下，该函数正常使用。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示有权限；false 表示无权限。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### func isDirectory()

```cangjie
public func isDirectory(): Bool
```

功能：判断当前文件是否是目录。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示是目录；false 表示不是目录。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### func isFile()

```cangjie
public func isFile(): Bool
```

功能：判断当前文件是否是普通文件。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示是文件；false 表示不是文件。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### func isHidden()

```cangjie
public func isHidden(): Bool
```

功能：判断当前文件是否隐藏。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示隐藏；false 表示未隐藏。

### func isReadOnly()

```cangjie
public func isReadOnly(): Bool
```

功能：判断当前文件是否只读。

- 在 Windows 环境下，用户对于文件的只读权限正常使用；用户始终拥有对于目录的删除修改权限，该函数不生效，返回 false。
- 在 Linux 和 macOS 环境下，该函数正常使用。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示是只读；false 表示不是只读。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### func isSymbolicLink()

```cangjie
public func isSymbolicLink(): Bool
```

功能：判断当前文件是否是软链接。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true 表示是软链接；false 表示不是软链接。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果判断过程中底层调用的系统接口发生错误，则抛异常。

### func setExecutable(Bool)

```cangjie
public func setExecutable(executable: Bool): Bool
```

功能：对当前实例对应的文件设置当前用户是否可执行的权限，当前用户没有权限修改抛异常。

- 对文件而言，设置用户是否有执行文件的权限，对目录而言，设置用户是否有进入目录的权限。
- 在 Windows 环境下，用户对于文件的执行权限由文件扩展名决定，用户始终拥有对于目录的执行权限该函数不生效，返回 false。
- 在 Linux 和 macOS 环境下，该函数正常使用如果在此函数调用期间，该 [FileInfo](fs_package_structs.md#struct-fileinfo) 对应的文件实体被其它用户或者进程修改，有可能因为竞争条件(Race Condition)导致其它修改不能生效。

参数：

- executable: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否设置可执行。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，操作成功；false，操作失败。

### func setReadable(Bool)

```cangjie
public func setReadable(readable: Bool): Bool
```

功能：对当前实例对应的文件设置当前用户是否可读取的权限，当前用户没有权限修改抛异常。

- 对文件而言，设置用户是否有读取文件的权限。
- 对目录而言，设置用户是否有浏览目录的权限。
- 在 Windows 环境下，用户始终拥有对于文件以及目录的可读权限，不可更改，该函数不生效当 readable 为 true 时，函数返回 true，当 readable 为 false 时，函数返回 false。
- 在 Linux 和 macOS 环境下，该函数正常使用如果在此函数调用期间，该 [FileInfo](fs_package_structs.md#struct-fileinfo) 对应的文件实体被其它用户或者进程修改，有可能因为竞争条件(Race Condition)导致其它修改不能生效。

参数：

- readable: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否设置可读。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，操作成功；false，操作失败。

### func setWritable(Bool)

```cangjie
public func setWritable(writable: Bool): Bool
```

功能：对当前实例对应的文件设置当前用户是否可写入的权限，当前用户没有权限修改抛异常。

- 对文件而言，设置用户是否有写入文件的权限。
- 对目录而言，设置用户是否有删除、移动、创建目录内文件的权限。
- 在 Windows 环境下，用户对于文件的可写权限正常使用；用户始终拥有对于目录的可写权限，不可更改，该函数不生效，返回 false。
- 在 Linux 和 macOS 环境下，该函数正常使用如果在此函数调用期间，该 [FileInfo](fs_package_structs.md#struct-fileinfo) 对应的文件实体被其它用户或者进程修改，有可能因为竞争条件(Race Condition)导致其它修改不能生效。

参数：

- writable: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 是否设置可写。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，操作成功；false，操作失败。

### operator func !=(FileInfo)

```cangjie
public operator func !=(that: FileInfo): Bool
```

功能：判断当前 [FileInfo](fs_package_structs.md#struct-fileinfo) 和另一个 [FileInfo](fs_package_structs.md#struct-fileinfo) 是否对应非同一文件。

参数：

- that: [FileInfo](fs_package_structs.md#struct-fileinfo) - 另一个 [FileInfo](fs_package_structs.md#struct-fileinfo)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，不是同一文件；false，是同一文件。

### operator func ==(FileInfo)

```cangjie
public operator func ==(that: FileInfo): Bool
```

功能：判断当前 [FileInfo](fs_package_structs.md#struct-fileinfo) 和另一个 [FileInfo](fs_package_structs.md#struct-fileinfo) 是否对应同一文件。

参数：

- that: [FileInfo](fs_package_structs.md#struct-fileinfo) - 另一个 [FileInfo](fs_package_structs.md#struct-fileinfo)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，是同一文件；false，不是同一文件。

## struct Path

```cangjie
public struct Path <: Equatable<Path> & Hashable & ToString {
    public init(rawPath: String)
}
```

功能：提供路径相关的函数。

Path 用来表示本地路径（Windows 平台已支持 DOS 设备路径和 UNC 路径，长度限制跟随系统）。 路径的字符串最大支持 4096 个字节（包括结束符 `\0`）。

> **说明：**
>
> 非法路径指的是以下情况之一：
>
> - 路径中包含非法字符，例如空格、制表符、换行符等；
> - 路径中包含不合法的字符，例如特殊字符、控制字符等；
> - 路径中包含不存在的目录或文件；
> - 路径中包含无法访问的目录或文件，例如权限不足或被锁定等。

在输入路径时，应该避免使用非法字符，确保路径的合法性，以便正确地访问目标文件或目录。

父类型：

- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[Path](#struct-path)>
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)
- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)

### prop directoryName

```cangjie
public prop directoryName: Option<Path>
```

功能：获得 [Path](fs_package_structs.md#struct-path) 的目录部分，以 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)> 形式返回。

- 对于路径 "/a/b/c"，此属性返回 Some(Path("/a/b"))。
- 对于路径 "/a/b/"，此属性返回 Some(Path("/a/b"))。
- 对于路径 "/a"，此属性返回 Some(Path("/"))。
- 对于路径 "/"，此属性返回 Some(Path("/"))。
- 对于路径 "./a/b"，此属性返回 Some(Path("./a"))。
- 对于路径 "./"，此属性返回 Some(Path("."))。
- 对于路径 "."，此属性返回 `None`。
- 对于路径 ".gitignore"，此属性返回 `None`。
- 对于路径 "a.txt"，此属性返回 `None`。
- 对于路径 "C:\a\b\c"，此属性返回 Some(Path("C:\a\b"))。
- 对于路径 "C:\a\b\"，此属性返回 Some(Path("C:\a\b"))。

返回值：返回构造时传入的路径中的目录部分，构造时传入的路径中无目录部分时返回 None。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)>

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### prop extensionName

```cangjie
public prop extensionName: Option<String>
```

功能：获得 [Path](fs_package_structs.md#struct-path) 的文件扩展名部分，以 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> 形式返回。

- 对于路径 "./NewFile.txt"，此属性返回 `Some("txt")`。
- 对于路径 "./.gitignore"，此属性返回 `Some("gitignore")`。
- 对于路径 "./noextension"，此属性返回 `None`。
- 对于路径 "./a.b.c"，此属性返回 `Some("c")`。
- 对于路径 "./NewDir/"，此属性返回 `None`。
- 对于路径 "./NewDir/NewFile."，此属性返回 `None`。

返回值：返回构造时传入的路径中的文件扩展名部分，构造时传入的路径中无文件扩展名部分时返回 None。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### prop fileName

```cangjie
public prop fileName: Option<String>
```

功能：获得 [Path](fs_package_structs.md#struct-path) 的文件名（含扩展名）部分，以 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> 形式返回。

- 对于路径 "./NewFile.txt"，此属性返回 `Some("NewFile.txt")`。
- 对于路径 "./.gitignore"，此属性返回 `Some(".gitignore")`。
- 对于路径 "./noextension"，此属性返回 `Some("noextension")`。
- 对于路径 "./a.b.c"，此属性返回 `Some("a.b.c")`。
- 对于路径 "./NewDir/"，此属性返回 `None`。

返回值：返回构造时传入的路径中的文件名（含扩展名）部分，构造时传入的路径中无文件名（含扩展名）部分时返回 None。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### prop fileNameWithoutExtension

```cangjie
public prop fileNameWithoutExtension: Option<String>
```

功能：获得 [Path](fs_package_structs.md#struct-path) 的文件名（不含扩展名）部分，以 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> 形式返回。

- 对于路径 "./NewFile.txt"，此属性返回 `Some("NewFile")`。
- 对于路径 "./.gitignore"，此属性返回 `None`。
- 对于路径 "./noextension"，此属性返回 `Some("noextension")`。
- 对于路径 "./a.b.c"，此属性返回 `Some("a.b")`。
- 对于路径 "./NewDir/"，此属性返回 `None`。

返回值：返回构造时传入的路径中的文件名（不含扩展名）部分，构造时传入的路径中无文件名（不含扩展名）部分时返回 None。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### init(String)

```cangjie
public init(rawPath: String)
```

功能：创建 [Path](fs_package_structs.md#struct-path) 实例时不检查路径字符串是否合法，支持绝对路径和相对路径。

参数：

- rawPath: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 路径的字符串。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获得 [Path](fs_package_structs.md#struct-path) 的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - [Path](fs_package_structs.md#struct-path) 的哈希值。

### func isAbsolute()

```cangjie
public func isAbsolute(): Bool
```

功能：判断 [Path](fs_package_structs.md#struct-path) 是否是绝对路径。在 Unix 中，以 `/` 开头的路径为绝对路径。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，是绝对路径；false，不是绝对路径。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### func isDirectory()

```cangjie
public func isDirectory(): Bool
```

功能：判断 [Path](fs_package_structs.md#struct-path) 是否是目录，与 isFile，isSymbolicLink 互斥。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，是目录；false，不是目录。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果路径不存在，或者判断过程中底层调用的系统接口发生错误，则抛异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### func isFile()

```cangjie
public func isFile(): Bool
```

功能：判断 [Path](fs_package_structs.md#struct-path) 是否是文件，与 isSymbolicLink，isDirectory 互斥。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，是文件；false，不是文件。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果路径不存在，或者判断过程中底层调用的系统接口发生错误，则抛异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### func isRelative()

```cangjie
public func isRelative(): Bool
```

功能：判断 [Path](fs_package_structs.md#struct-path) 是否是相对路径，其结果与函数 [isAbsolute](fs_package_structs.md#func-isAbsolute) 结果相反。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，是相对路径；false，不是相对路径。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### func isSymbolicLink()

```cangjie
public func isSymbolicLink(): Bool
```

功能：判断 [Path](fs_package_structs.md#struct-path) 是否是软链接，与 isFile，isDirectory 互斥。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，是软链接；false，不是软链接。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果路径不存在，或者判断过程中底层调用的系统接口发生错误，则抛异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### func join(Path)

```cangjie
public func join(path: Path): Path
```

功能：在当前路径后拼接另一个路径字符串形成新路径。

- 对于路径 "a/b"，"c"，返回 "a/b/c"。
- 对于路径 "a"，"b/c"，返回 "a/b/c"。

返回值：

- [Path](fs_package_structs.md#struct-path) - 新路径的 [Path](fs_package_structs.md#struct-path) 实例。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果参数 path 是绝对路径则抛异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当前路径为空，或当前路径、入参路径非法时抛出异常。

### func join(String)

```cangjie
public func join(path: String): Path
```

功能：在当前路径后拼接另一个路径字符串形成新路径。

- 对于路径 "a/b"，"c"，返回 "a/b/c"。
- 对于路径 "a"，"b/c"，返回 "a/b/c"。

返回值：

- [Path](fs_package_structs.md#struct-path) - 新路径的 [Path](fs_package_structs.md#struct-path) 实例。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 如果参数 path 是绝对路径则抛异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当前路径为空，或当前路径、入参路径非法时抛出异常。

### func split()

```cangjie
public func split(): (Option<Path>, Option<String>)
```

功能：将 [Path](fs_package_structs.md#struct-path) 分割成目录和文件名两部分以元组形式返回分割结果 `(directoryName, fileName)` 。

返回值：

- ([Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)>, [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>) - 返回值为元组类型，第一个元素表示路径，路径获取成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)>.Some(p)，失败，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Path](fs_package_structs.md#struct-path)>.None；第二个元素表示文件名，文件名获取成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.Some(s)，失败，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>.None。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当路径为空，或包含字符串结束符则抛出异常。

### func toCanonical()

```cangjie
public func toCanonical(): Path
```

功能：将 [Path](fs_package_structs.md#struct-path) 规范化返回绝对路径形式的规范化路径。

所有的中间引用和软链接都会处理 （UNC 路径下的软链接无法被规范化），例如，对于路径 "/foo/test/../test/bar.txt"，该函数会返回 "/foo/test/bar.txt"。

返回值：

- [Path](fs_package_structs.md#struct-path) - 规范化路径的 [Path](fs_package_structs.md#struct-path) 实例。

异常：

- [FSException](fs_package_exceptions.md#class-fsexception) - 路径不存在或无法规范化时抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 路径为空，或包含字符串结束符时抛出异常。

### func toString()

```cangjie
public func toString(): String
```

功能：获得 [Path](fs_package_structs.md#struct-path) 的路径字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - [Path](fs_package_structs.md#struct-path) 的路径字符串。

### operator func !=(Path)

```cangjie
public operator func !=(that: Path): Bool
```

功能：判断 [Path](fs_package_structs.md#struct-path) 是否不是同一路径。

参数：

- that: [Path](fs_package_structs.md#struct-path) - 另一个 [Path](fs_package_structs.md#struct-path)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，不是同一路径；false，是同一路径。

### operator func ==(Path)

```cangjie
public operator func ==(that: Path): Bool
```

功能：判断 [Path](fs_package_structs.md#struct-path) 是否是同一路径。

参数：

- that: [Path](fs_package_structs.md#struct-path) - 另一个 [Path](fs_package_structs.md#struct-path)。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - true，是同一路径；false，不是同一路径。
