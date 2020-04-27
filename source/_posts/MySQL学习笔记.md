---
title: 【笔记】MySQL 学习笔记
date: 2019-12-15 09:06:01
tage:
categories:
- Database
---

## 前言

`MySQL`原本是一个开放源码的关系数据库管理系统，原开发者为瑞典的`MySQL AB`公司，该公司于2008年被昇阳微系统（Sun Microsystems）收购。2009年，甲骨文公司（Oracle）收购昇阳微系统公司，MySQL成为Oracle旗下产品。（[维基百科](https://zh.wikipedia.org/wiki/MySQL)）

<!-- more -->

## 对数据库的操作

### 查询所有数据库

``` mysql
SHOW DATABASES;
```

### 创建数据库

``` mysql
CREATE DATABASES <database_name>;
```

### 打开数据库

``` mysql
USE <database_name>;
```

### 删除数据库

``` mysql
DROP DATABASE <database_name>;
```

### 修改数据库的默认字符集

``` mysql
ALTER DATABASE <database_name> DEFAULT CHARACTER SET <character_set>;
```

### 修改默认校对规则

``` mysql
ALTER DATABASE <database_name> DEFAULT COLLATE <proofreading_rules>;
```

## 对数据表的操作

### 创建数据表

> `<field_name>`：字段名
> `<type_of_data>`：数据类型
> `<length>`：长度
> `<constraint>`：约束

``` mysql
CREATE TABLE <table_name>(<field_name_1> <type_of_data>(<length>) <constraint>, <field_name_2> <type_of_data>);
```

### 查询所有数据表

``` mysql
SHOW TABLES;
```

### 查询数据表结构

``` mysql
DESC <table_name>
```

### 查询数据表结构（详细）

``` mysql
SHOW CREATE TABLE <table_name>
```

### 修改数据表名

``` mysql
ALTER TABLE <old_table_name> RENAME TO <new_table_name>
```

### 删除数据表

``` mysql
DROP TABLE <table_name>;
```

## 对字段的操作

### 增加字段

``` mysql
ALTER TABLE <table_name> ADD <new_filed_name> <new_type_of_data>(<length>) <constraint>;
ALTER TABLE <table_name> ADD <new_filed_name> <new_type_of_data>(<length>) <constraint> first;
ALTER TABLE <table_name> ADD <new_filed_name> <new_type_of_data>(<length>) <constraint> after <old_field_name>;
```

### 删除字段

``` mysql
ALTER TABLE <table_name> DROP COLUMN <filed_name>;
```

### 修改数据类型

``` mysql
ALTER TABLE <table_name> MODIFY <field_name> <new_type_of_data>;
```

### 修改字段

``` mysql
ALTER TABLE <table_name> CHANGE <old_field_name> <new_field_name> <new_type_of_data>(<new_length>) <new_constraint>
```

#### 修改字段名

``` mysql
ALTER TABLE <table_name> CHANGE <old_field_name> <new_field_name> <new_type_of_data>;
```

#### 修改字段排列位置

``` mysql
ALTER TABLE <table_name> MODIFY <field_name_1> <type_of_data_1> first <field_name_2>;
ALTER TABLE <table_name> MODIFY <field_name_2> <type_of_data_1> after <field_name_2>;
```

## 对数据的操作

### 插入数据

``` mysql
INSERT INTO <table_name>(<field_name_1>, <field_name_2>) VALUES(<value_1>, <value_2>);
INSERT INTO <table_name> SET <field_name_1>=<value_1>, <field_name_2>=<value_2>;
```

### 插入数据（多条）

``` mysql
INSERT INTO <table_name>(<field_name_1>, <field_name_2>) VALUES(value_1_1, value_1_2),(value_2_1, value_2_2);
```

### 插入数据（所有字段）

``` mysql
INSERT INTO <table_name> VALUES(<value_1>, <value_2>);
```

### 更新数据

``` mysql
UPDATE <table_name> SET <field_name_1>=<value_1>, <field_name_2>=<value_2>
```

### 修改数据

``` mysql
REPLACE INTO <table_name> SET <field_name_1>=<value_1>, <field_name_2>=<value_2>;
```

### 删除所有数据

``` mysql
DELETE FROM <table_name>;
TRUNCATE TABLE <table_name>;
```

### 删除指定数据

``` mysql
DELETE FROM <table_name> WHERE <field_name><operator><value>
```

### 查询所有数据

``` mysql
SELECT * FROM <table_name>;
```

### 查询部分数据

``` mysql
SELECT <field_name_1>,<field_name> FROM <table_name>;
```

### 查询到的数据重命名字段显示

``` mysql
SELECT <old_field_name_1> AS <new_field_name_1>, <old_field_name_2> AS <new_field_name_2> FROM <table_name>;
```

### 按需求查看数据

#### 运算符

##### 比较运算

- 比较两个表达式的大小

`=`、`<`、`>`、`<=`、`>=`、`<>`、`!=`、`!<`、`!>`

##### 多重条件

- 对两个表达式进行`与或非`的运算

`AND`、`OR`、`NOT`

##### 确定范围

- 判断值是否在指定的范围内

`BETWEEN...AND...`、`NOT BETWEEN...AND...`

##### 确定集合

- 查询值是否属于列表值之一

`IN`、`NOT IN`

##### 字符匹配

- 用于模糊查询

`LIKE`、`NOT LIKE`

##### 测试空值

- 判断值是否为空

`IS NULL`、`IS NOT NULL`

#### 运算符的应用

##### 按规则查询数据

> `<operator>`：运算符

``` mysql
SELECT * FROM <table_name> WHERE <field_name><operator><value>;
```

##### 按规则替换数据

``` mysql
SELECT CASE WHEN <field_name><operator><old_value> THEN <new_value> END FROM <table_name>
```

##### 查询重新计算后的数据

> `<operator>`：这里的运算符，指的是`+`、`-`、`*`、`/`、`%`

``` mysql
SELECT <field_name><operator> FROM <table_name>
```

##### 不显示重复结果

``` mysql
SELECT DISTINCT <field_name> FROM <table_name>
```

#### 聚合函数

##### 求和

- 计算一个数值列的总和

`SUM()`

##### 求平均值

- 计算一个数值列的平均值

`AVG()`

##### 求最大值

- 返回指定列中的最大值

`MAX()`

##### 求最小值

- 返回指定列中的最小值

`MIN()`

##### 计算总数

- 计算符合查询条件的总行数

`COUNT()`

#### 聚合函数的应用

##### 查询计算后的数据

> `<function>`：函数名

``` mysql
SELECT <function>(<field_name>) FROM <table_name>;
```

##### 分组查询

- 将查询到的数据根据字段进行分组

``` mysql
SELECT <field_name> FROM <table_name> GROUP BY <field_name>
```

###### 筛选

- 查询分组后筛选符合条件的数据

``` mysql
SELECT <field_name> FROM <table_name> GROUP BY <filed_name> HAVING <field_name><operator><value>
```

### 多表查询

``` mysql
SELECT <table_name_x>.<field_name_x> FROM <table_name_1>,<table_name_2>,<table_name_3> WHERE <table_name_1>.<field_name_1>=<table_name_2>.<field_name_1> AND <table_name_2>.<field_name_2>=<table_name_3>.<field_name_2>;
SELECT <table_name_x>.<field_name_x> FROM <table_name_2> JOIN <table_name_1> ON <table_name_2>.<field_name_1>=<table_name_1>.<field_name_1> JOIN <table_name_3> ON <table_name_2>.<field_name_2>=<table_name_3><field_name_2>;
```

## 对视图的操作

- 将特定条件下的查询结果创建为视图，可以通过对视图的操作简便查询

### 创建视图

> `<select>`：select语句

``` mysql
CREATE VIEW <view_name> AS <select>;
```

### 重建视图

``` mysql
REPLACE VIEW <view_name> AS <select>;
```

### 创建视图（强制）

``` mysql
CREATE OR REPLACE VIEW <view_name> AS <select>;
```

### 查询所有视图

``` mysql
SHOW TABLES;
```

### 查询视图结构

``` mysql
DESC <view_name>;
```

### 修改视图

``` mysql
ALTER VIEW <view_name> AS <select>;
```

### 删除视图

``` mysql
DROP VIEW <view_name>;
```

### 查询视图中的数据

``` mysql
SELECT * FROM <view_name>;
SELECT <field_name> FROM <view_name>;
```

### 插入数据

``` mysql
INSERT INTO <view_name> VALUES(<value_1>, <value_2>);
```

### 修改数据

``` mysql
UPDATE <view_name> SET <field_name>=<value>;
```

### 删除数据

``` mysql
DELETE FROM <view_name> WHERE <field_name>=<value>;
```

## 对索引的操作

### 查看所有索引

``` mysql
SHOW INDEX FROM <table_name>;
```

### 创建索引

``` mysql
CREATE INDEX <index_name> ON <table_name>(<field_name>);
ALTER TABLE <table_name> ADD INDEX <index_name>(<field_name_1>, <field_name_2>);
CREATE TABLE <table_name>(<field_name> <operator>(<length>), INDEX <index_name>(field_name));
```

### 删除索引

``` mysql
DROP INDEX <index_name> <table_name>;
```

## 对约束的操作

### 主键约束

- 作为列的完整性约束

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) PRIMARY KEY);
CREATE TABLE <table_name>(<field_name_1> <operator>(length), <field_name_2> <operator>(length), PRIMARY(<field_name_1>, <field_name_2>));
```

### 替代键约束

- 替代键是没有被选作主键的候选键

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) UNIQUE);
CREATE TABLE <table_name>(<field_name> <operator>(length), UNIQUE(<field_name>));
```

## 参考文献

工单课堂

