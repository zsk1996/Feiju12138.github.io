---
title: 【代码】JDBC 快速入门
categories:
  - Java
date: 2020-01-25 23:12:25
---

## 前言

`JDBC`快速入门程序代码

<!-- more -->

## 准备工作

- 项目中导入[mysql-connector-java-8.0.19.jar](https://dev.mysql.com/downloads/connector/j/)包

## 源代码

``` java
package cn.itcast.jdbc;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;

/**
 * JDBC快速入门
 */
public class JdbcDemo1 {

    public static void main(String[] args) throws Exception {

        // 1. 导入驱动jar包

        // 2. 注册驱动
        Class.forName("com.mysql.cj.jdbc.Driver");

        // 3. 获取数据库的连接对象
        Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/xscj?serverTimezone=UTC", "root", "123456"); // 如果连接本机且端口号为默认，可以省略不写`localhost:3306`

        // 4. 定义sql语句
        String sql = "UPDATE XS SET 性别=0 WHERE 学号=081241";

        // 5. 获取执行sql的对象 Statement
        Statement stmt = conn.createStatement();

        // 6. 执行sql
        int count = stmt.executeUpdate(sql);

        // 7. 处理结果
        System.out.println(count);

        // 8. 释放资源
        stmt.close();
        conn.close();

    }

}
```

## 完成

## 参考文献

[哔哩哔哩——怀瑾于轻L](https://www.bilibili.com/video/av63673244?p=3)

