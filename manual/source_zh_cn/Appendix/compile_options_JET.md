# `cjc` 编译选项

本章介绍常用的 `cjc` 编译选项。若某一选项同时适用于 `cjc-frontend`，则该选项会有 <sup>[frontend]</sup> 上标；若该选项在 `cjc-frontend` 下行为与 `cjc` 不同，选项会有额外说明。

- 两个横杠开头的选项为长选项，如 `--xxxx`。
  对于长选项，如果其后有参数，选项和参数之间既可以用空格隔开，也可以用等号连接，如 `--xxxx <value>` 与 `--xxxx=<value>` 等价。

- 一个横杠开头的选项为短选项，如 `-x`。
  对于短选项，如果其后有参数，选项和参数之间可以用空格隔开，也可以不隔开，如 `-x <value>` 与 `-x<value>` 等价。

## 基本选项

### `--output-type=[cbc|cbclib|staticlib]` <sup>[frontend]</sup>

指定输出文件的类型，`cbc` 模式下会生成 `.cbc` 文件，该文件用于在虚拟机执行；`cbclib` 模式下会生成 `.cbc` 库文件，该文件可以被虚拟机加载以用于执行其他 `cbc` 文件；`staticlib` 模式下会生成 `.bc` 文件，该文件为 CJVM 后端的静态库文件。
`cjc` 默认为 `cbc` 模式。

可以使用 `--output-type=cbclib` 将 `.cj` 代码编译为一个用于导入的库。假如有一个 `tool` 包，其源码文件为 `tool.cj`，可以使用以下命令编译：

```shell
$ cjc tool.cj --output-type=cbclib -o tool.cbc
```

cjc 在生成 `tool.cbc` 字节码文件的同时会生成 `tool.pdba` 符号信息文件，在编译导入了 `tool` 包的源码文件时，需要传入该符号信息文件，例如：

```shell
$ cjc main.cj tool.pdba -o main.cbc
```

可以通过使用 `cj` 工具来加载并执行 `main.cbc` 字节码文件。在运行时，还需要指定要导入的 `cbc` 文件所在的目录以使 `cj` 工具能够加载到导入库的字节码文件。例如：

```shell
$ cj --cbc-path . main.cbc
```

`cj` 会自动加载 `tool.cbc` 并开始执行 `main.cbc` 。

除了可以将 `.cj` 文件编译成字节码文件以外，也可以将其编译成静态库文件，例如使用

```shell
$ cjc tool.cj --output-type=staticlib
```

可以将 `tool.cj` 编译为静态库文件 ( `.bc` 文件)，此时 `cjc` 会生成文件 `tool.bc` 。

> 注：在一个工程中，导入的库文件仅能使用 `--output-type=cbclib` 或 `--output-type=staticlib` 其中一种形式，不支持两种形式混用。两种形式混用的场景下可能会造成预期外的运行时的问题。

<sup>[frontend]</sup> 在 `cjc-frontend` 中，编译流程仅进行至 `LLVM IR`，因此输出总是 `.bc` 文件，但是不同的 `--output-type` 类型仍会影响前端编译的策略。

### `--package`, `-p` <sup>[frontend]</sup>

编译包，使用此选项时需要指定一个目录作为输入，目录中的源码文件需要属于同一个包。

假如有文件 `log/printer.cj`：

```cangjie
package log

public func printLog(message: String) {
    println("[Log]: ${message}")
}
```

与文件 `main.cj`:

```cangjie
import log.*

main() {
    printLog("Everything is great")
}
```

可以使用

```shell
$ cjc -p log --output-type=staticlib
```

来编译 `log` 包，`cjc` 会在当前目录下生成一个 `log.bc` 文件。

然后可以使用 `log.bc` 文件来编译 `main.cj` ，编译命令如下：

```shell
$ cjc main.cj log.bc
```

`cjc` 会将 `main.cj` 与 `log.bc` 一同编译成一个可执行文件 `main` 。

