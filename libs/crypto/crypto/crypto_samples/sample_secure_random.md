# SecureRandom 使用

示例：Random 创建随机数对象。

代码：
<!-- run -->

```cangjie
import crypto.crypto.*
main() {
    let r = SecureRandom()
    for (_ in 0..10) {
        let flip = r.nextBool()
        println(flip)
    }
    return 0
}
```

运行结果：

> **说明**
>
> 可能出现的运行结果如下(true/false 的选择是随机的)。

```text
false
true
false
false
false
true
true
false
false
true
```
