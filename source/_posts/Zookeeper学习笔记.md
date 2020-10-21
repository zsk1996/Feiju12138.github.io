---
title: 【笔记】Zookeeper 学习笔记
categories:
  - Big Data
date: 2019-12-29 09:31:46
---

## 前言

Apache ZooKeeper是Apache软件基金会的一个软件项目，它为大型分布式计算提供开源的分布式配置服务、同步服务和命名注册。 ZooKeeper曾经是Hadoop的一个子项目，但现在是一个独立的顶级项目。 ZooKeeper的架构通过冗余服务实现高可用性。（[维基百科](https://zh.wikipedia.org/wiki/Apache_ZooKeeper)）

<!-- more -->

## Zookeeper 应用场景

- 集群管理，管理集群中节点状态是宕机还是正常工作
- 做集群统一的配置管理
- 统一的命名服务，命名服务的要求是名字标识具有唯一性
- 可以做集群中主备节点的管理和切换
- 消息的订阅和发布
- 分布式锁

## 基本命令

### 安装

``` sh
brew install zookeeper
```

### 服务端的操作

#### 启动服务端（单机模式）

``` sh
zkServer start
```

#### 关闭服务端

``` sh
zkServer stop
```

#### 重启服务器

``` sh
zkServer restart
```

#### 查看状态

``` sh
zkServer status
```

### 客户端的操作

#### 启动客户端

``` sh
zkCli
```

#### 关闭客户端

``` sh
quit
```

#### 创建节点

> `<name>`：节点名
> `""`：空数据
> `<data>`：数据

> `-e`：创建临时节点
> `-s`：创建顺序节点
> `-e -s`：创建临时顺序节点

``` sh
create /<name> ""
create /<name> <data>
create -e /<name> <data>
create -s /<name> <data>
create -e -s /<name> <data>
```

#### 查看数据

``` sh
get /<name>
```

#### 修改数据

``` sh
set /<name> <data>
```

#### 删除节点

``` sh
delete /<name>
rmr /<name>
```

## 未完待更

## 参考文献

[达内教育](http://www.tmooc.cn)
[简书——iengchen](https://www.jianshu.com/p/b889b86536be)

