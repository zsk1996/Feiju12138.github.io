---
title: 【笔记】Redis学习笔记
categories:
  - Database
date: 2020-08-30 17:28:20
---

## 前言

Redis学习笔记

<!-- more -->

## 数据类型及相关命令

- Redis存储的是key-value格式的数据，其中key是字符串，value有五种不同的数据类型

### 字符串类型String

> `<key>`：键
> `<value>`：值

#### 存储

```
set <key> <value>
```

#### 获取

```
get <key>
```

#### 删除

```
del <key>
```

### 哈希类型hash

- map格式
- 可以存储键值对

> `<field>`：值中存储的键值对的键
> `<value>`：值中存储的键值对的值

#### 存储

```
hset <key> <field> <value>
```

#### 获取

##### 获取指定酒店键值对

```
hget <key> <field>
```

##### 获取所有的键值对

```
hgetall <key>
```

#### 删除

```
hdel <key> <field>
```

### 列表类型list

- linkedlist格式
- 可以存储列表
- 允许重复元素
- 有序

#### 存储

##### 从列表头存储

```
lpush <key> <value>
```

##### 从列表尾存储

```
rpush <key> <value>
```

#### 获取

> `<start>`：指定获取的列表范围的起始值
> `<end>`：指定获取的列表范围的截止值

```
lrange <key> <start> <end>
```

##### 获取所有

```
lrange <key> 0 -1
```

#### 删除

##### 从列表头删除

- 返回删除的元素

```
lpop <key>
```

##### 从列表尾删除

- 返回删除的元素

```
rpop <key>
```

### 集合类型set

- 可以存储列表
- 不允许重复元素
- 无序

#### 存储

```
sadd <key> <value>
```

#### 获取

- 获取set集合中所有元素

```
smembers <key>
```

#### 删除

- 删除set集合中指定key的元素

```
srem <key> <value>
```

### 有序集合类型sortedset

- 可以存储列表
- 不允许重复元素
- 有序

> `<score>`：分数，将来会根据给定的分数排序

#### 存储

```
zadd <key> <score> <value>
```

#### 获取

```
zrange <key> <start> <end>
```

##### 同时获取分数

```
zrange <key> <start> <end> withscore
```

#### 删除

```
zrem key value
```

## 通用命令

### 查看所有的键

```
keys *
```

### 查看指定键的数据类型

```
type <key>
```

### 删除指定的键值对

```
del <key>
```

## 持久化

- Redis是一个内存数据库，当Redis服务器重启，或电脑重启，数据会丢失，我们可以将Redis内存中的数据持久化保存到硬盘的文件中

### 持久化机制

#### RDB

- 默认方式，不需要配置
- 在一定的间隔时间，检测key的变化情况，然后持久化数据

- 修改`redis.conf`配置文件第217、218、219行

```
# 900秒后，至少有1个key发生改变，就持久化一次
save 900 1

# 300秒后，至少有10个key发生改变，就持久化一次
save 300 10

# 60秒后，至少有1万个key发生改变，就持久化一次
save 60 10000
```

#### AOF

- 日志的记录方式
- 可以记录每一条命令的操作，可以每一次命令操作后，持久化数据

- 修改`redis.conf`配置文件第698行，`no`改为`yes`

```
appendonly yes
```

- 修改`redis.conf`配置文件第727、728、729行

```
# 每一次操作都进行一次持久化
# appendfsync always

# 每隔一秒进行一次持久化
appendfsync everysec

# 不进行持久化
# appendfsync no
```

## 完成

## 参考文献

[哔哩哔哩——黎曼的猜想](https://www.bilibili.com/video/BV1uJ411k7wy)

