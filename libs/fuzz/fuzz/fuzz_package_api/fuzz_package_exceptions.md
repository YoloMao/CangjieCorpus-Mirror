# 异常类

## class ExhaustedException

```cangjie
public class ExhaustedException <: Exception {
    public init()
    public init(message: String)
}
```

功能：此异常为转换数据时，剩余数据不足以转换时抛出的异常。

父类型：

- [Exception](../../../std/core/core_package_api/core_package_exceptions.md#class-exception)

### init()

```cangjie
public init()
```

功能：创建 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception) 实例。

### init(String)

```cangjie
public init(message: String)
```

功能：创建 [ExhaustedException](fuzz_package_exceptions.md#class-exhaustedexception) 实例。

参数：

- message: [String](../../../std/core/core_package_api/core_package_structs.md#struct-string) - 异常提示信息。
