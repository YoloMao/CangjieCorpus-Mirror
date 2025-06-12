## 与 Java 语言互操作

### 仓颉调用 Java 的函数

在仓颉编程语言中，可以直接通过 `import` 语句导入 Java 包顶层类型，包括类和接口（包括枚举和注解等）。只有包外可见（`public` 或 `protected`）的 Java 类型、属性或方法才能在仓颉中使用。

导入 Java 类型时，支持如下语法：

* 通过 `import packageName.*` 导入 Java 包中全部类型。
* 通过 `import packageName.name` 导入 Java 包中具体的类型。
* 通过 `import packageName.name as newName` 的方式进行重命名来避免冲突或简化书写。

Java 标准库的内容统一在 `java8` module 中。在仓颉中导入 `java.lang.Math` 使用，示例仓颉代码如下：

```cangjie
// Cangjie code
import java8.java.lang.Math

main(){
    Math.sin(Math.PI / 2)  // invoke static method and access static field
}
```

导入的 Java 类和接口在仓颉中支持如下用法：

* 创建类实例、访问类属性以及调用类方法等。
* 通过 `<:` 继承类或实现接口（必须有 `@Java` 注解）。

Java 中定义的类型、成员变量、成员方法，若其标识符与仓颉关键字同名，则需要使用原始标识符访问。

对于如下 Java 代码：

```java
// Java code
package example;

public class Example {
    public void func() {
        System.out.println("Hello, I'm func.");
    }

    public void Float64() {
        System.out.println("Hello, I'm Float64.");
    }
}
```

在仓颉中访问其成员函数的代码如下：

```cangjie
// Cangjie code
import test.example.*

main() {
    var e = Example()
    e.`func`()    // access java method `func` by raw identifier.
    e.`Float64`() // access java method `Float64` by raw identifier.
}
```

当仓颉调用 Java 代码时，被调用的 Java 代码在一个 `Java thread` 上被执行。`Cangjie thread` 和 `Java thread` 存在一比一对应关系，并且该对应关系在整个仓颉程序运行期间不会改变。在运行时，如果当前执行环境无法执行 Java 互操作，则在第一次尝试执行 Java 代码时抛出异常 `JavaNotSupportedException` 。

导入的 Java 类和接口在使用时需要遵循一定的映射规则（类型、修饰符映射等）和一些使用限制，详细的描述见后续章节。

### Java 调用仓颉的函数

在 Java 代码中支持通过反射（`Class.forName` 或 `ClassLoader.loadClass`）的方式调用定义在仓颉中的类，需要注意的是，被调用的仓颉的类必须通过 `@Java` 修饰。（关于 `@Java` 的使用可参考 [`@Java` 类和接口] 章节相关描述）

以 `Class.forName` 的使用为例，被 Java 侧调用的仓颉类，定义如下：

```cangjie
// Cangjie code
package example

@Java
public class CJClass {
    public func foo(): Unit {
       // do something
    }
}
```

在 Java 中通过 `Class.forName` 方法调用代码如下：

```java
// Java code
package com.company;

import java.lang.reflect.InvocationTargetException;
import java.lang.reflect.Method;

public class Main {
    public static void main(String[] args) throws ClassNotFoundException, NoSuchMethodException, InvocationTargetException, IllegalAccessException, InstantiationException {
        Class clz = Class.forName("example.CJClass");        // Get the class through forName
        Method method = clz.getMethod("foo", Object.class);  // Get the method
        method.invoke(clz.newInstance());    // Create instance and invoke the method
    }
}
```

暂时不支持在 Java 中通过 `import` 语句导入仓颉类型进行使用，在 Java 中调用仓颉代码也必须遵循对应的映射规则和限制，详细描述见后续章节。

注意：不支持通过 Java 的反射机制获取 `@Java` 类的扩展的方法。

### 类型映射

#### Java 基础类型及其包装类

Java 的基础类型作为类属性、方法参数及返回值类型时，可根据映射表对应的类型进行使用，映射关系如下表：

| Java    | Cangjie |
| ------- | ------- |
| byte    | Int8    |
| short   | Int16   |
| char    | UInt16  |
| int     | Int32   |
| long    | Int64   |
| float   | Float32 |
| double  | Float64 |
| boolean | Bool    |

Java 不支持的仓颉数值类型不允许作为 `@Java` 修饰的类的成员变量、成员函数的参数以及返回值类型，这些类型有：`UInt8`、 `UInt32`、`UInt64`、`Float16`、`IntNative`、`UIntNative`。

Java 中各个基础类型对应的包装类型，在仓颉中当作普通的 Java 类，并不提供额外的映射和自动装箱和拆箱操作。在仓颉中使用入参或返回值类型为包装类型的 Java 代码时，用户需要自行导入对应的包装类，手动创建实例传入。

下面是一个例子，Java 类 `BoxedExample` 的成员函数 `foo` 接受一个 `int` 的包装类 `Integer` 作为参数：

```java
// Java code
package com.example;
public class BoxedExample {
    // foo receive the packing type of the basic type.
    public void foo(Integer i) {
        System.out.println(i.toString());
    }
}
```

在仓颉中导入 `BoxedExample` 并创建实例调用 `foo` 函数时，必须手动创建 `Integer` 对象，代码如下：

