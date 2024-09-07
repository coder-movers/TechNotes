## 什么是 Docker Compose？

Docker Compose 是一个用于定义和运行多容器 Docker 应用程序的工具。通过使用单个文件来配置应用程序的服务、网络和卷，可以简化容器化应用的部署过程。

## 安装 Docker Compose

在开始之前，确保已经安装了 Docker。然后，按照以下步骤安装 Docker Compose：

```bash
# 安装 Docker Compose
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

# 赋予执行权限
sudo chmod +x /usr/local/bin/docker-compose

# 检查安装是否成功
docker-compose --version
```

## 编写 Docker Compose 文件

创建一个名为 `docker-compose.yml` 的文件，用于定义 Docker 应用程序的服务、网络和卷。以下是一个简单的示例：

```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
```

上述示例定义了两个服务：`web` 和 `db`。`web` 服务使用最新版本的 Nginx 镜像，并将容器的 80 端口映射到主机的 8080 端口。`db` 服务使用 MySQL 5.7 镜像，并设置了 MySQL 根密码。



## 相关命令

### 启动

```bash
docker-compose up
```

如果需要在后台运行，可以使用 `-d` 选项：

```bash
docker-compose up -d
```

### 关闭并删除

要停止应用程序并删除相关的容器，使用以下命令：

```bash
docker-compose down
```

> 只是删除容器，镜像还在

### 开启/停止/重启

```shell
docker-compose start|stop|restart
```

### 查看由docker compose管理的容器

```shell
docker-compose ps
```

### 查看日志

```shell
docker-compose logs -f
```



## Docker Compose 文件语法

Docker Compose 使用 YAML（YAML Ain't Markup Language）语言来定义应用程序的配置。以下是一些常见的 Docker Compose 文件语法规则：

1. **版本号：** 指定 Docker Compose 文件格式的版本。在文件的顶层，使用 `version` 关键字指定版本，例如 `version: '3'`。

2. **服务定义：** 使用 `services` 关键字定义应用程序中的各个服务。每个服务都是一个字典，其中包含有关该服务的配置信息，例如镜像、端口映射等。

   ```yaml
   services:
     web:
       image: nginx:latest
       ports:
         - "8080:80"
     db:
       image: mysql:5.7
       environment:
         MYSQL_ROOT_PASSWORD: example
   ```

3. **镜像：** 使用 `image` 关键字指定服务所使用的 Docker 镜像。

4. **端口映射：** 使用 `ports` 关键字定义容器端口与主机端口之间的映射关系。

5. **环境变量：** 使用 `environment` 关键字设置服务所需的环境变量。

6. **网络：** 使用 `networks` 关键字定义自定义网络，服务可以连接到指定的网络。

   ```yaml
   networks:
     custom_network:
   ```

7. **卷：** 使用 `volumes` 关键字定义卷，以便在容器和主机之间共享数据。

   ```yaml
   volumes:
     - /path/on/host:/path/in/container
   ```

8. **扩展性：** Docker Compose 文件支持变量和扩展，可以使用 `${VARIABLE}` 形式的变量，并在文件的顶部定义它们。

   ```yaml
   version: '3'
   services:
     web:
       image: nginx:${NGINX_VERSION}
   ```



## 和Dockerfile结合使用

使用docker-compose.yml文件，以及Dockerfile文件在生成自定义镜像的同时启动当前镜像，并且由
docker-compose去管理容器

示例：

```yaml
version: '3.8'
services:
  web-demo:
    restart: always
    build:							#构建自定义镜像
      context: ..					#指定Dockerfile文件所在路径
      dockerfile: Dockerfile		#指定Dockerfile文件名称
    image: demo:1.0                 #指定镜像名
    container_name: demo            #指定容器名
    ports:
     - "8081:8080"
    environment:
     TZ: Asia/Shanghai
```



## 和k8s区别

Docker Compose 和 Kubernetes 都是容器编排工具，但它们有一些关键的区别：

1. **范围和复杂性：**
   - **Docker Compose：** 适用于开发和测试环境，对于较小规模的应用程序和单个主机来说是一个简单的解决方案。Compose 更加轻量，易于使用，但在大规模和生产环境中的可扩展性相对有限。
   - **Kubernetes：** 面向生产环境，适用于大规模、复杂的应用程序。Kubernetes 提供了更多的功能，包括自动伸缩、服务发现、负载均衡等，以确保在生产环境中能够管理大规模、高可用性的应用。

2. **编排模型：**
   - **Docker Compose：** 使用声明性的、基于文件的方法来定义应用程序架构，以及如何运行每个服务。它更加直观和简单。
   - **Kubernetes：** 使用声明性配置，但是它采用了更为复杂的控制器和对象模型，例如 Pod、Deployment、Service 等，以提供更高级的容器编排功能。

3. **可扩展性：**
   - **Docker Compose：** 主要关注于本地开发和测试，可扩展性相对有限。
   - **Kubernetes：** 面向大规模分布式系统，具有高度的可扩展性和灵活性，适用于各种规模的应用程序。

4. **生态系统：**
   - **Docker Compose：** 主要关联于 Docker 生态系统，直接支持 Docker 镜像。
   - **Kubernetes：** 是一个独立的容器编排平台，支持多种容器运行时，并且与多个云服务提供商和工具有更紧密的集成。

Docker Compose 更适合在开发和测试较小规模的应用程序时使用。如果应用需要在生产环境中部署，并具有复杂的要求和高度的可扩展性，那么 Kubernetes 是更合适的选择。