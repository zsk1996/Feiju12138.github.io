---
title: 【笔记】SpringBoot项目配置前端页面
categories:
  - Java
date: 2020-09-30 16:17:45
---

## 前言

SpringBoot项目配置前端页面，需要引入`thymeleaf`和`spring web`依赖

<!-- more -->

## 配置

``` properties
# 单体架构
spring.thymeleaf.prefix=classpath:/templates/

# 前后端分离架构动态页面
# spring.thymeleaf.prefix=file:/src/main/resources/templates/
# spring.thymeleaf.prefix=file:///src/main/resources/templates/
# spring.thymeleaf.prefix=http://localhost/

# 前后端分离架构静态页面
# spring.mvc.static-path-pattern=
```

## 完成

