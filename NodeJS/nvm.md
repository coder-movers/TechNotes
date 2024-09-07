### 作用

在 Windows 系统上安装多个 Node.js 版本并在它们之间进行切换



### 安装

github上下载：https://github.com/coreybutler/nvm-windows/releases



### 命令

验证是否安装成功

```shell
nvm --version
```

> 报错找不到命令，检查环境变量是否配置
>
> 1. 打开nvm所在的安装目录，找到`settings.txt`文件，并用记事本打开。
> 2. 将`root`路径更改为你想要将nvm安装的路径，例如：`C:\Program Files\nvm`。
> 3. 将nvm所在目录添加到系统环境变量中
>
> 还不生效，重启以后再次使用命令验证



安装最新版node

```shell
nvm install node
```



安装指定版本node

```shell
nvm install 12.22.1
```



切换node版本

```shell
nvm use 12.22.1
```



使用指定node版本运行指定程序

```shell
nvm run 12.22.1 指定程序
```



卸载指定版本

```shell
nvm uninstall 12.22.1
```



查看所有可用版本

```shell
nvm ls

或者

nvm list
```



切换至淘宝源

```shell
nvm node_mirror https://npm.taobao.org/mirrors/node/
nvm npm_mirror https://npm.taobao.org/mirrors/npm/
```



清除缓存

> 在 Windows 系统上，nvm 并没有提供 `nvm cache clear` 命令

可以手动删除 nvm 的缓存目录。缓存目录的路径是 `%APPDATA%\nvm\Cache`。



