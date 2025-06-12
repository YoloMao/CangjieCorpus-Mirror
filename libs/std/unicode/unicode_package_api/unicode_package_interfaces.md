# 接口

## interface UnicodeExtension

```cangjie
public interface UnicodeExtension
```

功能：`Unicode` 字符集相关扩展的接口，用于为其他类型扩展 `Unicode` 字符集相关的操作。

可用于为 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 和 [String](../../core/core_package_api/core_package_structs.md#struct-string) 类型增加一系列与 `Unicode` 字符集相关的扩展函数，包括字符类型判断，字符大小写转换，删除空白字符等。

### extend Rune <: UnicodeExtension

```cangjie
extend Rune <: UnicodeExtension
```

父类型：

- [UnicodeExtension](#interface-unicodeextension)

#### func isLetter()

```cangjie
public func isLetter(): Bool
```

功能：判断字符是否是 `Unicode` 字母字符。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该字符是 `Unicode` 字母字符，返回 `true`，否则返回 `false`。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'a'.isLetter())
    println(r'1'.isLetter())
}
```

运行结果：

```text
true
false
```

#### func isLowerCase()

```cangjie
public func isLowerCase(): Bool
```

功能：判断字符是否是 `Unicode` 小写字符。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该字符是 `Unicode` 小写字符，返回 `true`，否则返回 `false`。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'a'.isLowerCase())
    println(r'A'.isLowerCase())
}
```

运行结果：

```text
true
false
```

#### func isNumber()

```cangjie
public func isNumber(): Bool
```

功能：判断字符是否是 `Unicode` 数字字符。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该字符是 `Unicode` 数字字符，返回 `true`，否则返回 `false`。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'a'.isNumber())
    println(r'1'.isNumber())
}
```

运行结果：

```text
false
true
```

#### func isTitleCase()

```cangjie
public func isTitleCase(): Bool
```

功能：判断字符是否是 `Unicode` 标题化字符。

`Unicode` 中的标题化字符指的是一种特殊的字母形式，它们在某些语言中用于表示标题中每个单词的首字母大写的形式。这些字母由特殊的字符表示，例如U+01C5（ǅ）和U+01F1（Ǳ）。这些字符通常用于一些东欧语言，如克罗地亚语和塞尔维亚语。

标题化字符包括：`0x01C5`、`0x01C8`、`0x01CB`、`0x01F2`、`0x1F88 - 0x1F8F`、`0x1F98 - 0x1F9F`、`0x1F98 - 0x1F9F`、`0x1FA8 - 0x1FAF`、`0x1FBC`、`0x1FCC`、`0x1FFC`

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该字符是 `Unicode` 标题大写字符，返回 `true`，否则返回 `false`。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'ǅ'.isTitleCase())
}
```

运行结果：

```text
true
```

#### func isUpperCase()

```cangjie
public func isUpperCase(): Bool
```

功能：：判断字符是否是 `Unicode` 大写字符。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该字符是 `Unicode` 大写字符，返回 `true`，否则返回 `false`。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'a'.isUpperCase())
    println(r'A'.isUpperCase())
}
```

运行结果：

```text
false
true
```

#### func isWhiteSpace()

```cangjie
public func isWhiteSpace(): Bool
```

功能：判断字符是否是 `Unicode` 空白字符。

空白字符包括 `0x0009`、`0x000A`、`0x000B`、`0x000C`、`0x000D`、`0x0020`、`0x0085`、`0x00A0`、`0X1680`、`0X2000`、`0X2001`、`0X2002`、`0X2003`、`0X2004`、`0X2005`、`0X2006`、`0X2007`、`0X2008`、`0X2009`、`0X200A`、`0X2028`、`0X2029`、`0X202F`、`0X205F`、`0X3000`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该字符是 `Unicode` 空白字符，返回 `true`，否则返回 `false`。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r' '.isWhiteSpace())
}
```

运行结果：

```text
true
```

#### func toLowerCase()

```cangjie
public func toLowerCase(): Rune
```

功能：获取该字符对应的 `Unicode` 小写字符。