> 如果 `main.cj` 依赖多个 `.bc` 文件，`.bc` 文件需要以依赖关系拓扑排序的逆序传给 `cjc` 。

### `--module-name <value>` <sup>[frontend]</sup>

指定要编译的模块的名字。

假如有文件 `my_module/src/log/printer.cj`：

```cangjie
package log

public func printLog(message: String) {
    println("[Log]: ${message}")
}
```

与文件 `main.cj`:

```cangjie
import my_module.log.*

main() {
    printLog("Everything is great")
}
```

可以使用

```shell
$ cjc -p my_module/src/log --module-name my_module --output-type=staticlib -o my_module/log.bc
```

来编译 `log` 包并指定其模块名为 `my_module`，`cjc` 会在 `my_module` 目录下生成一个 `my_module/log.bc` 文件。

然后可以使用 `log.bc` 文件来编译导入了 `log` 包的 `main.cj` ，编译命令如下：

```shell
$ cjc main.cj my_module/log.bc
```

`cjc` 会将 `main.cj` 与 `log.bc` 一同编译成一个可执行文件 `main` 。

### `--output <value>`, `-o <value>`, `-o<value>` <sup>[frontend]</sup>

指定输出文件的路径，编译器的输出将被写入指定的文件。

例如以下命令会将输出的可执行文件名字指定为 `a.out` 。

```shell
cjc main.cj -o a.out
```

在 `--output-type=cbc` 或 `--output-type=cbclib` 模式下， `--output` 指定的输出文件名必须有 `.cbc` 后缀名。

### `--library <value>`, `-l <value>`, `-l<value>`

指定要链接的动态库文件的文件名。

在 `--output-type=cbc` 或 `--output-type=cbclib` 模式下，该选项指定的库文件名会被记录在字节码中，使用 `cj` 工具执行字节码时虚拟机会通过 `LD_LIBRARY_PATH` 环境变量搜索并加载该动态库。

文件名的格式应为 `lib<value>.so`。

### `-g` <sup>[frontend]</sup>

生成带有调试信息的可执行文件或者是库文件。

### `--int-overflow=[throwing|wrapping|saturating]` <sup>[frontend]</sup>

指定固定精度整数运算的溢出策略，默认为溢出时抛出异常（ `throwing`）。

- 抛出异常（`throwing`）策略下整数运算溢出时，会抛出异常
- 高位截断（`wrapping`）策略下整数运算的结果超出用于接收它的内存空间所能表示的数据范围时，会截断超出该内存空间的部分
- 饱和（`saturating`）策略下整数运算溢出时，会选择对应固定精度的极值作为结果

### `--diagnostic-format=[default|noColor|json]` <sup>[frontend]</sup>

指定错误信息的输出格式，默认为 `default` 。

- `default` 错误信息默认格式输出（带颜色）
- `noColor` 错误信息默认格式输出（无颜色）
- `json` 错误信息`json`格式输出

### `--verbose`, `-V` <sup>[frontend]</sup>

`cjc` 会打印出编译器版本信息，工具链依赖的相关信息以及编译过程中执行的命令。

### `--help`, `-h` <sup>[frontend]</sup>

打印可用的编译选项。

使用此选项时编译器仅会打印编译选项相关信息，不会对任何输入文件进行编译。

### `--version`, `-v` <sup>[frontend]</sup>

打印编译器版本信息。

使用此选项时编译器仅会打印版本信息，不会对任何输入文件进行编译。

### `--save-temps <value>`

保留编译过程中生成的中间文件并保存至 `<value>` 路径下。

编译器会保留编译过程中生成的中间文件（例如 `.bc` 文件）。

### `--import-path <value>` <sup>[frontend]</sup>

指定导入模块的 AST 文件的搜索路径。

假如已经有以下目录结构，`libs/myModule` 目录中包含 `myModule` 模块的库文件和 `log` 包的 AST 导出文件，

```text
.
├── libs
|   └── myModule
|       ├── log.cjo
|       └── myModule.bc
└── main.cj
```

且有代码如下的 `main.cj` 文件，

