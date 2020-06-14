---
title: 【笔记】Linux 基础命令（RetHat篇）
date: 2019-11-11 22:30:29
tags:
categories:
- Linux
---

## 前言

Linux 操作系统最基本命令，其他高级命令将陆续更新在其他笔记中。（自定义参数均设为"xxx"）

<!-- more -->

## 笔记

### 显示日期

``` bash
$ date
```

### 输出语句

``` bash
$ echo
```

### 静态查看进程

``` bash
$ ps aux
```

### 动态查看进程

``` bash
$ top
```

### 查看进程编号

``` bash
$ pidof xxx
```

### 结束进程

``` bash
$ kill xxx
```

### 结束所有进程

``` bash
$ killall xx
```

### 查询版本信息

``` bash
$ uname -a
```

### top 命令第一行

``` bash
$ uptime
```

### 查看系统内存信息

``` bash
$ free
```

#### 自动单位

``` bash
$ free -h
```

#### 以MB为单位

``` bash
$ free -m
```

#### 以GB为单位

```
$ free -g
```

### 查看当前用户的登录信息

``` bash
$ who
```

### 查看当前系统的登录记录

``` bash
$ last
```

### 命令行历史记录

``` bash
$ history

```

#### 清空命令行历史

``` bash
$ history -c
```

#### 重复历史记录中的命令

``` bash
$ !xxx
```

### 收集重要的相关信息（排错） 

``` bash
$ sosreport
```

### 查看当前目录

``` bash
$ pwd
```

### 切换目录

``` bash
$ cd /xxx
```

#### 切换到主目录

``` bash
$ cd ~
```

#### 返回上一次目录

``` bash
$ cd -
```

#### 返回上一级目录

``` bash
$ cd ..
```

### 查看当前目录所有文件

``` bash
$ ls
```

#### 显示详细信息

``` bash
$ ls -l
```

#### 显示隐藏文件

``` bash
$ ls -a
```

### 查看文件内容

``` bash
$ cat xxx
```

### 查看长文件内容

``` bash
$ more xxx
```

- 备注

回车换行，空格翻页

#### 查看文件前十行内容

``` bash
$ head -n 10 xxx
```

#### 查看文件后十行内容

``` bash
$ tail -n 10 xxx
```

#### 查看实时更新的文件内容

``` bash
$ tail -f xxx
```

#### 显示文件行数 

``` bash
$ wc -l xxx
```

#### 显示文件字节数

``` bash
$ wc -c xxx
```

#### 显示文件单词数量

``` bash
$ wc -w xxx
```

### 查看文件的时间

``` bash
$ stat xxx
```

### 按列提取文件内容

``` bash
$ cut -d : -f 1 xxx
```

- 备注

以冒号为间隔提取1列的信息

### 判断两个文件是否相同

``` bash
$ diff --brief xxx1 xxx2
```

#### 判断两个文件具体哪处不同

``` bash
$ diff -c xxx1 xxx2
```

### 新建一个文本文件

``` bash
$ touch xxx
```

#### 修改文件的最后修改时间

``` bash
$ touch -d "13:14" xxx
```

- 备注

将时间修改为"13:14"

### 新建一个文件目录

``` bash
$ mkdir xxx
```

#### 新建一个有层次关系的目录

``` bash
$ mkdir -p xxx1/xxx2/xxx3
```

### 复制文件

``` bash
$ cp /SomeWhere1/xxx /SomeWhere2/xxx
```

#### 复制目录

``` bash
$ cp -r xxx1/ xxx2/
```

### 剪切文件

``` bash
$ mv /SomeWhere1/xxx /SomeWhere2/xxx2
```

#### 重命名文件

``` bash
$ mv xxx1 xxx2
```

### 删除文件

``` bash
$ rm xxx
```

#### 强制删除文件

``` bash
$ rm -f xxx
```

#### 删除目录

``` bash
$ rm -r xxx/
```

### 显示文件的类型

``` bash
$ file xxx
```

### 查看命令的位置

``` bash
$ whereis xxx
```

### 查看主机名

``` sh
$ hostname
```

#### 修改主机名

- 在终端临时修改

> `<name>`：修改后的主机名

``` sh
$ hostname <name>
```

## 参考文献

[Linux就该这么学——刘遄](https://www.linuxprobe.com)
