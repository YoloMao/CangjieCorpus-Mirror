# encoding 模块

>  **注意：**
>
> 当前暂不支持通过 import encoding 直接导入 encoding 模块，否则，在编译阶段会报无法找到 encoding 包的错误（error: can not find package 'encoding'） 。建议当前使用导入 encoding 子包的形式使用 encoding 模块。

## encoding 功能介绍

encoding 模块提供字符编解码功能。

支持 Base64、Hex、JSON、URL 格式数据的编解码。

## encoding 模块的包列表

encoding 模块提供了如下包：

|                              包名                              |    功能    |
| -------------------------------------------------------------- | --------- |
| [base64](./base64/base64_package_overview.md)                        | base 包提供字符串的 Base64 编码及解码。 |
| [hex](./hex/hex_package_overview.md)                        | hex 包提供字符串的 Hex 编码及解码。 |
| [json](./json/json_package_overview.md)                        | json 包用于对 json 数据的处理，实现 String, JsonValue, DataModel 之间的相互转换。 |
| [json.stream](./json_stream/json_stream_package_overview.md)                        | json.stream 包主要用于仓颉对象和 JSON 数据流之间的互相转换。 |
| [url](./url/url_package_overview.md)                        | url 包提供了 URL 相关的能力，包括解析 URL 的各个组件，对 URL 进行编解码，合并 URL 或路径等。 |