---
title: 【笔记】搭建Linux的Java项目部署环境
categories:
  - 云计算
date: 2020-09-06 14:44:26
---

## 前言

在`CentOS Linux 7`虚拟机上搭建Java项目部署环境

<!-- more -->

## 安装CentOS Linux系统

- [传送门](/2019/12/10/安装CentOSLinux系统/)

## 配置更新源

- [传送门](/2020/01/31/更换CentOSLinux更新源/)

## 安装git

``` sh
yum install git -y
```

- 查看版本号检测安装成功

``` sh
git --version
```

## 安装jdk

### 安装

- [官网](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)下载`Linux x64 Compressed Archive`

- 检查并删除所有`open jdk`相关软件包

> `<name>`：软件包名

``` sh
rpm -qa | grep java
yum remove <name> -y
```

- 创建java存放目录

``` sh
cd /usr/local/
mkdir java
cd java
```

- 将`.tar.gz`压缩包通过ftp工具上传到服务器并解压

``` sh
tar -zxvf jdk-8u261-linux-x64.tar.gz
rm -f jdk-8u261-linux-x64.tar.gz
```

- 复制路径保留备用

``` sh
cd jdk1.8.0_261/
pwd
```

### 配置环境变量

- 编辑`profile`文件

``` sh
vim /etc/profile
```

- 修改`profile`文件

``` sh
export JAVA_HOME=/usr/local/java/jdk1.8.0_261
export CLASSPATH=$JAVA_HOME/lib/
export PATH=$PATH:$JAVA_HOME/bin/
```

- 更新配置文件

``` sh
source /etc/profile
```

### 完成

- 查看版本号检测安装成功

``` sh
java -version
```

## 安装nodejs

### 安装

