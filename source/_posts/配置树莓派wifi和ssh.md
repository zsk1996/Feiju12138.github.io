---
title: 【笔记】配置 树莓派 wifi 和 ssh
categories:
  - 树莓派
date: 2020-01-13 11:01:39
---

## 前言

树莓派首次安装完系统，需要配置`wifi`和`ssh`以通过电脑远程连接

<!-- more -->

## 配置 wifi

- 在`/boot`目录下新建`wpa_supplicant.conf`wifi配置文件

- 在文件内写入配置信息

> `<name>`：wifi名称
> `<password>`：wifi密码，无密码为`NONE`
> `<num>`：优先级，值越小优先级越高（可选）
> `<safety>`：是否为`WPA/WPA2`加密方式，值为`WPA-PSK`（可选）
> `<value>`：是否为隐藏wifi，值为`1`（可选）

``` sh
country=CN
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="<name>"
    psk="<password>"
    key_mgmt=<safety>
    priority=<num>
    scan_ssid=<value>
}
```

## 配置 ssh

- 在`/boot`目录下新建空白`ssh`文件

``` sh
touch ssh
```

### ssh 远程连接树莓派

> `<name>`：用户名为`pi`
> `<password>`：密码为`raspberry`
> `<ip_address>`：树莓派ip地址

``` sh
ssh <name>@<ip_address>
<password>
```

## 完成

## 参考文献

[哔哩哔哩——jinganwang](https://www.bilibili.com/video/av72048534?p=2)
[南墙的博客](http://imzifeng.cn/2018/07/badusb-on-raspberry-pi-zero-w/)
[树莓派实验室](http://shumeipai.nxez.com/2017/09/13/raspberry-pi-network-configuration-before-boot.html)

