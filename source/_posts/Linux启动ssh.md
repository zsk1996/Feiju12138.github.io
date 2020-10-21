---
title: 【笔记】Linux 启动 ssh
categories:
  - Linux
date: 2020-01-31 16:36:04
---

## 前言

在`Linux`启动`ssh`服务

<!-- more -->

## RedHat系列

### 安装 openssh

``` sh
yum install openssh-server
```

### 修改配置

#### 编辑配置文件

``` sh
vim /etc/ssh/sshd_config
```

#### 去除端口号注释

``` sh
Port 22
```

#### 去除监听地址注释

``` sh
ListenAddress 0.0.0.0
ListenAddress ::
```

#### 允许远程登录

``` sh
PermitRootLogin yes
```

#### 允许使用密码验证身份

``` sh
PasswordAuthentication yes
```

### 启动 sshd 服务

``` sh
sudo service sshd start
```

## Debian系列

### 安装 openssh

``` sh
apt-get install openssh-client
apt-get install openssh-server
```

### 编辑配置文件

``` sh
vim /etc/ssh/sshd_config
```

### 修改配置文件

#### 去除端口号注释

``` sh
Port 22
```

#### 去除监听地址注释

``` sh
ListenAddress 0.0.0.0
ListenAddress ::
```

#### 允许远程登录

- 去掉`PermitRootLogin without-password`前面的`#`并修改为`PermitRootLogin yes`

Kali要严格的将`PermitRootLogin prohibit-password`改为`PermitRootLogin yes`才能实现远程使用root身份登陆

``` sh
PermitRootLogin yes
```

### 重启 ssh 服务

``` sh
/etc/init.d/ssh restart
service ssh restart
```

### 查看 ssh 状态

``` sh
service ssh status
```

### 设置开机自启

``` sh
sudo systemctl enable ssh
```

## 完成

## 参考文献

[CSDN——dh2580](https://blog.csdn.net/trackle400/article/details/52755571)
[博客园——殷大侠](https://www.cnblogs.com/yinheyi/p/6266748.html)
[CSDN——fandroid](https://blog.csdn.net/fandroid/article/details/86799932)
[CSDN——Tz.](https://blog.csdn.net/weixin_42551369/article/details/88946622)
