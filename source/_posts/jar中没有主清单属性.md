---
title: 【踩坑】jar中没有主清单属性
categories:
  - Java
date: 2020-10-01 21:17:51
---

## 前言

将打好的jar包通过命令行运行，报错：`...jar中没有主清单属性`

<!-- more -->

## 原因

- 工具打包的时候没有指定程序入口

## 解决问题

### 补齐Maven配置文件

- SpringBoot项目可以在修复pom.xml文件后使用install工具重新打包

- 在pom.xml文件添加构建的标签

``` xml
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

### 手动修复

- 非SpringBoot项目可以手动修复

- 通过压缩工具打开.jar文件

- 在`/META-INF/MANIFEST.MF`文件内添加一行，用于指定程序入口

> `<main>`：包含主方法的类的全局限定名

``` sh
Main-Class: <main>
```

## 完成

## 参考文献

[CSDN——xqnode](https://blog.csdn.net/xqnode/article/details/86628794)

