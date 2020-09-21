---
title: 【笔记】不使用submit提交表单的方法
categories:
  - HTML/CSS/JS
date: 2020-09-07 18:16:22
---

## 前言

不使用`<button type="submit"></button>`标签，也不使用`<input type="submit">`标签，提交表单的方法

<!-- more -->

## 提交表单

- html代码
- 必须定义name属性，因为会根据name属性向后端发送请求

``` html
<form id="formId">
    <div class="form-group">
        <label>标题：</label>
        <input type="text" name="title" id="titleId">
    </div>
</form>

<button type="button" onclick="doSave()">确定</button>
```

- javascript代码

``` javascript
function doSave() {
    // 定义传递参数的后端地址
    let url="";
    // 定义参数（通过jQuery的serialize()函数直接获取指定表单需要发送请求的数据）
    let params = $("#formId").serialize();
    // 发送请求（通过jQuery的ajax()函数发送异步请求）
    $.ajax({
        type:"post",
        url:url,
        data:params,
        success:function(result){
            console.log(result);
        }
    });
}
```

## 完成

