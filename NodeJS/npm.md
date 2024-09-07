### 常用命令

- 清除缓存：

  ```shell
  npm cache clean --force
  ```

- 配置淘宝镜像：

  ```shell
  npm config set registry https://registry.npm.taobao.org
  ```

- 取消淘宝镜像

  ```shell
  npm config delete registry
  ```

- 查看当前代理信息

  ```shell
  npm config list
  ```




### 配置代理解决网络问题无法安装依赖问题

```shell
# windows命令行执行(当前终端生效)
set http_proxy=http://127.0.0.1:7890
set https_proxy=http://127.0.0.1:7890

#git bash，git bash可以通过在~路径下新建.bashrc，将下面两条命令写入，然后source ~/.bashrc，就可以实现永久的设置代理
export http_proxy=http://127.0.0.1:7890
export https_proxy=http://127.0.0.1:7890
或者
export ALL_PROXY=http://127.0.0.1:7890

或者直接使用alias来简介操作，每次要用的时候输入setproxy，不用了就unsetproxy。
alias setproxy="export ALL_PROXY=http://127.0.0.1:7890" alias unsetproxy="unset ALL_PROXY"

#用这条命令来验证，不能使用ping（ping的协议不是https，也不是https，是ICMP协议）
curl -vv http://www.google.com

#如果指向对某些命令进行代理，也可以改相应工具的配置，比如apt的配置
sudo vim /etc/apt/apt.conf
#在文件末尾加入下面这行
Acquire::http::Proxy "http://127.0.0.1:7890"

#使用git对于其他方面都不是经常使用，可以直接配置git的命令。使用ss/ssr来加快git的速度。直接输入这个命令
git config --global http.proxy 'socks5://127.0.0.1:7890'
git config --global https.proxy 'socks5://127.0.0.1:7890'
```



### npm报错无法加载文件，在此系统上禁止运行脚本

解决办法：

1. 在终端运行

   ```shell
   get-ExecutionPolicy
   ```

   显示Restricted（表示没有权限）

2. 设置权限

   ```shell
   Set-ExecutionPolicy -Scope CurrentUser
   ```

3. 提示为参数提供值，输入`Remotesigned`

   ```shell
   ExecutionPolicy:Remotesigned
   ```




### npm install 中 node-sass报错

- 方法一：

  ```shell
  npm i node-sass -D
  ```

- 方法二：

  ```shell
  # windows
  set SASS_BINARY_SITE=http://npmmirror.com/mirrors/node-sass&&npm i node-sass
  
  # linux
  SASS_BINARY_SITE=http://npmmirror.com/mirrors/node-sass npm install node-sass
  ```

- 方法三：

  用cnpm install


- 方法四：

  ```shell
  yarn
  ```

  

### yarn

>优点：速度快、安装版本统一

| npm                          | yarn                 |
| ---------------------------- | -------------------- |
| npm install                  | yarn                 |
| npm install react --save     | yarn add react       |
| npm uninstall react --save   | yarn remove react    |
| npm install react --save-dev | yarn add react --dev |
| npm update --save            | yarn upgrade         |



### package.json中你的版本号规则

- 直接写版本号就是指定版本号
- **波浪号〜**匹配最新补丁版本号，也就是版本号的第三个数字。比如~1.2.3将匹配所有1.2.x版本，但将在1.3.0上停止。
- **插入符号^** 更宽松。 它匹配的是最新次要版本号，也就是第二个数字。比如：^ 1.2.3将匹配任何1.x.x版本，包括1.3.0，但将在2.0.0上停止。
- 版本号前面是星号*，那意思就是匹配任何版本。
- 版本号的值是**latest**，那意思安装的永远是最新发布的版本。



### npm镜像依赖拉取报错

```shell
npm install -g mirror-config-china --registry=https://registry.npmmirror.com

npm config set registry https://registry.npmmirror.com
```



### element-ui 报错 [Vue warn]:Prop being mutated: “placement“

>  原因：el-data-picker组件源码中在props接收了placement，并且有初始值，在created的时候又重新进行了赋值，所以会出现这种警告错误；

解决：只有element-ui版本为2.15.9时有这个问题，`package.json` 和 `package-lock.json`中避免该版本

