# 异常类

## class X509Exception

```cangjie
public class X509Exception <: Exception {
    public init()
    public init(message: String)
}
```

功能：此异常为 X509 包抛出的异常类型。

父类型：

- [Exception](../../../std/core/core_package_api/core_package_exceptions.md#class-exception)

### init()

```cangjie
public init()
```

功能：构造 [X509Exception](x509_package_exceptions.md#class-x509exception) 对象。

### init(String)

```cangjie
public init(message: String)
```

功能：构造 [X509Exception](x509_package_exceptions.md#class-x509exception) 对象。

参数：

- message: [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - 异常的信息。
