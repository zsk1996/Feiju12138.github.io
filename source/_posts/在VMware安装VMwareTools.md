---
title: 【笔记】在VMware安装VMwareTools（Kali篇）
date: 2019-11-03 20:12:19
tags:
categories:
- 虚拟机
---

## 前言

在VMware虚拟机安装kali系统之后，无法从虚拟机系统外复制文字或文件到虚拟机系统内，这是因为还没有安装虚拟机自带的工具，需要手动安装。（其他虚拟机软件大同小异，请根据软件提示安装）

<!-- more -->

## 在虚拟机系统内挂载虚拟光盘映像

- VMware菜单-> 虚拟机->安装 VMware Tools（因为我的已经安装成功，所以这里显示重新安装 VMware Tools）

![01.png](/images/20191103201219/01.png)

- 挂载成功后，kali系统会提示有光盘插入

![02.png](/images/20191103201219/02.png)

## 安装

- 复制虚拟光盘映像中的安装压缩包到本地Home目录

``` bash
cp /media/cdrom/VMwareTools-10.3.10-13959562.tar.gz ~
```

- 解压压缩包

``` bash
tar -xf VMwareTools-10.3.10-13959562.tar.gz vmware-tools-distrib/
```

- 执行安装命令

``` bash
cd ~
vmware-tools-distrib/vmware-install.pl
```

![03.png](/images/20191103201219/03.png)

## 配置

- 执行安装命令后，会遇到停顿，脚本会自动向你询问安装的具体配置，你可以根据需要在"()"内选择一项输入，也可以像我一样按回车键（直接回车确定表示使用默认配置）

- 显示"Enjoy,"表示安装成功

![04.png](/images/20191103201219/04.png)

