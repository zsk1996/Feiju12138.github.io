---
title: 【笔记】MongoDB学习笔记
categories:
  - Database
date: 2020-07-05 12:43:55
---

## 前言

MongoDB是一种面向文档的数据库管理系统，用C++等语言撰写而成，以解决应用程序开发社区中的大量现实问题。MongoDB由MongoDB Inc.（当时是10gen团队）于2007年10月开发，2009年2月首度推出，现以服务器端公共许可（SSPL）分发。（[维基百科](https://zh.wikipedia.org/wiki/MongoDB)）

<!-- more -->

## 安装

- MongoDB 已经宣布不再开源，从2019年9月2日开始 ，HomeBrew 也从核心仓库 (#43770) 当中移除了mongodb 模块
- 不过想要继续使用`brew install mongodb`也是可以的，MongoDB 官方提供了一个单独的 HomeBrew 的社区版本安装：[https://github.com/mongodb/homebrew-brew](https://github.com/mongodb/homebrew-brew) 。

### 添加仓库

``` sh
brew tap mongodb/brew
```

### 安装社区版

- 也可以参考文档安装指定的版本

``` sh
brew install mongodb-community
```

### 部分配置文件路径

> `configuration file`: /usr/local/etc/mongod.conf
> `log directory path`: /usr/local/var/log/mongodb
> `data directory path`: /usr/local/var/mongodb

## 服务

### 启动服务

``` sh
brew services start mongodb-community
```

### 关闭服务

``` sh
brew services stop mongodb-community
```

### 重启服务

``` sh
brew services restart mongodb-community
```

## 启动MongoDB

``` sh
mongo
```

## MongoDB和其他数据库的区别

- 数据库用`database`表示
- 集合（也就是其他数据库的数据表`table`）用`collection`表示
- 字段（也就是其他数据库的字段`colum`）用`field`表示

## 基本命令

- MongoDB的命令区分大小写
- MongoDB的命令末尾不需要分号

### 创建数据库

> `<database_name>`：数据库名

``` sql
use <database_name>
```

### 删除数据库

- 删除当前use的数据库

``` sql
db.dropDatabase()
```

### 查看所有数据库

``` sql
show dbs
```

### 创建集合并插入数据

> `<collection_name>`：集合名
> `<key>`：键
> `<value>`：值

``` sql
db.<collection_name>.insert({"<key>":"<value>"})
db.<collection_name>.insert({"<key_1>":"<value_1>", "<key_2>":"<value_2>"})
```

#### 以变量的形式插入数据

> `<name>`：变量名

``` sql
<name>=({"<key>":"<value>"})
db.<collection_name>.insert(<name>)
```

### 删除集合

``` sql
db.<collection_name>.drop()
```

### 查看所有集合

``` sql
show tables
```

### 查看集合内的所有数据

``` sql
db.<collection_name>.find()
```

#### 以json的格式展示

``` sql
db.<collection_name>.find().pretty()
```

#### 按条件查看数据

``` sql
db.<collection_name>.find({"<key>":"<value>"})
```

#### 多条条件查看数据

- 相当于其他数据库的`AND`关键字

``` sql
db.<collection_name>.find({"<key>":"<value>", "<key>":"<value>"})
```

- 相当于其他数据库的`OR`关键字

``` sql
db.<collection_name>.find({$or:[{"<key>":"<value>"},{"<key>":"<value>"}]})
```

#### 比较运算

> `<num>`：数值

##### 大于

``` sql
db.<collection_name>.find({"<key>":{$gt:<num>}})
```

##### 大于等于

``` sql
db.<collection_name>.find({"<key>":{$gte:<num>}})
```

##### 小于

``` sql
db.<collection_name>.find({"<key>":{$lt:<num>}})
```

##### 小于等于

``` sql
db.<collection_name>.find({"<key>":{$lte:<num>}})
```

##### 等于

``` sql
db.<collection_name>.find({"<key>":{$eq:<num>}})
db.<collection_name>.find({"<key>":{$lt:<num>,$gte:<num>}})
db.<collection_name>.find({"<key>":{$gt:<num>,$lte:<num>}})
```

##### 不等于

``` sql
db.<collection_name>.find({"<key>":{$ne:<num>}})
```

#### 读取指定位置的数据

> `<num>`：指定第几条数据

``` sql
db.<collection_name>.find().limit(<num>)
```

##### 跳过指定条数据后再读区指定位置的数据

``` sql
db.<collection_name>.find().limit(<num>).skip(<num>)
```

#### 指定显隐条件查看数据

- 值为`1`则为显示，值为`0`则为不显示

``` sql
db.<collection_name>.find({},{"<key_1>":1,"<key_2>":0})
```

#### 排序后查看

- 按照指定key排序，值为`1`为升序，值为`-1`为降序

``` sql
db.<collection_name>.find().sort({"<key>":1})
db.<collection_name>.find().sort({"<key>":-1})
```

### 修改数据

> `<key_old>`：原键
> `<value_old>`：原值
> `<key_new>`：新键
> `<value_new>`：新值

``` sql
db.<collection>.update({"<key_old>":"<value_old>"},{$set:{"<key_new>":"<value_new>"}})
```

#### 修改多条

- 当数据库存在多条相同数据，默认只会修改第一条，如果修改所有，可以在末尾添上`,{multi:true}`

``` sql
db.<collection>.update({"<key_old>":"<value_old>"},{$set:{"<key_new>":"<value_new>"}},{multi:true})
```

### 删除数据

``` sql
db.<collection_name>.remove({"<key>":"<value>"})
```

#### 清空数据

``` sql
db.<collection_name>.remove({})
```

## 参考文献

程序媛
[掘金——古拉里](https://juejin.im/post/5d9d7ad66fb9a04e373163c3)
[掘金——六个周](https://juejin.im/post/5e4cbcd66fb9a07c7c2d5a1c)

