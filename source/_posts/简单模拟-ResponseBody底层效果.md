---
title: 【代码】简单模拟@ResponseBody底层效果
categories:
  - Java
date: 2020-09-30 15:59:12
---

## 前言

SpringBoot项目中，当使用@ResponseBody注解描述控制层方法时，用于告诉Spring框架，这个方法返回值可以按照特定格式（例如JSON）进行转换，将转换以后的结果写到response对象的相应体中
方法的返回值不在封装为ModelAndView对象，不会再交给解析器进行解析，而是直接基于response对象响应到客户端

<!-- more -->

## 标注后代码

- 通过返回对象，底层会自动将处理结果响应到客户端

``` java
@ResponseBody
public Map<String, Object> doPrint() {
    Map<String, Object> map = new HashMap<>();
    map.put("username","刘德华");
    map.put("state",true);
    return map;
}
```

## 标注前代码

- 底层实现的代码

``` java
public void doPrint(HttpServletResponse response) throws Exception {
    Map<String, Object> map = new HashMap<>();
    map.put("username","刘德华");
    map.put("state",true);
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

## 完成

