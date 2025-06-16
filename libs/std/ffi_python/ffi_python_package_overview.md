# std.ffi.python 包

## 功能介绍

ffi.python 包提供仓颉与 Python 语言互操作调用的能力，以兼容强大的计算和 AI 生态。

本包为用户提供了以下能力：

1. Python 包为用户提供了全局解释器对象 `Python` ，其类型为 `PythonBuiltins` ，通过该解释器对象可以：

    - 加载、卸载解释器资源；
    - 获取当前使用的 Python 解释器版本；
    - 导入及使用 Python 的三方模块。

    详细介绍及使用请参见《仓颉编程语言开发指南》（跨语言互操作/与 Python 语言互操作/PythonBuiltins 内建函数类）。

2. Python 包提供了 Python 数据类型与仓颉类型之间的互相转换。如 PyBool/PyLong/PyFloat/PyString/PyTuple/PyList/PyDict/PySet, 它们均继承自 `PyObject` 类型，`PyObject` 类型提供了所有类型的通用接口，如成员变量访问、函数访问、到仓颉类型转换等。`PyObject` 类型的子类提供了每个类型独有的函数接口。

    详细映射关系介绍及使用请参见《仓颉编程语言开发指南》（跨语言互操作/与 Python 语言互操作/类型映射）。

3. Python 包支持简单的函数注册及 Python 对仓颉函数调用。Python 回调仓颉代码需要通过 C 作为中间层进行调用，并且使用到了 Python 的三方库： `ctypes` 以及 `_ctypes` 。

    详细映射关系介绍及使用请参见《仓颉编程语言开发指南》（跨语言互操作/与 Python 语言互操作/仓颉与 Python 的注册回调），该章节详细介绍了在回调过程中，两边参数和返回值的类型映射情况以及调用方式。

> **注意：**
>
> - 本包暂不支持 Windows 平台。

## API 列表

### 常量&变量

|               变量/常量名            |              功能              |
| ------------------------------ | ------------------------------ |
| [PYLOG](./ffi_python_package_api/ffi_python_package_constants_vars.md#let-pylog) | `ffi.python` 日志对象，用于打印控制及输出。 |
| [Python](./ffi_python_package_api/ffi_python_package_constants_vars.md#let-python) | Python 解释器全局资源。 |

### 接口

|               接口名            |              功能              |
| ------------------------------ | ------------------------------ |
| [CjObj](./ffi_python_package_api/ffi_python_package_interface.md#interface-cjobj) | 该接口提供将仓颉类型转换为 Python Object 的函数。 |
| [PyFFIType](./ffi_python_package_api/ffi_python_package_interface.md#interface-pyffitype) | 该接口表示支持与 Python 互操作的类型。 |

### 类

|               类型名            |              功能              |
| ------------------------------ | ------------------------------ |
| [PyBool](./ffi_python_package_api/ffi_python_package_classes.md#class-pybool) | 表示 Python 的布尔类型。 |
| [PyCFunc](./ffi_python_package_api/ffi_python_package_classes.md#class-pycfunc) | 表示 Python 的 C 风格函数类型。 |
| [PyDict\<K, V> where K <: Hashable & Equatable\<K> & PyFFIType](./ffi_python_package_api/ffi_python_package_classes.md#class-pydictk-v-where-k--hashable--equatablek--pyffitype) | 表示 Python 的字典类型。 |
| [PyFloat](./ffi_python_package_api/ffi_python_package_classes.md#class-pyfloat) | 表示 Python 的浮点数类型。 |
| [PyList\<T> where T <: PyFFIType](./ffi_python_package_api/ffi_python_package_classes.md#class-pylistt-where-t--pyffitype) | 表示 Python 的列表类型。 |
| [PyLong](./ffi_python_package_api/ffi_python_package_classes.md#class-pylong) | 表示 Python 的整数类型。 |
| [PyObj](./ffi_python_package_api/ffi_python_package_classes.md#class-pyobj) | 表示 Python 所有类型的父类。 |
| [PyObjIterator](./ffi_python_package_api/ffi_python_package_classes.md#class-pyobjiterator) | 表示 `PyObj` 的迭代器类型。 |
| [PyString](./ffi_python_package_api/ffi_python_package_classes.md#class-pystring) | 表示 Python 的字符串类型。 |
| [PySet\<T> where T <: Hashable & Equatable\<T> & PyFFIType](./ffi_python_package_api/ffi_python_package_classes.md#class-pysett-where-t--hashable--equatablet--pyffitype) | 表示 Python 的集合类型。 |
| [PySlice\<T> where T <: Countable\<T> & Comparable\<T> & Equatable\<T> & CjObj](./ffi_python_package_api/ffi_python_package_classes.md#class-pyslicet-where-t--countablet--comparablet--equatablet--cjobj) | 表示 Python 的区间类型。 |
| [PyTuple](./ffi_python_package_api/ffi_python_package_classes.md#class-pytuple) | 表示 Python 的元组类型。 |
| [PythonLogger](./ffi_python_package_api/ffi_python_package_classes.md#class-pythonlogger) | 表示 `ffi.python` 包的日志类型。 |
| [PythonBuiltins](./ffi_python_package_api/ffi_python_package_classes.md#class-pythonbuiltins) | 表示 Python 的内建函数集合。 |

### 异常类

|               类型名            |              功能              |
| ------------------------------ | ------------------------------ |
| [PythonException](./ffi_python_package_api/ffi_python_package_exception.md#class-pythonexception) | 表示来自 `ffi.python` 包的异常类型。 |
