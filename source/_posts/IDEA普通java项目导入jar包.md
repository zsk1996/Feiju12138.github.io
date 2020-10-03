---
title: 【笔记】IDEA普通java项目导入jar包
categories:
  - Java
date: 2020-10-02 13:40:07
---

## 前言

IDEA普通java项目导入jar包

<!-- more -->

## 导入jar包

- 在项目根目录下新建名为`lib`的目录，并将需要导入的jar包复制到lib目录下

![01.png](/images/20201002134007/01.png)

- `File`->`Project Structure`->`Modules`->选中项目->`Dependencies`->`+`->`JARs or directories`

![02.png](/images/20201002134007/02.png)

- 选中项目根目录中刚刚创建的lib目录

![03.png](/images/20201002134007/03.png)

- `OK`

- 此时jar包已经可以展开了，表示引入成功

![04.png](/images/20201002134007/04.png)

## 完成