```cangjie
// Cangjie code
import java8.java.lang.Integer
import test.com.example.*

main() {
    var instance = BoxedExample()
    instance.foo(1)  // compile error
    var i = Integer(1)
    instance.foo(i)  // OK
}
```

#### @Java 类和接口

`@Java` 是仓颉提供的一个内置宏，它最多可以有一个参数，参数类型必须为字符串字面量：

* `@Java`：无参形式，等同于 `@Java["app"]`；
* `@Java["app"]`：有参形式，表示其修饰的类会被 Java Application Classloader 加载；
* `@Java["ext"]`：有参形式，表示其修饰的类会被自定义的 Classloader 加载。

`@Java` 支持修饰 `class` 和 `interface`，通过 `@Java` 修饰的类型默认都是 `java.lang.Object` 的子类型。只有通过 `@Java` 修饰的类型才能在 Java 侧使用。这些类型也可在非 `@Java` 修饰的类或接口中使用。

需要注意的是，`@Java` 修饰的类型具有如下限制：

* `@Java` 修饰的类型，其成员变量、成员函数的参数和返回值类型必须满足 `JType` 约束。
    * 满足 `JType` 约束的类型有：类型映射表中的仓颉类型和使用 `@Java` 修饰的类和接口。
    * 不满足 `JType` 约束的仓颉类型有：`Array` 、`enum` 、`struct` 、函数类型、`Range` 、`String` 、`Nothing` 、`Rune` 、`UInt8`、 `UInt32`、`UInt64`、`Float16`、`IntNative`、`UIntNative`、`Unit`（`Unit`可作为函数的返回值类型）。
* `@Java` 修饰的类或接口可以继承和实现：
    * 导入的 Java 类和接口；
    * 其他被 `@Java` 修饰的类型；
    * 仓颉的 `interface` 类型；
* `@Java` 修饰的类不能包含 `prop` 声明，不能定义类终结器。
* `@Java` 修饰的接口可以声明非静态泛型方法。
    * `@Java` 修饰的接口中包含无默认实现的非静态泛型方法时，它的子类必须提供该方法的实现，且泛型约束必须保持一致或更严格。
    * `@Java` 修饰的接口中包含有默认实现的非静态泛型方法时，它的子类可以提供重新实现，也可以不提供。
    * `@Java` 修饰的类型实现或继承来自 Java 的接口，且接口中包含泛型方法时，该类型可以实现或重新实现这个泛型方法。

```cangjie
// Cangjie code
open class A{}

@Java
class B <: A {} // compile error, A is neither modified by @Java nor an imported java type.
```

`@Java` 修饰的类，其构造顺序与 Java 保持一致。

`@Java` 修饰的类，如果不指定父类，则父类为 `java.lang.Object`。通过 `@Java` 修饰的类的实例可直接调用 `java.lang.Object` 成员方法。示例代码如下：

```cangjie
// Cangjie code
@Java
class Foo {}
main() {
    var instance = Foo()
    instance.hashCode() // Call java.lang.Object method
}
```

在 Java 中，Class loaders 负责将 Java 类动态地加载到 VM 中。默认情况下，`@Java` 修饰的类会被 Java Application Classloader 加载，它等同于 `@Java["app"]`。而通过 `@Java["ext"]` 修饰则表示该类会被自定义的 Classloader 加载。

`@Java["ext"]` 和 `@Java["app"]` 用法完全相同，唯一区别是 `@Java["ext"]` 修饰的类只能被其他 `@Java["ext"]` 修饰的类所引用，但不影响类中的函数正常引用其他仓颉代码。`@Java["ext"]` 和 `@Java["app"]` 修饰的类都可在 Java 中通过反射进行访问。

#### Java void

在仓颉中调用 Java 方法时，`void` 返回值对应返回 `Unit` 类型，`Unit` 的值在仓颉调用侧分配。当仓颉的类继承了导入的 Java 类并重写了 Java 类的方法（该方法返回 `void`），重写的方法在 Java 侧被调用执行时不会创建 `Unit` 类型。

除了用作为函数返回类型，`Unit` 不允许出现在 `@Java` 修饰的类型的属性和成员函数参数中。

注意：`Unit` 的值在调用侧分配是指 `var a: Unit = JObject.callJMethod()` 等同于 `JObject.callJMethod(); var a: Unit = ()`。

示例如下：

```cangjie
// Cangjie code
@Java
class UnitExample <: SomeJavaClass {
    overrride func foo(): Unit{
        // other code
        return ()       // When the foo function is called on the Java side,
    }                   // the Unit will not be created.
}

main() {
    var instance = UnitExample()
    var a = instance.foo() // Same as instance.foo(); var a：Unit = ()
}
```

#### Java String

仓颉提供 `ffi.java.JString` 类型映射 `java.lang.String`，该类型具有 `java.lang.String` 的所有方法，在运行时两者是同一个类型。导入的 Java 类型中属性、成员方法入参和返回值类型为 `java.lang.String` 时都映射为 `ffi.java.JString`。仓颉原生的 `String` 类型禁止作为 `@Java` 修饰的类的属性、成员方法入参和返回值类型。