```cangjie
import myModule.log.printLog

main() {
    printLog("Everything is great")
}
```

可以通过使用 `--import-path ./libs` 来将 `./libs` 加入导入模块的 AST 文件搜索路径，`cjc` 会使用 `./libs/myModule/log.cjo` 文件来对 `main.cj` 文件进行语义检查与编译。

`--import-path` 提供与 `CANGJIE_PATH` 环境变量相同的功能，但通过 `--import-path` 设置的路径拥有更高的优先级。

### `--scan-dependency` <sup>[frontend]</sup>

通过 `--scan-dependency` 指令可以获得指定包源码或者一个包的 `cjo` 文件对于其他包的直接依赖以及其他信息，以 `json` 格式输出。

```cangjie
// this file is placed under directory pkgA
macro package pkgA
import pkgB.*
import std.io.*
import pkgB.subB.*
```

```shell
cjc --scan-dependency --package pkgA
```

或

```shell
cjc --scan-dependency pkgA.cjo
```

```json
{
  "package": "pkgA",
  "isMacro": true,
  "dependencies": [
    {
      "package": "pkgB",
      "isStd": false,
      "imports": [
        {
          "file": "pkgA/pkgA.cj",
          "begin": {
            "line": 2,
            "column": 1
          },
          "end": {
            "line": 2,
            "column": 14
          }
        }
      ]
    },
    {
      "package": "pkgB.subB",
      "isStd": false,
      "imports": [
        {
          "file": "pkgA/pkgA.cj",
          "begin": {
            "line": 4,
            "column": 1
          },
          "end": {
            "line": 4,
            "column": 19
          }
        }
      ]
    },
    {
      "package": "std.io",
      "isStd": true,
      "imports": [
        {
          "file": "pkgA/pkgA.cj",
          "begin": {
            "line": 3,
            "column": 1
          },
          "end": {
            "line": 3,
            "column": 16
          }
        }
      ]
    }
  ]
}
```

### `--no-sub-pkg` <sup>[frontend]</sup>

表明当前编译包没有子包。

开启该选项后，编译器可以进一步缩减 code size 大小。

### `--warn-off`, `-Woff <value>` <sup>[frontend]</sup>

关闭编译期出现的全部或部分警告。

`<value>` 可以为 `all` 或者一个设定好的警告组别。当参数为 `all` 时，对于编译过程中生成的所有警告，编译器都不会打印；当参数为其他设定好的组别时，编译器将不会打印编译过程中生成的该组别警告。

在打印每个警告时，会有一行 `#note` 提示该警告属于什么组别并如何关闭它，可以通过 `--help` 打印所有可用的编译选项参数，来查阅具体的组别名称。

### `--warn-on`, `-Won <value>` <sup>[frontend]</sup>

开启编译期出现的全部或部分警告。

`--warn-on` 的 `<value>` 与 `--warn-off` 的 `<value>` 取值范围相同，`--warn-on` 通常与 `--warn-off` 组合使用；比如，可以通过设定 `-Woff all -Won <value>` 来仅允许组别为 `<value>` 的警告被打印。

**特别要注意的是**，`--warn-on` 与 `--warn-off` 在使用上顺序敏感；针对同一组别，后设定的选项会覆盖之前选项的设定，比如，调换上例中两个编译选项的位置，使其变为 `-Won <value> -Woff all`，其效果将变为关闭所有警告。

### `--error-count-limit <value>` <sup>[frontend]</sup>

限制编译器打印错误个数的上限。

参数 `<value>` 可以为 `all` 或一个非负整数。当参数为 `all` 时，编译器会打印编译过程中生成的所有错误；当参数为非负整数 `N` 时，编译器最多会打印 `N` 个错误。此选项默认值为 8。

### `--output-dir <value>` <sup>[frontend]</sup>

控制编译器生成的中间文件与最终文件的保存目录。

控制编译器生成的中间文件的保存目录，例如 `.cjo` 文件。当指定 `--output-dir <path1>` 时也指定了 `--output <path2>`，则中间文件会被保存至 `<path1>`，最终输出会被保存至 `<path1>/<path2>` 。

