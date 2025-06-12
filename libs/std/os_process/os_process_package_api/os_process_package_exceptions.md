# 异常

## class ProcessException

```cangjie
public class ProcessException <: Exception {
    init(message: String)
}
```

功能：`os.process` 包的异常类。

父类型：

- [Exception](../../core/core_package_api/core_package_exceptions.md#class-exception)

### init(String)

```cangjie
public init(message: String)
```

功能：创建 [ProcessException](os_process_package_exceptions.md#class-processexception) 实例。

参数：

- message: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 异常提示信息。
