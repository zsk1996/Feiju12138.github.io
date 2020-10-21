---
title: 【进阶】Hadoop 伪分布式模式
categories:
  - Big Data
date: 2020-02-01 12:09:48
---

## 前言

启动`YARN`并运行`MapReduce`程序

<!-- more -->

## 准备工作

- 启动`NameNode`和`DataNode`

## 配置 yarn-env.sh

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/yarn-env.sh
```

### 修改内容

- 取消`export JAVA_HOME=`注释，并添加`JAVA_HOME`位置

## 配置 yarn-site.xml

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/yarn-site.xml
```

### 添加内容

- 在`<configuration></configuration>`标签内添加配置

``` xml
<!-- 获取数据的方式 -->
<property>
    <name>yarn.nodemanager.aux-services</name>
    <value>mapreduce_shuffle</value>
</property>

<!-- 指定YARN的ResourceManager地址 -->
<property>
    <name>yarn.resourcemanager.hostname</name>
    <value>localhost</value>
</property>
```

## 配置 mapred-env.sh

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/mapred-env.sh
```

### 修改内容

- 取消`export JAVA_HOME=`注释，并添加`JAVA_HOME`位置

## 配置 mapred-site.xml

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/mapred-site.xml
```

### 添加内容

- 在`<configuration></configuration>`标签内添加配置

``` xml
<!-- 指定MR运行在YARN上 -->
<property>
    <name>mapreduce.framework.name</name>
    <value>yarn</value>
</property>
```

## 启动 ResourceManager（可选）

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/hadoop-daemon.sh start resourcemanager
```

## 启动 NodeManager（可选）

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/hadoop-daemon.sh start nodemanager
```

## 直接启动 yarn

``` sh
cd /usr/local/Cellar/hadoop/3.2.1/libexec/sbin/
./start-yarn.sh
```

## 完成

- 查看正在运行的`java`程序

``` sh
jps
```

- 进入网页`localhost:8088`

![01.png](/images/20200201120948/01.png)

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)
[简书——张照博](https://www.jianshu.com/p/a86ccd96b78a)
