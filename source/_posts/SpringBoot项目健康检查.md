---
title: 【笔记】SpringBoot项目健康检查
categories:
  - Java
date: 2020-09-02 13:56:35
---

## 前言

SpringBoot项目健康检查

<!-- more -->

## 添加依赖

- 编辑pom.xml配置文件

``` java
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

## 管理页面

- 启动项目，在浏览器进入管理页面

``` sh
http://localhost/actuator
```

## 管理更多选项

- 编辑application.properties配置文件

``` properties
management.endpoints.web.exposure.include=*
```

## 完成


