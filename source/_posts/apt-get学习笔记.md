---
title: 【笔记】apt-get 学习笔记（Ubuntu篇）
date: 2019-12-09 23:35:55
tags:
categories:
- Linux
---

## 前言

高级打包工具是Debian及其派生的Linux软件包管理器。APT可以自动下载，配置，安装二进制或者源代码格式的软件包，因此简化了Unix系统上管理软件的过程。APT最早被设计成dpkg的前端，用来处理deb格式的软件包。现在经过APT-RPM组织修改，APT已经可以安装在支持RPM的系统管理RPM包。（[维基百科](https://zh.wikipedia.org/wiki/APT)）

<!-- more -->

## 基本命令

### 安装软件包

- 普通安装

``` bash
apt-get install <packegname>
```

- 重新安装

``` bash
apt-get reinstall <packagename>
```

- 安装源码包所需要的编译环境

``` bash
apt-get build-dep <packagename>
```

- 修复依赖关系

``` bash
apt-get -f install
```

- 下载软件包的源码

``` bash
apt-get source <packagename>
```


### 卸载软件包

- 卸载软件包

保留配置文件

``` bash
apt-get remove <packagename>
```

- 卸载软件包

删除配置文件

``` bash
apt-get purge <packagename>
apt-get --purge remove <packagename>
```

- 卸载软件包

删除配置文件和依赖包

``` bash
apt-get autoremove <packagename>
apt-get --purge autoremove <packagename>
```

- 删除已下载的包文件

``` bash
apt-get clean
```

- 删除已下载的旧包文件

``` bash
apt-get autoclean
```

### 更新软件包

- 更新安装源

``` bash
apt-get update
```

- 更新已安装的软件包

不处理依赖关系

``` bash
apt-get upgrade
```

- 更新已安装的软件包

处理依赖关系

``` bash
apt-get dist-upgrade
```

### 查询软件包

- 列出已安装的所有软件包

``` bash
dpkg -l
```

- 搜索软件包

``` bash
apt-cache search <packagename>
```

- 获取软件包的相关信息

``` bash
apt-cache show <packagename>
```

- 查看所需的依赖包

``` bash
apt-cache depends <packagename>
```

- 查看被哪些软件依赖

``` bash
apt-cache rdepends <packagename>
```

- 检查损坏的依赖

``` bash
apt-get check
```

## 参考文献

[CSDN——xietansheng](https://blog.csdn.net/xietansheng/article/details/80044644)

