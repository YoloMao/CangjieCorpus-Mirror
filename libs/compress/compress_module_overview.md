# compress 模块

>  **注意：**
>
> 当前暂不支持通过 import compress 直接导入 compress 模块，否则，在编译阶段会报无法找到 compress 包的错误（error: can not find package 'compress'） 。建议当前使用导入 compress 子包的形式使用 compress 模块。

## compress 功能介绍

compress 模块提供压缩解压功能。

压缩是指用更少的比特表示数据，以便更高效地存储和传输数据。在实际应用中，压缩广泛应用于文件压缩、网页压缩、数据库备份等。

压缩功能的实现依赖于压缩算法，主流的压缩算法有 deflate、lz77、lzw 等，这些算法可以将数据中的冗余信息去除或者替换成更紧凑的表示形式，从而实现数据压缩的目的。本模块目前使用自研的 deflate 算法。

基于 deflate 压缩算法，给压缩后数据加上首部和尾部，可封装成不同格式的压缩文件，如 deflate-raw（无封装）、gzip、zip、png 等。其中 zip 可用于多个文件的压缩和打包，gzip 仅包含一个压缩文件。本模块目前支持的数据格式有 deflate-raw 和 gzip，暂不支持文件打包功能。

此外，本模块支持设置压缩级别，更高的压缩级别对应着更高的压缩率和更慢的压缩速度，反之，更低的压缩级别对应着更低的压缩率和更快的压缩速度。

特别地，zlib 指的是压缩功能的一个实现库，本模块的 zlib 包实现了 deflate 算法，并支持 deflate-raw 和 gzip 压缩格式。

## compress 模块的包列表

compress 模块提供了如下包：

|                              包名                              |    功能    |
| -------------------------------------------------------------- | --------- |
| [zlib](./zlib/zlib_package_overview.md)                        | zlib 包提供压缩解压能力。 |
