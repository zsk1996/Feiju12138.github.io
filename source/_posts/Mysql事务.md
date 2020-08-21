---
title: 【笔记】Mysql事务
categories:
  - Database
date: 2020-08-19 11:02:27
---

## 前言

数据库事务（简称：事务）是数据库管理系统执行过程中的一个逻辑单位，由一个有限的数据库操作序列构成。（[维基百科](https://zh.wikipedia.org/wiki/数据库事务)）

<!-- more -->

## 事务的四个特性

### 原子性

- 事务中的所有操作都是一个整体，不能被分隔，要么全都执行成功，要么全都执行失败

### 一致性

- 在事务执行前后的业务数据之和是保持一致的

### 隔离性

- 在事务并发时，多个事务之间是具有隔离性，在一个事务中看不到另外一个事务正在进行中的状态

### 持久性

- 事务提交后，在事务中对数据的更新会持久的保存到数据库中
- 在事务提交之前，事务中执行的操作，并没有真正的更新到数据库

## Mysql中的事务

- 默认情况下，Mysql中每一条SQL都是一个事务
- 每次在执行SQL语句之前，会默认开启事务，在执行这条SQL语句之后，会自动提交事务
- 如果需要让两条或两条以上的SQL语句在执行时，在一个事务中，需要在执行之前开启事务，在最后一条SQL语句执行完后，立即结束事务

- Mysql中开启事务：`start transcation`
- Mysql中结束事务：`commit`（提交）/`rollbach`（回滚）
- 如果事务中所有SQL语句都执行成功了，最后我们提交事务
- 如果事务中的SQL语句有一条执行失败，就按照全部失败来处理，最后我们回滚事务

``` mysql
mysql> start transcation;
mysql> commit;
mysql> rollbach;
```

## JDBC中的事务

### 关闭JDBC自动提交事务（默认开启事务）

``` jave
conn.setAutoCommit(false);
```

### 提交事务

``` java
conn.commit();
```

### 回滚事务

``` java
conn.rollback();
```

## 事务并发读问题

### 脏读（dirty read）

- 在一个事务中，读取到另一个事务未提交更新的数据，即读取到了脏数据；

### 不可重复读（unrepeatable read）

- 对同一记录的两次读取结果不一致，因为在两次查询期间，有另一事务对该记录做了修改（是针对修改操作）

### 幻读（虚读）（phantom read）

- 对同一张表的两次查询结果不一致，因为在两次查询期间，有另一事务进行了插入或者是删除操作(是针对插入或删除操作)

## 事务的隔离级别

### READ UNCOMMITTED（读未提交数据）

- 安全性最差，可能出现任何事务并发问题(比如脏读、不可以重复读、幻读等)
- 但性能最好（不推荐）

### READ COMMITTED（读已提交数据）（Oracle默认）

- 安全性较差
- 性能较好
- 可以防止脏读，但不能防止不可重复读，也不能防止幻读；

### REPEATABLE READ（可重复读）（MySQL默认）

- 安全性较高
- 性能较差
- 可以防止脏读和不可重复读，但不能防止幻读问题；

### SERIALIZABLE（串行化）

- 安全性最高，不会出现任何并发问题，因为它对同一数据的访问是串行的，非并发访问；
- 性能最差(不推荐)

MySQL的默认隔离级别为REPEATABLE READ，即可以防止脏读和不可重复读

## Mysql设置隔离级别

### 查看当前的事务级别

``` mysql
SELECT @@@@tx_isolation;
```

### 设置隔离级别为 读未提交

``` mysql
SET tx_isolation='read-uncommitted';
```

### 设置隔离级别为 读已提交

``` mysql
SET tx_isolation='read-committed';
```

### 设置隔离级别为 可重复读

``` mysql
SET tx_isolation='repeatable-read';
```

### 设置隔离级别为 串行化

``` mysql
SET tx_isolation='serialiable';
```

## JDBC设置隔离级别

``` java
Connection.setTransactionIsolation(int level);
```

### 设置隔离级别为 读未提交

``` java
Connection.setTransactionIsolation(1);

Connection.setTransactionIsolation(Connection.TRANSACTION_READ_UNCOMMITTED);
```

### 设置隔离级别为 读已提交

``` java
Connection.setTransactionIsolation(2);

Connection.setTransactionIsolation(Connection.TRANSACTION_READ_COMMITTED);
```

### 设置隔离级别为 可重复读

``` java
Connection.setTransactionIsolation(4);

Connection.setTransactionIsolation(Connection.TRANSACTION_REPEATABLE_READ);
```

### 设置隔离级别为 串行化

``` java
Connection.setTransactionIsolation(8);

Connection.setTransactionIsolation(Connection.TRANSACTION_SERIALIZABLE);
```

### 不使用事务

``` java
Connection.setTransactionIsolation(0);

Connection.setTransactionIsolation(Connection.TRANSACTION_NONE);
```

## 完成
