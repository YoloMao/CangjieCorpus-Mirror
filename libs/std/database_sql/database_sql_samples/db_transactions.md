# 执行事务控制语句示例

## 普通数据库事务

<!-- compile -->

```cangjie
import std.database.sql.*
import std.time.*

func test_transaction() {
    let SQL_INSERT = "INSERT INTO EMPLOYEE (NAME, SALARY, CREATED_DATE) VALUES (?, ?, ?)"
    let SQL_UPDATE = "UPDATE EMPLOYEE SET SALARY=? WHERE NAME=?"
    let drv = DriverManager.getDriver("opengauss").getOrThrow()
    let db = drv.open("opengauss://localhost:5432/testdb")
    try(cn = db.connect()) {
        let psInsert = cn.prepareStatement(SQL_INSERT)
        let psUpdate = cn.prepareStatement(SQL_UPDATE)

        // 创建事务对象
        let tx = cn.createTransaction()
        try {
            psInsert.update(SqlChar("mkyong"), SqlBinary(Array<Byte>([10])), SqlTime(DateTime.now()))

            psInsert.update(SqlChar("kungfu"), SqlBinary(Array<Byte>([20])), SqlTime(DateTime.now()))

            // error, test rollback SQLException: No value specified for parameter 3.
            psInsert.update(SqlVarchar("mkyong"), SqlBinary(Array<Byte>([1, 2, 3, 4, 5])))

            // 提交事务
            tx.commit()

        } catch (e1: SqlException) {
            e1.printStackTrace()
            try {
                // 发生异常，回滚所有事务
                tx.rollback()
            } catch (e2: SqlException) {
                e2.printStackTrace()
            }
        }
    } catch (e: SqlException) {
        e.printStackTrace()
    }
}
```

## 事务保存点

如果数据库事务支持保存点，可以参考如下样例：

<!-- compile -->

```cangjie
import std.database.sql.*
import std.time.*

func test_savepoint() {
    let SQL_INSERT = "INSERT INTO EMPLOYEE (NAME, SALARY, CREATED_DATE) VALUES (?, ?, ?)"
    let SQL_UPDATE = "UPDATE EMPLOYEE SET SALARY=? WHERE NAME=?"
    let drv = DriverManager.getDriver("opengauss").getOrThrow()
    let db = drv.open("opengauss://localhost:5432/testdb")
    try(cn = db.connect()) {
        let psInsert = cn.prepareStatement(SQL_INSERT)
        let psUpdate = cn.prepareStatement(SQL_UPDATE)

        let tx = cn.createTransaction()
        try {
            // 创建保存点 1
            tx.save("save1")
            psInsert.update([SqlChar("mkyong"), SqlBinary(Array<Byte>([10])), SqlTime(DateTime.now())])

            // 创建保存点 2
            tx.save("save2")
            psInsert.update([SqlChar("kungfu"), SqlBinary(Array<Byte>([20])), SqlTime(DateTime.now())])

            // 创建保存点 3
            tx.save("save3")
            psInsert.update([SqlVarchar("mkyong"), SqlBinary(Array<Byte>([1, 2, 3, 4, 5]))])

            // 回滚到保存点 2
            tx.rollback("save2")

            // 提交事务
            tx.commit()

        } catch (e1: SqlException) {
            e1.printStackTrace()
            try {
                // 发生异常，回滚所有事务
                tx.rollback()
            } catch (e2: SqlException) {
                e2.printStackTrace()
            }
        }
    } catch (e: SqlException) {
        e.printStackTrace()
    }
}

```
