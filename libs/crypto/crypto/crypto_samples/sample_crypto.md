# SM4 使用

示例： SM4 加解密数据。

代码：
<!-- run -->

```cangjie
import crypto.crypto.*
import encoding.hex.fromHexString
main() {

    var plains = "hello cangjie!"
    var key = "1234567890123456"
    var iv = "1234567890123456"
    var sm4 = SM4(OperationMode.CBC, key.toArray(), iv: iv.toArray())
    var enRe = sm4.encrypt(plains.toArray())
    var dd =sm4.decrypt(enRe)
    println(String.fromUtf8(dd))
}
```

运行结果：

```text
hello cangjie!
```
