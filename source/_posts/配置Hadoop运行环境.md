---
title: 【笔记】配置 Hadoop 运行环境
categories:
  - Big Data
date: 2020-01-31 23:07:55
---

## 前言

配置`Hadoop`运行环境

<!-- more -->

## 准备工作

- Hadoop

## 配置

### 编辑配置文件

- 编辑`etc/hadoop/hadoop-env.sh`文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/hadoop-env.sh
```

- 修改54行，配置`JAVA_HOME`

``` sh
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home
```

- 修改58行，配置`HADOOP_HOME`

``` sh
export HADOOP_HOME=/usr/local/Cellar/hadoop/3.2.1/libexec
```

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)

