---
title: 【笔记】后台运行Minecraft服务器
categories:
  - Minecraft
date: 2020-06-24 12:34:56
---

## 前言

后台运行Minecraft服务器

<!-- more -->

## Linux

> `<server>`：启动服务器脚本

``` sh
nohup java -Xms3072M -Xmx3072M -jar <server>.jar -nogui &
```

- 此时即使关闭ssh远程连接，也可以后台运行Minecraft服务器

### 查看状态

``` sh
tail -f nohub.out
```

## 完成

## 参考文献

[Mr.Ma's的博客](https://www.misterma.com/archives/864/)

