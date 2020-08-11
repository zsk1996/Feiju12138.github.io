---
title:  【笔记】Java设计模式
categories:
  - Java
date: 2020-07-24 16:19:24
---

## 前言

Java 设计模式

<!-- more -->

## 单例设计模式

- 每个类只创建一个对象，节省内存

1. 构造方法私有
2. 外界设法获取内部创建好的对象
3. 对外提供全局访问点

### 饿汉式

``` java
public class Test {

    public static void main(String[] args) {
        MySingleton mySingleton = MySingleton.getMySingleton();
    }

}

class MySingleton {

    private static MySingleton mySingleton = new MySingleton();

    private MySingleton() {}

    public static MySingleton getMySingleton() {
        return mySingleton;
    }

}
```

### 懒汉式

``` java
public class Test {

    public static void main(String[] args) {
        MySingleton mySingleton = MySingleton.getMySingleton();
    }

}

class MySingleton {

    private static MySingleton mySingleton;

    private MySingleton() {}

    public static MySingleton getMySingleton() {
        if (mySingleton==null) {
            mySingleton = new MySingleton();
        }
        return mySingleton;
    }

}
```

#### 解决线程安全

``` java
public class Test {

    public static void main(String[] args) {
        MySingleton mySingleton = MySingleton.getMySingleton();
    }

}

class MySingleton {

    private static MySingleton mySingleton;

    private MySingleton() {}

    public static MySingleton getMySingleton() {
        synchronized (MySingleton.class) {
            if (mySingleton==null) {
                mySingleton = new MySingleton();
            }
            return mySingleton;
        }
    }

}
```

## 完成

