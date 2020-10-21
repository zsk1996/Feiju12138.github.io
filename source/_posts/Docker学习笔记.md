---
title: 【笔记】Docker学习笔记
categories:
  - Cloud Computing
date: 2020-09-10 12:03:32
---

## 前言

Docker 是一个开放源代码软件，是一个开放平台，用于开发应用、交付（shipping）应用、运行应用。 Docker允许用户将基础设施（Infrastructure）中的应用单独分割出来，形成更小的颗粒（容器），从而提高交付软件的速度。（[维基百科](https://zh.wikipedia.org/wiki/Docker)）

<!-- more -->

## 安装Docker

### MacOS

``` sh
brew cask install docker
```

### Linux

- 在CentOS安装Docker

#### 下载依赖

``` sh
yum -y install yum-utils device-mapper-persistent-data lvm2
```

#### 设置下载Docker的镜像源（可选）

``` sh
yum-config-manager --add-repo http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
```

#### 安装Docker

``` sh
yum makecache fast
yum -y install docker-ce
```

## 启动Docker

### MacOS

- 直接在启动台打开Docker.app

### Linux

#### 启动服务

``` sh
systemctl start docker
```

#### 设置开机自启

``` sh
systemctl enable docker
```

### 测试是否安装成功

``` sh
docker run hello-world
```

## 中央仓库

- 官方的中央仓库在国外（[https://hub.docker.com](https://hub.docker.com)）
- 国内有镜像网站（例如：[DaoCloud](http://hub.daocloud.io)）
- 公司有私服

### 配置私服

#### Linux

- 编辑`daemon.json`配置文件

``` sh
vim /etc/docker/daemon.json
```

- 修改配置文件

> `<ip>`：私服ip
> `<port>`：私服端口号

``` sh
{
    "registry-mirrors":["https://registry.docker-cn.com"],
    "insecure-registries":["<ip>:<port>"]
}
```

- 重启两个服务

``` sh
systemctl daemon-reload
systemctl restart docker
```

## 镜像操作

### 拉取镜像到本地

> `<name>`：镜像名

``` sh
docker pull <name>
```

#### 指定版本

``` sh
docker pull <name>:<version>
```

### 查看全部的镜像

``` sh
docker images
```

### 删除本地镜像

> `<image_id>`：镜像标识（可以简写）

``` sh
docker rmi <image_id>
```

### 镜像的导入导出（不规范）

#### 导出

> `<src>`：导出的路径
> `<name>`：导出后的文件名

``` sh
docker save -o <src>/<name> <image_id>
```

#### 导入

``` sh
docker load -i <src>/<name>
```

##### 修改导入后的空名称

- 修改导入后默认的名称null

> `:<version>`：版本号（可选）

``` sh
docker tag <image_id> <name_new>:<version>
```

## 容器的操作

### 运行容器

> `<name>:<version>`：镜像名和版本号指定镜像
> `<image_id>`：通过镜像唯一标识指定镜像

``` sh
docker run <name>:<version>

docker run <image_id>
```

#### 参数

> `-d`：后台运行容器
> `-p`：为了映射当前宿主机的端口和容器的端口
>> `<port_out>`：宿主机端口
>> `<port_in>`：容器端口

> `--name`：指定容器名称
>
> > `<name_in>`：容器名称

``` sh
docker run -d -p <port_out>:<port_in> --name <name_in> <name>:<version>

docker run -d -p <port_out>:<port_in> --name <name_in> <image_id>
```

##### mysql在运行时指定初始密码

> `-e`：指定初始密码
> `<password>`：初始密码

``` sh
docker run -d -p <port_out>:<port_in> --name <name_in> -e MYSQL_ROOT_PASSWORD=<password> <image_id>
```

### 查看正在进行的容器

``` sh
docker ps
```

#### 参数

> `-a`：查看所有容器，包括未运行的容器
> `-q`：只查看标识，不查看别的内容

``` sh
docker -aq ps
```

### 启动容器

> `<con_id>`：容器的唯一标识

``` sh
docker start <con_id>
```

### 停止容器

``` sh
docker stop <con_id>
```

#### 停止全部容器

``` sh
docker stop $(docker ps -aq)
```

### 删除容器

- 删除容器之前要停止容器

``` sh
docker rm <con_id>
```

#### 删除全部容器

``` sh
docker rm $(docker ps -aq)
```

### 进入到容器内部

- 不推荐在容器内部进行关闭服务的操作

``` sh
docker exec -it <con_id> bash
```

### 查看容器的日志

> `-f`：滚动查看日志的最后几行

``` sh
docker logs -f <con_id>
```

## 复制宿主机内容到容器内部

> `<file_old>`：宿主机文件的路径及文件名
> `<file_new>`：容器内部文件想要存放的路径名

``` sh
docker cp <file_old> <con_id>:<file_new>
```

## 数据卷

- 将宿主机的一个目录映射到容器的一个目录中
- 可以在宿主机中操作目录中的内容，那么容器内部映射的文件，也会跟着一起改变

### 创建数据卷

- 创建数据卷后，宿主机会产生一个新目录，作为数据卷交换数据的目录

`/var/lib/docker/volumes/<name>/_data`

> `<name>`：数据卷名称

``` sh
docker volume create <name>
```

### 查看数据卷的详细信息

``` sh
docker volume inspect <name>
```

### 查看全部数据卷

``` sh
docker volume ls
```

### 删除数据卷

``` sh
docker volume rm <name>
```

### 映射数据卷

- 类似于挂载操作（将容器内部的指定目录映射到宿主机的指定目录）

> `-v`：指定映射数据卷的参数
>> `<src_out>`：定义一个数据卷在宿主机的存放路径及目录名（如果在这之前没有创建过数据卷，Docker会自动创建目录并将其作为数据卷映射的目录，缺点是不能将当前容器内部的数据同步出来。如果在这之前创建过数据卷，请指定路径为创建数据卷后的默认路径，优点是能将容器内部当前的数据同步出来。所以推荐先手动创建数据卷，再将路径指向新建数据卷后的默认位置）
>> `<src_in>`：想要映射容器内部目录的路径

``` sh
docker run -d -p <port_out>:<port_in> --name <name_in> -v <src_old>:<src_in> <image_id>
```

## 自定义镜像

### 创建一个Dockerfile文件

- 创建一个Dockerfile文件（无扩展名），并且指定自定义镜像信息

### Dockerfile文件的参数

> `from`：指定当前自定义镜像以来的环境
> `copy`：将相对路径下的内容复制到自定义镜像中
> `workdir`：声明镜像默认的工作目录
> `cmd`：需要执行的命令（在workdir下执行，cmd可以写多个但只以最后一个为准）

- 举例：自定义一个tomcat镜像并将自己写的项目部署到comcat中

### 编辑Dockerfile

``` sh
from tomcat
copy 项目名.war /usr/local/tomcat/webapps
```

### 通过命令制作镜像

> `<name>`：自定义的镜像名称，后面可以追加`:版本号`
> `<dockerfile>`：Dockerfile文件存放的的路径

``` sh
docker build -t <name> <dockerfile> 
```

## docker-compose

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a Compose file to configure your application's services. Then, using a single command, you create and start all the services from your configuration. To learn more about all the features of Compose see the list of features.（[Github](https://github.com/docker/compose)）

- 通过docker-compose批量管理Docker容器

### 准备工作

- 添加执行权限

``` sh
chmod +x docker-compose
```

### 配置文件

#### 创建配置文件

- 配置文件要和`docker-compose`在同一目录下

``` sh
touch docker-compose.yml
```

#### 编辑配置文件

``` sh
vim docker-compose.yml
```

#### 修改配置文件

- 同时管理Mysql和Tomcat的配置示例

``` yaml
version: "3.1"
services:
  mysql:
    restart: always
    image: mysql
    container_name: mysql
    ports:
      - 3306:3306
    environment:
      MYSQL_ROOT_PASSWORD: root
      TZ: UTC
  tomcat:
    restart: always
    image: tomcat
    container_name: tomcat
    ports:
      - 8080:8080
    environment:
      TZ: UTC
```

### 启动docker-compose管理的容器

``` sh
docker-compose up
```

#### 以后台启动

``` sh
docker-compose up -d
```

### 关闭并删除docker-compose管理的容器

``` sh
docker-compose down
```

### 开启docker-compose管理的容器

``` sh
docker-compose start
```

### 关闭docker-compose管理的容器

``` sh
docker-compose stop
```

### 重启docker-compose管理的容器

``` sh
docker-compose restart
```

### 查看docker-compose管理的容器

> `-a`：查看所有容器，包括未运行的容器
> `-q`：只查看标识，不查看别的内容

``` sh
docker-compose ps
```

### 查看docker-compose管理的容器日志

> `-f`：滚动查看

``` sh
docker-compose logs -f
```

## 参考文献

[哔哩哔哩——千锋Java学习营](https://www.bilibili.com/video/BV1sK4y1s7Cj)
[菜鸟笔记](https://www.runoob.com/docker/docker-install-mysql.html)
