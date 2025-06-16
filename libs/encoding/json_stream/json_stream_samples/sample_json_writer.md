# 使用 Json Stream 进行序列化

代码如下：
<!-- verify -->

```cangjie
import encoding.json.stream.*
import std.io.ByteArrayStream

class Image <: JsonSerializable {
    var width: Int64
    var height: Int64
    var title: String
    var ids: Array<Int64>

    public init() {
        width = 0
        height = 0
        title = ""
        ids = Array<Int64>()
    }

    public func toJson(w: JsonWriter): Unit {
        w.startObject() // start encoding an object
        w.writeName("Width").writeValue(width) // write name and value pair in current object
        w.writeName("Height").writeValue(height)
        w.writeName("Title").writeValue(title)
        w.writeName("Ids").writeValue<Array<Int64>>(ids) //use class Array's func toJson
        w.endObject()// end current object
    }
}


main(){
    let image = Image()
    image.width = 800
    image.height = 600
    image.title = "View from 15th Floor"
    image.ids = [116, 943, 234, 38793]

    let stream = ByteArrayStream() // output
    let writer = JsonWriter(stream) // init a JsonWriter
    writer.writeValue(image) // serialize image to JSON
    writer.flush()
    println(String.fromUtf8(stream.readToEnd()))
}
```

运行结果如下：

```text
{"Width":800,"Height":600,"Title":"View from 15th Floor","Ids":[116,943,234,38793]}
```
