# 接口

## interface CheckedOp\<T>

```cangjie
public interface CheckedOp<T> {
    func checkedAdd(y: T): ?T
    func checkedDec(): ?T
    func checkedDiv(y: T): ?T
    func checkedInc(): ?T
    func checkedMod(y: T): ?T
    func checkedMul(y: T): ?T
    func checkedNeg(): ?T
    func checkedShl(y: T): ?T
    func checkedShr(y: T): ?T
    func checkedSub(y: T): ?T
}
```

功能：当整数运算出现溢出，返回 `None`。

### func checkedAdd(T)

```cangjie
func checkedAdd(y: T): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

参数：

- y: T - 加数。

返回值：

- ?T - 加法运算结果。

### func checkedDec()

```cangjie
func checkedDec(): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

返回值：

- ?T - 自减运算结果。

### func checkedDiv(T)

```cangjie
func checkedDiv(y: T): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- ?T - 除法运算结果。

### func checkedInc()

```cangjie
func checkedInc(): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

返回值：

- ?T - 自增运算结果。

### func checkedMod(T)

```cangjie
func checkedMod(y: T): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- ?T - 取余运算结果。

### func checkedMul(T)

```cangjie
func checkedMul(y: T): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

参数：

- y: T - 乘数。

返回值：

- ?T - 乘法运算结果。

### func checkedNeg()

```cangjie
func checkedNeg(): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

返回值：

- ?T - 负号运算结果。

### func checkedShl(T)

```cangjie
func checkedShl(y: T): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 `?T.None`，否则返回运算结果。

参数：

- y: T - 移位位数。

返回值：

- ?T - 左移运算结果。

### func checkedShr(T)

```cangjie
func checkedShr(y: T): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 `?T.None`，否则返回运算结果。

参数：

- y: T - 移位位数。

返回值：

- ?T - 右移运算结果。

### func checkedSub(T)

```cangjie
func checkedSub(y: T): ?T
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 `?T.None`，否则返回运算结果。

参数：

- y: T - 减数。

返回值：

- ?T - 减法运算结果。

### extend Int16 <: CheckedOp\<Int16>

```cangjie
extend Int16 <: CheckedOp<Int16>
```

功能：为 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[Int16](../../core/core_package_api/core_package_intrinsics.md#int16)>

#### func checkedAdd(Int16)

```cangjie
public func checkedAdd(y: Int16): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加数。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自减运算结果。

#### func checkedDiv(Int16)

```cangjie
public func checkedDiv(y: Int16): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自增运算结果。

#### func checkedMod(Int16)

```cangjie
public func checkedMod(y: Int16): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 取余运算结果。

#### func checkedMul(Int16)

```cangjie
public func checkedMul(y: Int16): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘数。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 负号运算结果。

#### func checkedShl(Int16)

```cangjie
public func checkedShl(y: Int16): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 左移运算结果。

#### func checkedShr(Int16)

```cangjie
public func checkedShr(y: Int16): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 右移运算结果。

#### func checkedSub(Int16)

```cangjie
public func checkedSub(y: Int16): ?Int16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16).None，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减数。

返回值：

- ?[Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减法运算结果。

### extend Int32 <: CheckedOp\<Int32>

```cangjie
extend Int32 <: CheckedOp<Int32>
```

功能：为 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)>

#### func checkedAdd(Int32)

```cangjie
public func checkedAdd(y: Int32): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加数。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自减运算结果。

#### func checkedDiv(Int32)

```cangjie
public func checkedDiv(y: Int32): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自增运算结果。

#### func checkedMod(Int32)

```cangjie
public func checkedMod(y: Int32): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 取余运算结果。

#### func checkedMul(Int32)

```cangjie
public func checkedMul(y: Int32): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘数。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 负号运算结果。

#### func checkedShl(Int32)

```cangjie
public func checkedShl(y: Int32): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 左移运算结果。

#### func checkedShr(Int32)

```cangjie
public func checkedShr(y: Int32): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 右移运算结果。

#### func checkedSub(Int32)

```cangjie
public func checkedSub(y: Int32): ?Int32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32).None，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减数。

返回值：

- ?[Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减法运算结果。

### extend Int64 <: CheckedOp\<Int64>

```cangjie
extend Int64 <: CheckedOp<Int64>
```

功能：为 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)>

#### func checkedAdd(Int64)

