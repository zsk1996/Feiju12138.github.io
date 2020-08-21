---
title: 【笔记】Tor 学习笔记
categories:
  - 网络安全
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

- ~Lantern添加如下语句~

``` sh
HTTPProxy 127.0.0.1:52909
HTTPSProxy 127.0.0.1:52909
```

- Lantern添加如下语句

``` sh
Socks5Proxy 127.0.0.1:52911
```

- Shadowsocks-R添加如下语句

``` sh
Socks5Proxy 127.0.0.1:1086
```

## 配置黑名单节点（可选）

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

## 配置入口节点（可选）

- 限定只使用某些国家的节点作为入口节点

``` sh
EntryNodes <country>
```

## 配置出口节点（可选）

- 限定只使用某些国家的节点作为出口节点

``` sh
ExitNodes <country>
```

## 跨机器共享Tor通道（可选）

- 编辑配置文件

``` sh
SocksListenAddress 0.0.0.0:9050
```

## 启动和关闭tor

### 直接启动

- 以默认配置文件启动tor

``` sh
tor
```

#### 指定配置文件启动

> `<src>`：配置文件路径

``` sh
tor -f <src>
```

### 查看tor运行状态

- tor默认端口号为9050，所以可以通过查看端口占用情况来查看tor运行状态

``` sh
lsof -i:9050
```

### 关闭tor

- 通过查看tor进程的pid号，来直接关闭tor进程

> `<num>`：tor进程的pid号

``` sh
kill <num>
```

- 直接杀掉所有tor进程

``` sh
killall tor
```

### 通过brew的服务管理器启动和关闭tor服务

``` sh
brew services start tor
brew services stop tor
```

## 完成

### 查看Tor是否已使用

- [https://check.torproject.org](https://check.torproject.org)

![01.png](/images/20200330205026/01.png)

### 查看当前IP

``` sh
curl --socks5 127.0.0.1:9050 http://checkip.amazonaws.com/
```

## 参考文献

[php5000](https://www.php5000.com/index/content/index/id/218)
[编程随想的博客](https://program-think.blogspot.com/2013/11/tor-faq.html)

