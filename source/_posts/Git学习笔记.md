---
title: 【笔记】Git学习笔记
categories:
  - null
date: 2020-10-03 11:17:49
---

## 前言

git是一个分布式版本控制软件，最初由林纳斯·托瓦兹创作，于2005年以GPL发布。最初目的是为更好地管理Linux内核开发而设计。应注意的是，这与GNU Interactive Tools（一个类似Norton Commander界面的文件管理器）不同。（[维基百科](https://zh.wikipedia.org/wiki/Git)）

## 安装Git

``` sh
brew install git
```

## 基本命令

### 初始化当前目录

- 初始化成功会在当前目录下自动创建一个存放git配置信息的名为`.git`的隐藏目录

``` sh
git init
```

### 查看状态

- 查看当前目录下的git状态，可以通过状态指引完成提交

``` sh
git status
```

### 新增

- 将指定文件从工作空间添加到本地索引

> `<name>`：文件名

``` sh
git add <name>
```

#### 新增所有

- 将当前目录及其子目录下的所有文件从工作空间添加到本地索引

``` sh
git add .
```

### 提交

- 将本地索引的所有文件提交到本地仓库

``` sh
git commit
```

- 通过vim键入提交的备注

- `:wq`保存并退出完成备注

#### 快速提交

> `<text>`：需要提交的备注内容

``` sh
git commit -
```


