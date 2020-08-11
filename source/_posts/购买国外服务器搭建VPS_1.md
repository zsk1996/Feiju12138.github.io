---
title: 【笔记】购买国外服务器搭建VPS（Ubuntu篇）
categories:
  - 云计算
date: 2019-11-10 13:50:02
---

## 前言

最近，在[Vultr](https://www.vultr.com)购买了国外的服务器，接下来我记录一下如何搭建VPS

<!-- more -->

## 远程连接到服务器

- 使用任意远程ssh连接工具连接，我这里直接使用的命令行工具"ssh"

- 将"IP Address"、"Username"作为参数分别复制到相应位置

- 出现输入密码提示时，将Password复制上去

``` bash
ssh Username@Ip_Address
```

## 安装SSR

- 使用wget工具安装SSR

``` bash
wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
```

## 配置SSR

- 安装过程中，可能需要根据提示进行配置，如果不清楚设置内容，回车默认就可以

## 安装成功

![01.png](/images/20191110135002/01.png)

## 安装谷歌BBR加速器（可选）

- 使用wget工具安装BBR

``` bash
wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```

## 配置BBR（可选）

- 回车默认即可

## 参考文献

[YouTube——抖音网红精选TOP](https://www.youtube.com/watch?v=aoUNRxFwpdA&t=462s)
