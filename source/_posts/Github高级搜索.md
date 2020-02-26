---
title: 【笔记】Github高级搜索
categories:
  - null
date: 2020-02-21 21:45:50
---

## 前言

Github高级搜索方法

<!-- more -->

## 搜索限制

> `<text>`：搜索关键字

### 标题搜索

```
in:name <text>
```

### 描述搜索

```
in:description <text>
```

### readme文档搜索

```
in:readme <text>
```

## 参数限制

- 参数限制追加到搜索限制后

> `<value>`：限制条件
>> 数量限制条件格式：`>1000`
>> 语言限制条件格式：`java`
>> 时间限制条件格式：`2012-12-12`

### stars限制

```
start:<value>
```

### forks限制

```
forks:<value>
```

### 编程语言限制

```
language:<value>
```

### 最后更新时间限制

```
pushed:<value>
```

## 参考文献

[哔哩哔哩——CodeSheep](https://www.bilibili.com/video/av75587104)

