---
title: 【代码】Spring IOC 控制反转 快速入门
categories:
  - Java
date: 2020-08-21 21:59:36
---

## 前言

Spring IOC 控制反转 快速入门

<!--more-->

## 代码

- 创建Maven项目，在`pom.xml`文件添加Spring包和Junit包

``` xml
<dependencies>
    <!-- 添加junit的jar包 -->
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.10</version>
    </dependency>
    <!-- 添加spring的jar包 -->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>4.1.3.RELEASE</version>
    </dependency>
</dependencies>
```

- 在`src/main/resources`目录下新建`applicationContext.xml`文件
- 传递实现类，通过Spring管理对象

> `id`：值唯一
> `class`：实现类的全局限定名

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd">
    
    <bean id="empService" class="com.tedu.service.impl.EmpServiceImpl02"></bean>
    
</beans>
```

- 创建测试类，创建测试方法

``` java
@Test
public void testService() {
    
    // 通过xml文件的位置创建Spring的对象
    ClassPathXmlApplicationContext ac = new ClassPathXmlApplicationContext("applicationContext.xml");
    
    // 通过xml中id属性获取使用Spring创建的对象
    EmpService service = (EmpService)ac.getBean("empService");

    // 直接调用对象的方法
    service.add();
}
```

## 完成
