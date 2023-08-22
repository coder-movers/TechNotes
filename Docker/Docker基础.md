### CentOS7安装docker

```properties
#安装(-y: 使用默认配置)
yum install -y docker

#查看是否安装成功
yum list installed | grep docker

#启动
systemctl start docker

#设置开机自启
systemctl enable docker
```



#### CentOS 8 异常处理

**CentOS8 运行docker报错`Emulate Docker CLI using podman. Create /etc/containers/nodocker to quiet msg.`**

> 原因：
>
> Centos 8执行`yum install docker`默认安装的是podman-docker

- 基本命令

  > 和docker命令使用基本一致

  ```shell
  # 创建容器
  podman create nginx
  
  # 启动容器
  podman start 79c842403792
  
  # 起别名
  alias podman=docker
  ```



### Ubuntu 安装docker

使用官方脚本自动安装

```shell
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```

也可使用也可以使用国内 daocloud 一键安装命令：

```shell
curl -sSL https://get.daocloud.io/docker | sh
```



### docker基本命令

```properties
#启动
systemctl start docker

#重启
systemctl restart docker

#停止
systemctl stop docker

#开机自启
systemctl enable docker

#状态查看
systemctl status docker

# 显示docker的版本信息
docker version

# 显示docker的系统信息，包括镜像和容器的数量
docker info

# 帮助命令
docker 命令xxx  --help   
```

### docker使用

```properties
#查看所有命令
docker

#获取目标镜像(docker pull 镜像名)
docker pull ubuntu 

#以命令行模式进入容器
docker run -it ubuntu /bin/bash

#查看所有的容器命令(-a 表示所有)
docker ps -a

#查看正在运行的容器
docker ps

#启动容器(通过容器id启动)
docker start 188b93882e3a

#后台运行(后台运行后默认不进入容器-d)
docker run -itd --name ubuntu-test ubuntu /bin/bash

#停止容器
docker stop 188b93882e3a

#重启容器
docker restart 188b93882e3a 

#查看容器完整command
docker ps -a --no-trunc

#进入容器①不推荐,从容器中退出会导致容器停止
docker attach 188b93882e3a

#进入容器②推荐，从容器中退出不会导致容器停止
docker exec -it 188b93882e3a /bin/bash

#导出容器(导出容器1e560fca3906快照到本地文件ubuntu.tar)
docker export 1e560fca3906 > ubuntu.tar

#导入容器快照①(将快照文件 ubuntu.tar 导入到镜像 test/ubuntu:v1:)
cat docker/ubuntu.tar | docker import - test/ubuntu:v1

#导入容器快照②(通过指定url或某个目录来导入)
docker import http://example.com/exampleimage.tgz example/imagerepo

#删除容器
docker rm -f 5ea0a2be12ee

#清理所有处于终止状态的容器
docker container prune
```



### docker容器设置开机自启动

- 创建容器时

  ```shell
  docker run --restart=on-failure:10 容器名
  ```

  > ```
  > --restart 具体参数值详细信息
  >     no - 容器退出时，不重启容器
  >     on-failure - 只有在非0状态退出时才从新启动容器(指定 Docker 将尝试重新启动容器的最大次数；默认情况下，Docker 将尝试永远重新启动容器)
  >     always - 无论退出状态是如何，都重启容器
  > ```

- 创建时未指定，通过update命令修改

  ```shell
  docker update --restart=always 容器ID
  ```



### docker查看某个容器日志

命令格式：(OPTIONS为可选参数，可不填；CONTAINER是容器id或容器名)

```shell
docker logs [OPTIONS] CONTAINER
```

> 参数说明：
>
> ```shell
> Options:
>     --details        显示更多的信息
>     -f, --follow         跟踪实时日志
>     --since string   显示自某个timestamp之后的日志，或相对时间，如42m（即42分钟）
>     --tail string    从日志末尾显示多少行日志， 默认是all
>     -t, --timestamps     显示时间戳
>     --until string   显示自某个timestamp之前的日志，或相对时间，如42m（即42分钟）
> ```