```cangjie
public func checkedAdd(y: Int64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自减运算结果。

#### func checkedDiv(Int64)

```cangjie
public func checkedDiv(y: Int64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自增运算结果。

#### func checkedMod(Int64)

```cangjie
public func checkedMod(y: Int64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 取余运算结果。

#### func checkedMul(Int64)

```cangjie
public func checkedMul(y: Int64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 负号运算结果。

#### func checkedPow(UInt64)

```cangjie
public func checkedPow(y: UInt64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的幂运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 指数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 幂运算结果。

#### func checkedShl(Int64)

```cangjie
public func checkedShl(y: Int64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 左移运算结果。

#### func checkedShr(Int64)

```cangjie
public func checkedShr(y: Int64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 右移运算结果。

#### func checkedSub(Int64)

```cangjie
public func checkedSub(y: Int64): ?Int64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64).None，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减数。

返回值：

- ?[Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减法运算结果。

### extend Int8 <: CheckedOp\<Int8>

```cangjie
extend Int8 <: CheckedOp<Int8>
```

功能：为 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[Int8](../../core/core_package_api/core_package_intrinsics.md#int8)>

#### func checkedAdd(Int8)

```cangjie
public func checkedAdd(y: Int8): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加数。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自减运算结果。

#### func checkedDiv(Int8)

```cangjie
public func checkedDiv(y: Int8): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自增运算结果。

#### func checkedMod(Int8)

```cangjie
public func checkedMod(y: Int8): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 取余运算结果。

#### func checkedMul(Int8)

```cangjie
public func checkedMul(y: Int8): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘数。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 负号运算结果。

#### func checkedShl(Int8)

```cangjie
public func checkedShl(y: Int8): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 左移运算结果。

#### func checkedShr(Int8)

```cangjie
public func checkedShr(y: Int8): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 右移运算结果。

#### func checkedSub(Int8)

```cangjie
public func checkedSub(y: Int8): ?Int8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8).None，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减数。

返回值：

- ?[Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减法运算结果。

### extend IntNative <: CheckedOp\<IntNative>

```cangjie
extend IntNative <: CheckedOp<IntNative>
```

功能：为 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative)>

#### func checkedAdd(IntNative)

```cangjie
public func checkedAdd(y: IntNative): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加数。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自减运算结果。

#### func checkedDiv(IntNative)

```cangjie
public func checkedDiv(y: IntNative): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自增运算结果。

#### func checkedMod(IntNative)

```cangjie
public func checkedMod(y: IntNative): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 取余运算结果。

#### func checkedMul(IntNative)

```cangjie
public func checkedMul(y: IntNative): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘数。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 负号运算结果。

#### func checkedShl(IntNative)

```cangjie
public func checkedShl(y: IntNative): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 左移运算结果。

#### func checkedShr(IntNative)

```cangjie
public func checkedShr(y: IntNative): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数或小于 0 时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 右移运算结果。

#### func checkedSub(IntNative)

```cangjie
public func checkedSub(y: IntNative): ?IntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative).None，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减数。

返回值：

- ?[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减法运算结果。

### extend UInt16 <: CheckedOp\<UInt16>

```cangjie
extend UInt16 <: CheckedOp<UInt16>
```

功能：为 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)>

#### func checkedAdd(UInt16)

```cangjie
public func checkedAdd(y: UInt16): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加数。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自减运算结果。

#### func checkedDiv(UInt16)

```cangjie
public func checkedDiv(y: UInt16): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自增运算结果。

#### func checkedMod(UInt16)

```cangjie
public func checkedMod(y: UInt16): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 取余运算结果。

#### func checkedMul(UInt16)

```cangjie
public func checkedMul(y: UInt16): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘数。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 负号运算结果。

#### func checkedShl(UInt16)

```cangjie
public func checkedShl(y: UInt16): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 左移运算结果。

#### func checkedShr(UInt16)

```cangjie
public func checkedShr(y: UInt16): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 右移运算结果。

#### func checkedSub(UInt16)

```cangjie
public func checkedSub(y: UInt16): ?UInt16
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16).None，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减数。

返回值：

- ?[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减法运算结果。

### extend UInt32 <: CheckedOp\<UInt32>

```cangjie
extend UInt32 <: CheckedOp<UInt32>
```

功能：为 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)>

#### func checkedAdd(UInt32)

```cangjie
public func checkedAdd(y: UInt32): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加数。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自减运算结果。

#### func checkedDiv(UInt32)

```cangjie
public func checkedDiv(y: UInt32): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自增运算结果。

#### func checkedMod(UInt32)

```cangjie
public func checkedMod(y: UInt32): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 取余运算结果。

#### func checkedMul(UInt32)

```cangjie
public func checkedMul(y: UInt32): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘数。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 负号运算结果。

#### func checkedShl(UInt32)

```cangjie
public func checkedShl(y: UInt32): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 左移运算结果。

#### func checkedShr(UInt32)

```cangjie
public func checkedShr(y: UInt32): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 右移运算结果。

#### func checkedSub(UInt32)

```cangjie
public func checkedSub(y: UInt32): ?UInt32
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32).None，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减数。

返回值：

- ?[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减法运算结果。

### extend UInt64 <: CheckedOp\<UInt64>

```cangjie
extend UInt64 <: CheckedOp<UInt64>
```

功能：为 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)>

#### func checkedAdd(UInt64)

```cangjie
public func checkedAdd(y: UInt64): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加数。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自减运算结果。

#### func checkedDiv(UInt64)

```cangjie
public func checkedDiv(y: UInt64): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自增运算结果。

#### func checkedMod(UInt64)

```cangjie
public func checkedMod(y: UInt64): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 取余运算结果。

#### func checkedMul(UInt64)

```cangjie
public func checkedMul(y: UInt64): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘数。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 负号运算结果。

#### func checkedShl(UInt64)

```cangjie
public func checkedShl(y: UInt64): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 左移运算结果。

#### func checkedShr(UInt64)

```cangjie
public func checkedShr(y: UInt64): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 右移运算结果。

#### func checkedSub(UInt64)

```cangjie
public func checkedSub(y: UInt64): ?UInt64
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64).None，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减数。

返回值：

- ?[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减法运算结果。

### extend UInt8 <: CheckedOp\<UInt8>

```cangjie
extend UInt8 <: CheckedOp<UInt8>
```

功能：为 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)>

#### func checkedAdd(UInt8)

```cangjie
public func checkedAdd(y: UInt8): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加数。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自减运算结果。

#### func checkedDiv(UInt8)

```cangjie
public func checkedDiv(y: UInt8): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自增运算结果。

#### func checkedMod(UInt8)

```cangjie
public func checkedMod(y: UInt8): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 取余运算结果。

#### func checkedMul(UInt8)

```cangjie
public func checkedMul(y: UInt8): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘数。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 负号运算结果。

#### func checkedShl(UInt8)

```cangjie
public func checkedShl(y: UInt8): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 左移运算结果。

#### func checkedShr(UInt8)

```cangjie
public func checkedShr(y: UInt8): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 右移运算结果。

#### func checkedSub(UInt8)

```cangjie
public func checkedSub(y: UInt8): ?UInt8
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8).None，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减数。

返回值：

- ?[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减法运算结果。

### extend UIntNative <: CheckedOp\<UIntNative>

```cangjie
extend UIntNative <: CheckedOp<UIntNative>
```

功能：为 [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) 实现 [CheckedOp](#interface-checkedopt) 接口。

父类型：

- [CheckedOp](#interface-checkedopt)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)>

#### func checkedAdd(UIntNative)

```cangjie
public func checkedAdd(y: UIntNative): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的加法运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加数。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加法运算结果。

#### func checkedDec()

```cangjie
public func checkedDec(): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自减运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自减运算结果。

#### func checkedDiv(UIntNative)

```cangjie
public func checkedDiv(y: UIntNative): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的除法运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除法运算结果。

#### func checkedInc()

```cangjie
public func checkedInc(): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的自增运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自增运算结果。

#### func checkedMod(UIntNative)

```cangjie
public func checkedMod(y: UIntNative): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的取余运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 取余运算结果。

#### func checkedMul(UIntNative)

```cangjie
public func checkedMul(y: UIntNative): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的乘法运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘数。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘法运算结果。

#### func checkedNeg()

```cangjie
public func checkedNeg(): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的负号运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 负号运算结果。

#### func checkedShl(UIntNative)

```cangjie
public func checkedShl(y: UIntNative): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的左移运算。

当移位位数大于等于操作数位数时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 左移运算结果。

#### func checkedShr(UIntNative)

```cangjie
public func checkedShr(y: UIntNative): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的右移运算。

当移位位数大于等于操作数位数时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 右移运算结果。

#### func checkedSub(UIntNative)

```cangjie
public func checkedSub(y: UIntNative): ?UIntNative
```

功能：使用返回 [Option](../../core/core_package_api/core_package_enums.md#enum-optiont) 策略的减法运算。

当运算出现溢出时，返回 ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative).None，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减数。

返回值：

- ?[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减法运算结果。

## interface SaturatingOp\<T>

```cangjie
public interface SaturatingOp<T> {
    func saturatingAdd(y: T): T
    func saturatingDec(): T
    func saturatingDiv(y: T): T
    func saturatingInc(): T
    func saturatingMod(y: T): T
    func saturatingMul(y: T): T
    func saturatingNeg(): T
    func saturatingShl(y: T): T
    func saturatingShr(y: T): T
    func saturatingSub(y: T): T
}
```

功能：当整数运算出现溢出，饱和处理。

### func saturatingAdd(T)

```cangjie
func saturatingAdd(y: T): T
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: T - 加数。

返回值：

- T - 加法运算结果。

### func saturatingDec()

```cangjie
func saturatingDec(): T
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- T - 自减运算结果。

### func saturatingDiv(T)

```cangjie
func saturatingDiv(y: T): T
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- T - 除法运算结果。

### func saturatingInc()

```cangjie
func saturatingInc(): T
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- T - 自增运算结果。

### func saturatingMod(T)

```cangjie
func saturatingMod(y: T): T
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- T - 取余运算结果。

### func saturatingMul(T)

```cangjie
func saturatingMul(y: T): T
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: T - 乘数。

返回值：

- T - 乘法运算结果。

### func saturatingNeg()

```cangjie
func saturatingNeg(): T
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- T - 负号运算结果。

### func saturatingShl(T)

```cangjie
func saturatingShl(y: T): T
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: T - 移位位数。

返回值：

- T - 左移运算结果。

### func saturatingShr(T)

```cangjie
func saturatingShr(y: T): T
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: T - 移位位数。

返回值：

- T - 右移运算结果。

### func saturatingSub(T)

```cangjie
func saturatingSub(y: T): T
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: T - 减数。

返回值：

- T - 减法运算结果。

### extend Int16 <: SaturatingOp\<Int16>

```cangjie
extend Int16 <: SaturatingOp<Int16>
```

功能：为 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[Int16](../../core/core_package_api/core_package_intrinsics.md#int16)>

#### func saturatingAdd(Int16)

```cangjie
public func saturatingAdd(y: Int16): Int16
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): Int16
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自减运算结果。

#### func saturatingDiv(Int16)

```cangjie
public func saturatingDiv(y: Int16): Int16
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): Int16
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自增运算结果。

#### func saturatingMod(Int16)

```cangjie
public func saturatingMod(y: Int16): Int16
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 取余运算结果。

#### func saturatingMul(Int16)

```cangjie
public func saturatingMul(y: Int16): Int16
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): Int16
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 负号运算结果。

#### func saturatingShl(Int16)

```cangjie
public func saturatingShl(y: Int16): Int16
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 左移运算结果。

#### func saturatingShr(Int16)

```cangjie
public func saturatingShr(y: Int16): Int16
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 右移运算结果。

#### func saturatingSub(Int16)

```cangjie
public func saturatingSub(y: Int16): Int16
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减法运算结果。

### extend Int32 <: SaturatingOp\<Int32>

```cangjie
extend Int32 <: SaturatingOp<Int32>
```

功能：为 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)>

#### func saturatingAdd(Int32)

```cangjie
public func saturatingAdd(y: Int32): Int32
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): Int32
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自减运算结果。

#### func saturatingDiv(Int32)

```cangjie
public func saturatingDiv(y: Int32): Int32
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): Int32
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自增运算结果。

#### func saturatingMod(Int32)

```cangjie
public func saturatingMod(y: Int32): Int32
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 取余运算结果。

#### func saturatingMul(Int32)

```cangjie
public func saturatingMul(y: Int32): Int32
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): Int32
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 负号运算结果。

