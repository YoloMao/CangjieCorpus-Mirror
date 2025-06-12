# 枚举

## enum RoundingMode

```cangjie
public enum RoundingMode {
    | CEILING
    | DOWN
    | FLOOR
    | HALF_EVEN
    | HALF_UP
    | UP
}
```

舍入规则枚举类，共包含 6 中舍入规则。除包含 IEEE 754 浮点数规定约定的 5 种舍入规则外，提供使用较多的 “四舍五入” 舍入规则。

|十进制数|UP|DOWN|CEILING|FLOOR|HALF_UP|HALF_EVEN|
|:----|:----:|:----:|:----:|:----:|:----:|:----:|
|7.5|8|7|8|7|8|8|
|4.5|5|4|5|4|5|4|
|-1.1|-2|-1|-1|-2|-1|-1|
|-4.5|-5|-4|-4|-5|-5|-4|
|-7.5|-8|-7|-7|-8|-8|-8|

### CEILING

```cangjie
CEILING
```

功能：向正无穷方向舍入。

### DOWN

```cangjie
DOWN
```

功能：向靠近零的方向舍入。

### FLOOR

```cangjie
FLOOR
```

功能：向负无穷方向舍入。

### HALF_EVEN

```cangjie
HALF_EVEN
```

功能：四舍六入五取偶，又称 “银行家舍入”。

### HALF_UP

```cangjie
HALF_UP
```

功能：四舍五入。

### UP

```cangjie
UP
```

功能：向远离零的方向舍入。