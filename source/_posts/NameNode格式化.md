---
title: 【踩坑】NameNode 格式化
categories:
  - 大数据
date: 2020-02-01 12:00:04
---

## 前言

在首次配置完`Hadoop`，需要格式化`NameNode`节点，但是只能首次使用之前格式化

<!-- more -->

## 原因

- 格式化`NameNode`节点，会产生新的集群id，会导致`NameNode`、`DataNode`集群id不一致，导致无法正常启动`DataNode`

## 解决问题

- 如果第二次格式化导致无法正常启动`DataNode`

- 删除`DataNode`数据再启动

``` sh
rm -r /Users/hatsunemiku/.hadoop/data/tmp/dfs/data
```

## 完成

## 参考文献

[哔哩哔哩——zhvsvd](https://www.bilibili.com/video/av64039568)

