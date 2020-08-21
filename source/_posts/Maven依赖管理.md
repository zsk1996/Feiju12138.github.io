---
title: 【笔记】Maven依赖管理
categories:
  - Java
date: 2020-08-18 10:19:05
---

## 前言

Maven依赖管理

<!-- more -->

## 编辑pom文件

> `<groupId></groupId>`：填写组名
> `<artifactId></artifactId>`：填写类名
> `<version></version>`：填写版本
> `<scope></scope>`：填写范围（[传送门](/2020/08/18/Maven依赖范围/)）

``` java
<dependencies>
    
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>servlet-api</artifactId>
        <version>2.5</version>
        <scope>provided</scope>
    </dependency>
        
</dependencies>
```

## pom配置搜索

- [mvnrepository](https://mvnrepository.com)

- [阿里云](https://maven.aliyun.com/mvn/view)

## 完成