> **注意：**
>
> 同时指定此选项与 `--output` 选项时，`--output` 选项的参数必须是一个相对路径。

### `--disable-reflection`

关闭反射选项，即编译过程中不生成相关反射信息。

## 单元测试选项

### `--test` <sup>[frontend]</sup>

`unittest` 测试框架提供的入口，由宏自动生成，当使用 `cjc --test` 选项编译时，程序入口不再是 `main`，而是 `test_entry`。unittest 测试框架的使用方法请参见 《仓颉编程语言库 API》文档。

对于 `pkgc` 目录下仓颉文件 `a.cj`:

```cangjie
import std.unittest.*
import std.unittest.testmacro.*

@Test
public class TestA {
    @TestCase
    public func case1(): Unit {
        print("case1\n")
    }
}
```

可以在 `pkgc` 目录下使用：

```shell
cjc a.cj --test
```

来编译 `a.cj` ，执行 `cj main.cbc` 会有如下输出：

> **注意：**
>
> 不保证用例每次执行的用时都相同。

```cangjie
case1
--------------------------------------------------------------------------------------------------
TP: default, time elapsed: 29710 ns, Result:
    TCS: TestA, time elapsed: 26881 ns, RESULT:
    [ PASSED ] CASE: case1 (16747 ns)
Summary: TOTAL: 1
    PASSED: 1, SKIPPED: 0, ERROR: 0
    FAILED: 0
--------------------------------------------------------------------------------------------------
```

对于如下目录结构 :

```text
application
├── src
├── pkgc
|   ├── a1.cj
|   └── a2.cj
└── a3.cj
```

可以在 `application`目录下使用 `-p` 编译选项配合编译整包：

```shell
cjc pkgc --test -p
```

来编译整个 `pkgc` 包下的测试用例 `a1.cj` 和 `a2.cj`。

```cangjie
/*a1.cj*/
package a

import std.unittest.*
import std.unittest.testmacro.*

@Test
public class TestA {
    @TestCase
    public func caseA(): Unit {
        print("case1\n")
    }
}
```

```cangjie
/*a2.cj*/
package a

import std.unittest.*
import std.unittest.testmacro.*

@Test
public class TestB {
    @TestCase
    public func caseB(): Unit {
        throw IndexOutOfBoundsException()
    }
}
```

执行 `cj main.cbc` 会有如下输出（**输出信息仅供参考**）：

```cangjie
case1
--------------------------------------------------------------------------------------------------
TP: a, time elapsed: 367800 ns, Result:
    TCS: TestA, time elapsed: 16802 ns, RESULT:
    [ PASSED ] CASE: caseA (14490 ns)
    TCS: TestB, time elapsed: 347754 ns, RESULT:
    [ ERROR  ] CASE: caseB (345453 ns)
    REASON: An exception has occurred:IndexOutOfBoundsException
        at std/core.Exception::init()(std/core/exception.cj:23)
        at std/core.IndexOutOfBoundsException::init()(std/core/index_out_of_bounds_exception.cj:9)
        at a.TestB::caseB()(/home/houle/cjtest/application/pkgc/a2.cj:7)
        at a.lambda.1()(/home/houle/cjtest/application/pkgc/a2.cj:7)
        at std/unittest.TestCases::execute()(std/unittest/test_case.cj:92)
        at std/unittest.UT::run(std/unittest::UTestRunner)(std/unittest/test_runner.cj:194)
        at std/unittest.UTestRunner::doRun()(std/unittest/test_runner.cj:78)
        at std/unittest.UT::run(std/unittest::UTestRunner)(std/unittest/test_runner.cj:200)
        at std/unittest.UTestRunner::doRun()(std/unittest/test_runner.cj:78)
        at std/unittest.UT::run(std/unittest::UTestRunner)(std/unittest/test_runner.cj:200)
        at std/unittest.UTestRunner::doRun()(std/unittest/test_runner.cj:75)
        at std/unittest.entryMain(std/unittest::TestPackage)(std/unittest/entry_main.cj:11)
Summary: TOTAL: 2
    PASSED: 1, SKIPPED: 0, ERROR: 1
    FAILED: 0
--------------------------------------------------------------------------------------------------
```