例子：(容器Id:`dd57c98422a3`)

1. 查看指定时间后的日志，只显示最后100行：

   ```shell
   docker logs -f -t --since="2021-08-05" --tail=100 dd57c98422a3
   ```

2. 查看最近30分钟的日志:

   ```shell
   docker logs --since 30m dd57c98422a3
   ```

3. 查看某时间之后的日志：

   ```shell
   docker logs -t --since="2021-08-05T08:23:37" dd57c98422a3
   ```

4. 查看某时间段日志：

   ```shell
   docker logs -t --since="2021-08-05T08:23:37" --until "2018-02-09T12:23:37" dd57c98422a3
   ```



### docker镜像

```properties
#列出镜像列表
docker images

#运行镜像(-i: 交互式操作。-t: 终端。)
docker run -t -i ubuntu:15.10 /bin/bash

#搜索镜像(搜索名为httpd的镜像)(NAME: 镜像仓库源的名称)(DESCRIPTION: 镜像的描述)(OFFICIAL: 是否 docker 官方发布)(stars: 类似 Github 里面的 star，表示点赞、喜欢的意思)(AUTOMATED: 自动构建。)
docker search httpd

#下载镜像(拉取镜像)
docker pull httpd

#删除镜像
docker rmi hello-world

#镜像名相同时选择某一镜像删除(REPOSITORY:镜像名)(TAG:标签名)
docker rmi  REPOSITORY:TAG

#登录镜像仓库/登出镜像仓库
docker login/logout
```



### docker切换镜像地址

​	**提升拉取镜像速度**

```properties
#进入设置
vi /etc/docker/daemon.json

#添加
{ "registry-mirrors": ["https://m2lv5yea.mirror.aliyuncs.com"]}

#保存退出后，输入
systemctl daemon-reload

#重启镜像
systemctl restart docker
```



### docker拉取MySQL

```properties
# 拉取官方版最新镜像
docker pull mysql:latest

# 查看本地镜像(查看是否安装)
docker images

# 运行MySQL镜像(-p 3306:3306 ：映射容器服务的 3306 端口到宿主机的 3306 端口，外部主机可以直接通过 宿主机ip:3306 访问到 MySQL 的服务。)(MYSQL_ROOT_PASSWORD=123456：设置 MySQL 服务 root 用户的密码。lower_case_table_names 数据库表名不区分大小写 ;--ulimit nofile=65536:65536 接触最大连接数限制)
#创建一个名为mysql-test的容器并运行
docker run -itd --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=root mysql --lower_case_table_names=1 --ulimit nofile=65536:65536

# 查看容器启动情况
docker ps
```

#### MySQL相关配置

**docker的MySQL所有用户权限配置**

```shell
# 进入容器(mysql:容器id或容器名)
docker exec -it mysql bash

# 进入mysql
mysql -u root -p

# 配置mysql 1.远程连接授权(如下命令对所有IP进行root账户授权)(mysql命令必须以分号结束)
GRANT ALL ON *.* TO 'root'@'%';

# 配置mysql 2.修改密码过期策略（PASSWORD EXPIRE NEVER：密码不过期）
ALTER USER 'root'@'%' IDENTIFIED BY 'password' PASSWORD EXPIRE NEVER;

# 配置mysql 3.更改root密码
ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY '123456'; 

# 配置mysql 4.刷新权限
flush privileges;

# 配置mysql 5.查看用户信息，确认配置成功
select host,user,plugin,authentication_string from mysql.user;

# 退出
exit
```



**docker的MySQL创建用户并分配权限**

```shell
# 进入容器(mysql:容器id或容器名)
docker exec -it mysql bash

# 进入mysql
mysql -u root -p

# 创建用户
CREATE USER 'cloud'@'%' IDENTIFIED BY 'cloud';

# 授权所有权限
GRANT ALL ON *.* TO 'cloud'@'%';

# 刷新权限
flush privileges;

# 退出
exit
```



**docker的MySQL修改用户权限相关操作**

