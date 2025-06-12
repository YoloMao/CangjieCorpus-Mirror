# HashMap 的 putAll/remove/clear 函数

此用例展示了 HashMap 的基本使用方法。

代码如下：

<!-- verify -->

```cangjie
import std.collection.*
main() {
    var map: HashMap<String, Int64> = HashMap<String, Int64>()
    var arr: Array<(String, Int64)> = [("d", 11), ("e", 12)]
    map.putAll(arr) // map : [("d", 11), ("e", 12)]
    var d = map.get("d")
    print("d=${d.getOrThrow()} ")
    map.remove("d") // map : [("e", 12)]
    var bool = map.contains("d")
    print("bool=${bool.toString()} ")
    map.clear() // map: []
    var bool1 = map.contains("e")
    print("bool1=${bool1.toString()}")
    return 0
}
```

运行结果如下:

```text
d=11 bool=false bool1=false
```
