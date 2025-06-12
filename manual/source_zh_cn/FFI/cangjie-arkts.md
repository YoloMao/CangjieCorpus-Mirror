# 仓颉-ArkTS 互操作

在 HarmonyOS 系统上，ArkTS 具备完整广泛的生态，为复用 ArkTS 生态，仓颉支持与 ArkTS 高效跨语言互通。

仓颉-ArkTS 互操作基于仓颉 CFFI 能力，通过调用 ArkTS 运行时接口，为用户提供库级别的 ArkTS 互操作能力。

使用场景：

1. 在 ArkTS 应用开发仓颉模块：把用户仓颉代码封装成为 ArkTS 模块，能够被 ArkTS 代码加载和调用。
2. 在仓颉应用里使用 ArkTS 存量库：在仓颉代码里创建新的 ArkTS 运行时，并加载和执行 ArkTS 的字节码。

互操作库的主要组成和功能：

1. JSValue: 统一的 ArkTS 数据类型，在跨语言调用中做传参，对 ArkTS 类型做判断和做数据转换。
2. JSContext: 一个 ArkTS 互操作上下文，用户创建 ArkTS 数据，辅助把 JSValue 转换为仓颉数据。
3. JSCallInfo: 一次 ArkTS 函数调用的参数集合，包含所有的入参和 this 指针。
4. JSRuntime: 一个由仓颉创建的 ArkTS 运行时。

## 在 ArkTS 应用里开发仓颉模块

在 ArkTS 应用中开发仓颉模块有以下两种方式：

