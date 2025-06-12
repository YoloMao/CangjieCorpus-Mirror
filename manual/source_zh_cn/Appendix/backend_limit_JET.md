# 后端限制与说明

## const 表达式

CJVM 后端由于实现限制暂不支持 `Array` 字面量的 const 表达式。

## VArray

CJVM 后端暂不支持 `VArray`。

## C 互操作

以 C 互操作[示例](../FFI/cangjie-c.md#示例)章节中的代码为例，CJVM 后端不需要 `-L .` 选项，编译命令如下：

```shell
cjc -l draw ./main.cj
```

CJVM 后端在编译时，`cjc` 编译器不会对 C 库中的符号进行解析，所有错误都发生在运行时。例如：

```shell
$ cjc main.cj    # 没有链接 libdraw.so
$ cj main.cbc    # 运行 cbc
An exception has occurred:
InternalError: AJIllegalStateException: Unsatisfied link: default.DrawPoint(unative)i32
         at default.$mainInvoke(<unknown>:0)
```

运行时发生链接错误，此时开发者应检查编译命令中是否包含了所有仓颉所需要的 C 库。

运行时 `cj` 还会根据操作系统 `LD_LIBRARY_PATH` 环境变量查找所需的 C 库，无法找到文件时会报错。例如：

```shell
$ cjc -l draw ./main.cj
$ cj main.cbc    # 缺少LD_LIBRARY_PATH
An exception has occurred:
InternalError: AJIOException: libpaint.so: cannot open shared object file: No such file or directory
         at default.$mainInvoke(<unknown>:0)
```

此时应检查 `LD_LIBRARY_PATH` 环境变量是否包含了所有所需 C 库的路径。
