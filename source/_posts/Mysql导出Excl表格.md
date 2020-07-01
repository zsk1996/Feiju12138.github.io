---
title: 【笔记】Mysql导出Excl表格
categories:
  - Database
date: 2020-06-17 17:40:28
---

## 前言

将Mysql数据表导出为Excl表格

<!-- more -->

## 查看是否可以导出

``` mysql
mysql> SHOW VARIABLES LIKE "secure_file_priv";
```

> `NULL`：表示禁止任何目录的导入导出
> `无内容`：表示允许任何目录的导入导出
> `指定内容`：表示仅允许指定目录的导入导出

## 修改配置

- 由于默认配置下不允许导入导出，所以需要修改配置

- 编辑配置文件（MacOS下配置文件在`/usr/local/etc/my.cnf`）

- 如果`[mysqld]`下有`secure_file_priv`键，则直接修改为空，如果没有则添加

``` sh
secure_file_priv =
```

## 重启mysql

- Mac下如下操作

``` sh
brew services restart mysql
```

## 导出数据表

- 登录mysql

``` sh
mysql -u root -p
```

- 进入需要导出的数据库

``` sh
mysql> USE tr;
```

- 导出`tr_model`数据表为Excl文件，并存储在`Downloads`目录下

``` sh
mysql> SELECT * FROM tr_model INTO OUTFILE '/Users/hatsunemiku/Downloads/test.xls';
```

## 导出后乱码（可选）

- Excl默认编码为`gb2312`，而Linux默认编码为UTF-8，所以可以通过记事本打开`.xls`文件，然后另存为`gb2312`编码的文件，即可解决乱码

## 完成

## 参考文献

[CSDN——小迷童](https://blog.csdn.net/ljguo212/article/details/17147877)
[博客园——kaizen](https://www.cnblogs.com/Braveliu/p/10728162.html)

