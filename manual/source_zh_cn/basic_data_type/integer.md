# 整数类型

整数类型分为有符号（signed）整数类型和无符号（unsigned）整数类型。

**有符号整数类型**包括 `Int8`、`Int16`、`Int32`、`Int64` 和 `IntNative`，分别用于表示编码长度为 `8-bit`、`16-bit`、`32-bit`、`64-bit` 和平台相关大小的有符号整数值的类型。

**无符号整数类型**包括 `UInt8`、`UInt16`、`UInt32`、`UInt64` 和 `UIntNative`，分别用于表示编码长度为 `8-bit`、`16-bit`、`32-bit`、`64-bit` 和平台相关大小的无符号整数值的类型。

对于编码长度为 `N` 的有符号整数类型，其表示范围为：$-2^{N-1} \sim 2^{N-1}-1$；对于编码长度为 `N` 的无符号整数类型，其表示范围为：$0 \sim 2^{N}-1$。下表列出了所有整数类型的表示范围：

| 类型         | 表示范围                                                                                |
|:-----------|:------------------------------------------------------------------------------------|
| Int8       | $-2^7 \sim 2^7-1 (-128 \sim 127)$                                                   |
| Int16      | $-2^{15} \sim 2^{15}-1 (-32,768 \sim 32,767)$                                       |
| Int32      | $-2^{31} \sim 2^{31}-1 (-2,147,483,648 \sim 2,147,483,647)$                         |
| Int64      | $-2^{63} \sim 2^{63}-1 (-9,223,372,036,854,775,808 \sim 9,223,372,036,854,775,807)$ |
| IntNative  | platform dependent                                                                  |
| UInt8      | $0 \sim 2^8-1 (0 \sim 255)$                                                         |
| UInt16     | $0 \sim 2^{16}-1 (0 \sim 65,535)$                                                   |
| UInt32     | $0 \sim 2^{32}-1 (0 \sim 4,294,967,295)$                                            |
| UInt64     | $0 \sim 2^{64}-1 (0 \sim 18,446,744,073,709,551,615)$                               |
| UIntNative | platform dependent                                                                  |

程序具体使用哪种整数类型，取决于该程序中需要处理的整数的性质和范围。在 `Int64` 类型适合的情况下，首选 `Int64` 类型，因为 `Int64` 的表示范围足够大，并且[整数类型字面量](./integer.md#整数类型字面量)在没有类型上下文的情况下默认推断为 `Int64` 类型，可以避免不必要的类型转换。

## 整数类型字面量

整数类型字面量有 4 种进制表示形式：二进制（使用 `0b` 或 `0B` 前缀）、八进制（使用 `0o` 或 `0O` 前缀）、十进制（没有前缀）、十六进制（使用 `0x` 或 `0X` 前缀）。例如，对于十进制数 `24`，表示成二进制是 `0b00011000`（或 `0B00011000`），表示成八进制是 `0o30`（或 `0O30`），表示成十六进制是 `0x18`（或 `0X18`）。

在各进制表示中，可以使用下划线 `_` 充当分隔符的作用，方便识别数值的位数，如 `0b0001_1000`。

对于整数类型字面量，如果它的值超出了上下文要求的整数类型的表示范围，编译器将会报错。

<!-- compile.error -->

```cangjie
let x: Int8 = 128          // Error, 128 out of the range of Int8
let y: UInt8 = 256         // Error, 256 out of the range of UInt8
let z: Int32 = 0x8000_0000 // Error, 0x8000_0000 out of the range of Int32
```

在使用整数类型字面量时，可以通过加入后缀来明确整数字面量的类型，后缀与类型的对应为：

|  后缀  | 类型  |  后缀  | 类型   |
| :----- | :---- | :----  | :----- |
| i8     | Int8  | u8     | UInt8  |
| i16    | Int16 | u16    | UInt16 |
| i32    | Int32 | u32    | UInt32 |
| i64    | Int64 | u64    | UInt64 |

加入了后缀的整数字面量可以通过以下方式使用：

<!-- compile -->

```cangjie
var x = 100i8  // x is 100 with type Int8
var y = 0x10u64 // y is 16 with type UInt64
var z = 0o432i32  // z is 282 with type Int32
```

## 字符字节字面量

仓颉编程语言支持字符字节字面量，以方便使用 ASCII 码表示 `UInt8` 类型的值。字符字节字面量由字符 b、一对标识首尾的单引号、以及一个 `ASCII` 字符组成，例如：

<!-- compile -->

```cangjie
var a = b'x'                    // a is 120 with type UInt8
var b = b'\n'                   // b is 10 with type UInt8
var c = b'\u{78}'               // c is 120 with type UInt8
c = b'\u{90}' - b'\u{66}' + c   // c is 162 with type UInt8
```

`b'x'` 表示类型为 UInt8 大小是 120 的字面值。另外还可以通过 `b'\u{78}'` 这种转义形式表示类型为 `UInt8`，16 进制大小为 0x78 或 10 进制大小为 120 的字面值。需要注意的是，`\u` 内部最多有两位 16 进制数，并且值必须小于 256（十进制）。

## 整数类型支持的操作

整数类型默认支持的操作符包括：算术操作符、位操作符、关系操作符、自增和自减操作符、复合赋值操作符。各操作符的优先级参见附录中的[操作符](../Appendix/operator.md)。

1. 算术操作符包括：一元负号（`-`）、加法（`+`）、减法（`-`）、乘法（`*`）、除法（`/`）、取模（`%`）、幂运算（`**`）。

    - 除了一元负号（`-`）和幂运算（`**`），其他操作符要求左右操作数是相同的类型。
    - `*`，`/`，`+` 和 `-` 的操作数可以是整数类型或浮点类型。
    - `%` 的操作数只支持整数类型。
    - `**` 的左操作数只能为 `Int64` 类型或 `Float64` 类型，并且：

        - 当左操作数类型为 `Int64` 时，右操作数只能为 `UInt64` 类型，表达式的类型为 `Int64`。
        - 当左操作数类型为 `Float64` 时，右操作数只能为 `Int64` 类型或 `Float64` 类型，表达式的类型为 `Float64`。

2. 位操作符包括：按位求反（`!`）、左移（`<<`）、右移（`>>`）、按位与（`&`）、按位异或（`^`）、按位或（`|`）。注意，按位与、按位异或和按位或操作符要求左右操作数是相同的整数类型。
3. 关系操作符包括：小于（`<`）、大于（`>`）、小于等于（`<=`）、大于等于（`>=`）、相等（`==`）、不等（`!=`）。要求关系操作符的左右操作数是相同的整数类型。
4. 自增和自减操作符包括：自增（`++`）和自减（`--`）。注意，仓颉中的自增和自减操作符只能作为一元后缀操作符使用。
5. 复合赋值操作符包括：`+=`、`-=`、`*=`、`/=`、`%=`、`**=`、`<<=`、`>>=`、`&=`、`^=`、`|=`。

整数类型之间、整数类型和浮点类型之间可以互相转换，整数类型可以转换为字符类型，具体的类型转换语法及规则请参见[数值类型之间的转换](../class_and_interface/typecast.md#数值类型之间的转换)。

> **注意：**
>
> 本章所提及的某个类型支持的操作，均是指在没有[操作符重载](../function/operator_overloading.md)的前提下。
