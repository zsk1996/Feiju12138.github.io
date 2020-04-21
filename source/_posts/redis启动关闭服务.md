---
title: 【笔记】redis 启动关闭服务
date: 2019-12-05 15:08:23
tags:
categories:
- Database
---

## 前言

`redis`服务的启动和关闭与其他服务不大一样

<!-- more -->

## 启动

### 直接启动

``` bash
redis-server
```

### 在后台启动

``` bash
redis-server &
```

### 指定配置文件启动

- 找到`redis`的配置文件，我使用的MacOS系统的`brew`安装`redis`，所以配置文件会放在`/usr/local/etc`目录下

- 如果没有`redis.conf`配置文件，将`redis.conf.default`复制一份，将文件名修改为`redis.conf`

- 将配置文件修改为自己的目录路径

``` bash
redis-server /usr/local/etc/redis.conf
```

## 关闭

### 正常关闭

- 修改redis默认密码（[传送门](https://feiju12138.github.io/2019/11/16/修改redis密码/)）

- 使用密码登录`redis`客户端

``` bash
redis-cli -a <password>
```

- 指定端口号登录（可选）

``` bash
redis-cli -p 6379
```

- 关闭`redis`服务

``` bash
127.0.0.1:6379> shutdown
```

- 退出`redis`

``` bash
127.0.0.1:6379> exit
```

### 快速关闭

``` bash
redis-cli -a <password> shutdown
```

## 参考文献

[CSDN——justinytsoft](https://blog.csdn.net/justinytsoft/article/details/69250497)
[doforme的博客](https://www.cnblogs.com/pqchao/p/6549510.html)
[简书——Rick_Ji](https://www.jianshu.com/p/12b877dba5f9)