`ffi.java.JString` 字面量只支持单行字符字面量，以大写字母 `J` 开头使用双引号定义（例如 `J"singleLineStringLiteral"`）, 双引号的内容可以是任意数量的任意字符，需要注意的是，`ffi.java.JString` 字面量不支持插值，仓颉插值语法的字符串会被当作普通字符串处理。

示例如下：

```cangjie
// Cangjie code
import std.ffi.java.JString

@Java
class A {
    let str1: String = "abc" // compile error
    let str2: JString = J"abc" // pass
}

main() {
    let jstr1: JString = J"Java String"
    let jstr2: String = J"Java String" // compile error, type incompatible
    let isEqual = J"STR".equals(J"str") // isEqual == false
}
```

`ffi.java` 标准库除支持 `java.lang.String` 的所有方法外还支持判等（`==`、 `!=`）以及拼接（`+`）操作。

`ffi.java` 标准库提供原生的 `String` 类型和 `ffi.java.JString` 类型的相互转换，转换函数签名如下：

```cangjie
public func toJString(str: String): JString
public func toString(jstr: JString): String
```

示例如下：

```cangjie
// Cangjie code
import std.ffi.java.*

main() {
    let jstr1 = J"Java" + J"String" // jstr1 == "JavaString"
    let isEqual = J"JavaString" == J"JavaString" // isEqual == true
    let isNotEqual = J"JavaString" != J"javaString" // isNotEqual == true
    let str = toString(J"Java String")
    let jstr = toJString("Cangjie String")
}
```

#### Java Array

仓颉提供 `ffi.java.JArray<T>` 类型映射 Java 的内置数组类型，`ffi.java.JArray<T>` 是一个仓颉泛型类型，其中类型变元 `T` 的类型必须是支持映射到 Java 的类型，包括：基础类型 (`Int8`、`Int16`、`UInt16`、`Int32`、`Int64`、`Float32`、`Float64`、`Bool`)、通过 `@Java` 宏修饰的类型、`JString` 类型、`JArray<T>` 类型。所有上述类型都实现了 `JType` 接口，`T` 具有约束 `where T <: JType`。不在上述范围的自定义类型如果实现接口 `JType` 并在 `JArray<T>` 中使用将产生未定义行为。

`ffi.java.JArray<T>` 有两种创建方法：

* 通过 `Array<T>` 扩展函数 `toJArray` 创建。
* 通过 `ffi.java.JArray<T>()` 或 `ffi.java.JArray<T>(arrayExpr: Array<T>)` 创建。

与 `Array` 类似，对于 `ffi.java.JArray<T>` 类型的实例 `arr`, 数组长度为 `n` ，支持通过 `arr[i]` 的方法访问具体位置处的元素，其中 `i` 为 `0` 到数组长度 `n-1` 的 `Int32` 类型。

`ffi.java.JArray<T>` 类型的成员与 Java 内置数组类型的成员相同，包括：`length` 属性、`clone` 方法以及继承自 `java.lang.Object` 的其他方法。

在 Java 中，`Integer[]` 的直接父类型为 `Number[]`，但在仓颉中使用时， `ffi.java.JArray<Integer>` 和 `ffi.java.JArray<Number>` 无父子类型关系，详细参考[泛型]章节内容。

示例如下：

```cangjie
// Cangjie code
import std.ffi.java.*

main() {
    // create java array with constructor
    let arr1 = JArray<Int64>()
    println(arr1.length)
    let arr2 = JArray<Int64>([1, 2, 3])
    println(arr2.length)

    // create java array with toJArray
    let arr = [1, 2, 3]
    let arr3: JArray<Int64> = arr.toJArray()
    println(arr2.length)
}
```

#### Java Lambda

