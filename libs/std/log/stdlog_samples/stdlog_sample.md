# 日志打印示例

## ALL 级别日志打印

下面是 ALL 级别日志打印示例。

代码如下：
<!-- verify -->

```cangjie
import std.log.*
main(): Int64 {
    let logger: SimpleLogger = SimpleLogger()
    logger.level = LogLevel.ALL
    logger.log(LogLevel.ALL, "============== 日志级别为 ALL================")
    logger.log(LogLevel.TRACE,
    "=============="+logger.level.toString()+"================")
    logger.log(LogLevel.OFF, "OFF 打印出来！")
    logger.log(LogLevel.ERROR, "error 打印出来！")
    logger.log(LogLevel.WARN, "warn 打印出来！")
    logger.log(LogLevel.INFO, "INFO 打印出来！")
    logger.log(LogLevel.DEBUG, "DEBUG 打印出来！")
    logger.log(LogLevel.TRACE, "trace 打印出来！")
    logger.log(LogLevel.ALL, "ALL 打印出来！")
    logger.flush()
    0
}
```

运行结果如下：

```text
2021/08/05 08:20:42.692770 ALL Logger ============== 日志级别为 ALL================
2021/08/05 08:20:42.696645 TRACE Logger ==============ALL================
2021/08/05 08:20:42.700188 ERROR Logger error 打印出来！
2021/08/05 08:20:42.703576 WARN Logger warn 打印出来！
2021/08/05 08:20:42.706920 INFO Logger INFO 打印出来！
2021/08/05 08:20:42.710268 DEBUG Logger DEBUG 打印出来！
2021/08/05 08:20:42.713602 TRACE Logger trace 打印出来！
2021/08/05 08:20:42.716940 ALL Logger ALL 打印出来！
```

## 指定日志级别和输出流

以下示例前半部分指定打印级别为 ERROR，输出流为 error_log.txt 文件，后半部分指定打印级别为 WARN，输出流为 warn_log.txt 文件。

代码如下：
<!-- verify -->

```cangjie
import std.fs.*
import std.log.*
main(): Int64 {
    let logger: SimpleLogger = SimpleLogger()

    logger.level = LogLevel.ERROR
    var s = File("./error_log.txt", OpenOption.CreateOrTruncate(false))
    logger.setOutput(s)
    logger.log(LogLevel.ERROR, "============== 日志级别为 ERROR================")
    logger.log(LogLevel.ERROR,
    "=============="+logger.level.toString()+"================")
    logger.log(LogLevel.OFF, "OFF 打印出来！")
    logger.log(LogLevel.ERROR, "error 打印出来！")
    logger.log(LogLevel.WARN, "warn 打印出来！")
    logger.log(LogLevel.INFO, "INFO 打印出来！")
    logger.log(LogLevel.DEBUG, "DEBUG 打印出来！")
    logger.log(LogLevel.TRACE, "trace 打印出来！")
    logger.log(LogLevel.ALL, "ALL 打印出来！")
    logger.flush()
    s.close()

    logger.level = LogLevel.WARN
    s = File("./warn_log.txt", OpenOption.CreateOrTruncate(false))
    logger.setOutput(s)
    logger.log(LogLevel.WARN, "============== 日志级别为 WARN================")
    logger.log(LogLevel.WARN,
    "=============="+logger.level.toString()+"================")
    logger.log(LogLevel.OFF, "OFF 打印出来！")
    logger.log(LogLevel.ERROR, "error 打印出来！")
    logger.log(LogLevel.WARN, "warn 打印出来！")
    logger.log(LogLevel.INFO, "INFO 打印出来！")
    logger.log(LogLevel.DEBUG, "DEBUG 打印出来！")
    logger.log(LogLevel.TRACE, "trace 打印出来！")
    logger.log(LogLevel.ALL, "ALL 打印出来！")
    logger.flush()
    s.close()
    0
}
```

运行结果如下：

```text
$ cat error_log.txt
2021/08/05 08:28:29.667441 ERROR Logger ============== 日志级别为 ERROR================
2021/08/05 08:28:29.671402 ERROR Logger ==============ERROR================
2021/08/05 08:28:29.674891 ERROR Logger error 打印出来！
$ cat warn_log.txt
2021/08/05 08:28:29.678978 WARN Logger ============== 日志级别为 WARN================
2021/08/05 08:28:29.682635 WARN Logger ==============WARN================
2021/08/05 08:28:29.686126 ERROR Logger error 打印出来！
2021/08/05 08:28:29.689561 WARN Logger warn 打印出来！
```
