# 类型别名

## type JString

```cangjie
public type JString = JavaString
```

功能：`JString` 是 `java8/java.lang.[String](../../core/core_package_api/core_package_structs.md#struct-string)` 的类型别名。

### extend JString <: JType

```cangjie
extend JString <: JType
```

功能：为 `JString` 扩展字符串判等和拼接函数。

#### operator func ==(JString)

```cangjie
public operator func ==(s: JString): Bool
```

功能：判断两个 `JString` 对象是否相同。

参数：

- s: JString - 用于比较的另一个 `JString` 对象。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 两个 `JString` 对象相同时返回 true，否则返回 false。

#### operator func !=(JString)

```cangjie
public operator func !=(s: JString): Bool
```

功能：判断两个 `JString` 对象是否不同。

参数：

- s: JString - 用于比较的另一个 `JString` 对象。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 两个 `JString` 对象不同时返回 true，否则返回 false。

#### operator func +(JString)

```cangjie
public operator func +(s: JString): JString
```

功能：拼接两个 `JString` 对象。

参数：

- s: JString - 用于拼接的另一个 `JString` 对象。

返回值：

- JString - 拼接之后的 `JString` 对象。
