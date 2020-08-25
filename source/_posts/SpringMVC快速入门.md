---
title: 【代码】SpringMVC快速入门
categories:
  - Java
date: 2020-08-23 10:43:44
---

## 前言

SpringMVC快速入门

<!-- more -->

## 创建项目

- 创建maven项目，配置pom.xml文件来引入项目所需要的jar包

``` xml
<dependencies>
	<!-- 单元测试 -->
	<dependency>
		<groupId>junit</groupId>
		<artifactId>junit</artifactId>
		<version>4.10</version>
		<scope>test</scope>
	</dependency>

	<!-- SpringMVC的jar包 -->
	<dependency>
		<groupId>org.springframework</groupId>
		<artifactId>spring-webmvc</artifactId>
		<version>4.1.3.RELEASE</version>
	</dependency>
	
	<!-- servlet 和 jsp的jar包 -->
  <dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>servlet-api</artifactId>
    <version>2.5</version>
    <scope>provided</scope>
  </dependency>
  <dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jsp-api</artifactId>
    <version>2.0</version>
    <scope>provided</scope>
  </dependency>
	
	<!-- java对象转换json的工具类
	<dependency>
		<groupId>com.fasterxml.jackson.core</groupId>
		<artifactId>jackson-databind</artifactId>
		<version>2.5.1</version>
	</dependency>
	 -->
</dependencies>
```

## 配置前端控制器

- 在web.xml文件内配置前端控制器

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://java.sun.com/xml/ns/javaee" xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd" version="2.5">
  <display-name>day20-springmvc</display-name>
  <welcome-file-list>
    <welcome-file>index.html</welcome-file>
    <welcome-file>index.htm</welcome-file>
    <welcome-file>index.jsp</welcome-file>
    <welcome-file>default.html</welcome-file>
    <welcome-file>default.htm</welcome-file>
    <welcome-file>default.jsp</welcome-file>
  </welcome-file-list>
  
  <!-- 配置springmvc的前端控制器(DispatcherServlet)，
  配置拦截除了jsp以外的所有请求 -->
  <servlet>
    <servlet-name>springmvc</servlet-name>
    <!-- 固定值 -->
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <!-- 配置springmvc-config文件的位置 -->
    <init-param>
        <!-- 固定值 -->
        <param-name>contextConfigLocation</param-name>
        <!--  文件名和位置 -->
        <param-value>classpath:springmvc-config.xml</param-value>
    </init-param>
  </servlet>
  <servlet-mapping>
    <servlet-name>springmvc</servlet-name>
    <!-- 拦截范围
    `/*`表示拦截所有静态资源包括jsp
    `/`表示拦截所有静态资源但是不包括jsp -->
    <url-pattern>/</url-pattern>
  </servlet-mapping>
  
</web-app>
```

## 配置springmvc-config.xml 

- 在`/src/main/resources/`目录下创建`springmvc-config.xml`文件

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:mvc="http://www.springframework.org/schema/mvc"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/mvc
                        http://www.springframework.org/schema/mvc/spring-mvc-4.0.xsd
                        http://www.springframework.org/schema/beans
                        http://www.springframework.org/schema/beans/spring-beans-4.0.xsd
                        http://www.springframework.org/schema/context
                        http://www.springframework.org/schema/context/spring-context-4.0.xsd">
    
    <!-- 1.配置前端控制器放行静态资源(html/css/js等，否则静态资源将无法访问) -->
    <mvc:default-servlet-handler/>
    
    <!-- 2.配置注解驱动，用于识别注解（比如@Controller） -->
    <mvc:annotation-driven></mvc:annotation-driven>
    
    <!-- 3.配置需要扫描的包：spring自动去扫描 base-package 下的类，
        如果扫描到的类上有 @Controller、@Service、@Component等注解，
        将会自动将类注册为bean 
     -->
    <context:component-scan base-package="com.tedu.controller">
    </context:component-scan>
    
    <!-- 4.配置内部资源视图解析器
        prefix:配置路径前缀
        suffix:配置文件后缀
     -->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/pages/"/>
        <property name="suffix" value=".jsp"/>
    </bean>

</beans>
```

## 实现Controller类

- 在`/src/main/java`目录下创建普通的java类，通过注解的方式将其标记为Controller

``` java
package com.tedu.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

/* @Controller，如果当前类所在的包配置了Spring容器包扫描，具有该注解的类就会作为bean注册到Spring容器中，由Spring容器创建实例 */
@Controller
@RequestMapping("/HelloController")
public class HelloController {
    
    // @RequestMapping，定义访问路径，如果Controller也有访问路径也可以配置
    @RequestMapping("/hello")
    public String hello() {
        System.out.println("HelloController.testHello()");
        // 实际上会访问`/WEB-INF/pages/home.jsp`，因为在`springmvc-config.xml`配置了前缀和后缀
        return "home";
    }
    
}
```

## 创建测试jsp

- 在`/src/main/webapp/WEB-INF`目录下新建`/jsp/home.jsp`文件

``` jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Title</title>
</head>
<body>
    <h1>测试页面</h1>
</body>
</html>
```

## 完成

- 访问路径`http://localhost:8080/项目名/Controller类的访问名/Controller内方法的访问名`