#### func saturatingShl(Int32)

```cangjie
public func saturatingShl(y: Int32): Int32
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 左移运算结果。

#### func saturatingShr(Int32)

```cangjie
public func saturatingShr(y: Int32): Int32
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 右移运算结果。

#### func saturatingSub(Int32)

```cangjie
public func saturatingSub(y: Int32): Int32
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减法运算结果。

### extend Int64 <: SaturatingOp\<Int64>

```cangjie
extend Int64 <: SaturatingOp<Int64>
```

功能：为 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)>

#### func saturatingAdd(Int64)

```cangjie
public func saturatingAdd(y: Int64): Int64
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): Int64
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自减运算结果。

#### func saturatingDiv(Int64)

```cangjie
public func saturatingDiv(y: Int64): Int64
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): Int64
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自增运算结果。

#### func saturatingMod(Int64)

```cangjie
public func saturatingMod(y: Int64): Int64
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 取余运算结果。

#### func saturatingMul(Int64)

```cangjie
public func saturatingMul(y: Int64): Int64
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): Int64
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 负号运算结果。

#### func saturatingPow(UInt64)

```cangjie
public func saturatingPow(y: UInt64): Int64
```

功能：使用饱和策略的幂运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 指数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 幂运算结果。

#### func saturatingShl(Int64)

```cangjie
public func saturatingShl(y: Int64): Int64
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 左移运算结果。

#### func saturatingShr(Int64)

```cangjie
public func saturatingShr(y: Int64): Int64
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 右移运算结果。

#### func saturatingSub(Int64)

```cangjie
public func saturatingSub(y: Int64): Int64
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减法运算结果。

### extend Int8 <: SaturatingOp\<Int8>

```cangjie
extend Int8 <: SaturatingOp<Int8>
```

功能：为 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[Int8](../../core/core_package_api/core_package_intrinsics.md#int8)>

#### func saturatingAdd(Int8)

```cangjie
public func saturatingAdd(y: Int8): Int8
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): Int8
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自减运算结果。

#### func saturatingDiv(Int8)

```cangjie
public func saturatingDiv(y: Int8): Int8
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): Int8
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自增运算结果。

#### func saturatingMod(Int8)

```cangjie
public func saturatingMod(y: Int8): Int8
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 取余运算结果。

#### func saturatingMul(Int8)

```cangjie
public func saturatingMul(y: Int8): Int8
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): Int8
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 负号运算结果。

#### func saturatingShl(Int8)

```cangjie
public func saturatingShl(y: Int8): Int8
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 左移运算结果。

#### func saturatingShr(Int8)

```cangjie
public func saturatingShr(y: Int8): Int8
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 右移运算结果。

#### func saturatingSub(Int8)

```cangjie
public func saturatingSub(y: Int8): Int8
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减法运算结果。

### extend IntNative <: SaturatingOp\<IntNative>

```cangjie
extend IntNative <: SaturatingOp<IntNative>
```

功能：为 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative)>

#### func saturatingAdd(IntNative)

```cangjie
public func saturatingAdd(y: IntNative): IntNative
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): IntNative
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自减运算结果。

#### func saturatingDiv(IntNative)

```cangjie
public func saturatingDiv(y: IntNative): IntNative
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): IntNative
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自增运算结果。

#### func saturatingMod(IntNative)

```cangjie
public func saturatingMod(y: IntNative): IntNative
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 取余运算结果。

#### func saturatingMul(IntNative)

```cangjie
public func saturatingMul(y: IntNative): IntNative
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): IntNative
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 负号运算结果。

#### func saturatingShl(IntNative)

```cangjie
public func saturatingShl(y: IntNative): IntNative
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 左移运算结果。

#### func saturatingShr(IntNative)

```cangjie
public func saturatingShr(y: IntNative): IntNative
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 右移运算结果。

#### func saturatingSub(IntNative)

```cangjie
public func saturatingSub(y: IntNative): IntNative
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减法运算结果。

### extend UInt16 <: SaturatingOp\<UInt16>

```cangjie
extend UInt16 <: SaturatingOp<UInt16>
```

功能：为 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)>

#### func saturatingAdd(UInt16)