```shell
# 查询所有用户权限
select user,host from mysql.user;

# 展示cloud用户所有权限
show grants for 'cloud'@'%';

# 移除用户所有权限
revoke ALL ON *.* FROM 'cloud'@'%';

# 单个数据库授权
GRANT ALL ON kcloud.* TO 'cloud'@'%';

# 删除用户
drop user 'cloud'@'%';

# 刷新权限
flush privileges;

```

> ```shell
> GRANT
>   [权限] 
> ON [库.表] 
> TO [用户名]@[IP] 
> ```
>
> GRANT命令说明：
> (1)`ALL PRIVILEGES` 表示所有权限，你也可以使用select、update等权限。
> (2)`ON` 用来指定权限针对哪些库和表。
> (3)`*.*` 中前面的*号用来指定数据库名，后面的*号用来指定表名。
> (4)`TO` 表示将权限赋予某个用户。
> (5)`@` 前面表示用户，@后面接限制的主机，可以是IP、IP段、域名以及%，%表示任何地方。
> (6)`WITH GRANT OPTION` 这个选项表示该用户可以将自己拥有的权限授权给别人。
>
> 注意：经常有人在创建操作用户的时候不指定WITH GRANT OPTION选项导致后来该用户不能使用GRANT命令创建用户或者给其它用户授权。
> 备注：可以使用GRANT重复给用户添加权限，权限叠加，比如你先给用户添加一个select权限，然后又给用户添加一个insert权限，那么该用户就同时拥有了select和insert权限。



**docker 的 MySQL 查看设置是否为不区分大小写**

> 修改my.cnf文件方式无法修改不区分大小写配置，仅在初始创建mysql容器时可设置不区分大小写

1. 进入容器

   ```shell
   docker exec -it mysql-latest bash
   ```

2. 登入MySQL

   ```shell
   mysql -u 用户名 -p 密码
   ```

3. 查看大小写配置

   ```shell
   show global variables like '%lower_case%';
   ```

   > lower_case_file_system
   > 表示当前系统文件是否大小写敏感，只读参数，无法修改。
   > ON 大小写不敏感
   > OFF 大小写敏感



#### MySQL异常处理

**docker容器中修改了MySQL的配置导致容器无法启动**

1. 查看容器日志，定位错误

   ```shell
   docker logs dd57c98422a3
   ```

2. 将出错的配置文件复制出来

   ```shell
   docker cp dd57c98422a3:/etc/mysql/my.cnf .
   ```

3. 修改成正确配置文件并保存

   ```shell
   vi my.cnf
   ```

4. 将修改完的文件复制回容器

   ```shell
   docker cp my.cnf dd57c98422a3:/etc/mysql/my.cnf
   ```

5. 重启容器

   ```shell
   docker restart dd57c98422a3
   ```



**docker修改未启动容器的配置信息**

> 修改mysql中my.cnf文件导致容器启动失败，进入容器还原设置

1. 进入docker 所有容器配置文件目录

   ```shell
   cd /var/lib/docker/overlay2
   ```

2. 查找指定配置文件

   ```shell
   find ./ -name my.cnf
   ```

3. 修改配置错误的文件

   ```shell
   vim ./b1755a6e3ee40ea474cebea54203c66c1d0a873cc9de1bedf04ae557a918b0fa/diff/etc/mysql/my.cnf
   ```

4. 重启容器

   ```shell
   docker restart mysql
   ```

   

### docker重启MySQL、Oracle服务

```properties
#查看容器
docker ps -a

#重新启动MySQL容器
docker restart bd14b4db22c3
```



### docker异常处理

**docker解决`Too many connections`**

方法一：创建容器时

```shell
# 创建容器并启动时追加参数
--ulimit nofile=65536:65536
```

方法二： 容器创建后

1. 接触限制

   ```shell
   # 在宿主机
   vim /etc/init.d/docker
   
   # 在文件开始部分加入以下代码
   ulimit -u 65536 -HSn 65536
   
   # 保存并退出
   ```

