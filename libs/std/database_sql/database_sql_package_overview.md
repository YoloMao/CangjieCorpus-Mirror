# std.database.sql 包

## 功能介绍

database.sql 包提供仓颉访问数据库的接口。

本包提供 SQL/CLI 的通用接口，配合数据库驱动 Driver 完成对数据库的各项操作。

> **注意：**
>
> 当前仅支持 SQL/CLI 接口。

SQL 数据类型和仓颉数据类型对应表如下：

| SQL         | CDBC/Cangjie     | SqlDataType    | 说明                                                  |
| ----------- | ---------------- | -------------- | ----------------------------------------------------- |
| `RUNE`      | `String`         | `SqlChar`      | -                                                     |
| `VARCHAR`   | `String`         | `SqlVarchar`   | -                                                     |
| `CLOB`      | `io.InputStream` | `SqlClob`      | -                                                     |
| `BINARY`    | `Array<Byte>`    | `SqlBinary`    | -                                                     |
| `VARBINARY` | `Array<Byte>`    | `SqlVarBinary` | -                                                     |
| `BLOB`      | `io.InputStream` | `SqlBlob`      | -                                                     |
| `NUMERIC`   | `Decimal`        | `sqlDecimal`   | -                                                     |
| `DECIMAL`   | `Decimal`        | `sqlDecimal`   | -                                                     |
| `BOOLEAN`   | `Bool`           | `SqlBool`      | -                                                     |
| `TINYINT`   | `Int8`           | `SqlByte`      | -                                                     |
| `SMALLINT`  | `Int16`          | `SqlSmallInt`  | -                                                     |
| `INTEGER`   | `Int32`          | `SqlInteger`   | -                                                     |
| `BIGINT`    | `Int64`          | `SqlBigInt`    | -                                                     |
| `REAL`      | `Float32`        | `SqlReal`      | -                                                     |
| `DOUBLE`    | `Float64`        | `SqlDouble`    | -                                                     |
| `DATE`      | `time.DateTime`  | `SqlDate`      | 值支持 `YEAR`，`MONTH`，`DAY`。                        |
| `TIME`      | `time.DateTime`  | `SqlTime`      | 值支持 `HOUR`，`MINUTE`，`SECOND`（不包括 `TIME ZONE`）。|
| `TIMETZ`    | `time.DateTime`  | `SqlTimeTz`    | 值支持 `HOUR`，`MINUTE`，`SECOND`（包括 `TIME ZONE`）。  |
| `TIMESTAMP` | `time.DateTime`  | `SqlTimestamp` | 值支持 `YEAR`，`MONTH`，`DAY`，`HOUR`，`MINUTE`，`SECOND`，`TIME ZONE`。 |
| `INTERVAL`  | `time.Duration`  | `SqlInterval`  | 年-月间隔或者日-时间隔。                                 |

## API列表

### 接口

