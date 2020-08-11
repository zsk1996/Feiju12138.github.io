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

## 注释

### 单行注释

``` mysql
-- 注释内容
# 注释内容
```

### 多行注释

``` mysql
/* 注释内容 */
```

## 对数据库的操作

### 查询所有数据库

``` mysql
SHOW DATABASES;
```

### 创建数据库

``` mysql
CREATE DATABASE <database_name>;
```

#### 同时指定字符集

``` mysql
CREATE DATABASE <database_name> CHARSET utf8;
```

#### 如果不存在

``` mysql
CREATE DATABASE IF NOT EXISTS <database_name>;
```

#### 查看创建数据库语句

``` mysql
SHOW CREATE DATABASE <database_name>;
```

### 进入数据库

``` mysql
USE <database_name>;
```

#### 查看当前进入的数据库

``` mysql
SELECT database();
```

### 删除数据库

``` mysql
DROP DATABASE <database_name>;
```

#### 如果存在

``` mysql
DROP DATABASE IF EXISTS <database_name>;
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
> `<length>`：长度（根据需求添加）
> `<constraint>`：约束（根据需求添加）

``` mysql
CREATE TABLE <table_name>(
    <field_name_1> <type_of_data>(<length>) <constraint>,
    <field_name_2> <type_of_data>(<length>) <constraint>
);
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

### 为查询到的数据定义表头别名

``` mysql
SELECT <old_field_name_1> AS <new_field_name_1> FROM <table_name>;
```

#### 简写

``` mysql
SELECT <old_field_name_1> <new_field_name_1> FROM <table_name>;
```

#### 表明也可以设置别名

- 表名也可以设置别名，也可以简写
- 但是指定表名别名后，后面只能使用别名，不能再使用原表名

``` mysql
SELECT * FROM <old_table_name> AS <old_table_name>;

SELECT * FROM <old_table_name> <old_table_name>;
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

- 配合通配符使用

> `%`：表示0或多个任意的字符
> `_`：表示1个任意的字符

##### 测试空值

- 判断值是否为空

`IS NULL`、`IS NOT NULL`

###### 空值替换

- 一些数据存在NULL值时，参与运算结果为NULL，不准确，为了解决问题，将NULL值替换为`0`

> `<field_name>`：可能会出现NULL值的字段

``` mysql
SELECT IFNULL(<field_name>, 0) FROM <table_name>;
```

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

#### 聚合函数（多行函数）

- 不能用在WHERE子句中
- 会默认直接丢弃NULL值

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

###### 计算所有数据总行数

`COUNT(*)`

#### 聚合函数的应用

##### 查询计算后的数据

> `<function>`：函数名

``` mysql
SELECT <function>(<field_name>) FROM <table_name>;
```

##### 分组查询

- 将查询到的数据根据字段进行分组

``` mysql
SELECT <field_name> FROM <table_name> GROUP BY <field_name>;
```

###### 筛选

- 查询分组后筛选符合条件的数据

``` mysql
SELECT <field_name> FROM <table_name> GROUP BY <filed_name> HAVING <field_name><operator><value>;
```

__WHERE和HAVING的区别__

WHERE是在分组之前,对记录进行筛选过滤，HAVING是在分组之后,对记录进行筛选过滤
WHERE子句中不能使用多行函数以及列别名，HAVING子句中可以使用多行函数以及列别名、表别名

##### 排序

- 默认为升序

###### 升序（从小到大）

``` mysql
SELECT <field_name> FROM <table_name> GROUP BY <field_name>;

SELECT <field_name> FROM <table_name> GROUP BY <field_name> ESC;
```

###### 降序（从大到小）

``` mysql
SELECT <field_name> FROM <table_name> GROUP BY <field_name> DESC;
```

### 多表查询（连接查询）

- 可以两个表，也可以多个表

``` mysql
SELECT <table_name_x>.<field_name_x> FROM <table_name_1>,<table_name_2>,<table_name_3> WHERE <table_name_1>.<field_name_1>=<table_name_2>.<field_name_1> AND <table_name_2>.<field_name_2>=<table_name_3>.<field_name_2>;