2. 修改最大连接数

   ```shell
   # 进入mysql容器，登陆
   # 查看最大连接数
   SHOW VARIABLES LIKE '%max_con%';
   
   # 设置最大连接数
   SET GLOBAL max_connections = 10000;
   
   # 设置超时时间
   SET GLOBAL wait_timeout = 600;
   SET GLOBAL interactive_timeout = 600;
   ```

   

### docker拉取Oracle

```properties
#拉取镜像(helowin是服务名(阿里云镜像)
docker pull registry.cn-hangzhou.aliyuncs.com/helowin/oracle_11g

#查看镜像
docker images

#创建并运行容器
docker run -d -p 1521:1521 --name oracle11g registry.cn-hangzhou.aliyuncs.com/helowin/oracle_11g

#查看容器是否运行
docker ps

#进入容器，进入容器后前缀由root变为oracle
#([root@izbp1dkb1fatetprkwsgpxz ~]# docker exec -it oracle bash)
#([oracle@a1aaa3feef10 /]$ )
docker exec -it oracle11g bash
 
#切换回root用户,密码是helowin
su root

#编辑环境变量(通过vi /etc/profile命令进入配置文件编辑器)
vi /etc/profile

#编辑配置文件，在文件末尾添加(注意：按i或按a进入编辑模式，添加后，按ESC键退出编辑模式，再输入:wq!保存退出)
export ORACLE_HOME=/home/oracle/app/oracle/product/11.2.0/dbhome_2
export ORACLE_SID=helowin
export PATH=$ORACLE_HOME/bin:$PATH

#保存配置并生效(在root用户下输入)
source /etc/profile

#创建软链接
ln -s $ORACLE_HOME/bin/sqlplus /usr/bin

#切换到oracle用户
su - oracle

#进入sql命令行
sqlplus /nolog

#配置oracle用户
SQL> conn / as  sysdba                           ## 使用sysdba 连接oracle，最大权限，os认证，只能在本机上登陆使用。
Connected.

SQL> alter user system identified by system;          ## 修改用户 system 的密码为 oracle ，可以自定义
User altered.

SQL> alter user sys identified by sys;
User altered.

SQL> create user ETS identified by ETS;
User created.

SQL> grant connect,resource,dba to ETS;
Grant succeeded.

SQL> exit     										 ##退出编辑SQL
Disconnected from Oracle Database 11g Enterprise Edition Release 11.2.0.1.0 - 64bit Production
With the Partitioning, OLAP, Data Mining and Real Application Testing options

#回到root用户
exit

#用Nacicat连接
账号system密码system服务名helowin
```



### docker拉取redis

1. 拉取官方镜像

   ```shell
   docker pull redis:latest
   ```

2. 查看已安装镜像

   ```shell
   docker images
   ```

3. 运行容器并设置密码

   ```shell
   docker run -itd --name redis -p 6379:6379 redis --requirepass "123456"
   ```

   > 为现有redis设置密码或修改密码
   >
   > ```shell
   > # ①进入redis容器
   > docker exec -it redis bash
   > 
   > # ②调用命令行
   > redis-cli
   > 
   > # ③查看现有redis密码
   > config get requirepass
   > 
   > # ④修改redis密码
   > config set requirepass "123456"
   > ```
   >
   > 如出现`(error) NOAUTH Authentication required.`
   >
   > ```shell
   > # 验证密码
   > auth 原密码
   > ```



### docker拉取db2

- **拉取镜像**(默认拉取最新版)

  ```shell
  docker pull ibmcom/db2
  ```

- **查看镜像**

  ```shell
  docker images
  ```
  