### `--mock <on|off|runtime-error>` <sup>[frontend]</sup>

如果传递了 `on` ，则该包将使能 mock 编译，该选项允许在测试用例中 mock 该包中的类。`off` 是一种显式禁用 mock 的方法。

**值得注意的是**，在测试模式下（当使能 `--test` ）自动启用对此包的 mock 支持，不需要显式传递 `--mock` 选项。

`runtime-error` 仅在测试模式下可用（当使能 `--test` 时），它允许编译带有 mock 代码的包，但不在编译器中做任何 mock 相关的处理（这些处理可能会造成一些开销并影响测试的运行时性能）。这对于带有 mock 代码用例进行基准测试时可能是有用的。使用此编译选项时，避免编译带有 mock 代码的用例并运行测试，否则将抛出运行时异常。

## 宏选项

`cjc` 支持以下宏选项，关于宏的更多内容请参阅[宏](../Macro/macro_introduction.md)章节。

### `--compile-macro` <sup>[frontend]</sup>

编译宏定义文件，生成默认的宏定义动态库文件。

### `--debug-macro` <sup>[frontend]</sup>

生成宏展开后的仓颉代码文件。该选项可用于调试宏展开功能。

### `--parallel-macro-expansion` <sup>[frontend]</sup>

开启宏展开并行。该选项可用于缩短宏展开编译时间。

## 条件编译选项

`cjc` 支持以下条件编译选项，关于条件编译的更多内容请参阅[“条件编译”](../Compile-And-Build/conditional_compilation.md)。

### `--cfg <value>` <sup>[frontend]</sup>

指定自定义编译条件。

## 优化选项

### `-O<N>` <sup>[frontend]</sup>

使用参数指定的代码优化级别。

指定越高的优化级别，编译器会越多地进行代码优化以生成更高效的程序，同时也可能会需要更长的编译时间。

`cjc` 默认使用 O2 级别的代码优化。当前 `cjc` 支持如下优化级别：O1、O2。

> **注意：**
>
> `-O1`选项为实验性功能选项，必须配合 `--experimental` 选项一同使用。
> 当前 `-O1` 和 `-O2` 编译的程序混合使用时可能会出现未定义的编译报错，推荐对全局程序使用统一的编译选项，不要一部分库使用 `-O1` 优化等级编译，另一部分库使用 `-O2` 优化等级编译。

## 实验性功能选项

### `--experimental` <sup>[frontend]</sup>

启用实验性功能，允许在命令行使用其他实验性功能选项。

> **注意：**
>
> 使用实验性功能生成的字节码有可能会存在潜在的运行时问题，请注意使用该选项的风险。

## `cjc` 用到的环境变量

这里介绍一些仓颉编译器在编译代码的过程中可能使用到的环境变量。

### `TMPDIR` 或者 `TMP`

仓颉编译器会将编译过程中产生的临时文件放置到临时目录中。默认情况下 `Linux` 操作系统会放在 `/tmp` 目录下；`Windows` 操作系统会放在 `C:\Windows\Temp` 目录下。仓颉编译器也支持自行设置临时文件存放目录，`Linux` 操作系统上通过设置环境变量 `TMPDIR` 来更改临时文件目录，`Windows` 操作系统上通过设置环境变量 `TMP` 来更改临时文件目录。

例如：
在 Linux shell 中

```shell
export TMPDIR=/home/xxxx
```

在 Windows cmd 中

```shell
set TMP=D:\\xxxx
```

## `仓颉虚拟机` 环境变量使用手册

本章介绍 `仓颉虚拟机`所提供的环境变量。

在 Linux shell 中，您可以使用以下方式设置仓颉运行时提供的环境变量：

