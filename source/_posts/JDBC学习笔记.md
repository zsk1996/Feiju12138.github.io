---
title: 【笔记】JDBC学习笔记
categories:
  - Java
date: 2020-05-19 11:30:47
---

## 前言

JDBC学习笔记

<!-- more -->

## 准备工作

- 项目中导入对应版本的[mysql-connector-java-8.0.19.jar](https://dev.mysql.com/downloads/connector/j/)

## 加载驱动

### 低版本mysql

``` java
Class.forName("com.mysql.jdbc.Driver");
```

### 高版本mysql

``` java
Class.forName("com.mysql.cj.jdbc.Driver");
```

## 创建字符串连接

> `<table>`：表名

### 低版本mysql

``` java
Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/<table>", "root", "123456");
```

### 高版本mysql


``` java
Connection connection = DriverManager.getConnection("jdbc:mysql://localhost:3306/<table>?serverTimezone=UTC", "root", "123456");
```

## sql语句

### 静态sql语句

``` java
Statement statement = connection.createStatement(); 
```

### 动态sql语句

``` java
PrepareStatement prepareStatement = connection.prepareStatement();
```

## 执行sql语句

> `<sql>`：sql语句

### 执行查询语句

``` java
ResultSet resultSet = statement.executeQuery("<sql>");
```

#### 查询所有数据

- 返回结果集

``` java
ResultSet resultSet = statement.executeQuery("SELECT * FROM <table>");
```

### 执行修改语句

- 增删改均属于修改语句

``` java
ResultSet resultSet = statement.executeUpdate("<sql>");
```

## 处理结果集

### 返回int类型

> `<int>`：字段索引，从1开始
> `<string>`：字段名

``` java
rs.getInt("<int>");
rs.getInt("<string>"):
```

### 返回String类型

``` java
rs.getString("<int>");
rs.getString("<string>"):
```

## 关闭数据库连接

- 遵循后开先关的原则

### 关闭执行语句

``` java
resultSet.close();
```

### 关闭sql语句

#### 关闭静态sql语句

``` java
statement.close();
```

#### 关闭动态sql语句

``` java
prepareStatement.close();
```

### 关闭数据库连接

``` java
connection.close();
```

## 占位符

- 在动态sql语句中，常用`?`表示占位符

``` java
String sql = "INSERT INTO <table> (username, password, nickname) values(?, ?, ?)";
```

### 替换占位符

> `<parameterIndex>`：参数下标，从1开始
> `<x>`：相对应数据类型的值

``` java
prepareStatement.setByte(<parameterIndex>, <x>);
prepareStatement.setShort(<parameterIndex>, <x>);
prepareStatement.setInt(<parameterIndex>, <x>);
prepareStatement.setLong(<parameterIndex>, <x>);
prepareStatement.setDouble(<parameterIndex>, <x>);
prepareStatement.setFloat(<parameterIndex>, <x>);
prepareStatement.setString(<parameterIndex>, <x>);
```

## 参考文献

达内教育

