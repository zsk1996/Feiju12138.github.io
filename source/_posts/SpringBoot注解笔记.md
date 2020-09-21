---
title: 【笔记】SpringBoot注解笔记
categories:
  - Java
date: 2020-08-26 17:34:05
---

## 前言

SpringBoot注解知识点笔记

<!-- more -->

## 入口注解

- @SpringBootApplication
- 描述SpringBoot项目的启动类，在类中会定义一个main方法，main方法会在运行时读取配置文件，并且加载指定资源，进行初始化操作

## 定义普通的组件

- @Component
- 可以在业务类中通过@Autowired注解从Bean池中获取并注入对象

## SpringMVC

### 持久层

- @Mapper
- 标注Dao层，是一种特殊的@Component

### 业务层

- @Service
- 标注业务层，是一种特殊的@Component

### 控制层

- @Controller
- 标注控制层，是一种特殊的@Component

## Rest风格的响应

- @ResponseBody
- 将字符串返回给AJAX

### RestController

- @RestController
- 等效于同时描述`@Controller`和`@ResponseBody`

### RestControllerAdvice

- @RestControllerAdvice
- 等效于同时描述`@ControllerAdvice`和`@ResponseBody`

## 指定访问路径

- @RequestMapping("")
- 可以描述类，也可以描述方法

## 指定参数

- @Param("")
- 描述参数，可以指定参数

## 注入对象

- @Autowired
- 描述属性，可以从Bean池中获取并注入对象，前提是要求实现的类或继承的类由Spring的组件注解标注
- 描述构造方法可以省略
- 描述set方法，通常配合无参构造
- 有参构造独立使用

### 指定注入对象名

- @Qualifier("")
- 对象名首字母小写
- 不能修饰方法

## 测试类

- @SpringBootTest
- 必须标注在SpringBoot项目的测试类上
- 类中的方法由@Test方法标注，使用Junit进行单元测试

## 全局异常处理类

- @ControllerAdvice
- 由此注解描述的类为一个控制层全局异常处理类，在此类中可以定义异常处理方法，机遇这些异常处理方法对异常进行处理

### 异常处理方法

- @ExceptionHandler(RuntimeException.class)
- 由此注解标注的方法为一个异常处理方法，在注解内部定义的异常类型为此方法可以处理的异常类型，包括异常的子类类型
- 可以在方法的参数列表传递与异常处理的类型相同类型（或父类类型）的参数

## 配置类

- @Configuration
- 由此注解描述的类为一个配置类

## Spring管理的Bean

- @Bean
- Spring容器中整个第三方Bean对象时，可以将其Bean对象的创建放在一个方法中，然后使用@Bean注解进行描述，Spring容器管理Bean对象时就会将方法名作为key对Bean对象进行存储

## 延时加载

### 标注在类上

- @Lazy(value=true)
- 简写为@Lazy(true)
- 简写为@Lazy
- 也称为懒加载
- 此注解告诉Spring框架，它描述的类的实例，假如暂时用不到，就不要先创建，当需要调用时再创建
- 只在单例情况下有效

## 单例和多例

- 标注在类上

### 单实例

- 单例@Scope("singleton")
- 单例会将创建的对象放在Bean池中
- 每个类只会创建一个对象，可以反复被调用

### 多实例

- 多例@Scope("prototype")
- 多例在对象使用时创建，使用后销毁
- 多例创建每个类可以创建多个对象
- 这个实例创建以后，不会交给spring管理，spring可以对其初始化，但不负责销毁

### 初始化方法

- @PostConstruct
- 标注在方法上
- 描述的方法会在对象构建以后执行
- 用于执行一些初始化操作

### 结束方法

- @PreDestroy
- 描述的方法会在单例对象销毁之前执行
- 只有在单例上时会生效
- Spring容器会在销毁之前会先将容器（Bean）中的对象移除，在移除之前，假如对象中定义了生命周期销毁方法，此时还会调用对象的生命周期销毁方法（在方法中做一些资源释放操作）

## 异常处理

- @ControllerAdvice
- 描述的类为全局异常处理类
- 在此类中可以定义异常处理方法，基于这些异常处理方法，对异常进行处理

### 全局异常处理方法

- @ExceptionHandler(RuntimeException.class)
- 全局异常处理类的异常处理方法

## Spring AOP

### 切面类型

- @Aspect
- 注解用于标识或者描述AOP中的切面类型，基于切面类型构建的对象用于为目标对象进行功能扩展或控制目标对象的执行

### 切入点

- Pointcut("bean()")
- 注解用于描述切面中的方法，并定义切面中的切入点（基于特定表达式的方式进行描述）
- 切入点表达式用的是bean表达式，这个表达式以bean开头，bean括号中的内容为一个spring管理的某个bean对象的名字

#### 切入点表达式增强

##### bean

- 用于指定bean对象的所有方法
- bean表达式一般应用于类级别，实现粗粒度的切入点定义

###### 指定一个类中所有方法

