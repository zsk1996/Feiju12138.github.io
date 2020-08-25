---
title: 【笔记】Spring DI 依赖注入
categories:
  - Java
date: 2020-08-22 10:40:00
---

## 前言

Spring DI 依赖注入

<!-- more -->

## 依赖注入

### set方法注入

- 在POJO类中写set方法

- 修改`applicationContext.xml`文件中的`<bean></bean>`标签

> `name`：变量名
> `value`：为变量赋值。调用对象相对应的set方法
> `ref`：为引用类型变量赋值。创建其他bean标签，调用set方法，将id值赋予为ref值

``` xml
<bean id="" class="">
    <property name="" value=""/>
    <property name="" ref=""/>
</bean>
```

### 构造方法注入

- 在POJO类中写构造方法

- 修改`applicationContext.xml`文件中的`<bean></bean>`标签

``` xml
<bean id="" class="">
    <constructor-arg name="" value=""/>
    <constructor-arg name="" ref=""/>
</bean>
```

- 注意：`<bean></bean>`标签内指定参数的数量需要和POJO类中构造方法的参数列表相同

## 完成

