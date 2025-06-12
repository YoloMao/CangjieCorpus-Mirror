# 对 Array 进行排序

创建一个无序Array，并这个 Array 进行升序排序，利用 isAse 判断排序后是否为升序。

代码：

<!-- verify -->

```cangjie
import std.sort.*
import std.random.*

main(): Unit {
    let r: Random = Random()
    let arr: Array<Int64> = Array<Int64>(70000, { _ => r.nextInt64() })
    arr.sortBy(stable: true){ rht: Int64, lht: Int64 =>
        if (rht < lht) {
            return Ordering.LT
        }
        if (rht > lht) {
            return Ordering.GT
        }
        return Ordering.EQ
    }

    println(isAse(arr))
}

func isAse(t: Array<Int64>) {
    var item: Int64 = t[0]
    for (i in 1..t.size) {
        if (item > t[i]) {
            return false
        }
        item = t[i]
    }
    return true
}
```

运行结果：

```text
true
```
