---
title: 【踩坑】解决 Spring MVC 的POST请求乱码问题
categories:
  - null
date: 2020-08-24 11:36:54
---

## 前言

解决`Spring MVC`的POST请求乱码问题

<!-- more -->

## 配置过滤器

- 在web.xml配置过滤器，将项目中所有POST请求的字符编码改为`UTF-8`

``` java
<!-- 配置过滤器,解决POST提交的中文参数乱码问题 -->
<filter>
	<filter-name>encodingFilter</filter-name>
	<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
	<init-param>
		<param-name>encoding</param-name>
		<param-value>UTF8</param-value>
	</init-param>
</filter>
<filter-mapping>
	<filter-name>encodingFilter</filter-name>
	<url-pattern>/*</url-pattern>
</filter-mapping>
```

## 完成