SELECT <table_name_x>.<field_name_x> FROM <table_name_2> JOIN <table_name_1> ON <table_name_2>.<field_name_1>=<table_name_1>.<field_name_1> JOIN <table_name_3> ON <table_name_2>.<field_name_2>=<table_name_3><field_name_2>;
```

#### 左外连接查询

- 左侧显示所有数据，右侧如果没有对应关系则显示为null

``` mysql
SELECT * FROM <table_name_1> LEFT JOIN <table_name_2> ON <table_name_1>.<field_name_2>=<table_name_2>.<field_name_1>;
```

#### 右外连接查询

- 右侧显示所有数据，左侧如果没有对应关系则显示为null

``` mysql
SELECT * FROM <table_name_1> RIGHT JOIN <table_name_2> ON <table_name_1>.<field_name_2>=<table_name_2>.<field_name_1>;
```

#### （模拟）全外连接查询

##### 去重（取交集）

- 通过`UNION`关键字将左外连接和右外连接取`交集`，模拟全外连接查询
- 两表展示出的列数必须相同
- 两表展示的表头名如果不同，可以用`AS`关键字为表头添加别名

``` mysql
SELECT id,name FROM <table_name_1> LEFT JOIN <table_name_2> ON <table_name_1>.<field_name_2>=<table_name_2>.<field_name_1>
UNION
SELECT id,name FROM <table_name_2> RIGHT JOIN <table_name_2> ON <table_name_1>.<field_name_2>=<table_name_2>.<field_name_1>;
```

##### 不去重（取并集）

- 通过`UNION ALL`关键字将左外连接和右外连接取`并集`，模拟全外连接查询

``` mysql
SELECT id,name FROM <table_name_1> LEFT JOIN <table_name_2> ON <table_name_1>.<field_name_2>=<table_name_2>.<field_name_1>
UNION ALL
SELECT id,name FROM <table_name_2> RIGHT JOIN <table_name_2> ON <table_name_1>.<field_name_2>=<table_name_2>.<field_name_1>;
```

### 分页查询

> `<index_first>`：每页的第一条数据在总数据中的下标（下标从0开始），所以公式为`(当前页码数-1)*每页显示的数据总数`
> `<index_all>`：每页显示的数据总数

``` mysql
SELECT <field_name> FROM <table_name> LIMIT <index_first>,<index_all>;
```

### 子查询

- 将一个sql语句查询的结果作为条件完成另一个sql语句查询

``` mysql
SELECT * FROM <table_name_1> WHERE <field_name_1><operator>(SELECT <field_name_2> FROM <table_name_2>);
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

### 非空约束

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) NOT NULL);
```

#### 可以为空（默认）

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) NULL);
```

### 主键约束

- 作为列的完整性约束
- 主键必须为非空

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) PRIMARY KEY NOT NULL);

CREATE TABLE <table_name>(
    <field_name_1> <operator>(length),
    <field_name_2> <operator>(length),
    PRIMARY(<field_name_1>)
);
```

#### 联合主键

- 每个主键字段的数值可以重复，但是多个联合主键的数值的并集不可以重复

``` mysql
CREATE TABLE <table_name>(
    <field_name_1> <operator>(length),
    <field_name_2> <operator>(length),
    PRIMARY(<field_name_1>, <field_name_2>)
);
```

#### 主键自增

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) PRIMARY KEY NOT NULL AUTO_INCREMENT);
```

### 替代键约束

- 替代键是没有被选作主键的候选键

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) UNIQUE);

CREATE TABLE <table_name>(<field_name> <operator>(length), UNIQUE(<field_name>));
```

### 唯一约束

- 如果为一个列添加了唯一约束，那么这个列的值就必须是唯一的（即不能重复），但可以为空

``` mysql
CREATE TABLE <table_name>(<field_name> <operator>(length) UNIQUE);
```

### 外键约束

- 通过外键约束将表与表建立联系，当出现有损表的完整性操作时，外键约束会对表进行保护

#### 一对多

##### 创建表时直接添加外键

> `<id_myself>`：当前表中设置为外键的字段名（例如本表中，可以将`<field_name_1>`作为主键，将`<field_name_2>`作为外键赋值给`<id_myself>`）
> `<table_name_other>`：关联为外键的表名
> `<id_other>`：关联为外键的表中的字段

``` mysql
CREATE TABLE <table_name>(
    <field_name_1> <type_of_data>,
    <field_name_2> <type_of_data>,
    FOREIGN KEY(<id_myself>) REFERENCES <table_name_other>(<id_other>)
);
```

##### 对已创建的表添加外键

> `<constarint_name>`：自定义外键名，可以省略

``` mysql
ALTER TABLE <table_name> ADD CONSTRAINT <constarint_name> FOREIGN KEY(<id_myself>) REFERENCES <table_name_other>(<id_other>);
```

#### 多对多

``` mysql
CREATE TABLE <table_name>(
    <id_myself_1> int,
    <id_myself_2> int,
    primary key(<id_myself_1>,<id_myself_2>),
    foreign key(<id_myself_1>) references <table_name_other_1>(<id_other_1>),
    foreign key(<id_myself_2>) references <table_name_other_2>(<id_other_2>)
);
```

## 其他函数

|函数|备注|
|---|---|
|curdate()|获取当前日期，格式是：年月日|
|curtime()|获取当前时间 ，格式是：时分秒|
|sysdate()/now()|获取当前日期+时间，格式是：年月日 时分秒|
|year(date)|返回date中的年份|
|month(date)|返回date中的月份|
|day(date)|返回date中的天数|
|hour(date)|返回date中的小时|
|minute(date)|返回date中的分钟|
|second(date)|返回date中的秒|
|CONCAT(s1,s2..)|将s1,s2 等多个字符串合并为一个字符串|
|CONCAT_WS(x,s1,s2..)|同CONCAT(s1,s2,..)函数，但是每个字符串之间要加上x，x是分隔符|

## 完成

