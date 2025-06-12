# std.os.process 包

## 功能介绍

os.process 包主要提供 Process 进程操作接口，主要包括进程创建，标准流获取，进程等待，进程信息查询等。

本包提供多平台统一操控能力，目前支持 Linux 平台，macOS 平台，Windows 平台与 HarmonyOS 平台。

## API 列表

### 类

|  类名 | 功能  |
| ------------ | ------------ |
| [CurrentProcess](./os_process_package_api/os_process_package_classes.md#class-currentprocess) | 此类为当前进程类，继承 `Process` 类，提供对当前进程操作相关功能。 |
| [Process](./os_process_package_api/os_process_package_classes.md#class-process) | 此类为进程类，提供进程操作相关功能。 |
| [SubProcess](./os_process_package_api/os_process_package_classes.md#class-subprocess) | 此类为子进程类，继承 `Process` 类，提供对子进程操作相关功能。 |

### 枚举

| 枚举名 | 功能 |
| --------------------------- | ------------------------ |
| [ProcessRedirect](./os_process_package_api/os_process_package_enums.md#enum-processredirect) | 用于在创建进程时设置子进程标准流的重定向模式。 |

### 异常类

| 异常类名 | 功能 |
| --------------------------- | ------------------------ |
| [ProcessException](./os_process_package_api/os_process_package_exceptions.md#class-processexception) | `os.process` 包的异常类。 |

### 兼容性说明

#### class Process

| 成员 |  支持平台 |
| ------------ | ------------ |
| [current](./os_process_package_api/os_process_package_classes.md#prop-current) | Linux、Windows、macOS、HarmonyOS |
| [pid](./os_process_package_api/os_process_package_classes.md#prop-pid) | Linux、Windows、macOS、HarmonyOS |
| [name](./os_process_package_api/os_process_package_classes.md#prop-name) | Linux、Windows、macOS、HarmonyOS |
| [command](./os_process_package_api/os_process_package_classes.md#prop-command) | Linux、Windows、macOS、HarmonyOS |
| [arguments](./os_process_package_api/os_process_package_classes.md#prop-arguments) | Linux、macOS、HarmonyOS |
| [commandLine](./os_process_package_api/os_process_package_classes.md#prop-commandLine) | Linux、macOS、HarmonyOS |
| [workingDirectory](./os_process_package_api/os_process_package_classes.md#prop-workingDirectory) | Linux、macOS、HarmonyOS |
| [environment](./os_process_package_api/os_process_package_classes.md#prop-environment) | Linux、HarmonyOS |
| [of(Int64)](./os_process_package_api/os_process_package_classes.md#static-func-ofint64) | Linux、Windows、macOS、HarmonyOS |
| [start(String, Array<String>, Path, Map<String, String>, ProcessRedirect, ProcessRedirect, ProcessRedirect)](./os_process_package_api/os_process_package_classes.md#static-func-startstring-arraystring-path-mapstring-string-processredirect-processredirect-processredirect) | Linux、Windows、macOS、HarmonyOS |
| [run(String, Array<String>, Path, Map<String, String>, ProcessRedirect, ProcessRedirect, ProcessRedirect, Duration)](./os_process_package_api/os_process_package_classes.md#static-func-runstring-arraystring-path-mapstring-string-processredirect-processredirect-processredirect-duration) | Linux、Windows、macOS、HarmonyOS |
| [runOutput(String, Array<String>, Path, Map<String, String>, ProcessRedirect, ProcessRedirect, ProcessRedirect)](./os_process_package_api/os_process_package_classes.md#static-func-runoutputstring-arraystring-path-mapstring-string-processredirect-processredirect-processredirect) | Linux、Windows、macOS、HarmonyOS |
| [terminate(Bool)](./os_process_package_api/os_process_package_classes.md#func-terminatebool) | Linux、Windows、macOS、HarmonyOS |

#### class CurrentProcss

| 成员 |  支持平台 |
| ------------ | ------------ |
| [stdIn](./os_process_package_api/os_process_package_classes.md#prop-stdIn) | Linux、Windows、macOS、HarmonyOS |
| [stdOut](./os_process_package_api/os_process_package_classes.md#prop-stdOut) | Linux、Windows、macOS、HarmonyOS |
| [stdErr](./os_process_package_api/os_process_package_classes.md#prop-stdErr) | Linux、Windows、macOS、HarmonyOS |
| [atExit(() -> Unit)](./os_process_package_api/os_process_package_classes.md#func-atexit---unit) | Linux、Windows、macOS、HarmonyOS |
| [exit(Int64)](./os_process_package_api/os_process_package_classes.md#func-exitint64) | Linux、Windows、macOS、HarmonyOS |

#### class SubProcess

| 成员 |  支持平台 |
| ------------ | ------------ |
| [stdIn](./os_process_package_api/os_process_package_classes.md#prop-stdIn) | Linux、Windows、macOS、HarmonyOS |
| [stdOut](./os_process_package_api/os_process_package_classes.md#prop-stdOut) | Linux、Windows、macOS、HarmonyOS |
| [stdErr](./os_process_package_api/os_process_package_classes.md#prop-stdErr) | Linux、Windows、macOS、HarmonyOS |
| [wait(Duration)](./os_process_package_api/os_process_package_classes.md#func-waitduration) | Linux、Windows、macOS、HarmonyOS |
| [waitOutput()](./os_process_package_api/os_process_package_classes.md#func-waitoutput) | Linux、Windows、macOS、HarmonyOS |