| 接口名                                                       | 功能                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ColumnInfo](./database_sql_package_api/database_sql_package_interfaces.md#interface-columninfo) | 执行 Select/Query 语句返回结果的列信息。                     |
| [Connection](./database_sql_package_api/database_sql_package_interfaces.md#interface-connection) | 数据库连接接口。                                             |
| [Datasource](./database_sql_package_api/database_sql_package_interfaces.md#interface-datasource) | 数据源接口。                                                 |
| [Driver](./database_sql_package_api/database_sql_package_interfaces.md#interface-driver) | 数据库驱动接口。                                             |
| [QueryResult](./database_sql_package_api/database_sql_package_interfaces.md#interface-queryresult) | 执行 Select 语句产生的结果接口。                             |
| [SqlDbType](./database_sql_package_api/database_sql_package_interfaces.md#interface-sqldbType) | 所有 sql 数据类型的父类。 |
| [SqlNullableDbType](./database_sql_package_api/database_sql_package_interfaces.md#interface-sqlnullabledbType) | 允许 `null` 值的 sql 数据类型父类。 |
| [Statement](./database_sql_package_api/database_sql_package_interfaces.md#interface-statement) | sql 语句预执行接口。                                         |
| [Transaction](./database_sql_package_api/database_sql_package_interfaces.md#interface-transaction) | 定义数据库事务的核心行为。                                   |
| [UpdateResult](./database_sql_package_api/database_sql_package_interfaces.md#interface-updateresult) | 执行 Insert、Update、Delete 语句产生的结果接口。             |

### 类

| 类名                                                         | 功能                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [DriverManager](./database_sql_package_api/database_sql_package_classes.md#class-drivermanager) | 支持运行时根据驱动名获取数据库驱动实例。                     |
| [PooledDatasource](./database_sql_package_api/database_sql_package_classes.md#class-pooleddatasource) | 数据库连接池类，提供数据库连接池能力。                       |
| [SqlOption](./database_sql_package_api/database_sql_package_classes.md#class-sqloption) | 预定义的 sql 选项名称和值。                                  |
| [SqlBigInt](./database_sql_package_api/database_sql_package_classes.md#class-sqlbigInt) | 大整数，对应仓颉 `Int64` 类型。                              |
| [SqlBinary](./database_sql_package_api/database_sql_package_classes.md#class-sqlbinary) | 定长二进制字符串，对应仓颉 `Array<Byte>` 类型。              |
| [SqlBlob](./database_sql_package_api/database_sql_package_classes.md#class-sqlblob) | 变长超大二进制字符串（BINARY LARGE OBJECT），对应仓颉 `InputStream` 类型。 |
| [SqlBool](./database_sql_package_api/database_sql_package_classes.md#class-sqlbool) | 布尔类型，对应仓颉 `Bool` 类型。                             |
| [SqlByte](./database_sql_package_api/database_sql_package_classes.md#class-sqlbyte) | 字节，对应仓颉 `Int8` 类型。                                 |
| [SqlChar](./database_sql_package_api/database_sql_package_classes.md#class-sqlchar) | 定长字符串，对应仓颉 `String` 类型。                         |
| [SqlClob](./database_sql_package_api/database_sql_package_classes.md#class-sqlclob) | 变长超大字符串（RUNE LARGE OBJECT），对应仓颉 `InputStream` 类型。 |
| [SqlDate](./database_sql_package_api/database_sql_package_classes.md#class-sqldate) | 日期，仅年月日有效，对应仓颉 `DateTime` 类型。               |
| [SqlDecimal](./database_sql_package_api/database_sql_package_classes.md#class-sqldecimal) | 高精度数，对应仓颉 `Decimal` 类型。                          |
| [SqlDouble](./database_sql_package_api/database_sql_package_classes.md#class-sqldouble) | 双精度数，对应仓颉 `Float64` 类型。    |
| [SqlInteger](./database_sql_package_api/database_sql_package_classes.md#class-sqlinteger) | 中整数，对应仓颉 `Int32` 类型。                              |
| [SqlInterval](./database_sql_package_api/database_sql_package_classes.md#class-sqlinterval) | 时间间隔，对应仓颉 `Duration` 类型。                         |
| [SqlReal](./database_sql_package_api/database_sql_package_classes.md#class-sqlreal) | 浮点数，对应仓颉 `Float32` 类型。                            |
| [SqlSmallInt](./database_sql_package_api/database_sql_package_classes.md#class-sqlsmallInt) | 小整数，对应仓颉 `Int16` 类型。                              |
| [SqlTime](./database_sql_package_api/database_sql_package_classes.md#class-sqltime) | 时间，仅时分秒毫秒有效，对应仓颉 `DateTime` 类型。           |
| [SqlTimestamp](./database_sql_package_api/database_sql_package_classes.md#class-sqltimestamp) | 时间戳，对应仓颉 `DateTime` 类型。                           |
| [SqlTimeTz](./database_sql_package_api/database_sql_package_classes.md#class-sqltimetz) | 带时区的时间，仅时分秒毫秒时区有效，对应仓颉 `DateTime` 类型。 |
| [SqlVarBinary](./database_sql_package_api/database_sql_package_classes.md#class-sqlvarbinary) | 变长二进制字符串，对应仓颉 `Array<Byte>` 类型。              |
| [SqlVarchar](./database_sql_package_api/database_sql_package_classes.md#class-sqlvarchar) | 变长字符串，对应仓颉 `String` 类型。                         |
| [SqlNullableBigInt](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablebigInt) | 大整数，对应仓颉 `Int64` 类型，可为数据库 `Null` 值。        |
| [SqlNullableBinary](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablebinary) | 定长二进制字符串，对应仓颉 `Array<Byte>` 类型，可为数据库 `Null` 值。 |
| [SqlNullableBlob](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullableblob) | 变长超大二进制字符串（BINARY LARGE OBJECT），对应仓颉 `InputStream` 类型，可为数据库 `Null` 值。 |
| [SqlNullableBool](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablebool) | 布尔类型，对应仓颉 `Bool` 类型，可为数据库 `Null` 值。       |
| [SqlNullableByte](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablebyte) | 字节，对应仓颉 `Int8` 类型，可为数据库 `Null` 值。           |
| [SqlNullableChar](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablechar) | 定长二进制字符串，对应仓颉 `String` 类型，可为数据库 `Null` 值。 |
| [SqlNullableClob](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullableclob) | 变长超大字符串（RUNE LARGE OBJECT），对应仓颉 `InputStream` 类型，可为数据库 `Null` 值。 |
| [SqlNullableDate](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullabledate) | 日期，仅年月日有效，对应仓颉 `DateTime` 类型，可为数据库 `Null` 值。 |
| [SqlNullableDecimal](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullabledecimal) | 高精度数，对应仓颉 `Decimal` 类型，可为数据库 `Null` 值。    |
| [SqlNullableDouble](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullabledouble) | 双精度数，对应仓颉 `Float64` 类型，可为数据库 `Null` 值。    |
| [SqlNullableInteger](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullableinteger) | 中整数，对应仓颉 `Int32` 类型，可为数据库 `Null` 值。        |
| [SqlNullableInterval](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullableinterval) | 时间间隔，对应仓颉 `Duration` 类型，可为数据库 `Null` 值。   |
| [SqlNullableReal](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablereal) | 浮点数，对应仓颉 `Float32` 类型，可为数据库 `Null` 值。      |
| [SqlNullableSmallInt](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablesmallint) | 小整数，对应仓颉 `Int16` 类型，可为数据库 `Null` 值。        |
| [SqlNullableTime](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullabletime) | 时间，仅时分秒毫秒有效，对应仓颉 `DateTime` 类型，可为数据库 `Null` 值。 |
| [SqlNullableTimestamp](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullabletimestamp) | 时间戳，对应仓颉 `DateTime` 类型，可为数据库 `Null` 值。     |
| [SqlNullableTimeTz](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullabletimeTz) | 带时区的时间，仅时分秒毫秒时区有效，对应仓颉 `DateTime` 类型，可为数据库 `Null` 值。 |
| [SqlNullableVarBinary](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablevarbinary) | 变长二进制字符串，对应仓颉 `Array<Byte>` 类型，可为数据库 `Null` 值。 |
| [SqlNullableVarchar](./database_sql_package_api/database_sql_package_classes.md#class-sqlnullablevarchar) | 变长字符串，对应仓颉 `String` 类型，可为数据库 `Null` 值。   |

### 枚举

| 枚举名                                                       | 功能                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ConnectionState](./database_sql_package_api/database_sql_package_enums.md#enum-connectionstate) | 描述与数据源连接的当前状态。                                 |
| [TransactionAccessMode](./database_sql_package_api/database_sql_package_enums.md#enum-transactionaccessmode) | 事务读写模式。                                               |
| [TransactionDeferrableMode](./database_sql_package_api/database_sql_package_enums.md#enum-transactiondeferrablemode) | 事务的延迟模式。                                             |
| [TransactionIsoLevel](./database_sql_package_api/database_sql_package_enums.md#enum-transactionisolevel) | 定义了数据库系统中，一个事务中操作的结果在何时以何种方式对其他并发事务操作可见。 |

### 异常类

| 异常类名                                                     | 功能                      |
| ------------------------------------------------------------ | ------------------------- |
| [SqlException](./database_sql_package_api/database_sql_package_exceptions.md#class-sqlexception) | 用于处理 sql 相关的异常。 |
