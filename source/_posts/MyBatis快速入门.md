---
title: 【代码】MyBatis快速入门
categories:
  - Java
date: 2020-08-20 09:30:25
---

## 前言

使用MyBatis作数据表的查询操作，将表内所有数据打印

<!-- more -->

## 创建POJO类

``` java
package com.tedu.pojo;

public class Emp {
    
    private Integer id;
    private String name;
    private String job;
    private Double salary;
    
    public Integer getId() {
        return id;
    }
    public void setId(Integer id) {
        this.id = id;
    }
    public String getName() {
        return name;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getJob() {
        return job;
    }
    public void setJob(String job) {
        this.job = job;
    }
    public Double getSalary() {
        return salary;
    }
    public void setSalary(Double salary) {
        this.salary = salary;
    }
    
    @Override
    public String toString() {
        return "Emp [id=" + id + ", name=" + name + ", job=" + job + ", salary=" + salary + "]";
    }
    
}

```

## 全局配置文件

- 在`src/main/resources`目录下新建`mybatis-config.xml`全局配置文件

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration
    PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-config.dtd">
    
<!-- MyBatis的全局配置文件 -->
<configuration >
    <!-- 1.配置环境，可配置多个环境（比如：develop开发、test测试） -->
    <environments default="develop">
        <environment id="develop">
            
            <!-- 1.1.配置事务管理方式：JDBC/MANAGED
            JDBC：将事务交给JDBC管理（推荐）
            MANAGED：自己管理事务
              -->
            <transactionManager type="JDBC"></transactionManager>
            
            <!-- 1.2.配置数据源，即连接池 JNDI/POOLED/UNPOOLED
                JNDI：已过时
                POOLED：使用连接池（推荐）
                UNPOOLED：不使用连接池
             -->
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.cj.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/yonghedb?serverTimezone=UTC"/>
                <property name="username" value="root"/>
                <property name="password" value="123456"/>
            </dataSource>
        </environment>
    </environments>
    
    <!-- 2.导入Mapper配置文件，如果mapper文件有多个，可以通过多个mapper标签导入 -->
    <mappers>
        <mapper resource="EmpMapper.xml"/>
    </mappers>
</configuration>
```

## Mapper配置文件

- 在`src/main/resources`目录下新建`EmpMapper.xml`Mapper配置文件

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper
    PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<!-- 
    不同Mapper文件的namespace值应该保证唯一
    在程序中通过[ namespace + id ]定位到要执行哪一条SQL语句
 -->
<mapper namespace="EmpMapper">
    <!-- 通过select、insert、update、delete标签声明要执行的SQL -->
    <!-- 练习1: 查询emp表中的所有员工信息
        resultType指定查询的结果将会封装到什么类型中
        即使最终返回的结果是集合(List<Emp>),resultType也只需要指定集合中的泛型即可!
    -->
    <select id="findAll" resultType="com.tedu.pojo.Emp">
        select * from emp
    </select>

</mapper>
```

## 测试类

``` java
package com.tedu;

import java.io.IOException;
import java.io.InputStream;
import java.util.List;

import org.apache.ibatis.io.Resources;
import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;
import org.junit.Test;

import com.tedu.pojo.Emp;

public class TestMybatis01 {
    
    @Test
    public void findAll() throws IOException {
        //1.读取mybatis的核心配置文件(mybatis-config.xml)
        InputStream in = Resources.getResourceAsStream("mybatis-config.xml");
        //2.通过配置信息获取一个SqlSessionFactory工厂对象
        SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
        SqlSessionFactory fac = sqlSessionFactoryBuilder.build( in );
        //3.通过工厂获取一个SqlSession对象
        SqlSession session = fac.openSession();
        //4.通过namespace+id找到要执行的sql语句并执行sql语句
        List<Emp> list = session.selectList("EmpMapper.findAll"); // namespace.id
        //5.输出结果
        for(Emp e : list) {
            System.out.println( e );
        }
    }
}

```

## 完成
