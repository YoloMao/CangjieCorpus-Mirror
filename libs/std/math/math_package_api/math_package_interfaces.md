# 接口

## interface MathExtension

```cangjie
public interface MathExtension
```

功能：为了导出 prop 而作辅助接口，辅助导出 Max，Min 属性，浮点数额外导出 NaN，Inf，PI，E，MinDenormal，MinNormal 属性和 isInf，isNaN，isNormal 接口。该辅助接口内部为空。

### extend Float16 <: MathExtension

```cangjie
extend Float16 <: MathExtension
```

功能：拓展半精度浮点数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop E

```cangjie
public static prop E: Float16
```

功能：获取半精度浮点数的自然常数。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### static prop Inf

```cangjie
public static prop Inf: Float16
```

功能：获取半精度浮点数的无穷数。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### static prop Max

```cangjie
public static prop Max: Float16
```

功能：获取半精度浮点数的最大值。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### static prop Min

```cangjie
public static prop Min: Float16
```

功能：获取半精度浮点数的最小值。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### static prop MinDenormal

```cangjie
public static prop MinDenormal: Float16
```

功能：获取半精度浮点数的最小次正规数。最小正次正规数是以 IEEE 双精度格式表示的最小正数。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### static prop MinNormal

```cangjie
public static prop MinNormal: Float16
```

功能：获取半精度浮点数的最小正规数。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### static prop NaN

```cangjie
public static prop NaN: Float16
```

功能：获取半精度浮点数的非数。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### static prop PI

```cangjie
public static prop PI: Float16
```

功能：获取半精度浮点数的圆周率常数。

类型：[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)

#### func isInf()

```cangjie
public func isInf(): Bool
```

功能：判断某个浮点数 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 是否为无穷数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 的值正无穷大或负无穷大，则返回 `true`；否则，返回 `false`。

#### func isNaN()

```cangjie
public func isNaN(): Bool
```

功能：判断某个浮点数 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 是否为非数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 的值为非数值，则返回 `true`；否则，返回 `false`。

#### func isNormal()

```cangjie
public func isNormal(): Bool
```

