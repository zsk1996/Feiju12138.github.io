---
title: 【笔记】Spring AOP 快速入门
categories:
  - Java
date: 2020-09-16 11:12:45
---

## 前言

Spring AOP 快速入门

<!-- more -->

## 快速入门

- 在service添加一个切面，用于添加代码执行的日志信息

``` java
@Aspect
@Slf4j
@Component
public class SysLogAspect {

    @Pointcut("bean(sysUserServiceImpl)")
    public void logPointCut() {}

    @Around("logPointCut()")
    public Object around(ProceedingJoinPoint jp)
            throws Throwable{
        try {
            long t1 = System.currentTimeMillis();
            Object result=jp.proceed();//最终会调用目标方法
            long t2 = System.currentTimeMillis();
            log.info("目标方法执行时常: {}",t2-t1);
            return result;
        }catch(Throwable e) {
            log.error("目标方法执行过程中出现了问题: {}"+e.getMessage());
            throw e;
        }
    }
}
```

## 完成
