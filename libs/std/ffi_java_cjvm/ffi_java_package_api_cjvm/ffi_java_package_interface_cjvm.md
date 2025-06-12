# 接口

## interface JType

```cangjie
sealed interface JType
```

功能：作为所有 Java 互操作支持类型的父类型，便于在泛型约束中使用。此接口不包含任何函数。

> **注意：**
>
> - `JType` 接口是仓颉中的一个接口类型，它本身不满足 `JType` 约束；
> - `JType` 接口不允许被继承、扩展。
