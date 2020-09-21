---
title: 【笔记】Gradle学习笔记
categories:
  - Java
date: 2020-09-21 08:11:40
---

## 前言

Gradle是一个基于Apache Ant和Apache Maven概念的项目自动化建构工具。Gradle 构建脚本使用的是 Groovy 或 Kotlin 的特定领域语言来编写的，而不是传统的XML。
当前官方支持的语言为Java、Groovy、Scala、C++、Swift、JavaScript等以及Spring框架。（[维基百科](https://zh.wikipedia.org/wiki/Gradle)）

<!-- more -->

## 配置

- Gradle项目的配置文件为使用Groovy语言编写的`build.gradle`文件

- 通过IDEA创建Gradle项目会生成如下模版

``` groovy
plugins {
    id 'java'
}

group 'org.example'
version '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testCompile group: 'junit', name: 'junit', version: '4.12'
}
```

> `mavenCentral()`：指定所使用的仓库。表示使用中央仓库
> `testCompile`：作用域。表示当前依赖在测试的时候起作用
> `group`：定义依赖的组名
> `group`：定义依赖的项目名
> `group`：定义依赖的版本号




## 未完待更

[哔哩哔哩——代码基基](https://www.bilibili.com/video/BV1At411375J)
