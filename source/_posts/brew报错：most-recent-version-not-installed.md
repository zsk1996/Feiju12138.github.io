---
title: 【踩坑】brew 报错：most recent version not installed
categories:
  - null
date: 2020-04-25 10:46:01

---

## 前言

在执行`brew cleanup`命令时，报错：`most recent version not installed`

<!-- more -->

![01.png](/images/20200425104601/01.png)

## 原因

- `httping`出现了问题

## 解决问题

``` sh
brew uninstall -f httping
brew cleanup
brew install httping
brew info httping
```

## 完成

## 参考文献

[StackExchange——Simba](https://apple.stackexchange.com/questions/371175/brew-cleanup-warning-skipping-xxx-most-recent-version-x-not-installed)

