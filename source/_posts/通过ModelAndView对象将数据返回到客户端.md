---
title: 【代码】通过ModelAndView对象将数据返回到客户端
categories:
  - Java
date: 2020-09-30 16:09:08
---

## 前言

SpringBoot项目中Controller层，通过ModelAndView对象将数据返回到客户端

<!-- more -->

## 代码

- 返回值会交给DispatcherServletd对象进行处理
- DispatcherServlet对象会调用viewresolver对结果进行解析
- 基于viewresolver找到对应的view页面（prefix+viewname+suffix）
- 将model中的数据填充到view页面上
- 返回一个带有model数据的页面给DispatcherServlet
- DispatcherServlet将带有model数据的页面响应到客户端

``` java
public ModelAndView do() {// 此对象由DispatcherServlet对象通过反射调用
    ModelAndView modelAndView = new ModelAndView();
    modelAndView.setViewName("default");
    modelAndView.addObject("username","chenzishu");
    modelAndView.addObject("state","yajiankang");
    return modelAndView;
}
```

## 完成