```shell
$ export JETVMPROP=value
```

目前仓颉虚拟机只提供 Linux shell 的设置方式，没有提供 Windows 的设置方式，

### 虚拟机初始化可选配置

仓颉虚拟机所有的选项都通过 JETVMPROP 来传入，并在运行时生效，传值时有可能会同时传入多条选项，这时可以通过添加引号`""`来支持传入多条选项。

#### `-Xmx`

指定仓颉堆的最大值，支持单位为 KB（K）、MB（M）、GB（G），支持设置范围为[128KB, 系统物理内存]，超出范围的设置无效，仍旧使用默认值。默认不限制堆大小，可以使用全部系统物理内存。

在设置变量选择单位时，写 K、M、G 即可，不需要写完整的 KB、MB、GB，下同。

例如：

```shell
$ export JETVMPROP=-Xmx512K
$ export JETVMPROP=-Xmx128M
$ export JETVMPROP=-Xmx16G
```

#### `-Djet.cj.use.fibers`

指定开启协程，目前仓颉虚拟机的线程实现默认是 OS 系统线程，使用该选项后会将线程实现切换到协程。

例如：

```shell
$ export JETVMPROP=-Djet.cj.use.fibers
```

#### `-Djet.fiber.stack.size`

指定开启协程后，指定协程栈的大小，支持设置范围是`[4KB, 128MB]`，默认值为 `128KB`，超出范围的设置无效，仍旧使用默认值。

例如：

```shell
$ export JETVMPROP="-Djet.cj.use.fibers -Djet.fiber.stack.size=256K"
```

#### `-Djet.fiber.carrier.count`

指定开启协程后，最多有多少 OS 系统线程被用来支持协程，输入只支持正整数，非法输入会报错。实际活跃的 OS 系统线程数可能小于这个值，配置时需要注意应用负载，如果设置过大有可能和机器上其他进程抢占 CPU 资源。默认值是系统核数的一半。

例如：

```shell
$ export JETVMPROP="-Djet.cj.use.fibers -Djet.fiber.carrier.count=5"
```

#### `-Djet.gc.ratio`

指定 GC 吞吐量，支持设置范围为`[0, 400]`，默认值为`11`，`gc.ratio / 10` 表示 GC 对 mutator 的时间占比，GC 在执行时会尽量分配 GC 时间以满足该设置，当`gc.ratio=0`时表示禁用该设置， GC 的触发时间由其他默认机制保证，当`gc.ratio`超过`400`时设置不生效，依旧使用默认值。

例如：

```shell
$ export JETVMPROP="-Djet.gc.ratio=11" // GC占总程序的时间为1.1%
$ export JETVMPROP="-Djet.gc.ratio=400" // GC占总程序的时间为40%
$ export JETVMPROP="-Djet.gc.ratio=500" // 设置不生效，使用默认值11
$ export JETVMPROP="-Djet.gc.ratio=0" // 禁用推定吞吐量，GC的触发时间由其他机制保证
```

#### `-Djet.heap.dump.on.oom`

开启内存溢出时自动导出堆内存。当主线程因`OutOfMemoryError`正常退出时，将会自动触发`cjmap -dump`，在`仓颉进程执行的目录`生成`jet.heap.dump.<data>.<timestamp>.PID-<pid>.hprof`文件。

**值得注意的是**，当因内存溢出触发运行时`Fatal error`时可能无法自动导出堆内存，因为此时运行时处于不可恢复的错误状态。

有关堆内存使用情况的详细信息，请参考[仓颉语言工具使用指南/命令行工具使用指南/仓颉堆内存查看工具使用指南](../../tools/source_zh_cn/tools/cjmap_manual_cjvm.md)章节。

例如：

```shell
$ export JETVMPROP="-Djet.heap.dump.on.oom"
$ cj main.cbc
An exception has occurred:
OutOfMemoryError
Start generating heap dump.
Finished generating heap dump
// 生成 jet.heap.dump.<data>.<timestamp>.PID-<pid>.hprof 文件。
```
