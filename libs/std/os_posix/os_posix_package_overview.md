# std.os.posix 包

## 功能介绍

os.posix 包主要适配 POSIX 系统接口。

本包提供多平台统一操控能力，目前支持 Linux 平台，macOS 平台，Windows 平台与 HarmonyOS 平台。

## API 列表

### 函数

|  函数名 | 功能  | 支持平台 |
| ------------ | ------------ | ----------- |
| [open(String, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-openstring-int32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、Windows、macOS、HarmonyOS |
| [open(String, Int32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-openstring-int32-uint32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、Windows、macOS、HarmonyOS |
| [access(String, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-accessstring-int32) | 判断某个文件是否具有某种权限，具有返回 `0`，否则返回 `-1`。 | Linux、Windows、macOS、HarmonyOS |
| [chdir(String)](./os_posix_package_api/os_posix_package_funcs.md#func-chdirstring) | 通过指定路径的方式，更改调用进程的当前工作目录。 | Linux、Windows、macOS、HarmonyOS |
| [chmod(String, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-chmodstring-uint32) | 修改文件访问权限。 | Linux、Windows、macOS、HarmonyOS |
| [chown(String, UInt32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-chownstring-uint32-uint32) | 修改文件所有者和文件所有者所属组。 | Linux、macOS、HarmonyOS |
| [close(Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-closeint32) | 关闭文件，`close` 将会触发数据写回磁盘，并释放文件占用的资源。 | Linux、Windows、macOS、HarmonyOS |
| [creat(String, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-creatstring-uint32) | 创建文件并为其返回文件描述符，或在失败时返回 `-1`。 | Linux、Windows、macOS、HarmonyOS |
| [dup(Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-dupint32) | 用于复制旧 `fd` 参数指定的文件描述符并返回。 | Linux、Windows、macOS、HarmonyOS |
| [dup2(Int32, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-dupint32-int32) | 用于复制 `oldfd` 参数指定的文件描述符，并将其返回到 `newfd` 参数。 | Linux、Windows、macOS、HarmonyOS |
| [faccessat(Int32, String, Int32, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-faccessatint32-string-int32-int32) | 判断 `fd` 对应的文件是否具有某种权限，具有返回 `0`，否则返回 `-1`。 | Linux、macOS、HarmonyOS |
| [fchdir(Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-fchdirint32) | 通过指定文件路径的描述符，更改调用进程的当前工作目录。 | Linux、macOS、HarmonyOS |
| [fchmod(Int32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-fchmodint32-uint32) | 修改文件描述符对应的文件访问权限。 | Linux、Windows、macOS、HarmonyOS |
| [fchmodat(Int32, String, UInt32, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-fchmodatint32-string-uint32-int32) | 修改文件描述符对应的文件访问权限。 | Linux、Windows、macOS、HarmonyOS |
| [fchown(Int32, UInt32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-fchownint32-uint32-uint32) | 修改 `fd` 对应的文件所有者和文件所有者所属组。 | Linux、macOS、HarmonyOS |
| [fchownat(Int32, String, UInt32, UInt32, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-fchownatint32-string-uint32-uint32-int32) | 修改文件描述符对应的文件所有者和文件所有者所属组。 | Linux、macOS、HarmonyOS |
| [getcwd()](./os_posix_package_api/os_posix_package_funcs.md#func-getcwd) | 获取当前执行进程工作目录的绝对路径。 | Linux、Windows、macOS、HarmonyOS |
| [getgid()](./os_posix_package_api/os_posix_package_funcs.md#func-getgid) | 获取用户组 `ID`。 | Linux、macOS、HarmonyOS |
| [getgroups(Int32, CPointer\<UInt32>)](./os_posix_package_api/os_posix_package_funcs.md#func-getgroupsint32-cpointeruint32) | 获取当前用户所属组的代码。 | Linux、macOS、HarmonyOS |
| [gethostname()](./os_posix_package_api/os_posix_package_funcs.md#func-gethostname) | 获取主机名称，此名称通常是 `TCP/IP` 网络上主机的名称。 | Linux、macOS、HarmonyOS |
| [getlogin()](./os_posix_package_api/os_posix_package_funcs.md#func-getlogin) | 获取当前登录名。 | Linux、macOS、HarmonyOS |
| [getos()](./os_posix_package_api/os_posix_package_funcs.md#func-getos) | 从 `/proc/version` 文件中获取 Linux 系统的信息。 | Linux |
| [getpgid(Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-getpgidint32) | 获取 `pid` 指定的进程的 `PGID`，如果 `pid` 为零，返回调用进程的进程 `ID`。 | Linux、macOS、HarmonyOS |
| [getpgrp()](./os_posix_package_api/os_posix_package_funcs.md#func-getpgrp) | 获取调用进程的父进程 `ID`。 | Linux、macOS、HarmonyOS |
| [getpid()](./os_posix_package_api/os_posix_package_funcs.md#func-getpid) | 获取调用进程的进程 `ID(PID)`。 | Linux、Windows、macOS、HarmonyOS |
| [getppid()](./os_posix_package_api/os_posix_package_funcs.md#func-getppid) | 获取调用进程的父进程 `ID`。 | Linux、macOS、HarmonyOS |
| [getuid()](./os_posix_package_api/os_posix_package_funcs.md#func-getuid) | 获取调用进程的真实用户 `ID`。 | Linux、macOS、HarmonyOS |
| [isBlk(String)](./os_posix_package_api/os_posix_package_funcs.md#func-isblkstring) | 检查传入对象是否为块设备，并返回布尔类型。 | Linux、Windows、macOS、HarmonyOS |
| [isChr(String)](./os_posix_package_api/os_posix_package_funcs.md#func-ischrstring) | 检查传入对象是否为字符设备，返回布尔类型。 | Linux、Windows、macOS、HarmonyOS |
| [isDir(String)](./os_posix_package_api/os_posix_package_funcs.md#func-isdirstring) | 检查传入对象是否为文件夹，返回布尔类型。 | Linux、Windows、macOS、HarmonyOS |
| [isFIFO(String)](./os_posix_package_api/os_posix_package_funcs.md#func-isfifostring) | 检查传入对象是否为 `FIFO` 文件，返回布尔类型。 | Linux、macOS、HarmonyOS |
| [isLnk(String)](./os_posix_package_api/os_posix_package_funcs.md#func-islnkstring) | 检查传入对象是否为软链路，返回布尔类型。 | Linux、macOS、HarmonyOS |
| [isReg(String)](./os_posix_package_api/os_posix_package_funcs.md#func-isregstring) | 检查传入对象是否为普通文件，返回布尔类型。 | Linux、Windows、macOS、HarmonyOS |
| [isSock(String)](./os_posix_package_api/os_posix_package_funcs.md#func-issockstring) | 检查传入对象是否为套接字文件，返回布尔类型。 | Linux、macOS、HarmonyOS |
| [isType(String, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-istypestring-uint32) | 检查文件是否为指定模式的文件。 | Linux、macOS、HarmonyOS |
| [isatty(Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-isattyint32) | 用于测试文件描述符是否引用终端，成功时返回 `true`，否则返回 `false`。 | Linux、Windows、macOS、HarmonyOS |
| [kill(Int32, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-killint32-int32) | 系统调用可用于向任何进程组或进程发送任何信号。 | Linux、macOS、HarmonyOS |
| [killpg(Int32, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-killpgint32-int32) | 将信号 `sig` 发送到进程组 `pgrp`，如果 `pgrp` 为 `0`，则 killpg() 将信号发送到调用进程的进程组。 | Linux、macOS、HarmonyOS |
| [lchown(String, UInt32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-lchownstring-uint32-uint32) | 修改文件链接本身所有者和所有者所属组。 | Linux、macOS |
| [link(String, String)](./os_posix_package_api/os_posix_package_funcs.md#func-linkstring-string) | 为存在的文件创建链接，一个文件可以有多个指向其 `i-node` 的目录条目。 | Linux、macOS、HarmonyOS |
| [linkat(Int32, String, Int32, String, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-linkatint32-string-int32-string-int32) | 创建相对于目录文件描述符的文件链接。 | Linux、macOS、HarmonyOS |
| [lseek(Int32, Int64, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-lseekint32-int64-int32) | 当文件进行读或写时，读或写位置相应增加。 | Linux、Windows、macOS、HarmonyOS |
| [nice(Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-niceint32) | 更改当前线程的优先级。 | Linux、macOS、HarmonyOS |
| [open64(String, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-openstring-int32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、HarmonyOS |
| [open64(String, Int32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-openstring-int32-uint32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、HarmonyOS |
| [openat(Int32, String, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-openatint32-string-int32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、macOS、HarmonyOS |
| [openat(Int32, String, Int32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-openatint32-string-int32-uint32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、macOS、HarmonyOS |
| [openat64(Int32, String, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-openatint32-string-int32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、macOS、HarmonyOS |
| [openat64(Int32, String, Int32, UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-openatint32-string-int32-uint32) | 打开文件并为其返回新的文件描述符，或在失败时返回 `-1`。 | Linux、macOS、HarmonyOS |
| [pread(Int32, CPointer\<UInt8>, UIntNative, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-preadint32-cpointeruint8-uintnative-int32) | 将 `fd` 指向的文件的 `nbyte` 字节传输到 `buffer` 指向的内存中。 | Linux、macOS、HarmonyOS |
| [pwrite(Int32, CPointer\<UInt8>, UIntNative, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-pwriteint32-cpointeruint8-uintnative-int32) | 将 `buffer` 指向的内存中 `nbyte` 字节从指定偏移位置开始写入到 `fd` 指向的文件。 | Linux、macOS、HarmonyOS |
| [read(Int32, CPointer\<UInt8>, UIntNative)](./os_posix_package_api/os_posix_package_funcs.md#func-readint32-cpointeruint8-uintnative) | 将 `fd` 指向的文件的 `nbyte` 字节传输到 `buffer` 指向的内存中。 | Linux、Windows、macOS、HarmonyOS |
| [remove(String)](./os_posix_package_api/os_posix_package_funcs.md#func-removestring) | 删除文件或目录。 | Linux、Windows、macOS、HarmonyOS |
| [rename(String, String)](./os_posix_package_api/os_posix_package_funcs.md#func-renamestring-string) | 重命名文件，如果需要将会移动文件所在目录。 | Linux、Windows、macOS、HarmonyOS |
| [renameat(Int32, String, Int32, String)](./os_posix_package_api/os_posix_package_funcs.md#func-renameatint32-string-int32-string) | 重命名文件，如果需要将会移动文件所在目录。 | Linux、macOS、HarmonyOS |
| [setgid(UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-setgiduint32) | 设置调用进程的有效组 `ID`，需要适当的权限。 | Linux、macOS |
| [sethostname(String)](./os_posix_package_api/os_posix_package_funcs.md#func-sethostnamestring) | 设置主机名，仅超级用户可以调用。 | Linux、macOS |
| [setpgid(Int32, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-setpgidint32-int32) | 此函数将参数 `pid` 指定的组 `ID` 设置为参数 `pgrp` 指定的组 `ID`。 | Linux、macOS、HarmonyOS |
| [setpgrp()](./os_posix_package_api/os_posix_package_funcs.md#func-setpgrp) | 将当前进程所属的组 `ID` 设置为当前进程的进程 `ID`，此函数等同于调用 setpgid(0, 0)。 | Linux、macOS、HarmonyOS |
| [setuid(UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-setuiduint32) | 设置调用进程的有效用户 `ID`，需要适当的权限。 | Linux、macOS |
| [symlink(String, String)](./os_posix_package_api/os_posix_package_funcs.md#func-symlinkstring-string) | 创建一个名为 `symPath` 链接到 `path` 所指定的文件。 | Linux、macOS、HarmonyOS |
| [symlinkat(String, Int32, String)](./os_posix_package_api/os_posix_package_funcs.md#func-symlinkatstring-int32-string) | 创建一个名为 `symPath` 链接到 `path` 与 `fd` 所指定的文件。 | Linux、macOS、HarmonyOS |
| [ttyname(Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-ttynameint32) | 返回终端名称。 | Linux、Windows、macOS、HarmonyOS |
| [umask(UInt32)](./os_posix_package_api/os_posix_package_funcs.md#func-umaskuint32) | 设置权限掩码。 | Linux、Windows、macOS、HarmonyOS |
| [unlink(String)](./os_posix_package_api/os_posix_package_funcs.md#func-unlinkstring) | 从文件系统中删除文件。 | Linux、macOS、HarmonyOS |
| [unlinkat(Int32, String, Int32)](./os_posix_package_api/os_posix_package_funcs.md#func-unlinkatint32-string-int32) | 从文件系统中删除文件。 | Linux、macOS、HarmonyOS |
| [write(Int32, CPointer\<UInt8>, UIntNative)](./os_posix_package_api/os_posix_package_funcs.md#func-writeint32-cpointeruint8-uintnative) | 将 `buffer` 指向的内存中 `nbyte` 字节写入到 `fd` 指向的文件。 | Linux、Windows、macOS、HarmonyOS |

### 常量

| 常量名 | 功能 | 支持平台 |
| ------------ | ------------ | ----------- |
| [AT_EMPTY_PATH](./os_posix_package_api/os_posix_package_constants_vars.md#const-at_empty_path) | 表示在文件系统中空路径（即没有指定任何文件或目录）时返回的文件描述符，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、HarmonyOS |
| [AT_REMOVEDIR](./os_posix_package_api/os_posix_package_constants_vars.md#const-at_removedir) | 如果指定了 `AT_REMOVEDIR` 标志，则对 `pathname` 执行等效于 `rmdir(2)` 的操作，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [O_CLOEXEC](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_cloexec) | 在某些多线程程序中，使用此标志是必不可少的。因为在一个线程同时打开文件描述符，而另一个线程执行 `fork(2)` 加 `execve(2)` 场景下使用单独的 `fcntl(2)` `F_SETFD` 操作设置 `FD_CLOEXEC` 标志并不足以避免竞争条件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、macOS、HarmonyOS |
| [O_DIRECTORY](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_directory) | 如果 `pathname` 指定的文件不是目录，则打开文件失败，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、macOS、HarmonyOS |
| [O_CREAT](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_creat) | 如果要打开的文件不存在，则自动创建该文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [O_DSYNC](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_dsync) | 每次写入都会等待物理 `I/O` 完成，但如果写操作不影响读取刚写入的数据，则不等待文件属性更新，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、macOS、HarmonyOS |
| [O_EXCL](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_excl) | 如同时设置 `O_CREAT`，则此指令检查文件是否存在。如果文件不存在，则创建文件。否则，打开文件出错。此外，如果同时设置了 `O_CREAT` 和 `O_EXCL`，并且要打开的文件是符号链接，则打开文件失败，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [O_NOCTTY](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_noctty) | 如要打开的文件是终端设备，则该文件不会成为这个进程的控制终端，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、macOS、HarmonyOS |
| [O_NOFOLLOW](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_nofollow) | 如 `pathname` 指定的文件是单符号连接，则打开文件失败，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、macOS、HarmonyOS |
| [O_NONBLOCK](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_nonblock) | 以非阻塞的方式打开文件，即 `I/O` 操作不会导致调用进程等待，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、macOS、HarmonyOS |
| [O_SYNC](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_sync) | 同步打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、macOS、HarmonyOS |
| [O_RDONLY](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_rdonly) | 以只读方式打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [O_RDWR](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_rdwr) | 以读写模式打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [O_WRONLY](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_wronly) | 以只写方式打开文件，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [O_APPEND](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_append) | 读取或写入文件时，数据将从文件末尾移动。即写入的数据将附加到文件的末尾，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [O_RSYNC](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_rsync) | 此标志仅影响读取操作，必须与 `O_SYNC` 或 `O_DSYNC` 结合使用。如果有必要，它将导致读取调用阻塞，直到正在读取的数据（可能还有元数据）刷新到磁盘，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、HarmonyOS |
| [O_TRUNC](./os_posix_package_api/os_posix_package_constants_vars.md#const-o_trunc) | 如果文件存在且打开可写，则此标志将文件长度清除为 0，文件中以前存储的数据消失，适用函数 `open`、`open64`、`openat`、`openat64`，所属函数参数 `oflag`。 | Linux、Windows、macOS、HarmonyOS |
| [R_OK](./os_posix_package_api/os_posix_package_constants_vars.md#const-r_ok) | 测试文件读权限，适用函数 `access`，`faccessat`，所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [W_OK](./os_posix_package_api/os_posix_package_constants_vars.md#const-w_ok) | 测试文件写权限，适用函数 `access`，`faccessat`，所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [X_OK](./os_posix_package_api/os_posix_package_constants_vars.md#const-x_ok) | 测试文件执行权限，适用函数 `access`，`faccessat`，所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [F_OK](./os_posix_package_api/os_posix_package_constants_vars.md#const-f_ok) | 测试文件是否存在，适用函数 `access`，`faccessat`，所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [SEEK_SET](./os_posix_package_api/os_posix_package_constants_vars.md#const-seek_set) | 偏移参数表示新的读写位置，适用函数 `lseek`，所属函数参数 `whence`。 | Linux、Windows、macOS、HarmonyOS |
| [SEEK_CUR](./os_posix_package_api/os_posix_package_constants_vars.md#const-seek_cur) | 向当前读或写位置添加偏移量，适用函数 `lseek`，所属函数参数 `whence`。 | Linux、Windows、macOS、HarmonyOS |
| [SEEK_END](./os_posix_package_api/os_posix_package_constants_vars.md#const-seek_end) | 将读写位置设置为文件末尾，并添加偏移量，适用函数 `lseek`，所属函数参数 `whence`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGABRT](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigabrt) | 异常终止，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGBUS](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigbus) | 硬件故障，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGFPE](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigfpe) | 算术错误，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGKILL](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigkill) | 终止，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGCONT](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigcont) | 暂停过程的继续，默认操作继续或忽略，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGHUP](./os_posix_package_api/os_posix_package_constants_vars.md#const-sighup) | 连接已断开，默认操作已终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGINT](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigint) | 终端中断字符，默认动作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGQUIT](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigquit) | 终端退出字符，默认动作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGILL](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigill) | 硬件指令无效，默认动作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGTRAP](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigtrap) | 硬件故障，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGIOT](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigiot) | 硬件故障，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGIO](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigio) | 异步 `IO`，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGPIPE](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigpipe) | 写入未读进程的管道，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGALRM](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigalrm) | 计时器到期，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGPWR](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigpwr) | 电源故障或重启，系统调用无效，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、HarmonyOS |
| [SIGSEGV](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigsegv) | 内存引用无效，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGSTOP](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigstop) | 停止，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGTERM](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigterm) | 终止，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGSTKFLT](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigstkflt) | 协处理器堆栈故障，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、HarmonyOS |
| [SIGCHLD](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigchld) | 子进程状态更改，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGTSTP](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigtstp) | 终端停止符号，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGTTIN](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigttin) | 后台读取控件 `tty`，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGTTOU](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigttou) | 后台写控制 `tty`，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGURG](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigurg) | 紧急情况（套接字），忽略默认操作，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGUSR1](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigusr1) | 用户定义的信号，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGUSR2](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigusr2) | 用户定义的信号，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGVTALRM](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigvtalrm) | 虚拟时间警报，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGPROF](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigprof) | 摘要超时，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGWINCH](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigwinch) | 终端窗口大小更改，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGXCPU](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigxcpu) | `CPU` 占用率超过上限，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [SIGXFSZ](./os_posix_package_api/os_posix_package_constants_vars.md#const-sigxfsz) | 文件长度超过上限，默认操作终止，适用函数 `kill`，`killpg`，所属函数参数 `sig`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IRUSR](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_irusr) | 表示文件所有者具有读权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IWUSR](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_iwusr) | 表示文件所有者具有写权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IRGRP](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_iwgrp) | 表示文件用户组具有读权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IWGRP](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_iwgrp) | 表示文件用户组具有写权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IFREG](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ifreg) | 文件类型为一般文件，适用函数 `isType`， 所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IFBLK](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ifblk) | 文件类型为块设备，适用函数 `isType`， 所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IFDIR](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ifdir) | 文件类型为目录，适用函数 `isType`， 所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IFCHR](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ifchr) | 文件类型为字符设备，适用函数 `isType`， 所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IFIFO](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ififo) | 文件类型为 `FIFO` 文件，适用函数 `isType`， 所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IFLNK](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_iflnk) | 文件类型为软连接，适用函数 `isType`， 所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IFSOCK](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ifsock) | 文件类型为套接字文件，适用函数 `isType`， 所属函数参数 `mode`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IROTH](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_iroth) | 表示其他用户对文件具有读权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IRWXG](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_irwxg) | 表示文件用户组具有读、写、执行权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IRWXU](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_irwxu) | 表示文件所有者具有读、写和执行权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IWOTH](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_iwoth) | 表示其他用户对文件具有写权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IXOTH](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ixoth) | 表示其他用户对文件具有执行权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IRWXO](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_irwxo) | 表示其他用户对文件具有读、写和执行权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IXGRP](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ixgrp) | 表示文件用户组具有执行权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
| [S_IXUSR](./os_posix_package_api/os_posix_package_constants_vars.md#const-s_ixusr) | 表示文件所有者具有执行权限，适用函数 `open`，`open64`，`openat`，`openat64`，`chmod(mode)`，`fchmod(mode)`，`fchmodat(mode)`，`creat`， 所属函数参数 `flag`。 | Linux、Windows、macOS、HarmonyOS |
