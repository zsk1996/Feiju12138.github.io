---
title: 【笔记】Maven配置JDK版本
categories:
  - Java
date: 2020-08-17 14:45:13
---

## 前言

把Maven所需要的JDK版本配置为固定1.8

<!-- more -->

## 配置代理

- 编辑`Maven`配置文件

``` sh
vim /usr/local/Cellar/maven/3.6.3_1/libexec/conf/settings.xml
```

- 修改`<profiles></profiles>`中的配置

``` xml
<profiles>
    <profile>
      <id>development</id>
      <activation>
        <jdk>1.8</jdk>
        <activeByDefault>true</activeByDefault>
      </activation>
      <properties>
      	<maven.compiler.source>1.8</maven.compiler.source>
      	<maven.compiler.target>1.8</maven.compiler.target>
    		<maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
      </properties>
    </profile>
</profiles>
```

## 完成

