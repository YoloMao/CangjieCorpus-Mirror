# 函数

## func sleep(Duration)

```cangjie
public func sleep(dur: Duration): Unit
```

功能：休眠当前线程。

若 `dur` 小于等于 [Duration.Zero](../../time/time_package_api/time_package_structs.md#static-prop-zero)，当前线程会让出运行权。

参数：

- dur: [Duration](../../time/time_package_api/time_package_structs.md#struct-duration) - 线程休眠的时长。
