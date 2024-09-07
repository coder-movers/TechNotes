# Dockerfile

Dockerfile 是用于构建 Docker 镜像的文本文件，其中包含了一系列指令，用于描述如何组装镜像。下面是一个详细的 Dockerfile 教程，涵盖了常用的指令和最佳实践。

## 基础结构

一个简单的 Dockerfile 通常包含以下几个部分：

```dockerfile
# 设置基础镜像
FROM base_image:tag

# 维护者信息
MAINTAINER author_name <author_email>

# 安装依赖
RUN apt-get update && apt-get install -y package_name

# 设置工作目录
WORKDIR /app

# 复制本地文件到镜像中
COPY src /app/src

# 暴露端口
EXPOSE 80

# 定义环境变量
ENV ENV_NAME value

# 启动应用
CMD ["executable", "param1", "param2"]
```

## 常用指令详解

### FROM

指定基础镜像，可以是官方镜像（如 `ubuntu`, `alpine`）或其他自定义镜像。

```dockerfile
FROM ubuntu:latest
```

### MAINTAINER

设置维护者信息。

```dockerfile
MAINTAINER Your Name <your.email@example.com>
```

### RUN

在镜像中运行命令，可以用于安装软件包等。

```dockerfile
RUN apt-get update && apt-get install -y package_name
```

### WORKDIR

设置工作目录，后续的指令都会在这个目录下执行。

```dockerfile
WORKDIR /app
```

### COPY

将本地文件复制到镜像中。

```dockerfile
COPY src /app/src
```

### EXPOSE

声明容器运行时监听的端口，但并不会自动映射到宿主机。

```dockerfile
EXPOSE 80
```

### ENV

设置环境变量。

```dockerfile
ENV ENV_NAME value
```

### CMD

定义容器启动时运行的命令。

```dockerfile
CMD ["executable", "param1", "param2"]
```



## 构建镜像

使用 `docker build` 命令构建镜像，以下是一个示例：

```bash
docker build -t image_name:tag .
```

其中，`-t` 指定了镜像的名称和标签，`.` 表示 Dockerfile 所在的当前目录。



## 运行容器

使用 `docker run` 命令运行容器，以下是一个示例：

```bash
docker run -p 8080:80 -d image_name:tag
```

其中，`-p` 指定了宿主机端口和容器端口的映射关系，`-d` 表示在后台运行容器。



## 自定义镜像示例1

假设要构建一个基于 Node.js 的 Web 应用。

```dockerfile
# 使用官方 Node.js 镜像作为基础镜像
FROM node:14

# 设置工作目录
WORKDIR /app

# 复制 package.json 和 package-lock.json 到工作目录
COPY package*.json ./

# 安装应用依赖
RUN npm install

# 复制应用程序代码到工作目录
COPY . .

# 暴露应用监听的端口
EXPOSE 3000

# 定义环境变量，可以在运行时覆盖
ENV NODE_ENV=production

# 启动应用
CMD ["npm", "start"]
```

### 构建镜像

使用以下命令构建镜像：

```bash
docker build -t my-node-app:1.0 .
```

### 运行容器

运行容器，并将宿主机的端口映射到容器内的端口：

```bash
docker run -p 8080:3000 -d my-node-app:1.0
```

假设 Node.js 应用监听在容器的 3000 端口，映射到宿主机的 8080 端口。



## 自定义镜像示例2

```dockerfile
# 设置基础镜像
FROM python:3.9

# 设置工作目录
WORKDIR /app

# 复制项目文件到容器中
COPY . /app

# 安装项目依赖
RUN pip install --no-cache-dir -r requirements.txt

# 暴露容器端口
EXPOSE 5810

# 运行应用程序
CMD ["gunicorn", "app:app", "--bind", "0.0.0.0:5810", "--workers", "4", "--log-level", "info"]
```

