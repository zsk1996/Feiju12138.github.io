---
title: 【笔记】SpringBoot 发邮件
categories:
  - Java
date: 2020-09-23 16:15:15
---

## 前言

SpringBoot项目实现发邮件，案例通过QQ邮箱实现

<!-- more -->

## 准备工作

- 导入依赖

> `Spring Web`
> `Java Mail Sender`

## 源代码

- 修改`application.properties`项目配置文件

``` properties
server.port=80

spring.mail.host=smtp.qq.com
#改成自己的邮箱
spring.mail.username=000000@qq.com
#邮箱的密码(QQ邮箱需要使用授权码)
spring.mail.password=000000
spring.mail.default-encoding=utf-8
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
spring.mail.properties.mail.smtp.starttls.required=true
```

- 创建Controller做测试

``` sh
package com.cy.mail.pj;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.mail.SimpleMailMessage;
import org.springframework.mail.javamail.JavaMailSender;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.io.PrintWriter;
import java.io.StringWriter;

@RestController
public class MailController {

    //加上autowired之后，框架创建一个JavaMailSender，赋值给javaMailSender
    @Autowired
    JavaMailSender javaMailSender;

    public void sendMail(String subject, String text) {
        //创建一封邮件
        SimpleMailMessage mailMessage = new SimpleMailMessage();
        //设置收件人
        mailMessage.setTo("000000@qq.com");
        //设置发件人
        mailMessage.setFrom("000000@qq.com");
        //设置标题
        mailMessage.setSubject(subject);
        //设置正文
        mailMessage.setText(text);
        //发送邮件
        javaMailSender.send(mailMessage);
    }

    // 成功案例
    @RequestMapping("/send1")
    public String send1() {
        sendMail("邮件标题", "邮件正文");
        return "发送成功";
    }

    // 失败案例
    @RequestMapping("/send2")
    public String send2() {
        try {
            int n = 10 / 0;
        } catch (Exception e) {
            //异常信息打印到服务器中，程序员看不到
            //e.printStackTrace();
            //把异常信息转成字符串
            StringWriter stingWriter = new StringWriter();
            PrintWriter printWriter = new PrintWriter(stingWriter);
            e.printStackTrace(printWriter);
            String execeptionInfo = stingWriter.toString();
            //return execeptionInfo;
            this.sendMail("异常信息", execeptionInfo);
            return "发送失败";
        }
        return "发送成功";
    }

}
```

## 完成

- 访问`http://localhost/send1`测试发送成功效果
- 访问`http://localhost/send2`测试发送失败效果

