---
title: 【笔记】Spring MVC 响应数据
categories:
  - Java
date: 2020-08-24 11:40:14
---

## 前言

Spring MVC 响应数据

<!-- more -->

## 准备工作

### 配置前端页面访问路径的前后缀

- 不配置默认使用以下为默认值

``` properties
spring.thymeleaf.prefix=classpath:/templates/
spring.thymeleaf.suffix=.html
```

## 只跳转页面

- 以后我们写代码可以单独写`TemplatePageController`用于处理页面跳转

### 返回字符串（常用）

- 通过返回的字符串(string)，根据prefix+string+suffix进行页面跳转

``` java
@RequestMapping("")
public String testModel() {
    ...
    return "";
}
```

#### 请求转发

##### 转发到本项目

``` java
@RequestMapping("")
public String testForward() {
    ...
    return "index";
}
```

##### 转发到其他位置

- 在return加前缀`forward:`

``` java
@RequestMapping("")
public String testForward() {
    ...
    return "forward:/index";
}
```

#### 目标重定向

##### 重定向到站内

- 在SpringMVC中目标重定向也可以通过Model传递参数
- 在return加前缀`redirect:`

``` java
@RequestMapping("/testRedirect")
public String testRedirect() {
    ...
    return "redirect:/test";
}
```

##### 重定向到站外

``` java
@RequestMapping("/testRedirect")
public String testRedirect() {
    ...
    return "redirect:/http://localhost:8080/";
}
```

## 只响应数据

- 以后我们写代码可以单独写`JsonObjectController`用于响应数据

### 返回Map对象（常用）

- 由`@ResponseBody`注解标注，ModelAndView会自动将返回值转换为json格式字符串

``` java
@RequestMapping("")
@ResponseBody
public Map<String, Object> testMap() {
    Map<String, Object> map = new HashMap<>();
    map.put(<key>, <value>);
    return map;
}
```

### 返回值为空

- 将数据存储在Map对象，将Map对象转换为json格式字符串
- 通过HttpServletResponse对象，响应数据到客户端

``` java
@RequestMapping("")
public void testVoid(HttpServletResponse response) throws Exception {
    Map<String, Object> map = new HashMap<>();
    map.put(<key>, <value>);
    // 将map中的数据转换为json格式字符串
    ObjectMapper objectMapper = new ObjectMapper();
    String jsonStr = objectMapper.writeValueAsString(map);
    // 设置响应数据的编码
    //response.setCharacterEncoding("utf-8");
    // 告诉客户端相应数据类型为text/html，编码为utf-8，请以这种编码形式进行数据呈现
    response.setContentType("text/html;charset=utf-8");
    // 将字符串响应到客户端
    response.getWriter().println(jsonStr);
}
```

## 既相应数据，又跳转页面

- 以后我们写代码可以单独写`ModelAndViewController`用于同时页面跳转并响应数据

### 返回ModelAndView对象（常用）

- 返回值会交给DispatcherServletd对象进行处理
- DispatcherServlet对象会调用viewresolver对结果进行解析
- 基于viewresolver找到对应的view页面（prefix+viewname+suffix）
- 将model中的数据填充到view页面上
- 返回一个带有model数据的页面给DispatcherServlet
- DispatcherServlet将带有model数据的页面响应到客户端

``` java
@RequestMapping("")
public ModelAndView testModelAndView() {
    ModelAndView modelAndView = new ModelAndView();
    modelAndView.setViewName("");
    modelAndView.addObject(<key>, <value>);
    return modelAndView;
}
```

### 返回字符串

- 通过Model对象传输数据，将数据填充到页面上
- 通过返回的字符串(string)，根据prefix+string+suffix进行页面跳转

> `<key>`：键，仅可以字符串类型
> `<value>`：值，可以任意类型

``` java
@RequestMapping("")
public String testModel(Model model) {
    model.addAttribute(<key>, <value>);
    ...
    return "";
}
```

## 完成

