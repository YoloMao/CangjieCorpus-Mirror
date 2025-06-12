# std.fs 包

## 功能介绍

fs（file system）包提供对文件、文件夹、路径、文件元数据信息的一些操作函数。

目前支持 Linux，macOS 和 Windows 平台下使用。

## API 列表

### 类

|                 类名              |                功能                 |
| --------------------------------- | ---------------------------------- |
| [Directory](./fs_package_api/fs_package_classes.md#class-directory) | 对应文件系统中的目录，它提供创建、移动、复制、删除、查询属性以及遍历目录等能力。  |
| [File](./fs_package_api/fs_package_classes.md#class-file) | 提供一些对文件进行操作的函数，包括文件的打开、创建、关闭、移动、复制、删除，文件的流式读写操作，查询属性以及一些其他函数。   |

### 枚举

|              枚举名          |           功能           |
| --------------------------- | ------------------------ |
| [OpenOption](./fs_package_api/fs_package_enums.md#enum-openoption) | 表示不同的文件打开选项。 |

### 结构体

|              结构体名          |           功能           |
| --------------------------- | ------------------------ |
| [FileDescriptor](./fs_package_api/fs_package_structs.md#struct-filedescriptor) | 用于获取文件句柄信息。 |
| [FileInfo](./fs_package_api/fs_package_structs.md#struct-fileinfo) | 对应文件系统中的文件元数据，提供一些文件属性的查询和设置等函数。 |
| [Path](./fs_package_api/fs_package_structs.md#struct-path) | 提供路径相关的函数。 |

### 异常类

|              异常类名          |           功能           |
| --------------------------- | ------------------------ |
| [FSException](./fs_package_api/fs_package_exceptions.md#class-fsexception) | 文件流异常类，继承了异常类。 |
