# 函数

## func toStringOrPlaceholder\<T>(T)

```cangjie
public func toStringOrPlaceholder<T>(value: T)
```

功能：将实现 [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring) 的参数转换为字符串表达。不支持 [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring) 的转换为默认字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 参数的字符串表达。
