---
title: 【踩坑】Linux 开机自动连接网络（CentOS篇）
date: 2019-11-13 12:59:17
tags:
---

## 前言

安装到 CentOS 8 系统，发现默认开机不会自动连接网络，通过修改网络配置文件，让 Cent OS 8 开机自动连接网络。

<!-- more -->

## 打开终端

- 活动->终端

![01.png](/images/20191113125917/01.png)

## 配置网络设置

- 进入网络配置文件夹,并查看当前目录下的文件

``` bash
cd /etc/sysconfig/network-scripts/
ls
```

![02.png](/images/20191113125917/02.png)

- 使用"vim"工具修改上一步查看到的文件

``` bash
sudo vim ifcfg-enp2s0
```

- 备注

如果当前用户为非"root"用户，需要输入管理员密码才可以进行下一步

- 按"i"键进入输入模式

- 将光标移动到"ONBOOT"，将值由"no"改为"yes"

![03.png](/images/20191113125917/03.png)

- 按"ESC"键退出输入模式，输入":wq"按回车保存并退出

![04.png](/images/20191113125917/04.png)

## 完成

至此，重启系统后，网络会自动连接

## 参考文献

[百度经验——wsfxzxb](https://jingyan.baidu.com/article/19192ad8f7c320e53e570728.html)