```cangjie
public func saturatingAdd(y: UInt16): UInt16
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): UInt16
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自减运算结果。

#### func saturatingDiv(UInt16)

```cangjie
public func saturatingDiv(y: UInt16): UInt16
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): UInt16
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自增运算结果。

#### func saturatingMod(UInt16)

```cangjie
public func saturatingMod(y: UInt16): UInt16
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 取余运算结果。

#### func saturatingMul(UInt16)

```cangjie
public func saturatingMul(y: UInt16): UInt16
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): UInt16
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 负号运算结果。

#### func saturatingShl(UInt16)

```cangjie
public func saturatingShl(y: UInt16): UInt16
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 左移运算结果。

#### func saturatingShr(UInt16)

```cangjie
public func saturatingShr(y: UInt16): UInt16
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 右移运算结果。

#### func saturatingSub(UInt16)

```cangjie
public func saturatingSub(y: UInt16): UInt16
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减法运算结果。

### extend UInt32 <: SaturatingOp\<UInt32>

```cangjie
extend UInt32 <: SaturatingOp<UInt32>
```

功能：为 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)>

#### func saturatingAdd(UInt32)

```cangjie
public func saturatingAdd(y: UInt32): UInt32
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): UInt32
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自减运算结果。

#### func saturatingDiv(UInt32)

```cangjie
public func saturatingDiv(y: UInt32): UInt32
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): UInt32
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自增运算结果。

#### func saturatingMod(UInt32)

```cangjie
public func saturatingMod(y: UInt32): UInt32
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 取余运算结果。

#### func saturatingMul(UInt32)

```cangjie
public func saturatingMul(y: UInt32): UInt32
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): UInt32
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 负号运算结果。

#### func saturatingShl(UInt32)

```cangjie
public func saturatingShl(y: UInt32): UInt32
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 左移运算结果。

#### func saturatingShr(UInt32)

```cangjie
public func saturatingShr(y: UInt32): UInt32
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 右移运算结果。

#### func saturatingSub(UInt32)

```cangjie
public func saturatingSub(y: UInt32): UInt32
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减法运算结果。

### extend UInt64 <: SaturatingOp\<UInt64>

```cangjie
extend UInt64 <: SaturatingOp<UInt64>
```

功能：为 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)>

#### func saturatingAdd(UInt64)

```cangjie
public func saturatingAdd(y: UInt64): UInt64
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): UInt64
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自减运算结果。

#### func saturatingDiv(UInt64)

```cangjie
public func saturatingDiv(y: UInt64): UInt64
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): UInt64
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自增运算结果。

#### func saturatingMod(UInt64)

```cangjie
public func saturatingMod(y: UInt64): UInt64
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 取余运算结果。

#### func saturatingMul(UInt64)

```cangjie
public func saturatingMul(y: UInt64): UInt64
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): UInt64
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 负号运算结果。

#### func saturatingShl(UInt64)

```cangjie
public func saturatingShl(y: UInt64): UInt64
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 左移运算结果。

#### func saturatingShr(UInt64)

```cangjie
public func saturatingShr(y: UInt64): UInt64
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 右移运算结果。

#### func saturatingSub(UInt64)

```cangjie
public func saturatingSub(y: UInt64): UInt64
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减法运算结果。

### extend UInt8 <: SaturatingOp\<UInt8>

```cangjie
extend UInt8 <: SaturatingOp<UInt8>
```

功能：为 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)>

#### func saturatingAdd(UInt8)

```cangjie
public func saturatingAdd(y: UInt8): UInt8
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): UInt8
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自减运算结果。

#### func saturatingDiv(UInt8)

```cangjie
public func saturatingDiv(y: UInt8): UInt8
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): UInt8
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自增运算结果。

#### func saturatingMod(UInt8)

```cangjie
public func saturatingMod(y: UInt8): UInt8
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 取余运算结果。

#### func saturatingMul(UInt8)

```cangjie
public func saturatingMul(y: UInt8): UInt8
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): UInt8
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 负号运算结果。

#### func saturatingShl(UInt8)

```cangjie
public func saturatingShl(y: UInt8): UInt8
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 左移运算结果。

#### func saturatingShr(UInt8)

```cangjie
public func saturatingShr(y: UInt8): UInt8
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 右移运算结果。

#### func saturatingSub(UInt8)

```cangjie
public func saturatingSub(y: UInt8): UInt8
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减法运算结果。

### extend UIntNative <: SaturatingOp\<UIntNative>

```cangjie
extend UIntNative <: SaturatingOp<UIntNative>
```

功能：为 [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) 实现 [SaturatingOp](#interface-saturatingopt) 接口。

父类型：

- [SaturatingOp](#interface-saturatingopt)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)>

#### func saturatingAdd(UIntNative)

```cangjie
public func saturatingAdd(y: UIntNative): UIntNative
```

功能：使用饱和策略的加法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加法运算结果。

#### func saturatingDec()

```cangjie
public func saturatingDec(): UIntNative
```

功能：使用饱和策略的自减运算。

当运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自减运算结果。

#### func saturatingDiv(UIntNative)

```cangjie
public func saturatingDiv(y: UIntNative): UIntNative
```

功能：使用饱和策略的除法运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除法运算结果。

#### func saturatingInc()

```cangjie
public func saturatingInc(): UIntNative
```

功能：使用饱和策略的自增运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自增运算结果。

#### func saturatingMod(UIntNative)

```cangjie
public func saturatingMod(y: UIntNative): UIntNative
```

功能：使用饱和策略的取余运算。

当运算出现上溢时，返回操作数类型的最大值，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 取余运算结果。

#### func saturatingMul(UIntNative)

```cangjie
public func saturatingMul(y: UIntNative): UIntNative
```

功能：使用饱和策略的乘法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘法运算结果。

#### func saturatingNeg()

```cangjie
public func saturatingNeg(): UIntNative
```

功能：使用饱和策略的负号运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 负号运算结果。

#### func saturatingShl(UIntNative)

```cangjie
public func saturatingShl(y: UIntNative): UIntNative
```

功能：使用饱和策略的左移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 左移运算结果。

#### func saturatingShr(UIntNative)

```cangjie
public func saturatingShr(y: UIntNative): UIntNative
```

功能：使用饱和策略的右移运算。

当移位位数大于等于操作数位数时，将移位位数置为操作数位数 - 1，移位位数小于 0 时，将移位位数置为 0，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 右移运算结果。

#### func saturatingSub(UIntNative)

```cangjie
public func saturatingSub(y: UIntNative): UIntNative
```

功能：使用饱和策略的减法运算。

当运算出现上溢时，返回操作数类型的最大值，运算出现下溢时，返回操作数类型的最小值，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减法运算结果。

## interface ThrowingOp\<T>

```cangjie
public interface ThrowingOp<T> {
    func throwingAdd(y: T): T
    func throwingDec(): T
    func throwingDiv(y: T): T
    func throwingInc(): T
    func throwingMod(y: T): T
    func throwingMul(y: T): T
    func throwingNeg(): T
    func throwingShl(y: T): T
    func throwingShr(y: T): T
    func throwingSub(y: T): T
}
```

功能：当整数运算出现溢出，抛出异常。

### func throwingAdd(T)

```cangjie
func throwingAdd(y: T): T
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: T - 加数。

返回值：

- T - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

### func throwingDec()

```cangjie
func throwingDec(): T
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- T - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

### func throwingDiv(T)

```cangjie
func throwingDiv(y: T): T
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- T - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

### func throwingInc()

```cangjie
func throwingInc(): T
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- T - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

### func throwingMod(T)

```cangjie
func throwingMod(y: T): T
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- T - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

### func throwingMul(T)

```cangjie
func throwingMul(y: T): T
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: T - 乘数。

返回值：

- T - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

### func throwingNeg()

```cangjie
func throwingNeg(): T
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- T - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

### func throwingShl(T)

```cangjie
func throwingShl(y: T): T
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: T - 移位位数。

返回值：

- T - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

### func throwingShr(T)

```cangjie
func throwingShr(y: T): T
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: T - 移位位数。

返回值：

- T - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

### func throwingSub(T)

```cangjie
func throwingSub(y: T): T
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: T - 减数。

返回值：

- T - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend Int16 <: ThrowingOp\<Int16>

```cangjie
extend Int16 <: ThrowingOp<Int16>
```

功能：为 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[Int16](../../core/core_package_api/core_package_intrinsics.md#int16)>

#### func throwingAdd(Int16)

```cangjie
public func throwingAdd(y: Int16): Int16
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): Int16
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(Int16)

```cangjie
public func throwingDiv(y: Int16): Int16
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): Int16
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(Int16)

```cangjie
public func throwingMod(y: Int16): Int16
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(Int16)

```cangjie
public func throwingMul(y: Int16): Int16
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): Int16
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(Int16)

```cangjie
public func throwingShl(y: Int16): Int16
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingShr(Int16)

```cangjie
public func throwingShr(y: Int16): Int16
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingSub(Int16)

```cangjie
public func throwingSub(y: Int16): Int16
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend Int32 <: ThrowingOp\<Int32>

```cangjie
extend Int32 <: ThrowingOp<Int32>
```

功能：为 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)>

#### func throwingAdd(Int32)

```cangjie
public func throwingAdd(y: Int32): Int32
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): Int32
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(Int32)

