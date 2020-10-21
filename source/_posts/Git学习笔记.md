---
title: 【笔记】Git学习笔记
categories:
  - null
date: 2020-10-03 11:17:49
---

## 前言

git是一个分布式版本控制软件，最初由林纳斯·托瓦兹创作，于2005年以GPL发布。最初目的是为更好地管理Linux内核开发而设计。应注意的是，这与GNU Interactive Tools（一个类似Norton Commander界面的文件管理器）不同。（[维基百科](https://zh.wikipedia.org/wiki/Git)）

<!-- more -->

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

- 不需要打开vim而快速提交

> `<text>`：需要提交的备注内容

``` sh
git commit -m "<text>"
```

#### 直接提交

- 将当前目录及其子目录下的所有文件从工作空间添加到本地索引，并直接进行提交

``` sh
git commit -a
```

#### 直接快速提交

- 将当前目录及其子目录下的所有文件从工作空间添加到本地索引，不需要打开vim，并直接进行快速提交

``` sh
git commit -a -m "<text>"
```

### 推送

- 预先在远程创建仓库，并将本地仓库的所有文件推送到远程仓库（公共仓库或自己搭建的私有仓库）

``` sh
git push
```

#### 首次推送

- 指定当前git目录对应的远程仓库地址

> `<url>`：远程仓库地址

``` sh
git remote add origin <url>
```

- 首次推送要指定主分支

> `master`：主分支名，可以自定义

``` sh
git push --set-upstream origin master
```

### 克隆

- 首次将所有文件从远程仓库直接克隆到本地仓库（当前目录下）

> `<git>`：远程仓库地址

``` sh
git clone <git>
```

### 拉取

- 在已经克隆的情况下，从远程仓库拉取新文件到本地仓库

``` sh
git pull
```

### 切换分支

> `<name>`：分支名

``` sh
git branch -M <name>
```

## git配置

### 查看所有配置

``` sh
git config --list
```

### 配置当前使用者的用户名

> `<username>`：用户名

``` sh
git config --global user.name "<username>"
```

### 配置当前使用者的邮箱

> `<email>`：邮箱

``` sh
git config --clobal user.email "<email>"
```

### 重置用户名密码信息

``` sh
git config --system --unset credential.helper
```

## 完成

