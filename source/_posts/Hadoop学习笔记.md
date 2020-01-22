---
title: 【笔记】Hadoop学习笔记
categories:
  - 大数据
date: 2020-01-16 09:18:58
---

## 前言

Apache Hadoop是一款支持数据密集型分布式应用程序并以Apache 2.0许可协议发布的开源软件框架。它支持在商品硬件构建的大型集群上运行的应用程序。Hadoop是根据谷歌公司发表的MapReduce和Google文件系统的论文自行实现而成。（[维基百科](https://zh.wikipedia.org/wiki/Apache_Hadoop)）

<!-- more -->

## 基本命令

### 新建

#### 新建目录

> `<directory_old>`：想要新建目录的位置
> `<directory_new>`：新目录名

``` sh
hadoop fs -mkdir <directory_old>/<directory_new>
```

#### 新建一个空文件

``` sh
hadoop fs -touchz <file>
```

### 查看

#### 查看目录文件

> `<directory>`：目录名
> `-r`：递归操作

``` sh
hadoop fs -ls <directory>
hadoop fs -lsr <directory>
```

#### 查看文件详细信息

> `-files`：查看文件的原数据信息
> `-blocks`：查看文件被切成的块数
> `-locations`：查看文件每一块存放的位置

``` sh
hadoop fsck <file> -files -blocks -locations
```

#### 查看文件大小

``` sh
hadoop fs -du <file>
```

##### 查看目录下所有文件大小

``` sh
hadoop fs -du <directory>
```

#### 查看文件内容

> `-cat`：查看文件所有内容
> `-tail`：查看文件末尾十行内容

``` sh
hadoop fs -cat <file>
hadoop fs -tail <file>
```

### 上传和下载

#### 上传文件

> `<file_from_linux>`：想要从`linux`上传文件的位置及名称
> `<directory>`：想要保存在`hadoop`的目录

``` sh
hadoop fs -put <file_from_linux> <directory>
hadoop fs -copyFromLocal <file_from_linux> <directory>
```

#### 下载文件

> `<file_from_hadoop>`：想要从`hadoop`下载文件的位置及名称

``` sh
hadoop fs -get <file_from_hadoop> <directory>
hadoop fs -copyToLocal <file_from_hadoop> <directory>
```

##### 合并文件下载

- 将目录下所有文件合并成一个文件，并下载到linux本地

``` sh
hadoop fs -getmerge <directory> <file_from_linux>
```

### 删除

#### 删除文件

> `<file>`：想要操作的文件位置及名称

``` sh
hadoop fs -rm <file>
```

#### 删除目录

> `<directory>`：想要操作的目录位置及名称

``` sh
hadoop fs -rmdir <directory>
hadoop fs -rmr <directory>
```

### 移动

``` sh
hadoop fs -mv <file_old> <file_new>
hadoop fs -mv <directory_old> <directory_new>
```

### 复制

``` sh
hadoop fs -cp <file> <directory>
hadoop fs -cp <file> <directory_1> <directory_2>
```



