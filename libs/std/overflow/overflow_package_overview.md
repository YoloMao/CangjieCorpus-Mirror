# std.overflow 包

## 功能介绍

overflow 包提供了整数运算溢出时的处理能力。

在整数运算时，若运算结果大于其类型最大值或小于其类型最小值即是溢出。默认情况下，出现溢出时会抛出异常。

overflow 包提供了四种溢出处理策略，并定义了对应的接口，列举如下：

| 策略                   | 接口                          | 描述                                           |
| ---------------------- | ----------------------------- | --------------------------------------------- |
| 返回 Option         | [CheckedOp](./overflow_package_api/overflow_package_interfaces.md#interface-checkedop)    | 当整数运算出现溢出，返回 `None`。                  |
| 饱和                    | [SaturatingOp](./overflow_package_api/overflow_package_interfaces.md#interface-saturatingop) | 当计算结果大于目标类型的 MAX 值，返回 MAX 值；当计算结果小于目标类型的 MIN 值，返回 MIN 值。 |
| 抛出异常                | [ThrowingOp](./overflow_package_api/overflow_package_interfaces.md#interface-throwingop)   | 当整数运算出现溢出，抛出异常。                              |
| 高位截断                | [WrappingOp](./overflow_package_api/overflow_package_interfaces.md#interface-wrappingop)   | 当整数运算出现溢出，将运算结果中超出目标类型位数的高位截断。                              |

overflow 包中通过扩展为所有的整数类型提供了这些接口的实现，用户可以用同样的方式为其他类型实现 overflow 接口。

## API 列表

### 接口

|              接口名          |           功能           |
| --------------------------- | ------------------------ |
| [CheckedOp](./overflow_package_api/overflow_package_interfaces.md#interface-checkedop)    | 当整数运算出现溢出，返回 `None`。                        |
| [SaturatingOp](./overflow_package_api/overflow_package_interfaces.md#interface-saturatingop) | 当整数运算出现溢出，饱和处理。                           |
| [ThrowingOp](./overflow_package_api/overflow_package_interfaces.md#interface-throwingop)   | 当整数运算出现溢出，抛出异常。                           |
| [WrappingOp](./overflow_package_api/overflow_package_interfaces.md#interface-wrappingop)   | 当整数运算出现溢出，将运算结果中超出目标类型位数的高位截断。                           |

### 异常类

|                 类名              |                功能                 |
| --------------------------------- | ---------------------------------- |
| [OvershiftException](./overflow_package_api/overflow_package_exceptions.md#class-overshiftexception) | 移位运算时移位位数超过操作数位数时抛出的异常。       |
| [UndershiftException](./overflow_package_api/overflow_package_exceptions.md#class-undershiftexception) | 移位运算时移位位数小于 0 时抛出的异常。          |
