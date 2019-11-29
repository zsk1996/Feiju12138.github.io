---
title: 【笔记】HomeBrew
date: 2019-11-26 19:58:17
tags:
---

## 前言

Homebrew是一款自由及开放源代码的软件包管理系统，用以简化macOS系统上的软件安装过程，最初由马克斯·霍威尔写成。（[维基百科](https://zh.wikipedia.org/wiki/Homebrew)）

<!-- more -->

## 安装 Xcode 命令行工具

``` bash
xcode-select --install
```

## 安装 HomeBrew

- 进入[brew官网](brew.sh)查看最新更新代码

``` bash
open -a "/Applications/Safari.app" https://brew.sh
```

- 将最新的安装代码复制到终端

``` bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

- 是否确认，按回车

- 等待安装成功

## brew 基本命令

### 更新 brew 自身

``` bash
brew update
```

### 更新 brew 本地仓库的所有软件包

``` bash
brew upgrade
```

### 查找软件包

``` bash
brew search [软件包]
```

### 查询可更新的软件包

``` bash
brew outdated
```

### 安装软件包

``` bash
brew install [软件包]
```

### 卸载软件包

``` bash
brew uninstall [软件包]
```

### 重装软件包

``` bash
brew reinstall [软件包]
```

### 清理软件包

> 用于清理中断下载的软件包残留
> 用于清理软件包旧版本

``` bash
brew cleanup
```

### 查看已安装软件包

``` bash
brew list
```

### 查看包信息

``` bash
brew info [软件包]
```

## 卸载 HomeBrew

``` bash
cd `brew --prefix`
rm -rf Cellar
brew prune
rm `git ls-files`
rm -r Library/Homebrew Library/Aliases Library/Formula Library/Contributions
rm -rf .git
rm -rf ~/Library/Caches/Homebrew
```

## 参考文献

[掘金——WenBo丨星空灬](https://juejin.im/post/5a561685f265da3e2b164fe7)
