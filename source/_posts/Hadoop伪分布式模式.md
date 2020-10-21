---
title: 【笔记】Hadoop 伪分布式模式
categories:
  - Big Data
date: 2020-01-31 23:36:54
---

## 前言

启动`HDFS`并运行`MapReduce`程序

<!-- more -->

## 准备工作

- 开启`Mac`的`ssh`

![01.png](/images/20200131233654/01.png)

## 配置 core-site.xml

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/core-site.xml
```

### 添加内容

- 在`<configuration></configuration>`标签内添加配置

``` xml
<!-- 指定HDFS中NameNode的地址 -->
<property>
    <name>fs.default.name</name>
    <value>hdfs://localhost:9000</value>
</property>

<!-- 指定Hadoop运行时产生文件的存储目录 -->
<property>
    <name>hadoop.tmp.dir</name>
    <value>/Users/hatsunemiku/.hadoop/data/tmp</value>
</property>
```

## 配置 hdfs-site.xml 文件

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/hdfs-site.xml
```

### 添加内容

- 在`<configuration></configuration>`标签内添加配置

``` xml
<property>
    <!-- 指定HDFS副本的数量 -->
    <name>dfs.replication</name>
    <value>1</value>
</property>
```

## 首次启动格式化

``` sh
/usr/local/Cellar/hadoop/3.2.1/libexec/bin/hdfs namenode -format
```

## 启动 namenode 节点

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/hadoop-daemon.sh start namenode
```

## 启动 datanode 节点

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/hadoop-daemon.sh start datanode
```

## 确认

- 查看正在运行的`java`程序

``` sh
jps
```

- 进入网页`localhost:9870`

![02.png](/images/20200131233654/02.png)

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)
[简书——张照博](https://www.jianshu.com/p/a86ccd96b78a)
