# 类

## class SimpleLogger

```cangjie
public class SimpleLogger <: Logger {
    public init()
    public init(name: String, level: LogLevel, output: OutputStream)
}
```

功能：此类实现 [Logger](stdlog_package_interfaces.md#interface-logger) 接口，提供基础的日志打印和管理功能。

包括自定义日志名称，控制日志打印级别，自定义输出流，默认情况下，日志名称为 “[Logger](stdlog_package_interfaces.md#interface-logger)”，打印级别为 `INFO`，输出流为 `stdOut`。

父类型：

- [Logger](../../../log/log/log_package_api/log_package_classes.md#class-logger)

### prop level

```cangjie
public mut prop level: LogLevel
```

功能：获取和修改日志打印级别。

类型：[LogLevel](stdlog_package_enums.md#enum-loglevel)

### init()

```cangjie
public init()
```

功能：创建一个默认的 [SimpleLogger](stdlog_package_classes.md#class-simplelogger) 实例。

### init(String, LogLevel, OutputStream)

```cangjie
public init(name: String, level: LogLevel, output: OutputStream)
```

功能：创建一个 [SimpleLogger](stdlog_package_classes.md#class-simplelogger) 实例，指定日志名称，日志打印级别和输出流。

参数：

- name: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志名称。
- level: [LogLevel](stdlog_package_enums.md#enum-loglevel) - 日志级别。
- output: [OutputStream](../../io/io_package_api/io_package_interfaces.md#interface-outputstream) - 输出流。

### func debug(String)

```cangjie
public func debug(msg: String): Unit
```

功能：打印 `DEBUG` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func error(String)

```cangjie
public func error(msg: String): Unit
```

功能：打印 `ERROR` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func flush()

```cangjie
public func flush(): Unit
```

功能：刷新输出流。

### func info(String)

```cangjie
public func info(msg: String): Unit
```

功能：打印 `INFO` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func log(LogLevel, String)

```cangjie
public func log(level: LogLevel, msg: String): Unit
```

功能：打印日志的通用函数，需指定日志级别。

参数：

- level: [LogLevel](stdlog_package_enums.md#enum-loglevel) - 日志级别。
- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func setOutput(OutputStream)

```cangjie
public func setOutput(output: OutputStream): Unit
```

功能：设置输出流，日志信息将打印到该输出流中。

参数：

- output: [OutputStream](../../io/io_package_api/io_package_interfaces.md#interface-outputstream) - 输出流。

### func trace(String)

```cangjie
public func trace(msg: String): Unit
```

功能：打印 `TRACE` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func warn(String)

```cangjie
public func warn(msg: String): Unit
```

功能：打印 `WARN` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。
