# 安装仓颉工具链

请在仓颉官方渠道（官网或者 Gitee）根据平台架构下载相应安装包，如 `linux_x64` 。

下载成功后，解压安装包，通过配置环境变量即可完成安装。具体步骤如下（以 `Cangjie-0.XX.X-linux_x64-cjvm.tar.gz` 为例）：

1. 解压：

    ```shell
    $ tar -xvf Cangjie-0.XX.X-linux_x64-cjvm.tar.gz
    ```

    > **注意：**
    >
    > 请不要将 `cjc` 安装在包含 `:` (冒号) 或 `;` (分号) 的目录下，否则 `cjc` 可能无法正常使用。

2. 配置环境变量：

    ```shell
    $ source cangjie/envsetup.sh
    ```

3. 验证安装，执行以下命令：

    ```shell
    $ cjc -v
    ```

    若成功安装，应该可以看到当前的版本号，其格式如下：

    ```shell
    Cangjie Compiler: x.y.z ...
    ```

    至此，仓颉工具链在 Ubuntu 18.04 上的安装完成。

**需要注意的是**，所配置的环境变量仅在运行 `source` 命令的当前 `shell` 会话窗口有效，重启 `shell` 后需要重新执行配置环境变量的步骤。若想使这些环境变量在 `shell` 每次启动时自动生效，可以在 `$HOME/.bashrc` 或 `$HOME/.zshrc`（依 `shell` 种类而定）等 `shell` 初始化配置文件的最后加入以下命令：

```shell
# 假设仓颉安装包解压在 /home/user/cangjie 中
source /home/user/cangjie/envsetup.sh  # 即 envsetup.sh 的绝对路径
```
