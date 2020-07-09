---
title: 【笔记】SQLite学习笔记
categories:
  - Database
date: 2020-07-05 09:33:01
---

## 前言

SQLite是遵守ACID的关系数据库管理系统，它包含在一个相对小的C程序库中。与许多其它数据库管理系统不同，SQLite不是一个客户端/服务器结构的数据库引擎，而是被集成在用户程序中。（[维基百科](https://zh.wikipedia.org/wiki/SQLite)）

<!-- more -->

## 安装sqlite

- MacOS新版本预装sqlite，如果没有可以使用brew安装

``` sh
brew install sqlite
```

## 启动sqlite

``` sh
sqlite3
```

## 基本命令

### 创建数据库

- 创建成功后会在命令行当前目录下生成`.db`文件

> `<database_name>`：数据库名（不可以包含中文）

``` sh
sqlite3 <database_name>.db
```

### 查看数据库

- 查看数据库存放位置

``` sqlite
.databases
```

### 创建数据表

> `<table_name>`：数据表名
> `<field_name>`：字段名
> `<type_of_data>`：数据类型
> `<length>`：长度
> `<constraint>`：约束

``` mysql
CREATE TABLE <table_name>(<field_name_1> <type_of_data> <constraint>, <field_name_2> <type_of_data> <constraint>);
```

#### 数据类型

> `NULL`：表示该值为NULL值。
> `INTEGER`：无符号整型值。
> `REAL`：浮点值。
> `TEXT`：文本字符串，存储使用的编码方式为UTF-8、UTF-16BE、UTF-16LE。
> `BLOB`：存储Blob数据，该类型数据和输入数据完全相同。

> 布尔数据类型：
>> SQLite并没有提供专门的布尔存储类型，取而代之的是存储整型1表示true，0表示false。

> 日期和时间数据类型：
>> 和布尔类型一样，SQLite也同样没有提供专门的日期时间存储类型，而是以TEXT、REAL和INTEGER类型分别不同的格式表示该类型

### 查看数据表

``` sqlite
.tables
```

### 删除数据表

``` sqlite
DROP TABLE <table_name>;
```

### 插入数据

> `<value>`：数据值

``` sqlite
INSERT INTO <table_name> VALUES (<value_1>, value_2);
INSERT INTO (<field_name_1>, <field_name_2>) VALUES (<value_1>, <value_2>);
```

### 查看数据

#### 查看所有字段的所有数据

``` sqlite
SELECT * FROM <table_name>;
```

#### 查看指定字段的所有数据

``` sqlite
SELECT <field_name> FROM <table_name>;
```

#### 查看指定的多个字段的所有数据

``` sqlite
SELECT <field_name_1>,<field_name_2> FROM <table_name>
```

#### 查看所有字段的指定数据

> `<operator>`：运算符

``` sqlite
SELECT * FROM <table_name> WHERE <field_name><operator><value>;
```

### 删除数据

``` sqlite
DELETE FROM <table_name> WHERE <field_name><operator><value>;
```

## 完成

程序媛
[博客园——OrangeAdmin](https://www.cnblogs.com/orangeform/archive/2012/02/22/2325258.html)



