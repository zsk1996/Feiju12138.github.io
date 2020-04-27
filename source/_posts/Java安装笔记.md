---
title: 【笔记】Java安装笔记
categories:
  - Linux
date: 2020-04-26 21:14:16
---

## 前言

在CentOS上安装JDK1.8

<!-- more -->

## 安装JDK

``` sh
yum install java-1.8.0-openjdk-devel.x86_64
```

## 配置环境变量

### 编辑环境变量

``` sh
vi /etc/profile
```

### 添加环境变量

``` sh
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.171-8.b10.el6_9.x86_64
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
```

### 刷新环境变量

``` sh
source /etc/profile
```

## 查看版本号

``` sh
java -version
```

## 参考文献

[segmentfault——恒不动](https://segmentfault.com/a/1190000015389941)

