# 枚举

## enum OpenOption

```cangjie
public enum OpenOption {
    | Append
    | Create(Bool)
    | CreateOrAppend
    | CreateOrTruncate(Bool)
    | Open(Bool, Bool)
    | Truncate(Bool)
}
```

功能：表示不同的文件打开选项。

### Append

```cangjie
Append
```

功能：构造一个 [OpenOption](fs_package_enums.md#enum-openoption) 实例，指定文件系统应打开现有文件并查找到文件尾，用这个选项创建的 [File](fs_package_classes.md#class-file) 默认只具有 Write 权限，试图查找文件尾之前的位置时会引发 [FSException](fs_package_exceptions.md#class-fsexception) 异常，并且任何试图读取的操作都会失败并引发 [FSException](fs_package_exceptions.md#class-fsexception) 异常。如果文件不存在，则将引发 [FSException](fs_package_exceptions.md#class-fsexception) 异常。

### Create(Bool)

```cangjie
Create(Bool)
```

功能：构造一个 [OpenOption](fs_package_enums.md#enum-openoption) 实例，指定文件系统应创建新文件，用这个选项创建的 [File](fs_package_classes.md#class-file) 默认具有 Write 权限，可以通过参数指定是否具有 Read 权限。如果文件已存在，则将引发 [FSException](fs_package_exceptions.md#class-fsexception) 异常。

### CreateOrAppend

```cangjie
CreateOrAppend
```

功能：构造一个 [OpenOption](fs_package_enums.md#enum-openoption) 实例，指定文件系统应打开文件（如果文件存在），否则，应创建新文件。用这个选项创建的 [File](fs_package_classes.md#class-file) 默认只具有 Write 权限，并且试图查找文件尾之前的位置时会引发 [FSException](fs_package_exceptions.md#class-fsexception) 异常。分为两种情况：如果文件不存在，则使用 Create；否则使用 Append。

### CreateOrTruncate(Bool)

```cangjie
CreateOrTruncate(Bool)
```

功能：构造一个 [OpenOption](fs_package_enums.md#enum-openoption) 实例，指定文件系统应创建新文件，如果此文件已存在，则会将其覆盖。用这个选项创建的 [File](fs_package_classes.md#class-file) 默认具有 Write 权限，可以通过参数指定是否具有 Read 权限。分为两种情况：如果文件不存在，则使用 Create；否则使用 Truncate。

### Open(Bool, Bool)

```cangjie
Open(Bool, Bool)
```

功能：构造一个 [OpenOption](fs_package_enums.md#enum-openoption) 实例，指定文件系统应打开现有文件，第一个参数指定文件是否具有 Read 权限，第二个参数指定文件是否具有 Write 权限。如果文件不存在，则将引发 [FSException](fs_package_exceptions.md#class-fsexception) 异常。

### Truncate(Bool)

```cangjie
Truncate(Bool)
```

功能：构造一个 [OpenOption](fs_package_enums.md#enum-openoption) 实例，指定文件系统应打开现有文件，该文件被打开时，将被截断为零字节大小。用这个选项创建的 [File](fs_package_classes.md#class-file) 默认具有 Write 权限，可以通过参数指定是否具有 Read 权限。如果文件不存在，则将引发 [FSException](fs_package_exceptions.md#class-fsexception) 异常。
