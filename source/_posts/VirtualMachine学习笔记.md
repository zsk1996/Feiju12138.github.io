---
title: 【笔记】Virtual Machine 学习笔记
categories:
  - Linux
date: 2020-06-30 21:38:55
---

## 前言

rht-vmctl主要是用于管理红帽培训中使用到的KVM虚拟机,该工具是红帽公司出的。（[Linux命令大全](https://www.linuxcool.com/rht-vmctl)）

<!-- more -->

## 安装

- 在Redhat系列Linux下使用yum命令安装

``` sh
yum install virt*
```

## 在内虚拟机安装系统

### 启动管理器

- `应用程序（Applications）`->`系统工具（System Tools）`->`虚拟系统管理器（Virtual Machine Manager）`

![01.png](/images/20200630213855/01.png)

### 安装新系统

- 左上角图标`新建`

![02.png](/images/20200630213855/02.png)

- `前进`

![03.png](/images/20200630213855/03.png)

- `浏览`->`本地浏览`->选择`.iso`映像文件->`打开`->`前进`->`是`

![04.png](/images/20200630213855/04.png)

- 设置内存->设置CPU->前进

![05.png](/images/20200630213855/05.png)

- 设置`为虚拟机创建磁盘镜像`

![06.png](/images/20200630213855/06.png)

- 修改名称->`完成`

![07.png](/images/20200630213855/07.png)

- 进入到Linux安装过程

[传送门](/2019/12/10/安装CentOSLinux系统/)

## 管理

### 打开虚拟机

> `<name>`：虚拟机主机名

``` sh
rht-vmctl start <name>
```

### 显示虚拟机

``` sh
rht-vmctl view <name>
```

### 关闭虚拟机

``` sh
rht-vmctl poweroff <name>
```

### 重置虚拟机

``` sh
rht-vmctl reset <name>
```

## 完成

## 参考文献

[YouToBe——Android and Tech Solutions](https://www.youtube.com/watch?v=iAfsW2ychkM)
[Linux命令大全（手册）](https://www.linuxcool.com/rht-vmctl)

