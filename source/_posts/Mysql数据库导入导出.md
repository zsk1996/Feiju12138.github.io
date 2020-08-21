---
title: 【笔记】Mysql数据库导入导出
categories:
  - Database
date: 2020-08-05 18:38:10
---

## 前言

Mysql数据库备份和恢复

<!-- more -->

## 导出（备份）

### 导出某数据库的某数据表

> `<root>`：登陆Mysql的用户名
> `<pwd>`：登陆Mysql的密码
> `<database>`：数据库名
> `<table>`：数据表名

``` sh
mysqldump -u<root> -p<pwd> <database> <table> > Backup.sql
```

### 导出某数据库的所有数据

``` sh
mysqldump -u<root> -p<pwd> <database> > Backup.sql
```

### 导出所有库的所有数据

- 不适用所有版本

``` sh
mysqldump -u<root> -p<pwd> --all-databases > Backup.sql
```

## 导入（恢复）

### 直接导入

> `<database>`：导入到指定的数据库

``` sh
mysql -u<root> -p<pwd> <database> < Backup.sql
```

### 执行备份文件的源码

- 首先进入到Mysql

``` sh
mysql -u<root> -p<pwd>
```

- 然后创建并进入 需要导出的数据 所 要求存放 的数据表

> `<Backup.sql>`：`.sql`存放的目录

``` sql
source <Backup.sql>
```

## 完成

## 参考文献

[菜鸟笔记](https://www.runoob.com/mysql/mysql-database-export.html)

