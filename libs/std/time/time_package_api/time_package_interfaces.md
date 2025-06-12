# 接口

## interface DurationExtension

```cangjie
public interface DurationExtension {
    operator func *(r: Duration): Duration
}
```

功能：[DurationExtension](time_package_interfaces.md#interface-durationextension) 用于拓展 [Duration](time_package_structs.md#struct-duration) 实例作为右操作数时，返回乘积为新 [Duration](time_package_structs.md#struct-duration) 实例的乘法运算。

### operator func *(Duration)

```cangjie
operator func *(r: Duration): Duration
```

功能：实现 `T` 类型（`T` 是实现 [DurationExtension](time_package_interfaces.md#interface-durationextension) 接口的类型）和 [Duration](time_package_structs.md#struct-duration) 类型的乘法，即 T * [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 乘法的右操作数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - `T` 类型实例和 `r` 的乘积。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相乘后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### extend Float64 <: DurationExtension

```cangjie
extend Float64 <: DurationExtension
```

功能：拓展了 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型作为左操作数和 [Duration](time_package_structs.md#struct-duration) 类型作为右操作数的乘法运算。

父类型：

- [DurationExtension](#interface-durationextension)

#### operator func *(Duration)

```cangjie
public operator func *(r: Duration): Duration
```

功能：实现 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型和 [Duration](time_package_structs.md#struct-duration) 类型的乘法，即 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) * [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型实例和 `r` 的乘积。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相乘后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### extend Int64 <: DurationExtension

```cangjie
extend Int64 <: DurationExtension
```

功能：拓展了 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型作为左操作数和 [Duration](time_package_structs.md#struct-duration) 类型作为右操作数的乘法运算。

父类型：

- [DurationExtension](#interface-durationextension)

#### operator func *(Duration)

```cangjie
public operator func *(r: Duration): Duration
```

功能：实现 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型和 [Duration](time_package_structs.md#struct-duration) 类型的乘法，即 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) * [Duration](time_package_structs.md#struct-duration) 运算。

例如 2 * [Duration](time_package_structs.md#struct-duration).second 返回表示时间间隔为 2 秒的 [Duration](time_package_structs.md#struct-duration) 实例。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 乘法的右操作数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型实例和 `r` 的乘积。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相乘后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

