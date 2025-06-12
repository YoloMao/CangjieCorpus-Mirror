# 仓颉虚拟机环境变量使用手册

本章介绍 `仓颉虚拟机`所提供的环境变量。

在 Linux shell 中，您可以使用以下方式设置仓颉运行时提供的环境变量：

```shell
$ export JETVMPROP=value
```

目前仓颉虚拟机只提供 Linux shell 的设置方式，没有提供 Windows 的设置方式，

## 虚拟机初始化可选配置

仓颉虚拟机所有的选项都通过 JETVMPROP 来传入，并在运行时生效，传值时有可能会同时传入多条选项，这时可以通过添加引号`""`来支持传入多条选项。

### `-Xmx`

`堆（ heap ）` 是指仓颉进程特殊创建的一块内存，用来自动管理创建对象的分配、移动和回收。

`-Xmx` 选项可以指定仓颉堆允许使用的最大值，支持单位为 KB（K）、MB（M）、GB（G），支持设置范围为[4MB, 系统物理内存]，如果设置的值小于 `4MB` ，则会自动调整到 `4MB` 。在不设置 `-Xmx` 的情况下，默认不限制堆的最大值，可以使用全部系统物理内存。

在设置变量选择单位时，写 K、M、G 即可，不需要写完整的 KB、MB、GB，下同。

例如：

```shell
$ export JETVMPROP=-Xmx512K; cj hello.cbc
Warning: user defined heap limit 524288 was adjusted to 4194304
hello world!

$ export JETVMPROP=-Xmx128M // ok
$ export JETVMPROP=-Xmx16G  // ok
```

### `-Djet.cj.use.fibers`

指定开启协程，目前仓颉虚拟机的线程实现默认是 OS 系统线程，使用该选项后会将线程实现切换到协程。

例如：

```shell
$ export JETVMPROP=-Djet.cj.use.fibers
```

### `-Djet.fiber.stack.size`

指定开启协程后，指定协程栈的大小，支持设置范围是`[4KB, 128MB]`，默认值为 `128KB`，超出范围的设置无效，仍旧使用默认值。

例如：

```shell
$ export JETVMPROP="-Djet.cj.use.fibers -Djet.fiber.stack.size=256K"
```

### `-Djet.fiber.carrier.count`

指定开启协程后，最多有多少 OS 系统线程被用来支持协程，输入只支持正整数，非法输入会报错。实际活跃的 OS 系统线程数可能小于这个值，配置时需要注意应用负载，如果设置过大有可能和机器上其他进程抢占 CPU 资源。默认值是系统核数的一半。

例如：

```shell
$ export JETVMPROP="-Djet.cj.use.fibers -Djet.fiber.carrier.count=5"
```

### `-Djet.gc.ratio`

指定 GC 吞吐量，支持设置范围为`[0, 400]`，默认值为`11`，`gc.ratio / 10` 表示 GC 对 mutator 的时间占比，GC 在执行时会尽量分配 GC 时间以满足该设置，当`gc.ratio=0`时表示禁用该设置， GC 的触发时间由其他默认机制保证，当`gc.ratio`超过`400`时设置不生效，依旧使用默认值。

例如：

```shell
$ export JETVMPROP="-Djet.gc.ratio=11" // GC占总程序的时间为1.1%
$ export JETVMPROP="-Djet.gc.ratio=400" // GC占总程序的时间为40%
$ export JETVMPROP="-Djet.gc.ratio=500" // 设置不生效，使用默认值11
$ export JETVMPROP="-Djet.gc.ratio=0" // 禁用推定吞吐量，GC的触发时间由其他机制保证
```

### `-Djet.heap.dump.on.oom`

开启内存溢出时自动导出堆内存。当主线程因`OutOfMemoryError`正常退出时，将会自动触发`cjmap -dump`，在`仓颉进程执行的目录`生成`jet.heap.dump.<data>.<timestamp>.PID-<pid>.hprof`文件。

注意，当因内存溢出触发运行时`Fatal error`时可能无法自动导出堆内存，因为此时运行时处于不可恢复的错误状态。

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

### `-Djet.gc.brief.out.of.memory`

指定当虚拟机因内存溢出崩溃时，使用简洁报错信息。不开启选项时，内存溢出导致的进程崩溃将会生成包含堆转储信息的`jet_err_[pid]`文件。开启选项后，只会在控制台打印简洁的报错信息，格式与`OutOfMemory`异常一致。

例如：

```
$ cj main.cbc                                        // 因内存溢出导致崩溃
JET RUNTIME HAS DETECTED UNRECOVERABLE ERROR: out of memory
...
Please, contact the technical support.
Extra information about error is saved in the "jet_err_2921771.txt" file.

$ export JETVMPROP="-Djet.gc.brief.out.of.memory"    // 开启选项
$ cj main.cbc                                        // 因内存溢出导致崩溃
An exception has occurred:
OutOfMemoryError
```