返回值：

- [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 当前字符对应的小写字符。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'A'.toLowerCase())
}
```

运行结果：

```text
a
```

#### func toTitleCase()

```cangjie
public func toTitleCase(): Rune
```

功能：获取该字符对应的 `Unicode` 标题大写字符。

返回值：

- [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 当前字符对应的标题大写字符。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'a'.toTitleCase())
}
```

运行结果：

```text
A
```

#### func toUpperCase()

```cangjie
public func toUpperCase(): Rune
```

功能：获取该字符对应的 `Unicode` 大写字符。

返回值：

- [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 当前字符对应的小写字符。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(r'a'.toUpperCase())
}
```

运行结果：

```text
A
```

### extend String <: UnicodeExtension

```cangjie
extend String <: UnicodeExtension
```

父类型：

- [UnicodeExtension](#interface-unicodeextension)

#### func isBlank()

```cangjie
public func isBlank(): Bool
```

功能：判断当前字符串是否为空，或仅包含 `Unicode` 字符集中的空字符。

空白字符包括 `0x0009`、`0x000A`、`0x000B`、`0x000C`、`0x000D`、`0x0020`、`0x0085`、`0x00A0`、`0X1680`、`0X2000`、`0X2001`、`0X2002`、`0X2003`、`0X2004`、`0X2005`、`0X2006`、`0X2007`、`0X2008`、`0X2009`、`0X200A`、`0X2028`、`0X2029`、`0X202F`、`0X205F`、`0X3000`。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果字符串为空，或仅包含空字符，返回 `true`，否则返回 `false`。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println(" \t\n\r".isBlank())
}
```

运行结果：

```text
true
```

#### func toLower()

```cangjie
public func toLower(): String
```

功能：将当前字符串中所有 `Unicode` 字符集范围内的大写字符转化为小写字符。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的全小写字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果字符串中存在无效的 UTF-8 编码，抛出异常。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println("AbcDEF".toLower())
}
```

运行结果：

```text
abcdef
```

#### func toTitle()

```cangjie
public func toTitle(): String
```

功能：将当前字符串中 `Unicode` 字符集范围内可以转换为标题大写字符的转换为标题大写字符。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的标题大写字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果字符串中存在无效的 UTF-8 编码，抛出异常。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println("AbcDEF".toTitle())
}
```

运行结果：

```text
ABCDEF
```

#### func toUpper()

```cangjie
public func toUpper(): String
```

功能：将当前字符串中所有 `Unicode` 字符集范围内的小写字符转化为大写字符。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 转换后的全大写字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果字符串中存在无效的 UTF-8 编码，抛出异常。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println("AbcDEF".toUpper())
}
```

运行结果：

```text
ABCDEF
```

#### func trim()

```cangjie
public func trim(): String
```

功能：去除原字符串开头结尾以空字符组成的子字符串，空字符定义见 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 类型的扩展函数 `isWhiteSpace`。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 去除首尾空字符后的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果字符串中不存在有效的 UTF-8 编码，抛出异常。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println("\nx \t ".trim())
}
```

运行结果：

```text
x
```

#### func trimLeft()

```cangjie
public func trimLeft(): String
```

功能：去除原字符串开头以空字符组成的子字符串，空字符定义见 [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) 类型的扩展函数 `isWhiteSpace`。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 去除开头空字符后的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果字符串中不存在有效的 UTF-8 编码，抛出异常。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println("  x  ".trimLeft())
}
```

运行结果：

```text
x
```

#### func trimRight()

```cangjie
public func trimRight(): String
```

功能：去除原字符串结尾以空字符组成的子字符串，空字符定义见 [Rune](../../../std/core/core_package_api/core_package_intrinsics.md#rune) 类型的扩展函数 `isWhiteSpace`。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 去除结尾空字符后的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 如果字符串中不存在有效的 UTF-8 编码，抛出异常。

示例：

```cangjie
import std.unicode.*

main(): Unit {
    println("  x  ".trimRight())
}
```

运行结果：

```text
  x
```
