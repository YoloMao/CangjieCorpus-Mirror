# 执行数据库操作语句示例

## 插入数据

<!-- compile -->

```cangjie
import std.database.sql.*

main() {
    // 获取数据库连接示例
    let drv = DriverManager.getDriver("opengauss") ?? return
    let ds = drv.open("opengauss://testuser:testpwd@localhost:5432/testdb", [])
    let conn = ds.connect()

    // 插入数据示例
    var stmt = conn.prepareStatement("INSERT INTO test VALUES(?, ?)")
    var name = SqlVarchar("li lei")
    var age = SqlNullableInteger(12)
    var ur = stmt.update(name, age)
    println("Update Result: ${ur.rowCount} ${ur.lastInsertId}")
    name.value = "han meimei"
    age.value = 13
    ur = stmt.update(name, age)
    println("Update Result: ${ur.rowCount} ${ur.lastInsertId}")

    // 如果需要在插入数据后返回插入的 id 值，可以参考如下方式：
    let sql = "INSERT INTO test (name, age) VALUES (?,?) RETURNING id, name"
    try (stmt = conn.prepareStatement(sql)) {
        var name = SqlVarchar("li hua")
        var age = SqlNullableInteger(12)
        let qr = stmt.query(name, age)
        let id = SqlInteger(0)
        while (qr.next(id, name)) {
            println("id = ${id.value}, name=${name.value}")
        }
    } catch (e: Exception) {
        e.printStackTrace()
    }
    stmt.close()
}
```

## 查询数据

<!-- compile -->

```cangjie
import std.database.sql.*

main() {
    // 获取数据库连接示例
    let drv = DriverManager.getDriver("opengauss") ?? return
    let ds = drv.open("opengauss://testuser:testpwd@localhost:5432/testdb", [])
    let conn = ds.connect()

    // 查询操作示例
    var stmt = conn.prepareStatement("select * from test where name = ?")
    var name = SqlNullableVarchar("li lei")
    let id = SqlInteger(0)
    let qr = stmt.query(name)
    var age = SqlNullableInteger(0)
    while (qr.next(id, name, age)) {
        println("id = ${id.value}, name = ${name.value}, age=${age.value}")
    }
    stmt.close()
}
```

## 更新数据

<!-- compile -->

```cangjie
import std.database.sql.*

main() {
    // 获取数据库连接示例
    let drv = DriverManager.getDriver("opengauss") ?? return
    let ds = drv.open("opengauss://testuser:testpwd@localhost:5432/testdb", [])
    let conn = ds.connect()

    // 更新操作示例
    var stmt = conn.prepareStatement("update test set age = ? where name = ?")
    var age = SqlNullableInteger(15)
    var name = SqlNullableVarchar("li lei")
    var ur = stmt.update(age, name)
    println("Update Result: ${ur.rowCount} ${ur.lastInsertId}")
    stmt.close()
}
```

## 删除数据

<!-- compile -->

```cangjie
import std.database.sql.*

main() {
    // 获取数据库连接示例
    let drv = DriverManager.getDriver("opengauss") ?? return
    let ds = drv.open("opengauss://testuser:testpwd@localhost:5432/testdb", [])
    let conn = ds.connect()

    // 删除操作示例
    var stmt = conn.prepareStatement("delete from test where name = ?")
    var name = SqlNullableVarchar("li lei")
    var ur = stmt.update(name)
    println("Update Result: ${ur.rowCount} ${ur.lastInsertId}")
    stmt.close()
}
```
