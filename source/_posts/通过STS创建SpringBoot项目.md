---
title: 【笔记】通过STS创建SpringBoot项目
categories:
  - Java
date: 2020-08-25 17:06:03
---

## 前言

基于SpringToolSuite4创建SpringBoot项目

<!-- more -->

## 准备工作

- Java 1.8
- Maven 3.6.3

### STS中Maven的配置

- `Spring Tool Suite 4`->`Preferences`->`Maven`->`Installations`->`Add`

![01.png](/images/20200825170603/01.png)

- 配置Maven安装目录

![02.png](/images/20200825170603/02.png)

- 选中新的配置->应用

![03.png](/images/20200825170603/03.png)

- `Maven`->`User Settings`->修改配置->应用

![04.png](/images/20200825170603/04.png)

## 通过官方的Starter创建项目

- `File`->`New`->`Spring Starter Project`

![05.png](/images/20200825170603/05.png)

- 配置项目参数->`Next`

![06.png](/images/20200825170603/06.png)

- 选择SpringBoot版本->`Finish`

![07.png](/images/20200825170603/07.png)

## 通过阿里云的Starter创建项目

- `File`->`New`->`Spring Starter Project`

![05.png](/images/20200825170603/05.png)

- 配置项目参数，将`Server URL`改为阿里云的Starter->`Next`

![08.png](/images/20200825170603/08.png)

- 如果版本显示错误，可以手动调整版本，在配置版本处不管版本号，选择`Next`

![09.png](/images/20200825170603/09.png)

- 手动调整版本号->`Finish`

![10.png](/images/20200825170603/10.png)


## 通过官网打包导入项目

- 在官网配置项目参数，下载打包的新项目[https://start.spring.io](https://start.spring.io)

![11.png](/images/20200825170603/11.png)

- 解压，导入项目到STS

- `File`->`Inport`->`Maven`->`Existing Maven Projects`->`Next`

![12.png](/images/20200825170603/12.png)

- 选择项目根目录->`Finish`

![13.png](/images/20200825170603/13.png)

## 通过普通Maven项目创建项目

- 创建一个简单的Maven项目

- `File`->`New`->`Other`->`Maven`->`Maven Project`->选择简单Maven项目->`Next`

![14.png](/images/20200825170603/14.png)

- 配置项目参数 ->`Finish`

![15.png](/images/20200825170603/15.png)

- 替换pom.xml文件内容

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.3.3.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.company</groupId>
	<artifactId>CGB-SPRINGBOOT-04</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>CGB-SPRINGBOOT-01</name>
	<description>Demo project for Spring Boot</description>

	<properties>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
			<exclusions>
				<exclusion>
					<groupId>org.junit.vintage</groupId>
					<artifactId>junit-vintage-engine</artifactId>
				</exclusion>
			</exclusions>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```

- 右键项目->`Maven`->`Update Project`

![16.png](/images/20200825170603/16.png)

- 选中`Force Update of Snapshots/Releases`强制更新->`OK`

![17.png](/images/20200825170603/17.png)

- 手动创建入口程序

- 新建Java文件，全局限定名为`com.company.CgbSpringboot04Application`

- 在类上定义注解`@SpringBootApplication`，并定义main方法

``` java
@SpringBootApplication
public class CgbSpringboot04Application {

    public static void main(String[] args) {
        SpringApplication.run(CgbSpringboot04Application.class, args);
    }
    
}
```

## 通过在其他机器的新项目复制

- 通过以上任何方式构建完整新项目后，压缩项目拷贝到其他机器

- 在pom.xml文件内调整参数

## 完成
