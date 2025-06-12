# 枚举

## enum Color

```cangjie
public enum Color <: Equatable<Color> {
    | RED
    | GREEN
    | YELLOW
    | BLUE
    | CYAN
    | MAGENTA
    | GRAY
    | DEFAULT_COLOR;
}
```

功能：指定颜色。

父类型：

- [Equatable](../../core/core_package_api/core_package_interfaces.md#interface-equatablet)\<[Color](#enum-color)>

### RED

```cangjie
RED
```

功能：红色。

### GREEN

```cangjie
GREEN
```

功能：绿色。

### YELLOW

```cangjie
YELLOW
```

功能：黄色。

### BLUE

```cangjie
BLUE
```

功能：蓝色。

### CYAN

```cangjie
CYAN
```

功能：青色。

### MAGENTA

```cangjie
MAGENTA
```

功能：品红色。

### GRAY

```cangjie
GRAY
```

功能：灰色。

### DEFAULT_COLOR

```cangjie
DEFAULT_COLOR
```

功能：默认色。

### operator func ==(Color)

```cangjie
public operator func ==(that: Color): Bool
```

功能：判断颜色是否相等。

参数：

- that: [Color](#enum-color) - 被对比的颜色。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 相等时返回 `true` ，否则返回 `false` 。

### operator func !=(Color)

```cangjie
public operator func !=(that: Color): Bool
```

功能：判断颜色是否不相等。

参数：

- that: [Color](#enum-color) - 被对比的颜色。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 不相等时返回 `true` ，否则返回 `false` 。
