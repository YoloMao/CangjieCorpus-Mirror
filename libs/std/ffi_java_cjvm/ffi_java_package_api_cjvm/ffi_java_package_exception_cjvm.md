# 异常类

## class JavaException

```cangjie
public class JavaException <: Exception
```

功能：此类为 Java 中异常类型的包装类型，可以通过首先捕获此异常的方式，来捕获发生在 Java 侧的异常。

### func getCause()

```cangjie
public func getCause(): java.lang.Throwable
```

功能：获取实际的 Java 侧异常。

返回值：

- java.lang.Throwable - Java 侧实际发生的异常。

## class JavaNotSupportedException

```cangjie
public class JavaNotSupportedException <: Exception
```

功能：此类表示当前后端不支持 Java 互操作。当在不支持 Java 互操作的后端上使用互操作的任何特性时，抛出此异常。