- **创建容器并运行**

  1. 运行

     ```shell
     docker run -d -it -p 50000:50000 --name mydb2 --privileged=true -e DB2INST1_PASSWORD=db2inst1 -e LICENSE=accept -e DBNAME=uatdb -v /usr/database/db2:/db2data ibmcom/db2
     ```

  2. 参数说明：

     ```yaml
         -d                                   # 表示在后台启动容器
         -p 50000:50000                       # 指定容器访问端口 （容器外:容器内）
      --name mydb2                         # 指定容器名称
         --privileged=true                    # 使得容器内 root 拥有真正的 root 权限
      -e LICENSE=accept                    # 接受协议
         -e DB2INST1_PASSWORD=mydb2pass       # 设置内置实例用户 db2inst1 的密码为 mydb2pass
         -e DBNAME=uatdb                     # 容器启动时自动创建一个名为 uatdb 的数据库，不指定不创建
         -v /usr/database/db2:/db2data     # 磁盘挂载（容器外:容器内）
         ibmcom/db2                           # 镜像名称
     ```





### docker拉取Tomcat

1. 拉取镜像

   ```properties
   docker pull tomcat:8.5.35
   ```

2. 查看本地镜像

   ```properties
   docker images
   ```

3. 启动镜像并新建容器(-v /etc/localtime:/etc/localtime:ro  表示让容器使用宿主机的时间时区)

   ```properties
   docker run --name tomcat8080 -v /etc/localtime:/etc/localtime:ro -d -p 8080:8080  6759d91a032b
   ```

4. 进入容器

   ```properties
   docker exec -it tomcat8080 /bin/bash
   ```



### docker拉取nacos

1. 拉取镜像

   ```shell
   docker pull nacos/nacos-server
   ```

2. 启动容器

   ```shell
   docker run -d -p 8848:8848 -p 9848:9848 --env MODE=standalone --name nacos nacos/nacos-server
   ```

3. 在网页运行nacos（`http://ip地址:8848/nacos`）

   如`http://127.0.0.1:8848/nacos`

   默认用户名密码都是：nacos

#### Nacos异常处理

**启动项目nacos报错：`Client not connected,current status:STARTING`**

​	这是因为nacos版本2.X之后加了一个grpc的远程通信端口，所以在你的<code>docker run</code> 原命令之上再加一个 9848的端口进行映射就可以了。

原命令：

```shell
docker run -d -p 8848:8848 --env MODE=standalone --name nacos  nacos/nacos-server
```

改为：

```shell
docker run -d -p 8848:8848 -p 9848:9848 --env MODE=standalone --name nacos nacos/nacos-server
```



### docker拉取nginx

1. 拉取镜像

   ```shell
   docker pull nginx
   ```

2. 创建容器

   ```shell
   docker run --name nginx -p 8080:80 -d nginx
   ```

3. 测试连接

   > 网页直接访问`域名:8080`
   >
   > 出现`Welcome to nginx!`页面即连接成功
   >
   > 如连接不上则为宿主机防火墙拦截，宿主机开启8080端口访问即可

4. 配置项目

   1. 宿主机创建目录

      ```shell
      mkdir -p /root/nginx/html /root/nginx/logs /root/nginx/conf
      ```

   2. 将nginx容器中关键目录copy到宿主机

      ```shell
      docker cp nginx:/etc/nginx/nginx.conf /root/nginx/conf
      ```

   3. 删除原nginx容器并重新创建新容器，并将`html`，`logs`，`conf`目录映射到宿主机

      ```shell
      docker run --name nginx -p 8080:80 -v /root/nginx/html:/usr/share/nginx/html -v /root/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v /root/nginx/logs:/var/log/nginx -d nginx
      ```

   4. 将打包好的项目内容放入`/root/nginx/html`目录下

      > 网页直接访问`域名:8080`即可访问项目



### docker拉取jenkins

1. 拉取镜像

   ```shell
   docker pull jenkins/jenkins
   ```

2. 创建宿主机映射目录

   ```shell
   mkdir -p /root/jenkins
   ```

