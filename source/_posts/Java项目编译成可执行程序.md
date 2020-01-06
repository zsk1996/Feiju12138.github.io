---
title: 【笔记】Java 项目编译成可执行程序
date: 2019-12-25 15:10:03
tags:
categories:
- Java
---

## 前言

将`Java项目`编译成`.exe`Windows可执行程序，Java编译的可执行程序需要系统已安装`JVM`才可以运行

<!-- more -->

## 准备工作

- exe4j（[传送门](https://www.ej-technologies.com/download/exe4j/files)）

- `Java项目`生成的`jar包`（[传送门](https://feiju12138.github.io/2019/12/25/Java项目打成jar包/)）

## 生成可执行程序

### 打开 exe4j

![01.png](/images/20191225151003/01.png)

### Welcome to exe4j!

- 选择`next`

![02.png](/images/20191225151003/02.png)

### Choose project type

- 将`JAR`转换为`EXE`文件

![03.png](/images/20191225151003/03.png)

### Configure application

- 设置软件短名称

- 设置导出文件的目录

![04.png](/images/20191225151003/04.png)

### Configure executable

- 设置软件名称

- 如果有图标可以设置软件图标

![05.png](/images/20191225151003/05.png)

### Select the architecture of the generated executable

- 设置是否在`64位Windows系统`下运行，如果是64位系统，勾选`Generate 64-bit executable`

![06.png](/images/20191225151003/06.png)

### Configue Java invocation

- 添加包括项目和第三方依赖的`jar包`

![07.png](/images/20191225151003/07.png)

- 选择`jar包`

![08.png](/images/20191225151003/08.png)

- 选择程序主函数

![09.png](/images/20191225151003/09.png)

- 如果编码格式是`UTF-8`，为防止中文乱码（Windows下默认编码方式为GBK），在`VM Parameters`输入`-Dfile.encoding=utf-8`

![10.png](/images/20191225151003/10.png)

### Configue JRE

- 设置软件版本

![11.png](/images/20191225151003/11.png)

### Configure search sequence

- 设置`JRE`目录，默认为系统环境变量，如果未设置`Java`环境变量，程序将无法运行

- 为防止出现问题，可以点击加号将`JRE`目录手动选择

![12.png](/images/20191225151003/12.png)

### 开始创建

- 点击`Compile executable`或`Finish`开始创建

![13.png](/images/20191225151003/13.png)

## 踩坑

- 代码内出现的文件路径应为Windows下的格式，应使用反斜杠

- 软件所需的其他素材应与程序捆绑复制

## 完成

## 参考文献

[CSDN——YoungStar70](https://blog.csdn.net/YoungStar70/article/details/75116227)