1. 使用[仓颉与 ArkTS 声明式互操作宏](#仓颉与-arkts-声明式互操作宏)。声明式互操作宏以静态声明来简化使用；对于纯 ArkTS 代码的互操作场景，推荐使用。
2. 使用[仓颉-ArkTS 互操作库](#仓颉与-arkts-互操作库)。提供动态类型接口，适用于与 javascript 和 typescript 相互调用；偏底层接口，适用于追求性能的场景。

两种方式可以只使用一种也可以结合使用。

### 仓颉与 ArkTS 声明式互操作宏

#### 声明式互操作宏简介

针对在 ArkTS 应用里开发仓颉模块的场景，可以通过本章节介绍的仓颉-ArkTS 声明式互操作宏来简化互操作开发难度，仓颉-ArkTS 声明式互操作宏通过解析被注解修饰的仓颉代码，自动生成 ArkTS 声明文件及互操作层代码，为开发者提供近原生调用的开发体验。

#### 使用方法

针对互操作章节[仓颉与 ArkTS 互操作库](./cangjie-arkts.md#仓颉与-arkts-互操作库)中仓颉侧部分代码，可以按照如下的步骤进行简化。

1. 导入互操作库 `import ohos.ark_interop.*` 和声明式互操作宏库 `import ohos.ark_interop_macro.*`。
2. 在仓颉文件中，针对 class、interface 和函数，可以使用 `@Interop[ArkTS]` 进行修饰，被修饰的对象是希望被 ArkTS 调用的。
3. 在 DevEco Studio 中的仓颉文件或者 module 名称右键选择“Generate Cangjie-ArkTS Interop API”，会在 cangjie 目录下生成 ark_interop_api 的声明文件。
4. ArkTS 侧添加依赖并 `import ark_interop_api` 即可使用。

module 内目录结构

```
├─entry
│  └─src
│      └─main
│         ├─cangjie              // 仓颉页面声明代码
|         |  ├─src               // 仓颉源码
|         |  └─ark_interop_api   // 自动生成互操作接口声明文件目录
│         ├─ets                  // ArkTS页面以及Xcomponent占位
│         └─resources
```

#### 使用范围

##### 数据类型

声明式互操作宏支持转换的数据类型如下表。

| cangjie 类型 | ArkTS 对应类型 | 备注 |
| :--- | :--- | :--- |
| Int8、Int16、Int32、Int64、UInt8、UInt16、UInt32、UInt64、Float16、Float32、Float64 | number | - |
| Bool | boolean | - |
| String、JSStringEx | string | - |
| Unit | undefined | - |
| Option\<T> | T \| undefined | T 不支持 Option\<T> 类型和函数类型，如果 T 为自定义类型（class 或 interface 类型），该自定义类型必须被 Interop 宏修饰 |
| func | function | - |
| JSArrayEx\<T>| Array\<T> | T 不支持函数类型，如果 T 为自定义类型（class 或 interface 类型），该自定义类型必须被 Interop 宏修饰 |
| JSHashMapEx\<K, V> | Map\<K, V> | V 不支持函数类型，如果 V 为自定义类型（class 或 interface 类型），该自定义类型必须被 Interop 宏修饰 |
| Array\<Byte> | ArrayBuffer | - |
| class | class | - |
| interface | interface | - |

> **注意：**
>
> * 在被 `Interop` 宏所应用的函数签名，和对成员变量和属性的类型标注中，不支持使用语法糖，比如 `Option<T>` 类型的语法糖 `?T`。
> * `JSStringEx`、`JSArrayEx<T>` 和 `JSHashMapEx<K, V>` 三种类型只能使用在被 `Interop` 宏所应用的函数、class 和 interface 中。

##### 适用场景

声明式互操作宏可修饰范围包括函数、class 和 interface，针对不同的场景使用建议如下表。

| 适用场景 | 使用类型 | 修饰 |
| :--- | :--- | :--- |
| ArkTS 调用仓颉函数 | 函数 | @Interop[ArkTS] |
| ArkTS 调用耗时仓颉函数 | 异步函数 | @Interop[ArkTS, Async] |
| 用于返回仓颉侧创建的对象给 ArkTS | class  | @Interop[ArkTS] 修饰整个 class<br>@Interop[ArkTS, Invisible] 修饰 class 中不准备暴露的成员 |
| 用于传递 ArkTS 侧创建的对象给仓颉 | interface  | @Interop[ArkTS] |

##### 函数特性

| 修饰符 | 类型参数 | 命名参数 | 返回类型 |
| :--- | :--- | :--- | :--- |
| 必带 public，不支持其他 | 不支持 | 支持，ArkTS 调用方法和非命名参数一致，不支持默认值 | 不可缺省 |

##### 异步函数特性

| 修饰符 | 类型参数 | 命名参数 | 返回类型 |
| :--- | :--- | :--- | :--- |
| 必带 public，不支持其他 | 不支持 | 支持，ArkTS 调用方法和非命名参数一致，不支持默认值 | 不可缺省 |

> **注意：**
>
> `JSStringEx`、`JSArrayEx<T>` 和 `JSHashMapEx<K, V>` 三种类型不能在异步函数中使用。

##### 接口特性

| 修饰符 | 类型参数 | 父接口 | 成员函数 | 操作符重载 | 成员属性 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 必带 public，不支持其他 | 不支持 | 不支持 | 支持，无修饰符，其他和函数限制一致 | 不支持 | 支持，支持 mut 修饰符 |

##### class 特性

| 修饰符 | 类型参数 | 类继承| 接口实现 | 静态初始化器 | 构造函数 | 成员变量 | 成员函数 | 操作符重载 | 成员属性 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 必带 public，不支持其他 | 不支持 | 支持书写，不会展开 | 支持书写，不会展开 | 不支持 | 有且仅有一个普通构造函数或主构造函数，修饰符必带 public，不支持其他修饰符，不支持成员变量形参，不支持参数默认值 | 可选默认值，修饰符必带 public，不支持其他修饰符，不可省略变量类型标注 | 和函数限制一致 | 不支持 | 修饰符必带 public，可选 mut

> **注意：**
>
> class 的特性约束只针对准备暴露给 ArkTS 的部分，可以通过修饰符不带 `public` 和 `@Interop[ArkTS, Invisible]` 修饰的方式标记不准备暴露的成员。

#### 示例

##### 函数

```cangjie
import ohos.ark_interop.*
import ohos.ark_interop_macro.*

@Interop[ArkTS]
public func addF64(a: Float64, b!: Float64): Float64 {
    a + b
}
```

```typescript
// 自动生成 .d.ts
declare interface CustomLib {
    addF64(a: number, b: number): number
}

// ArkTS 调用
import {CustomLib} from "libark_interop_api.so"

let cjLib : CustomLib = requireCJLib("libentry.so") as CustomLib

console.log("result " + cjLib.addF64(1, 2))
```

##### 异步函数

```cangjie
import ohos.ark_interop.*
import ohos.ark_interop_macro.*

@Interop[ArkTS, Async]
public func doAsync(a: Float64, b: Float64): Float64 {
    a + b
}
```

```typescript
// 自动生成 .d.ts
declare interface CustomLib {
    doAsync(a: number, b: number): Promise<number>
}

// ArkTS 调用
import {CustomLib} from "libark_interop_api.so"

let cjLib : CustomLib = requireCJLib("libentry.so") as CustomLib

cjLib.doAsync(1, 2).then(result => {
    console.log("result " + result)
})
```

##### 接口

```cangjie
import ohos.ark_interop.*
import ohos.ark_interop_macro.*

@Interop[ArkTS]
public interface InterfaceDemo {
    mut prop id: Float64
    func foo(a!: Float64): Float64
}

@Interop[ArkTS]
public func doInterface(a: InterfaceDemo): Float64  {
    return a.foo(a: a.id)
}
```

```typescript
// 自动生成 .d.ts
export declare interface InterfaceDemo {
    id: number
    foo: (a: number) => number
}

export declare interface CustomLib {
    doInterface(a: InterfaceDemo): number
}

// ArkTS 调用
import {CustomLib, InterfaceDemo} from "libark_interop_api.so"

let cjLib : CustomLib = requireCJLib("libentry.so") as CustomLib

let callbackInterface = (a: number): number => {
  return a + 1
}

let inter1: InterfaceDemo = {foo: callbackInterface, id: 6}

console.log("result " + cjLib.doInterface(inter1))
```

##### 类

```cangjie
import ohos.ark_interop.*
import ohos.ark_interop_macro.*

@Interop[ArkTS]
public class ClassDemo {
    public var value2: Float64 = 1.0
    public let value3: Float64 = 1.0
    @Interop[ArkTS, Invisible]
    public var value4: Float64 = 1.0

    public init(a: Float64) {
        value2 = a
    }

    public func foo(a: Float64 ): Float64 {
        a
    }

    @Interop[ArkTS, Invisible]
    public func foo2(): Float64 {
        1.0
    }

    public mut prop id: Float64 {
        get() {
            value2
        }
        set(value) {
            this.value2 = value
        }
    }

    public prop id2: Float64 {
        get() {
            value3
        }
    }

    @Interop[ArkTS, Invisible]
    public prop id3: Float64 {
        get() {
            value4
        }
    }
}
```

```typescript
// 自动生成 .d.ts
export declare class ClassDemo {
    value2: number
    value3: number
    foo(number): number
    id: number
    id2: number
}

export declare interface CustomLib {
    ClassDemo: {new (a: number): ClassDemo}
}

// ArkTS 调用
import {CustomLib, ClassDemo} from "libark_interop_api.so"

let cjLib : CustomLib = requireCJLib("libentry.so") as CustomLib

let class1: ClassDemo = new cjLib.ClassDemo(3)

console.log("result " + class1.foo(5))
console.log("result " + class1.value2)
```

### 仓颉与 ArkTS 互操作库

> **说明：**
>
> 优先推荐使用“声明式互操作宏”的方式实现 ArkTS 调用仓颉模块，互操作宏的方式无法满足开发者场景时再使用“仓颉与 ArkTS 互操作库”的方式。

开发仓颉互操作模块：

1. 【仓颉侧】导入互操作库。

    ```cangjie
    import ohos.ark_interop.*
    ```

2. 【仓颉侧】定义要导出的函数，可被 ArkTS 调用的仓颉函数的类型是固定的：`(JSContext, JSCallInfo)->JSValue`。

    ```cangjie
    func addNumber(context: JSContext, callInfo: JSCallInfo): JSValue {
        // 从 JSCallInfo 获取参数列表
        let arg0: JSValue = callInfo[0]
        let arg1: JSValue = callInfo[1]

        // 把 JSValue 转换为仓颉类型
        let a: Float64 = arg0.toNumber()
        let b: Float64 = arg1.toNumber()

        // 实际仓颉函数行为
        let value = a + b

        // 把结果转换为 JSValue
        let result: JSValue = context.number(value).toJSValue()

        // 返回 JSValue
        return result
    }
    ```

3. 【仓颉侧】注册要导出的函数。

    ```cangjie
    // 类名没有影响
    class Main {
        // 定义静态构造函数（也可用全局变量和静态变量的初始化表达式触发）
        static init() {
            // 注册键值对
            JSModule.registerModule {context, exports =>
                exports["addNumber"] = context.function(addNumber).toJSValue()
            }
        }
    }
    ```

4. 【ArkTS 侧】导入 ark_interop_loader，这是一个在 ohos-sdk 中提供的 napi 模块，作为仓颉运行时的启动器和仓颉模块的加载器。

    ```typescript
    import {requireCJLib} from "libark_interop_loader.so"
    ```

5. 【ArkTS 侧】定义仓颉库导出的接口。

    ```typescript
    interface CustomLib {
        // 定义的仓颉互操作函数，名称与仓颉侧注册名称一致。一般先定义 ArkTS 函数声明，在实现仓颉函数时根据声明来解析参数和返回。
        addNumber(a: number, b: number): number;
    }
    ```

6. 【ArkTS 侧】导入和调用仓颉库。

    ```typescript
    // 导入仓颉库，仓颉模块默认编译产物是 libentry.so，用户可以在 cjpm.toml 中修改配置。
    const cjLib = requireCJLib("libentry.so") as CustomLib;
    // 调用仓颉接口
    let result = cjLib.addNumber(1, 2);
    console.log(`1 + 2 = ${result}`);
    ```

上述流程中，仓颉侧定义的要导出的函数中通过互操作库使用了最基础的仓颉类型，其他类型可以参照章节[操作 ArkTS 数据](./cangjie-arkts.md#操作-arkts-数据)和[在 ArkTS 里操作仓颉对象](./cangjie-arkts.md#在-arkts-里操作仓颉对象)。

## 在仓颉应用里使用 ArkTS 模块

ArkTS 模块的编译产物主要有两种：

1. C 代码（+ArkTS）编译成 so。
2. 纯 ArkTS 代码编译成 abc。

### 加载 ArkTS so 模块

ArkTS so 模块根据部署方式的不同，分为以下几种：

1. 随系统发布，在镜像的`/system/lib64/module`目录下。
2. 随应用（hap）发布，在应用的`/libs/arm64-v8a`目录下，安装后在设备上的全局路径（通过`hdc shell`观察到的路径）：`/data/app/el1/bundle/public/${bundleName}/libs/arm64`、沙箱路径（运行时可访问路径）：`/data/storage/el1/bundle/libs/arm64`。
3. 随动态库（hsp）发布。

这里主要介绍怎么加载随系统发布的 so 模块，这些 so 模块的详细介绍请参见 HarmonyOS 的官方文档。

接下来以[相册管理](https://developer.huawei.com/consumer/cn/doc/harmonyos-references-V5/js-apis-photoaccesshelper-V5)模块作为示例，详细的介绍加载流程。

1. 查看 ArkTS 文档，其导入模块的范本如下。

    ```typescript
    import photoAccessHelper from '@ohos.file.photoAccessHelper';
    ```

2. 创建 ArkTS 运行时，准备互操作上下文。

    ```cangjie
    import ohos.ark_interop.*

    func tryLoadArkTSSo() {
        // 创建新的 ArkTS 运行时
        let runtime = JSRuntime()
        // 获取互操作上下文
        let context = runtime.mainContext
        ...
    }
    ```

3. 根据 ArkTS 文档里模块导入名称，推导仓颉的模块导入参数。

    | ArkTS 导入名                    | 仓颉导入参数                                   | 说明                                         |
    |:-----------------------------|:-----------------------------------------|:-------------------------------------------|
    | @ohos.file.photoAccessHelper | ("file.photoAccessHelper")               | 以 @ohos 开头，那么参数只需要去掉 "@ohos."。             |
    | @hms.core.push.pushService   | ("core.push.pushService", prefix: "hms") | 以非 @ohos 开头，那么参数去掉 "@xxx."，并把 xxx 作为第二个参数。 |

4. 导入 ArkTS 模块。

    ```cangjie
    func tryLoadArkTSSo() {
        ...
        let module = context.requireSystemNativeModule("file.photoAccessHelper")
    }
    ```

模块导入进来是一个 JSValue，接下来可以按照操作 ArkTS 数据的方法去操作模块。

## 操作 ArkTS 数据

此章节介绍如何操作 JSValue，在上述两种场景中都涉及对 JSValue 的操作。
从 ArkTS 传过来的参数，其原始类型是`JSValue`，这是一个匿名类型的数据，首先需要知晓其类型。

* 通过 `JSValue.typeof()` 获取其类型枚举 `JSType`。
* 通过其他途径（包括但不限于阅读 ArkTS 源码、参考文档以及开发者口述）知晓其类型，然后通过类型校验接口来验证，比如判断是否是 number 类型 `JSValue.isNumber()`。

当知道其类型之后，再把 `JSValue` 转换为对应的仓颉类型或 ArkTS 引用。

* 转换为仓颉类型，比如一个 ArkTS string 转换为仓颉 String，`JSValue.toString(JSContext)`。
* 转换为 ArkTS 引用，比如一个 ArkTS string 转换为 JSString，`JSValue.asString(JSContext)`。

通过仓颉数据来构造 ArkTS 数据，是通过 JSContext 的方法类构造 ArkTS 数据。

一个应用进程可以存在多个 ArkTS 运行时，而 ArkTS 运行时之间的数据是不通用的，任何 ArkTS 数据都归属于一个特定的运行时，因此创建 ArkTS 数据接口是从运行时的角度出发。

以 `number` 为例，创建一个 `number` 的方式是 `JSContext.number(Float64)`。

ArkTS 主要数据类型对应到仓颉类型的映射如下：

| ArkTS 类型 | 仓颉类型    | 安全引用     | typeof 类型       |
|-----------|---------|-------------|------------------|
| undefined | -       | JSUndefined | JSType.UNDEFINED |
| null      | -       | JSNull      | JSType.NULL      |
| boolean   | Bool    | JSBoolean   | JSType.BOOL      |
| number    | Float64 | JSNumber    | JSType.NUMBER    |
| string    | String  | JSString    | JSType.STRING    |
| object    | -       | JSObject    | JSType.OBJECT    |
| Array     | -       | JSArray     | JSType.OBJECT    |
| bigint    | BigInt  | JSBigInt    | JSType.BIGINT    |
| function  | -       | JSFunction  | JSType.FUNCTION  |
| symbol    | -       | JSSymbol    | JSType.SYMBOL    |

安全引用的安全体现在两个方面：

* 类型安全，特定类型的接口只能从安全引用里访问，总是需要先做显式的类型转换再访问。
* 生命周期安全，对于由 ArkTS 来分配和回收的对象，安全引用能保障这些对象的生命周期。

### 操作 ArkTS 对象

从一个互操作函数的实现举例。

1. ArkTS 调用函数：

    ```typescript
    import {requireCJLib} from "libark_interop_loader.so"

    interface CustomObject {
        a: number;
        b: number;
    }

    interface CustomLib {
        // 定义的仓颉互操作函数，名称与仓颉侧注册名称一致。一般先定义 ArkTS 函数声明，在实现仓颉函数时根据声明来解析参数和返回。
        addByObject(args: CustomObject): number;
    }

    // 导入仓颉库，仓颉模块默认编译产物是 libentry.so，用户可以在 cjpm.toml 中修改配置。
    const cjLib = requireCJLib("libentry.so") as CustomLib;
    // 调用仓颉接口
    let result = cjLib.addByObject({a: 1, b: 2});
    console.log(`1 + 2 = ${result}`);
    ```

2. 仓颉函数实现：

    ```cangjie
    func addByObject(context: JSContext, callInfo: JSCallInfo): JSValue {
        // 获取首个参数
        let arg0 = callInfo[0]
        // 校验参数0是否是对象，否则返回undefined
        if (!arg0.isObject()) {
            return context.undefined().toJSValue()
        }
        // 把参数0转换为JSObject
        let obj = arg0.asObject(context)
        // 从JSObject获取属性
        let argA = obj["a"]
        let argB = obj["b"]
        // 把JSValue转换为Float64
        let a = argA.toNumber()
        let b = argB.toNumber()

        let result = a + b
        return context.number(result).toJSValue()
    }
    ```

除了可以从对象上读取属性外，还可以对属性赋值或创建新属性，操作方式为 `JSObject[key] = value`，其中 key 可以是仓颉 String 、JSString 或 JSSymbol，value 是 JSValue 。

> **说明：**
>
> 通过 `JSObject[key] = value` 定义属性时，该属性可写、可枚举、可配置。
> 更多参见 [JavaScript 标准内置对象](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object)。

对属性赋值在以下几种场景会失败，失败之后没有异常或日志：

1. 目标对象是 sealed 对象，由 `Object.seal()` 接口创建的对象具有不可修改的特性，无法创建新的属性和修改原有属性。
2. 目标属性的 writable 是 false ，由 `Object.defineProperty(object, key, {writable: false, value: xxx})` 定义属性时，可以指定属性是否可写。

对于一个未知对象，可以枚举出该对象的可枚举属性：

```cangjie
func handleUnknownObject(context: JSContext, target: JSObject): Unit {
    // 枚举对象的可枚举属性
    let keys = target.keys()
    println("target keys: ${keys}")
}
```

创建一个新的 ArkTS 对象，可以通过 `JSContext.object()` 来创建。

对于 ArkTS 运行时，有一个特殊的对象，该对象是 ArkTS 全局对象，在任何 ArkTS 代码里都可以直接访问该对象下的属性，在仓颉侧可以通过 `JSContext.global` 来访问它。

### 调用 ArkTS 函数

获取一个 ArkTS 函数后（通过参数传递，全局变量传递，从 ArkTS 数据集合里获取如从数组通过索引获取元素），可以在仓颉里直接调用。
该示例是先从 ArkTS 调用仓颉函数，然后在仓颉函数的实现里回调 ArkTS 函数。

1. ArkTS 调用仓颉：

    ```typescript
    import {requireCJLib} from "libark_interop_loader.so"

    interface CustomLib {
        addByCallback(a: number, b: number, callback: (result: number)=>void): void
    }

    // 导入仓颉库，仓颉模块默认编译产物是 libentry.so，用户可以在 cjpm.toml 中修改配置。
    const cjLib = requireCJLib("libentry.so") as CustomLib;

    // 调用仓颉接口
    cjLib.addByCallback(1, 2, (result) => {
        console.log(`1 + 2 = ${result}`);
    });

    ```

2. 仓颉代码中回调 ArkTS 函数：

    ```cangjie
    func addByCallback(context: JSContext, callInfo: JSCallInfo): JSValue {
        // 获取参数，并转换为Float64
        let a = callInfo[0].toNumber()
        let b = callInfo[1].toNumber()
        // 把第3个参数转换为JSFunction
        let callback = callInfo[2].asFunction(context)
        // 计算结果
        let result = a + b
        // 从仓颉Float64创建ArkTS number
        let retJSValue = context.number(result).toJSValue()
        // 调用回调函数
        callback.call(retJSValue)
    }
    ```

这个用例里的函数是不带 this 指针的，针对需要 this 指针的方法调用，可以通过命名参数 `thisArg` 来指定。

```cangjie
func doSth(context: JSContext, callInfo: JSCallInfo): JSValue {
    let callback = callInfo[0].asFunction(context)
    let thisArg = callInfo[1]

    callback.call(thisArg: thisArg)
}
```

在 ArkTS 代码里，可以通过 `对象.方法(...)` 来进行调用，这时会隐式传递 this 指针。

```typescript
class Someone {
    id: number = 0
    doSth(): void {
        console.log(`someone ${this.id} have done something`)
    }
}

let target = new Someone()

// 这里会隐式传递this指针，调用正常
target.doSth()

let doSth = target.doSth;
// 这里没有传递this指针，会出现异常`can't read property of undefined`
doSth.call()
```

在仓颉里，对应的写法如下：

```cangjie
func doSth(context: JSContext, callInfo: JSCallInfo): JSValue {
    let object = callInfo[0].asObject(context)
    // 会隐式传递this指针，调用正常
    object.callMethod("doSth")

    let doSth = object["doSth"].asFunction(context)
    // 未传递this指针，会出现异常`can't read property of undefined`
    doSth.call()
    // 显式传递this指针，调用正常
    doSth.call(thisArg: object.toJSValue())
}
```

## 在 ArkTS 里操作仓颉对象

此章节介绍使用互操作库，如何在 ArkTS 里操作仓颉的对象。

有以下三种方式：

1. 自定义函数：使用 ArkTS 运行时的内存管理机制来控制仓颉对象的生命周期，并通过相关的互操作接口来访问该对象。
2. JSExternal：将仓颉对象存入 JSExternal 中，并绑定在 JSObject 上，把 JSExternal 的数据隐藏起来，以此来提高接口的安全性。
3. JSClass：对于追求性能的场景，可以定义一个 JSClass 来加速对象创建和减小内存占用。

### 自定义函数

这里用例展示的是把仓颉对象分享到 ArkTS 运行时，使用 ArkTS 运行时的内存管理机制来控制仓颉对象的生命周期，并通过相关的互操作接口来访问该对象。

1. 定义仓颉函数：

    ```cangjie
    // 定义共享类
    class Data <: SharedObject {
        Data(
            // 定义2个属性
            var id: Int64,
            let name: String
        ) {}

        static init() {
            // 注册导出到ark的函数
            JSModule.registerFunc("createData", createData)
            JSModule.registerFunc("setDataId", setDataId)
            JSModule.registerFunc("getDataId", getDataId)
        }

        // 创建共享对象
        static func createData(context: JSContext, _: JSCallInfo): JSValue {
            // 创建仓颉对象
            let data = Data(1, "abc")
            // 创建js对仓颉对象的引用
            let jsExternal = context.external(data)
            // 返回js对仓颉对象的引用
            return jsExternal.toJSValue()
        }

        // 设置对象的id
        static func setDataId(context: JSContext, callInfo: JSCallInfo): JSValue {
            // 读取参数
            let arg0 = callInfo[0]
            let arg1 = callInfo[1]

            // 把参数0转换为js对仓颉对象的引用
            let jsExternal = arg0.asExternal(context)
            // 获取仓颉对象
            let data: Data = jsExternal.cast<Data>().getOrThrow()
            // 把参数1转换为Float64
            let value = arg1.toNumber()

            // 仓颉对象修改属性
            data.id = Int64(value)

            // 返回undefined
            let result = context.undefined().toJSValue()
            return result
        }

        // 获取对象的id
        static func getDataId(context: JSContext, callInfo: JSCallInfo): JSValue {
            let arg0 = callInfo[0]

            let jsExternal = arg0.asExternal(context)

            let data: Data = jsExternal.cast<Data>().getOrThrow()

            let result = context.number(Float64(data.id)).toJSValue()
            return result
        }
    }
    ```

2. ArkTS 调用仓颉函数：

    ```typescript
    import {requireCJLib} from "libark_interop_loader.so"
    // 定义导出符号
    interface CustomLib {
        createData(): undefined
        setDataId(data: undefined, value: number): void
        getDataId(data: undefined): number
    }

    // 加载自定义库
    const cjLib = requireCJLib("libentry.so") as CustomLib

    // 创建共享对象
    let data = cjLib.createData()
    // 操作对象属性
    cjLib.setDataId(data, 3)
    let id = cjLib.getDataId(data)

    console.log("id is " + id)
    ```

JSExternal 对象在 ArkTS 里的类型会被识别为 undefined，直接使用 undefined 来作为参数很容易被传递错误的参数会在运行时出错，如下示例：

```typescript
...
// 创建共享对象
let data = cjLib.createData()
// 操作对象属性
cjLib.setDataId(undefined, 3) // 错误的参数，应该传递的是仓颉引用，但是编译器能通过编译
let id = cjLib.getDataId(data)
...
```

### JSExternal

在实际开发接口时，可以把 JSExternal 对象绑定到一个 JSObject 对象上，把 JSExternal 的数据隐藏起来，以此来提高接口的安全性。

下面通过一个例子来展示：

```cangjie
// 定义共享类
class Data <: SharedObject {
    Data(
        // 定义2个属性
        var id: Int64,
        let name: String
    ) {}

    static init() {
        // 注册导出到ark的函数
        JSModule.registerFunc("createData", createData)
    }

    // 创建共享对象
    static func createData(context: JSContext, _: JSCallInfo): JSValue {
        let data = Data(1, "abc")
        let jsExternal = context.external(data)

        // 创建空JSObject
        let object = context.object()
        // 把js对仓颉对象的引用挂在JSObject的隐藏属性上
        object.attachCJObject(jsExternal)

        // 为js对象增加2个方法
        object["setId"] = context.function(setDataId).toJSValue()
        object["getId"] = context.function(getDataId).toJSValue()

        return object.toJSValue()
    }

    // 设置对象的id
    static func setDataId(context: JSContext, callInfo: JSCallInfo): JSValue {
        // 获取this指针
        let thisArg = callInfo.thisArg
        let arg0 = callInfo[0]

        // 把this指针转换为JSObject
        let thisObject = thisArg.asObject(context)
        // 从JSObject上获取隐藏属性
        let jsExternal = thisObject.getAttachInfo().getOrThrow()
        // 从js对仓颉对象的引用上获取仓颉对象
        let data = jsExternal.cast<Data>().getOrThrow()
        // 把参数0转换为Float64
        let value = arg0.toNumber()

        // 修改仓颉对象的属性
        data.id = Int64(value)

        let result = context.undefined()
        return result.toJSValue()
    }

    // 获取对象的id
    static func getDataId(context: JSContext, callInfo: JSCallInfo): JSValue {
        let thisArg = callInfo.thisArg
        let thisObject = thisArg.asObject(context)
        let jsExternal = thisObject.getAttachInfo().getOrThrow()
        let data = jsExternal.cast<Data>().getOrThrow()

        let result = context.number(Float64(data.id)).toJSValue()
        return result
    }
}
```

```typescript
import {requireCJLib} from "libark_interop_loader.so"
// 定义导出符号
interface Data {
    setId(value: number): void
    getId(): number
}

interface CustomLib {
    createData(): Data
}

// 加载自定义库
const cjLib = requireCJLib("libentry.so") as CustomLib

// 创建共享对象
let data = cjLib.createData()
// 操作对象属性
data.setId(3)
let id = data.getId()

console.log("id is " + id)
```

### JSClass

把所有的对象操作方法直接挂在对象上，一方面占用内存比较大，另一方面创建对象的开销比较大。对于追求性能的场景，可以定义一个 JSClass 来加速对象创建和减小内存占用。

```cangjie
// 定义共享类
class Data <: SharedObject {
    Data(
        // 定义2个属性
        var id: Int64,
        let name: String
    ) {}

    static init() {
        // 注册导出到ark的类
        JSModule.registerClass("Data") { context =>
            // 创建JSClass
            let clazz = context.clazz(jsConstructor)
            // 增加方法
            clazz.addMethod(context.string("setId"), context.function(setDataId))
            clazz.addMethod(context.string("getId"), context.function(getDataId))

            return clazz
        }
    }

    // js构造函数
    static func jsConstructor(context: JSContext, callInfo: JSCallInfo): JSValue {
        // 获取this指针
        let thisArg = callInfo.thisArg
        // 转换为JSObject
        let thisObject = thisArg.asObject(context)
        // 创建创建对象
        let data = Data(1, "abc")
        // 创建js对仓颉对象的引用
        let jsExternal = context.external(data)
        // 设置JSObject属性
        thisObject.attachCJObject(jsExternal)
        return thisObject.toJSValue()
    }

    // 设置对象的id
    static func setDataId(context: JSContext, callInfo: JSCallInfo): JSValue {
        // 获取this指针
        let thisArg = callInfo.thisArg
        // 把this指针转换为JSObject
        let thisObject = thisArg.asObject(context)
        // 从JSObject上获取隐藏属性
        let jsExternal = thisObject.getAttachInfo().getOrThrow()
        // 从js对仓颉对象的引用上获取仓颉对象
        let data = jsExternal.cast<Data>().getOrThrow()

        let arg0 = callInfo[0]
        // 把参数0转换为Float64
        let value = arg0.toNumber()

        // 修改仓颉对象的属性
        data.id = Int64(value)

        let result = context.undefined()
        return result.toJSValue()
    }

    // 获取对象的id
    static func getDataId(context: JSContext, callInfo: JSCallInfo): JSValue {
        let thisArg = callInfo.thisArg
        let thisObject = thisArg.asObject(context)
        let jsExternal = thisObject.getAttachInfo().getOrThrow()
        let data = jsExternal.cast<Data>().getOrThrow()

        let result = context.number(Float64(data.id)).toJSValue()
        return result
    }
}
```

```typescript
import {requireCJLib} from "libark_interop_loader.so"
// 定义Data的接口
interface Data {
    setId(value: number): void
    getId(): number
}

interface CustomLib {
    // 定义Data的构造函数（JSClass）
    Data: {new (): Data}
}

// 加载自定义库
const cjLib  = requireCJLib("libentry.so") as CustomLib

// 创建共享对象
let data = new cjLib.Data()
// 操作对象属性
data.setId(3)
let id = data.getId()

console.log("id is " + id)
```

## 仓颉多线程中使用互操作库

ArkTS 是单线程执行的虚拟机，在运行时上没有对并发做任何的容错；而仓颉在语法上支持内存共享的多线程。

如果在互操作的场景不加限制的使用多线程，可能会导致无法预期的错误，因此需要一些规范和指引来保证程序正常执行：

1. ArkTS 代码以及大部分互操作接口只能在 ArkTS 线程上执行，否则会抛出仓颉异常。
2. 在进入其他线程前，需要把所有依赖的 ArkTS 数据转换为仓颉数据。
3. 在其他线程如果想要使用 ArkTS 接口，需要通过 `context.postJSTask` 切换到 ArkTS 线程来执行。

下面通过一个用例来展示具体做法，该用例是互操作函数，该函数的功能是对两个数字相加，并调用回调来返回相加数。

```typescript
import {requireCJLib} from "libark_interop_loader.so"
// 定义导出的接口
interface CustomLib {
    addNumberAsync(a: number, b: number, callback: (result: number)=>void): void
}
// 导入仓颉库
const cjLib = requireCJLib("libentry.so") as CustomLib;
// 调用仓颉函数
cjLib.addNumberAsync(1, 2, (result)=> {
    console.log("1 + 2 = " + result)
})
```

```cangjie
// 类名没有影响
class Main {
    // 定义静态构造函数
    static init() {
        // 注册键值对
        JSModule.registerFunc("addNumberAsync", addNumberAsync)
    }
}

func addNumberAsync(context: JSContext, callInfo: JSCallInfo): JSValue {
    // 从JSCallInfo获取参数列表
    let arg0: JSValue = callInfo[0]
    let arg1: JSValue = callInfo[1]
    let arg2: JSValue = callInfo[2]
    // 把JSValue转换为仓颉类型
    let a: Float64 = arg0.toNumber()
    let b: Float64 = arg1.toNumber()
    let callback = arg2.asFunction(context)
    // 新建仓颉线程
    spawn {
        // 实际仓颉函数行为
        let value = a + b
        // 发起异步回调
        context.postJSTask {
            // 创建result
            let result = context.number(value).toJSValue()
            // 调用js回调
            callback.call(result)
        }
    }

    // 返回 void
    return context.undefined().toJSValue()
}
```

在 ArkTS 存在着 Promise，这是对回调机制的一种封装，配合 async 、 await 的语法让回调机制变成同步调用的形式。对于上一个用例，使用 Promise 的形式来定义接口和访问：

```cangjie
// 接口定义
func addNumberAsync(context: JSContext, callInfo: JSCallInfo): JSValue {
    // 参数转换为仓颉类型
    let a = callInfo[0].toNumber()
    let b = callInfo[1].toNumber()
    // 创建PromiseCapability对象
    let promise = context.promiseCapability()
    // 创建新线程
    spawn {
        // 在新线程执行仓颉逻辑
        let result = a + b
        // 切换到ArkTS线程
        context.postJSTask {
            // 在ArkTS线程执行resolve
            promise.resolve(context.number(result).toJSValue())
        }
    }
    // 返回Promise
    promise.toJSValue()
}
```

```typescript
// ArkTS 调用
import {requireCJLib} from "libark_interop_loader.so"
// 定义导出的接口
interface CustomLib {
    addNumberAsync(a: number, b: number): Promise<number>
}

async function call() {
    // 导入仓颉库
    const cjLib = requireCJLib("libentry.so") as CustomLib;
    // 调用仓颉函数
    let result = await cjLib.addNumberAsync(1, 2)
    console.log("1 + 2 = " + result)
}

call()
```

## 仓颉与 ArkTS 互操作场景辅助库

基于仓颉与 ArkTS 互操作库，同时还向开发者提供了辅助库，用于处理 ArkTS 与仓颉互操作业务。

在仓颉应用里使用 ArkTS 存量库场景中，当开发者想要调用的 ArkTS 模块中的接口需要传入一个 context 入参时，可以使用辅助库提供的 getJSContext 函数来获取。

例如，如下给出相机选择器 ArkTS 模块中的 pick 方法的声明，其第一个参数类型为 common.Context。

```typescript
declare namespace cameraPicker {
  // ...
  function pick(context: Context, mediaTypes: Array<PickerMediaType>, pickerProfile: PickerProfile): Promise<PickerResult>
}
```

针对这类互操作场景，互操作 helper 库提供了一个 getJSContext 接口，可以将 AbilityContext 类型的 context 转换为互操作可调用的 JSValue。

```cangjie
public func getJSContext(runtime: JSRuntime, abilityContext: AbilityContext): JSValue
```

用如下示例说明:

```cangjie
// AbilityContext 的全局实例
var globalAbilityContext: ?AbilityContext = None

class MainAbility <: Ability {
    ...
    public override func onCreate(want: Want, launchParam: LaunchParam): Unit {
        // 在 Ability 创建时保存 context 实例
        globalAbilityContext = context
    }
    ...
}
```

```cangjie
import ohos.ark_interop.*
import ohos.ark_interop_helper.*

var runtime = Option<JSRuntime>.None

// Get JSRuntime from the global variable.
func getRuntime() {
    return match (runtime) {
        case Some(v) => v
        case None =>
            let v = JSRuntime()
            runtime = v
            v
    }
}

// Get AbilityContext from the global varible which
// should initialized with the context property of Ability.
func getContext(): AbilityContext {
    match (globalAbilityContext) {
        case Some(context) =>
            context
        case _ =>
            AppLog.error("####getContext err ")
            throw Exception("get globalAbilityContext failed")
    }
}

// Get value of JSContext transformed from AbilityContext.
func getJSContextCase(): JSValue {
    let runtime = getRuntime()
    let abilityContext = getContext()
    getJSContext(runtime, abilityContext)
}
```
