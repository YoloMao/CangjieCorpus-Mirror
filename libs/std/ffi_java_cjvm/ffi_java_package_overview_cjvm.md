# std.ffi.java 包

## 功能介绍

为了兼容 Java 庞大的生态，仓颉支持与 Java 语言的互操作，并通过本包提供了一些基础能力。

本包为用户提供了以下能力：

1. 本包提供了 JArray/JString 两种类型，分别与 Java 的数组和字符串类型进行映射，同时提供仓颉 String 类型与 JString 类型的互相转换接口；

2. 本包提供了 JType 接口，用于约束与 Java 互操作的类型范围；

3. 本包提供了 JavaException/JavaNotSupportedException 两种类型，处理来自 Java 侧的异常。

## API 列表

### 函数

|               函数名            |              功能              |
| ------------------------------ | ------------------------------ |
| [toJString(String)](./ffi_java_package_api_cjvm/ffi_java_package_funcs_cjvm.md#func-tojstringstring) | 将仓颉的 `String` 对象转换为 `JString` 对象。 |
| [toString(JString)](./ffi_java_package_api_cjvm/ffi_java_package_funcs_cjvm.md#func-tostringjstring) | 将 `JString` 对象转换为仓颉的 `String` 对象。 |

### 类型别名

|               类型别名            |              描述              |
| ------------------------------ | ------------------------------ |
| [JString](./ffi_java_package_api_cjvm/ffi_java_package_types_cjvm.md#extend-jstring--jtype) | `java8/java.lang.String` 的类型别名。 |

### 接口

|               接口名            |              功能              |
| ------------------------------ | ------------------------------ |
| [JType](./ffi_java_package_api_cjvm/ffi_java_package_interface_cjvm.md#interface-jtype) | Java 互操作支持的类型的父类型。 |

### 类

|               类名            |              功能              |
| ------------------------------ | ------------------------------ |
| [JArray\<T> where T <: JType](./ffi_java_package_api_cjvm/ffi_java_package_classes_cjvm.md#class-jarrayt-where-t--jtype) | Java 互操作支持的类型的父类型。 |

### 异常类

|               异常类名            |              功能              |
| ------------------------------ | ------------------------------ |
| [JavaException](./ffi_java_package_api_cjvm/ffi_java_package_exception_cjvm.md#class-javaexception) | 此类为 Java 中异常类型的包装类型。 |
| [JavaNotSupportedException](./ffi_java_package_api_cjvm/ffi_java_package_exception_cjvm.md#class-javanotsupportedexception) | 此类表示当前后端不支持 Java 互操作。 |
