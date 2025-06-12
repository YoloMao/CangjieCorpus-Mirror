# crypto 模块

>  **注意：**
>
> 当前暂不支持通过 import crypto 直接导入 crypto 模块，否则，在编译阶段会报无法找到 crypto 包的错误（error: can not find package 'crypto'） 。建议当前使用导入 crypto 子包的形式使用 crypto 模块。

## crypto 功能介绍

crypto 模块提供安全加密能力，包括生成安全随机数、生成消息摘要、数据加密和签名、创建和解析证书等。

在实际应用中，crypto 模块常用于加密用户密码、保护敏感数据、生成数字签名等场景。

## crypto 模块的包列表

crypto 模块提供了如下包：

|                              包名                              |    功能    |
| -------------------------------------------------------------- | --------- |
| [crypto](./crypto/crypto_package_overview.md)                        | crypto 包提供安全随机数功能。 |
| [digest](./digest/crypto_digest_package_overview.md)                        | digest 包提供常用的消息摘要算法，包括 MD5、SHA1、SHA224、SHA256、SHA384、SHA512、HMAC、SM3等。 |
| [keys](./keys/keys_package_overview.md)                        | keys 包提供非对称加密和签名算法，包括 RSA 和 SM2 非对称加密算法以及 ECDSA 签名算法。 |
| [x509](./x509/x509_package_overview.md)                        | x509 包提供处理数字证书功能，提供包括解析和序列化 X509 证书、验证证书、创建自签名证书、创建和验证证书链等主要功能。 |
