# 接口

## interface Logger

```cangjie
public interface Logger {
    mut prop level: LogLevel
    func setOutput(output: OutputStream): Unit
    func trace(msg: String): Unit
    func debug(msg: String): Unit
    func info(msg: String): Unit
    func warn(msg: String): Unit
    func error(msg: String): Unit
    func log(level: LogLevel, msg: String): Unit
}
```

此接口用于管理和打印日志。

### prop level

```cangjie
mut prop level: LogLevel
```

功能：获取和修改日志打印级别，只有级别小于等于该值的日志会被打印。

类型：[LogLevel](stdlog_package_enums.md#enum-loglevel)

### func debug(String)

```cangjie
func debug(msg: String): Unit
```

功能：打印 `DEBUG` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func error(String)

```cangjie
func error(msg: String): Unit
```

功能：打印 `ERROR` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func info(String)

```cangjie
func info(msg: String): Unit
```

功能：打印 `INFO` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func log(LogLevel, String)

```cangjie
func log(level: LogLevel, msg: String): Unit
```

功能：打印日志的通用函数，需指定日志级别。

参数：

- level: [LogLevel](stdlog_package_enums.md#enum-loglevel) - 日志级别。
- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func setOutput(OutputStream)

```cangjie
func setOutput(output: OutputStream): Unit
```

功能：设置日志输出流，日志将被打印到该输出流。

参数：

- output: [OutputStream](../../io/io_package_api/io_package_interfaces.md#interface-outputstream) - 输出流。

### func trace(String)

```cangjie
func trace(msg: String): Unit
```

功能：打印 `TRACE` 级别的日志的便捷函数。如果设置的打印级别小于 `TRACE`，将忽略这条日志信息，否则打印到输出流。以下日志打印函数均使用该规则。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。

### func warn(String)

```cangjie
func warn(msg: String): Unit
```

功能：打印 `WARN` 级别的日志的便捷函数。

参数：

- msg: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 日志内容。
