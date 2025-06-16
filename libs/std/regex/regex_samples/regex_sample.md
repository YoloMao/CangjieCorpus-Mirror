# regex 示例

## RegexOption 获取当前正则匹配模式
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    var a = RegexOption()
    println(a.toString())
    a = RegexOption().ignoreCase()
    println(a.toString())
    a = RegexOption().multiLine()
    println(a.toString())
    a = RegexOption().multiLine().ignoreCase()
    println(a.toString())
}

```

运行结果：

```text
NORMAL,NFA
IGNORECASE,NFA
MULTILINE,NFA
MULTILINE,IGNORECASE,NFA
```

## Regex 匹配大小写
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    let r1 = Regex("ab")
    let r2 = Regex("ab", RegexOption().ignoreCase())
    match (r1.matches("aB")) {
        case Some(r) => println(r.matchStr())
        case None => println("None")
    }
    match (r2.matches("aB")) {
        case Some(r) => println(r.matchStr())
        case None => println("None")
    }
}
```

运行结果：

```text
None
aB
```

## MatchOption 匹配多行
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    let rule = ##"^(\w+)\s(\d+)*$"##
    let pattern: String = """
Joe 164
Sam 208
Allison 211
Gwen 171
"""

    let r1 = Regex(rule, RegexOption().multiLine())
    var arr = r1.matcher(pattern).findAll() ?? Array<MatchData>()
    for (md in arr) {
        println(md.matchStr())
    }
}
```

运行结果：

```text
Joe 164
Sam 208
Allison 211
Gwen 171
```

## Matcher 和 MatchData 的使用
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    let r = Regex(#"a\wa"#).matcher("1aba12ada555")
    for (_ in 0..2) {
        let matchData = r.find()
        match (matchData) {
            case Some(md) =>
                println(md.matchStr())
                let pos = md.matchPosition()
                println("[${pos.start}, ${pos.end})")
            case None => println("None")
        }
    }
}
```

运行结果：

```text
aba
[1, 4)
ada
[6, 9)
```

## Matcher 中 resetString/fullMatch/matchStart 函数
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    let r = Regex("\\d+")
    let m = r.matcher("13588123456")
    let matchData1 = m.fullMatch()
    m.resetString("13588abc")
    let matchData2 = m.matchStart()
    m.resetString("abc13588123abc")
    let matchData3 = m.matchStart()
    match (matchData1) {
        case Some(md) => println(md.matchStr())
        case None => println("None")
    }
    match (matchData2) {
        case Some(md) => println(md.matchStr())
        case None => println("None")
    }
    match (matchData3) {
        case Some(md) => println(md.matchStr())
        case None => println("None")
    }
}
```

运行结果：

```text
13588123456
13588
None
```

## Matcher 中 replace/replaceAll 函数
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    let r = Regex("\\d").matcher("a1b1c2d3f4")
    println(r.replace("X")) //replace a digit once with X
    println(r.replace("X", 2)) //replace once from index 4
    println(r.replaceAll("X")) //replace all digit with X
    println(r.replaceAll("X", 2)) //replace all at most 2 times
    println(r.replaceAll("X", -1)) //replace all digit with X
}
```

运行结果：

```text
aXb1c2d3f4
a1bXc2d3f4
aXbXcXdXfX
aXbXc2d3f4
aXbXcXdXfX
```

## Matcher 获取匹配总数
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    var matcher = Regex("a+b").matcher("1ab2aab3aaab4aaaab")
    println(matcher.allCount())
}
```

运行结果：

```text
4
```

## MatchData 中 groupNumber 函数
<!-- verify -->

```cangjie
import std.regex.*

main(): Unit {
    var r = Regex("(a+c)(a?b)()(()?c+((e|s([a-h]*))))")
    var m = r.matcher("aacbcsdedd")
    var matchData = m.find()
    match (matchData) {
        case Some(s) =>
            println("groupNum : ${s.groupNumber()}")
            if (s.groupNumber() > 0) {
                for (i in 1..=s.groupNumber()) {
                    println("group[${i}] : ${s.matchStr(i)}")
                    var pos = s.matchPosition(i)
                    println("position : [${pos.start}, ${pos.end})")
                }
            }
        case None => ()
    }
}
```

运行结果：

```text
groupNum : 8
group[1] : aac
position : [0, 3)
group[2] : b
position : [3, 4)
group[3] :
position : [4, 4)
group[4] : csdedd
position : [4, 10)
group[5] :
position : [10, 10)
group[6] : sdedd
position : [5, 10)
group[7] : sdedd
position : [5, 10)
group[8] : dedd
position : [6, 10)
```
