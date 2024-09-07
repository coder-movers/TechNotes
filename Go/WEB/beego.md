## 安装

1. 启用模块支持

   ```shell
   go env -w GO111MODULE=on
   ```

2. 修改代理地址（可选）

   ```shell
   go env -w GOPROXY=https://mirrors.aliyun.com/goproxy/,direct
   # 或者https://goproxy.io,direct
   # 或者https://goproxy.cn,direct
   go env -w GOPROXY=https://goproxy.io,direct
   ```

3. 配置`%GOPATH%\bin`环境变量

4. 关闭https验证（可选）

   ```shell
   git config --global http.sslVerify false
   ```

5. 安装beego

   ```shell
   # beego
   go get github.com/beego/beego/v2
   # bee
   go get github.com/beego/bee/v2
   ```

6. 如果`%GOPATH%\bin`路径下没有生成bee文件，编译一下包

   ```shell
   go install github.com/beego/bee/v2
   ```

   > 从1.18开始，go get不安装了，必须用go install
   >
   > ```plaintext
   > go install github.com/beego/bee/v2@latest
   > ```

7. 验证

   ```shell
   bee version
   ```

   

