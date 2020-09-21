---
title: 【笔记】MyBatis缓存
categories:
  - Java
date: 2020-09-15 16:23:27
---

## 前言

MyBatis缓存

<!-- more -->

## 一级缓存

- 一级缓存默认开启
- 使用同一个`SqlSession`进行SQL语句的查询，只会查询一次

``` java
@Test
public void testFirstLevelCache() {
    SqlSession session = ssf.openSession();
    String statement = "com.cy.pj.sys.dao.SysMenuDao.findObjects";
    session.selectList(statement);
    session.selectList(statement);
    session.close();
}
```

## 二级缓存

- 使用不同的`SqlSession`进行SQL语句的查询，会查询两次
- 二级缓存默认开启，但需要配置。需要在Mapper里写`<cache/>`标签，在代码中使用`commit()`进行提交。此时只会查询一次

``` xml
<mapper namespace="">
    <cache/>
</mapper>
```

``` java
@Test
public void testSecondLevelCache() {
    SqlSession session1 = ssf.openSession();
    SqlSession session2 = ssf.openSession();
    String statement = "com.cy.pj.sys.dao.SysMenuDao.findObjects";
    session1.selectList(statement);
    session1.commit();
    session2.selectList(statement);
    session1.close();
    session2.close();
}
```

### 更多配置

> `eviction`：缓存策略
> `flushInterval`：每隔指定毫秒值刷新
> `size`：最多可以存储结果对象或列表的引用个数
> `readyOnle`：是否只读
>> `false`：默认值。多个线程使用反序列化实现缓存，会产生两个对象
>> `true`：多个线程使用相同对象地址实现缓存，会产生一个对象

``` xml
<cache
  eviction="FIFO"
  flushInterval="60000"
  size="512"
  readOnly="true"/>
```

## 完成

