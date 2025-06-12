# 实现数据库驱动查询功能示例

对于数据库驱动提供者，此处给出实现查询功能的样例代码：

<!-- compile -->

```cangjie
import std.database.sql.*
import std.sync.*

// 实现 QueryResult 接口
public class Rows <: QueryResult {
    let closed = AtomicBool(false)
    public func close(): Unit {
        if (isClosed()) {
            return
        }
        closed.store(true)
    }
    public func isClosed(): Bool {
        closed.load()
    }
    public prop columnInfos: Array<ColumnInfo> {
        get() {
            []
        }
    }
    public func next(values: Array<SqlDbType>): Bool {
        for (idx in 0..values.size) {
            match (values[idx]) {
                case v: SqlBigInt => v.value = 100
                case v: SqlVarchar => v.value = "foo"
                case v: SqlNullableTimestamp => v.value = None
                case _ => ()
            }
        }
        return false
    }
}
```
