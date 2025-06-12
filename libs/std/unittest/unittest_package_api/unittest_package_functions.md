# 函数

## func assertCaughtUnexpectedE(String,String,String) 

```cangjie
public func assertCaughtUnexpectedE(
    message: String,
    expectedExceptions: String,
    caughtException: String
): Nothing
```

功能：捕获的异常不符合预期，记录信息，抛出异常。

参数：

- message: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 不符合预期时的提示信息。
- expectedExceptions: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 期望的捕获的异常。
- caughtException: [String](../../core/core_package_api/core_package_structs.md#struct-string)  - 实际捕获的异常。

## func assertEqual\<T>(String, String, T, T): Unit where T <: Equatable\<T>

```cangjie
public func assertEqual<T>(leftStr: String, rightStr: String, expected: T, actual: T): Unit where T <: Equatable<T>
```

功能：比较 `expected` 和 `actual` 值是否相等。若不等，直接抛出异常。

参数：

- leftStr: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 期望的表达式的字符串。
- rightStr: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 实际的表达式的字符串。
- expected: T - 期望的值。
- actual: T  - 实际值。

## func csv\<T>(String, Rune, Rune, Rune, Option\<Rune>, Option<Array\<String>>, Array\<UInt64>, Array\<UInt64>, Bool) where T <: Serializable\<T>

```cangjie
public func csv<T>(
 fileName: String,
 delimiter!: Rune = ',',
    quoteChar!: Rune = '"',
    escapeChar!: Rune = '"',
    commentChar!: Option<Rune> = None,
    header!: Option<Array<String>> = None,
    skipRows!: Array<UInt64> = [],
    skipColumns!: Array<UInt64> = [],
    skipEmptyLines!: Bool = false
): CsvStrategy<T> where T <: Serializable<T>
```

功能：该函数可从 csv 文件中读取类型 T 的数据值，其中 T 必须可被序列化。该函数的返回值是参数化测试的一种参数源。

参数：

- fileName: [String](../../core/core_package_api/core_package_structs.md#struct-string) - CSV 格式的文件地址，可为相对地址，不限制后缀名。
- delimiter!: [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 一行中作为元素分隔符的符号。默认值为 `,` （逗号）。
- quoteChar!: [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 括住元素的符号。默认值为 `"` （双引号）。
- escapeChar!: [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) ：转义括住元素的符号。默认值为 `"` （双引号）。
- commentChar!: [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Rune](../../core/core_package_api/core_package_intrinsics.md#rune)> - 注释符号，跳过一行。必须在一行的最左侧。默认值是 `None` (不存在注释符号)。
- header!: [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>> - 提供一种方式覆盖第一行。
    - 当 header 被指定时，文件的第一行将被作为数据行，指定的 header 将被使用。
    - 当 header 被指定，同时第一行通过指定 `skipRows` 被跳过时，第一行将被忽略，指定的 header 将被使用。
    - 当 header 未被指定时，即值为 `None` 时，文件的第一行将被作为表头。此为默认值。
- skipRows!: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)> - 指定需被跳过的数据行号，行号从 0 开始。默认值为空数组 `[]` 。
- skipColumns!: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)> - 指定需被跳过的数据列号，列号从 0 开始。当有数据列被跳过，并且用户指定了自定义的 header 时，该 header 将按照跳过后的实际数据列对应。默认值为空数据 `[]` 。
- skipEmptyLines!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 指定是否需要跳过空行。默认值为 `false` 。

返回值：

- [CsvStrategy](unittest_package_classes.md#class-csvstrategy)\<T> 对象，T 可被序列化，数据值从 CSV 文件中读取。

## func defaultConfiguration()

```cangjie
public func defaultConfiguration(): Configuration
```

功能：生成默认的配置信息。

返回值：

- [Configuration](../../unittest_common/unittest_common_package_api/unittest_common_package_classes.md#class-configuration) - 配置信息。

## func entryMain(TestPackage)

```cangjie
public func entryMain(testPackage: TestPackage): Int64
```

功能：提供给 `cjc --test` 使用，框架执行测试用例的入口函数。

参数：

- testPackage: [TestPackage](./unittest_package_classes.md#class-testpackage) - 测试包对象。

返回值:

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) -  执行结果。

## func expectCaughtUnexpectedE(String,String,String) 

```cangjie
public func expectCaughtUnexpectedE(
    message: String,
    expectedExceptions: String,
    caughtException: String
): Unit
```

功能：捕获的异常不符合预期，记录信息，不抛出异常。

参数：

- message: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 不符合预期时的提示信息。
- expectedExceptions: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 期望的捕获的异常。
- caughtException: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 实际捕获的异常。

## func expectEqual\<T>(String, String, T, T): Unit where T <: Equatable\<T>

```cangjie
public func expectEqual<T>(leftStr: String, rightStr: String, expected: T, actual: T): Unit where T <: Equatable<T>
```

功能：比较 `expected` 和 `actual` 值是否相等。记录比较结果，不抛出异常。

参数：

- leftStr: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 期望的表达式的字符串。
- rightStr: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 实际的表达式的字符串。
- expected: T - 期望的值。
- actual: T  - 实际值。

## func fail(String) 

```cangjie
public func fail(message: String): Nothing 
```

功能：使该用例失败，直接抛出异常。

参数：

- message: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 失败信息。

## func failExpect(String)

```cangjie
public func failExpect(message: String): Unit 
```

功能：使该用例失败，记录信息，不抛出异常。

参数：

- message: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 失败信息。

## func json\<T>(String) where T <: Serializable\<T>

```cangjie
public func json<T>(fileName: String): JsonStrategy<T> where T <: Serializable<T>
```

功能：该函数可从 JSON 文件中读取类型 T 的数据值，其中 T 必须可被序列化。该函数的返回值是参数化测试的一种参数源。

参数：

- fileName: [String](../../core/core_package_api/core_package_structs.md#struct-string) - JSON 格式的文件地址，可为相对地址。

返回值：

- [JsonStrategy](unittest_package_classes.md#class-jsonstrategy)\<T> - T 可被序列化，数据值从 JSON 文件中读取。

示例：

```cangjie
@Test[user in json("users.json")]
func test_user_age(user: User): Unit {
    @Expect(user.age, 100)
}
```

json 文件示例：

```json
[
    {
        "age": 100
    },
    {
        "age": 100
    }
]
```

创建一种被用作测试函数参数的类，该类实现接口 [Serializable](../../../serialization/serialization/serialization_package_api/serialization_package_interfaces.md#interface-serializable) 。

<!--compile-->
```cangjie
class User <: Serializable<User> {
    User(let age: Int64) {}

    public func serialize(): DataModel {
        DataModelStruct()
          .add(Field("age", DataModelInt(age)))
    }

    public static func deserialize(dm: DataModel): User {
        if (let Some(dms) <- dm as DataModelStruct) {
          if (let Some(age) <- dms.get("age") as DataModelInt) {
            return User(age.getValue())
          }
        }

        throw Exception("Can't deserialize user.")
    }
}
```

任何实现 [Serializable](../../../serialization/serialization/serialization_package_api/serialization_package_interfaces.md#interface-serializable) 的类型都可以用作参数类型，包括默认值：

```cangjie
@Test[user in json("numbers.json")]
func test(value: Int64)
```

```cangjie
@Test[user in json("names.json")]
func test(name: String)
```

## func tsv\<T>(String, Rune, Rune, Option\<Rune>, Option\<Array\<String>>, Array\<UInt64>, Array\<UInt64>, Bool) where T <: Serializable\<T>

```cangjie
public func tsv<T>(
    fileName: String,
    quoteChar!: Rune = '"',
    escapeChar!: Rune = '"',
    commentChar!: Option<Rune> = None,
    header!: Option<Array<String>> = None,
    skipRows!: Array<UInt64> = [],
    skipColumns!: Array<UInt64> = [],
    skipEmptyLines!: Bool = false
): CsvStrategy<T> where T <: Serializable<T>
```

功能：该函数可从 tsv 文件中读取类型 T 的数据值，其中 T 必须可被序列化。该函数的返回值是参数化测试的一种参数源。

参数：

- fileName: [String](../../core/core_package_api/core_package_structs.md#struct-string) - TSV 格式的文件地址，可为相对地址，不限制后缀名。
- quoteChar!: [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 括住元素的符号。默认值为 `"` （双引号）。
- escapeChar!: [Rune](../../core/core_package_api/core_package_intrinsics.md#rune) - 转义括住元素的符号。默认值为 `"` （双引号）。
- commentChar!: [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Rune](../../core/core_package_api/core_package_intrinsics.md#rune)> - 注释符号，跳过一行。必须在一行的最左侧。默认值是 `None` (不存在注释符号)。
- header!: [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[String](../../core/core_package_api/core_package_structs.md#struct-string)>> - 提供一种方式覆盖第一行。
    - 当 header 被指定时，文件的第一行将被作为数据行，指定的 header 将被使用。
    - 当 header 被指定，同时第一行通过指定 `skipRows` 被跳过时，第一行将被忽略，指定的 header 将被使用。
    - 当 header 未被指定时，即值为 `None` 时，文件的第一行（跳过后的实际数据）将被作为表头。此为默认值。
- skipRows!: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)> - 指定需被跳过的数据行号，行号从 0 开始。默认值为空数组 `[]` 。
- skipColumns!: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)> - 指定需被跳过的数据列号，列号从 0 开始。当有数据列被跳过，并且用户指定了自定义的 header 时，该 header 将按照跳过后的实际数据列对应。默认值为空数据 `[]` 。
- skipEmptyLines!: [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 指定是否需要跳过空行。默认值为 `false` 。

返回值：

- [CsvStrategy](unittest_package_classes.md#class-csvstrategy)\<T> - T 可被序列化，数据值从 TSV 文件中读取。

示例：

在单元测试中，可以通过传入 csv/tsv 文件地址进行参数化测试。

CSV 文件每一行的数据应当被表示成一个 [Serializable](../../../serialization/serialization/serialization_package_api/serialization_package_interfaces.md#interface-serializable)\<T> 对象，它的成员名是文件每一列头的值，成员值是 [DataModelString](../../../serialization/serialization/serialization_package_api/serialization_package_classes.md#class-datamodelstring) 类型的对应列号上的值。

举例来说，有一个 `testdata.csv` 文件，具有如下内容：

```csv
username,age
Alex Great,21
Donald Sweet,28
```

有几种方式可以序列化上述数据：

1. 将数据表示为 [HashMap](../../collection/collection_package_api/collection_package_class.md#class-hashmapk-v-where-k--hashable--equatablek)\<[String](../../core/core_package_api/core_package_structs.md#struct-string), [String](../../core/core_package_api/core_package_structs.md#struct-string)> 类型。

    具体示例为：

    <!--compile-->
    ```cangjie
    import std.collection.HashMap
    import std.unittest.*
    import std.unittest.testmacro.*


    @Test[user in csv("testdata.csv")]
    func testUser(user: HashMap<String, String>) {
        @Assert(user["username"] == "Alex Great" || user["username"] == "Donald Sweet")
        @Assert(user["age"] == "21" || user["age"] == "28")
    }
    ```

2. 将数据表示为 [Serializable](../../../serialization/serialization/serialization_package_api/serialization_package_interfaces.md#interface-serializable)\<T> 类型数据，其 [String](../../core/core_package_api/core_package_structs.md#struct-string) 类型的数据可被反序列化为 [DataModelStruct](../../../serialization/serialization/serialization_package_api/serialization_package_classes.md#class-datamodelstruct) 格式对象。

具体示例为：

<!--compile-->
```cangjie
    import serialization.serialization.*
    import std.convert.*
    import std.unittest.*
    import std.unittest.testmacro.*


    public class User <: Serializable<User> {
        public User(let name: String, let age: UInt32) {}

        public func serialize(): DataModel {
            let dms = DataModelStruct()
            dms.add(Field("username", DataModelString(name)))
            dms.add(Field("age", DataModelString(age.toString())))
            return dms
        }

        static public func deserialize(dm: DataModel): User {
            var data: DataModelStruct = match (dm) {
                case dms: DataModelStruct => dms
                case _ => throw DataModelException("this data is not DataModelStruct")
            }

            let name = String.deserialize(data.get("username"))
            let age = String.deserialize(data.get("age"))
            return User(name, UInt32.parse(age))
        }
    }

    @Test[user in csv("testdata.csv")]
    func testUser(user: User) {
        @Assert(user.name == "Alex Great" || user.name == "Donald Sweet")
        @Assert(user.age == 21 || user.age == 28)
    }
```
