---
title: 【笔记】Pyenv 学习笔记
categories:
  - Python
date: 2020-02-06 20:34:17
---

## 前言

pyenv lets you easily switch between multiple versions of Python. It's simple, unobtrusive, and follows the UNIX tradition of single-purpose tools that do one thing well.（[官网](https://github.com/pyenv/pyenv)）

`MacOS`下管理多个版本`python`

<!-- more -->

## 删除使用pkg包安装的 python

### 删除 Python 框架

``` sh
sudo rm -rf /Library/Frameworks/Python.framework
```

### 删除 Python 程序

``` sh
sudo rm -rf /Applications/Python*
```

## 安装 pyenv

``` sh
brew install pyenv
```

## 基本命令

### 查看当前使用的版本

``` sh
pyenv version
```

### 查看所有已安装的版本

- 首次查看通常只有`system`版本

``` sh
pyenv versions
```

### 查看所有可安装的版本

``` sh
pyenv install --list
```

### 安装或卸载对应版本

> `<version>`：版本号

``` sh
pyenv install -v <version>
pyenv uninstall -v <version>
```

### 更新数据库

``` sh
pyenv rehash
```

### 设置首选版本

#### 全局设置

- 通过将版本号写入`~/.pyenv/version`文件的方式设置`python`的全局版本

``` sh
pyenv global <version>
```

#### 本地设置

- 写入当前目录下的`.python-version`文件的方式设置`python`的本地版本
- 通过这种方式设置的`python`版本优先级比`global`高

``` sh
pyenv local <version>
```

#### shell 设置

- 通过设置当前`shell`的`PYENV_VERSION`环境变量的方式
- 这个版本的优先级比`local`和`global`都要高

``` sh
pyenv shell <version>
```

## 参考文献

[CSDN——水之光love](https://blog.csdn.net/coding_dong/article/details/80343756)

