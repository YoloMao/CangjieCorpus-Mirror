# 类

## class MatchData

```cangjie
public class MatchData {}
```

功能：存储正则表达式匹配结果，并提供对正则匹配结果进行查询的函数。

### func groupNumber()

```cangjie
public func groupNumber(): Int64
```

功能：获取捕获组的个数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 捕获组的个数。

### func matchPosition()

```cangjie
public func matchPosition(): Position
```

功能：获取上一次匹配到的子字符串在输入字符串中起始位置和末尾位置的索引。

返回值：

- [Position](regex_package_structs.md#struct-position) - 匹配结果位置信息。

### func matchPosition(Int64)

```cangjie
public func matchPosition(group: Int64): Position
```

功能：根据给定的索引获取上一次匹配中该捕获组匹配到的子字符串在输入字符串中的位置信息。

参数：

- group: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 指定组。

返回值：

- [Position](regex_package_structs.md#struct-position) - 对应捕获组的位置信息。

异常：

- [IndexOutOfBoundsException](../../core/core_package_api/core_package_exceptions.md#class-indexoutofboundsexception) - 当 group 小于 0 或者大于 groupNumber 时，抛出异常。
- [RegexException](regex_package_exceptions.md#class-regexexception) - 当 group 不为 0 且没有捕获组时，抛出异常。

### func matchStr()

```cangjie
public func matchStr(): String
```

功能：获取上一次匹配到的子字符串，结果与调用 matchStr(0) 相同。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 匹配到的子字符串。

异常：

- [IndexOutOfBoundsException](../../core/core_package_api/core_package_exceptions.md#class-indexoutofboundsexception) - 当匹配字符串数组长度小于 1，抛出异常。

### func matchStr(Int64)

```cangjie
public func matchStr(group: Int64): String
```

功能：根据给定的索引获取上一次匹配中该捕获组匹配到的子字符串。

捕获组的索引从 1 开始，索引为 0 表示获取整个正则表达式的匹配结果。

参数：

- group: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 指定组。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 匹配到的子字符串。

异常：

- [IndexOutOfBoundsException](../../core/core_package_api/core_package_exceptions.md#class-indexoutofboundsexception) - 当 group 小于 0 或者大于 groupNumber 时，抛出异常。
- [RegexException](regex_package_exceptions.md#class-regexexception) - 当 group 不为 0 且没有捕获组时，抛出异常。

## class Matcher

```cangjie
public class Matcher {
    public init(re: Regex, input: String)
}
```

功能：正则匹配器，用于扫描输入序列并进行匹配。

> **注意：**
>
> - 要匹配的字符串最大长度不得超过 2<sup>31</sup>-1。
> - 要使用 replaceAll 替换的字符串最大长度不得超过 2<sup>30</sup>-2。

### init(Regex, String)

```cangjie
public init(re: Regex, input: String)
```

功能：使用传入的正则表达式和输入序列创建 [Matcher](regex_package_classes.md#class-matcher) 实例。

参数：

- re: [Regex](regex_package_classes.md#class-regex) - 正则表达式。
- input: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 输入序列。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当初始化失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 input 中包含空字符或长度大于2<sup>31</sup>-1时，抛出异常。

### func allCount()

```cangjie
public func allCount(): Int64
```

功能：获取正则表示式的匹配结果总数。

默认是从头到尾匹配的结果，使用了 setRegion 后只会在设置的范围内查找。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 匹配结果总数。

### func find()

```cangjie
public func find(): Option<MatchData>
```

功能：自当前字符串偏移位置起，查找第一个匹配到的子序列。

find 调用一次，当前偏移位置为最新一次匹配到的子序列后第一个字符位置，下次调用时，find 从当前位置开始匹配。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)> - 匹配到结果返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>，如果匹配不到，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>.None。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。

### func find(Int64)

```cangjie
public func find(index: Int64): Option<MatchData>
```

功能：重置该匹配器索引位置，从 index 对应的位置处开始对输入序列进行匹配，返回匹配到的子序列。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)> - 匹配到结果返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>，如果匹配不到，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>.None。

异常：

- [IndexOutOfBoundsException](../../core/core_package_api/core_package_exceptions.md#class-indexoutofboundsexception) - 当 index 小于 0，或 index 大于等于输入序列的 size 时，抛出异常。
- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。

### func findAll()

```cangjie
public func findAll(): Option<Array<MatchData>>
```

功能：对整个输入序列进行匹配，查找所有匹配到的子序列。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) < [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[MatchData](regex_package_classes.md#class-matchdata)>> - 如果匹配到结果，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[MatchData](regex_package_classes.md#class-matchdata)>>；如果匹配不到，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)<[Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[MatchData](regex_package_classes.md#class-matchdata)>>.None

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器内存分配失败或申请内存失败时，抛出异常。

### func fullMatch()

```cangjie
public func fullMatch(): Option<MatchData>
```

功能：对整个输入序列进行匹配。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)> - 如果全部匹配成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>.None。

### func getString()

```cangjie
public func getString(): String
```

功能：获取匹配序列。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 匹配序列。

### func matchStart()

```cangjie
public func matchStart(): Option<MatchData>
```

功能：对输入序列的头部进行匹配。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)> - 如果匹配成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>；否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>.None。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。

### func region()

```cangjie
public func region(): Position
```

功能：返回匹配器的区域设置。

返回值：

- [Position](regex_package_structs.md#struct-position) - 匹配器的区域设置。

### func replace(String)

```cangjie
public func replace(replacement: String): String
```

功能：自当前字符串偏移位置起，匹配到的第一个子序列替换为目标字符串，并将当前索引位置设置到匹配子序列的下一个位置。

参数：

- replacement: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 指定替换字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 替换后字符串。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 replacement 长度大于 2<sup>30</sup>-2，或者 replacement 包含空字符时，抛出异常。

### func replace(String, Int64)

```cangjie
public func replace(replacement: String, index: Int64): String
```

功能：从输入序列的 index 位置起匹配正则，将匹配到的第一个子序列替换为目标字符串。

参数：

- replacement: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 指定替换字符串。
- index: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 匹配开始位置。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 替换后字符串。

异常：

- [IndexOutOfBoundsException](../../core/core_package_api/core_package_exceptions.md#class-indexoutofboundsexception) - 当 index 小于 0，或 index 大于等于输入序列的 size 时，抛出异常。
- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 replacement 长度大于 2<sup>30</sup>-2，或者 replacement 包含空字符时，抛出异常。

### func replaceAll(String)

```cangjie
public func replaceAll(replacement: String): String
```

功能：将输入序列中所有与正则匹配的子序列替换为给定的目标字符串。

参数：

- replacement: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 指定替换字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 替换后的字符串。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，或者 c 侧申请内存失败，或者替换字符串时发生了 [GC](../../runtime/runtime_package_api/runtime_package_funcs.md#func-gcbool) 时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 replacement 长度大于 2<sup>30</sup>-2，或者 replacement 包含空字符时，抛出异常。

### func replaceAll(String, Int64)

```cangjie
public func replaceAll(replacement: String, limit: Int64): String
```

功能：将输入序列中与正则匹配的前 limit 个子序列替换为给定的替换字符串。

参数：

- limit: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 替换次数。如果 limit 等于 0，返回原来的序列；如果 limit 为负数，将尽可能多次的替换。
- replacement: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 指定替换字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 替换后字符串。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，或者 c 侧申请内存失败，或者替换字符串时发生了 [GC](../../runtime/runtime_package_api/runtime_package_funcs.md#func-gcbool) 时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 replacement 长度大于 2<sup>30</sup>-2，或者 replacement 包含空字符时，抛出异常。

### func resetRegion()

```cangjie
public func resetRegion(): Matcher
```

功能：重置匹配器开始位置和结束位置。

返回值：

- [Matcher](regex_package_classes.md#class-matcher) - 匹配器自身。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。

### func resetString(String)

```cangjie
public func resetString(input: String): Matcher
```

功能：重设匹配序列，并重置匹配器。

参数：

- input: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 新的匹配序列。

返回值：

- [Matcher](regex_package_classes.md#class-matcher) - 匹配器自身。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 input 长度大于 2<sup>31</sup>-1 或者包含空字符时，抛出异常。

### func setRegion(Int64, Int64)

```cangjie
public func setRegion(beginIndex: Int64, endIndex: Int64): Matcher
```

功能：设置匹配器可搜索区域的位置信息，具体位置由指定的 begin 和 end 决定。

参数：

- beginIndex: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 区域开始位置。
- endIndex: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 区域结束位置。

返回值：

- [Matcher](regex_package_classes.md#class-matcher) - 匹配器自身。

异常：

- [IndexOutOfBoundsException](../../core/core_package_api/core_package_exceptions.md#class-indexoutofboundsexception) - 当 beginIndex 小于0，或 beginIndex 大于输入序列的 size 时，抛出异常；当 endIndex 小于0，或 endIndex 大于输入序列的 size 时，抛出异常；当 beginIndex 大于 endIndex 时，抛出异常。

### func split()

```cangjie
public func split(): Array<String>
```

功能：将给定的输入序列根据正则尽可能的分割成多个子序列。

返回值：

- [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 子序列数组。

### func split(Int64)

```cangjie
public func split(limit: Int64): Array<String>
```

功能：将给定的输入序列根据正则尽可能的分割成多个子序列 (最多分割成 limit 个子串)。

参数：

- limit: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 最多分割的子串个数。

返回值：

- [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)> - 如果 limit>0，返回最多 limit 个子串；如果 limit<=0，返回最大可分割数个子串。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当重置匹配器失败时，抛出异常。

## class Regex

```cangjie
public class Regex {
    public init(s: String)
    public init(s: String, option: RegexOption)
}
```

功能：用来指定编译类型和输入序列。

正则匹配规则详见 regex 规则集。

### init(String)

```cangjie
public init(s: String)
```

功能：创建 [Regex](regex_package_classes.md#class-regex) 实例， 匹配模式为普通模式。

参数：

- s: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 正则表达式。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当初始化失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 s 中包含空字符时，抛出异常。

### init(String, RegexOption)

```cangjie
public init(s: String, option: RegexOption)
```

功能：使用指定的模式创建一个 [Regex](regex_package_classes.md#class-regex) 实例。

参数：

- s: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 正则表达式。
- option: [RegexOption](regex_package_classes.md#class-regexoption) - 正则匹配的模式。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当初始化失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 s 中包含空字符时，抛出异常。

### func matcher(String)

```cangjie
public func matcher(input: String): Matcher
```

功能：创建匹配器。

参数：

- input: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 要匹配的字符串，字符串长度最大 2<sup>31</sup> - 1。

返回值：

- [Matcher](regex_package_classes.md#class-matcher) - 创建的匹配器。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当初始化失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 input 中包含空字符时，抛出异常。

### func matches(String)

```cangjie
public func matches(input: String): Option<MatchData>
```

功能：创建匹配器，并将入参 input 与正则表达式进行完全匹配。

参数：

- input: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 要匹配的字符串，字符串长度最大 2<sup>31</sup> - 1。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)> - 如果匹配成功，返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>，否则返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[MatchData](regex_package_classes.md#class-matchdata)>.None。

异常：

- [RegexException](regex_package_exceptions.md#class-regexexception) - 当初始化失败时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 input 中包含空字符时，抛出异常。

### func string()

```cangjie
public func string(): String
```

功能：获取正则的输入序列。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 输入序列。

## class RegexOption

```cangjie
public class RegexOption <: ToString {
    public init()
}
```

功能：用于指定正则匹配的模式。

默认的正则匹配算法为 NFA ，匹配运行次数上限为 1000000。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)

### init()

```cangjie
public init()
```

功能：创建一个 [RegexOption](regex_package_classes.md#class-regexoption) 实例， 匹配模式为普通模式（NORMAL）。

### func ignoreCase()

```cangjie
public func ignoreCase(): RegexOption
```

功能：修改 [RegexOption](regex_package_classes.md#class-regexoption)，修改匹配模式为忽略大小写（IGNORECASE）。

返回值：

- [RegexOption](regex_package_classes.md#class-regexoption) - 修改后的 [RegexOption](regex_package_classes.md#class-regexoption)。

### func multiLine()

```cangjie
public func multiLine(): RegexOption
```

功能：修改 [RegexOption](regex_package_classes.md#class-regexoption)，修改匹配模式为多行文本模式（MULTILINE）。

返回值：

- [RegexOption](regex_package_classes.md#class-regexoption) - 修改后的 [RegexOption](regex_package_classes.md#class-regexoption)。

### func toString()

```cangjie
public func toString(): String
```

功能：获取 [RegexOption](regex_package_classes.md#class-regexoption) 当前表示的正则匹配模式。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 正则匹配模式。
