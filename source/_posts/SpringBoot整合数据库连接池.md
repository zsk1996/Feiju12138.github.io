---
title: 【笔记】SpringBoot整合数据库连接池
categories:
  - Java
date: 2020-08-28 17:04:15
---

## 前言

SpringBoot整合数据库连接池
数据库以Mysql为例
连接池以HikariCP为例

<!-- more -->

## 创建项目时添加依赖

- 在项目依赖搜索`JDBC`添加`JDBC API`和`Mysql Driver`的依赖包

- 创建后的pom.xml文件会自动添加`Mysql驱动依赖`和`Spring对象创建JDBC依赖`（并默认下载HikariCP连接池）

Mysql依赖

``` xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```

Spring对象创建JDBC依赖

``` xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jdbc</artifactId>
</dependency>
```

## 配置连接池

- 在`src/main/resources/application.properties`配置连接池

``` properties
spring.datasource.url=jdbc:mysql://localhost:3306/dbgoods?serverTimezone=UTC&characterEncoding=utf8
spring.datasource.username=root
spring.datasource.password=123456
```

### 更多配置

- 在`src/main/resources/application.properties`配置连接池
- 最大连接数通常设置为`最大线程数*核心数+硬盘数`

``` properties
spring.datasource.type=com.zaxxer.hikari.HikariDataSource
spring.datasource.hikari.minimum-idle=5
spring.datasource.hikari.maximum-pool-size=15
spring.datasource.hikari.auto-commit=true
spring.datasource.hikari.idle-timeout=30000
spring.datasource.hikari.pool-name=DatebookHikariCP
spring.datasource.hikari.max-lifetime=1800000
spring.datasource.hikari.connection-timeout=30000
spring.datasource.hikari.connection-test-query=SELECT 1
```

## 创建测试类

``` java
@SpringBootTest
public class DataSourceTests {
    
    @Autowired
    private DataSource dataSource;

    @Test
    public void testConnection() throws Exception{
        System.out.println(dataSource.getConnection());
    }
    
}
```

## 完成