```cangjie
public func throwingDiv(y: Int32): Int32
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): Int32
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(Int32)

```cangjie
public func throwingMod(y: Int32): Int32
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(Int32)

```cangjie
public func throwingMul(y: Int32): Int32
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): Int32
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(Int32)

```cangjie
public func throwingShl(y: Int32): Int32
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingShr(Int32)

```cangjie
public func throwingShr(y: Int32): Int32
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingSub(Int32)

```cangjie
public func throwingSub(y: Int32): Int32
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend Int64 <: ThrowingOp\<Int64>

```cangjie
extend Int64 <: ThrowingOp<Int64>
```

功能：为 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)>

#### func throwingAdd(Int64)

```cangjie
public func throwingAdd(y: Int64): Int64
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): Int64
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(Int64)

```cangjie
public func throwingDiv(y: Int64): Int64
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): Int64
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(Int64)

```cangjie
public func throwingMod(y: Int64): Int64
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(Int64)

```cangjie
public func throwingMul(y: Int64): Int64
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): Int64
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingPow(UInt64)

```cangjie
public func throwingPow(y: UInt64): Int64
```

功能：使用抛出异常策略的幂运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 指数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 幂运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当幂运算出现溢出时，抛出异常。

#### func throwingShl(Int64)

```cangjie
public func throwingShl(y: Int64): Int64
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingShr(Int64)

```cangjie
public func throwingShr(y: Int64): Int64
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingSub(Int64)

```cangjie
public func throwingSub(y: Int64): Int64
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend Int8 <: ThrowingOp\<Int8>

```cangjie
extend Int8 <: ThrowingOp<Int8>
```

功能：为 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[Int8](../../core/core_package_api/core_package_intrinsics.md#int8)>

#### func throwingAdd(Int8)

```cangjie
public func throwingAdd(y: Int8): Int8
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): Int8
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(Int8)

```cangjie
public func throwingDiv(y: Int8): Int8
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): Int8
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(Int8)

```cangjie
public func throwingMod(y: Int8): Int8
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(Int8)

```cangjie
public func throwingMul(y: Int8): Int8
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): Int8
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(Int8)

```cangjie
public func throwingShl(y: Int8): Int8
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingShr(Int8)

```cangjie
public func throwingShr(y: Int8): Int8
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingSub(Int8)

```cangjie
public func throwingSub(y: Int8): Int8
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend IntNative <: ThrowingOp\<IntNative>

```cangjie
extend IntNative <: ThrowingOp<IntNative>
```

功能：为 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative)>

#### func throwingAdd(IntNative)

```cangjie
public func throwingAdd(y: IntNative): IntNative
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): IntNative
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(IntNative)

```cangjie
public func throwingDiv(y: IntNative): IntNative
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): IntNative
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(IntNative)

```cangjie
public func throwingMod(y: IntNative): IntNative
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(IntNative)

```cangjie
public func throwingMul(y: IntNative): IntNative
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): IntNative
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(IntNative)

```cangjie
public func throwingShl(y: IntNative): IntNative
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingShr(IntNative)

```cangjie
public func throwingShr(y: IntNative): IntNative
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。
- [UndershiftException](overflow_package_exceptions.md#class-undershiftexception) - 当移位位数小于 0 时，抛出异常。

#### func throwingSub(IntNative)

```cangjie
public func throwingSub(y: IntNative): IntNative
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend UInt16 <: ThrowingOp\<UInt16>

```cangjie
extend UInt16 <: ThrowingOp<UInt16>
```

功能：为 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)>

#### func throwingAdd(UInt16)

```cangjie
public func throwingAdd(y: UInt16): UInt16
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): UInt16
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(UInt16)

```cangjie
public func throwingDiv(y: UInt16): UInt16
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): UInt16
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(UInt16)

```cangjie
public func throwingMod(y: UInt16): UInt16
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(UInt16)

```cangjie
public func throwingMul(y: UInt16): UInt16
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): UInt16
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(UInt16)

```cangjie
public func throwingShl(y: UInt16): UInt16
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingShr(UInt16)

```cangjie
public func throwingShr(y: UInt16): UInt16
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingSub(UInt16)

```cangjie
public func throwingSub(y: UInt16): UInt16
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend UInt32 <: ThrowingOp\<UInt32>

```cangjie
extend UInt32 <: ThrowingOp<UInt32>
```

功能：为 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)>

#### func throwingAdd(UInt32)

```cangjie
public func throwingAdd(y: UInt32): UInt32
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): UInt32
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(UInt32)

```cangjie
public func throwingDiv(y: UInt32): UInt32
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): UInt32
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(UInt32)

```cangjie
public func throwingMod(y: UInt32): UInt32
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(UInt32)

```cangjie
public func throwingMul(y: UInt32): UInt32
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): UInt32
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(UInt32)

```cangjie
public func throwingShl(y: UInt32): UInt32
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingShr(UInt32)

```cangjie
public func throwingShr(y: UInt32): UInt32
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingSub(UInt32)

