---
title: 【笔记】Lombok学习笔记
categories:
  - Java
date: 2020-09-02 12:32:34
---

## 前言

Project Lombok is a java library that automatically plugs into your editor and build tools, spicing up your java.
Never write another getter or equals method again, with one annotation your class has a fully featured builder, Automate your logging variables, and much more.（[官网](https://projectlombok.org)）

<!-- more -->

## 项目引入Lombok

- 编辑pom.xml配置文件

``` xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
</dependency>
```

## 安装Lombok插件

- 在SpringToolSuite4 For Mac安装Lombok插件

- 找到Lombok的jar包

`~/.m2/repository/org/projectlombok/lombok/1.18.12/lombok-1.18.12.jar`

- 运行jar包

``` sh
java -jar lombok-1.18.12.jar
```

![01.png](/images/20200902123234/01.png)

- 默认会扫描到Eclipse但是扫描不到SpringToolSuite4，点`Spedify location`手动指定`SpringToolSuite4`安装根目录

MacOS无法选中根目录，需要指定到`SpringToolSuite4.ini`配置文件

![02.png](/images/20200902123234/02.png)

- 选中需要安装插件的软件

![03.png](/images/20200902123234/03.png)

- 安装完成

## 使用Lombok注解

### 编译时为POJO类自动生成set、get、toString、equals等方法

- 定义在类上

``` java
@Data
```

### 编译时为POJO类自动生成get方法

- 定义在类上，为类的所有属性添加get方法
- 定义在属性上，为指定属性添加get方法

``` java
@Getter
```

### 编译时为POJO类自动生成set方法

- 定义在类上，为类的所有属性添加set方法
- 定义在属性上，为指定属性添加set方法

``` java
@Setter
```

### 编译时为POJO类自动生成toString方法

- 定义在类上

``` java
@ToString
```

### 编译时为POJO类自动生成全参构造方法方法

- 定义在类上

``` java
@AllArgsConstructor
```

### 编译时为POJO类自动生成无参构造方法

- 定义在类上

``` java
@NoArgsConstructor
```

### 自动创建名为log的Slf4j对象

- 定义在类上

``` java
@Slf4j
```

### 启动链式加载

``` java
@Accessors(chain = true)
```

## 完成

## 参考文献

[CSDN——一缕82年的清风](https://blog.csdn.net/lsqingfeng/article/details/89842258)

