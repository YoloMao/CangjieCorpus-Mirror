# compress.zlib 包

## 功能介绍

zlib 压缩解压库。

本包使用自研 deflate 算法，支持 deflate-raw 和 gzip 数据格式，支持快速、默认、高压缩率三种压缩等级，压缩速度依次下降，压缩率依次提升。

本包提供流式压缩和解压功能，即支持从输入流读取数据，将其压缩或解压，并写入字节数组，或从字节数组中读取数据，将其压缩或解压，并写入输出流。

> **说明：**
>
> 本包暂不支持文件打包功能。

## API 列表

### 类

|                 类名              |                功能                 |
| --------------------------------- | ---------------------------------- |
| [CompressInputStream](./zlib_package_api/zlib_package_classes.md#class-compressinputstream) | 压缩输入流。    |
| [CompressOutputStream](./zlib_package_api/zlib_package_classes.md#class-compressoutputstream) | 压缩输出流。       |
| [DecompressInputStream](./zlib_package_api/zlib_package_classes.md#class-decompressinputstream) | 解压输入流。    |
| [DecompressOutputStream](./zlib_package_api/zlib_package_classes.md#class-decompressoutputstream) | 解压输出流。      |

### 枚举

|                 枚举名              |                功能                 |
| --------------------------------- | ---------------------------------- |
| [CompressLevel](./zlib_package_api/zlib_package_enums.md#enum-compresslevel) | 压缩等级。      |
| [WrapType](./zlib_package_api/zlib_package_enums.md#enum-wraptype) | 压缩数据格式。    |

### 异常类

|                 异常类名              |                功能                 |
| --------------------------------- | ---------------------------------- |
| [ZlibException](./zlib_package_api/zlib_package_exceptions.md#class-zlibexception) | `zlib` 包的异常类。      |