```cangjie
public func throwingSub(y: UInt32): UInt32
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend UInt64 <: ThrowingOp\<UInt64>

```cangjie
extend UInt64 <: ThrowingOp<UInt64>
```

功能：为 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)>

#### func throwingAdd(UInt64)

```cangjie
public func throwingAdd(y: UInt64): UInt64
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): UInt64
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(UInt64)

```cangjie
public func throwingDiv(y: UInt64): UInt64
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): UInt64
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(UInt64)

```cangjie
public func throwingMod(y: UInt64): UInt64
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(UInt64)

```cangjie
public func throwingMul(y: UInt64): UInt64
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): UInt64
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(UInt64)

```cangjie
public func throwingShl(y: UInt64): UInt64
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingShr(UInt64)

```cangjie
public func throwingShr(y: UInt64): UInt64
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingSub(UInt64)

```cangjie
public func throwingSub(y: UInt64): UInt64
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend UInt8 <: ThrowingOp\<UInt8>

```cangjie
extend UInt8 <: ThrowingOp<UInt8>
```

功能：为 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)>

#### func throwingAdd(UInt8)

```cangjie
public func throwingAdd(y: UInt8): UInt8
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): UInt8
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(UInt8)

```cangjie
public func throwingDiv(y: UInt8): UInt8
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): UInt8
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(UInt8)

```cangjie
public func throwingMod(y: UInt8): UInt8
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(UInt8)

```cangjie
public func throwingMul(y: UInt8): UInt8
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): UInt8
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(UInt8)

```cangjie
public func throwingShl(y: UInt8): UInt8
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingShr(UInt8)

```cangjie
public func throwingShr(y: UInt8): UInt8
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingSub(UInt8)

```cangjie
public func throwingSub(y: UInt8): UInt8
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

### extend UIntNative <: ThrowingOp\<UIntNative>

```cangjie
extend UIntNative <: ThrowingOp<UIntNative>
```

功能：为 [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) 实现 [ThrowingOp](#interface-throwingopt) 接口。

父类型：

- [ThrowingOp](#interface-throwingopt)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)>

#### func throwingAdd(UIntNative)

```cangjie
public func throwingAdd(y: UIntNative): UIntNative
```

功能：使用抛出异常策略的加法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当加法运算出现溢出时，抛出异常。

#### func throwingDec()

```cangjie
public func throwingDec(): UIntNative
```

功能：使用抛出异常策略的自减运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自减运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自减运算出现溢出时，抛出异常。

#### func throwingDiv(UIntNative)

```cangjie
public func throwingDiv(y: UIntNative): UIntNative
```

功能：使用抛出异常策略的除法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当除法运算出现溢出时，抛出异常。

#### func throwingInc()

```cangjie
public func throwingInc(): UIntNative
```

功能：使用抛出异常策略的自增运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自增运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当自增运算出现溢出时，抛出异常。

#### func throwingMod(UIntNative)

```cangjie
public func throwingMod(y: UIntNative): UIntNative
```

功能：使用抛出异常策略的取余运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 取余运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当取余运算出现溢出时，抛出异常。

#### func throwingMul(UIntNative)

```cangjie
public func throwingMul(y: UIntNative): UIntNative
```

功能：使用抛出异常策略的乘法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当乘法运算出现溢出时，抛出异常。

#### func throwingNeg()

```cangjie
public func throwingNeg(): UIntNative
```

功能：使用抛出异常策略的负号运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 负号运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当负号运算出现溢出时，抛出异常。

#### func throwingShl(UIntNative)

```cangjie
public func throwingShl(y: UIntNative): UIntNative
```

功能：使用抛出异常策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，抛出异常，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 左移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingShr(UIntNative)

```cangjie
public func throwingShr(y: UIntNative): UIntNative
```

功能：右移运算。

当移位位数大于等于操作数位数时，抛出异常，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 右移运算结果。

异常：

- [OvershiftException](overflow_package_exceptions.md#class-overshiftexception) - 当移位位数大于等于操作数位数时，抛出异常。

#### func throwingSub(UIntNative)

```cangjie
public func throwingSub(y: UIntNative): UIntNative
```

功能：使用抛出异常策略的减法运算。

当运算出现溢出时，抛出异常，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减法运算结果。

异常：

- [OverflowException](../../core/core_package_api/core_package_exceptions.md#class-overflowexception) - 当减法运算出现溢出时，抛出异常。

## interface WrappingOp\<T>

```cangjie
public interface WrappingOp<T> {
    func wrappingAdd(y: T): T
    func wrappingDec(): T
    func wrappingDiv(y: T): T
    func wrappingInc(): T
    func wrappingMod(y: T): T
    func wrappingMul(y: T): T
    func wrappingNeg(): T
    func wrappingShl(y: T): T
    func wrappingShr(y: T): T
    func wrappingSub(y: T): T
}
```

功能：当整数运算出现溢出，高位截断。

### func wrappingAdd(T)

```cangjie
func wrappingAdd(y: T): T
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: T - 加数。

返回值：

- T - 加法运算结果。

### func wrappingDec()

```cangjie
func wrappingDec(): T
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- T - 自减运算结果。

### func wrappingDiv(T)

```cangjie
func wrappingDiv(y: T): T
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- T - 除法运算结果。

### func wrappingInc()

```cangjie
func wrappingInc(): T
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- T - 自增运算结果。

### func wrappingMod(T)

```cangjie
func wrappingMod(y: T): T
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: T - 除数。

返回值：

- T - 取余运算结果。

### func wrappingMul(T)

```cangjie
func wrappingMul(y: T): T
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: T - 乘数。

返回值：

- T - 乘法运算结果。

### func wrappingNeg()

```cangjie
func wrappingNeg(): T
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- T - 负号运算结果。

### func wrappingShl(T)

```cangjie
func wrappingShl(y: T): T
```

功能：使用高位截断策略的左移运算。

当移位位数大于等于操作数位数或小于 0 时，高位截断。例如，对 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的数进行移位，当 y (移位位数)超大于等于 8时，仅取 y 的低 3 位作为移位位数，以此保证移位位数在 0 到 7 之间。

参数：

- y: T - 移位位数。

返回值：

- T - 左移运算结果。

### func wrappingShr(T)

```cangjie
func wrappingShr(y: T): T
```

功能：使用高位截断策略的右移运算。

当移位位数大于等于操作数位数或小于 0 时，高位截断。例如，对 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 类型的数进行移位，当 y (移位位数)超大于等于 8时，仅取 y 的低 3 位作为移位位数，以此保证移位位数在 0 到 7 之间。

参数：

- y: T - 移位位数。

返回值：

- T - 右移运算结果。

### func wrappingSub(T)

```cangjie
func wrappingSub(y: T): T
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: T - 减数。

返回值：

- T - 减法运算结果。

### extend Int16 <: WrappingOp\<Int16>

```cangjie
extend Int16 <: WrappingOp<Int16>
```

功能：为 [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[Int16](../../core/core_package_api/core_package_intrinsics.md#int16)>

#### func wrappingAdd(Int16)

```cangjie
public func wrappingAdd(y: Int16): Int16
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): Int16
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自减运算结果。