3. 启动容器

   ```shell
   docker run --name jenkins -p 10240:8080 -p 10241:50000 -v /root/jenkins:/var/jenkins_home -v /etc/localtime:/etc/localtime -d jenkins/jenkins
   ```

   > 容器运行失败：
   >
   > ```shell
   > # 查看日志
   > docker logs jenkins
   > 
   > # 报错信息
   > touch: cannot touch ‘/var/jenkins_home/copy_reference_file.log’: Permission denied
   > Can not write to /var/jenkins_home/copy_reference_file.log. Wrong volume permissions?
   > ```
   >
   > 原因：
   >
   > > 需要修改下目录权限, 因为当映射本地数据卷时，/root/jenkins目录的拥有者为root用户，而容器中jenkins user的uid为1000
   >
   > 解决办法：
   >
   > ```shell
   > sudo chown -R 1000:1000 /root/jenkins
   > ```

4. 配置镜像加速

   ```shell
   # 进入映射目录
   cd /root/jenkins
   
   # 修改配置文件
   vi  hudson.model.UpdateCenter.xml
   
   # url替换成清华大学镜像
   https://mirrors.tuna.tsinghua.edu.cn/jenkins/updates/update-center.json
   ```

5. ip:10240访问jenkins页面

6. 获取管理员密码

   ```shell
   cat /root/jenkins/secrets/initialAdminPassword
   ```

7. 安装推荐插件

   >安装报错重启jenkins：
   >
   >```shell
   ># 访问地址
   >http://yourhost:10240/restart
   >```



### docker拉取mongodb

1. 拉取镜像

   ```shell
   docker pull mongo
   ```

2. 运行容器

   ```shell
   docker run -itd --name mongo -p 27127:27017 mongo
   ```

3. 创建管理员用户，设置密码

   ```shell
   # 用admin账户进入容器
   docker exec -it mongo bash

   # 打开mongo命令行
   mongo
   
   # 使用admin权限
   use admin
   
   # 创建管理员账户(不能创建数据库)
   db.createUser({ user: "admin", pwd: "123456", roles: [{ role: "userAdminAnyDatabase", db: "admin"}]});
   
   # 创建超级管理员(可以创建数据库)
   db.createUser({ user: "root", pwd: "123456", roles: [{ role: "root", db: "admin"}]});
   
   # 退出
   exit
   ```
   
4. 创建普通用户，设置密码

   ```shell
   # 登陆admin数据库
   mongo admin
   
   # root管理员登陆
   db.auth('root','123456');
   
   # 创建名为test的数据库
   use test
   
   # 查看是否有名为test数据库，结果是没有的
   show dbs;
   
   # 需要往里面添加数据，test才会生成
   db.createCollection("list");
   
   # 查看是否有test数据库，结果是有的
   show dbs;
   
   #退出
   exit
   ```

#### MongDB异常处理

**docker的MongoDB报错`serverSelectionTimeoutMS`**

服务器防火墙未开启



**docker的MongoDB报错`Authentication failed`**

```shell
# 用admin账户进入容器
docker exec -it mongo bash

# 进行mongo 初始化认证
mongod --auth --dbpath=/data/db --logpath=/data/log

# 使用超级管理员账户登录admin数据库
mongo admin -u root -p 123456

# 进入test
use test

# 创建test数据库的管理员
db.createUser({user: "test", pwd: "test", roles:["dbOwner"]})

# 退出
exit
```



**服务器异常关机重启后，docker的MongoDB启动异常，无法正常启动**

```shell
# 查看启动日志
docker logs 容器id

# 出现以下错误，是因为/tmp/mongodb-27017.sock这个文件没有操作权限
[initandlisten] Failed to unlink socket file /tmp/mongodb-27017.sock errno:1 Operation not permitted

# 解决办法：
# 进入后台文件元信息管理
docker inspect 容器id

# 在GraphDriver的Data中找到以下内容
"MergedDir": "/var/lib/docker/overlay2/a904530be8190626a822524570efe5c29d3afb744b99112b4fbf153bcae2b3d225/merged",

# 进入该目录
cd /var/lib/docker/overlay2/a904530be8190626a822524570efe5c29d3afb744b99112b4fbf153bcae2b3d225

cd diff/tmp/

# 目录中有mongodb-27017.sock，删除该文件
sudo rm -rf  mongodb-27017.sock

# 重启容器
docker restart 容器id
```