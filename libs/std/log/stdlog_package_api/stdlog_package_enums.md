# 枚举

## enum LogLevel

```cangjie
public enum LogLevel <: ToString {
    | OFF
    | ERROR
    | WARN
    | INFO
    | DEBUG
    | TRACE
    | ALL
}
```

功能：该枚举类表示打印级别。

定义了日志打印的七个级别，级别从低到高分别为 `OFF`、`ERROR`、`WARN`、`INFO`、`DEBUG`、`TRACE`、`ALL`。

[SimpleLogger](stdlog_package_classes.md#class-simplelogger) 类的实现中，指定了日志打印级别，以及每一条日志的级别，只有级别小于等于指定打印级别的日志条目会被打印到输出流中。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)

### ALL

```cangjie
ALL
```

功能：构造一个日志打印级别的枚举实例，等级为所有。

### DEBUG

```cangjie
DEBUG
```

功能：构造一个日志打印级别的枚举实例，等级为调试。

### ERROR

```cangjie
ERROR
```

功能：构造一个日志打印级别的枚举实例，等级为错误。

### INFO

```cangjie
INFO
```

功能：构造一个日志打印级别的枚举实例，等级为通知。

### OFF

```cangjie
OFF
```

功能：构造一个日志打印级别的枚举实例，等级为禁用。

### TRACE

```cangjie
TRACE
```

功能：构造一个日志打印级别的枚举实例，等级为跟踪。

### WARN

```cangjie
WARN
```

功能：构造一个日志打印级别的枚举实例，等级为警告。

### func level()

```cangjie
public func level(): Int64
```

功能：获取日志级别对应的数字，`OFF` 为 1，`ERROR` 为 2，此后依次加一。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前的日志级别对应的数字。

### func toString()

```cangjie
public func toString(): String
```

功能：获取日志级别对应的名称。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 当前的日志级别的名称。

### operator func >=(LogLevel)

```cangjie
public operator func >=(target: LogLevel): Bool
```

功能：比较日志级别高低。

参数：

- target: [LogLevel](stdlog_package_enums.md#enum-loglevel) - 将当前日志级别和 `target` 进行比较。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果当前日志级别大于等于 `target`，返回 `true`，否则返回 `false`。
