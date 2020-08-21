---
title: 【笔记】Eclipse添加Servlet模版
categories:
  - Java
date: 2020-08-21 21:31:37
---

## 前言

在Eclipse添加Servlet模版，这样以后就可以通过提示自动补齐为模版代码

<!-- more -->

## 添加模版

- `Eclipse`->`Preferences`->`java`->`Editor`->`Templates`

![01.png](/images/20200821213137/01.png)

- 添加模版

![02.png](/images/20200821213137/02.png)

``` java
package ${enclosing_package};

import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

public class ${primary_type_name} extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.setContentType("text/html;charset=utf-8");
		PrintWriter out = response.getWriter();
	}
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doGet(request, response);
	}
}
```

- `Apply and Close`保存并退出

## 完成
