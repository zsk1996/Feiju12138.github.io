---
title: 【笔记】Fping 学习笔记
date: 2019-12-04 22:31:04
tags:
categories:
- Penetration Tests
---

## 前言

Fping类似于ping，但比ping强大。Fping与ping不同的地方在于，fping可以在命令行中指定要ping的主机数量范围，也可以指定含有要ping的主机列表文件。

与ping要等待某一主机连接超时或发回反馈信息不同，fping给一个主机发送完数据包后，马上给下一个主机发送数据包，实现多主机同时ping。如果某一主机ping通，则此主机将被打上标记，并从等待列表中移除，如果没ping通，说明主机无法到达，主机仍然留在等待列表中，等待后续操作。

<font color="red">本文仅用于网络信息防御学习</font>

<!-- more -->

## 基本命令

### Ping 网段

``` bash
fping -g 192.168.1.0 192.168.1.255
```

#### Ping全网段

``` sh
fping -g 192.168.1.1/24
```

### 显示可ping通的目标

``` bash
fping -a
```

### 将目标以ip地址的形式显示

``` bash
fping -A
```

### ping 数据包的大小

- 默认为56

``` bash
fping -b <num>
```

### 设置指数反馈因子到f

``` bash
fping -B <f>
```

### ping每个目标的次数

- 默认为1

``` bash
fping -c <num>
fping -C <num>
```

### 显示返回数据包所费时间

``` bash
fping -e
```

### 从文件获取目标列表

- 不能与`-g`同时使用

``` bash
fping -f <file>
```

### 设置ip的TTL值

- 生存时间

``` bash
fping -i
```

### 循环发送ping

``` bash
fping -l
```

### ping目标主机的多个网口

``` bash
fping -m
```

### 将目标以主机名或域名显示

``` bash
fping -n
fping -d
```

### 对同一个目标的ping包间隔(毫秒) 

- 在循环和统计模式中，默认为1000

``` bash
fping -p <num>
```

### 安静模式

- 不显示每个目标或每个ping的结果

``` bash
fping -q
fping -Q
```

### 当ping失败时，最大重试次数

- 默认为3次

``` bash
fping -r <num>
```

### 打印最后的统计数据

``` bash
fping -s
```

### 单个目标的超时时间(毫秒)

- 默认500

``` bash
fping -t <num>
```

### 显示不可到达的目标

``` bash
fping -u
```

### 显示版本号

``` bash
fping -v
```

## 参考文献

[CSDN——wz_cow](https://blog.csdn.net/wz_cow/article/details/80967255)

