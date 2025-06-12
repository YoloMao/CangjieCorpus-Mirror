# 函数

## func currentDir()

```cangjie
public func currentDir(): Directory
```

功能：获取当前工作目录。

> **说明：**
>
> - 返回值为 [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory) 类型，可以使用 [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory).info.path.toString() 获取路径的字符串。

返回值：

- [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory) - 当前工作目录。

## func envVars()

```cangjie
public func envVars(): HashMap<String, String>
```

功能：获取所有环境变量。

> **说明：**
>
> - 返回值为 [HashMap](../../collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)，它以 `key` 和 `value` 的形式存储环境变量。

返回值：

- [HashMap](../../collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek) < [String](../../core/core_package_api/core_package_structs.md#struct-string), [String](../../core/core_package_api/core_package_structs.md#struct-string) > - 所有环境变量值。

## func getArgs()

```cangjie
public func getArgs(): Array<String>
```

功能：返回命令行参数列表，例如在命令行中执行 `a.out ab cd ef`，其中 `a.out` 是程序名，返回的列表包含三个元素 ab cd ef。

> **说明：**
>
> - 使用 C 语言调用仓颉动态库方式时，通过 int SetCJCommandLineArgs(int argc, const char* argv[]) 设置的命令行参数，在使用 [getArgs](os_package_funcs.md#func-getargs)() 获取时将会被舍弃掉第一个参数。

返回值：

- [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 命令行参数列表。

## func getEnv(String)

```cangjie
public func getEnv(k: String): Option<String>
```

功能：获取指定名称的环境变量值。

参数：

- k: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 环境变量名称。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 指定名称对应的环境变量值。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当函数参数 `k` 包含空字符时，抛出异常。

## func homeDir()

```cangjie
public func homeDir(): Directory
```

功能：获取 `home` 目录。

> **说明：**
>
> - 返回值为 [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory) 类型，可以使用 [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory).info.path.toString() 获取路径的字符串。

返回值：

- [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory) - `home` 目录。

## func processorCount()

```cangjie
public func processorCount(): Int64
```

功能：获取处理器数量。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 处理器数量。

## func removeEnv(String)

```cangjie
public func removeEnv(k: String): Unit
```

功能：通过指定环境变量名称移除环境变量。

参数：

- k: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 环境变量名称。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当函数参数 `k` 包含空字符时，抛出异常。

## func setEnv(String, String)

```cangjie
public func setEnv(k: String, v: String): Unit
```

功能：用于设置一对环境变量。如果设置了同名环境变量，原始环境变量值将被覆盖。

参数：

- k: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 环境变量名称。
- v: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 环境变量值。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当函数参数 `k` 或 `v` 中包含空字符时，抛出异常。

## func tempDir()

```cangjie
public func tempDir(): Directory
```

功能：获取临时目录。从环境变量中获取 `TMPDIR`、`TMP`、`TEMP` 和 `TEMPDIR` 环境变量。如果以上值在环境变量中均不存在，则默认返回 `/tmp` 目录。

> **说明：**
>
> - 返回值为 [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory) 类型，可以使用 [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory).info.path.toString() 获取路径的字符串。

返回值：

- [Directory](../../fs/fs_package_api/fs_package_classes.md#class-directory) - 临时目录。
