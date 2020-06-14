---
title: 【笔记】配置静态IP地址
categories:
  - Linux
date: 2020-06-11 16:45:20
---

## 前言

在RedHat系列Linux上配置静态IP地址

<!-- more -->

## 编辑网卡配置

``` sh
vim /etc/sysconfig/network-script/ifcfg-ens33
```

## 修改网卡配置

- 修改`BOOTPROTO=dhcp`

``` sh
BOOTPROTO=static
```

- 修改`ONBOOT=no`

``` sh
ONBOOT=yes
```

- 添加静态IP配置

> `<ip>`：IP地址

``` sh
IPADDR=<ip>
```

- 添加子网掩码配置

``` sh
NETMASK=255.255.255.255
```

- 添加网关配置

> `<ip>`：网段为1的IP地址（192.168.1.1）

``` sh
GATEWAY=<ip>
```

- 添加DNS配置

``` sh
DNS1=114.114.114.114
```

## 重启网卡

``` sh
systemctl restart network.service
```

## 完成

## 参考文献

[哔哩哔哩——CodeSheep](https://www.bilibili.com/video/BV1bA411b7vs)

