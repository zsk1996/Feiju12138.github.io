---
title: 【笔记】Maven依赖范围
categories:
  - Java
date: 2020-08-18 10:13:07
---

## 前言

Maven依赖范围

<!-- more -->

## 添加位置

- 在`<scope></scope>`内部添加此依赖的范围

``` java
<dependency>
  <scope></scope>
</dependency>
```

## 依赖范围

- **compile** ：编译依赖范围。默认的范围，可以不填，表示在所有过程中都有效，如编译期、测试过程中、运行期间等。
- **provided** ：已提供依赖范围。这个范围表示只提供编译和测试阶段有效，运行期间不需要，像tomcat等容器本身已经提供的 servlet-api、jsp-api 等依赖。
- **runtime** ：运行时依赖范围。这个范围表示只有在运行和测试期间才有效，编译期间不需要，像连接数据库的jdbc驱动程序等。
- **test** ：测试依赖范围。这个范围只有测试阶段有效，编译和运行不需要，像单元测试提供的junit包。
- **system** ：系统依赖范围。这个范围表示不依赖本地仓库，jar在其他的目录，需要通过systemPath指定路径，这个不建议使用。

- **import** ：引用依赖范围。Maven2.0.9之后新增的范围，只能用在<dependencyManagement>中，并且导入的type为pom类型的父工程配置，一般用来解决多继承问题。

## 完成