功能：判断某个浮点数 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 是否为常规数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float16](../../core/core_package_api/core_package_intrinsics.md#float16) 的值是正常的浮点数，返回 `true`；否则，返回 `false`。

### extend Float32 <: MathExtension

```cangjie
extend Float32 <: MathExtension
```

功能：拓展单精度浮点数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop E

```cangjie
public static prop E: Float32
```

功能：获取单精度浮点数的自然常数。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### static prop Inf

```cangjie
public static prop Inf: Float32
```

功能：获取单精度浮点数的无穷数。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### static prop Max

```cangjie
public static prop Max: Float32
```

功能：获取单精度浮点数的最大值。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### static prop Min

```cangjie
public static prop Min: Float32
```

功能：获取单精度浮点数的最小值。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### static prop MinDenormal

```cangjie
public static prop MinDenormal: Float32
```

功能：获取单精度浮点数的最小次正规数。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### static prop MinNormal

```cangjie
public static prop MinNormal: Float32
```

功能：获取单精度浮点数的最小正规数。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### static prop NaN

```cangjie
public static prop NaN: Float32
```

功能：获取单精度浮点数的非数。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### static prop PI

```cangjie
public static prop PI: Float32
```

功能：获取单精度浮点数的圆周率常数。

类型：[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)

#### func isInf()

```cangjie
public func isInf(): Bool
```

功能：判断某个浮点数 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 是否为无穷数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 的值正无穷大或负无穷大，则返回 `true`；否则，返回 `false`。

#### func isNaN()

```cangjie
public func isNaN(): Bool
```

功能：判断某个浮点数 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 是否为非数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 的值为非数值，则返回 `true`；否则，返回 `false`。

#### func isNormal()

```cangjie
public func isNormal(): Bool
```

功能：判断某个浮点数 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 是否为常规数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float32](../../core/core_package_api/core_package_intrinsics.md#float32) 的值是正常的浮点数，返回 `true`；否则，返回 `false`。

### extend Float64 <: MathExtension

```cangjie
extend Float64 <: MathExtension
```

功能：拓展双精度浮点数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop E

```cangjie
public static prop E: Float64
```

功能：获取双精度浮点数的自然常数。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### static prop Inf

```cangjie
public static prop Inf: Float64
```

功能：获取双精度浮点数的无穷数。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### static prop Max

```cangjie
public static prop Max: Float64
```

功能：获取双精度浮点数的最大值。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### static prop Min

```cangjie
public static prop Min: Float64
```

功能：获取双精度浮点数的最小值。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### static prop MinDenormal

```cangjie
public static prop MinDenormal: Float64
```

功能：获取双精度浮点数的最小次正规数。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### static prop MinNormal

```cangjie
public static prop MinNormal: Float64
```

功能：获取双精度浮点数的最小正规数。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### static prop NaN

```cangjie
public static prop NaN: Float64
```

功能：获取双精度浮点数的非数。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### static prop PI

```cangjie
public static prop PI: Float64
```

功能：获取双精度浮点数的圆周率常数。

类型：[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)

#### func isInf()

```cangjie
public func isInf(): Bool
```

功能：判断某个浮点数 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 是否为无穷数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 的值正无穷大或负无穷大，则返回 `true`；否则，返回 `false`。

#### func isNaN()

```cangjie
public func isNaN(): Bool
```

功能：判断某个浮点数 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 是否为非数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 的值为非数值，则返回 `true`；否则，返回 `false`。

#### func isNormal()

```cangjie
public func isNormal(): Bool
```

功能：判断某个浮点数 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 是否为常规数值。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 的值是正常的浮点数，返回 `true`；否则，返回 `false`。

### extend Int16 <: MathExtension

```cangjie
extend Int16 <: MathExtension
```

功能：拓展 16 位有符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: Int16
```

功能：获取 16 位有符号整数的最大值。

类型：[Int16](../../core/core_package_api/core_package_intrinsics.md#int16)

#### static prop Min

```cangjie
public static prop Min: Int16
```

功能：获取 16 位有符号整数的最小值。

类型：[Int16](../../core/core_package_api/core_package_intrinsics.md#int16)

### extend Int32 <: MathExtension

```cangjie
extend Int32 <: MathExtension
```

功能：拓展 32 位有符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: Int32
```

功能：获取 32 位有符号整数的最大值。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

#### static prop Min

```cangjie
public static prop Min: Int32
```

功能：获取 32 位有符号整数的最小值。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

### extend Int64 <: MathExtension

```cangjie
extend Int64 <: MathExtension
```

功能：拓展 64 位有符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: Int64
```

功能：获取 64 位有符号整数的最大值。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

#### static prop Min

```cangjie
public static prop Min: Int64
```

功能：获取 64 位有符号整数的最小值。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### extend Int8 <: MathExtension

```cangjie
extend Int8 <: MathExtension
```

功能：拓展 8 位有符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: Int8
```

功能：获取 8 位有符号整数的最大值。

类型：[Int8](../../core/core_package_api/core_package_intrinsics.md#int8)

#### static prop Min

```cangjie
public static prop Min: Int8
```

功能：获取 8 位有符号整数的最小值。

类型：[Int8](../../core/core_package_api/core_package_intrinsics.md#int8)

### extend IntNative <: MathExtension

```cangjie
extend IntNative <: MathExtension
```

功能：拓展平台相关有符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: IntNative
```

功能：获取平台相关有符号整数的最大值。

类型：[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative)

#### static prop Min

```cangjie
public static prop Min: IntNative
```

功能：获取平台相关有符号整数的最小值。

类型：[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative)

### extend UInt16 <: MathExtension

```cangjie
extend UInt16 <: MathExtension
```

功能：拓展 16 位无符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: UInt16
```

功能：获取 16 位无符号整数的最大值。

类型：[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)

#### static prop Min

```cangjie
public static prop Min: UInt16
```

功能：获取 16 位无符号整数的最小值。

类型：[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)

### extend UInt32 <: MathExtension

```cangjie
extend UInt32 <: MathExtension
```

功能：拓展 32 位无符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: UInt32
```

功能：获取 32 位无符号整数的最大值。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

#### static prop Min

```cangjie
public static prop Min: UInt32
```

功能：获取 32 位无符号整数的最小值。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

### extend UInt64 <: MathExtension

```cangjie
extend UInt64 <: MathExtension
```

功能：拓展 64 位无符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: UInt64
```

功能：获取 64 位无符号整数的最大值。

类型：[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)

#### static prop Min

```cangjie
public static prop Min: UInt64
```

功能：获取 64 位无符号整数的最小值。

类型：[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)

### extend UInt8 <: MathExtension

```cangjie
extend UInt8 <: MathExtension
```

功能：拓展 8 位无符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: UInt8
```

功能：获取 8 位无符号整数的最大值。

类型：[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)

#### static prop Min

```cangjie
public static prop Min: UInt8
```

功能：获取 8 位无符号整数的最小值。

类型：[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)

### extend UIntNative <: MathExtension

```cangjie
extend UIntNative <: MathExtension
```

功能：拓展平台相关无符号整数以支持一些数学常数。

父类型：

- [MathExtension](#interface-mathextension)

#### static prop Max

```cangjie
public static prop Max: UIntNative
```

功能：获取平台相关无符号整数的最大值。

类型：类型：[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)

#### static prop Min

```cangjie
public static prop Min: UIntNative
```

功能：获取平台相关无符号整数的最小值。

类型：[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)
