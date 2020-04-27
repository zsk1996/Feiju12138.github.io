---
title: 【踩坑】取消vim鼠标进入可视模式
categories:
  - MacOS
date: 2020-02-26 01:16:31
---

## 前言

在高版本vim下，使用鼠标选区会自动进入可视模式，对于习惯用鼠标选区复制粘贴的小伙伴极其不方便

<!-- more -->

## 解决问题

### 将vim默认配置文件拷贝到Home目录下

``` sh
cp /usr/share/vim/vim81/defaults.vim ~/.vimrc
```

### 编辑 .vimrc 配置文件

``` sh
vim ~/.vimrc
```

### 修改 .vimrc 配置文件

- 为78、79、80行添加注释

``` sh
" if has('mouse')
"   set mouse=a
" endif
```

## 完成

## 参考文献

[CSDN——天印湖的倒影](https://blog.csdn.net/weixin_42099269/article/details/80331126)

