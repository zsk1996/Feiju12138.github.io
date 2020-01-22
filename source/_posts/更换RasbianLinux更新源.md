---
title: 【笔记】更换 Rasbian Linux 更新源
categories:
  - 树莓派
date: 2020-01-14 21:21:22
---

## 前言

更换`Rasbian Linux`更新源

<!-- more -->

## 换源

### 编辑 sources 文件

``` sh
sudo nano /etc/apt/sources.list
```

### 修改 sources 文件

- 将其他源使用`#`注释，添加国内更新源

``` sh
deb http://mirrors.aliyun.com/raspbian/raspbian/ jessie main non-free contrib rpi
deb-src http://mirrors.aliyun.com/raspbian/raspbian/ jessie main non-free contrib rpi
```

## 完成

## 参考文献

[简书——黑球君](https://www.jianshu.com/p/abb1d797d1f3)

