---
title: 【笔记】SpringBoot整合Mybatis框架
categories:
  - Java
date: 2020-08-29 10:58:58
---

## 前言

SpringBoot整合Mybatis框架

<!-- more -->

## 在pom.xml添加依赖

``` xml
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.1.3</version>
</dependency>
```

## SpringBoot配置

- 编辑`application.properties`配置文件
- 配置Mybatis的Mapper文件位置

``` properties
mybatis.mapper-locations=classpath:/mapper/*/*.xml
```

## 注解方式

- 删除指定一条数据实例

### Dao层定义接口

- 实现删除业务示例

``` java
@Mapper
public interface GoodsDao {
    /**
     * 在Mybatis中假如SQL映射语句比较简单，可以直接在dao方法上以注解方式进行定义
     */
    @Delete("DELETE FROM tb_goods WHERE id=#{id}")
    public String deleteById(Integer id);

}
```

### 测试类

``` java
@SpringBootTest
public class GoodsDaoTests {
    
    /**
     * 关联数据层接口，并由Spring为其进行值的注入
     */
    @Autowired
    private GoodsDao goodsDao;
    
    @Test
    public void testDeleteById() throws Exception {
        String row = goodsDao.deleteById(1);
        System.out.println("影响的行数："+row);
    }

}
```

## xml方式

- 删除指定多条记录示例

### 定义Mapper文件

- 在`/src/main/resources/mapper/goods`新建`Goods.Mapper.xml`SQL映射文件

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.cy.pj.goods.dao.GoodsDao">
    <delete id="deleteObjects">
        delete from tb_goods where id in <!-- (1,2,3,4,5) -->
        <foreach collection="ids" open="(" close=")"
            separator="," item="id">
            #{id}
        </foreach>
    </delete>
</mapper>
```

### 配置Mapper文件

- 修改`application.properties`文件

``` properties
mybatis.mapper-locations=classpath:mapper/*/*.xml
```

### Dao层定义接口

``` java
@Mapper
public interface GoodsDao {
    public Integer deleteObjects(@Param("ids")Integer... ids);
}
```

### 测试类

``` java
@SpringBootTest
public class GoodsDaoTests {
    
    /**
     * 关联数据层接口，并由Spring为其进行值的注入
     */
    @Autowired
    private GoodsDao goodsDao;
    
    @Test
    public void testDeleteObjects() throws Exception {
        int row = goodsDao.deleteObjects(2,4);
        System.out.println("影响的行数："+row);
    }

}
```

## 完成

