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

## 添加包扫描

- @ComponentScan("")
- 描述SpringBoot项目的启动类
- 将包名定义为参数，将指定包及子包下的类定义为Bean


- @MapperScan("")
- 将包名定义为参数，告诉Mybatis框架，为指定的包中所有的接口创建代理对象

## 定义普通的组件

- @Component
- 可以在业务类中通过@Autowired注解从Bean池中获取并注入对象
- 如果没有指定bean的名字，则默认为类名首字母小写（前提是起名要规范）

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

## 描述数据层实现类对象

- @Repository
- 描述在类上，是一种特殊的@Component

## 响应到客户端

- @ResponseBody
- 当使用此注解描述控制层方法时，用于告诉Spring框架，这个方法返回值可以按照特定格式（例如JSON）进行转换，将转换以后的结果写到response对象的相应体中
- 方法的返回值不在封装为ModelAndView对象，不会再交给解析器进行解析，而是直接基于response对象响应到客户端

### RestController

- @RestController
- 等效于同时描述`@Controller`和`@ResponseBody`

### RestControllerAdvice

- @RestControllerAdvice
- 等效于同时描述`@ControllerAdvice`和`@ResponseBody`

## 处理请求

### 处理所有请求

- @RequestMapping("")
- 参数为跳转的链接地址
- 可以描述类，也可以描述方法

#### 定义请求方式

- @RequestMapping(value="",method=RequestMethod.GET)
- @RequestMapping(value="",method=RequestMethod.POST)

### 处理Get请求方式

- @GetMapping()
- 等效于@RequestMapping(method=RequestMethod.GET)

### 处理POST请求

- @PostMapping()
- 等效于@RequestMapping(method=RequestMethod.POST)

### 允许任何网站通过javascript访问

- @CrossOrigin
- 标注在类或方法上

## 指定参数

- @Param("")
- 描述参数，可以指定参数

### Rest风格的参数传递

- @PathVariable("")
- 描述参数，可以指定Rest风格的参数
- 如果参数列表的参数名和链接的参数名相同，可以不加@PathVariable的参数

### 指定请求参数

- @RequestParam
- 描述参数，指定被描述的对象为请求接收对象
- 用来接收`application/x-www-form-urlencoded`格式数据

#### 支持参数个数不匹配

- @RequestParam(required=false)
- required默认为true，表示必须匹配参数个数，否则会报错

### 指定请求参数

- @RequestBody
- 描述参数，指定被描述的对象为请求接收对象
- `application/json`、`application/xml`格式数据必须用@RequestBody接收
- 也可以用来接收`application/x-www-form-urlencoded`格式数据

## DI注入对象

- @Autowired
- 描述属性，可以从Bean池中获取并注入对象，前提是要求实现的类或继承的类由Spring的组件注解标注
- 描述构造方法可以省略
- 描述set方法，通常配合无参构造
- 有参构造独立使用

### 指定注入对象名

- @Qualifier("")
- 需要配合@Autowired使用
- 对象名首字母小写
- 可以描述属性、构造方法、set方法参数

## 测试类

- @SpringBootTest
- 必须标注在SpringBoot项目的测试类上
- 类中的方法由@Test方法标注，使用Junit进行单元测试

## 全局异常处理类

- @ControllerAdvice
- 由此注解描述的类为一个控制层全局异常处理类，在此类中可以定义异常处理方法，机遇这些异常处理方法对异常进行处理

### 异常处理方法

- @ExceptionHandler(Throwable.class)
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

- @Scope("singleton")
- 不写@Scope参数或不写@Scope默认为单例作用域
- 单例会将创建的对象放在Bean池中
- 每个类只会创建一个对象，可以反复被调用

### 多实例

- @Scope("prototype")
- 多例在对象使用时创建，使用后销毁
- 多例创建每个类可以创建多个对象
- 这个实例创建以后，不会交给spring管理，spring可以对其初始化，但不负责销毁

## 对象生命周期方法

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

- [传送门](/2020/10/17/SpringAOP学习笔记/)

## 事务

- [传送门](/2020/10/24/SpringBoot事务处理/)

## 启动异步操作

- @EnableAsync
- 标注在启动类上

### 配置异步操作

- @Async
- 此注解描述的方法为一个异步切入点方法
- 此方法会在执行时运行在Spring框架提供的一个独立的线程中
- 如果返回值不为void需要做额外的处理


## 缓存

- [传送门](/2020/10/24/SpringBootCache/)

## 支持跨域访问

- @CrossOrigin
- 标注在Controller的方法上
- 使当前URL支持跨域访问

## 通过配置文件为对象赋值

- @Value("${father.son}")
- 针对于`application.yml`配置文件
- 标注在对象上
- 为所标注的对象赋值
- 参数为SPEL表达式

### 通过自定义配置文件

- 首先在`resources`目录下创建`properties`目录用于存放以`.properties`结尾的自定义配置
- @PropertySource("classpath:/properties/redis.properties")
- 标注在类上
- 之后再通过@Value标注在对象上，为所标注的对象赋值
- key必须唯一，因为当出现与全局配置`.yml`文件中的key同名时时，优先获取`.yml`文件中的配置

#### 以UTF-8格式加载properties以解决乱码

- 因为默认
- @PropertySource(value="classpath:/properties/redis.properties",encoding="utf-8")

## 未完待更
