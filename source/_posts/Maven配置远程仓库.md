---
title: 【笔记】Maven配置远程仓库
categories:
  - Java
date: 2020-08-17 14:41:33
---

## 前言

将Maven配置远程仓库为阿里云仓库

<!-- more -->

## 配置代理

- 编辑`Maven`配置文件

``` sh
vim /usr/local/Cellar/maven/3.6.3_1/libexec/conf/settings.xml
```

- 修改`<mirrors></mirrors>`中的配置

``` xml
<mirrors>
    <mirror>
      <id>nexus-aliyun</id>
      <name>Nexus aliyun</name>
      <mirrorOf>central</mirrorOf>
      <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
    </mirror>
</mirrors>
```

## 完成
