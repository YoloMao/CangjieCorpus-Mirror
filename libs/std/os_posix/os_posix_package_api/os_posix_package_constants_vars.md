# 常量&变量

## const AT_EMPTY_PATH

```cangjie
public const AT_EMPTY_PATH: Int32
```

功能：表示在文件系统中空路径（即没有指定任何文件或目录）时返回的文件描述符，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const AT_REMOVEDIR

```cangjie
public const AT_REMOVEDIR: Int32
```

功能：如果指定了 [AT_REMOVEDIR](os_posix_package_constants_vars.md#const-at_removedir) 标志，则对 `pathname` 执行等效于 `rmdir(2)` 的操作，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const F_OK

```cangjie
public const F_OK: Int32
```

功能：测试文件是否存在，适用函数 [access](os_posix_package_funcs.md#func-accessstring-int32)，[faccessat](os_posix_package_funcs.md#func-faccessatint32-string-int32-int32)，所属函数参数 `mode`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_APPEND

```cangjie
public const O_APPEND: Int32
```

功能：读取或写入文件时，数据将从文件末尾移动。即写入的数据将附加到文件的末尾，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_CLOEXEC

```cangjie
public const O_CLOEXEC: Int32
```

功能：在某些多线程程序中，使用此标志是必不可少的。因为在一个线程同时打开文件描述符，而另一个线程执行 `fork(2)` 加 `execve(2)` 场景下使用单独的 `fcntl(2)` `F_SETFD` 操作设置 `FD_CLOEXEC` 标志并不足以避免竞争条件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_CREAT

```cangjie
public const O_CREAT: Int32
```

功能：如果要打开的文件不存在，则自动创建该文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_DIRECTORY

```cangjie
public const O_DIRECTORY: Int32
```

功能：如果 `pathname` 指定的文件不是目录，则打开文件失败，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_DSYNC

```cangjie
public const O_DSYNC: Int32
```

功能：每次写入都会等待物理 `I/O` 完成，但如果写操作不影响读取刚写入的数据，则不等待文件属性更新，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_EXCL

```cangjie
public const O_EXCL: Int32
```

功能：如同时设置 [O_CREAT](os_posix_package_constants_vars.md#const-o_creat)，则此指令检查文件是否存在。如果文件不存在，则创建文件。否则，打开文件出错。此外，如果同时设置了 [O_CREAT](os_posix_package_constants_vars.md#const-o_creat) 和 [O_EXCL](os_posix_package_constants_vars.md#const-o_excl)，并且要打开的文件是符号链接，则打开文件失败，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_NOCTTY

```cangjie
public const O_NOCTTY: Int32
```

功能：如要打开的文件是终端设备，则该文件不会成为这个进程的控制终端，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_NOFOLLOW

```cangjie
public const O_NOFOLLOW: Int32
```

功能：如 `pathname` 指定的文件是单符号连接，则打开文件失败，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_NONBLOCK

```cangjie
public const O_NONBLOCK: Int32
```

功能：以非阻塞的方式打开文件，即 `I/O` 操作不会导致调用进程等待，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_RDONLY

```cangjie
public const O_RDONLY: Int32
```

功能：以只读方式打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_RDWR

```cangjie
public const O_RDWR: Int32
```

功能：以读写模式打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_RSYNC

```cangjie
public const O_RSYNC: Int32
```

功能：此标志仅影响读取操作，必须与 [O_SYNC](os_posix_package_constants_vars.md#const-o_sync) 或 [O_DSYNC](os_posix_package_constants_vars.md#const-o_dsync) 结合使用。如果有必要，它将导致读取调用阻塞，直到正在读取的数据（可能还有元数据）刷新到磁盘，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_SYNC

```cangjie
public const O_SYNC: Int32
```

功能：同步打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_TRUNC

```cangjie
public const O_TRUNC: Int32
```

功能：如果文件存在且打开可写，则此标志将文件长度清除为 0，文件中以前存储的数据消失，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const O_WRONLY

```cangjie
public const O_WRONLY: Int32
```

功能：以只写方式打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const R_OK

```cangjie
public const R_OK: Int32
```

功能：测试文件读权限，适用函数 [access](os_posix_package_funcs.md#func-accessstring-int32)，[faccessat](os_posix_package_funcs.md#func-faccessatint32-string-int32-int32)，所属函数参数 `mode`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SEEK_CUR

```cangjie
public const SEEK_CUR: Int32
```

功能：向当前读或写位置添加偏移量，适用函数 [lseek](os_posix_package_funcs.md#func-lseekint32-int64-int32)，所属函数参数 `whence`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SEEK_END

```cangjie
public const SEEK_END: Int32
```

功能：将读写位置设置为文件末尾，并添加偏移量，适用函数 [lseek](os_posix_package_funcs.md#func-lseekint32-int64-int32)，所属函数参数 `whence`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SEEK_SET

```cangjie
public const SEEK_SET: Int32
```

功能：偏移参数表示新的读写位置，适用函数 [lseek](os_posix_package_funcs.md#func-lseekint32-int64-int32)，所属函数参数 `whence`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGABRT

```cangjie
public const SIGABRT: Int32
```

功能：异常终止，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGALRM

```cangjie
public const SIGALRM: Int32
```

功能：计时器到期，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGBUS

```cangjie
public const SIGBUS: Int32
```

功能：硬件故障，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGCHLD

```cangjie
public const SIGCHLD: Int32
```

功能：子进程状态更改，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGCONT

```cangjie
public const SIGCONT: Int32
```

功能：暂停过程的继续，默认操作继续或忽略，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGFPE

```cangjie
public const SIGFPE: Int32
```

功能：算术错误，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGHUP

```cangjie
public const SIGHUP: Int32
```

功能：连接已断开，默认操作已终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGILL
 
```cangjie
public const SIGILL: Int32
```
 
功能：硬件指令无效，默认动作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。
 
类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGINT

```cangjie
public const SIGINT: Int32
```

功能：终端中断字符，默认动作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGIO

```cangjie
public const SIGIO: Int32
```

功能：异步 `IO`，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGIOT

```cangjie
public const SIGIOT: Int32
```

功能：硬件故障，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGKILL

```cangjie
public const SIGKILL: Int32
```

功能：终止，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGPIPE

```cangjie
public const SIGPIPE: Int32
```

功能：写入未读进程的管道，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGPROF

```cangjie
public const SIGPROF: Int32
```

功能：摘要超时，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGPWR

```cangjie
public const SIGPWR: Int32
```

功能：电源故障或重启，系统调用无效，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGQUIT

```cangjie
public const SIGQUIT: Int32
```

功能：终端退出字符，默认动作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGSEGV

```cangjie
public const SIGSEGV: Int32
```

功能：内存引用无效，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGSTKFLT

```cangjie
public const SIGSTKFLT: Int32
```

功能：协处理器堆栈故障，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGSTOP

```cangjie
public const SIGSTOP: Int32
```

功能：停止，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGTERM

```cangjie
public const SIGTERM: Int32
```

功能：终止，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGTRAP

```cangjie
public const SIGTRAP: Int32
```

功能：硬件故障，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGTSTP

```cangjie
public const SIGTSTP: Int32
```

功能：终端停止符号，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGTTIN

```cangjie
public const SIGTTIN: Int32
```

功能：后台读取控件 `tty`，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGTTOU

```cangjie
public const SIGTTOU: Int32
```

功能：后台写控制 `tty`，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGURG

```cangjie
public const SIGURG: Int32
```

功能：紧急情况（套接字），忽略默认操作，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGUSR1

```cangjie
public const SIGUSR1: Int32
```

功能：用户定义的信号，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGUSR2

```cangjie
public const SIGUSR2: Int32
```

功能：用户定义的信号，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGVTALRM

```cangjie
public const SIGVTALRM: Int32
```

功能：虚拟时间警报，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGWINCH

```cangjie
public const SIGWINCH: Int32
```

功能：终端窗口大小更改，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGXCPU

```cangjie
public const SIGXCPU: Int32
```

功能：`CPU` 占用率超过上限，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const SIGXFSZ

```cangjie
public const SIGXFSZ: Int32
```

功能：文件长度超过上限，默认操作终止，适用函数 [kill](os_posix_package_funcs.md#func-killint32-int32)，[killpg](os_posix_package_funcs.md#func-killpgint32-int32)，所属函数参数 `sig`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)

## const S_IFBLK

```cangjie
public const S_IFBLK: UInt32
```

功能：文件类型为块设备，适用函数 [isType](os_posix_package_funcs.md#func-istypestring-uint32)， 所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IFCHR

```cangjie
public const S_IFCHR: UInt32
```

功能：文件类型为字符设备，适用函数 [isType](os_posix_package_funcs.md#func-istypestring-uint32)， 所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IFDIR

```cangjie
public const S_IFDIR: UInt32
```

功能：文件类型为目录，适用函数 [isType](os_posix_package_funcs.md#func-istypestring-uint32)， 所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IFIFO

```cangjie
public const S_IFIFO: UInt32
```

功能：文件类型为 `FIFO` 文件，适用函数 [isType](os_posix_package_funcs.md#func-istypestring-uint32)， 所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IFLNK

```cangjie
public const S_IFLNK: UInt32
```

功能：文件类型为软连接，适用函数 [isType](os_posix_package_funcs.md#func-istypestring-uint32)， 所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IFREG

```cangjie
public const S_IFREG: UInt32
```

功能：文件类型为一般文件，适用函数 [isType](os_posix_package_funcs.md#func-istypestring-uint32)， 所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IFSOCK

```cangjie
public const S_IFSOCK: UInt32
```

功能：文件类型为套接字文件，适用函数 [isType](os_posix_package_funcs.md#func-istypestring-uint32)， 所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IRGRP

```cangjie
public const S_IRGRP: UInt32
```

功能：表示文件用户组具有读权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IROTH

```cangjie
public const S_IROTH: UInt32
```

功能：表示其他用户对文件具有读权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IRUSR

```cangjie
public const S_IRUSR: UInt32
```

功能：表示文件所有者具有读权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IRWXG

```cangjie
public const S_IRWXG: UInt32
```

功能：表示文件用户组具有读、写、执行权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IRWXO

```cangjie
public const S_IRWXO: UInt32
```

功能：表示其他用户对文件具有读、写和执行权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IRWXU

```cangjie
public const S_IRWXU: UInt32
```

功能：表示文件所有者具有读、写和执行权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IWGRP

```cangjie
public const S_IWGRP: UInt32
```

功能：表示文件用户组具有写权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IWOTH

```cangjie
public const S_IWOTH: UInt32
```

功能：表示其他用户对文件具有写权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IWUSR

```cangjie
public const S_IWUSR: UInt32
```

功能：表示文件所有者具有写权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IXGRP

```cangjie
public const S_IXGRP: UInt32
```

功能：表示文件用户组具有执行权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IXOTH

```cangjie
public const S_IXOTH: UInt32
```

功能：表示其他用户对文件具有执行权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const S_IXUSR

```cangjie
public const S_IXUSR: UInt32
```

功能：表示文件所有者具有执行权限，适用函数 open，open64，openat，openat64，[chmod](os_posix_package_funcs.md#func-chmodstring-uint32)(mode)，[fchmod](os_posix_package_funcs.md#func-fchmodint32-uint32)(mode)，[fchmodat](os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32)(mode)，[creat](os_posix_package_funcs.md#func-creatstring-uint32)， 所属函数参数 `flag`。

## const W_OK

```cangjie
public const W_OK: Int32
```

功能：测试文件写权限，适用函数 [access](os_posix_package_funcs.md#func-accessstring-int32)，[faccessat](os_posix_package_funcs.md#func-faccessatint32-string-int32-int32)，所属函数参数 `mode`。

类型：[UInt32](../../core/core_package_api/core_package_intrinsics.md#uint32)

## const X_OK

```cangjie
public const X_OK: Int32
```

功能：测试文件执行权限，适用函数 [access](os_posix_package_funcs.md#func-accessstring-int32)，[faccessat](os_posix_package_funcs.md#func-faccessatint32-string-int32-int32)，所属函数参数 `mode`。

类型：[Int32](../../core/core_package_api/core_package_intrinsics.md#int32)
