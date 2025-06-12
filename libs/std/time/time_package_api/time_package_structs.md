# 结构体

## struct DateTime

```cangjie
public struct DateTime <: ToString & Hashable & Comparable<DateTime>
```

功能：[DateTime](time_package_structs.md#struct-datetime) 表示日期时间，是一个描述某一时间点的时间类型，提供了基于时区的日期时间读取、计算、比较、转换，以及序列化和反序列化等功能。

- [DateTime](time_package_structs.md#struct-datetime) 是不可变的类型，包含了日期，时间和时区信息。可表示的时间区间为 [-999,999,999-01-01T00:00:00.000000000, 999,999,999-12-31T23:59:59.999999999]，该区间适用于任何合法的时区。
- 以下为 [DateTime](time_package_structs.md#struct-datetime) 中 [now](#static-func-nowtimezone) 和 [nowUTC](#static-func-nowutc) 函数获取当前时间使用的系统调用函数：

  | 系统    | 系统调用函数   | 时钟类型 |
  | ------- | ------------- |--------------- |
  | Linux   | clock_gettime | CLOCK_REALTIME |
  | Windows | clock_gettime | CLOCK_REALTIME |
  | macOS   | clock_gettime | CLOCK_REALTIME |

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)
- [Comparable](../../core/core_package_api/core_package_interfaces.md#interface-comparablet)\<[DateTime](#struct-datetime)>

### static prop UnixEpoch

```cangjie
public static prop UnixEpoch: DateTime
```

功能：获取 Unix 时间纪元，即表示零时区 `1970年1月1日0时0分0秒0纳秒` 的 [DateTime](time_package_structs.md#struct-datetime) 实例。

类型：[DateTime](time_package_structs.md#struct-datetime)

### prop dayOfMonth

```cangjie
public prop dayOfMonth: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例基于当前月第几日。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop dayOfWeek

```cangjie
public prop dayOfWeek: DayOfWeek
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例基于当前周的第几日。

类型：[DayOfWeek](time_package_enums.md#enum-dayofweek)

### prop dayOfYear

```cangjie
public prop dayOfYear: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例基于当前年份的第几日。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop hour

```cangjie
public prop hour: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例的小时。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop isoWeek

```cangjie
public prop isoWeek: (Int64, Int64)
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例基于 ISO8601 标准的年份和基于年的周数。

类型：([Int64](../../core/core_package_api/core_package_intrinsics.md#int64), [Int64](../../core/core_package_api/core_package_intrinsics.md#int64))

### prop minute

```cangjie
public prop minute: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例的分钟。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop month

```cangjie
public prop month: Month
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例的月份。

类型：[Month](time_package_enums.md#enum-month)

### prop monthValue

```cangjie
public prop monthValue: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例以数字形式表示的月份。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop nanosecond

```cangjie
public prop nanosecond: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例的纳秒。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop second

```cangjie
public prop second: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例的秒。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop year

```cangjie
public prop year: Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例的年份。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop zone

```cangjie
public prop zone: TimeZone
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例所关联的时区。

类型：[TimeZone](time_package_classes.md#class-timezone)

### prop zoneId

```cangjie
public prop zoneId: String
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例所关联的 [TimeZone](time_package_classes.md#class-timezone) 实例的时区 ID。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop zoneOffset

```cangjie
public prop zoneOffset: Duration
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例所关联的 [TimeZone](time_package_classes.md#class-timezone) 实例的时间偏移。

类型：[Duration](time_package_structs.md#struct-duration)

### static func fromUnixTimeStamp(Duration)

```cangjie
public static func fromUnixTimeStamp(d: Duration): DateTime
```

功能：获取自 [UnixEpoch](#static-prop-unixepoch) 开始，参数 `d` 指定时间间隔后的日期时间。

参数：

- d: [Duration](time_package_structs.md#struct-duration) - 时间间隔。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 自 [UnixEpoch](#static-prop-unixepoch) 开始，指定 `d` 后的日期时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当结果超过日期时间的表示范围时，抛出异常。

### static func now(TimeZone)

```cangjie
public static func now(timeZone!: TimeZone = TimeZone.Local): DateTime
```

功能：获取参数 `timeZone` 指定时区的当前时间。该方法获取的当前时间受系统时间影响，如存在使用不受系统时间影响的计时场景，可使用 [MonoTime](time_package_structs.md#struct-monotime).now() 替代。

参数：

- timeZone!: [TimeZone](time_package_classes.md#class-timezone) - 时区，默认为本地时区。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 返回指定时区当前时间。

### static func nowUTC()

```cangjie
public static func nowUTC(): DateTime
```

功能：获取 UTC 时区的当前时间。该方法获取的当前时间受系统时间影响，如存在使用不受系统时间影响的计时场景，可使用 [MonoTime](time_package_structs.md#struct-monotime).now() 替代。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - UTC 时区当前时间。

### static func of(Int64, Int64, Int64, Int64, Int64, Int64, Int64, TimeZone)

```cangjie
public static func of(
    year!: Int64,
    month!: Int64,
    dayOfMonth!: Int64,
    hour!: Int64 = 0,
    minute!: Int64 = 0,
    second!: Int64 = 0,
    nanosecond!: Int64 = 0,
    timeZone!: TimeZone = TimeZone.Local
): DateTime
```

功能：根据参数指定的年、月、日、时、分、秒、纳秒、时区构造 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- year!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 年，范围[-999,999,999, 999,999,999]。
- month!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 月，范围[1, 12]。
- dayOfMonth!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 日，范围[1, 31]，最大取值需要跟 month 匹配，可能是 28、29、30、31。
- hour!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 时，范围[0, 23]。
- minute!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 分，范围[0, 59]。
- second!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 秒，范围[0, 59]。
- nanosecond!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 纳秒，范围[0, 999,999,999]。
- timeZone!: [TimeZone](time_package_classes.md#class-timezone) - 时区。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 根据指定参数构造的 [DateTime](time_package_structs.md#struct-datetime) 实例。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当参数值超出指定范围，抛出异常。

### static func of(Int64, Month, Int64, Int64, Int64, Int64, Int64, TimeZone)

```cangjie
public static func of(
    year!: Int64,
    month!: Month,
    dayOfMonth!: Int64,
    hour!: Int64 = 0,
    minute!: Int64 = 0,
    second!: Int64 = 0,
    nanosecond!: Int64 = 0,
    timeZone!: TimeZone = TimeZone.Local
): DateTime
```

功能：根据参数指定的年、月、日、时、分、秒、纳秒、时区构造 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- year!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 年，范围[-999,999,999, 999,999,999]。
- month!: [Month](time_package_enums.md#enum-month) - 月，[Month](time_package_enums.md#enum-month) 类型。
- dayOfMonth!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 日，范围[1, 31]，最大取值需要跟 month 匹配，可能是 28、29、30、31。
- hour!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 时，范围[0, 23]。
- minute!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 分，范围[0, 59]。
- second!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 秒，范围[0, 59]。
- nanosecond!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 纳秒，范围[0, 999,999,999]。
- timeZone!: [TimeZone](time_package_classes.md#class-timezone) - 时区。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 根据指定参数构造的 [DateTime](time_package_structs.md#struct-datetime) 实例。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当参数值超出指定范围，抛出异常。

### static func ofEpoch(Int64, Int64)

```cangjie
public static func ofEpoch(second!: Int64, nanosecond!: Int64): DateTime
```

功能：根据入参 `second` 和 `nanosecond` 构造 [DateTime](time_package_structs.md#struct-datetime) 实例。入参 `second` 表示 unix 时间的秒部分，`nanosecond` 表示 unix 时间的纳秒部分。unix 时间以 [UnixEpoch](#static-prop-unixepoch) 开始计算，`nanosecond` 的范围不可以超过[0, 999,999,999]，否则抛出异常。

参数：

- second!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - unix 时间的秒部分。
- nanosecond!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - unix 时间的纳秒部分，范围不可以超过[0, 999,999,999]。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 自 [UnixEpoch](#static-prop-unixepoch) 开始，指定 `second` 和 `nanosecond` 后的时间。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `nanosecond` 值超出指定范围时，抛出异常。
- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当结果超过日期时间的表示范围时，抛出异常。

### static func ofUTC(Int64, Int64, Int64, Int64, Int64, Int64, Int64)

```cangjie
public static func ofUTC(
    year!: Int64,
    month!: Int64,
    dayOfMonth!: Int64,
    hour!: Int64 = 0,
    minute!: Int64 = 0,
    second!: Int64 = 0,
    nanosecond!: Int64 = 0
): DateTime
```

功能：根据参数指定的年、月、日、时、分、秒、纳秒构造 `UTC` 时区 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- year!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 年，范围[-999,999,999, 999,999,999]。
- month!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 月，范围[1, 12]。
- dayOfMonth!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 日，范围[1, 31]，最大取值需要跟 month 匹配，可能是 28、29、30、31。
- hour!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 时，范围[0, 23]。
- minute!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 分，范围[0, 59]。
- second!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 秒，范围[0, 59]。
- nanosecond!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 纳秒，范围[0, 999,999,999]。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 根据指定参数构造的 `UTC` 时区 [DateTime](time_package_structs.md#struct-datetime) 实例。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当参数值超出指定范围时，抛出异常

### static func ofUTC(Int64, Month, Int64, Int64, Int64, Int64, Int64)

```cangjie
public static func ofUTC(
    year!: Int64,
    month!: Month,
    dayOfMonth!: Int64,
    hour!: Int64 = 0,
    minute!: Int64 = 0,
    second!: Int64 = 0,
    nanosecond!: Int64 = 0
): DateTime
```

功能：根据参数指定的年、月、日、时、分、秒、纳秒构造 `UTC` 时区 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- year!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 年，范围[-999,999,999, 999,999,999]。
- month!: [Month](time_package_enums.md#enum-month) - 月，[Month](time_package_enums.md#enum-month) 类型
- dayOfMonth!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 日, 范围[1, 31]，最大取值需要跟 month 匹配，可能是 28、29、30、31。
- hour!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 时，范围[0, 23]。
- minute!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 分，范围[0, 59]。
- second!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 秒，范围[0, 59]。
- nanosecond!: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 纳秒，范围[0, 999,999,999]。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 根据指定参数构造的 `UTC` 时区 [DateTime](time_package_structs.md#struct-datetime) 实例。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当参数值超出指定范围时，抛出异常。

### static func parse(String)

```cangjie
public static func parse(str: String): DateTime
```

功能：从参数 `str` 中解析得到时间，解析成功时返回 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- str: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 时间字符串，格式为 `RFC3339` 中 `date-time` 格式，可包含小数秒，如 "2023-04-10T08:00:00[.123456]+08:00"(`[]` 中的内容表示可选项)。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 从参数 `str` 中解析出的 [DateTime](time_package_structs.md#struct-datetime) 实例。

异常：

- [TimeParseException](time_package_exceptions.md#class-timeparseexception) - 无法正常解析时，抛出异常。

### static func parse(String, String)

```cangjie
public static func parse(str: String, format: String): DateTime
```

功能：根据 `format` 指定的时间格式，从字符串 `str` 中解析得到时间，解析成功时返回 [DateTime](time_package_structs.md#struct-datetime) 实例，解析具体规格可见下文“从字符串中解析得到时间”模块。

参数：

- str: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 时间字符串，例如："2023/04/10 08:00:00 +08:00"。
- format: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 时间字符串的格式，例如："yyyy/MM/dd HH:mm:ss OOOO"。格式说明详见[时间字符串格式](../time_package_overview.md#时间字符串格式)。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 根据参数 `format` 指定的时间格式，从参数 `str` 中解析出的 [DateTime](time_package_structs.md#struct-datetime) 实例。

异常：

- [TimeParseException](time_package_exceptions.md#class-timeparseexception) - 当无法正常解析时，或存在同一 `format` 的多次取值时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `format` 格式不正确时，抛出异常。

### static func parse(String, DateTimeFormat)

```cangjie
public static func parse(str: String, format: DateTimeFormat): DateTime
```

功能：根据 `format` 指定的时间格式，从字符串 `str` 中解析得到时间，解析成功时返回 [DateTime](time_package_structs.md#struct-datetime) 实例，解析具体规格可见下文“从字符串中解析得到时间”模块。

参数：

- str: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 时间字符串，例如："2023/04/10 08:00:00 +08:00"。
- format: [DateTimeFormat](./time_package_classes.md#class-datetimeformat) - 时间格式，例如："yyyy/MM/dd HH:mm:ss OOOO"对应的时间格式。格式说明详见[时间字符串格式](../time_package_overview.md#时间字符串格式)。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - 根据参数 `format` 指定的时间格式，从参数 `str` 中解析出的 [DateTime](time_package_structs.md#struct-datetime) 实例。

异常：

- [TimeParseException](time_package_exceptions.md#class-timeparseexception) - 当无法正常解析时，或存在同一 `format` 的多次取值时，抛出异常。
- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `format` 格式不正确时，抛出异常。

### func addDays(Int64)

```cangjie
public func addDays(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 天之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少天的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 天后的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 天后的日期时间超过表示范围时，抛出异常。

### func addHours(Int64)

```cangjie
public func addHours(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 小时之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少小时的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 小时后的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 小时后的日期时间超过表示范围时，抛出异常。

### func addMinutes(Int64)

```cangjie
public func addMinutes(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 分钟之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少分钟的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 分钟后的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 分钟后的日期时间超过表示范围时，抛出异常。

### func addMonths(Int64)

```cangjie
public func addMonths(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 月之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

> **注意：**
>
> 由于月的间隔不固定，若设 dt 表示 “2020年3月30日”，`dt.addMonths(1)` 不会返回非法日期“2020年3月31日”。为了尽量返回有效的日期，会偏移到当月最后一天，返回“2020年4月30日”。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少月的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 月后的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 月后的日期时间超过表示范围时，抛出异常。

### func addNanoseconds(Int64)

```cangjie
public func addNanoseconds(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 纳秒之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少纳秒的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 纳秒后的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 纳秒后时间的日期时间超过表示范围时，抛出异常。

### func addSeconds(Int64)

```cangjie
public func addSeconds(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 秒之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少秒的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 秒后的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 秒后的日期时间超过表示范围时，抛出异常。

### func addWeeks(Int64)

```cangjie
public func addWeeks(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 周之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少周的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 周后的时间。

异常：

功能：获取入参 n 周之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

### func addYears(Int64)

```cangjie
public func addYears(n: Int64): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 年之后的时间，返回新的 [DateTime](time_package_structs.md#struct-datetime) 实例。

> **注意：**
>
> 由于年的间隔不固定，若设 dt 表示 “2020年2月29日”，`dt.addYears(1)` 不会返回非法日期“2021年2月29日”。为了尽量返回有效的日期，会偏移到当月最后一天，返回 “2021年2月28日”。

参数：

- n: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 自 [DateTime](time_package_structs.md#struct-datetime) 实例后多少年的数量。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 年后的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) -  [DateTime](time_package_structs.md#struct-datetime) 实例 `n` 年后的日期时间超过表示范围时，抛出异常。

### func compare(DateTime)

```cangjie
public func compare(rhs: DateTime): Ordering
```

功能：判断一个 [DateTime](time_package_structs.md#struct-datetime) 实例与参数 `rhs` 的大小关系。如果大于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).GT；如果等于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).EQ；如果小于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).LT。

参数：

- rhs: [DateTime](time_package_structs.md#struct-datetime) - 参与比较的 [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering) -  [DateTime](time_package_structs.md#struct-datetime) 实例与 `rhs` 大小关系。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 哈希值。

### func inLocal()

```cangjie
public func inLocal(): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例在本地时区的时间。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例在本地时区的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当返回的 [DateTime](time_package_structs.md#struct-datetime) 实例表示的日期时间超过表示范围时，抛出异常。

### func inTimeZone(TimeZone)

```cangjie
public func inTimeZone(timeZone: TimeZone): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例在参数 `timeZone` 指定时区的时间。

参数：

- timeZone: [TimeZone](time_package_classes.md#class-timezone) - 目标时区。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例在参数 `timezone` 指定时区的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当返回的 [DateTime](time_package_structs.md#struct-datetime) 实例表示的日期时间超过表示范围时，抛出异常。

### func inUTC()

```cangjie
public func inUTC(): DateTime
```

功能：获取 [DateTime](time_package_structs.md#struct-datetime) 实例在 `UTC` 时区的时间。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) -  [DateTime](time_package_structs.md#struct-datetime) 实例在 `UTC` 时区的时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当返回的 [DateTime](time_package_structs.md#struct-datetime) 实例表示的日期时间超过表示范围时，抛出异常。

### func toString()

```cangjie
public func toString(): String
```

功能：返回一个表示 [DateTime](time_package_structs.md#struct-datetime) 实例的字符串，其格式为 `RFC3339` 中 `date-time` 格式，如果时间包含纳秒信息（不为零），会打印出小数秒。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) -  [DateTime](time_package_structs.md#struct-datetime) 实例的字符串表示。

### func toString(String)

```cangjie
public func toString(format: String): String
```

功能：返回一个表示 [DateTime](time_package_structs.md#struct-datetime) 实例的字符串，其格式由参数 `format` 指定。格式说明详见[时间字符串格式](../time_package_overview.md#时间字符串格式)

参数：

- format: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 返回字符串的格式，其格式可为 "yyyy/MM/dd HH:mm:ss OOOO"。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) -  [DateTime](time_package_structs.md#struct-datetime) 实例在 `format` 指定格式下的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `format` 格式不正确时，抛出异常。

### func toString(DateTimeFormat)

```cangjie
public func toString(format: DateTimeFormat): String
```

功能：返回一个表示 [DateTime](time_package_structs.md#struct-datetime) 实例的字符串，其格式由参数 `format` 指定。格式说明详见[时间字符串格式](../time_package_overview.md#时间字符串格式)

参数：

- format: [DateTimeFormat](./time_package_classes.md#class-datetimeformat) - 时间格式，其格式可为 "yyyy/MM/dd HH:mm:ss OOOO"。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) -  [DateTime](time_package_structs.md#struct-datetime) 实例在 `format` 指定格式下的字符串。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `format` 格式不正确时，抛出异常。

### func toUnixTimeStamp()

```cangjie
public func toUnixTimeStamp(): Duration
```

功能：获取当前实例自 [UnixEpoch](#static-prop-unixepoch) 的时间间隔。

返回值：

- [Duration](time_package_structs.md#struct-duration) - 当前实例自 [UnixEpoch](#static-prop-unixepoch) 的时间间隔。

### operator func !=(DateTime)

```cangjie
public operator func !=(r: DateTime): Bool
```

功能：判断当前 [DateTime](time_package_structs.md#struct-datetime) 实例是否不等于 `r`。

若两个 [DateTime](time_package_structs.md#struct-datetime) 不相等，那么它们指向的不是同一 UTC 时间。

参数：

- r: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [DateTime](time_package_structs.md#struct-datetime) 实例不等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func +(Duration)

```cangjie
public operator func +(r: Duration): DateTime
```

功能：实现 [DateTime](time_package_structs.md#struct-datetime) 类型和 [Duration](time_package_structs.md#struct-duration) 类型加法，即 [DateTime](time_package_structs.md#struct-datetime) + [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 加法的右操作数。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 类型实例和 `r` 的和。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当结果超过日期时间的表示范围时，抛出异常。

### operator func -(DateTime)

```cangjie
public operator func -(r: DateTime): Duration
```

功能：实现 [DateTime](time_package_structs.md#struct-datetime) 类型之间的减法，即 [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 运算。

参数：

- r: [DateTime](time_package_structs.md#struct-datetime) - 减法的右操作数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [DateTime](time_package_structs.md#struct-datetime) 类型实例和 `r` 的差。

### operator func -(Duration)

```cangjie
public operator func -(r: Duration): DateTime
```

功能：实现 [DateTime](time_package_structs.md#struct-datetime) 类型和 [Duration](time_package_structs.md#struct-duration) 类型减法，即 [DateTime](time_package_structs.md#struct-datetime) - [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 减法的右操作数。

返回值：

- [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 类型实例和 `r` 的差。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当结果超过日期时间的表示范围时，抛出异常。

### operator func <(DateTime)

```cangjie
public operator func <(r: DateTime): Bool
```

功能：判断当前 [DateTime](time_package_structs.md#struct-datetime) 实例是否早于 `r`（指向更早的 UTC 时间的 [DateTime](time_package_structs.md#struct-datetime) 更小）。

参数：

- r: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [DateTime](time_package_structs.md#struct-datetime) 实例早于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func <=(DateTime)

```cangjie
public operator func <=(r: DateTime): Bool
```

功能：判断当前 [DateTime](time_package_structs.md#struct-datetime) 实例是否早于或等于 `r`（指向更早的 UTC 时间的 [DateTime](time_package_structs.md#struct-datetime) 更小）。

参数：

- r: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [DateTime](time_package_structs.md#struct-datetime) 实例早于或等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func ==(DateTime)

```cangjie
public operator func ==(r: DateTime): Bool
```

功能：判断当前 [DateTime](time_package_structs.md#struct-datetime) 实例是否等于 `r`。

若两个 [DateTime](time_package_structs.md#struct-datetime) 相等，那么它们指向同一 UTC 时间。

参数：

- r: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [DateTime](time_package_structs.md#struct-datetime) 实例等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func >(DateTime)

```cangjie
public operator func >(r: DateTime): Bool
```

功能：判断当前 [DateTime](time_package_structs.md#struct-datetime) 实例是否晚于 `r`（指向更晚的 UTC 时间的 [DateTime](time_package_structs.md#struct-datetime) 更大）。

参数：

- r: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [DateTime](time_package_structs.md#struct-datetime) 实例晚于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func >=(DateTime)

```cangjie
public operator func >=(r: DateTime): Bool
```

功能：判断当前 [DateTime](time_package_structs.md#struct-datetime) 实例是否晚于或等于 `r`（指向更晚的 UTC 时间的 [DateTime](time_package_structs.md#struct-datetime) 更大）。

参数：

- r: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [DateTime](time_package_structs.md#struct-datetime) 实例晚于或等于 `r` 时，返回 `true`；否则，返回 `false`。

## struct Duration

```cangjie
public struct Duration <: ToString & Hashable & Comparable<Duration>
```

功能：[Duration](time_package_structs.md#struct-duration) 表示时间间隔，是一个描述一段时间的时间类型，提供了常用的静态实例，以及计算、比较等功能。

> **说明：**
>
> - [Duration](time_package_structs.md#struct-duration) 表示范围为 [Duration](time_package_structs.md#struct-duration).Min 至 [Duration](time_package_structs.md#struct-duration).Max，数值表示为 [-2<sup>63</sup>, 2<sup>63</sup>)（单位为秒），精度为纳秒。
> - [Duration](time_package_structs.md#struct-duration) 每个时间单位均用整数表示，如果实际值不为整数，则向绝对值小的方向取整。例如表示 `1小时30分46秒` 的 [Duration](time_package_structs.md#struct-duration) 实例调用 `toHours` 方法，将返回结果 1 而不是 1.5 或 2。

父类型：

- [ToString](../../core/core_package_api/core_package_interfaces.md#interface-tostring)
- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)
- [Comparable](../../core/core_package_api/core_package_interfaces.md#interface-comparablet)\<[Duration](#struct-duration)>

### static prop Max

```cangjie
public static prop Max: Duration
```

功能：表示最大时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop Min

```cangjie
public static prop Min: Duration
```

功能：表示最小时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop Zero

```cangjie
public static prop Zero: Duration
```

功能：表示 0 纳秒时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop day

```cangjie
public static prop day: Duration
```

功能：表示 1 天时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop hour

```cangjie
public static prop hour: Duration
```

功能：表示 1 小时时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop microsecond

```cangjie
public static prop microsecond: Duration
```

功能：表示 1 微秒时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop millisecond

```cangjie
public static prop millisecond: Duration
```

功能：表示 1 毫秒时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop minute

```cangjie
public static prop minute: Duration
```

功能：表示 1 分钟时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop nanosecond

```cangjie
public static prop nanosecond: Duration
```

功能：表示 1 纳秒时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static prop second

```cangjie
public static prop second: Duration
```

功能：表示 1 秒时间间隔的 [Duration](time_package_structs.md#struct-duration) 实例。

类型：[Duration](time_package_structs.md#struct-duration)

### static func since(DateTime)

```cangjie
public static func since(t: DateTime): Duration
```

功能：计算从参数 `t` 开始到当前时间为止的时间间隔。

参数：

- t: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

### static func until(DateTime)

```cangjie
public static func until(t: DateTime): Duration
```

功能：计算从当前时间开始到参数 `t` 为止的时间间隔。

参数：

- t: [DateTime](time_package_structs.md#struct-datetime) - [DateTime](time_package_structs.md#struct-datetime) 实例。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

### func abs()

```cangjie
public func abs(): Duration
```

功能：返回一个新的 [Duration](time_package_structs.md#struct-duration) 实例，其值大小为当前 [Duration](time_package_structs.md#struct-duration) 实例绝对值。

返回值：

- [Duration](time_package_structs.md#struct-duration) - 当前 [Duration](time_package_structs.md#struct-duration) 实例取绝对值的结果。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 如果当前 [Duration](time_package_structs.md#struct-duration) 实例等于 [Duration](time_package_structs.md#struct-duration).Min，会因为取绝对值超出 [Duration](time_package_structs.md#struct-duration) 表示范围而抛异常。

### func compare(Duration)

```cangjie
public func compare(rhs: Duration): Ordering
```

功能：比较当前 [Duration](time_package_structs.md#struct-duration) 实例与另一个 [Duration](time_package_structs.md#struct-duration) 实例的关系，如果大于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).GT；如果等于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).EQ；如果小于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).LT。

参数：

- rhs: [Duration](time_package_structs.md#struct-duration) - 参与比较的 [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering) - 当前 [Duration](time_package_structs.md#struct-duration) 实例与 `rhs` 的大小关系。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例的哈希值。

### func toDays()

```cangjie
public func toDays(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例以天为单位的整数大小。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例以天为单位的大小。

### func toHours()

```cangjie
public func toHours(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例以小时为单位的整数大小。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例以小时为单位的大小。

### func toMicroseconds()

```cangjie
public func toMicroseconds(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例以微秒为单位的整数大小。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例以微秒为单位的大小。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当 [Duration](time_package_structs.md#struct-duration) 实例以微秒为单位的大小超过 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 表示范围时，抛出异常。

### func toMilliseconds()

```cangjie
public func toMilliseconds(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例以毫秒为单位的整数大小。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例以毫秒为单位的大小。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当 [Duration](time_package_structs.md#struct-duration) 实例以毫秒为单位的大小超过 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 表示范围时，抛出异常。

### func toMinutes()

```cangjie
public func toMinutes(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例以分钟为单位的整数大小。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例以分钟为单位的大小。

### func toNanoseconds()

```cangjie
public func toNanoseconds(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例以纳秒为单位的整数大小，向绝对值小的方向取整。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例以纳秒为单位的大小。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当 [Duration](time_package_structs.md#struct-duration) 实例以“纳秒”为单位的大小超过 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 表示范围时，抛出异常。

### func toSeconds()

```cangjie
public func toSeconds(): Int64
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例以秒为单位的整数大小。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 当前 [Duration](time_package_structs.md#struct-duration) 实例以秒为单位的大小。

### func toString()

```cangjie
public func toString(): String
```

功能：获得当前 [Duration](time_package_structs.md#struct-duration) 实例的字符串表示，格式形如："1d2h3m4s5ms6us7ns"，表示“1天2小时3分钟4秒5毫秒6微秒7纳秒”。某个单位下数值为 0 时此项会被省略，特别地，当所有单位下数值都为 0 时，返回 "0s"。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 当前 [Duration](time_package_structs.md#struct-duration) 实例的字符串表示。

### operator func !=(Duration)

```cangjie
public operator func !=(r: Duration): Bool
```

功能：判断当前 [Duration](time_package_structs.md#struct-duration) 实例是否不等于 `r`。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [Duration](time_package_structs.md#struct-duration) 实例不等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func *(Float64)

```cangjie
public operator func *(r: Float64): Duration
```

功能：实现 [Duration](time_package_structs.md#struct-duration) 类型与 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的乘法，即 [Duration](time_package_structs.md#struct-duration) * [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 运算。

参数：

- r: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 乘法的右操作数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 类型实例和 `r` 的乘积。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相乘后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### operator func *(Int64)

```cangjie
public operator func *(r: Int64): Duration
```

功能：实现 [Duration](time_package_structs.md#struct-duration) 类型与 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的乘法，即 [Duration](time_package_structs.md#struct-duration) * [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 运算。

参数：

- r: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 乘法的右操作数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 类型实例和 `r` 的乘积。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相乘后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### operator func +(Duration)

```cangjie
public operator func +(r: Duration): Duration
```

功能：实现 [Duration](time_package_structs.md#struct-duration) 类型之间的加法，即 [Duration](time_package_structs.md#struct-duration) + [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 加法的右操作数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 类型实例和 `r` 的和。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相加后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### operator func -(Duration)

```cangjie
public operator func -(r: Duration): Duration
```

功能：实现 [Duration](time_package_structs.md#struct-duration) 类型之间的减法，即 [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 减法的右操作数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 类型实例和 `r` 的差。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相减后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### operator func /(Duration)

```cangjie
public operator func /(r: Duration): Float64
```

功能：实现 [Duration](time_package_structs.md#struct-duration) 类型与 [Duration](time_package_structs.md#struct-duration) 类型的除法，即 [Duration](time_package_structs.md#struct-duration) / [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 除数。

返回值：

- [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - [Duration](time_package_structs.md#struct-duration) 类型实例和 `r` 的商。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `r` 等于 [Duration](time_package_structs.md#struct-duration).Zero 时，抛出异常。

### operator func /(Float64)

```cangjie
public operator func /(r: Float64): Duration
```

功能：实现 [Duration](time_package_structs.md#struct-duration) 类型与 [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 类型的除法，即 [Duration](time_package_structs.md#struct-duration) / [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) 运算。

参数：

- r: [Float64](../../core/core_package_api/core_package_intrinsics.md#float64) - 除数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 类型实例和 `r` 的商。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `r` 等于 0 时，抛出异常。
- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相除后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### operator func /(Int64)

```cangjie
public operator func /(r: Int64): Duration
```

功能：实现 [Duration](time_package_structs.md#struct-duration) 类型与 [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 类型的除法，即 [Duration](time_package_structs.md#struct-duration) / [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) 运算。

参数：

- r: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 除数。

返回值：

- [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 类型实例和 `r` 的商。

异常：

- [IllegalArgumentException](../../core/core_package_api/core_package_exceptions.md#class-illegalargumentexception) - 当 `r` 等于 0 时，抛出异常。
- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当相除后的结果超出 [Duration](time_package_structs.md#struct-duration) 的表示范围时，抛出异常。

### operator func <(Duration)

```cangjie
public operator func <(r: Duration): Bool
```

功能：判断当前 [Duration](time_package_structs.md#struct-duration) 实例是否小于 `r`。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [Duration](time_package_structs.md#struct-duration) 实例小于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func <=(Duration)

```cangjie
public operator func <=(r: Duration): Bool
```

功能：判断当前 [Duration](time_package_structs.md#struct-duration) 实例是否小于等于 `r`。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [Duration](time_package_structs.md#struct-duration) 实例小于等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func ==(Duration)

```cangjie
public operator func ==(r: Duration): Bool
```

功能：判断当前 [Duration](time_package_structs.md#struct-duration) 实例是否等于 `r`。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [Duration](time_package_structs.md#struct-duration) 实例等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func >(Duration)

```cangjie
public operator func >(r: Duration): Bool
```

功能：判断当前 [Duration](time_package_structs.md#struct-duration) 实例是否大于 `r`。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [Duration](time_package_structs.md#struct-duration) 实例大于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func >=(Duration)

```cangjie
public operator func >=(r: Duration): Bool
```

功能：判断当前 [Duration](time_package_structs.md#struct-duration) 实例是否大于等于 `r`。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - [Duration](time_package_structs.md#struct-duration) 实例。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [Duration](time_package_structs.md#struct-duration) 实例大于等于 `r` 时，返回 `true`；否则，返回 `false`。

## struct MonoTime

```cangjie
public struct MonoTime <: Hashable & Comparable<MonoTime>
```

功能：[MonoTime](time_package_structs.md#struct-monotime) 表示单调时间，是一个用来衡量经过时间的时间类型，类似于一直运行的秒表，提供了获取当前时间，计算和比较等功能。

- [MonoTime](time_package_structs.md#struct-monotime) 可表示的范围为 [Duration.Zero](#static-prop-zero) 至 [Duration.Max](#static-prop-max)，数值表示为 [0, 2<sup>63</sup>)（单位为秒），精度为纳秒。通过 [now](#static-func-now) 方法创建的 [MonoTime](time_package_structs.md#struct-monotime) 总是晚于先使用该方式创建的 [MonoTime](time_package_structs.md#struct-monotime)，常用于性能测试和时间优先的任务队列。
- 以下为 [MonoTime](time_package_structs.md#struct-monotime) 中 [now](#static-func-now) 函数获取当前时间使用的系统调用函数：

  | 系统    | 系统调用函数   | 时钟类型 |
  | ------- | ------------- |---------------- |
  | Linux   | clock_gettime | CLOCK_MONOTONIC |
  | Windows | clock_gettime | CLOCK_MONOTONIC |
  | macOS   | clock_gettime | CLOCK_MONOTONIC |

父类型：

- [Hashable](../../core/core_package_api/core_package_interfaces.md#interface-hashable)
- [Comparable](../../core/core_package_api/core_package_interfaces.md#interface-comparablet)\<[MonoTime](#struct-monotime)>

### static func now()

```cangjie
public static func now(): MonoTime
```

功能：获取与当前时间对应的 [MonoTime](time_package_structs.md#struct-monotime)。

返回值：

- [MonoTime](time_package_structs.md#struct-monotime) - 与当前时间对应的 [MonoTime](time_package_structs.md#struct-monotime)。

### func compare(MonoTime)

```cangjie
public func compare(rhs: MonoTime): Ordering
```

功能：判断一个 [MonoTime](time_package_structs.md#struct-monotime) 实例与参数 `rhs` 的大小关系。如果大于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).GT；如果等于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).EQ；如果小于，返回 [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering).LT。

参数：

- rhs: [MonoTime](time_package_structs.md#struct-monotime) - 参与比较的 [MonoTime](time_package_structs.md#struct-monotime) 实例。

返回值：

- [Ordering](../../core/core_package_api/core_package_enums.md#enum-ordering) - 当前 [MonoTime](time_package_structs.md#struct-monotime) 实例与 `rhs` 大小关系。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取当前 [MonoTime](time_package_structs.md#struct-monotime) 实例的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 哈希值。

### operator func !=(MonoTime)

```cangjie
public operator func !=(r: MonoTime): Bool
```

功能：判断当前 [MonoTime](time_package_structs.md#struct-monotime) 实例是否不等于 `r`。

参数：

- r: [MonoTime](time_package_structs.md#struct-monotime) - 单调时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [MonoTime](time_package_structs.md#struct-monotime) 实例不等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func +(Duration)

```cangjie
public operator func +(r: Duration): MonoTime
```

功能：实现 [MonoTime](time_package_structs.md#struct-monotime) 类型和 [Duration](time_package_structs.md#struct-duration) 类型加法，即 [MonoTime](time_package_structs.md#struct-monotime) + [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 时间间隔。

返回值：

- [MonoTime](time_package_structs.md#struct-monotime) - 参数 `r` 表示时间间隔后的单调时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当结果超过单调时间的表示范围时，抛出异常。

### operator func -(Duration)

```cangjie
public operator func -(r: Duration): MonoTime
```

功能：实现 [MonoTime](time_package_structs.md#struct-monotime) 类型和 [Duration](time_package_structs.md#struct-duration) 类型减法，即 [MonoTime](time_package_structs.md#struct-monotime) - [Duration](time_package_structs.md#struct-duration) 运算。

参数：

- r: [Duration](time_package_structs.md#struct-duration) - 时间间隔。

返回值：

- [MonoTime](time_package_structs.md#struct-monotime) - 参数 `r` 表示时间间隔前的单调时间。

异常：

- [ArithmeticException](../../core/core_package_api/core_package_exceptions.md#class-arithmeticexception) - 当结果超过单调时间的表示范围时，抛出异常。

### operator func -(MonoTime)

```cangjie
public operator func -(r: MonoTime): Duration
```

功能：实现 [MonoTime](time_package_structs.md#struct-monotime) 类型之间的减法，即 [MonoTime](time_package_structs.md#struct-monotime) - [MonoTime](time_package_structs.md#struct-monotime) 运算。

参数：

- r: [MonoTime](time_package_structs.md#struct-monotime) - 单调时间。

返回值：

- [Duration](time_package_structs.md#struct-duration) - 当前实例距 `r` 经过的时间间隔。

### operator func <(MonoTime)

```cangjie
public operator func <(r: MonoTime): Bool
```

功能：判断当前 [MonoTime](time_package_structs.md#struct-monotime) 实例是否早于 `r`。

参数：

- r: [MonoTime](time_package_structs.md#struct-monotime) - 单调时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [MonoTime](time_package_structs.md#struct-monotime) 实例早于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func <=(MonoTime)

```cangjie
public operator func <=(r: MonoTime): Bool
```

功能：判断当前 [MonoTime](time_package_structs.md#struct-monotime) 实例是否早于或等于 `r`。

参数：

- r: [MonoTime](time_package_structs.md#struct-monotime) - 单调时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [MonoTime](time_package_structs.md#struct-monotime) 实例早于或等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func ==(MonoTime)

```cangjie
public operator func ==(r: MonoTime): Bool
```

功能：判断当前 [MonoTime](time_package_structs.md#struct-monotime) 实例是否等于 `r`。

参数：

- r: [MonoTime](time_package_structs.md#struct-monotime) - 单调时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [MonoTime](time_package_structs.md#struct-monotime) 实例等于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func >(MonoTime)

```cangjie
public operator func >(r: MonoTime): Bool
```

功能：判断当前 [MonoTime](time_package_structs.md#struct-monotime) 实例是否晚于 `r`。

参数：

- r: [MonoTime](time_package_structs.md#struct-monotime) - 单调时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [MonoTime](time_package_structs.md#struct-monotime) 实例晚于 `r` 时，返回 `true`；否则，返回 `false`。

### operator func >=(MonoTime)

```cangjie
public operator func >=(r: MonoTime): Bool
```

功能：判断当前 [MonoTime](time_package_structs.md#struct-monotime) 实例是否晚于或等于 `r`。

参数：

- r: [MonoTime](time_package_structs.md#struct-monotime) - 单调时间。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - `true` 或 `false`。当前 [MonoTime](time_package_structs.md#struct-monotime) 实例晚于或等于 `r` 时，返回 `true`；否则，返回 `false`。
