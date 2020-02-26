---
title: 【笔记】Tomcat 学习笔记
date: 2019-11-26 14:44:20
tags:
categories:
- 服务器
---

## 前言

Tomcat是由Apache软件基金会属下Jakarta项目开发的Servlet容器，按照Sun Microsystems提供的技术规范，实现了对Servlet和JavaServer Page（JSP）的支持，并提供了作为Web服务器的一些特有功能，如Tomcat管理和控制平台、安全局管理和Tomcat阀等。（[维基百科](https://zh.wikipedia.org/wiki/Apache_Tomcat)）

<!-- more -->

## 准备工作

- 安装jdk，并配置环境变量

## 安装

- MacOS使用`brew`命令安装最新版`tomcat`

``` bash
brew install tomcat
```

## 配置环境变量

- 打开环境变量配置文件

``` bash
vim ~/.bash_profile
```

- 添加环境变量

``` bash
export PATH=$PATH:/usr/local/Cellar/tomcat/9.0.29/libexec/bin
```

- 保存并退出

``` bash
:wq
```

- 使配置立即生效

``` bash
source ~/.bash_profile
```

## 查看版本号

``` bash
catalina version
```

## 启动

``` bash
catalina run
```

## 关闭

- 使用关闭命令

``` bash
catalina stop
```

- 直接停止进程

``` bash
^c
```

## 访问

- 使用`Safari`打开站点

``` bash
open -a /Applications/Safari.app 127.0.0.1:8080
```

## 修改端口号

- 修改配置文件第69行

``` bash
vim /usr/local/Cellar/tomcat/9.0.29/libexec/conf/server.xml
```

## 部署项目

1. 直接将项目放到webapps目录下

2. 修改全局配置文件

- 编辑`server.xml`文件

``` bash
vim /usr/local/Cellar/tomcat/9.0.29/libexec/conf/server.xml
```

- 添加标签

> docBase：项目存放的目录
> path：虚拟目录

``` xml
<Host>
    <Context docBase="~/Sites/demo" path="/demo"/>
</Host>
```

3. 创建局部配置文件

- 新建并编辑`demo.xml`

``` bash
vim /usr/local/Cellar/tomcat/9.0.29/libexec/conf/Catalina/localhost/demo.xml
```

- 添加标签

> docBase：项目存放的目录

``` bash
<Context docBase="~/Sites/demo"/>
```

## 参考文献

[哔哩哔哩——张奇MAX](https://www.bilibili.com/video/av70420291)
