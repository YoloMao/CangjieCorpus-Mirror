# 类

## class ClassTypeInfo

```cangjie
public class ClassTypeInfo <: TypeInfo
```

功能：描述 `class` 类型的类型信息。

### prop constructors

```cangjie
public prop constructors: Collection<ConstructorInfo>
```

功能：获取该 `class` 类型信息所对应的 `class` 类型所拥有的所有公开构造函数的信息所组成的集合。

> **注意：**
>
> - 如果该 `class` 类型无任何公开构造函数，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[ConstructorInfo](reflect_package_classes_cjvm.md#class-constructorinfo)>

### prop instanceVariables

```cangjie
public prop instanceVariables: Collection<InstanceVariableInfo>
```

功能：获取该 [ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) 对应的 `class` 的所有公开实例成员变量信息，返回对应集合。

> **注意：**
>
> - 如果该 `class` 类型无任何公开实例成员变量，则返回空集合。
> - 该集合不保证遍历顺序恒定。
> - 该集合不包含任何继承而来的公开实例成员变量。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo)>

### prop staticVariables

```cangjie
public prop staticVariables: Collection<StaticVariableInfo>
```

功能：获取该 [ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) 对应的 `class` 的所有公开静态成员变量信息，返回对应集合。

> **注意：**
>
> - 如果该 `class` 类型无任何公开静态成员变量，则返回空集合。
> - 该集合不保证遍历顺序恒定。
> - 该集合不包含任何继承而来的公开静态成员变量。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo)>

### prop superClass

```cangjie
public prop superClass: Option<ClassTypeInfo>
```

功能：获取该 `class` 类型信息所对应的 `class` 类型的直接父类。

> **注意：**
>
> 理论上只有 class [Object](../../core/core_package_api/core_package_classes.md#class-object) 没有直接父类。

类型：[Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo)>

### func getConstructor(Array\<TypeInfo>)

```cangjie
public func getConstructor(parameterTypes: Array<TypeInfo>): ConstructorInfo
```

功能：尝试在该 [ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) 对应的 `class` 类型中获取与给定形参类型信息列表匹配的公开构造函数的信息。

参数：

- parameterTypes: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)> - 形参类型信息列表。

返回值：

