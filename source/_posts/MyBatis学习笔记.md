---
title: 【笔记】MyBatis学习笔记
categories:
  - null
date: 2020-08-20 16:18:09
---

## 前言

MyBatis是一个Java持久化框架，它通过XML描述符或注解把对象与存储过程或SQL语句关联起来。
MyBatis是在Apache许可证 2.0下分发的自由软件，是iBATIS 3.0的分支版本。其维护团队也包含iBATIS的初创成员。（[维基百科](https://zh.wikipedia.org/wiki/MyBatis)）

<!-- more -->

## 引入MyBatis

- 在Maven项目中引入MyBatis的jar包

- 编辑`pom.xml`文件

``` xml
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>3.2.8</version>
</dependency>
```

## 创建配置文件

- 在`src/main/resources`目录下新建`mybatis-config.xml`全局配置文件

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration
    PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-config.dtd">
    
<!-- MyBatis的全局配置文件 -->
<configuration >

</configuration>
```

- 在`src/main/resources`目录下新建`XxxMapper.xml`Mapper配置文件

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper
	PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
	"http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<!-- 
	不同Mapper文件的namespace值应该保证唯一
	在程序中通过[ namespace + id ]定位到要执行哪一条SQL语句
 -->
<mapper namespace="">

</mapper>
```

- 向全局配置文件引入Mapper配置文件

- 详细步骤[传送门](/2020/08/20/MyBatis快速入门/)

## MyBatis实现增删改查

- 读取mybatis的核心配置文件(mybatis-config.xml)
- 通过配置信息获取一个SqlSessionFactory工厂对象
- 通过工厂获取一个SqlSession对象

``` java
    SqlSession session;
    
    @Before
    public void testBefore() throws IOException {
        // 读取mybatis的核心配置文件(mybatis-config.xml)
        InputStream in = Resources.getResourceAsStream("mybatis-config.xml");
        // 通过配置信息获取一个SqlSessionFactory工厂对象
        SqlSessionFactoryBuilder sqlSessionFactoryBuilder = new SqlSessionFactoryBuilder();
        SqlSessionFactory fac = sqlSessionFactoryBuilder.build( in );
        // 通过工厂获取一个SqlSession对象
        session = fac.openSession(true);
    }
```

### 增

- 在Mapper定义SQL语句

``` xml
<insert id="ins">
    INSERT INTO emp VALUES(null, "赵云", "保安", 6000.0)
</insert>
```

- 返回int类型的值

``` java
@Test
public void testIns() {
    int rol = session.insert("EmpMapper.ins");
    System.out.println("影响的行数："+rol);
}
```

#### 占位符（多个）

- 在Mapper定义SQL语句

``` xml
<insert id="ins">
    INSERT INTO emp VALUES(null, #{name}, #{job}, #{salary})
</insert>
```

##### 通过POJO对象传参

- 返回int类型的值

``` java
@Test
public void testIns() {
    Emp emp = new Emp();
    emp.setName("赵云");
    emp.setJob("保安");
    emp.setSalary(6000.0);
    int rol = session.insert("EmpMapper.ins", emp);
    System.out.println("影响的行数："+rol);
}
```

##### 通过map对象传参

- 返回int类型的值

``` java
@Test
public void testIns() {
    Map map = new HashMap();
    map.put("name", "赵云");
    map.put("job", "保安");
    map.put("salary", 6000.0);
    int rol = session.insert("EmpMapper.ins", map);
    System.out.println("影响的行数："+rol);
}
```

### 删

- 在Mapper定义SQL语句

``` xml
<delete id="del">
    DELETE FROM emp
</delete>
```

- 返回int类型的值

``` java
@Test
public void testDel() {
    int rol = session.insert("EmpMapper.del");
    System.out.println("影响的行数："+rol);
}
```

#### 占位符

- 同上（[传送门](/2020/08/20/MyBatis学习笔记/#占位符（多个）)）

### 改

- 在Mapper定义SQL语句

``` xml
<update id="upd">
    UPDATE emp SET job='保镖', salary=20000.0 WHERE name='赵云'
</update>
```

- 返回int类型的值

``` java
@Test
public void testUpd() {
    int rol = session.insert("EmpMapper.upd");
    System.out.println("影响的行数："+rol);
}
```

#### 占位符

- 同上（[传送门](/2020/08/20/MyBatis学习笔记/#占位符（多个）)）

### 查

#### 查全部

- 在Mapper定义SQL语句

``` xml
<select id="findAll" resultType="com.tedu.pojo.Emp">
    SELECT * FROM emp
</select>
```

- 返回保存所有POJO对象的List对象

``` java
List<Emp> list = session.selectList("EmpMapper.findAll");
for(Emp e : list) {
    System.out.println(e);
}
```

#### 查指定行（占位符）

- 在Mapper定义SQL语句

``` xml
<select id="fin2" resultType="com.tedu.pojo.Emp">
    SELECT * FROM emp WHERE name=#{name}
</select>
```

- 如果只有一个参数，可以直接使用重载方法
- 如果返回结果只有一条，可以直接使用selectOne只接收一条

``` java
@Test
public void testFin2() {
    Emp emp = session.selectOne("EmpMapper.fin2", "赵云");
    System.out.println(emp);
}
```

#### 查指定列（占位符）

- 在Mapper定义SQL语句

``` xml
<select id="fin3" resultType="com.tedu.pojo.Emp">
    SELECT ${cols} FROM emp
</select>
```

- 返回保存所有POJO对象的List对象

``` java
@Test
public void testFin3() {
    Map map = new HashMap();
    map.put("cols", "name,job");
    List<Emp> selectList = session.selectList("EmpMapper.fin3", map);
    for (Emp emp:selectList) {
         System.out.println(emp.getName()+"\t"+emp.getJob());
    }
}
```

## 占位符

### 两种占位符示例（索引）

- `#{}`占位符示例[传送门](/2020/08/20/MyBatis学习笔记/#占位符（多个）)
- `${}`占位符示例[传送门](/2020/08/20/MyBatis学习笔记/#查指定列（占位符）)

### 三种传参方式示例（索引）

- 单个参数传参[传送门](/2020/08/20/MyBatis学习笔记/#查指定行（占位符）)
- map对象传参[传送门](/2020/08/20/MyBatis学习笔记/#通过map对象传参)
- POJO对象传参[传送门](/2020/08/20/MyBatis学习笔记/#通过POJO对象传参)

### 两种占位符的区别

- `#{}`在接收到数据后，如果是`日期类型`或`字符串类型`，会在前后添加引号，适用于指定值
- `${}`在接收到数据后，会直接将数据拼接到SQL语句中，适用于指定SQL子句
- `${}`如果指定了POJO对象不存在的成员变量，只能用[map方式传参](/2020/08/20/MyBatis学习笔记/#通过map对象传参)

## 标签和参数

> `<select></select>`：查询语句
>> `id`：与`@Mapper`所标注的类中方法名相对应
>> `resultType`：与`@Mapper`所标注的类中方法返回值类型（的别名）相对应
>> `resultMap`：[传送门](/2020/08/20/MyBatis学习笔记/#自定义映射)

> `<insert></insert>`：插入语句
>> `parameterType`：实体类的全局限定名
>> `useGeneratedKeys`：值为true时表示使用主键
>> `keyProperty`：指定主键名

> `<update></update>`：修改语句
> `<delete></delete>`：删除语句

> `<sql></sql>`：[传送门](/2020/08/20/MyBatis学习笔记/#Mybatis的xml实现sql代码的复用)

## MyBatis动态SQL标签

### if和where标签

- `<if test=""></if>`：是根据test属性中的布尔表达式的值，从而决定是否执行包含在其中的SQL片段。如果判断结果为true，则执行其中的SQL片段；如果结果为false，则不执行其中的SQL片段

- `<where></where>`：用于对包含在其中的SQL片段进行检索，在需要时可以生成where关键字，并且在需要时会剔除多余的连接词（比如and或者or）

#### 示例

- 如果不传参数，查询所有数据
- 如果传一个最小值，查询不小于最小值的数据
- 如果传一个最大值，查询不大于最大值的数据
- 如果传一个最小值和一个最大值，查询在最小值和最大值区间的数据

``` xml
<select id="fin4" resultType="com.tedu.pojo.Emp">
    SELECT * FROM emp
    <where>
        <if test="minSal != null">AND salary&gt;=#{minSal}</if>
        <if test="maxSal != null">AND salary&lt;=#{maxSal}</if>
    </where>
</select>
```

- 打印按照要求查询到的数据

``` java
@Test
public void testFin4() {
    Map map = new HashMap();
    map.put("minSal", "3500");
    map.put("maxSal", "5000");
    List<Emp> selectList = session.selectList("EmpMapper.fin4", map);
    for (Emp emp:selectList) {
        System.out.println(emp);
    }
}
```

### foreach标签

- `<foreach></foreach>`：可以对传过来的参数数组或集合进行遍历

#### 示例

> `collection`：传过来的参数类型（必须）
>> `array`：传过来的是数组
>> `list`：传过来的是集合
>> 如果将数组或集合存入map中，传过来的是map集合，就把对应的key写为参数

> `item`：定义迭代器名（必须）
> `open`：定义开头符号
> `separator`：定义间隔符号
> `close`：定义结尾符号

``` xml
<delete id="del">
    DELETE FROM emp WHERE id IN
    <foreach collection="array" item="id" open="(" separator="," close=")">
        #{id}
    </foreach>
</delete>
```

``` java
@Test
public void testDel() {
    Integer[] ids = {1, 2, 3, 4};
    session.delete("EmpMapper.del", ids);
}
```

## 面向接口开发

### 条件

1. 写一个接口，接口的全类名等于对应Mapper文件的namespace值
2. 接口中的方法名要对应Mapper文件中SQL标签的id值
3. 如果是查询，select标签上的resultType类型和接口中的方法的返回值类型保持一致（如果接口返回List<泛型>，resultType只需要指定集合中泛型即可）
4. 接口中的方法的参数类型和SQL标签上的参数类型（可以不指定）保持一致

### 示例

- 修改`EmpMapper.xml`中`<mapper></mapper>`标签内`namespace`的值为对应接口的全局限定名

``` xml
<mapper namespace="com.tedu.dao.EmpMapper">
    ...
</mapper>
```

- 在dao包下创建`EmpMapper`接口
- 接口内提供各种功能的抽象方法，根据SQL语句修改返回值类型

``` java
public interface EmpMapper {
    public List<Emp> findAll();
}
```

- 方法名需要和`EmpMapper.xml`内的对应标签的`id`值相同

``` xml
<select id="findAll" resultType="com.tedu.pojo.Emp">
    select * from emp
</select>
```

- 在测试类中，使用session对象，通过反射，获取`EmpMapper`实现类（我们只需要定义接口，实现类由框架为我们提供）
- 通过mapper对象调用对应方法实现增删改查

``` java
@Test
public void testFindAll() {
    EmpMapper mapper = session.getMapper(EmpMapper.class);
    List<Emp> findAll = mapper.findAll();
    for (Emp emp : findAll) {
        System.out.println(emp);
    }
}
```

## 面向注解开发

### 示例

- 在面向接口开发的基础上，可以删除`EmpMapper.xml`文件
- 在接口定义的抽象方法上使用注解`@Insert`、`@Delete`、`@Update`、`@Select`作增删改查操作

``` java
public interface EmpMapper {
    @Select("select * from emp")
    public List<Emp> findAll();
}
```

- 注意：不允许重载方法，原因是面向注解开发不允许出现同名方法

## Mapper.xml特殊符号处理方式

### 使用html转义字符

- `>`：`&gt;`
- `<`：`&lt;`

### 使用CDATA区存放特殊符号

``` xml
<![CDATA[>]]>
<![CDATA[<]]>
```

## Mybatis的xml实现sql代码的复用

- 将重复语句写在`<sql></sql>`标签内，在其他语句通过id属性引用

``` xml
<sql id="id1">
    ...
</sql>

<select id="id2">
    <include refid="id1" />
</select>
```

## jdbc注册信息写入properties文件

- 在`src/main/resources`目录下新建`jdbc.properties`配置文件

``` properties
jdbc.driver=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/yonghedb?characterEncoding=utf-8&serverTimezone=UTC
jdbc.username=root
jdbc.password=123456
```

- 在`mybatis-config.xml`的`<configuration></configuration>`标签哪引入

``` xml
<configuration>
    <properties resource="jdbc.properties"/>
</configuration>
```

- 将`mybatis-config.xml`内的jdbc注册信息由常量改成变量

``` xml
<dataSource type="POOLED">
    <property name="driver" value="${jdbc.driver}"/>
    <property name="url" value="${jdbc.url}"/>
    <property name="username" value="${jdbc.username}"/>
    <property name="password" value="${jdbc.password}"/>
</dataSource>
```

## 自定义映射

- resultMap为框架中实现高级映射时采用的一种映射策略
- 主要用于表中字段与类中属性不匹配、用于多表嵌套查询、用于多表关联查询

### 定义一个查询

``` xml
<select id="" resultMap="">
    ...
</select>
```

#### 一对一

> `resultMap`->`id`：与查询语句的`resultMap`值相对应
> `resultMap`->`type`：返回值实体类的全局限定名
> `<id></id>`：主键字段映射
> `<result></result>`：自定义映射
> `column`：对应的查询到结果的数据表字段
> `property`：对应的类的属性名

``` xml
<resultMap id="" type="">
    <id property="id" column="id"></id>
    <result property="name" column="name"></result>
</resultMap>
```

#### 一对多

> `ofType`：结果集中每个结果的类型
> `collection`->`select`：嵌套查询。@Mapper所标注的类中方法的全局限定名
> `collection`->`column`与`result`->`column`：均为对应的查询到结果的数据表字段，如果相同可以省略`<result></result>`

``` xml
<resultMap id="" type="">
    <collection id="" column="" property="" ofType="" select="">
        <result column=""></result>
    </collection>
</resultMap>
```

#### 多对一

``` xml
<resultMap id="" type="">
    <association id="" column="" property="" select="">
    </association>
</resultMap>
```

## 完成
