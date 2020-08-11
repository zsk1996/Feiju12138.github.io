---
title: 【笔记】完整卸载pkg包安装的软件
categories:
  - MacOS
date: 2020-08-05 10:12:44
---

## 前言

完整卸载使用`.pkg`安装包安装的软件

<!-- more -->

## 安装pkg_uninstaller

- [官网](https://github.com/mpapis/pkg_uninstaller)

``` sh
sudo bash < <(curl -sL https://raw.github.com/mpapis/pkg_uninstaller/master/pkg-install)
```

## 配置环境变量

``` sh
sudo echo 'PATH=$PATH:/opt/pkg_uninstaller' >> /etc/profile
echo 'PATH=$PATH:$HOME/.pkg_uninstaller' >> $HOME/.bash_profile
```

## 获取所有已安装的软件列表

``` sh
pkg-list
```

## 根据获取的软件完整名进行卸载

> `<com.xxx>`：软件包完整名

``` sh
pkg-uninstall <com.xxx>
```

## 参考文献

[百度经验——szh0129](https://jingyan.baidu.com/article/ac6a9a5e0b0a662b653eac2f.html)