- [ConstructorInfo](reflect_package_classes_cjvm.md#class-constructorinfo) - 如果成功匹配则返回该公开构造函数的信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应公开构造函数，则抛出异常。

### func getInstanceVariable(String)

```cangjie
public func getInstanceVariable(name: String): InstanceVariableInfo
```

功能：给定变量名称，尝试获取该 [ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) 所对应的 `class` 类型中匹配的实例成员变量的信息。

参数：

- name: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 变量名称。

返回值：

- [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) - 如果成功匹配则返回该实例成员变量的信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应实例成员变量，则抛出异常。

### func getStaticVariable(String)

```cangjie
public func getStaticVariable(name: String): StaticVariableInfo
```

功能：给定变量名称，尝试获取该 [ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) 所对应的 `class` 类型中匹配的静态成员变量的信息。

参数：

- name: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 变量名称。

返回值：

- [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) - 如果成功匹配则返回该静态成员变量的信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应静态成员变量，则抛出异常。

## class ConstructorInfo

```cangjie
public class ConstructorInfo <: Equatable<ConstructorInfo> & Hashable & ToString
```

功能：描述构造函数信息。

### prop annotations

```cangjie
public prop annotations: Collection<Annotation>
```

功能：获取所有作用于该 [ConstructorInfo](reflect_package_classes_cjvm.md#class-constructorinfo) 对应的构造函数的注解，返回对应集合。

> **注意：**
>
> - 如果无任何注解作用于该构造函数信息所对应的构造函数，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[Annotation](../../ast/ast_package_api/ast_package_classes.md#class-annotation)>

### prop parameters

```cangjie
public prop parameters: InfoList<ParameterInfo>
```

功能：获取该 [ConstructorInfo](reflect_package_classes_cjvm.md#class-constructorinfo) 对应的构造函数的形参类型列表。

类型：[InfoList](reflect_package_classes_cjvm.md#class-infolist)\<[ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo)>

### func findAnnotation\<T>() where T <: Annotation

```cangjie
public func findAnnotation<T>(): Option<T> where T <: Annotation
```

功能：尝试获取作用于该 [ConstructorInfo](reflect_package_classes_cjvm.md#class-constructorinfo) 对应的构造函数且拥有给定限定名称的注解。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 如果成功匹配则返回该注解，否则返回 `None`。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该构造器信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该构造器信息的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该构造函数信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该构造函数信息。

### operator func !=(ConstructorInfo)

```cangjie
public operator func !=(that: ConstructorInfo): Bool
```

功能：判断该构造器信息与给定的另一个构造器信息是否不等。

参数：

- that: [ConstructorInfo](reflect_package_classes_cjvm.md#class-constructorinfo) - 被比较相等性的另一个构造器信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该构造器信息与 `that` 不等则返回 `true`，否则返回 `false`。

### operator func ==(ConstructorInfo)

```cangjie
public operator func ==(that: ConstructorInfo): Bool
```

功能：判断该构造器信息与给定的另一个构造器信息是否相等。

参数：

- that: [ConstructorInfo](reflect_package_classes_cjvm.md#class-constructorinfo) - 被比较相等性的另一个构造器信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该构造器信息与 `that` 相等则返回 `true`，否则返回 `false`。

## class GlobalFunctionInfo

```cangjie
public class GlobalFunctionInfo <: Equatable<GlobalFunctionInfo> & Hashable & ToString
```

功能：描述全局函数信息。

### prop name

```cangjie
public prop name: String
```

功能：获取该 [GlobalFunctionInfo](reflect_package_classes_cjvm.md#class-globalfunctioninfo) 对应的全局函数的名称。

> **注意：**
>
> 构成重载的所有全局函数将拥有相同的名称。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop parameters

```cangjie
public prop parameters: InfoList<ParameterInfo>
```

功能：获取该 [GlobalFunctionInfo](reflect_package_classes_cjvm.md#class-globalfunctioninfo) 对应的全局函数的形参信息列表。

类型：[InfoList](reflect_package_classes_cjvm.md#class-infolist)\<[ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo)>

### prop returnType

```cangjie
public prop returnType: TypeInfo
```

功能：获取该 [GlobalFunctionInfo](reflect_package_classes_cjvm.md#class-globalfunctioninfo) 对应的全局函数的返回类型的类型信息。

类型：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该全局函数信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该全局函数信息的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该全局函数信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该全局函数信息。

### operator func ==(GlobalFunctionInfo)

```cangjie
public operator func ==(that: GlobalFunctionInfo): Bool
```

功能：判断该全局函数信息与给定的另一个全局函数信息是否相等。

参数：

- that: [GlobalFunctionInfo](reflect_package_classes_cjvm.md#class-globalfunctioninfo) - 被比较相等性的另一个全局函数信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该全局函数信息与 `that` 相等则返回 `true`，否则返回 `false`。

### operator func !=(GlobalFunctionInfo)

```cangjie
public operator func !=(that: GlobalFunctionInfo): Bool
```

功能：判断该全局函数信息与给定的另一个全局函数信息是否不等。

参数：

- that: [GlobalFunctionInfo](reflect_package_classes_cjvm.md#class-globalfunctioninfo) - 被比较相等性的另一个全局函数信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该全局函数信息与 `that` 不等则返回 `true`，否则返回 `false`。

## class GlobalVariableInfo

```cangjie
public class GlobalVariableInfo <: Equatable<GlobalVariableInfo> & Hashable & ToString
```

功能：描述全局变量信息。

### prop name

```cangjie
public prop name: String
```

功能：获取该 [GlobalVariableInfo](reflect_package_classes_cjvm.md#class-globalvariableinfo) 对应的全局变量的名称。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop typeInfo

```cangjie
public prop typeInfo: TypeInfo
```

功能：获取该 [GlobalVariableInfo](reflect_package_classes_cjvm.md#class-globalvariableinfo) 对应的全局变量的声明类型的类型信息。

类型：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)

### func getValue()

```cangjie
public func getValue(): Any
```

功能：获取该 [GlobalVariableInfo](reflect_package_classes_cjvm.md#class-globalvariableinfo) 对应的全局变量的值。

返回值：

- [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 该全局变量的值。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该全局变量信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该全局变量信息的哈希值。

### func setValue(Any)

```cangjie
public func setValue(newValue: Any): Unit
```

功能：设置该 [GlobalVariableInfo](reflect_package_classes_cjvm.md#class-globalvariableinfo) 对应的全局变量的值。

参数：

- newValue: [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 新的值。

异常：

- [IllegalSetException](reflect_package_exceptions_cjvm.md#class-illegalsetexception) - 如果该全局变量信息所对应的全局变量不可修改，则抛出异常。
- [IllegalTypeException](reflect_package_exceptions_cjvm.md#class-illegaltypeexception) - 如果新值 `newValue` 的运行时类型不是全局变量信息所对应的全局变量的声明类型的子类型，则抛出异常。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该全局变量信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该全局变量信息。

### operator func ==(GlobalVariableInfo)

```cangjie
public operator func ==(that: GlobalVariableInfo): Bool
```

功能：判断该全局变量信息与给定的另一个全局变量信息是否相等。

参数：

- that: [GlobalVariableInfo](reflect_package_classes_cjvm.md#class-globalvariableinfo) - 被比较相等性的另一个全局变量信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该全局变量信息与 `that` 相等则返回 `true`，否则返回 `false`。

### operator func !=(GlobalVariableInfo)

```cangjie
public operator func !=(that: GlobalVariableInfo): Bool
```

功能：判断该全局变量信息与给定的另一个全局变量信息是否不等。

参数：

- that: [GlobalVariableInfo](reflect_package_classes_cjvm.md#class-globalvariableinfo) - 被比较相等性的另一个全局变量信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该全局变量信息与 `that` 不等则返回 `true`，否则返回 `false`。

## class InfoList

```cangjie
public class InfoList<T> <: Collection<T>
```

功能：信息列表，用于保存只读的反射信息。

### prop size

```cangjie
public prop size: Int64
```

功能：获取该信息列表中的元素个数。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### func get(Int64)

```cangjie
public func get(index: Int64): ?T
```

功能：尝试获取该信息列表指定位置上的元素。

参数：

- index: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 位置索引。

返回值：

- ?T - 该信息列表指定位置上的元素。

### func isEmpty()

```cangjie
public func isEmpty(): Bool
```

功能：判断该信息列表是否为空。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该信息列表为空则返回 `true`，否则返回 `false`。

### func iterator()

```cangjie
public func iterator(): Iterator<T>
```

功能：获取该信息列表的迭代器。

返回值：

- [Iterator](../../core/core_package_api/core_package_classes.md#class-iteratort)\<T> - 该信息列表的迭代器。

### operator func []\(Int64)

```cangjie
public operator func [](index: Int64): T
```

功能：获取该信息列表指定位置上的元素。

参数：

- index: [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 位置索引。

返回值：

- T - 该信息列表指定位置上的元素。

异常：

- [IndexOutOfBoundsException](../../core/core_package_api/core_package_exceptions.md#class-indexoutofboundsexception) - 如果 `index` 超出索引范围，则抛出异常。

## class InstanceFunctionInfo

```cangjie
public class InstanceFunctionInfo <: Equatable<InstanceFunctionInfo> & Hashable & ToString
```

功能：描述实例成员函数信息。

### prop annotations

```cangjie
public prop annotations: Collection<Annotation>
```

功能：获取所有作用于该 [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) 对应的实例成员函数的注解，返回对应集合。

> **注意：**
>
> - 如果无任何注解作用于该实例成员函数信息所对应的实例成员函数，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[Annotation](../../ast/ast_package_api/ast_package_classes.md#class-annotation)>

### prop name

```cangjie
public prop name: String
```

功能：获取该 [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) 对应的实例成员函数的名称。

> **注意：**
>
> - 构成重载的所有实例成员函数将拥有相同的名称。
> - 操作符重载函数的名称就是该操作符本身的符号内容，如"`+`"，"`*`"，"`[]`"。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop parameters

```cangjie
public prop parameters: InfoList<ParameterInfo>
```

功能：获取该 [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) 对应的实例成员函数的形参信息列表。

类型：[InfoList](reflect_package_classes_cjvm.md#class-infolist)\<[ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo)>

### prop returnType

```cangjie
public prop returnType: TypeInfo
```

功能：获取该 [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) 对应的实例成员函数的返回值类型的类型信息。

类型：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)

### func findAnnotation\<T>() where T <: Annotation

```cangjie
public func findAnnotation<T>(): Option<T> where T <: Annotation
```

功能：尝试获取作用于该 [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) 对应的实例成员函数且拥有给定限定名称的注解。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 如果成功匹配则返回该注解，否则返回 `None`。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该实例成员函数信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该实例成员函数信息的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该实例成员函数信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该实例成员函数信息。

### operator func ==(InstanceFunctionInfo)

```cangjie
public operator func ==(that: InstanceFunctionInfo): Bool
```

功能：判断该实例成员函数信息与给定的另一个实例成员函数信息是否相等。

参数：

- that: [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) - 被比较相等性的另一个实例成员函数信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该实例成员函数信息与 `that` 相等则返回 `true`，否则返回 `false`。

### operator func !=(InstanceFunctionInfo)

```cangjie
public operator func !=(that: InstanceFunctionInfo): Bool
```

功能：判断该实例成员函数信息与给定的另一个实例成员函数信息是否不等。

参数：

- that: [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) - 被比较相等性的另一个实例成员函数信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该实例成员函数信息与 `that` 不等则返回 `true`，否则返回 `false`。

## class InstanceVariableInfo

```cangjie
public class InstanceVariableInfo <: Equatable<InstanceVariableInfo> & Hashable & ToString
```

功能：描述实例成员变量信息。

### prop annotations

```cangjie
public prop annotations: Collection<Annotation>
```

功能：获取所有作用于该 [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) 对应的实例成员变量的注解，返回对应集合。

> **注意：**
>
> - 如果无任何注解作用于该实例成员变量信息所对应的实例成员变量，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[Annotation](../../ast/ast_package_api/ast_package_classes.md#class-annotation)>

### prop name

```cangjie
public prop name: String
```

功能：获取该 [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) 对应的实例成员变量的名称。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop typeInfo

```cangjie
public prop typeInfo: TypeInfo
```

功能：获取该 [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) 对应的实例成员变量的声明类型的类型信息。

类型：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)

### func findAnnotation\<T>() where T <: Annotation

```cangjie
public func findAnnotation<T>(): Option<T> where T <: Annotation
```

功能：尝试获取作用于该 [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) 对应的实例成员变量且拥有给定限定名称的注解。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 如果成功匹配则返回该注解，否则返回 `None`。

### func getValue(Any)

```cangjie
public func getValue(instance: Any): Any
```

功能：获取该 [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) 对应的实例成员变量在给定实例中的值。

> **注意：**
>
> - 如果实例 `instance` 的运行时类型与该实例成员变量信息所对应的实例成员变量所属的类型不严格相同，则行为未定义。
> - 目前，实例 `instance` 不支持 `struct` 类型的实例。
> - 目前，返回值不支持为 `struct` 类型的实例。

参数：

- instance: [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 实例。

返回值：

- [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 该实例成员变量在实例 `instance` 中的值。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该实例成员变量信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该实例成员变量信息的哈希值。

### func setValue(Any, Any)

```cangjie
public func setValue(instance: Any, newValue: Any): Unit
```

功能：设置该 [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) 对应的实例成员变量在给定实例中的值。

> **注意：**
>
> - 如果实例 `instance` 的运行时类型与该实例成员变量信息所对应的实例成员变量所属的类型不严格相同，则行为未定义。
> - 目前，实例 `instance` 不支持 `struct` 类型的实例。

参数：

- instance: [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 实例。
- newValue: [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 新值。

异常：

- [IllegalSetException](reflect_package_exceptions_cjvm.md#class-illegalsetexception) - 如果该实例成员变量信息所对应的实例成员变量不可修改，则抛出异常。
- [IllegalTypeException](reflect_package_exceptions_cjvm.md#class-illegaltypeexception) - 如果新值 `newValue` 的运行时类型不是该实例成员变量信息所对应的实例成员变量的声明类型的子类型，则抛出异常。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该实例成员变量信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该实例成员变量信息。

### operator func ==(InstanceVariableInfo)

```cangjie
public operator func ==(that: InstanceVariableInfo): Bool
```

功能：判断该实例成员变量信息与给定的另一个实例成员变量信息是否相等。

参数：

- that: [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) - 被比较相等性的另一个实例成员变量信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该实例成员变量信息与 `that` 相等则返回 `true`，否则返回 `false`。

### operator func !=(InstanceVariableInfo)

```cangjie
public operator func !=(that: InstanceVariableInfo): Bool
```

功能：判断该实例成员变量信息与给定的另一个实例成员变量信息是否不等。

参数：

- that: [InstanceVariableInfo](reflect_package_classes_cjvm.md#class-instancevariableinfo) - 被比较相等性的另一个实例成员变量信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该实例成员变量信息与 `that` 不等则返回 `true`，否则返回 `false`。

## class InterfaceTypeInfo

```cangjie
public class InterfaceTypeInfo <: TypeInfo
```

功能：`interface` 类型的类型信息。

## class ModuleInfo

```cangjie
public class ModuleInfo <: Equatable<ModuleInfo> & Hashable & ToString
```

功能：描述模块信息，提供了仓颉动态模块加载、缓存能力以及模块内包信息查询能力。

仓颉动态模块是仓颉编译器生成的一种特殊二进制文件，这种文件可以被外部的仓颉程序在运行时被加载与使用。

> **注意：**
>
> 任一模块下不允许包含拥有相同限定名称的包。

### prop name

```cangjie
public prop name: String
```

功能：获取该 [ModuleInfo](reflect_package_classes_cjvm.md#class-moduleinfo) 对应的模块的名称。

> **注意：**
>
> - 模块的名称由被加载的模块的文件名决定，该文件名的格式为 `lib<module_name>_<package_name>(.<package_name>)*`。
> - `<module_name>` 和 `<package_name>` 均不允许为空。
> - 由于当前实现的局限性，`<module_name>` 中如果包含下划线 "`_`" 字符，可能出现非预期的加载错误。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop packages

```cangjie
public prop packages: Collection<PackageInfo>
```

功能：获取该模块中包含的所有包。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo)>

### prop version

```cangjie
public prop version: String
```

功能：获取该 [ModuleInfo](reflect_package_classes_cjvm.md#class-moduleinfo) 对应的模块的版本号。

> **注意：**
>
> 由于目前动态库中尚无版本信息，获取到的版本号总是 `1.0`。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### static func find(String)

```cangjie
public static func find(moduleName: String): Option<ModuleInfo>
```

功能：尝试在所有已加载的仓颉动态库模块中获取与给定模块名称匹配的模块的信息。

参数：

- moduleName: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 仓颉动态库模块名称。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<[ModuleInfo](reflect_package_classes_cjvm.md#class-moduleinfo)> - 如果匹配成功则返回该模块的信息，否则返回 `None`。

### static func load(String)

```cangjie
public static func load(path: String): ModuleInfo
```

功能：运行时动态加载指定路径下的一个仓颉动态库模块并获得该模块的信息。

> **注意：**
>
> - 为了提升兼容性，路径 `path` 中的共享库文件名不允许有后缀名 `.cbc` 。
> - 由于当前实现局限性，具有相同模块名称的动态库不能被同时加载，否则将抛出异常。如 `m/a`、`m/a.b`、`m/a.c` 这三个包所对应的共享库的加载是互斥的。

参数：

- path: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 共享库文件的绝对路径或相对路径。

异常：

- [ReflectException](reflect_package_exceptions_cjvm.md#class-reflectexception) - 如果共享库加载失败，则抛出异常。
- [UnsupportedException](../../core/core_package_api/core_package_exceptions.md#class-unsupportedexception) - 如果具有相同模块名称的共享库被重复加载，则抛出异常。

### func getPackageInfo(String)

```cangjie
public func getPackageInfo(packageName: String): PackageInfo
```

功能：尝试在该 [ModuleInfo](reflect_package_classes_cjvm.md#class-moduleinfo) 对应的模块中获取与给定包的名称或限定名称匹配的包的信息。

参数：

- packageName: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 包的名称或限定名称。

返回值：

- [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) - 如果匹配成功则返回该包的信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应包，则抛出异常。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该模块信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该模块信息的哈希值。

> **注意：**
>
> 内部实现为该模块信息的名称和版本号字符串的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该模块信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该模块信息。

> **注意：**
>
> 内容为该模块的名称和版本号。

### operator func !=(ModuleInfo)

```cangjie
public operator func !=(that: ModuleInfo): Bool
```

功能：判断该模块信息与给定的另一个模块信息是否不等。

参数：

- that: [ModuleInfo](reflect_package_classes_cjvm.md#class-moduleinfo) - 被比较相等性的另一个模块信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该模块信息与 `that` 不等则返回 `true`，否则返回 `false`。

### operator func ==(ModuleInfo)

```cangjie
public operator func ==(that: ModuleInfo): Bool
```

功能：判断该模块信息与给定的另一个模块信息是否相等。

参数：

- that: [ModuleInfo](reflect_package_classes_cjvm.md#class-moduleinfo) - 被比较相等性的另一个模块信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该模块信息与 `that` 相等则返回 `true`，否则返回 `false`。

## class PackageInfo

```cangjie
public class PackageInfo <: Equatable<PackageInfo> & Hashable & ToString
```

功能：描述包信息。

### prop functions

```cangjie
public prop functions: Collection<GlobalFunctionInfo>
```

功能：获取该 [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) 对应的包中所有公开全局函数的信息所组成的列表。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[GlobalFunctionInfo](reflect_package_classes_cjvm.md#class-globalfunctioninfo)>

### prop name

```cangjie
public prop name: String
```

功能：获取该包信息所对应的包的名称。

> **注意：**
>
> 包的名称不包含其所在的模块名称和其父包的名称，例如限定名称为 `a/b.c.d` 的包的名称是 `d` 。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop qualifiedName

```cangjie
public prop qualifiedName: String
```

功能：获取该 [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) 对应的包的限定名称。

> **注意：**
>
> 包的限定名称的格式是 `(module_name/)?(default|package_name)(.package_name)*`，例如限定名称为 `a/b.c.d` 的包位于模块 `a` 下的 `b` 包里的 `c` 包里。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop typeInfos

```cangjie
public prop typeInfos: Collection<TypeInfo>
```

功能：获取该 [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) 对应的包中所有全局定义的公开类型的类型信息，返回对应集合。

> **注意：**
>
> 目前该列表不包含所有反射尚未支持的类型。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)>

### prop variables

```cangjie
public prop variables: Collection<GlobalVariableInfo>
```

功能：获取该 [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) 对应的包中所有公开全局变量的信息所组成的列表。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[GlobalVariableInfo](reflect_package_classes_cjvm.md#class-globalvariableinfo)>

### func getFunction(String, Array\<TypeInfo>)

```cangjie
public func getFunction(name: String, parameterTypes: Array<TypeInfo>): GlobalFunctionInfo
```

功能：尝试在该 [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) 对应的包中获取拥有给定函数名称且与给定形参类型信息列表匹配的公开全局函数的信息。

参数：

- name: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 全局函数的名称。
- parameterTypes: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)> - 形参类型信息列表。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应全局定义的公开全局函数，则抛出异常。

### func getTypeInfo(String)

```cangjie
public func getTypeInfo(qualifiedName: String): TypeInfo
```

功能：尝试在该 [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) 对应的包中获取拥有给定类型名称的全局定义的公开类型的类型信息。

参数：

- qualifiedName: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 类型的限定名称

返回值：

- [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) - 如果成功匹配则返回该全局定义的公开类型的类型信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应全局定义的公开类型，则抛出异常。

### func getVariable(String)

```cangjie
public func getVariable(name: String): GlobalVariableInfo
```

功能：尝试在该 [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) 对应的包中获取拥有给定变量名称的公开全局变量的信息。

参数：

- name: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 全局变量的名称。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应全局定义的公开全局变量，则抛出异常。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该包信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该包信息的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该包信息。

> **注意：**
>
> 内部实现为该包信息的限定名称字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该包信息。

### operator func !=(PackageInfo)

```cangjie
public operator func !=(that: PackageInfo): Bool
```

功能：判断该包信息与给定的另一个包信息是否不等。

> **注意：**
>
> 内部实现为比较两个包信息的限定名称是否相等。

参数：

- that: [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) - 被比较相等性的另一个包信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该包信息与 `that` 不等则返回 `true`，否则返回 `false`。

### operator func ==(PackageInfo)

```cangjie
public operator func ==(that: PackageInfo): Bool
```

功能：判断该包信息与给定的另一个包信息是否相等。

> **注意：**
>
> 内部实现为比较两个包信息的限定名称是否相等。

参数：

- that: [PackageInfo](reflect_package_classes_cjvm.md#class-packageinfo) - 被比较相等性的另一个包信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该包信息与 `that` 相等则返回 `true`，否则返回 `false`。

## class ParameterInfo

```cangjie
public class ParameterInfo <: Equatable<ParameterInfo> & Hashable & ToString
```

功能：描述函数形参信息。

### prop annotations

```cangjie
public prop annotations: Collection<Annotation>
```

功能：获取所有作用于该 [ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo) 对应的函数形参的注解，返回对应集合。

> **注意：**
>
> - 如果无任何注解作用于该函数形参信息所对应的函数形参，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[Annotation](../../ast/ast_package_api/ast_package_classes.md#class-annotation)>

### prop index

```cangjie
public prop index: Int64
```

功能：获知该 [ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo) 对应的形参是其所在函数的第几个形参。

> **注意：**
>
> `index` 从0开始计数。

类型：[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)

### prop name

```cangjie
public prop name: String
```

功能：获取该 [ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo) 对应的形参的名称。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop typeInfo

```cangjie
public prop typeInfo: TypeInfo
```

功能：获取该 [ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo) 对应的函数形参的声明类型所对应的类型信息。

类型：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)

### func findAnnotation\<T>() where T <: Annotation

```cangjie
public func findAnnotation<T>(): Option<T> where T <: Annotation
```

功能：尝试获取作用于该 [ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo) 对应的函数形参且拥有给定限定名称的注解。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 如果成功匹配则返回该注解，否则返回 `None`。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该函数形参信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该函数形参信息的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该函数形参信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该函数形参信息。

### operator func !=(ParameterInfo)

```cangjie
public operator func !=(that: ParameterInfo): Bool
```

功能：判断该函数形参信息与给定的另一个函数形参信息是否不等。

参数：

- that: [ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo) - 被比较相等性的另一个函数形参信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该函数形参信息与 `that` 不等则返回 `true`，否则返回 `false`。

### operator func ==(ParameterInfo)

```cangjie
public operator func ==(that: ParameterInfo): Bool
```

功能：判断该函数形参信息与给定的另一个函数形参信息是否相等。

参数：

- that: [ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo) - 被比较相等性的另一个函数形参信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该函数形参信息与 `that` 相等则返回 `true`，否则返回 `false`。

## class PrimitiveTypeInfo

```cangjie
public class PrimitiveTypeInfo <: TypeInfo
```

功能：描述原始数据类型的类型信息。

原始数据类型包括无类型（`Nothing`）、单元类型（[Unit](../../core/core_package_api/core_package_intrinsics.md#unit)）、字符类型（`Rune`）、布尔类型（[Bool](../../core/core_package_api/core_package_intrinsics.md#bool)），整形类型（[Int8](../../core/core_package_api/core_package_intrinsics.md#int8)，[Int16](../../core/core_package_api/core_package_intrinsics.md#int16)，[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)，[Int64](../../core/core_package_api/core_package_intrinsics.md#int64)，[IntNative](../../core/core_package_api/core_package_intrinsics.md#intnative)，[UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8)，[UInt16](../../core/core_package_api/core_package_intrinsics.md#uint16)，[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)，[UInt64](../../core/core_package_api/core_package_intrinsics.md#uint64)，[UIntNative](../../core/core_package_api/core_package_intrinsics.md#uintnative)）和浮点类型（[Float16](../../core/core_package_api/core_package_intrinsics.md#float16)，[Float32](../../core/core_package_api/core_package_intrinsics.md#float32)，[Float64](../../core/core_package_api/core_package_intrinsics.md#float64)）。

> **注意：**
>
> 目前尚不支持 `Nothing` 和 [Unit](../../core/core_package_api/core_package_intrinsics.md#unit) 原始数据类型。

## class StaticFunctionInfo

```cangjie
public class StaticFunctionInfo <: Equatable<StaticFunctionInfo> & Hashable & ToString
```

功能：描述静态成员函数信息。

### prop annotations

```cangjie
public prop annotations: Collection<Annotation>
```

功能：获取所有作用于该 [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) 对应的静态成员函数的注解，返回对应集合。

> **注意：**
>
> - 如果无任何注解作用于该 [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) 对应的静态成员函数，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[Annotation](../../ast/ast_package_api/ast_package_classes.md#class-annotation)>

### prop name

```cangjie
public prop name: String
```

功能：获取该 [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) 对应的静态成员函数的名称。

> **注意：**
>
> 构成重载的所有静态成员函数将拥有相同的名称。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop parameters

```cangjie
public prop parameters: InfoList<ParameterInfo>
```

功能：获取该 [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) 对应的静态成员函数的形参信息列表。

类型：[InfoList](reflect_package_classes_cjvm.md#class-infolist)\<[ParameterInfo](reflect_package_classes_cjvm.md#class-parameterinfo)>

### prop returnType

```cangjie
public prop returnType: TypeInfo
```

功能：获取该 [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) 对应的静态成员函数的返回值类型的类型信息。

类型：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)

### func findAnnotation\<T>() where T <: Annotation

```cangjie
public func findAnnotation<T>(): Option<T> where T <: Annotation
```

功能：尝试获取作用于 [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) 对应的静态成员函数且拥有给定限定名称的注解。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 如果成功匹配则返回该注解，否则返回 `None`。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该静态成员函数信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该静态成员函数信息的哈希值。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该静态成员函数信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该静态成员函数信息。

### operator func !=(StaticFunctionInfo)

```cangjie
public operator func !=(that: StaticFunctionInfo): Bool
```

功能：判断该静态成员函数信息与给定的另一个静态成员函数信息是否不等。

参数：

- that: [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) - 被比较相等性的另一个静态成员函数信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该静态成员函数信息与 `that` 不等则返回 `true`，否则返回 `false`。

### operator func ==(StaticFunctionInfo)

```cangjie
public operator func ==(that: StaticFunctionInfo): Bool
```

功能：判断该静态成员函数信息与给定的另一个静态成员函数信息是否相等。

参数：

- that: [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) - 被比较相等性的另一个静态成员函数信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该静态成员函数信息与 `that` 相等则返回 `true`，否则返回 `false`。

## class StaticVariableInfo

```cangjie
public class StaticVariableInfo <: Equatable<StaticVariableInfo> & Hashable & ToString
```

功能：描述静态成员变量信息。

### prop annotations

```cangjie
public prop annotations: Collection<Annotation>
```

功能：获取所有作用于该 [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) 对应的静态成员变量的注解，返回对应集合。

> **注意：**
>
> - 如果无任何注解作用于该静态成员变量信息所对应的静态成员变量，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[Annotation](../../ast/ast_package_api/ast_package_classes.md#class-annotation)>

### prop name

```cangjie
public prop name: String
```

功能：获取该 [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) 对应的静态成员变量的名称。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop typeInfo

```cangjie
public prop typeInfo: TypeInfo
```

功能：获取该 [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) 对应的静态成员变量的声明类型的类型信息。

类型：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)

### func findAnnotation\<T>() where T <: Annotation

```cangjie
public func findAnnotation<T>(): Option<T> where T <: Annotation
```

功能：尝试获取作用于该 [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) 对应的静态成员变量且拥有给定限定名称的注解。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 如果成功匹配则返回该注解，否则返回 `None`。

### func getValue()

```cangjie
public func getValue(): Any
```

功能：获取该 [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) 对应的静态成员变量的值。

返回值：

- [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 该静态成员变量的值。

> **注意：**
>
> - 返回值不支持为 `struct` 类型。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该静态成员变量信息的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该静态成员变量信息的哈希值。

### func setValue(Any)

```cangjie
public func setValue(newValue: Any): Unit
```

功能：设置该 [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) 对应的静态成员变量的值。

参数：

- newValue: [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 新值。

异常：

- [IllegalSetException](reflect_package_exceptions_cjvm.md#class-illegalsetexception) - 如果该 [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) 对应的静态成员变量不可修改，则抛出异常。
- [IllegalTypeException](reflect_package_exceptions_cjvm.md#class-illegaltypeexception) - 如果新值 `newValue` 的运行时类型不是该静态成员变量信息所对应的静态成员变量的声明类型的子类型，则抛出异常。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该静态成员变量信息。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该静态成员变量信息。

### operator func !=(StaticVariableInfo)

```cangjie
public operator func !=(that: StaticVariableInfo): Bool
```

功能：判断该静态成员变量信息与给定的另一个静态成员变量信息是否不等。

参数：

- that: [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) - 被比较相等性的另一个静态成员变量信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该静态成员变量信息与 `that` 不等则返回 `true`，否则返回 `false`。

### operator func ==(StaticVariableInfo)

```cangjie
public operator func ==(that: StaticVariableInfo): Bool
```

功能：判断该静态成员变量信息与给定的另一个静态成员变量信息是否相等。

参数：

- that: [StaticVariableInfo](reflect_package_classes_cjvm.md#class-staticvariableinfo) - 被比较相等性的另一个静态成员变量信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该静态成员变量信息与 `that` 相等则返回 `true`，否则返回 `false`。

## class TypeInfo

```cangjie
sealed abstract class TypeInfo <: Equatable<TypeInfo> & Hashable & ToString
```

功能：[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 提供了所有数据类型通用的操作接口。开发者通常无需向下转型为更具体的数据类型，如 [ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) 等，就能进行反射操作。

[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 的子类包括 [PrimitiveTypeInfo](reflect_package_classes_cjvm.md#class-primitivetypeinfo)、[ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) 和 [InterfaceTypeInfo](reflect_package_classes_cjvm.md#class-interfacetypeinfo)，分别对应基本数据类型，`class` 数据类型和 `interface` 数据类型的类型信息。

> **说明**
>
> 类型的限定名称为`(module_name/)?(default|package_name)(.package_name)*.(type_name)`。

### prop annotations

```cangjie
public prop annotations: Collection<Annotation>
```

功能：获取所有作用于该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型的注解，返回对应集合。

> **注意：**
>
> - 如果无任何注解作用于该类型信息所对应的类型，则返回空集合。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[Annotation](../../ast/ast_package_api/ast_package_classes.md#class-annotation)>

### prop instanceFunctions

```cangjie
public prop instanceFunctions: Collection<InstanceFunctionInfo>
```

功能：获取该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应类型的所有公开实例成员函数信息，返回对应集合。

> **注意：**
>
> - 如果该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型无任何公开实例成员函数，则返回空集合。
> - 该集合不保证遍历顺序恒定。
> - 如果该类型信息所对应的类型是 `class` 类型，则该集合包含从其他 `interface` 类型继承而来的非抽象的实例成员函数的信息。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo)>

### prop instanceProperties

```cangjie
public prop instanceProperties: Collection<InstancePropertyInfo>
```

功能：获取该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应类型的所有公开实例成员属性信息，返回对应集合。

> **注意：**
>
> - 如果该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型无任何公开实例成员属性，则返回空集合。
> - 该集合不保证遍历顺序恒定。
> - 如果该类型信息所对应的类型是 `struct` 或 `class` 类型，则该集合包含从其他 `interface` 类型继承而来的非抽象的实例成员属性的信息。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[InstancePropertyInfo](reflect_package_classes_cjvm.md#class-instancepropertyinfo)>

### prop name

```cangjie
public prop name: String
```

功能：获取该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型的名称。

> **注意：**
>
> - 该名称不包含任何模块名和包名前缀。
> - 类型别名的类型信息就是实际类型其本身的类型信息，所以该函数并不会返回类型别名本身的名称而是实际类型的名称，如类型别名 [Byte](../../core/core_package_api/core_package_types.md#type-byte) 的类型信息的名称是 [UInt8](../../core/core_package_api/core_package_intrinsics.md#uint8) 而不是 [Byte](../../core/core_package_api/core_package_types.md#type-byte)。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop qualifiedName

```cangjie
public prop qualifiedName: String
```

功能：获取该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型的限定名称。

> **注意：**
>
> - 限定名称包含模块名和包名前缀。
> - 特别的，仓颉内置数据类型，以及位于 `std` 模块 `core` 包下的所有类型的限定名称都是不带有任何模块名和包名前缀的。
> - 在缺省模块名和包名的上下文中定义的所有类型，均无模块名前缀，但拥有包名前缀"`default`"，如："`default.MyType`"。

类型：[String](../../core/core_package_api/core_package_structs.md#struct-string)

### prop staticFunctions

```cangjie
public prop staticFunctions: Collection<StaticFunctionInfo>
```

功能：获取该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应类型的所有公开静态成员函数信息，返回对应集合。

> **注意：**
>
> - 如果该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型无任何公开静态成员函数，则返回空集合。
> - 该集合不保证遍历顺序恒定。
> - 如果该类型信息所对应的类型是 `class` 或 `interface` 类型，则该集合包含从其他 `interface` 类型继承而来的非抽象的静态成员函数的信息。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo)>

### prop staticProperties

```cangjie
public prop staticProperties: Collection<StaticPropertyInfo>
```

功能：获取该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应类型的所有公开静态成员属性信息，返回对应集合。

> **注意：**
>
> - 如果该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型无任何公开静态成员属性，则返回空集合。
> - 该集合不保证遍历顺序恒定。
> - 如果该类型信息所对应的类型是 `struct` 、`class` 或 `interface` 类型，则该集合包含从其他 `interface` 类型继承而来的非抽象的静态成员属性的信息。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[StaticPropertyInfo](reflect_package_classes_cjvm.md#class-staticpropertyinfo)>

### prop superInterfaces

```cangjie
public prop superInterfaces: Collection<InterfaceTypeInfo>
```

功能：获取该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型直接实现的所有 `interface` 类型的信息，返回对应集合。

> **注意：**
>
> - 所有类型均默认直接实现 interface [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) 类型。
> - 该集合不保证遍历顺序恒定。

类型：[Collection](../../core/core_package_api/core_package_interfaces.md#interface-collectiont)\<[InterfaceTypeInfo](reflect_package_classes_cjvm.md#class-interfacetypeinfo)>

### static func get(String)

```cangjie
public static func get(qualifiedName: String): TypeInfo
```

功能：获取给定的类型的限定名称所对应的类型的类型信息。

类型的限定名称为`(module_name/)?(default|package_name)(.package_name)*.(type_name)`。

> **注意：**
>
> - 未实例化的泛型类型的类型信息无法被获取。
> - 目前， 类型的限定名称 `qualifiedName` 不支持 `Nothing` 类型、函数类型、元组类型、`enum` 类型和带有泛型的 `struct` 类型的限定名称。

参数：

- qualifiedName: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 类型的限定名称。

返回值：

- [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) - 类型的限定名称 `qualifiedName` 所对应的类型的类型信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果无法获取与给定类型的限定名称 `qualifiedName` 匹配的类型所对应的类型信息，则抛出异常。

### static func of(Any)

```cangjie
public static func of(a: Any): TypeInfo
```

功能：获取给定的任意类型的实例的运行时类型所对应的类型信息。

运行时类型是指在程序运行时，通过动态绑定确定的类型，运行时类型与实例对象相绑定。在继承等场景下运行时类型和静态类型可能不一致。

> **注意：**
>
> 目前，实例 `a` 不支持运行时类型为函数类型，元组类型，`enum` 类型和带有泛型的 `struct` 类型的实例。

参数：

- a: [Any](../../core/core_package_api/core_package_interfaces.md#interface-any) - 实例。

返回值：

- [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) - 实例 `a` 的运行时类型所对应的类型信息。

### static func of(Object)

```cangjie
public static func of(a: Object): ClassTypeInfo
```

功能：获取给定的 `class` 类型的实例的运行时类型所对应的 `class` 类型信息。

参数：

- a: [Object](../../core/core_package_api/core_package_classes.md#class-object) - `class` 类型的实例。

返回值：

- [ClassTypeInfo](reflect_package_classes_cjvm.md#class-classtypeinfo) - `class` 类型的实例 `a` 的运行时类型所对应的 `class` 类型信息。

### static func of\<T>()

```cangjie
public static func of<T>(): TypeInfo
```

功能：获取给定类型对应的类型信息。

> **注意：**
>
> - `T` 可以是当前所在包中的全局定义的公开的类型。
> - `T` 可以是导入的包中的全局定义的公开的类型。
> - `T` 支持传入类型别名，包括内置类型别名（如 [Int](../../core/core_package_api/core_package_types.md#type-int)、[UInt](../../core/core_package_api/core_package_types.md#type-uint) 和 `Rune` 等）与用户自定义类型别名。
> - 目前，`T` 不支持 `Nothing` 类型、[Unit](../../core/core_package_api/core_package_intrinsics.md#unit) 类型、函数类型，元组类型，`enum` 类型和 `struct` 类型。
> - 目前，如果无法获得类型 `T` 所对应的类型信息，将产生未定义行为。

返回值：

- [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) - `T` 类型对应的类型信息。

### func findAnnotation\<T>() where T <: Annotation

```cangjie
public func findAnnotation<T>(): Option<T> where T <: Annotation
```

功能：尝试获取作用于该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型且拥有给定限定名称的注解。

返回值：

- [Option](../../core/core_package_api/core_package_enums.md#enum-optiont)\<T> - 如果成功匹配则返回该注解，否则返回 `None`。

### func getInstanceFunction(String, Array\<TypeInfo>)

```cangjie
public func getInstanceFunction(name: String, parameterTypes: Array<TypeInfo>): InstanceFunctionInfo
```

功能：给定函数名称与函数形参类型列表所对应的类型信息列表，尝试获取该类型中匹配的实例成员函数的信息。

参数：

- name: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 函数名称。
- parameterTypes: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)> - 函数形参类型列表所对应的类型信息列表。

返回值：

- [InstanceFunctionInfo](reflect_package_classes_cjvm.md#class-instancefunctioninfo) - 如果成功匹配则返回该实例成员函数的信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应公开实例成员函数，则抛出异常。

### func getStaticFunction(String, Array\<TypeInfo>)

```cangjie
public func getStaticFunction(name: String, parameterTypes: Array<TypeInfo>): StaticFunctionInfo
```

功能：通过给定函数名称与函数形参类型列表所对应的类型信息列表，尝试获取该类型中匹配的静态成员函数的信息。

参数：

- name: [String](../../core/core_package_api/core_package_structs.md#struct-string) - 函数名称。
- parameterTypes: [Array](../../core/core_package_api/core_package_structs.md#struct-arrayt)\<[TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo)> - 函数形参类型列表所对应的类型信息列表。

返回值：

- [StaticFunctionInfo](reflect_package_classes_cjvm.md#class-staticfunctioninfo) - 如果成功匹配则返回该静态成员函数的信息。

异常：

- [InfoNotFoundException](reflect_package_exceptions_cjvm.md#class-infonotfoundexception) - 如果没找到对应公开静态成员函数，则抛出异常。

### func hashCode()

```cangjie
public func hashCode(): Int64
```

功能：获取该类型信息的哈希值。

> **注意：**
>
> 内部实现为该类型信息的限定名称字符串的哈希值。

返回值：

- [Int64](../../core/core_package_api/core_package_intrinsics.md#int64) - 该类型信息的哈希值。

### func isSubtypeOf(TypeInfo)

```cangjie
public func isSubtypeOf(supertype: TypeInfo): Bool
```

功能：判断当前 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 实例对应的类型是否是参数中指定的 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 实例表示的类型的子类型。

参数：

- supertype: [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) - 目标类型的类型信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该 [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) 对应的类型是 `supertype` 所对应的类型的子类型则返回 `true`，否则返回 `false`。

### func toString()

```cangjie
public func toString(): String
```

功能：获取字符串形式的该类型信息。

> **注意：**
>
> 内部实现为该类型信息的限定名称字符串。

返回值：

- [String](../../core/core_package_api/core_package_structs.md#struct-string) - 字符串形式的该类型信息。

### operator func !=(TypeInfo)

```cangjie
public operator func !=(that: TypeInfo): Bool
```

功能：判断该类型信息与给定的另一个类型信息是否不等。

参数：

- that: [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) - 被比较相等性的另一个类型信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该类型信息的限定名称与 `that` 不等则返回 `true`，否则返回 `false`。

### operator func ==(TypeInfo)

```cangjie
public operator func ==(that: TypeInfo): Bool
```

功能：判断该类型信息与给定的另一个类型信息是否相等。

参数：

- that: [TypeInfo](reflect_package_classes_cjvm.md#class-typeinfo) - 被比较相等性的另一个类型信息。

返回值：

- [Bool](../../core/core_package_api/core_package_intrinsics.md#bool) - 如果该类型信息的限定名称与 `that` 相等则返回 `true`，否则返回 `false`。
