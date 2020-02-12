---
title: 【笔记】Hadoop 配置日志的聚集
categories:
  - 大数据
date: 2020-02-04 16:17:05
---

## 前言

`Hadoop`配置日志的聚集

<!-- more -->

## 配置 mapred-site.xml

- 配置历史服务器

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/mapred-site.xml
```

### 添加内容

> `<<ip_address>>`：作为历史服务器的计算机在网络中的ip地址或网络名称

``` xml
<!-- 历史服务器端地址 -->
<property>
    <name>mapreduce.jobhistory.address</name>
    <value><<ip_address>>:10020</value>
</property>

<!-- 历史服务器端地址 -->
<property>
    <name>mapreduce.jobhistory.webapp.address</name>
    <value><<ip_address>>:19888</value>
</property>
```

## 配置 yarn-site.xml

- 配置日志的聚集

### 编辑配置文件

``` sh
vim /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/yarn-site.xml
```

### 添加内容

``` xml
<!-- 日志聚集功能使能 -->
<property>
    <name>yarn.log-aggregation-enable</name>
    <value>true</value>
</property>

<!-- 日志保留时间设置7天 -->
<property>
    <name>yarn.log-aggregation.retain-seconds</name>
    <value>604800</value>
</property>
```

## 启动

### 重新启动集群

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/start-dfs.sh
/usr/local/Cellar/hadoop/3.2.1/sbin/start-yarn.sh
```

### 启动历史服务器

- 在配置完日志聚集的计算机启动历史服务器

``` sh
/usr/local/Cellar/hadoop/3.2.1/sbin/mr-jobhistory-daemon.sh start historyserver
```

## 确认

### 查看所有计算机上程序运行情况

``` sh
ssh hadoop102 "jps"
ssh hadoop103 "jps"
ssh hadoop104 "jps"
```

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)

