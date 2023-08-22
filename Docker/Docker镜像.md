### docker搭建私服

#### 1. 修改注册文件

修改/etc/docker/daemon.json文件，若文件不存在，则手动创建

添加如下内容

```json
{
    "registry-mirrors":["http://docker-cn.com"], // 镜像源
    "insecure-registries":["ip:port"] // 替换相应ip和端口号
}
```

#### 2. 重启服务

```shell
systemctl daemon-reload
systemctl restart docker
```



### 镜像倒入导入（不规范）

将本地的镜像导出

```shell
docker save -o 导出的路径 镜像id
```

加载本地的镜像文件

```shell
docker load -i 镜像文件
```



### 修改镜像名称

```shell
docker tag 镜像id 新名称:版本
```



### 运行容器时参数

```shell
docker run -d -p 宿主机端口:容器端口 --name 容器名称 镜像的标识 镜像的名称[:tag]
```

- `-d`：代表后台运行
- `--name `容器名称：指定容器的名称



### 查看容器日志

```shell
docker logs -f 容器id
```



### 进入容器内部

```shell
docker exec -it 容器id bash
```

