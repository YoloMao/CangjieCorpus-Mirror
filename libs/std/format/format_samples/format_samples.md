# format 使用示例

## 格式化整型

下面是格式化整型示例。

代码如下：

<!-- verify -->

```cangjie
import std.format.*

main(): Int64 {
    var a: Int32 = -20
    var res1 = a.format("-10")
    var res2 = a.format("+10")
    var res3 = (-20).format("10")
    var res4 = a.format("-")
    println("\"${res1}\"")
    println("\"${res2}\"")
    println("\"${res3}\"")
    println("\"${res4}\"")
    return 0
}
```

运行结果如下：

```text
"-20       "
"       -20"
"       -20"
"-20"
```

## 格式化浮点型

下面是格式化浮点型示例。

代码如下：

<!-- verify -->

```cangjie
 import std.format.*

/* flags '-' */
main(): Int64 {
    var a: Float16 = -0.34
    var b: Float32 = .34
    var c: Float64 = 3_0.3__4_
    var d: Float64 = 20.00
    /* left  align */
    var res1 = a.format("-20")
    /* right align */
    var res2 = b.format("+20")
    /* left  align */
    var res3 = c.format("10")
    /* left  align */
    var res4 = d.format("-10")
    /* left  align */
    var res5 = d.format("-")
    println("\"${res1}\"")
    println("\"${res2}\"")
    println("\"${res3}\"")
    println("\"${res4}\"")
    println("\"${res5}\"")
    return 0
}
```

运行结果如下：

```text
"-0.340088           "
"           +0.340000"
" 30.340000"
"20.000000 "
"20.000000"
```

## 格式化字符型

下面是格式化字符型示例。

代码如下：

<!-- verify -->

```cangjie
import std.format.*

main(): Int64 {
    var a: Rune = 'a'
    var b: Rune = '-'
    /* left  align */
    var res1 = a.format("-10")
    /* right  align */
    var res2 = b.format("-10")
    /* left  align */
    var res3 = a.format("10")
    /* left  align */
    var res4 = b.format("10")
    println("\"${res1}\"")
    println("\"${res2}\"")
    println("\"${res3}\"")
    println("\"${res4}\"")
    return 0
}
```

运行结果如下：

```text
"a         "
"-         "
"         a"
"         -"
```
