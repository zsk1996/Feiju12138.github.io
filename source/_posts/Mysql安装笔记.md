---
title: 【笔记】Mysql安装笔记
categories:
  - Linux
date: 2020-06-03 14:43:18
---

## 前言

在`CentOS`上用yum方法安装Mysql社区版

<!-- more -->

## 更新yum源

### 下载yum源

``` sh
wget https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
```

### 安装yum源

``` sh
sudo rpm -Uvh mysql80-community-release-el7-3.noarch.rpm
```

### 检查是否安装成功

``` sh
yum repolist enabled | grep "mysql.*-community.*"
```

## 选择Mysql版本（可选）

- 不选则为安装最新版

### yum-config-manager 方法

#### 查看所有可安装版本

``` sh
yum repolist all | grep mysql
```

#### 切换版本

``` sh
sudo yum-config-manager --disable mysql80-community
sudo yum-config-manager --enable mysql57-community
```

### mysql-community.repo 方法

#### 编辑mysql-community.repo文件

``` sh
vim /etc/yum.repos.d/mysql-community.repo
```

#### 修改mysql-community.repo文件

- 设置禁用新版本`enabled=0`

``` sh
[mysql80-community]
name=MySQL 8.0 Community Server
baseurl=http://repo.mysql.com/yum/mysql-8.0-community/el/7/$basearch/
enabled=0
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```

- 设置启用新版本`enabled=1`

``` sh
[mysql57-community]
name=MySQL 5.7 Community Server
baseurl=http://repo.mysql.com/yum/mysql-5.7-community/el/7/$basearch/
enabled=1
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
```

#### 检查当前启用的Mysql版本

``` sh
yum repolist enabled | grep mysql
```

## 安装Mysql

``` sh
sudo yum install mysql-community-server -y
```

## 启动Mysql

``` sh
sudo systemctl start mysqld.service
```

## 停止Mysql

``` sh
sudo systemctl stop mysqld.service
```

## 重启Mysql

``` sh
sudo systemctl restart mysqld.service
```

## 查看启动状态

``` sh
sudo systemctl status mysqld.service
```

## 初始化

### 查看初始密码

``` sh
sudo grep 'temporary password' /var/log/mysqld.log
```

### 登录

``` sh
mysql -uroot -p
```

### 修改密码

- 初次使用必须修改密码，不修改密码将不能使用

``` sh
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
```

### 设置开机自启

``` sh
systemctl enable mysqld
systemctl daemon-reload
```

## 完成

