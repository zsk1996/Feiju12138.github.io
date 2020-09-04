---
title: 【笔记】SpringBoot整合SpringMVC
categories:
  - Java
date: 2020-08-31 16:47:42
---

## 前言

SpringBoot整合SpringMVC

<!-- more -->

## 添加SpringMVC依赖

- 编辑`pom.xml`配置文件

- 添加Web依赖（提供SpringMVC核心API，同时会嵌入一个Tomcat服务器）

``` xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

- 添加Thymeleaf（提供了一个视图解析器对象以及数据绑定机制）

``` xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

## 配置SpringMVC核心对象

- 编辑`application.properties`配置文件

- 定义前缀和后缀

``` properties
spring.thymeleaf.prefix=classpath:/templates/pages/
spring.thymeleaf.suffix=.html
```

- 配置热部署（可选）

``` properties
spring.thymeleaf.cache=false
```

- 配置项目访问路径，默认为`/`（可选）

``` properties
server.servlet.context-path=/
```

- 配置访问端口号，默认为`8080`（可选）

``` properties
server.port=80
```

## View

- 静态页面书写位置：`/src/main/resources/static`

- 动态页面书写位置：`/src/main/resources/templates/pages`

## 完成

