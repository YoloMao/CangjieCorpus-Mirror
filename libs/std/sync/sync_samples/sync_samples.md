# Atomic、Monitor 和 Timer 的使用

## Atomic 的使用

在多线程程序中，使用原子操作实现计数：

```cangjie
import std.sync.*
import std.time.*
import std.collection.*

let count = AtomicInt64(0)

main(): Int64 {
    let list = ArrayList<Future<Int64>>()

    /* 创建 1000 个线程 */
    for (_ in 0..1000) {
        let fut = spawn {
            sleep(Duration.millisecond) /* 睡眠 1 毫秒 */
            count.fetchAdd(1)
        }
        list.append(fut)
    }

    /* 等待所有线程完成 */
    for (f in list) {
        f.get()
    }

    var val = count.load()
    println("count = ${val}")
    return 0
}
```

输出结果：

```text
count = 1000
```

## Monitor 的使用

示例：

在不同线程中，使用 `Monitor` 实现挂起和唤醒线程：
<!-- verify -->

```cangjie
import std.sync.*
import std.time.{Duration, DurationExtension}

var mon = Monitor()
var flag: Bool = true

main(): Int64 {
    let fut = spawn {
        mon.lock()
        while (flag) {
            println("New thread: before wait")
            mon.wait()
            println("New thread: after wait")
        }
        mon.unlock()
    }

    /* 睡眠 10 毫秒，以确保新线程可以执行 */
    sleep(10 * Duration.millisecond)

    mon.lock()
    println("Main thread: set flag")
    flag = false
    mon.unlock()

    println("Main thread: notify")
    mon.lock()
    mon.notifyAll()
    mon.unlock()

    /* 等待新线程完成 */
    fut.get()
    return 0
}
```

输出结果：

```text
New thread: before wait
Main thread: set flag
Main thread: notify
New thread: after wait
```

## Timer 的使用

示例：

使用 `Timer` 创建一次性和重复性任务：
<!-- verify -->

```cangjie
import std.sync.*
import std.time.{Duration, DurationExtension}

main(): Int64 {
    let count = AtomicInt8(0)

    Timer.once(50 * Duration.millisecond) { =>
        println("run only once")
        count.fetchAdd(1)
    }

    let timer = Timer.repeat(100 * Duration.millisecond, 200 * Duration.millisecond, { =>
        println("run repetitively")
        count.fetchAdd(10)
    })

    sleep(Duration.second)
    timer.cancel()
    sleep(500 * Duration.millisecond)
    println("count = ${count.load()}")
    0
}
```

输出结果：

```text
run only once
run repetitively
run repetitively
run repetitively
run repetitively
run repetitively
count = 51
```
