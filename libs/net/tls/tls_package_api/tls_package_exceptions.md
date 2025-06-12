# 异常类

## class TlsException

```cangjie
public class TlsException <: Exception
```

功能：TLS 处理出现错误时抛出的异常。

父类型：

- [Exception](../../../std/core/core_package_api/core_package_exceptions.md#class-exception)

### init()

```cangjie
public init()
```

功能：创建 [TlsException](tls_package_exceptions.md#class-tlsexception) 实例，异常提示消息为空。

### init(String)

```cangjie
public init(message: String)
```

功能：根据异常信息创建 TlsException 实例。

参数：

- message: [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - 异常信息。
