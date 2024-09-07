### 1. 创建数据卷

```shell
docker volume create 数据卷名称
```

创建数据卷之后，默认会存放在目录:`/var/lib/docker/volumes/数据卷名称/_data`



### 2. 查看数据卷详细信息

```shell
docker voleme inspect 数据卷名称
```



### 3. 查看全部数据卷

```shell
docker volume ls
```



### 4. 删除数据卷

```shell
docker volume rm 数据卷名称
```



### 5. 应用数据卷

当映射数据卷时，如果数据卷不存在，Docker会自动创建。

有两种写法，第一种是旧语法，使用`-v`参数映射，第二种新语法，使用`--mount`参数映射。

1. `-v`映射

```shell
docker run -v 数据卷名称:容器内部的路径 镜像id
```

例如：

```shell
docker run -v mydata:/data/test nginx
```

这将直接使用名为 mydata 的数据卷映射到容器的 /data 目录。



2. `--mount`映射

`--mount` 参数是在 Docker 1.13 版本新增的,提供了更丰富的数据卷配置选项。但从简单的映射使用来说,`-v` 参数也可以实现同样的效果。

两者的区别主要在于:

- `-v` 是旧的语法,直接通过卷名映射
- `--mount` 是较新的语法,可以通过source提供配置项

但基本的数据卷映射功能两者都是可以实现的。

所以我们可以混合使用两种语法，比如:

```shell
docker run -v data:/data --mount source=config,target=/etc/nginx nginx
```

这就同时使用 `-v` 和 `--mount` 两种方式来映射不同的数据卷。



### 6. 数据卷和直接映射区别

在运行容器映射目录时可以不适用数据卷，直接将容器目录映射至宿主机目录

1. 直接映射宿主机目录

使用`-v`参数可以直接映射宿主机的一个目录到容器内,例如:

```shell
docker run -v /host/data:/data nginx
```

这会直接将宿主机的/host/data目录映射到容器的/data目录。



2. 使用数据卷映射

使用`--mount`参数可以将一个数据卷挂载到容器内,例如:

```shell
docker run --mount source=mydata,target=/data nginx
```

这会将名为mydata的数据卷挂载到容器的/data目录。

两者的主要区别是:

- 直接映射会将宿主机目录直接映射到容器内,任何对容器内数据的修改都会直接作用在宿主机上。
- 数据卷创建一个独立的主机外的数据环境,对容器内数据的修改不会对宿主机产生影响,但也可以通过mount主机目录到数据卷中来实现宿主机访问。
- 数据卷可以在容器之间共享和重用,直接映射的目录无法多个容器共享。

所以一般来说,如果只是为了单个容器访问宿主机目录,直接映射更简单。如果需要在多个容器间共享数据,建议使用数据卷。