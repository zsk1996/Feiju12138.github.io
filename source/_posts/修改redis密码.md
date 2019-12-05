---
title: 【踩坑】修改redis密码
date: 2019-11-16 15:45:48
tags:
categories:
- Redis
---

## 前言

安装完"redis"的第一件事就是配置，其中有一项需要配置的内容就是设置redis的密码，默认安装好会有一个默认密码，但是要修改成自己的密码才可以正常使用

<!-- more -->

## 找到redis配置文件

- Windows系统的redis配置文件在redis安装根目录下的"redis.conf"

- 我这里使用的MacOS，安装方法是通过HomeBrew

- 我的配置文件在"/usr/local/etc/redis.conf"

## 修改redis配置文件

- 修改506行，将密码改为"123456"

``` bash
requirepass 123456
```

![01.png](/images/20191116154548/01.png)

## 完成

