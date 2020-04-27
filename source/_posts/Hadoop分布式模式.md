---
title: 【笔记】Hadoop 分布式模式
categories:
  - 大数据
date: 2020-02-02 12:00:11
---

## 前言

`Hadoop`分布式模式，至少6台计算机（学习阶段使用3台）

<!-- more -->

## 集群部署规则

### 标准阶段规则

|hadoop102|hadoop103|hadoop104|hadoop105|hadoop106|hadoop107|
|---|---|---|---|---|---|
|NameNode|SecondaryNameNode|DataNode & NameManageer|DataNode & NameManager|DataNode & NameManager|ResourceManager|

#### 主从关系

##### HDFS 集群

- 主机

`hadoop102`

- 从机

`hadoop103`、`hadoop104`、`hadoop105`、`hadoop106`

##### YARN 集群

- 主机

`hadoop107`

- 从机

`hadoop104`、`hadoop105`、`hadoop106`

### 学习阶段规则

|hadoop102|hadoop103|hadoop104|
|---|---|---|
|NameNode|ResourceManager|SecondaryNameNode|
|DataNode & NameManager|DataNode & NameManager|DataNode & NameManager|

#### 主从关系

##### HDFS 集群

- 主机

`hadoop102`

- 从机

`hadoop102`、`hadoop103`、`hadoop104`

##### YARN 集群

- 主机

`hadoop103`

- 从机

`hadoop102`、`hadooop103`、`hadoop104`

## 集群配置

### env

- 配置`hadoop-env.sh`、`mapred-env.sh`、`yarn-env.sh`的`JAVA_HOME`

### site

> `<<ip_address>>`：计算机在网络中的ip地址或网络名称

#### core-site.xml

- 指定HDFS中NameNode的地址

``` xml
<property>
    <name>fs.defaultFS</name>
    <value>hdfs://<<ip_address>>:9000</value>
</property>
```

**注意：使用`fs.default.name`还是使用`fs.defaultFS`，要首先判断是否开启了`NameNode`的`HighAvaliable`，如果开启了`NameNode`的`HighAvaliable`，那么就用`fs.defaultFS`，在单一`NameNode`的情况下，就用`fs.default.name`。**

- 指定Hadoop运行时产生文件的存储目录

``` xml
<property>
    <name>hadoop.tmp.dir</name>
    <value>/Users/hatsunemiku/.hadoop/data/tmp</value>
</property>
```

#### hdfs-site.xml

- 指定HDFS副本的数量

``` xml
<property>
    <name>dfs.replication</name>
    <value>3</value>
</property>
```

- 指定Hadoop辅助名称节点主机配置

``` xml
<property>
    <name>dfs.namenode.secondary.http-address</name>
    <value><<ip_address>>:50090</value>
</property>
```

#### mapred-site.xml

- 指定MR运行在YARN上

``` xml
<property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
</property>
```

#### yarn-site.xml

- Reducer获取数据的方式

``` xml
<property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
</property>
```

- 指定YARN的ResourceManager地址

``` xml
<property>
    <name>yarn.resourcemanager.hostname</name>
    <value><<ip_address>></value>
</property>
```

## 集群启动

### 格式化

- 首次启动格式化，在配置了`NameNode`的计算机（`hadoop102`）上格式化

``` sh
hdfs namenode -format
```

### 启动

- 在`hadoop102`上启动`NameNode`、`DataNode`

``` sh
hadoop-daemon.sh start namenode
hadoop-daemon.sh start datanode
```

- 在`hadoop103`上启动`DataNode`

``` sh
hadoop-daemon.sh start datanode
```

- 在`hadoop104`上启动`DataNode`、`SecondaryNameNode`

``` sh
hadoop-daemon.sh start datanode
hadoop-daemon.sh start secondarynamenode
```

### 确认

#### 在各个计算机上查看程序运行情况

``` sh
jps
```

#### 在浏览器上查看计算机运行情况

- 进入网页`hadoop102:50070`

如果在`Datanodes`页面找到其他设备，则配置成功

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)
[CSDN——lepton126](https://blog.csdn.net/lepton126/article/details/88327205)

