---
title: 【笔记】Socket 网络编程
categories:
  - Java
date: 2020-07-27 16:53:50
---

## 前言

Java Socket&ServerSocket 网络套接字编程

<!-- more -->

## ServerSocket

- 服务器代码

``` java
import java.io.InputStream;
import java.io.OutputStream;
import java.net.ServerSocket;
import java.net.Socket;

public class Server {
    public static void main(String[] args) throws Exception {
        // 创建ServerSocket对象，参数为开放的端口号
        ServerSocket server = new ServerSocket(8000);
        System.out.println("服务器已启动");
        // 获取客户端的连接（Socket对象）
        Socket socket = server.accept();
        // 获取IO流
        InputStream in = socket.getInputStream();
        OutputStream out = socket.getOutputStream();

        // IO读写操作
        ...

        out.flush(); // 把资源刷出去但不关闭资源
    }
}
```

## Socket

- 客户端代码

``` java
import java.io.InputStream;
import java.io.OutputStream;
import java.net.Socket;

public class Client {
    public static void main(String[] args) throws Exception {
        // 创建Socket对象，参数为服务器IP地址和端口号
        Socket socket = new Socket("127.0.0.1", 8000);
        System.out.println("与服务器连接成功");
        // 获取IO流
        InputStream in = socket.getInputStream();
        OutputStream out = socket.getOutputStream();
        
        // IO读写操作
        ...

        out.flush(); // 把资源刷出去但不关闭资源
    }
}
```

## 完成

