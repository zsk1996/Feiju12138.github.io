---
title: 【笔记】Tor学习笔记
categories:
  - MacOS
date: 2020-03-30 20:50:26
---

## 前言

Tor是实现匿名通信的自由软件。其名源于“The Onion Router”（洋葱路由器）的英语缩写。用户可透过Tor接达由全球志愿者免费提供，包含7000+个中继的覆盖网络，从而达至隐藏用户真实地址、避免网络监控及流量分析的目的。Tor用户的互联网活动（包括浏览在线网站、帖子以及即时消息等通信形式）相对较难追踪。Tor的设计原意在于保障用户的个人隐私，以及不受监控地进行秘密通信的自由和能力。（[维基百科](https://zh.wikipedia.org/wiki/Tor)）

<!-- more -->

## 安装

``` sh
brew install tor
```

## 配置代理

- 通常情况下，由于tor的节点可能会出现在国外，所以需要配合其他代理软件使用

### 编辑配置文件

``` sh
vim /usr/local/etc/tor/torrc
```

### 修改配置文件

- Lantern添加如下语句

``` sh
HTTPProxy 127.0.0.1:52909
HTTPSProxy 127.0.0.1:52909
```

- Shadowsocks-R添加如下语句

``` sh
Socks5Proxy 127.0.0.1:1086
```

## 配置黑名单节点

- 由于部分国家以合作的方式进行网络审查，所以需要将部分国家节点列入黑名单

### 编辑配置文件

``` sh
vim /usr/local/etc/tor/torrc
```

### 修改配置文件

- 添加如下语句

``` sh
ExcludeNodes  {cn},{hk},{mo},{kp},{ir},{sy},{pk},{cu},{vn}
StrictNodes  1
```

## 启动tor

- 以默认配置文件启动tor

``` sh
tor
```

### 指定配置文件启动

> `<src>`：配置文件路径

``` sh
tor -f <src>
```

## 查看tor运行状态

- tor默认端口号为9050，所以可以通过查看端口占用情况来查看tor运行状态

``` sh
lsof -i:9050
```

## 关闭tor

- 通过查看tor进程的pid号，来直接关闭tor进程

> `<num>`：tor进程的pid号

``` sh
kill <num>
```

## 完成

![01.png](/images/20200330205026/01.png)

## 参考文献

[php5000](https://www.php5000.com/index/content/index/id/218)

