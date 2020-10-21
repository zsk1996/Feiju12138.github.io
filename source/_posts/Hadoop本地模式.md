---
title: 【笔记】Hadoop 本地模式
categories:
  - Big Data
date: 2020-01-31 23:15:11
---

## 前言

`Hadoop`本地模式运行两个`demo`

<!-- more -->

## 官方 Grep 案例

### 新建输入目录

``` sh
mkdir input
```

### 拷贝数据文件

``` sh
cp /usr/local/Cellar/hadoop/3.2.1/libexec/etc/hadoop/*.xml input
```

### 启动 demo

> `grep`：主类名
> `input`：输入目录
> `output`：输出目录（必须不存在）

``` sh
/usr/local/Cellar/hadoop/3.2.1/libexec/bin/hadoop jar /usr/local/Cellar/hadoop/3.2.1/libexec/share/hadoop/mapreduce/hadoop-mapreduce-examples-3.2.1.jar grep input output 'dfs[a-z.]+'
```

### 查看结果

``` sh
cat output/*
```

## 官方 WordCount 案例

### 创建输入目录

``` sh
mkdir wcinput
```

### 创建数据文件

#### 新建 wc.input 文件

``` sh
touch wcinput/wc.input
```

#### 编辑 wc.input 文件

- 编辑文件

``` sh
vim wcinput/wc.input
```

- 输入文字

``` sh
hadoop yarn
hadoop mapreduce
atguigu
atguigu
```

### 启动 demo

``` sh
/usr/local/Cellar/hadoop/3.2.1/libexec/bin/hadoop jar /usr/local/Cellar/hadoop/3.2.1/libexec/share/hadoop/mapreduce/hadoop-mapreduce-examples-3.2.1.jar wordcount wcinput wcoutput
```

### 查看结果

``` sh
cat wcoutput/*
```

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)