Java8 开始支持 lambda 表达式，其表达式的类型是特定的函数式接口（[Functional Interfaces](https://docs.oracle.com/javase/specs/jls/se8/html/jls-9.html#jls-9.8)）类型。Java 中的函数式接口是指仅有一个 `abstract` 方法（除 `java.lang.Object` 方法之外）的接口。

在 Java 中可以通过实例化类以及 lambda 表达式来创建函数式接口的实例，以 `java.lang.Runnable` 为例，该接口是 Java 中比较常见的函数式接口类型：

```java
// Java code
@FunctionalInterface
public interface Runnable {
    public abstract void run();
}
```

在 Java 侧支持如下两种方式创建 `Runnable` 的实例：

1. 实现该 `Runnable` 接口，并实例化类：

    ```java
    // Java code
    public class Hello implements Runnable {
        // Implement the Runnable interface.
        public void run() {
            System.out.println("Hello World!");
        }

        public static void main(String[] args) {
            Runnable r = new Hello(); // Create an instance of Hello.
            Thread th = new Thread(r);
            th.start();
        }
    }
    ```

2. 使用 lambda 表达式：

    ```java
    // Java code
    public class Hello {
        public static void main(String[] args) {
            // Use lambda expression.
            Runnable r = () -> System.out.println("Hello World!");
            Thread th = new Thread(r);
            th.start();
        }
    }
    ```

在仓颉中，可以直接导入 Java 侧声明的函数式接口来使用，也可以在仓颉侧声明只有一个 `abstract` 方法并且用 `@Java` 宏修饰的接口，来作为 Java 侧函数式接口使用。

仓颉仅支持通过类实例化的方法来创建 Java 函数式接口的实例，该类需要使用 `@Java` 宏修饰并且实现对应的函数式接口；不支持通过仓颉的 lambda 表达式去创建 Java 函数式接口的实例。

> 仓颉 lambda 表达式的类型不支持直接映射到 Java lambda 表达式的类型。

仓颉在调用 Java 侧入参为 lambda 类型的方法时，需要传入对应的函数式接口的实例。示例如下：

* Java 侧代码如下，定义了一个函数式接口 `MathOperation`，以及一个 Java 类 `LambdaExample`：

    ```java
    // Java code
    package com.example;

    public interface MathOperation {
        int operation(int a, int b);
    }
    ```

    ```java
    // Java code
    package com.example;

    public class LambdaExample {
        // The Java side can be created directly using a lambda expression.
        public MathOperation add = (int a, int b) -> a + b;

        public int foo(int a, int b, MathOperation op) {
           return op.operation(a, b);
        }
    }
    ```

* 仓颉代码如下，导入上述 Java 包，并实现 `MathOperation` 接口：

    ```cangjie
    // Cangjie code
    import javaTest.com.example.*

    @Java
    class Sub <: MathOperation {
        public func operation(a: Int32,b: Int32): Int32 {
            return a - b
        }
    }

    main() {
        var instance = LambdaExample()

        var add = instance.add // Direct access to Java-side functional  interface type properties.
        let res1 = instance.foo(1, 2, add) // Transfer the instance  obtained from the Java side.
        println("foo(1, 2, add) = ${res1}")

        var sub = Sub() // Create an instance.
        let res2 = instance.foo(2, 1, sub)
        println("foo(2, 1, sub) = ${res2}")
    }
    ```

程序正确执行的打印如下：

```shell
foo(1, 2, add) = 3
foo(2, 1, sub) = 1
```

#### Java Enum

仓颉语言支持导入 Java 的 Enum 类型和其相关接口 `java.lang.Enum<E>` 进行使用。

在 Java 语言中，编译器会将 Enum 类型转换为一个继承了 `java.lang.Enum<E>` 的类，例如：

```java
// Java code
public enum Day {
    MONDAY, TUESDAY, WEDNESDAY,
    THURSDAY, FRIDAY, SATURDAY, SUNDAY
}
```

上述 Java 代码中，`enum Day` 最终被转换为字节码中一个名为 `Day` 的类，它继承了 `java.lang.Enum<Day>` ，并且具有两个静态成员方法 `values` 和 `valueOf` 。对于以上 Java 代码，与之匹配的仓颉侧声明为：

```cangjie
// Cangjie code
@Java
public class Day <: java.lang.Enum<Day> {
    public static let MONDAY: Day
    public static let TUESDAY: Day
    public static let WEDNESDAY: Day
    public static let THURSDAY: Day
    public static let FRIDAY: Day
    public static let SATURDAY: Day
    public static let SUNDAY: Day

    public static func values(): JArray<Day>
    public static func valueOf(p: JString): Day
}
```

在仓颉侧可以通过 `import` 导入该 Java 侧枚举类 `Day`, 并访问其 `static` 成员变量及方法，参考如下示例：

```cangjie
// Cangjie code
import std.ffi.java.*
import test.jcode.Day

main() {
    var day = Day.MONDAY         // day's type is class Day
    var values = Day.values()    // values's type is JArray<Day>
    day = values[0]              // day's value is Day.MONDAY
    day = Day.valueOf(J"MONDAY") // day's value is Day.MONDAY
}
```

在仓颉中可以定义一个 Java Enum 类型，并且支持作为函数参数传递给 Java。

例如，如果 Java 侧有以下接口 `getName`，用于获取对应 Enum 对象的字符串形式，其接受一个 Enum 类型的参数：

```java
// Java code
package example;

public class Jffi {
    public <E extends Enum<E>> String getName(E e){
        return e.name();
    }
}
```

在仓颉中，我们可以通过以下方式定义一个 Java Enum 类型 `Day`，它是 Java Enum 的子类，每个 Enum 成员都是它的静态成员变量，通过 `Day` 的构造方法进行初始化。

```cangjie
// Cangjie code
import test.example.*
import std.ffi.java.*
import java8.java.lang.Enum as E

@Java
public class Day <: E<Day> {
    public static var MONDAY: Day = Day(J"MONDAY", 0)
    public static var TUESDAY: Day = Day(J"TUESDAY", 1)
    public static var WEDNESDAY: Day = Day(J"WEDNESDAY", 2)
    public static var THURSDAY: Day = Day(J"THURSDAY", 3)
    public static var FRIDAY: Day = Day(J"FRIDAY", 4)
    public static var SATURDAY: Day = Day(J"SATURDAY", 5)
    public static var SUNDAY: Day = Day(J"SUNDAY", 6)

    public init(s: JString, i: Int32) { super(s, i) }
}
```

注意：由于运行时对静态初始化器的处理策略，定义的 Enum 类型中，每个 Enum 成员都必须通过 `var` 定义，并且构造函数应使用 `public` 修饰。

使用时，`Day` 可以直接作为实数传递给 Java 函数 `getName`。

```cangjie
// Cangjie code
main(){
    var jffi = Jffi()
    var h: JString = jffi.getName(Day.SUNDAY) // h is J"SUNDAY".
    return 0
}
```

#### Java 可变长参数

在 Java 语言中，可变长参数是一个语法糖，其等同于一个 `Java Array` 类型的参数。从仓颉侧传递一个 Java 的可变长参数时，需要构造一个对应类型的 `JArray` 对象作为实参传递。

示例：

如果有一个 Java 方法定义如下：

```java
// Java code
package jcode;

public class JavaVarargsExample {
    public void foo(String... args) {
        // some java code.
    }
}
```

`foo` 函数对应仓颉的声明为：

```cangjie
// Cangjie code
@Java
public class JavaVarargsExample {
    public func foo(args: JArray<String>): Unit
}
```

如果需要在仓颉侧调用，需要手动构造 `JArray` 对象：

```cangjie
// Cangjie code
// 'test' is module name of java code above.
import test.jcode.JavaVarargsExample
import std.ffi.java.*

main() {
    var varargsExample = JavaVarargsExample()
    // No argument.
    var argsArray0 = JArray<String>()
    varargsExample.foo(argsArray0)
    // Two arguments.
    var argsArray1 = JArray<String>([J"1", J"2"])
    varargsExample.foo(argsArray1)
}
```

### Java 修饰符

导入的 Java 类和接口以及其成员，在仓颉中使用时，其修饰符将根据一定规则进行映射，它们的映射关系将在下文中详细讨论。

#### 接口的修饰符

Java 接口的修饰符与仓颉 `@Java` 修饰的接口修饰符映射关系如下：

|     Java      | Cangjie @Java | 行为 |
| ------------- | ------------- | ---- |
| public        | public        | 该接口对外公开。 |
| (no modifier) | (no modifier) | 默认可见性，仅在包内可见。 |
| strictfp      | -             | 仓颉无对应修饰符，在仓颉侧调用 Java 函数使用该类型时，对应的类型与原行为一致。 |

例如，如下是一个对外公开的 Java 接口：

```java
// Java code
public interface JavaCode {}
```

那么与之表达相同含义的仓颉 `@Java` 类写为：

```cangjie
// Cangjie code
@Java
public interface JavaCode {}
```

#### 类的修饰符

Java 类的修饰符与仓颉 `@Java` 类的修饰符映射关系如下：

|       Java       |  Cangjie @Java  | 行为 |
| ---------------- | --------------- | ---- |
| public           | public          | 该接口对外公开。 |
| (no modifier)    | (no modifier)   | 默认可见性，仅在包内可见。 |
| abstract         | abstract        | 抽象类修饰符。 |
| final/(no final) | (non open)/open | 不允许/允许被其他类型继承。 |
| strictfp         | -               | 仓颉无对应修饰符，在仓颉侧调用 Java 函数使用该类型时，对应的类型与原行为一致。 |

例如，如下是一个对外公开且不可被其他类型继承的类：

```java
// Java code
public final class JavaCode {}
```

那么与之表达相同含义的仓颉 `@Java` 类写为：

```cangjie
// Cangjie code
@Java
public class JavaCode {}
```

#### 成员方法的修饰符

Java 成员方法的修饰符与仓颉 `@Java` 类或接口的成员方法修饰符映射关系如下：

|       Java       |  Cangjie @Java  | 行为 |
| ---------------- | --------------- | ---- |
| public           | public          | 该接口对外公开。 |
| private          | private         | 仅在本类型中可见。 |
| protected        | protected       | 本类或者子类中可见，同包中不同类型中可见。 |
| (no modifier)    | (no modifier)   | 默认可见性，仅在包内可见。 |
| final/(no final) | (non open)/open | 不允许/允许被其他类型继承。 |
| static           | static          | 指定方法被所有对象共享，通过类型名直接调用。 |
| synchronize      | -               | 仓颉无对应修饰符，仓颉侧调用该方法仍然保持原有加锁或释放行为。 |
| native           | -               | 仓颉无对应修饰符，仓颉侧可正常调用该修饰符对应的 Java 方法。 |
| strictfp         | -               | 仓颉无对应修饰符，在仓颉侧调用 Java 函数使用该类型时，对应的类型与原行为一致。 |
| @Override        | override        | 该修饰符（注解）标明该方法是重写父类的方法，当父类中无同签名方法时报错。 |

> **注意：**
>
> `@Override` 在 Java 中为注解，仓颉对应的关键字 `override` 为修饰符。

例如，如下是一个 `JavaCodeSub` 类，它继承了 `JavaCode` ，`JavaCodeSub` 覆盖了 `JavaCode` 中的 `foo` 方法，可以通过 `@Override` 进行标注：

```java
// Java code
class JavaCode {
    public void foo() {
        System.out.println("JavaCode foo");
    }
}

class JavaCodeSub extends JavaCode {
    @Override
    public void foo() {
        System.out.println("JavaCodeSub foo");
    }
}
```

那么与之表达相同含义的仓颉 `@Java` 类写为：

```cangjie
// Cangjie code
@Java
open class JavaCode {
    public open func foo(): Unit {
        println("JavaCode foo")
    }
}

@Java
class JavaCodeSub <: JavaCode {
    public override func foo(): Unit {
        println("JavaCodeSub foo")
    }
}
```

#### 成员变量的修饰符

Java 类中成员变量的修饰符与仓颉 `@Java` 类或接口的成员变量修饰符映射关系如下：

|       Java       |  Cangjie @Java  | 行为 |
| ---------------- | --------------- | ---- |
| public           | public          | 该接口对外公开。 |
| private          | private         | 仅在本类型中可见。 |
| protected        | protected       | 本类或者子类中可见，同包中不同类型中可见。 |
| (no modifier)    | (no modifier)   | 默认可见性，仅在包内可见。 |
| final/(no final) | let/var         | 该成员变量不允许/允许被修改。 |
| static           | static          | 指定方法被所有对象共享，通过类型名直接调用。 |
| transient        | -               | 仓颉无对应修饰符，仓颉侧导入该成员变量后，调用 Java 序列化接口保持原有属性。 |
| volatile         | -               | 仓颉无对应修饰符，且仓颉侧导入包含该修饰符修饰的成员的类型后，该成员会正常导入，但仓颉侧访问时报错。 |

> **注意：**
>
> 仓颉可以构造和使用包含 `volatile` 的类型，但不允许在仓颉侧访问它。

如下例子：

```java
// Java code
package jcode;
public class JavaExample {
    volatile int i = 0;
}
```

在仓颉中，可以正常构造 `JavaExample` 类对象，但不允许访问 `volatile` 成员变量 `i` ：

```cangjie
// Cangjie code
import test.jcode.JavaExample
import std.ffi.java.*

main() {
    var a = JavaExample() // Ok
    a.i // Error, Java volatile member variables cannot be accessed in Cangjie.
    0
}
```

### 可空类型

对所有 Java 侧可能为 `null` 的类型，在仓颉侧使用时有两种方式：

* 当作仓颉中非可空类型进行直接使用。

  将 Java 侧得到的可空变量存储到任意非可空变量时，如果值为 `null`, 运行时将抛出 `NullPointerException` 异常；运行时，对值为 `null` 的引用变量直接访问其成员或调用其成员方法时也将抛出 `NullPointerException` 异常。该使用方式下抛出的 `NullPointerException` 异常会被包在 `JavaException` 中，在仓颉代码中应捕获后者，之后通过 `getCause` 方法得到原始异常。

* 将其存储到 `Option` 类型变量中。

  编译器自动将其封装为 `Option` 类型，如果在运行时为 `null` ，则映射为 `Option` 类型中的 `None` ，否则映射为 `Some constructor`。

下面是一个例子，Java 侧提供了以下类型：

```java
// Java code
package example;

public class Person {
    public String name;

    public static Person getNull() {
        return null;
    }
}
```

在仓颉侧使用该类型：

```cangjie
// Cangjie code
import test.example.*

main() {
    let person1 = Person.getNull() // will throw NullPointerException

    let person2: ?Person = Person.getNull() // person2 is Option<Person>.None
    match (person2) {
        case Some(v) => ()
        case None => println("person2 is Option<Person>.None") // will reach here
    }

    let person3 = Person()
    let name = person3.name    // will throw NullPointerException
    person3.name.toLowerCase() // will throw NullPointerException
}
```

### 异常

在仓颉侧调用 Java 代码时，Java 侧抛出的所有异常都会被映射为仓颉类 `JavaException` ，可以被仓颉捕获；同样的，在 Java 侧执行仓颉代码时，仓颉侧抛出的所有异常类都会被映射为 Java 类 `CangjieException` ，可以在 Java 侧被捕获。它们的映射关系如下表：

| Cangjie Type                            | Java Type                    |
| --------------------------------------- | ---------------------------- |
| Exception or Error and their subclasses | CangjieException             |
| JavaException                           | Throwable and its subclasses |

在仓颉和 Java 侧都可以通过 `try/catch` 语句对映射的异常进行捕获。在仓颉侧捕获 Java 侧抛出的异常时，可以通过 `getCause` 方法获取其实际抛出的异常类，再进行判断处理。

`JavaException` 定义在 `std/ffi.java` 中。

`CangjieException` 包名为 `cangjie.lang`。

示例代码：

```cangjie
// Cangjie code
import java8.java.lang.Integer
import java8.java.lang.Throwable
import java8.java.lang.NumberFormatException
import java8.java.lang.ArrayIndexOutOfBoundsException

main() {
    try {
        var s = J"abc"
        var n = Integer.parseInt(s) // It will throw exception.
        let array = JArray<Int64>([0, 1, 2, 3, 4, 5])
        var el = array[n]
    } catch (e: JavaException) {
        var cause: Throwable = e.getCause()
        match (cause) {
            case _: NumberFormatException => print("Wrong parseInt input!")
            case _: ArrayIndexOutOfBoundsException => print("Out of Bounds!")
            case _ => ()
        }
    }
}
```

### 泛型

在仓颉中，可以直接导入 Java 侧泛型类型，创建其实例、调用其方法、继承（泛型类）或实现（泛型接口）该类型等。导入的 Java 泛型类型以及通过 `@Java` 修饰的泛型类型在编译时会做类型擦除（与 Java 保持一致）。

在仓颉中使用 Java 中定义的泛型类型的示例代码如下：

```cangjie
// Cangjie code
import java8.java.util.ArrayList as JArrayList
import java8.java.lang.Integer

main() {
    var arrayList = JArrayList<Integer>()
    arrayList.add(Integer(1))
    arrayList.add(Integer(3))
    arrayList.add(Integer(5))
    var iter = arrayList.iterator()
    while (iter.hasNext()) {
        iter.next().toString()
    }
}
```

大部分 Java 泛型都可以直接在仓颉中进行使用，但必须遵循一定的映射规则和使用限制，详细见下面章节。

#### Java 类型参数约束

Java 中泛型类型参数约束只能通过 `extends` 指定上界（不支持指定下界），可以有多个上界，多上界的约束中第一个必须是类，之后的必须是接口。其类型参数约束的语法如下：

```java
T extends C1 & I1 & I2 & ... & In
T extends C1
T extends I1
```

上述语法可直接映射仓颉如下语法：

```cangjie
where T <: C1 & I1 & I2 & ... & In
where T <: C1
where T <: I1
```

需要注意的是，`@Java` 注解的泛型类和接口具有如下特点：

* 类型是 `java.lang.Object` 的子类。
* 类型参数隐含带有约束 `where T <: java.lang.Object`（`ffi.java.JArray<T>` 中的 `T` 除外，`T` 可能是 `Int64` 等非 `java.lang.Object` 子类型的类型）。
* 不能通过类型参数 `T` 访问上界中定义的 `static` 成员，而非 `@Java` 注解的仓颉泛型类型是允许的。

#### Java 类型通配符

Java 中通配符用来表示一个系列的类型，可以作为类型实参（不能用于泛型方法），包括三种类型：无界、上界、下界通配符。

在 Java 中，当非通配符的类型约束过于严格时可以使用通配符作为类型参数。如下代码，调用 `sort` 方法时将出现编译错误：

```java
// Java code
class Person implements Comparable<Person> {}
class Student extends Person {}
class Utilities {
    public static <T extends Comparable<T>> void sort(List<T> list) {}
}

List<Student> list = new ArrayList<Student>();
Utilities.sort(list); // Error
```

如果使用通配符作为类型参数，则 `sort` 可以正常调用，修改后的 `sort` 方法如下：

```java
// Java code
class Utilities {
    public static <T extends Comparable <? super T >> void sort(List<T> list) {}
}
```

在仓颉中，不支持通配符类型，但可以按照一定规则映射。所有需要映射的通配符类型的情况如下：

* 导入的 Java 类型的成员属性、方法入参以及方法返回值的类型存在通配符类型；
* `@Java` 注解修饰的仓颉类型继承或实现导入的 Java 类型，并且该类型中存在通配符类型，比如重写导入的 Java 类型的成员方法时，该方法入参或方法返回值的类型存在通配符类型。

Java 中的上界、下界以及无界通配符类型与仓颉泛型类型的映射规则如下：

| Java                | Cangjie                  |
| ------------------- | ------------------------ |
| `List<? super T>`   | `List<java.lang.Object>` |
| `List<? extends T>` | `List<T>`                |
| `List<?>`           | `List<java.lang.Object>` |

#### 泛型实例成员函数

在仓颉中，在继承或实现导入的 Java 类型时，可以使用泛型成员函数 `override` 父类成员函数。需要注意的是：

* 泛型成员函数语法与全局泛型成员函数语法要求相同。
* 泛型成员函数所在的类或接口必须使用 `@Java` 注解。

需要注意的是返回类型必须和被重写方法的返回类型相同或者是返回类型的子类型。

参考示例代码如下：

```cangjie
// Cangjie code
package example

import test.java.GenericClassExample // Importing Java Generic Types.

@Java
class B <: GenericClassExample {
    override public foo<T>(t: T) { // Overrides super class member functions only.
        // do something
    }
}

main() {
    var p = B()
    p.foo(p)
}
```

在仓颉中子类成员不可遮盖父类成员，而 Java 允许。当发生遮盖的两个 Java 类在仓颉中当作纯仓颉的泛型类型参数时，运行时对遮盖变量的访问与 Java 侧行为一致。

#### Java Raw 类型

Java 侧 Raw 类型直接映射为对应的 `java.lang.Object` 的泛型类型，如下表：

| Java Generic Type | Java Raw Type | Cangjie                |
| ----------------- | ------------- | ---------------------- |
| `C1`              | `C1`          | `C1<java.lang.Object>` |

参考如下类型：

```java
// Java code
package com.example;

public class A<T> {}

public class C {
    public A a; // A is a raw type
}
```

在仓颉中，使用如下：

```cangjie
// Cangjie code
import java8.java.lang.Object as JObject
import test.com.example.*

main() {
    var c = C()
    var rawType: ?A<JObject> = c.a
}
```

> **注意**：
>
> * 若泛型类型没有明确指定上界，则相应 Raw 类型映射为  `java.lang.Object`。
> * 若泛型类型只有一个上界，则相应 Raw 类型映射为第一个上界。
> * 若泛型类型的上界超过一个，暂不支持。

### Java 注解

Java 注解是一种特殊接口类型，Java 侧部分自定义注解类型会被映射为仓颉注解类型，允许仓颉侧导入和使用，但只能在 `@Java` 修饰的类型中使用。

示例代码如下，在 Java 中定义了一个注解类型：

```java
// Java code
package com.example;

@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
public @interface JavaAnno {
    String value();
}
```

在仓颉中导入上述注解并使用，示例代码如下：

```cangjie
// Cangjie code
import com.example.*

// pure cangjie class
class CangjieClass {
    // annotation types from java can only be used in @Java-modified types.
    @JavaAnno[J"value"] // compile error
    func a(): Unit{}
}

@Java
class JavaClass {
    @JavaAnno[J"value"] // OK
    func a():Unit {}
}
```

不支持导入 Java 的内置注解类型，Java 8 的内置注解类型包括：`@Override`、`@Deprecated`、`@SuppressWarnings`、`@Retention`、`@Documented`、`@Target`、`@Inherited`、`@SafeVarargs`、`@FunctionalInterface`、`@Repeatable`、`@Native`。

不支持导入 Java 侧 `@Retention` 属性值为 `RetentionPolicy.SOURCE` 的注解类型。

导入的 Java 注解类型在仓颉侧使用时需要满足仓颉注解对使用位置的约束（详见“注解”章节 `target` 参数的说明）。Java 使用 `@Target` 注解（接收的参数是一个 `ElementType[]`）用于指定其修饰的注解类型可在哪些位置使用，与仓颉注解里的 `target` 参数（接收的参数是一个 `Array<AnnotationKind>`）作用相同。对于一个导入的 Java 注解类型：

* 如果使用了 `@Target` 注解来限制其使用位置，其 `@Target` 属性值将按照下表映射为仓颉注解的 `target` 参数值。
* 如果没有使用 `@Target` 注解，则将其映射为仓颉注解的 `target` 参数值为 `[Type, Parameter, Init, MemberFunction, MemberVariable]`。

| Java ElementType | Cangjie AnnotationKind |
|------------------|------------------------|
| TYPE             | Type           |
| FIELD            | MemberVariable |
| METHOD           | MemberFunction |
| PARAMETER        | Parameter      |
| CONSTRUCTOR      | Init           |
| LOCAL_VARIABLE   | -              |
| ANNOTATION_TYPE  | -              |
| PACKAGE          | -              |
| TYPE_PARAMETER   | -              |
| TYPE_USE         | -              |

### 不支持的用法

在仓颉的 Java 互操作中，存在一些不支持的场景：

* 若 Java 中 `field` 的类型、`method` 的入参或返回类型是未知的类型，在仓颉侧无法访问该 `field`、`method`；
* 若 Java 中类型的父类/父接口中存在未知的类型，则认为不存在相应的继承/实现关系；
* 若 Java 中泛型声明的泛型约束中存在未知的类型，在仓颉侧无法访问该泛型声明；
* 对于 Java 中非泛型类的泛型构造函数，在仓颉侧无法访问；
* 对于 Java 中的内部类，暂时无法在仓颉侧访问；
* 若 Java 中存在同名的 `field` 和 `method`，在仓颉侧只能访问 `method`，无法访问 `field`；
* 若 Java 中的标识符使用了仓颉不支持的字符，在仓颉侧无法访问；
* 对于 Java 中仅编译期可见的注解，在仓颉侧无法访问。
* 若 Java 中类型的泛型函数未被 `final` 修饰，在仓颉侧继承该类型时不允许重写该泛型方法。
* 对于 Java 中支持，但仓颉不支持的修饰符，在仓颉侧访问时，其行为参照 [Java 修饰符] 章节。
* 对于导入的 Java 注解，若其参数的类型为 `JArray`、`Class`，如果它有默认值，默认值会被忽略，且由于无法在仓颉中为其构造相应类型的值，故无法在仓颉侧使用该注解。

未知类型主要包括上述无法访问的 Java 类型、非 `public` 的 Java 类型、`cjpm` 配置文件中某个 Java `module` 指定的 `jar` 文件列表中不存在的 Java 类型，`cjpm` 详见《仓颉语言工具链用户手册》。

### JType

除类型映射一节提供的与 Java 类型进行映射的类型外，仓颉还提供了一个 `JType` 接口，接口本身不包含任何方法，它可以作为所有 Java 互操作支持的类型的父类型，便于在泛型约束中使用。

需要注意的是：

1. `JType` 接口是仓颉中的一个接口类型，它本身不满足 `JType` 约束；
2. `JType` 接口不允许被继承、扩展；
3. `JType` 接口不会突破子类型的使用限制。

`JType` 的使用示例如下：

```cangjie
// Cangjie code
import std.ffi.java.*

class A<T> where T <: JType {
    var a: T

    init(a: T) {
        this.a = a
    }
}

main() {
    var a1 = A<Int8>(1)
    var a2 = A<Int16>(2)
    var a3 = A<UInt16>(3)
    var a4 = A<Int32>(4)
    var a5 = A<Int64>(5)

    if (!(a1.a == 1 && a2.a == 2 && a3.a == 3 && a4.a == 4 && a5.a == 5)) {
        return 1
    }

    var aa1 = A<Float32>(1.0)
    var aa2 = A<Float64>(2.0)
    var aa3 = A<Bool>(true)
    if (!(aa1.a == 1.0 && aa2.a == 2.0 && aa3.a)) {
        return 1
    }

    var au = A<Unit>(())
    0
}
```
