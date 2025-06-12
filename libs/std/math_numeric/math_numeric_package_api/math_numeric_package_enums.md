# 枚举

## enum OverflowStrategy

```cangjie
public enum OverflowStrategy {
    | saturating
    | throwing
    | wrapping
}
```

溢出策略枚举类，共包含 3 种溢出策略。[BigInt](math_numeric_package_structs.md#struct-bigint) 类型、[Decimal](math_numeric_package_structs.md#struct-decimal) 类型转换为整数类型时，允许指定不同的溢出处理策略。

### saturating

```cangjie
saturating
```

功能：出现溢出，当前值大于目标类型的 MAX 值，返回目标类型 MAX 值，当前值小于目标类型的 MIN 值，返回目标类型 MIN 值。

### throwing

```cangjie
throwing
```

功能：出现溢出，抛出异常。

### wrapping

```cangjie
wrapping
```

功能：出现溢出，高位截断。