- [官网](https://nodejs.org/zh-cn/download/)下载`Linux 二进制文件 (x64)`

- 创建node存放目录

``` sh
cd /usr/local/
mkdir node
cd node/
```

- 将`.tar.xz`压缩包通过ftp工具上传到服务器并解压

``` sh
tar -xJvf node-v12.18.3-linux-x64.tar.xz
rm -f node-v12.18.3-linux-x64.tar.xz
```

- 复制路径保留备用

``` sh
cd node-v12.18.3-linux-x64/
pwd
```

### 配置环境变量

- 编辑`profile`文件

``` sh
vim /etc/profile
```

- 修改`profile`文件

``` sh
export PATH=$PATH:/usr/local/node/node-v12.18.3-linux-x64/bin
```

- 更新配置文件

``` sh
source /etc/profile
```

### 完成

- 查看版本号检测安装成功

``` sh
node --version
npm --version
npx --version
npm version
```

## 安装python3

- 系统自带python2，需要再安装python3

``` sh
python --version
```

### 安装

- [官网](https://www.python.org/downloads/source/)下载`Latest Python 3 Release - Python 3.8.5`

- 创建python3存放目录

``` sh
cd /usr/local/
mkdir python3
cd python3/
```

- 安装编译环境

``` sh
yum install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gcc make -y
```

- 将`.tgz`压缩包通过ftp工具上传到服务器并解压

``` sh
tar -zxvf Python-3.8.5.tgz
rm -f Python-3.8.5.tgz
```

- 编译并安装

``` sh
cd Python-3.8.5/
./configure prefix=/usr/local/python3
make && make install
```

- 添加软链接

``` sh
ln -s /usr/local/python3/bin/python3 /usr/bin/python3
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
```

### 完成

- 查看版本号检测安装成功

``` sh
python3 --version
python --version
```

## 安装maven

### 安装

- [官网](https://maven.apache.org/download.cgi)下载`apache-maven-3.6.3-bin.tar.gz`

- 创建maven存放目录

``` sh
cd /opt/
mkdir maven
cd maven/
```

- 将`.tar.gz`压缩包通过ftp工具上传到服务器并解压

``` sh
tar -zxvf apache-maven-3.6.3-bin.tar.gz
rm -f apache-maven-3.6.3-bin.tar.gz
```

- 复制路径保留备用

``` sh
cd apache-maven-3.6.3/
pwd
```

### 配置maven

- 编辑`setting.xml`文件

``` sh
vim /opt/maven/apache-maven-3.6.3/conf/settings.xml
```

- 修改`setting.xml`文件

[传送门](/2020/08/17/Maven配置远程仓库/)

### 配置环境变量

- 编辑`profile`文件

``` sh
vim /etc/profile
```

- 修改`profile`文件

``` sh
export MAVEN_HOME=/opt/maven/apache-maven-3.6.3
export PATH=$PATH:$MAVEN_HOME/bin
```

- 更新配置文件

``` sh
source /etc/profile
```

### 完成

- 查看版本号检测安装成功

``` sh
mvn --version
```

## 安装mysql

### 安装准备

- [官网](https://downloads.mysql.com/archives/community/)下载`5.7.30`、`Linux - Generic`、`Linux - Generic(glibc 2.12)(x86,64-bit)`、`TAR`

- 检查并删除所有`mariadb`相关软件包

> `<name>`：软件包名

``` sh
rpm -qa | grep mariadb
yum remove <name> -y
```

- 创建mysql存放目录

``` sh
cd /usr/local/
mkdir mysql
cd mysql/
```

- 将`.tar`压缩包通过ftp工具上传到服务器并解压

``` sh
tar -xvf mysql-5.7.30-linux-glibc2.12-x86_64.tar
tar -zxvf mysql-5.7.30-linux-glibc2.12-x86_64.tar.gz
rm -f mysql-5.7.30-linux-glibc2.12-x86_64.tar
rm -f mysql-5.7.30-linux-glibc2.12-x86_64.tar.gz
rm -f mysql-test-5.7.30-linux-glibc2.12-x86_64.tar.gz
```

- 将所有mysql文件挪到`/usr/local/mysql`目录中

``` sh
mv mysql-5.7.30-linux-glibc2.12-x86_64/* .
rm -rf mysql-5.7.30-linux-glibc2.12-x86_64/
```

- 创建用户和用户组

``` sh
groupadd mysql
useradd -g mysql mysql
```

- 修改mysql目录的归属用户

``` sh
chown -R mysql:mysql ./
```

### 配置mysql

- 新建并编辑`my.cnf`文件

``` sh
vim /etc/my.cnf
```

- 修改`my.cnf`文件

``` sh
[client]
# 设置mysql客户端默认字符集
default-character-set = utf8
socket = /var/lib/mysql/mysql.sock

[mysqld]
skip-name-resolve
# 设置3306端口
port = 3306
socket = /var/lib/mysql/mysql.sock
# 设置mysql的安装目录
basedir = /usr/local/mysql
# 设置mysql数据库的数据的存放目录
datadir = /usr/local/mysql/data
# 允许最大连接数
max_connections = 200
# 服务端使用的字符集（默认为8比特编码的latin1字符集）
character-set-server = utf8
# 创建新表时使用的默认存储引擎
default-storage-engine = INNODB
lower_case_table_names = 1
max_allowed_packet = 16M
```

- 创建相关目录并修改权限

``` sh
mkdir /var/lib/mysql
chmod 777 /var/lib/mysql
```

### 正式安装mysql

``` sh
./bin/mysqld --initialize --user=mysql --basedir=/usr/local/mysql --datadir=/usr/local/mysql/data
```

- 完成后会生成临时密码：`root@localhost: y8stx3ad>1Yy`

- 复制启动脚本到资源目录

``` sh
cp ./support-files/mysql.server /etc/init.d/mysqld
```

- 编辑配置

``` sh
vim /etc/init.d/mysqld
```

- 修改配置，为`basedir`和`datadir`指定实际对应目录

``` sh
basedir=/usr/local/mysql
datadir=/usr/local/mysql/data
```

### 设置mysql为系统服务并开机自启

``` sh
chmod +x /etc/init.d/mysqld
chkconfig --add mysqld
chkconfig --list mysqld
```

- 2，3，4，5均为开即可

### 启动mysql

``` sh
service mysqld start
```

### 配置环境变量

- 编辑`profile`文件

``` sh
vim ~/.bash_profile
```

- 修改`profile`文件

``` sh
export path=$PATH:/usr/local/mysql/bin
```

- 更新配置文件

``` sh
source ~/.bash_profile
```

### 完成

- 查看版本号检测安装成功

``` sh
mysql --version
```

### 使用临时密码登陆

``` sh
mysql -u root -p
```

### 修改密码

``` mysql
mysql> alter user user() identified by "123456";
mysql> flush privileges;
```

### 配置远程登陆主机

``` mysql
mysql> use mysql;
mysql> update user set user.Host='%' where user.User='root';
mysql> flush privileges;
```

## 安装redis

### 安装

- 安装软件源

``` sh
yum install epel-release -y
yum update
```

- 通过软件源安装

``` sh
yum install redis -y
```

- 启动redis

``` sh
systemctl start redis
```

### 配置redis

- 编辑`redis.conf`文件

``` sh
vim /etc/redis.conf
```

- 修改`redis.cnf`文件，为`bind 127.0.0.1`这一行加上注释

``` sh
#bind 127.0.0.1
```

- 解除`requirepass`这一行注释，并修改默认密码

``` sh
requirepass 123456
```

- 重启redis

``` sh
systemctl restart redis
```

- 配置开机启动redis

``` sh
systemctl enable redis.service
```

## 安装tomcat

### 安装

- [官网](https://tomcat.apache.org/download-90.cgi)下载`9.0.37`->`Core`->`.tar.gz`

- 创建tomcat存放目录

``` sh
cd /usr/local/
mkdir tomcat
cd tomcat/
```

- 将`.tar.gz`压缩包通过ftp工具上传到服务器并解压

``` sh
tar -zxvf apache-tomcat-9.0.37.tar.gz
rm -f apache-tomcat-9.0.37.tar.gz
```

- 启动tomcat

``` sh
cd apache-tomcat-9.0.37/
./bin/startup.sh
```

### 配置快捷操作和开机自启

``` sh
cd /etc/rc.d/init.d/
touch tomcat
chmod +x tomcat
```

- 编辑脚本

``` sh
vim tomcat
```

- 修改脚本

``` sh
#!/bin/bash
#chkconfig:- 20 90
#description:tomcat
#processname:tomcat
TOMCAT_HOME=/usr/local/tomcat/apache-tomcat-9.0.37
case $1 in
    start) su root $TOMCAT_HOME/bin/startup.sh;;
    stop) su root $TOMCAT_HOME/bin/shutdown.sh;;
    *) echo "require start|stop";;
esac
```

- 使用脚本

``` sh
service tomcat start
service tomcat stop
```

- 加入开机自启

``` sh
chkconfig --add tomcat
chkconfig tomcat on
```

### 配置环境变量使用自带脚本（可选）

- 编辑`profile`文件

``` sh
vim /etc/profile
```

- 修改`profile`文件

``` sh
export PATH=$PATH:/usr/local/tomcat/apache-tomcat-9.0.37/bin
```

- 更新配置文件

``` sh
source /etc/profile
```

- 自带脚本操作

``` sh
catalina.sh start
catalina.sh stop
catalina.sh restart
```

- 查看版本

``` sh
catalina.sh version
```

## 安装nginx

### 安装

- [官网](https://nginx.org/en/download.html)下载`nginx-1.18.0`

- 创建tomcat存放目录

``` sh
cd /usr/local/
mkdir nginx
cd nginx/
```

- 将`.tar.gz`压缩包通过ftp工具上传到服务器并解压

``` sh
tar -zxvf nginx-1.18.0.tar.gz
rm -f nginx-1.18.0.tar.gz
```

- 安装编译环境

``` sh
yum install pcrl-devel openssl openssl-devel -y
```

- 编译安装

``` sh
cd nginx-1.18.0/
./configure
make && make install
```

- 启动nginx

``` sh
/usr/local/nginx/sbin/nginx
```

- 关闭nginx

``` sh
/usr/local/nginx/sbin/nginx -s stop
```

- 重载nginx配置

``` sh
/usr/local/nginx/sbin/nginx -s reload
```

## 关闭防火墙

- 关闭防火墙并关闭开机自启防火墙

``` sh
systemctl stop firewalld.service
systemctl disable firewalld.service
```

## 完成

## 参考文献

程序羊公众号——CodeSheep
[stackoverflow——Ocean Chou](https://stackoverflow.com/questions/61694459/installing-redis-use-install-server-sh)
[知乎——王小鱼](https://zhuanlan.zhihu.com/p/34527270)
