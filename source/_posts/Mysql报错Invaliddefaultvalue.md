---
title: 【踩坑】Mysql报错Invalid default value
categories:
  - Database
date: 2020-08-17 16:44:39
---

## 前言

Mysql在创建表时，指定某个timestamp类型的默认值为`0000-00-00 00:00:00`时报错：`ERROR 1067 (42000): Invalid default value for 'order_time'`

<!-- more -->

## 原因

- Mysql5.6以后`sql_mode`中多了一条`NO_ZERO_DATE`（不允许时间值全部为0）

## 解决问题

- 重新配置`sql_mode`让它支持全部为0的时间值

``` mysql
mysql> set sql_mode="ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION";
```

## 报错

- 再次报错：`ERROR 1231 (42000): Variable 'sql_mode' can't be set to the value of 'NO_AUTO_CREATE_USER'`

## 原因

- Mysql8.0以上已经取消了`NO_AUTO_CREATE_USER`这个关键字

## 解决问题

- 重新配置`sql_mode`并删掉`NO_AUTO_CREATE_USER`关键字

``` mysql
mysql> set sql_mode="ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_ENGINE_SUBSTITUTION";
```

## 完成

## 参考文献

[CSDN——linmengmeng_1314](https://blog.csdn.net/linmengmeng_1314/article/details/81269576)
[简书——神经电泳实现师](https://www.jianshu.com/p/8f4b930295fb)
[CSDN——Dreamboy_w](https://blog.csdn.net/Dreamboy_w/article/details/99888907)
[简书——丶Rainbow丨](https://www.jianshu.com/p/62c769e8d0f0)