#### func wrappingDiv(Int16)

```cangjie
public func wrappingDiv(y: Int16): Int16
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): Int16
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 自增运算结果。

#### func wrappingMod(Int16)

```cangjie
public func wrappingMod(y: Int16): Int16
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 除数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 取余运算结果。

#### func wrappingMul(Int16)

```cangjie
public func wrappingMul(y: Int16): Int16
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): Int16
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 负号运算结果。

#### func wrappingShl(Int16)

```cangjie
public func wrappingShl(y: Int16): Int16
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 4 位作为移位位数。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 左移运算结果。

#### func wrappingShr(Int16)

```cangjie
public func wrappingShr(y: Int16): Int16
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 4 位作为移位位数。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 移位位数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 右移运算结果。

#### func wrappingSub(Int16)

```cangjie
public func wrappingSub(y: Int16): Int16
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减数。

返回值：

- [Int16](../../core/core_package_api/core_package_intrinsics.md#int16) - 减法运算结果。

### extend Int32 <: WrappingOp\<Int32>

```cangjie
extend Int32 <: WrappingOp<Int32>
```

功能：为 [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)>

#### func wrappingAdd(Int32)

```cangjie
public func wrappingAdd(y: Int32): Int32
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): Int32
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自减运算结果。

#### func wrappingDiv(Int32)

```cangjie
public func wrappingDiv(y: Int32): Int32
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): Int32
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 自增运算结果。

#### func wrappingMod(Int32)

```cangjie
public func wrappingMod(y: Int32): Int32
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 除数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 取余运算结果。

#### func wrappingMul(Int32)

```cangjie
public func wrappingMul(y: Int32): Int32
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): Int32
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 负号运算结果。

#### func wrappingShl(Int32)

```cangjie
public func wrappingShl(y: Int32): Int32
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 5 位作为移位位数。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 左移运算结果。

#### func wrappingShr(Int32)

```cangjie
public func wrappingShr(y: Int32): Int32
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 5 位作为移位位数。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 移位位数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 右移运算结果。

#### func wrappingSub(Int32)

```cangjie
public func wrappingSub(y: Int32): Int32
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减数。

返回值：

- [Int32](../../core/core_package_api/core_package_intrinsics.md#int32) - 减法运算结果。

### extend Int64 <: WrappingOp\<Int64>

```cangjie
extend Int64 <: WrappingOp<Int64>
```

功能：为 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)>

#### func wrappingAdd(Int64)

```cangjie
public func wrappingAdd(y: Int64): Int64
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): Int64
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自减运算结果。

#### func wrappingDiv(Int64)

```cangjie
public func wrappingDiv(y: Int64): Int64
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): Int64
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自增运算结果。

#### func wrappingMod(Int64)

```cangjie
public func wrappingMod(y: Int64): Int64
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 取余运算结果。

#### func wrappingMul(Int64)

```cangjie
public func wrappingMul(y: Int64): Int64
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): Int64
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 负号运算结果。

#### func wrappingPow(UInt64)

```cangjie
public func wrappingPow(y: UInt64): Int64
```

功能：使用高位截断策略的幂运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 指数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 幂运算结果。

#### func wrappingShl(Int64)

```cangjie
public func wrappingShl(y: Int64): Int64
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 6 位作为移位位数。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 左移运算结果。

#### func wrappingShr(Int64)

```cangjie
public func wrappingShr(y: Int64): Int64
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 6 位作为移位位数。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 移位位数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 右移运算结果。

#### func wrappingSub(Int64)

```cangjie
public func wrappingSub(y: Int64): Int64
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减数。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 减法运算结果。

### extend Int8 <: WrappingOp\<Int8>

```cangjie
extend Int8 <: WrappingOp<Int8>
```

功能：为 [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[Int8](../../core/core_package_api/core_package_intrinsics.md#int8)>

#### func wrappingAdd(Int8)

```cangjie
public func wrappingAdd(y: Int8): Int8
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): Int8
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自减运算结果。

#### func wrappingDiv(Int8)

```cangjie
public func wrappingDiv(y: Int8): Int8
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): Int8
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 自增运算结果。

#### func wrappingMod(Int8)

```cangjie
public func wrappingMod(y: Int8): Int8
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 除数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 取余运算结果。

#### func wrappingMul(Int8)

```cangjie
public func wrappingMul(y: Int8): Int8
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): Int8
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 负号运算结果。

#### func wrappingShl(Int8)

```cangjie
public func wrappingShl(y: Int8): Int8
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 3 位作为移位位数。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 左移运算结果。

#### func wrappingShr(Int8)

```cangjie
public func wrappingShr(y: Int8): Int8
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低 3 位作为移位位数。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 移位位数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 右移运算结果。

#### func wrappingSub(Int8)

```cangjie
public func wrappingSub(y: Int8): Int8
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减数。

返回值：

- [Int8](../../core/core_package_api/core_package_intrinsics.md#int8) - 减法运算结果。

### extend IntNative <: WrappingOp\<IntNative>

```cangjie
extend IntNative <: WrappingOp<IntNative>
```

功能：为 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative)>

#### func wrappingAdd(IntNative)

```cangjie
public func wrappingAdd(y: IntNative): IntNative
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): IntNative
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自减运算结果。

#### func wrappingDiv(IntNative)

```cangjie
public func wrappingDiv(y: IntNative): IntNative
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): IntNative
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 自增运算结果。

#### func wrappingMod(IntNative)

```cangjie
public func wrappingMod(y: IntNative): IntNative
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 除数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 取余运算结果。

#### func wrappingMul(IntNative)

```cangjie
public func wrappingMul(y: IntNative): IntNative
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): IntNative
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 负号运算结果。

#### func wrappingShl(IntNative)

```cangjie
public func wrappingShl(y: IntNative): IntNative
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低位作为移位位数，具体取的位数取决于当前系统下 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的位数。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 左移运算结果。

#### func wrappingShr(IntNative)

```cangjie
public func wrappingShr(y: IntNative): IntNative
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数或小于 0 时，取右操作数的低位作为移位位数，具体取的位数取决于当前系统下 [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) 的位数。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 移位位数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 右移运算结果。

#### func wrappingSub(IntNative)

```cangjie
public func wrappingSub(y: IntNative): IntNative
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减数。

返回值：

- [IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative) - 减法运算结果。

### extend UInt16 <: WrappingOp\<UInt16>

```cangjie
extend UInt16 <: WrappingOp<UInt16>
```

功能：为 [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)>

#### func wrappingAdd(UInt16)

```cangjie
public func wrappingAdd(y: UInt16): UInt16
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): UInt16
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自减运算结果。

#### func wrappingDiv(UInt16)

```cangjie
public func wrappingDiv(y: UInt16): UInt16
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): UInt16
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 自增运算结果。

#### func wrappingMod(UInt16)