> `<class>`：类名

``` java
bean("<class>")
```

###### 指定包含一个类名结尾的所有方法

``` java
bean("*<class>")
```

##### within

- within表达式应用于类级别，实现粗粒度的切入点表达式定义

###### 指定当前包中这个类内部的所有方法

> `<package>`：包名

``` java
within("<package>.<class>")
```

###### 指定当前目录下的所有类的所有方法

``` java
within("<package>.*")
```

###### 指定当前目录以及子目录中类的所有方法

``` java
within("<package>..*")
```

##### execution

- execution表达式应用于方法级别，实现细粒度的切入点表达式定义

###### 匹配无参方法

``` java
execution(void <package>.<class>())
```

###### 匹配有参方法

``` java
execution(void <package>.<class>(String))
```

##### @annotation

- @annotaion表达式应用于方法级别，实现细粒度的切入点表达式定义

###### 匹配有指定自定义注解描述的方法

- 定义自定义注解

> `<aspect>`：自定义注解名注解名

``` java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface <aspect> {

}
```

- 通过指定自定义注解，为此注解所标注的方法，定义切入点

> `<method>`：方法名
> `<notice>`：通知名

``` java
@Pointcut("@annotation(<package>.<aspect>)")
public void <method>() {}

@<notice>("<method>()")
public void do<method>(){
    ...
}
```

### 通知方法

#### 环绕通知

- @Around("")
- 注解用于描述切面中方法
- 在目标方法执行之前（@Before之前）和目标方法结束之前（@After之前）都要执行
- 注解内部value属性的值为一个切入点表达式或者是切入点表达式的一个引用，这个引用为一个@PointCut注解描述的方法的方法名（包括参数列表）
- ProceedingJoinPoint只能作为环绕通知参数

#### 其他通知

- @Before("")
- 在目标方法执行之前执行


- @After("")
- 在目标方法结束之前执行


- @AfterReturning("")
- 在目标方法正常结束之前执行

- @AfterThrowing("")
- @AfterThrowing(value="",throwing="e")
- 在目标方法异常结束之前执行

#### 测试类

- 正常执行顺序：`@Around.before`->`@Before`->`@Around.after`->`@After`->`@AfterReturning`
- 异常执行顺序：`@Around.before`->`@Before`->`@Around.error`->`@After`->`@AfterThrowing`

``` java
@Component
@Aspect
public class SysTimeAspect {
    @Pointcut("bean(sysUserServiceImpl)")
    public void doTime(){}

    @Before("doTime()")
    public void doBefore(JoinPoint jp){
        System.out.println("@Before");
    }
    @After("doTime()")
    public void doAfter(){
        System.out.println("@After");
    }
    @AfterReturning("doTime()")
    public void doAfterReturning(){
        System.out.println("@AfterReturning");
    }
    @AfterThrowing("doTime()")
    public void doAfterThrowing(){
        System.out.println("@AfterThrowing");
    }
    @Around("doTime()")
    public Object doAround(ProceedingJoinPoint jp)
            throws Throwable{
        System.out.println("@Around.before");
        try{
            Object obj=jp.proceed();
            System.out.println("@Around.after");
            return obj;
        }catch(Throwable e){
            System.out.println("@Around.error");
            throw e;
        }

    }
}
```

### 定义切面优先级

- @Order(1)
- 用于描述切面类
- 数字越小，优先级越高
- 可以是负数

## 事务

- @Transactional
- 用于描述类或方法，方法的注解优先级高于类的注解优先级
- 启动事务

### 线程安全

- @Transactional(readonly=false)
- readonly默认为false
- 查询建议readonly=true

### 回滚策略

- @Transactional(rollbackFor=Throwable.class)
- 指定异常添加到回滚策略
- 默认策略有RuntimeException和Error
- 但是检查异常不回滚

#### 不回滚策略

- @Transactional(noRollbackFor=Throwable.class)

### 是否超时

- @Transactional(timeout=-1)
- 是否支持事务超时
- 默认值为-1，表示不支持事务超时，我们可以给定一个秒值

### 隔离级别

- @Transactional(isolation=Isolation.READ_COMMITTED)
- 默认值

- @Transactional(isolation=Isolation.SERIALIZABLE)

- @Transactional(isolation=Isolation.REPEATABLE_READ)

### 事务的传播特性

- @Transactional(propagation=Propagation.REQUIRED)

- @Transactional(propagation=Propagation.REQUIREDS_NEW)
- 放在一个独立的事务中

## 启动异步操作

- @EnableAsync
- 标注在启动类上

### 配置异步操作

- @Async
- 此注解描述的方法会运行在Spring框架提供的一个线程中
- 如果返回值不为void需要做额外的处理

## 启动缓存

- @EnableCaching
- 标注在启动类上

### 配置缓存操作

- @Cacheable

#### 指定缓存名称

- @Cacheable(value="")

#### 清除所有缓存

- @Cacheable(allEntries=true)

## 未完待更
