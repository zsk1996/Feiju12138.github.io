---
title: 【笔记】用IDEA创建一个Javaweb项目
categories:
  - Java
date: 2020-05-07 16:45:56
---

## 前言

用IDEA创建一个Javaweb项目

<!-- more -->

## 新建项目

- `Java Enterprise`->选择SDK版本->勾选`Web Application`

![01.png](/images/20200507164556/01.png)

- 项目命名->`finish`

## 创建classes目录和lib目录

- 在`web->WEB-INF`目录下分别创建`classes`目录和`lib`目录

![02.png](/images/20200507164556/02.png)

## 部署classes目录

- `File`->`Project Structure...`->`Modules`->`Paths`->勾选`Use module compule output path`

- 在`Output path`和`Test output path`都选择刚刚创建的`classes`目录

![03.png](/images/20200507164556/03.png)

## 部署lib目录

- `File`->`Project Structure...`->`Modules`->`Dependencies`->点击加号->`JARs or directories...`

- 选择刚刚创建的`lib`目录

![04.png](/images/20200507164556/04.png)

- 选择`Jar Directory`

![05.png](/images/20200507164556/05.png)

## 配置打包方式

- `File`->`Project Structure...`->`Artifacts`->选择项目->勾选`Include in project build`->勾选`Show content of elements`

![06.png](/images/20200507164556/06.png)

## 配置运行方式

- `Run`->`Edit Configurations...`->点击加号->选择`Tomcat Server`

- 点击`Configure...`选择配置好的相应版本Tomcat

如果没有任何配置好的Tomcat

点击加号->选择`Tomcat Home`->`OK`->`OK`

![07.png](/images/20200507164556/07.png)

- 去掉勾选`After launch`

- 选择浏览器

- 在`Tomcat Server Settings`配置Tomcat参数

![08.png](/images/20200507164556/08.png)

## 完成

## 参考文献

[CSDN——遇见1995](https://blog.csdn.net/weixin_38500325/article/details/82356175)

