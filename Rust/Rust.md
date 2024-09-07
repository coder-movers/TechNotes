### 检测rust版本

```shell
rustc --version

# 或者
rustc -V
```

### 本地文档

```shell
rustup doc
```

### 手动编译

> 只适合简单的rust程序

```shell
rustc <文件名>

# 比如
rustc main.rs
```



### Rust配置镜像源

> 解决更新Rust和下载依赖过慢的问题

#### 1. 配置两个镜像源

环境变量中增加：

1. `RUSTUP_DIST_SERVER=https://rsproxy.cn`

2. `RUSTUP_UPDATE_ROOT=https://rsproxy.cn/rustup`

> `RUSTUP_DIST_SERVER`：指定下载rustup所管理的工具链（如Rust编译器、标准库和相关组件等）的服务器地址。
>
> `RUSTUP_UPDATE_ROOT`：指定下载rustup自身的初始化和自我更新的服务器地址。



#### 2. 迁移cargo下载的依赖仓库（可选）

> 解决下载的依赖在C盘占用空间问题，将本地依赖仓库迁移至其他盘

1. 在D盘任意目录创建新文件夹，比如：`D:\Rust\cargo`
2. 在C盘用户目录下找`.cargo`文件夹，将该文件夹下`bin`目录复制至D盘新文件夹下
3. 新增环境变量：`CARGO_HOME=D:\Rust\cargo`
4. 在path中新增环境变量：`D:\Rust\cargo\bin`
5. 重启电脑使环境变量生效（可选）
6. 验证是否设置成功，终端使用`rust --version`命令校验



#### 3. 设置cargo的配置文件

> 解决cargo构建项目缓慢的问题

在C盘用户目录下找`.cargo`文件夹（或者迁移后的cargo目录），修改`config.toml`配置文件，没有就直接创建，写入配置内容，保存并退出：

```toml
[source.crates-io]
replace-with = 'rsproxy-sparse'
[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"
[source.rsproxy-sparse]
registry = "sparse+https://rsproxy.cn/index/"
[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"
[net]
git-fetch-with-cli = true
```



### 运行项目

```shell
cargo run
```

会在target目录生成一个`.exe`，项目运行会执行并监听这个`.exe`文件，但是无法直接点击运行



### 检查代码

```shell
cargo check
```

检查代码，确保可以通过编译，但不产生可执行文件

速度比build快很多，开发时通常使用check检查代码



### 打包为可执行文件

```shell
cargo build

# 发布应用使用这个
cargo build --release
```

会在target目录的release目录下生成一个高度集成的可执行文件，一般情况下可以直接分发

