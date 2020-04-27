---
title: 【笔记】更换 Arch Linux 更新源
categories:
  - Linux
date: 2020-02-11 00:22:43
---

## 前言

更换`Arch Linux`更新源

<!-- more -->

## 换源

### 编辑配置文件

``` sh
nano /etc/pacman.d/mirrorlist
``` 

### 修改配置文件

- 去掉`Server = http://mirror.archlinuxarm.org/%arch/$>`的注释

- `Ctrl`+`X`离开

- `Y`保存

- `Enter`直接确定，不修改文件名

## 完成

## 参考文献

[CSDN——过了即是客](https://blog.csdn.net/u011054333/article/details/53510968)