```cangjie
public func wrappingMod(y: UInt16): UInt16
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 除数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 取余运算结果。

#### func wrappingMul(UInt16)

```cangjie
public func wrappingMul(y: UInt16): UInt16
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): UInt16
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 负号运算结果。

#### func wrappingShl(UInt16)

```cangjie
public func wrappingShl(y: UInt16): UInt16
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 4 位作为移位位数。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 左移运算结果。

#### func wrappingShr(UInt16)

```cangjie
public func wrappingShr(y: UInt16): UInt16
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 4 位作为移位位数。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 移位位数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 右移运算结果。

#### func wrappingSub(UInt16)

```cangjie
public func wrappingSub(y: UInt16): UInt16
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减数。

返回值：

- [UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16) - 减法运算结果。

### extend UInt32 <: WrappingOp\<UInt32>

```cangjie
extend UInt32 <: WrappingOp<UInt32>
```

功能：为 [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)>

#### func wrappingAdd(UInt32)

```cangjie
public func wrappingAdd(y: UInt32): UInt32
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): UInt32
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自减运算结果。

#### func wrappingDiv(UInt32)

```cangjie
public func wrappingDiv(y: UInt32): UInt32
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): UInt32
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 自增运算结果。

#### func wrappingMod(UInt32)

```cangjie
public func wrappingMod(y: UInt32): UInt32
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 除数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 取余运算结果。

#### func wrappingMul(UInt32)

```cangjie
public func wrappingMul(y: UInt32): UInt32
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): UInt32
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 负号运算结果。

#### func wrappingShl(UInt32)

```cangjie
public func wrappingShl(y: UInt32): UInt32
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 5 位作为移位位数。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 左移运算结果。

#### func wrappingShr(UInt32)

```cangjie
public func wrappingShr(y: UInt32): UInt32
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 5 位作为移位位数。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 移位位数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 右移运算结果。

#### func wrappingSub(UInt32)

```cangjie
public func wrappingSub(y: UInt32): UInt32
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减数。

返回值：

- [UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32) - 减法运算结果。

### extend UInt64 <: WrappingOp\<UInt64>

```cangjie
extend UInt64 <: WrappingOp<UInt64>
```

功能：为 [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)>

#### func wrappingAdd(UInt64)

```cangjie
public func wrappingAdd(y: UInt64): UInt64
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): UInt64
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自减运算结果。

#### func wrappingDiv(UInt64)

```cangjie
public func wrappingDiv(y: UInt64): UInt64
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): UInt64
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 自增运算结果。

#### func wrappingMod(UInt64)

```cangjie
public func wrappingMod(y: UInt64): UInt64
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 除数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 取余运算结果。

#### func wrappingMul(UInt64)

```cangjie
public func wrappingMul(y: UInt64): UInt64
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): UInt64
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 负号运算结果。

#### func wrappingShl(UInt64)

```cangjie
public func wrappingShl(y: UInt64): UInt64
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 6 位作为移位位数。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 左移运算结果。

#### func wrappingShr(UInt64)

```cangjie
public func wrappingShr(y: UInt64): UInt64
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 6 位作为移位位数。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 移位位数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 右移运算结果。

#### func wrappingSub(UInt64)

```cangjie
public func wrappingSub(y: UInt64): UInt64
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减数。

返回值：

- [UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64) - 减法运算结果。

### extend UInt8 <: WrappingOp\<UInt8>

```cangjie
extend UInt8 <: WrappingOp<UInt8>
```

功能：为 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)>

#### func wrappingAdd(UInt8)

```cangjie
public func wrappingAdd(y: UInt8): UInt8
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): UInt8
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自减运算结果。

#### func wrappingDiv(UInt8)

```cangjie
public func wrappingDiv(y: UInt8): UInt8
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): UInt8
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 自增运算结果。

#### func wrappingMod(UInt8)

```cangjie
public func wrappingMod(y: UInt8): UInt8
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 除数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 取余运算结果。

#### func wrappingMul(UInt8)

```cangjie
public func wrappingMul(y: UInt8): UInt8
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): UInt8
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 负号运算结果。

#### func wrappingShl(UInt8)

```cangjie
public func wrappingShl(y: UInt8): UInt8
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 3 位作为移位位数。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 左移运算结果。

#### func wrappingShr(UInt8)

```cangjie
public func wrappingShr(y: UInt8): UInt8
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数时，取右操作数的低 3 位作为移位位数。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 移位位数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 右移运算结果。

#### func wrappingSub(UInt8)

```cangjie
public func wrappingSub(y: UInt8): UInt8
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减数。

返回值：

- [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) - 减法运算结果。

### extend UIntNative <: WrappingOp\<UIntNative>

```cangjie
extend UIntNative <: WrappingOp<UIntNative>
```

功能：为 [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) 实现 [WrappingOp](#interface-wrappingopt) 接口。

父类型：

- [WrappingOp](#interface-wrappingopt)\<[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)>

#### func wrappingAdd(UIntNative)

```cangjie
public func wrappingAdd(y: UIntNative): UIntNative
```

功能：使用高位截断策略的加法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 加法运算结果。

#### func wrappingDec()

```cangjie
public func wrappingDec(): UIntNative
```

功能：使用高位截断策略的自减运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自减运算结果。

#### func wrappingDiv(UIntNative)

```cangjie
public func wrappingDiv(y: UIntNative): UIntNative
```

功能：使用高位截断策略的除法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除法运算结果。

#### func wrappingInc()

```cangjie
public func wrappingInc(): UIntNative
```

功能：使用高位截断策略的自增运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 自增运算结果。

#### func wrappingMod(UIntNative)

```cangjie
public func wrappingMod(y: UIntNative): UIntNative
```

功能：使用高位截断策略的取余运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 除数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 取余运算结果。

#### func wrappingMul(UIntNative)

```cangjie
public func wrappingMul(y: UIntNative): UIntNative
```

功能：使用高位截断策略的乘法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 乘法运算结果。

#### func wrappingNeg()

```cangjie
public func wrappingNeg(): UIntNative
```

功能：使用高位截断策略的负号运算。

当运算出现溢出时，高位截断，否则返回运算结果。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 负号运算结果。

#### func wrappingShl(UIntNative)

```cangjie
public func wrappingShl(y: UIntNative): UIntNative
```

功能：使用高位截断策略的左移运算。

当右操作数大于等于左操作数位数时，取右操作数的低位作为移位位数，具体取的位数取决于当前系统下 UIntNative 的位数。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 左移运算结果。

#### func wrappingShr(UIntNative)

```cangjie
public func wrappingShr(y: UIntNative): UIntNative
```

功能：使用高位截断策略的右移运算。

当右操作数大于等于左操作数位数时，取右操作数的低位作为移位位数，具体取的位数取决于当前系统下 UIntNative 的位数。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 移位位数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 右移运算结果。

#### func wrappingSub(UIntNative)

```cangjie
public func wrappingSub(y: UIntNative): UIntNative
```

功能：使用高位截断策略的减法运算。

当运算出现溢出时，高位截断，否则返回运算结果。

参数：

- y: [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减数。

返回值：

- [UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative) - 减法运算结果。
