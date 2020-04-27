---
title: 【笔记】Hadoop 群启
categories:
  - 大数据
date: 2020-02-04 15:55:10
---

## 前言

在分布式模式下，实现“群启”

<!-- more -->

## 配置从机

- 在`NameNode`编辑`hadoop/etc/hadoop/slaves`文件

- 添加从机信息

``` sh
hadoop102
hadoop103
hadoop104
```

- 同步

## 群启 HDFS

- 在配置了`NameNode`的`hadoop102`群启`HDFS`

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/start-dfs.sh
``` 

## 确认

### 在各个计算机上查看程序运行情况

``` sh
jps
```

### 在浏览器上查看计算机运行情况

- 进入网页`hadoop102:50070`

## 群启 YARN

- 在配置了`ResourceManager`的`hadoop103`群启`YARN`

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/start-yarn.sh
```

## 确认

### 在各个计算机上查看程序运行情况

``` sh
jps
```

### 在浏览器上查看计算机运行情况

- 进入网页`hadoop103:8088`

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)

