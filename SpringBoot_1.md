# SpringBoot

## 1、SpringBoot简介

### 1.1、什么是Spring

Spring是一个开源框架，2003 年兴起的一个轻量级的Java 开发框架，作者：Rod Johnson  。

**Spring是为了解决企业级应用开发的复杂性而创建的，简化开发。**

### 1.2、Spring如何简化Java开发

为了降低Java开发的复杂性，Spring采用了以下4种关键策略：

1、基于POJO的轻量级和最小侵入性编程，所有东西都是bean；

2、通过IOC，依赖注入（DI）和面向接口实现松耦合；

3、基于切面（AOP）和惯例进行声明式编程；

4、通过切面和模版减少样式代码，RedisTemplate，xxxTemplate；

### 1.3、什么是SpringBoot

为了降低Java开发的复杂性，Spring采用了以下4种关键策略：

1、基于POJO的轻量级和最小侵入性编程，所有东西都是bean；

2、通过IOC，依赖注入（DI）和面向接口实现松耦合；

3、基于切面（AOP）和惯例进行声明式编程；

4、通过切面和模版减少样式代码，RedisTemplate，xxxTemplate；

什么是SpringBoot呢，就是一个javaweb的开发框架，和SpringMVC类似，对比其他javaweb框架的好处，官方说是简化开发，约定大于配置，  you can "just run"，能迅速的开发web应用，几行代码开发一个http接口。

所有的技术框架的发展似乎都遵循了一条主线规律：从一个复杂应用场景 衍生 一种规范框架，人们只需要进行各种配置而不需要自己去实现它，这时候强大的配置功能成了优点；发展到一定程度之后，人们根据实际生产应用情况，选取其中实用功能和设计精华，重构出一些轻量级的框架；之后为了提高开发效率，嫌弃原先的各类配置过于麻烦，于是开始提倡“约定大于配置”，进而衍生出一些一站式的解决方案。

是的这就是Java企业级应用->J2EE->spring->springboot的过程。

随着 Spring 不断的发展，涉及的领域越来越多，项目整合开发需要配合各种各样的文件，慢慢变得不那么易用简单，违背了最初的理念，甚至人称配置地狱。Spring Boot 正是在这样的一个背景下被抽象出来的开发框架，目的为了让大家更容易的使用 Spring 、更容易的集成各种常用的中间件、开源软件；

Spring Boot 基于 Spring 开发，Spirng Boot 本身并不提供 Spring 框架的核心特性以及扩展功能，只是用于快速、敏捷地开发新一代基于 Spring 框架的应用程序。也就是说，它并不是用来替代 Spring 的解决方案，而是和 Spring 框架紧密结合用于提升 Spring 开发者体验的工具。Spring Boot 以**约定大于配置的核心思想**，默认帮我们进行了很多设置，多数 Spring Boot 应用只需要很少的 Spring 配置。同时它集成了大量常用的第三方库配置（例如 Redis、MongoDB、Jpa、RabbitMQ、Quartz 等等），Spring Boot 应用中这些第三方库几乎可以零配置的开箱即用。

简单来说就是SpringBoot其实不是什么新的框架，它默认配置了很多框架的使用方式，就像maven整合了所有的jar包，spring boot整合了所有的框架 。

Spring Boot 出生名门，从一开始就站在一个比较高的起点，又经过这几年的发展，生态足够完善，Spring Boot 已经当之无愧成为 Java 领域最热门的技术。

**Spring Boot的主要优点：**

- 为所有Spring开发者更快的入门
- **开箱即用**，提供各种默认配置来简化项目配置
- 内嵌式容器简化Web项目
- 没有冗余代码生成和XML配置的要求

## 2、HelloWorld

### 2.1、创建基础项目说明

Spring官方提供了非常方便的工具让我们快速构建应用

Spring Initializr：https://start.spring.io/

**项目创建方式一：**使用Spring Initializr 的 Web页面创建项目

1、打开  https://start.spring.io/

2、填写项目信息

3、点击”Generate Project“按钮生成项目；下载此项目

4、解压项目包，并用IDEA以Maven项目导入，一路下一步即可，直到项目导入完毕。

5、如果是第一次使用，可能速度会比较慢，包比较多、需要耐心等待一切就绪。

![image-20210407223351847](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210407223351847.png)



**项目创建方式二：**使用 IDEA 直接创建项目

1、创建一个新项目

2、选择spring initalizr ， 可以看到默认就是去官网的快速构建工具那里实现

3、填写项目信息

4、选择初始化的组件（初学勾选 Web 即可）

5、填写项目路径

6、等待项目构建成功

**项目结构分析：**

通过上面步骤完成了基础项目的创建。就会自动生成以下文件。

1、程序的主启动类

2、一个 application.properties 配置文件

3、一个 测试类

4、一个 pom.xml

### 2.2、pom.xml分析

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.4.4</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.lei</groupId>
    <artifactId>springboot-02-config</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>springboot-02-config</name>
    <description>Demo project for Spring Boot</description>
    <properties>
        <java.version>1.8</java.version>
    </properties>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```

### 2.3、编写一个http接口

1、在主程序的同级目录下，新建一个controller包，一定要在同级目录下，否则识别不到

2、在包中新建一个HelloController类

```java
@RestControllerpublic class HelloController {
    @RequestMapping("/hello")    
    public String hello() {        
        return "Hello World";    
    }    
}
```

3、编写完毕后，从主程序启动项目，浏览器发起请求，看页面返回；控制台输出了 Tomcat 访问的端口号！

## 3、运行原理初探

### 3.1、pom.xml

#### 1、父依赖

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.4.4</version>
    <relativePath/> <!-- lookup parent from repository -->
</parent>
```

**父依赖的父依赖**

```
<parent>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-dependencies</artifactId>
  <version>2.4.4</version>
</parent>
```

这里才是真正管理SpringBoot应用里面所有依赖版本的地方，SpringBoot的版本控制中心；

![image-20210407223953780](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210407223953780.png)

**以后我们导入依赖默认是不需要写版本；但是如果导入的包没有在依赖中管理着就需要手动配置版本了；**

#### 2、启动器spring-boot-starter

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

**springboot-boot-starter-xxx**：就是spring-boot的场景启动器

**spring-boot-starter-web**：帮我们导入了web模块正常运行所依赖的组件；

SpringBoot将所有的功能场景都抽取出来，做成一个个的starter （启动器），只需要在项目中引入这些starter即可，所有相关的依赖都会导入进来 ， 我们要用什么功能就导入什么样的场景启动器即可 ；我们未来也可以自己自定义 starter；

### 3.2、主启动类

#### 默认的主启动类

```java
@SpringBootApplication
public class Springboot02ConfigApplication {

    public static void main(String[] args) {
        SpringApplication.run(Springboot02ConfigApplication.class, args);
    }

}
```

#### @SpringBootApplication

作用：标注在某个类上说明这个类是SpringBoot的主配置类 ， SpringBoot就应该运行这个类的main方法来启动SpringBoot应用；

进入这个注解：可以看到上面还有很多其他注解！

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan(excludeFilters = { @Filter(type = FilterType.CUSTOM, classes = TypeExcludeFilter.class),
      @Filter(type = FilterType.CUSTOM, classes = AutoConfigurationExcludeFilter.class) })
public @interface SpringBootApplication {

   /**
```

#### @ComponentScan

这个注解在Spring中很重要 ,它对应XML配置中的元素。

作用：自动扫描并加载符合条件的组件或者bean ， 将这个bean定义加载到IOC容器中

#### @SpringBootConfiguration

作用：SpringBoot的配置类 ，标注在某个类上 ， 表示这是一个SpringBoot的配置类；

我们继续进去这个注解查看

```java
// 点进去得到下面的 @Component
@Configuration
public @interface SpringBootConfiguration {}

@Component
public @interface Configuration {}
```

这里的 @Configuration，说明这是一个配置类 ，配置类就是对应Spring的xml 配置文件；

里面的 @Component 这就说明，启动类本身也是Spring中的一个组件而已，负责启动应用！

我们回到 SpringBootApplication 注解中继续看。

#### @EnableAutoConfiguration

**@EnableAutoConfiguration ：开启自动配置功能**

以前我们需要自己配置的东西，而现在SpringBoot可以自动帮我们配置 ；@EnableAutoConfiguration告诉SpringBoot开启自动配置功能，这样自动配置才能生效；

点进注解接续查看：

```java
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
@AutoConfigurationPackage
@Import(AutoConfigurationImportSelector.class)
public @interface EnableAutoConfiguration {

   /**
```

**@AutoConfigurationPackage ：自动配置包**

**@import** ：Spring底层注解@import ， 给容器中导入一个组件

Registrar.class 作用：将主启动类的所在包及包下面所有子包里面的所有组件扫描到Spring容器 ；

这个分析完了，退到上一步，继续看

**@Import({AutoConfigurationImportSelector.class}) ：给容器导入组件 ；**

AutoConfigurationImportSelector ：自动配置导入选择器，那么它会导入哪些组件的选择器呢？我们点击去这个类看源码：

1、这个类中有一个这样的方法

```java
protected List<String> getCandidateConfigurations(AnnotationMetadata metadata, AnnotationAttributes attributes) {
    //这里的getSpringFactoriesLoaderFactoryClass（）方法
    //返回的就是我们最开始看的启动自动导入配置文件的注解类；EnableAutoConfiguration
    List<String> configurations = SpringFactoriesLoader.loadFactoryNames(getSpringFactoriesLoaderFactoryClass(),getBeanClassLoader());
    Assert.notEmpty(configurations, "No auto configuration classes found in META-INF/spring.factories. If you "
                    + "are using a custom packaging, make sure that file is correct.");
    return configurations;
}

protected Class<?> getSpringFactoriesLoaderFactoryClass() {
    return EnableAutoConfiguration.class;
}
```

2、这个方法又调用了  SpringFactoriesLoader 类的静态方法！我们进入SpringFactoriesLoader类loadFactoryNames() 方法

```java
public static List<String> loadFactoryNames(Class<?> factoryType, @Nullable ClassLoader classLoader) {
   ClassLoader classLoaderToUse = classLoader;
   if (classLoaderToUse == null) {
      classLoaderToUse = SpringFactoriesLoader.class.getClassLoader();
   }
   String factoryTypeName = factoryType.getName();
    //这里它又调用了 loadSpringFactories 方法
   return loadSpringFactories(classLoaderToUse).getOrDefault(factoryTypeName, Collections.emptyList());
}
```

3、我们继续点击查看 loadSpringFactories 方法

```java
private static Map<String, List<String>> loadSpringFactories(ClassLoader classLoader) {
    //获得classLoader ， 我们返回可以看到这里得到的就是EnableAutoConfiguration标注的类本身
   Map<String, List<String>> result = cache.get(classLoader);
   if (result != null) {
      return result;
   }

   result = new HashMap<>();
   try {
       //去获取一个资源 "META-INF/spring.factories"
      Enumeration<URL> urls = classLoader.getResources(FACTORIES_RESOURCE_LOCATION);
       //将读取到的资源遍历，封装成为一个Properties
      while (urls.hasMoreElements()) {
         URL url = urls.nextElement();
         UrlResource resource = new UrlResource(url);
         Properties properties = PropertiesLoaderUtils.loadProperties(resource);
         for (Map.Entry<?, ?> entry : properties.entrySet()) {
            String factoryTypeName = ((String) entry.getKey()).trim();
            String[] factoryImplementationNames =
                  StringUtils.commaDelimitedListToStringArray((String) entry.getValue());
            for (String factoryImplementationName : factoryImplementationNames) {
               result.computeIfAbsent(factoryTypeName, key -> new ArrayList<>())
                     .add(factoryImplementationName.trim());
            }
         }
      }

      // Replace all lists with unmodifiable lists containing unique elements
      result.replaceAll((factoryType, implementations) -> implementations.stream().distinct()
            .collect(Collectors.collectingAndThen(Collectors.toList(), Collections::unmodifiableList)));
      cache.put(classLoader, result);
   }
   catch (IOException ex) {
      throw new IllegalArgumentException("Unable to load factories from location [" +
            FACTORIES_RESOURCE_LOCATION + "]", ex);
   }
   return result;
}
```

4、发现一个多次出现的文件：spring.factories，全局搜索它

#### spring.factories

我们根据源头打开spring.factories ， 看到了很多自动配置的文件；这就是自动配置根源所在！

![image-20210407225912361](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210407225912361.png)

**WebMvcAutoConfiguration**

我们在上面的自动配置类随便找一个打开看看，比如 ：WebMvcAutoConfiguration

![image-20210407230009111](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210407230009111.png)

可以看到这些一个个的都是JavaConfig配置类，而且都注入了一些Bean，可以找一些自己认识的类，看着熟悉一下！

所以，自动配置真正实现是从classpath中搜寻所有的META-INF/spring.factories配置文件 ，并将其中对应的 org.springframework.boot.autoconfigure. 包下的配置项，通过反射实例化为对应标注了 @Configuration的JavaConfig形式的IOC容器配置类 ， 然后将这些都汇总成为一个实例并加载到IOC容器中。

**结论：**

1. SpringBoot在启动的时候从类路径下的META-INF/spring.factories中获取EnableAutoConfiguration指定的值
2. 将这些值作为自动配置类导入容器 ， 自动配置类就生效 ， 帮我们进行自动配置工作；
3. 整个J2EE的整体解决方案和自动配置都在springboot-autoconfigure的jar包中；
4. 它会给容器中导入非常多的自动配置类 （xxxAutoConfiguration）, 就是给容器中导入这个场景需要的所有组件 ， 并配置好这些组件 ；
5. 有了自动配置类 ， 免去了我们手动编写配置注入功能组件等的工作；



## 4、yaml配置注入

### 4.1、yaml语法

**配置文件**

SpringBoot使用一个全局的配置文件 ， 配置文件名称是固定的

- application.properties

- - 语法结构 ：key=value

- application.yml

- - 语法结构 ：key：空格 value

**配置文件的作用 ：**修改SpringBoot自动配置的默认值，因为SpringBoot在底层都给我们自动配置好了；

比如我们可以在配置文件中修改Tomcat 默认启动的端口号！测试一下！

```xml
server.port=8081
```

**yaml概述**

YAML是 "YAML Ain't a Markup Language" （YAML不是一种标记语言）的递归缩写。在开发的这种语言时，YAML 的意思其实是："Yet Another Markup Language"（仍是一种标记语言）

**这种语言以数据作为中心，而不是以标记语言为重点！**

以前的配置文件，大多数都是使用xml来配置；比如一个简单的端口配置，我们来对比下yaml和xml

传统xml配置：

```xml
<server>    
	<port>8081<port>
</server>
```

yaml配置：

```yaml
server:
  port: 8081
```

**yaml基础语法**

说明：语法要求严格！

1、空格不能省略

2、以缩进来控制层级关系，只要是左边对齐的一列数据都是同一个层级的。

3、属性和值的大小写都是十分敏感的。



**字面量：普通的值  [ 数字，布尔值，字符串  ]**

字面量直接写在后面就可以 ， 字符串默认不用加上双引号或者单引号；

```yaml
k: v
```

注意：

- “ ” 双引号，不会转义字符串里面的特殊字符 ， 特殊字符会作为本身想表示的意思；

  比如 ：name: "kuang \n shen"  输出 ：kuang  换行  shen

- '' 单引号，会转义特殊字符 ， 特殊字符最终会变成和普通字符一样输出

  比如 ：name: ‘kuang \n shen’  输出 ：kuang  \n  shen

**对象、Map（键值对）**

```yaml
k:
 v1:
 v2:
```

在下一行来写对象的属性和值得关系，注意缩进；比如：

```yaml
student:
 name: leige
 age: 11
```

行内写法

```yaml
student: {name: leige,age: 11}
```

**数组（ List、set ）**

用 - 值表示数组中的一个元素,比如：

```yaml
pets:
 - cat
 - dog
 - pig
```

行内写法

```yaml
pets: [cat,dog,pig]
```

### 4.2、注入配置文件

yaml文件更强大的地方在于，它可以给我们的实体类直接注入匹配值

#### **yaml注入配置文件**

1、在springboot项目中的resources目录下新建一个文件 application.yaml

2、编写一个实体类 Dog；

```java
package com.lei.pojo;

import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

/**
 * @author zhulei
 * @create 2021-04-08 21:55
 */
@Component  //注册bean到容器中
public class Dog {

    private String name;
    private Integer age;

    //有参无参构造、get、set方法、toString()方法  
}
```

3、编写一个复杂一点的实体类：Person 类

```java
@Component
public class Person {

    private String name;
    private Integer age;
    private Boolean happy;
    private Date birthday;
    private Map<String,Object> maps;
    private List<Object> list;
    private Dog dog;

    
}
```

4、我们来使用yaml配置的方式进行注入，大家写的时候注意区别和优势，我们编写一个yaml配置！

```yaml
person:
  name: leige${random.int}
  age: 3
  happy: false
  birthday: 2019/1/1
  maps: {ke: v1,k2: v2}
  list:
    - code
    - music
    - girl
  dog:
    name: wangcai
    age: 3
```

5、我们刚才已经把person这个对象的所有值都写好了，我们现在来注入到我们的类中！

```java
@Component
@ConfigurationProperties(prefix = "person")
public class Person {

    @Email
    private String name;
    private Integer age;
    private Boolean happy;
    private Date birthday;
    private Map<String,Object> maps;
    private List<Object> list;
    private Dog dog;
```

6、IDEA 提示，springboot配置注解处理器没有找到，让我们看文档，我们可以查看文档，找到一个依赖！

```xml
<!-- 导入配置文件处理器，配置文件进行绑定就会有提示，需要重启 -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-configuration-processor</artifactId>
    <optional>true</optional>
</dependency>
```

7、确认以上配置都OK之后，我们去测试类中测试一下：

```java
@SpringBootTest
class Springboot02ConfigApplicationTests {

    @Autowired
    private Person person;

    @Test
    void contextLoads() {

        System.out.println(person);

    }

}
```

```java
Person{name='leige464418008', age=3, happy=false, birthday=Tue Jan 01 00:00:00 CST 2019, maps={ke=v1, k2=v2}, list=[code, music, girl], dog=Dog{name='wangcai', age='3'}}
```

#### **加载指定的配置文件**

**@PropertySource ：**加载指定的配置文件；

**@configurationProperties**：默认从全局配置文件中获取值；

1、我们去在resources目录下新建一个**person.properties**文件

2、然后在我们的代码中指定加载person.properties文件

```java
@Component
@PropertySource(value = "classpath:application.properties")
public class Person {

    private String name;
    private Integer age;
    private Boolean happy;
    private Date birthday;
    private Map<String,Object> maps;
    private List<Object> list;
    private Dog dog;
```

3、再次输出测试一下：指定配置文件绑定成功！

#### **配置文件占位符**

配置文件还可以编写占位符生成随机数

```yaml
person:
  name: leige${random.int} # 随机int
  age: 3
  happy: false
  birthday: 2019/1/1
  maps: {ke: v1,k2: v2}
  list:
    - code
    - music
    - girl
  dog:
    name: wangcai
    age: 3
```

#### 回顾properties配置

我们上面采用的yaml方法都是最简单的方式，开发中最常用的；也是springboot所推荐的！那我们来唠唠其他的实现方式，道理都是相同的；写还是那样写；配置文件除了yml还有我们之前常用的properties ，

【注意】properties配置文件在写中文的时候，会有乱码 ， 我们需要去IDEA中设置编码格式为UTF-8；

settings-->FileEncodings 中配置；

![image-20210409201840433](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210409201840433.png)



**对比**

@Value这个使用起来并不友好！我们需要为每个属性单独注解赋值，比较麻烦；

|                | @ConfigurationProperties   | @Value     |
| -------------- | -------------------------- | ---------- |
| 功能           | 批量注入配置文件中的属性值 | 一个个指定 |
| 松散绑定       | 支持                       | 不支持     |
| Spel           | 不支持                     | 支持       |
| JSR303数据校验 | 支持                       | 不支持     |
| 复杂类型封装   | 支持                       | 不支持     |

1、@ConfigurationProperties只需要写一次即可 ， @Value则需要每个字段都添加

2、松散绑定：这个什么意思呢? 比如我的yml中写的last-name，这个和lastName是一样的， - 后面跟着的字母默认是大写的。这就是松散绑定。可以测试一下

3、JSR303数据校验 ， 这个就是我们可以在字段是增加一层过滤器验证 ， 可以保证数据的合法性

4、复杂类型封装，yml中可以封装对象 ， 使用value就不支持

**结论：**

配置yml和配置properties都可以获取到值 ， 强烈推荐 yml；

如果我们在某个业务中，只需要获取配置文件中的某个值，可以使用一下 @value；

如果说，我们专门编写了一个JavaBean来和配置文件进行一一映射，就直接@configurationProperties，



## 5、JSR303数据校验

### 5.1、使用

Springboot中可以用@validated来校验数据，如果数据异常则会统一抛出异常，方便异常中心统一处理。我们这里来写个注解让我们的name只能支持Email格式；

```java
@Component
@ConfigurationProperties(prefix = "person")
@Validated
public class Person {

    @Email
    private String name;
```

![image-20210409202426509](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210409202426509.png)

**使用数据校验，可以保证数据的正确性；** 



**注意：**

springboot 2.3.0以上需要注入依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
<dependency>
    <groupId>org.hibernate.validator</groupId>
    <artifactId>hibernate-validator</artifactId>
    <version>6.0.17.Final</version>
    <scope>compile</scope>
</dependency>
```

### 5.2、常见参数

```java
@NotNull(message="名字不能为空")
private String userName;
@Max(value=120,message="年龄最大不能查过120")
private int age;
@Email(message="邮箱格式错误")
private String email;

空检查
@Null       验证对象是否为null
@NotNull    验证对象是否不为null, 无法查检长度为0的字符串
@NotBlank   检查约束字符串是不是Null还有被Trim的长度是否大于0,只对字符串,且会去掉前后空格.
@NotEmpty   检查约束元素是否为NULL或者是EMPTY.
    
Booelan检查
@AssertTrue     验证 Boolean 对象是否为 true  
@AssertFalse    验证 Boolean 对象是否为 false  
    
长度检查
@Size(min=, max=) 验证对象（Array,Collection,Map,String）长度是否在给定的范围之内  
@Length(min=, max=) string is between min and max included.

日期检查
@Past       验证 Date 和 Calendar 对象是否在当前时间之前  
@Future     验证 Date 和 Calendar 对象是否在当前时间之后  
@Pattern    验证 String 对象是否符合正则表达式的规则

.......等等
除此以外，我们还可以自定义一些数据校验规则
```



## 6、多环境切换

profile是Spring对不同环境提供不同配置功能的支持，可以通过激活不同的环境版本，实现快速切换环境；

### 6.1、多配置文件

我们在主配置文件编写的时候，文件名可以是 application-{profile}.properties/yml , 用来指定多个环境版本；

application-test.properties 代表测试环境配置

application-dev.properties 代表开发环境配置

但是Springboot并不会直接启动这些配置文件，它**默认使用application.properties主配置文件**；

我们需要通过一个配置来选择需要激活的环境：

```properties
#比如在配置文件中指定使用dev环境，我们可以通过设置不同的端口号进行测试；
#我们启动SpringBoot，就可以看到已经切换到dev下的配置了；
spring.profiles.active=dev
```

### 6.2、yaml的多文档块

和properties配置文件中一样，但是使用yml去实现不需要创建多个配置文件，更加方便了 !

```yaml
server:
  port: 8081
#选择要激活那个环境块
spring:
  profiles:
    active: prod

---
server:
  port: 8083
spring:
  profiles: dev #配置环境的名称


---

server:
  port: 8084
spring:
  profiles: prod  #配置环境的名称
```

**注意：如果yml和properties同时都配置了端口，并且没有激活其他环境 ， 默认会使用properties配置文件的！**

### 6.3、配置文件加载位置

**外部加载配置文件的方式十分多，我们选择最常用的即可，在开发的资源文件中进行配置！**

![image-20210409220951467](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210409220951467.png)

springboot 启动会扫描以下位置的application.properties或者application.yml文件作为Spring boot的默认配置文件：

```java
优先级1：项目路径下的config文件夹配置文件
优先级2：项目路径下配置文件
优先级3：资源路径下的config文件夹配置文件
优先级4：资源路径下配置文件
```

优先级由高到底，高优先级的配置会覆盖低优先级的配置；

**SpringBoot会从这四个位置全部加载主配置文件；互补配置；**

指定位置加载配置文件

我们还可以通过spring.config.location来改变默认的配置文件位置

项目打包好以后，我们可以使用命令行参数的形式，启动项目的时候来指定配置文件的新位置；这种情况，一般是后期运维做的多，相同配置，外部指定的配置文件优先级最高

#### 在打包完成的情况下，需要新增一些配置，这时该怎么做呢？ 可以通过配置spring.config.location来改变默认配置。

- G盘符下创建文件application.properties

  ```properties
  G:\application.properties
  
  server.port=9999
  server.servlet.context-path=/boot02
  ```

- 在idea中terminal执行语句：

  ```java
  java -jar spring-boot-02-config-0.0.1-SNAPSHOT.jar --spring.config.location=G:\application.properties
  ```

- controller代码

  ```
  package com.lei.controller;
  
  import org.springframework.web.bind.annotation.RequestMapping;
  import org.springframework.web.bind.annotation.RestController;
  
  @RestController
  public class HelloController {
  
      @RequestMapping("/hello")
      public String hello() {
          return "hello....";
      }
  }
  ```

- 访问出结果

  ![image-20210409221904739](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210409221904739.png)

## 7、自动配置原理

### 7.1、分析自动配置原理

我们以**HttpEncodingAutoConfiguration（Http编码自动配置）**为例解释自动配置原理；

```java
//表示这是一个配置类，和以前编写的配置文件一样，也可以给容器中添加组件；
@Configuration(proxyBeanMethods = false)
//启动指定类的ConfigurationProperties功能；
  //进入这个ServerProperties查看，将配置文件中对应的值和ServerProperties绑定起来；
  //并把ServerProperties加入到ioc容器中
@EnableConfigurationProperties(ServerProperties.class)
//Spring底层@Conditional注解
  //根据不同的条件判断，如果满足指定的条件，整个配置类里面的配置就会生效；
  //这里的意思就是判断当前应用是否是web应用，如果是，当前配置类生效
@ConditionalOnWebApplication(type = ConditionalOnWebApplication.Type.SERVLET)
//判断当前项目有没有这个类CharacterEncodingFilter；SpringMVC中进行乱码解决的过滤器；
@ConditionalOnClass(CharacterEncodingFilter.class)
//判断配置文件中是否存在某个配置：server.servlet.encoding.enabled；
  //如果不存在，判断也是成立的
  //即使我们配置文件中不配置pring.http.encoding.enabled=true，也是默认生效的；
@ConditionalOnProperty(prefix = "server.servlet.encoding", value = "enabled", matchIfMissing = true)
public class HttpEncodingAutoConfiguration {

    //他已经和SpringBoot的配置文件映射了
   private final Encoding properties;
	//只有一个有参构造器的情况下，参数的值就会从容器中拿
   public HttpEncodingAutoConfiguration(ServerProperties properties) {
      this.properties = properties.getServlet().getEncoding();
   }
	
    //给容器中添加一个组件，这个组件的某些值需要从properties中获取
   @Bean
   @ConditionalOnMissingBean//判断容器没有这个组件？
   public CharacterEncodingFilter characterEncodingFilter() {
      CharacterEncodingFilter filter = new OrderedCharacterEncodingFilter();
      filter.setEncoding(this.properties.getCharset().name());
      filter.setForceRequestEncoding(this.properties.shouldForce(Encoding.Type.REQUEST));
      filter.setForceResponseEncoding(this.properties.shouldForce(Encoding.Type.RESPONSE));
      return filter;
   }

   @Bean
   public LocaleCharsetMappingsCustomizer localeCharsetMappingsCustomizer() {
      return new LocaleCharsetMappingsCustomizer(this.properties);
   }

   //...

}
```

**一句话总结 ：根据当前不同的条件判断，决定这个配置类是否生效！**

- 一但这个配置类生效；这个配置类就会给容器中添加各种组件；
- 这些组件的属性是从对应的properties类中获取的，这些类里面的每一个属性又是和配置文件绑定的；
- 所有在配置文件中能配置的属性都是在xxxxProperties类中封装着；
- 配置文件能配置什么就可以参照某个功能对应的这个属性类

```java
@ConfigurationProperties(prefix = "server", ignoreUnknownFields = true)
public class ServerProperties {
```

我们去配置文件里面试试前缀，看提示！

![image-20210409222753420](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210409222753420.png)

### 7.2、精髓

SpringBoot启动会加载大量的自动配置类

2、我们看我们需要的功能有没有在SpringBoot默认写好的自动配置类当中；

3、我们再来看这个自动配置类中到底配置了哪些组件；（只要我们要用的组件存在在其中，我们就不需要再手动配置了）

4、给容器中自动配置类添加组件的时候，会从properties类中获取某些属性。我们只需要在配置文件中指定这些属性的值即可；

**xxxxAutoConfigurartion：自动配置类；**给容器中添加组件

**xxxxProperties:封装配置文件中相关属性；**



### 7.3、了解：@Conditional

了解完自动装配的原理后，我们来关注一个细节问题，**自动配置类必须在一定的条件下才能生效；**

**@Conditional派生注解（Spring注解版原生的@Conditional作用）**

作用：必须是@Conditional指定的条件成立，才给容器中添加组件，配置配里面的所有内容才生效；

| @Conditional扩展注解            | 作用（判断是否满足当前指定条件）                 |
| ------------------------------- | ------------------------------------------------ |
| @ConditionalOnJava              | 系统的java版本是否符合要求                       |
| @ConditionalOnBean              | 系统中是否存在指定bean                           |
| @ConditionalOnMissingBean       | 系统中是否不存在指定bean                         |
| @ConditionalOnExpression        | 满足SpEL表达式指定                               |
| @ConditionalOnClass             | 系统中有指定的类                                 |
| @ConditionalOnMissingClass      | 系统中没有指定的类                               |
| @ConditionalOnSingleCandidate   | 容器中只有一个指定的bean，或者这个bean是首选bean |
| @ConditionalOnProperty          | 系统中指定的属性是否有指定的值                   |
| @ConditionalOnResourse          | 类路径下是否存在指定资源文件                     |
| @ConditionalOnWebApplication    | 当时是web环境                                    |
| @ConditionalOnNotWebApplication | 当前不是web环境                                  |
| @ConditionalOnJndi              | JNDI存在指定项                                   |

**那么多的自动配置类，必须在一定的条件下才能生效；也就是说，我们加载了这么多的配置类，但不是所有的都生效了。**

我们怎么知道哪些自动配置类生效？

**我们可以通过启用 debug=true属性；来让控制台打印自动配置报告，这样我们就可以很方便的知道哪些自动配置类生效；**

```yaml
debug: true
```

**Positive matches:（自动配置类启用的：正匹配）**

**Negative matches:（没有启动，没有匹配成功的自动配置类：负匹配）**

**Unconditional classes: （没有条件的类）**

## 8、Web开发静态资源处理

### 8.1、静态资源处理

#### 1、静态资源映射规则

SpringBoot对于静态资源放置的位置，是有规定的

SpringBoot中，SpringMVC的web配置都在 WebMvcAutoConfiguration 这个配置类里面；

有一个方法：addResourceHandlers 添加资源处理

```java
@Override
protected void addResourceHandlers(ResourceHandlerRegistry registry) {
   super.addResourceHandlers(registry);
   if (!this.resourceProperties.isAddMappings()) {
      logger.debug("Default resource handling disabled");
      return;
   }
   ServletContext servletContext = getServletContext();
   addResourceHandler(registry, "/webjars/**", "classpath:/META-INF/resources/webjars/");
   addResourceHandler(registry, this.mvcProperties.getStaticPathPattern(), (registration) -> {
      registration.addResourceLocations(this.resourceProperties.getStaticLocations());
      if (servletContext != null) {
         registration.addResourceLocations(new ServletContextResource(servletContext, SERVLET_LOCATION));
      }
   });
}
```

读一下源代码：比如所有的 **/webjars/**** ， 都需要去 **classpath:/META-INF/resources/webjars/** 找对应的资源；

#### 2、什么是webjars

Webjars本质就是以jar包的方式引入我们的静态资源 ， 我们以前要导入一个静态资源文件，直接导入即可。

使用SpringBoot需要使用Webjars，我们可以去搜索一下：

网站：https://www.webjars.org 

要使用jQuery，我们只要要引入jQuery对应版本的pom依赖即可！

```xml
<dependency>
    <groupId>org.webjars</groupId>
    <artifactId>jquery</artifactId>
    <version>3.6.0</version>
</dependency>
```

导入完毕，查看webjars目录结构，并访问Jquery.js文件！

![image-20210411220224044](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210411220224044.png)

访问：只要是静态资源，SpringBoot就会去对应的路径寻找资源，我们这里访问：http://localhost:8080/webjars/jquery/3.6.0/jquery.js

![image-20210411220331106](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210411220331106.png)

#### 3、第二种静态资源映射规则

项目中要是使用自己的静态资源该怎么导入

我们去找getStaticPathPattern发现第二种映射规则 ：/** , 访问当前的项目任意资源，它会去找 Resource 这个类，我们可以点进去看一下分析：

```java
private static final String[] CLASSPATH_RESOURCE_LOCATIONS = { "classpath:/META-INF/resources/",
      "classpath:/resources/", "classpath:/static/", "classpath:/public/" };

/**
 * Locations of static resources. Defaults to classpath:[/META-INF/resources/,
 * /resources/, /static/, /public/].
 */
private String[] staticLocations = CLASSPATH_RESOURCE_LOCATIONS;
```

Resource 可以设置和我们静态资源有关的参数；这里面指向了它会去寻找资源的文件夹，即上面数组的内容。

所以得出结论，以下四个目录存放的静态资源可以被我们识别：

```java
"classpath:/META-INF/resources/"
"classpath:/resources/",
"classpath:/static/",
"classpath:/public/"
```

我们可以在resources根目录下新建对应的文件夹，都可以存放我们的静态文件；

比如我们访问 http://localhost:8080/1.js , 他就会去这些文件夹中寻找对应的静态资源文件；

#### 4、自定义静态资源路径

我们也可以自己通过配置文件来指定一下，哪些文件夹是需要我们放静态资源文件的，在application.properties中配置；

```properties
spring.resources.static-locations=classpath:/coding/,classpath:/lei/
```

一旦自己定义了静态文件夹的路径，原来的自动配置就都会失效了！

### 8.2、首页处理

继续向下看源码，可以看到一个欢迎页的映射，就是首页

```java
@Bean
public WelcomePageHandlerMapping welcomePageHandlerMapping(ApplicationContext applicationContext,
      FormattingConversionService mvcConversionService, ResourceUrlProvider mvcResourceUrlProvider) {
   WelcomePageHandlerMapping welcomePageHandlerMapping = new WelcomePageHandlerMapping(
         new TemplateAvailabilityProviders(applicationContext), applicationContext, getWelcomePage(),
         this.mvcProperties.getStaticPathPattern());// getWelcomePage 获得欢迎页
   welcomePageHandlerMapping.setInterceptors(getInterceptors(mvcConversionService, mvcResourceUrlProvider));
   welcomePageHandlerMapping.setCorsConfigurations(getCorsConfigurations());
   return welcomePageHandlerMapping;
}
```

点进去继续看

```java
private Resource getWelcomePage() {
   for (String location : this.resourceProperties.getStaticLocations()) {
      Resource indexHtml = getIndexHtml(location);
      if (indexHtml != null) {
         return indexHtml;
      }
   }
   ServletContext servletContext = getServletContext();
   if (servletContext != null) {
      return getIndexHtml(new ServletContextResource(servletContext, SERVLET_LOCATION));
   }
   return null;
}
```

欢迎页，静态资源文件夹下的所有 index.html 页面；被 /** 映射。

比如访问  http://localhost:8080/ ，就会找静态资源文件夹下的 index.html

新建一个 index.html ，在上面的3个目录中任意一个；然后访问测试  http://localhost:8080/  看结果

## 9、Thymeleaf

### 9.1、模板引擎

前端交给我们的页面，是html页面。如果是我们以前开发，我们需要把他们转成jsp页面，jsp好处就是当我们查出一些数据转发到JSP页面以后，我们可以用jsp轻松实现数据的显示，及交互等。

jsp支持非常强大的功能，包括能写Java代码，但是呢，我们现在的这种情况，SpringBoot这个项目首先是以jar的方式，不是war，像第二，我们用的还是嵌入式的Tomcat，所以呢，**他现在默认是不支持jsp的**。

那不支持jsp，如果我们直接用纯静态页面的方式，那给我们开发会带来非常大的麻烦，那怎么办呢？

**SpringBoot推荐你可以来使用模板引擎：**

模板引擎，我们其实大家听到很多，其实jsp就是一个模板引擎，还有用的比较多的freemarker，包括SpringBoot给我们推荐的Thymeleaf，模板引擎有非常多，但再多的模板引擎，他们的思想都是一样的，什么样一个思想呢我们来看一下这张图：

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7Idia351qHgmH2vbzurk1Pp6V42bcomyzTYY0q6ic7AB8lvciaoicxyalNYQYZgslIrIjdXWLFNcOxUmQ/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

模板引擎的作用就是我们来写一个页面模板，比如有些值呢，是动态的，我们写一些表达式。而这些值，从哪来呢，就是我们在后台封装一些数据。然后把这个模板和这个数据交给我们模板引擎，模板引擎按照我们这个数据帮你把这表达式解析、填充到我们指定的位置，然后把这个数据最终生成一个我们想要的内容给我们写出去，这就是我们这个模板引擎，不管是jsp还是其他模板引擎，都是这个思想。只不过呢，就是说不同模板引擎之间，他们可能这个语法有点不一样。其他的我就不介绍了，我主要来介绍一下SpringBoot给我们推荐的Thymeleaf模板引擎，这模板引擎呢，是一个高级语言的模板引擎，他的这个语法更简单。而且呢，功能更强大。

### 9.2、引入Thymeleaf

Thymeleaf 官网：https://www.thymeleaf.org/

Thymeleaf 在Github 的主页：https://github.com/thymeleaf/thymeleaf

Spring官方文档：找到我们对应的版本

https://docs.spring.io/spring-boot/docs/2.2.5.RELEASE/reference/htmlsingle/#using-boot-starter 

找到对应的pom依赖：可以适当点进源码看下本来的包！

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

![image-20210411221938558](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210411221938558.png)

### 9.3、Thymeleaf分析

我们首先得按照SpringBoot的自动配置原理看一下我们这个Thymeleaf的自动配置规则，在按照那个规则，我们进行使用。

找一下Thymeleaf的自动配置类：ThymeleafProperties

```java
@ConfigurationProperties(prefix = "spring.thymeleaf")
public class ThymeleafProperties {

   private static final Charset DEFAULT_ENCODING = StandardCharsets.UTF_8;

   public static final String DEFAULT_PREFIX = "classpath:/templates/";

   public static final String DEFAULT_SUFFIX = ".html";
```

我们可以在其中看到默认的前缀和后缀！

我们只需要把我们的html页面放在类路径下的templates下，thymeleaf就可以帮我们自动渲染了。

使用thymeleaf什么都不需要配置，只需要将他放在指定的文件夹下即可！

**测试**

1、编写一个TestController

```java
@Controller
public class IndexController {
    @RequestMapping("/test")
    public String index(Model model) {
        model.addAttribute("msg","hello SpringBoot");
        return "test";
    }
}
```

2、编写一个测试页面  test.html 放在 templates 目录下

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>测试页面</h1>
</body>
</html>
```

3、启动项目请求测试

### 9.4、Thymeleaf语法

**入门**

1、修改测试请求，增加数据传输；

```java
@Controller
public class IndexController {

    @RequestMapping("/test")
    public String index(Model model) {
        model.addAttribute("msg","hello SpringBoot");
        return "test";
    }
}
```

2、我们要使用thymeleaf，需要在html文件中导入命名空间的约束，方便提示。

我们可以去官方文档的#3中看一下命名空间拿来过来：

```html
xmlns:th="http://www.thymeleaf.org"
```

3、我们去编写下前端页面

```html
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<div th:text="${msg}"></div>
</body>
</html>
```

4、启动测试！

![image-20210411222526384](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210411222526384.png)

**正式开始**

1、

## 10、MVC自动配置原理

https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-spring-mvc-auto-configuration

![image-20210413224810149](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413224810149.png)

```
Spring MVC Auto-configuration
// Spring Boot为Spring MVC提供了自动配置，它可以很好地与大多数应用程序一起工作。
Spring Boot provides auto-configuration for Spring MVC that works well with most applications.
// 自动配置在Spring默认设置的基础上添加了以下功能：The auto-configuration adds the following features on top of Spring’s defaults:
// 包含视图解析器
Inclusion of ContentNegotiatingViewResolver and BeanNameViewResolver beans.
// 支持静态资源文件夹的路径，以及webjars
Support for serving static resources, including support for WebJars 
// 自动注册了Converter：
// 转换器，这就是我们网页提交数据到后台自动封装成为对象的东西，比如把"1"字符串自动转换为int类型
// Formatter：【格式化器，比如页面给我们了一个2019-8-10，它会给我们自动格式化为Date对象】
Automatic registration of Converter, GenericConverter, and Formatter beans.
// HttpMessageConverters
// SpringMVC用来转换Http请求和响应的的，比如我们要把一个User对象转换为JSON字符串，可以去看官网文档解释；
Support for HttpMessageConverters (covered later in this document).
// 定义错误代码生成规则的Automatic registration of MessageCodesResolver (covered later in this document).
// 首页定制
Static index.html support.
// 图标定制
Custom Favicon support (covered later in this document).
// 初始化数据绑定器：帮我们把请求数据绑定到JavaBean中！Automatic use of a ConfigurableWebBindingInitializer bean (covered later in this document).

/*如果您希望保留Spring Boot MVC功能，并且希望添加其他MVC配置（拦截器、格式化程序、视图控制器和其他功能），则可以添加自己的@configuration类，类型为webmvcconfiguer，但不添加@EnableWebMvc。如果希望提供RequestMappingHandlerMapping、RequestMappingHandlerAdapter或ExceptionHandlerExceptionResolver的自定义实例，则可以声明WebMVCregistrationAdapter实例来提供此类组件。*/
If you want to keep Spring Boot MVC features and you want to add additional MVC configuration (interceptors, formatters, view controllers, and other features), you can add your own @Configuration class of type WebMvcConfigurer but without @EnableWebMvc. If you wish to provide custom instances of RequestMappingHandlerMapping, RequestMappingHandlerAdapter, or ExceptionHandlerExceptionResolver, you can declare a WebMvcRegistrationsAdapter instance to provide such components.

// 如果您想完全控制Spring MVC，可以添加自己的@Configuration，并用@EnableWebMvc进行注释。
If you want to take complete control of Spring MVC, you can add your own @Configu
```

### **ContentNegotiatingViewResolver 内容协商视图解析器** 

自动配置了ViewResolver，就是我们之前学习的SpringMVC的视图解析器；

即根据方法的返回值取得视图对象（View），然后由视图对象决定如何渲染（转发，重定向）。

我们去看看这里的源码：我们找到 WebMvcAutoConfiguration ， 然后搜索ContentNegotiatingViewResolver。找到如下方法！

```java
@Bean
@ConditionalOnBean(ViewResolver.class)
@ConditionalOnMissingBean(name = "viewResolver", value = ContentNegotiatingViewResolver.class)
public ContentNegotiatingViewResolver viewResolver(BeanFactory beanFactory) {
   ContentNegotiatingViewResolver resolver = new ContentNegotiatingViewResolver();
   resolver.setContentNegotiationManager(beanFactory.getBean(ContentNegotiationManager.class));
   // ContentNegotiatingViewResolver uses all the other view resolvers to locate
   // a view so it should have a high precedence
    // ContentNegotiatingViewResolver使用所有其他视图解析器来定位视图，因此它应该具有较高的优先级
   resolver.setOrder(Ordered.HIGHEST_PRECEDENCE);
   return resolver;
}
```

我们可以点进这类看看！找到对应的解析视图的代码；

```java
@Override
@Nullable
public View resolveViewName(String viewName, Locale locale) throws Exception {
   RequestAttributes attrs = RequestContextHolder.getRequestAttributes();
   Assert.state(attrs instanceof ServletRequestAttributes, "No current ServletRequestAttributes");
   List<MediaType> requestedMediaTypes = getMediaTypes(((ServletRequestAttributes) attrs).getRequest());
   if (requestedMediaTypes != null) {
       // 获取候选的视图对象
      List<View> candidateViews = getCandidateViews(viewName, locale, requestedMediaTypes);
       // 选择一个最适合的视图对象，然后把这个对象返回
      View bestView = getBestView(candidateViews, requestedMediaTypes, attrs);
      if (bestView != null) {
         return bestView;
      }
   }

   String mediaTypeInfo = logger.isDebugEnabled() && requestedMediaTypes != null ?
         " given " + requestedMediaTypes.toString() : "";

   if (this.useNotAcceptableStatusCode) {
      if (logger.isDebugEnabled()) {
         logger.debug("Using 406 NOT_ACCEPTABLE" + mediaTypeInfo);
      }
      return NOT_ACCEPTABLE_VIEW;
   }
   else {
      logger.debug("View remains unresolved" + mediaTypeInfo);
      return null;
   }
}
```

我们继续点进去看，他是怎么获得候选的视图的呢？

getCandidateViews中看到他是把所有的视图解析器拿来，进行for循环，挨个解析！

```java
private List<View> getCandidateViews(String viewName, Locale locale, List<MediaType> requestedMediaTypes)
      throws Exception {

   List<View> candidateViews = new ArrayList<>();
   if (this.viewResolvers != null) {
      Assert.state(this.contentNegotiationManager != null, "No ContentNegotiationManager set");
      for (ViewResolver viewResolver : this.viewResolvers) {
         View view = viewResolver.resolveViewName(viewName, locale);
         if (view != null) {
            candidateViews.add(view);
         }
         for (MediaType requestedMediaType : requestedMediaTypes) {
            List<String> extensions = this.contentNegotiationManager.resolveFileExtensions(requestedMediaType);
            for (String extension : extensions) {
               String viewNameWithExtension = viewName + '.' + extension;
               view = viewResolver.resolveViewName(viewNameWithExtension, locale);
               if (view != null) {
                  candidateViews.add(view);
               }
            }
         }
      }
   }
   if (!CollectionUtils.isEmpty(this.defaultViews)) {
      candidateViews.addAll(this.defaultViews);
   }
   return candidateViews;
}
```

所以得出结论：**ContentNegotiatingViewResolver 这个视图解析器就是用来组合所有的视图解析器的** 

我们再去研究下他的组合逻辑，看到有个属性viewResolvers，看看它是在哪里进行赋值的！

```java
@Override
protected void initServletContext(ServletContext servletContext) {
    // 这里它是从beanFactory工具中获取容器中的所有视图解析器
    // ViewRescolver.class 把所有的视图解析器来组合的
   Collection<ViewResolver> matchingBeans =
     BeanFactoryUtils.beansOfTypeIncludingAncestors(obtainApplicationContext(), ViewResolver.class).values();
   if (this.viewResolvers == null) {
      this.viewResolvers = new ArrayList<>(matchingBeans.size());
      for (ViewResolver viewResolver : matchingBeans) {
         if (this != viewResolver) {
            this.viewResolvers.add(viewResolver);
         }
      }
   }
   else {
      for (int i = 0; i < this.viewResolvers.size(); i++) {
         ViewResolver vr = this.viewResolvers.get(i);
         if (matchingBeans.contains(vr)) {
            continue;
         }
         String name = vr.getClass().getName() + i;
         obtainApplicationContext().getAutowireCapableBeanFactory().initializeBean(vr, name);
      }

   }
   AnnotationAwareOrderComparator.sort(this.viewResolvers);
   this.cnmFactoryBean.setServletContext(servletContext);
}
```

### 修改SpringBoot的默认配置

这么多的自动配置，原理都是一样的，通过这个WebMVC的自动配置原理分析，我们要学会一种学习方式，通过源码探究，得出结论；这个结论一定是属于自己的，而且一通百通。

SpringBoot的底层，大量用到了这些设计细节思想，所以，没事需要多阅读源码！得出结论；

SpringBoot在自动配置很多组件的时候，先看容器中有没有用户自己配置的（如果用户自己配置@bean），如果有就用用户配置的，如果没有就用自动配置的；

如果有些组件可以存在多个，比如我们的视图解析器，就将用户配置的和自己默认的组合起来！

**扩展使用SpringMVC**  官方文档如下：

If you want to keep Spring Boot MVC features and you want to add additional MVC configuration (interceptors, formatters, view controllers, and other features), you can add your own @Configuration class of type WebMvcConfigurer but without @EnableWebMvc. If you wish to provide custom instances of RequestMappingHandlerMapping, RequestMappingHandlerAdapter, or ExceptionHandlerExceptionResolver, you can declare a WebMvcRegistrationsAdapter instance to provide such components.

我们要做的就是编写一个@Configuration注解类，并且类型要为WebMvcConfigurer，还**不能标注@EnableWebMvc注解**；我们去自己写一个；我们新建一个包叫config，写一个类MyMvcConfig；

```
@Configuration
public class MyMvcConfig implements WebMvcConfigurer {

    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addViewController("/").setViewName("index");
        registry.addViewController("/index.html").setViewName("index");
        registry.addViewController("/main.html").setViewName("dashboard");
    }
}
```

**我们要扩展SpringMVC，官方就推荐我们这么去使用，既保SpringBoot留所有的自动配置，也能用我们扩展的配置！**

我们可以去分析一下原理：

1、WebMvcAutoConfiguration 是 SpringMVC的自动配置类，里面有一个类WebMvcAutoConfigurationAdapter

2、这个类上有一个注解，在做其他自动配置时会导入：@Import(EnableWebMvcConfiguration.class)

3、我们点进EnableWebMvcConfiguration这个类看一下，它继承了一个父类：DelegatingWebMvcConfiguration

这个父类中有这样一段代码：

```java
@Configuration(proxyBeanMethods = false)
public class DelegatingWebMvcConfiguration extends WebMvcConfigurationSupport {

   private final WebMvcConfigurerComposite configurers = new WebMvcConfigurerComposite();

	// 从容器中获取所有的webmvcConfigurer
   @Autowired(required = false)
   public void setConfigurers(List<WebMvcConfigurer> configurers) {
      if (!CollectionUtils.isEmpty(configurers)) {
         this.configurers.addWebMvcConfigurers(configurers);
      }
   }
    //...
}
```

4、我们可以在这个类中去寻找一个我们刚才设置的viewController当做参考，发现它调用了一个

```java
@Override
protected void addViewControllers(ViewControllerRegistry registry) {
   this.configurers.addViewControllers(registry);
}
```

5、我们点进去看一下

```java
@Override
public void addViewControllers(ViewControllerRegistry registry) {
   for (WebMvcConfigurer delegate : this.delegates) {
      delegate.addViewControllers(registry);
   }
}
```

所以得出结论：所有的WebMvcConfiguration都会被作用，不止Spring自己的配置类，我们自己的配置类当然也会被调用；

### 全面接管SpringMVC

全面接管即：SpringBoot对SpringMVC的自动配置不需要了，所有都是我们自己去配置！

只需在我们的配置类中要加一个@EnableWebMvc。

我们看下如果我们全面接管了SpringMVC了，我们之前SpringBoot给我们配置的静态资源映射一定会无效，我们可以去测试一下；

不加注解之前，访问首页：

![image-20210413232742973](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413232742973.png)

给配置类加上注解：@EnableWebMvc

![image-20210413232755787](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413232755787.png)

我们发现所有的SpringMVC自动配置都失效了！回归到了最初的样子；

**当然，我们开发中，不推荐使用全面接管SpringMVC**

思考问题？为什么加了一个注解，自动配置就失效了！我们看下源码：

1、这里发现它是导入了一个类，我们可以继续进去看

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.TYPE)
@Documented
@Import(DelegatingWebMvcConfiguration.class)
public @interface EnableWebMvc {
}
```

2、它继承了一个父类 WebMvcConfigurationSupport

```java
public class DelegatingWebMvcConfiguration extends WebMvcConfigurationSupport {
    //...
}
```

3、我们来回顾一下Webmvc自动配置类

```java
@Configuration(proxyBeanMethods = false)
@ConditionalOnWebApplication(type = Type.SERVLET)
@ConditionalOnClass({ Servlet.class, DispatcherServlet.class, WebMvcConfigurer.class })
@ConditionalOnMissingBean(WebMvcConfigurationSupport.class)
@AutoConfigureOrder(Ordered.HIGHEST_PRECEDENCE + 10)
@AutoConfigureAfter({ DispatcherServletAutoConfiguration.class, TaskExecutionAutoConfiguration.class,
      ValidationAutoConfiguration.class })
public class WebMvcAutoConfiguration {
//...
}
```

总结一句话：@EnableWebMvc将WebMvcConfigurationSupport组件导入进来了；

而导入的WebMvcConfigurationSupport只是SpringMVC最基本的功能！

## 11、页面国际化

### 11.1、准备工作

先在IDEA中统一设置properties的编码问题

![image-20210413233359995](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413233359995.png)

编写国际化配置文件，抽取页面需要显示的国际化页面消息。我们可以去登录页面查看一下，哪些内容我们需要编写国际化的配置！

### 11.2、配置文件编写

1、我们在resources资源文件下新建一个i18n目录，存放国际化配置文件

2、建立一个login.properties文件，还有一个login_zh_CN.properties；发现IDEA自动识别了我们要做国际化操作；文件夹变了！

![image-20210413233503708](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413233503708.png)

3、我们可以在这上面去新建一个文件；

![image-20210413233552417](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413233552417.png)

弹出如下页面：我们再添加一个英文的；

![image-20210413233558491](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413233558491.png)

这样就快捷多了！

4、**接下来，我们就来编写配置，我们可以看到idea下面有另外一个视图；**

![image-20210413233706111](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413233706111.png)

### 11.3、配置文件生效探究

我们去看一下SpringBoot对国际化的自动配置！这里又涉及到一个类：MessageSourceAutoConfiguration

里面有一个方法，这里发现SpringBoot已经自动配置好了管理我们国际化资源文件的组件 ResourceBundleMessageSource；

```java
@Bean
public MessageSource messageSource(MessageSourceProperties properties) {
   ResourceBundleMessageSource messageSource = new ResourceBundleMessageSource();
   if (StringUtils.hasText(properties.getBasename())) {
      messageSource.setBasenames(StringUtils
            .commaDelimitedListToStringArray(StringUtils.trimAllWhitespace(properties.getBasename())));
   }
   if (properties.getEncoding() != null) {
      messageSource.setDefaultEncoding(properties.getEncoding().name());
   }
   messageSource.setFallbackToSystemLocale(properties.isFallbackToSystemLocale());
   Duration cacheDuration = properties.getCacheDuration();
   if (cacheDuration != null) {
      messageSource.setCacheMillis(cacheDuration.toMillis());
   }
   messageSource.setAlwaysUseMessageFormat(properties.isAlwaysUseMessageFormat());
   messageSource.setUseCodeAsDefaultMessage(properties.isUseCodeAsDefaultMessage());
   return messageSource;
}
```

我们真实 的情况是放在了i18n目录下，所以我们要去配置这个messages的路径；

```properties
spring.messages.basename=i18n.login
```

去页面获取国际化的值，查看Thymeleaf的文档，找到message取值操作为：#{...}。我们去页面测试下：

```html
<body class="text-center">
   <form class="form-signin" th:action="@{/user/login}">
      <img class="mb-4" th:src="@{/img/bootstrap-solid.svg}" alt="" width="72" height="72">
      <h1 class="h3 mb-3 font-weight-normal" th:text="#{login.tip}">Please sign in</h1>
      <p th:text="${msg}" th:if="${not #strings.isEmpty(msg)}"></p>
      <input type="text" name="username" class="form-control" th:placeholder="#{login.username}" required="" autofocus="">
      <input type="password" name="password" class="form-control" th:placeholder="#{login.password}" required="">
      <div class="checkbox mb-3">
         <label>
         <input type="checkbox" value="remember-me"> [[#{login.remember}]]
       </label>
      </div>
      <button class="btn btn-lg btn-primary btn-block" type="submit" th:text="#{login.btn}">Sign in</button>
      <p class="mt-5 mb-3 text-muted">© 2017-2018</p>
      <a class="btn btn-sm" th:href="@{/index.html(l='zh_CN')}">中文</a>
      <a class="btn btn-sm" th:href="@{/index.html(l='en_US')}">English</a>
   </form>

</body>
```

启动项目，访问一下，发现已经自动识别为中文

![image-20210413234304503](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210413234304503.png)

### 11.4、配置国际化解析

在Spring中有一个国际化的Locale （区域信息对象）；里面有一个叫做LocaleResolver （获取区域信息对象）的解析器！

我们去我们webmvc自动配置文件，寻找一下！看到SpringBoot默认配置：

```java
@Override
@Bean
@ConditionalOnMissingBean(name = DispatcherServlet.LOCALE_RESOLVER_BEAN_NAME)
@SuppressWarnings("deprecation")
public LocaleResolver localeResolver() {
    // 容器中没有就自己配，有的话就用用户配置的
   if (this.webProperties.getLocaleResolver() == WebProperties.LocaleResolver.FIXED) {
      return new FixedLocaleResolver(this.webProperties.getLocale());
   }
   if (this.mvcProperties.getLocaleResolver() == WebMvcProperties.LocaleResolver.FIXED) {
      return new FixedLocaleResolver(this.mvcProperties.getLocale());
   }
    // 接收头国际化分解
   AcceptHeaderLocaleResolver localeResolver = new AcceptHeaderLocaleResolver();
   Locale locale = (this.webProperties.getLocale() != null) ? this.webProperties.getLocale()
         : this.mvcProperties.getLocale();
   localeResolver.setDefaultLocale(locale);
   return localeResolver;
}
```

AcceptHeaderLocaleResolver 这个类中有一个方法

```java
@Override
public Locale resolveLocale(HttpServletRequest request) {
   Locale defaultLocale = getDefaultLocale();
    // 默认的就是根据请求头带来的区域信息获取Locale进行国际化
   if (defaultLocale != null && request.getHeader("Accept-Language") == null) {
      return defaultLocale;
   }
   Locale requestLocale = request.getLocale();
   List<Locale> supportedLocales = getSupportedLocales();
   if (supportedLocales.isEmpty() || supportedLocales.contains(requestLocale)) {
      return requestLocale;
   }
   Locale supportedLocale = findSupportedLocale(request, supportedLocales);
   if (supportedLocale != null) {
      return supportedLocale;
   }
   return (defaultLocale != null ? defaultLocale : requestLocale);
}
```

那假如我们现在想点击链接让我们的国际化资源生效，就需要让我们自己的Locale生效！

我们去自己写一个自己的LocaleResolver，可以在链接上携带区域信息！

修改一下前端页面的跳转连接：

```html
<!-- 这里传入参数不需要使用 ？使用 （key=value）-->
<a class="btn btn-sm" th:href="@{/index.html(l='zh_CN')}">中文</a>
<a class="btn btn-sm" th:href="@{/index.html(l='en_US')}">English</a>
```

我们去写一个处理的组件类！

```java
package com.lei.config;
import org.springframework.util.StringUtils;
import org.springframework.web.servlet.LocaleResolver;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.util.Locale;

//可以在链接上携带区域信息
public class MyLocalResolver implements LocaleResolver {

    @Override
    public Locale resolveLocale(HttpServletRequest request) {

        String language = request.getParameter("l");

        // 如果没有获取到就使用系统默认的
        Locale locale = Locale.getDefault();
		
        //如果请求链接不为空
        if (StringUtils.hasText(language)){
            //分割请求参数
            String[] split = language.split("_");
            //国家，地区
            locale = new Locale(split[0], split[1]);
        }

        return locale;
    }

    @Override
    public void setLocale(HttpServletRequest request, HttpServletResponse response, Locale locale) {

    }
}
```

为了让我们的区域化信息能够生效，我们需要再配置一下这个组件！在我们自己的MvcConofig下添加bean；

```java
@Bean
public LocaleResolver localeResolver(){
    return new MyLocalResolver();
}
```

## 12、整合JDBC

对于数据访问层，无论是 SQL(关系型数据库) 还是 NOSQL(非关系型数据库)，Spring Boot 底层都是采用 Spring Data 的方式进行统一处理。

Spring Boot 底层都是采用 Spring Data 的方式进行统一处理各种数据库，Spring Data 也是 Spring 中与 Spring Boot、Spring Cloud 等齐名的知名项目。

Sping Data 官网：https://spring.io/projects/spring-data

数据库相关的启动器 ：可以参考官方文档：

https://docs.spring.io/spring-boot/docs/current/reference/html/using-spring-boot.html#using-boot-starter

### 12.1、创建测试项目测试数据源

1、新建一个项目测试：springboot-04-data ; 引入相应的模块！基础模块

![image-20210415231036334](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210415231036334.png)

2、项目建好之后，发现自动帮我们导入了如下的启动器：

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jdbc</artifactId>
</dependency>
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```

3、编写yml配置文件连接数据库

```yaml
spring:
  datasource:
    username: "root"
    password: "9468"
    url: "jdbc:mysql://localhost:3306/mybatis?useUnicode=true&characterEncoding=utf-8"
    driver-class-name: com.mysql.cj.jdbc.Driver
```

4、配置完这一些东西后，我们就可以直接去使用了，因为SpringBoot已经默认帮我们进行了自动配置；去测试类测试一下

```java
@SpringBootTest
class Springboot04DataApplicationTests {
    @Autowired
    DataSource dataSource;
    @Test
    void contextLoads() throws SQLException {
        //查看默认数据源
        System.out.println(dataSource.getClass());
        Connection connection = dataSource.getConnection();
        System.out.println(connection);
        connection.close();
    }
}
```

结果：我们可以看到他默认给我们配置的数据源为 : class com.zaxxer.hikari.HikariDataSource ， 我们并没有手动配置

全局搜索，找到数据源的所有自动配置都在 ：DataSourceAutoConfiguration文件：

```java
@Import({ DataSourceConfiguration.Hikari.class, DataSourceConfiguration.Tomcat.class,
      DataSourceConfiguration.Dbcp2.class, DataSourceConfiguration.OracleUcp.class,
      DataSourceConfiguration.Generic.class, DataSourceJmxConfiguration.class })
protected static class PooledDataSourceConfiguration {

}
```

这里导入的类都在 DataSourceConfiguration 配置类下，可以看出 Spring Boot 2.2.5 默认使用HikariDataSource 数据源，而以前版本，如 Spring Boot 1.5 默认使用 org.apache.tomcat.jdbc.pool.DataSource 作为数据源；

**HikariDataSource 号称 Java WEB 当前速度最快的数据源，相比于传统的 C3P0 、DBCP、Tomcat jdbc 等连接池更加优秀；**

**可以使用 spring.datasource.type 指定自定义的数据源类型，值为 要使用的连接池实现的完全限定名。**



关于数据源我们并不做介绍，有了数据库连接，显然就可以 CRUD 操作数据库了。但是我们需要先了解一个对象 JdbcTemplate

### 12.2、JDBCTemplate

1、有了数据源(com.zaxxer.hikari.HikariDataSource)，然后可以拿到数据库连接(java.sql.Connection)，有了连接，就可以使用原生的 JDBC 语句来操作数据库；

2、即使不使用第三方第数据库操作框架，如 MyBatis等，Spring 本身也对原生的JDBC 做了轻量级的封装，即JdbcTemplate。

3、数据库操作的所有 CRUD 方法都在 JdbcTemplate 中。

4、Spring Boot 不仅提供了默认的数据源，同时默认已经配置好了 JdbcTemplate 放在了容器中，程序员只需自己注入即可使用

5、JdbcTemplate 的自动配置是依赖 org.springframework.boot.autoconfigure.jdbc 包下的 JdbcTemplateConfiguration 类

**JdbcTemplate主要提供以下几类方法：**

- execute方法：可以用于执行任何SQL语句，一般用于执行DDL语句；
- update方法及batchUpdate方法：update方法用于执行新增、修改、删除等语句；batchUpdate方法用于执行批处理相关语句；
- query方法及queryForXXX方法：用于执行查询相关语句；
- call方法：用于执行存储过程、函数相关语句。

**【测试】**

编写一个Controller，注入 jdbcTemplate，编写测试方法进行访问测试；

```java
package com.lei.springboot04data.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;
import java.util.Map;

/**
 * @author zhulei
 * @create 2021-04-15 21:09
 */
@RestController
public class JDBCController {

    @Autowired
    JdbcTemplate jdbcTemplate;

    //查询数据库所有信息
    @GetMapping("/userList")
    public List<Map<String,Object>> userList() {
        String sql = "select * from mybatis.user";
        List<Map<String, Object>> list_maps = jdbcTemplate.queryForList(sql);
        return list_maps;
    }

    @GetMapping("/addUser")
    public String addUser() {
        String sql = "insert into mybatis.user (id,name,pwd) value(6,'周六','123456')";
        jdbcTemplate.update(sql);
        return "update-ok";
    }

    @GetMapping("/updateUser/{id}")
    public String updateUser(@PathVariable("id") int id) {
        String sql = "update mybatis.user set name=?,pwd=? where id="+id;

        Object[] objects = new Object[2];
        objects[0] = "小明2";
        objects[1] = "zzzzzz";

        jdbcTemplate.update(sql,objects[0],objects[1]);
        return "updateUser-ok";
    }

    @GetMapping("/deleteUser/{id}")
    public String deleteUser(@PathVariable("id") int id) {
        String sql = "delete from mybatis.user where id=?";
        jdbcTemplate.update(sql,id);
        return "deleteUser-ok";
    }
}
```

## 13、整合Druid

### 13.1、简介

java程序很大一部分要操作数据库，为了提高性能操作数据库的时候，又不得不使用数据库连接池。

Druid 是阿里巴巴开源平台上一个数据库连接池实现，结合了 C3P0、DBCP 等 DB 池的优点，同时加入了日志监控。

Druid 可以很好的监控 DB 池连接和 SQL 的执行情况，天生就是针对监控而生的 DB 连接池。

Druid已经在阿里巴巴部署了超过600个应用，经过一年多生产环境大规模部署的严苛考验。

Spring Boot 2.0 以上默认使用 Hikari 数据源，可以说 Hikari 与 Driud 都是当前 Java Web 上最优秀的数据源，我们来重点介绍 Spring Boot 如何集成 Druid 数据源，如何实现数据库监控。

Github地址：https://github.com/alibaba/druid/

**com.alibaba.druid.pool.DruidDataSource 基本配置参数如下：**

| 配置                                      | 缺省值             | 说明                                                         |
| ----------------------------------------- | ------------------ | ------------------------------------------------------------ |
| name                                      |                    | 配置这个属性的意义在于，如果存在多个数据源，监控的时候可以通过名字来区分开来。如果没有配置，将会生成一个名字，格式是："DataSource-" + System.identityHashCode(this). 另外配置此属性至少在1.0.5版本中是不起作用的，强行设置name会出错。[详情-点此处](http://blog.csdn.net/lanmo555/article/details/41248763)。 |
| url                                       |                    | 连接数据库的url，不同数据库不一样。例如： mysql : jdbc:mysql://10.20.153.104:3306/druid2 oracle : jdbc:oracle:thin:@10.20.149.85:1521:ocnauto |
| username                                  |                    | 连接数据库的用户名                                           |
| password                                  |                    | 连接数据库的密码。如果你不希望密码直接写在配置文件中，可以使用ConfigFilter。[详细看这里](https://github.com/alibaba/druid/wiki/使用ConfigFilter) |
| driverClassName                           | 根据url自动识别    | 这一项可配可不配，如果不配置druid会根据url自动识别dbType，然后选择相应的driverClassName |
| initialSize                               | 0                  | 初始化时建立物理连接的个数。初始化发生在显示调用init方法，或者第一次getConnection时 |
| maxActive                                 | 8                  | 最大连接池数量                                               |
| maxIdle                                   | 8                  | 已经不再使用，配置了也没效果                                 |
| minIdle                                   |                    | 最小连接池数量                                               |
| maxWait                                   |                    | 获取连接时最大等待时间，单位毫秒。配置了maxWait之后，缺省启用公平锁，并发效率会有所下降，如果需要可以通过配置useUnfairLock属性为true使用非公平锁。 |
| poolPreparedStatements                    | false              | 是否缓存preparedStatement，也就是PSCache。PSCache对支持游标的数据库性能提升巨大，比如说oracle。在mysql下建议关闭。 |
| maxPoolPreparedStatementPerConnectionSize | -1                 | 要启用PSCache，必须配置大于0，当大于0时，poolPreparedStatements自动触发修改为true。在Druid中，不会存在Oracle下PSCache占用内存过多的问题，可以把这个数值配置大一些，比如说100 |
| validationQuery                           |                    | 用来检测连接是否有效的sql，要求是一个查询语句，常用select 'x'。如果validationQuery为null，testOnBorrow、testOnReturn、testWhileIdle都不会起作用。 |
| validationQueryTimeout                    |                    | 单位：秒，检测连接是否有效的超时时间。底层调用jdbc Statement对象的void setQueryTimeout(int seconds)方法 |
| testOnBorrow                              | true               | 申请连接时执行validationQuery检测连接是否有效，做了这个配置会降低性能。 |
| testOnReturn                              | false              | 归还连接时执行validationQuery检测连接是否有效，做了这个配置会降低性能。 |
| testWhileIdle                             | false              | 建议配置为true，不影响性能，并且保证安全性。申请连接的时候检测，如果空闲时间大于timeBetweenEvictionRunsMillis，执行validationQuery检测连接是否有效。 |
| keepAlive                                 | false （1.0.28）   | 连接池中的minIdle数量以内的连接，空闲时间超过minEvictableIdleTimeMillis，则会执行keepAlive操作。 |
| timeBetweenEvictionRunsMillis             | 1分钟（1.0.14）    | 有两个含义： 1) Destroy线程会检测连接的间隔时间，如果连接空闲时间大于等于minEvictableIdleTimeMillis则关闭物理连接。 2) testWhileIdle的判断依据，详细看testWhileIdle属性的说明 |
| numTestsPerEvictionRun                    | 30分钟（1.0.14）   | 不再使用，一个DruidDataSource只支持一个EvictionRun           |
| minEvictableIdleTimeMillis                |                    | 连接保持空闲而不被驱逐的最小时间                             |
| connectionInitSqls                        |                    | 物理连接初始化的时候执行的sql                                |
| exceptionSorter                           | 根据dbType自动识别 | 当数据库抛出一些不可恢复的异常时，抛弃连接                   |
| filters                                   |                    | 属性类型是字符串，通过别名的方式配置扩展插件，常用的插件有： 监控统计用的filter:stat 日志用的filter:log4j 防御sql注入的filter:wall |
| proxyFilters                              |                    | 类型是List<com.alibaba.druid.filter.Filter>，如果同时配置了filters和proxyFilters，是组合关系，并非替换关系 |

**通用配置**

DruidDataSource大部分属性都是参考DBCP的，如果你原来就是使用DBCP，迁移是十分方便的。

```xml
 <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close"> 
     <property name="url" value="${jdbc_url}" />
     <property name="username" value="${jdbc_user}" />
     <property name="password" value="${jdbc_password}" />

     <property name="filters" value="stat" />

     <property name="maxActive" value="20" />
     <property name="initialSize" value="1" />
     <property name="maxWait" value="6000" />
     <property name="minIdle" value="1" />

     <property name="timeBetweenEvictionRunsMillis" value="60000" />
     <property name="minEvictableIdleTimeMillis" value="300000" />

     <property name="testWhileIdle" value="true" />
     <property name="testOnBorrow" value="false" />
     <property name="testOnReturn" value="false" />

     <property name="poolPreparedStatements" value="true" />
     <property name="maxOpenPreparedStatements" value="20" />

     <property name="asyncInit" value="true" />
 </bean>
```

- 在上面的配置中，通常你需要配置url、username、password，maxActive这三项。
- Druid会自动跟url识别驱动类名，如果连接的数据库非常见数据库，配置属性driverClassName
- asyncInit是1.1.4中新增加的配置，如果有initialSize数量较多时，打开会加快应用启动时间

### 13.2、配置数据源

1、添加上 Druid 数据源依赖

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.1.21</version>
</dependency>
```

2、切换数据源；之前已经说过 Spring Boot 2.0 以上默认使用 com.zaxxer.hikari.HikariDataSource 数据源，但可以 通过 spring.datasource.type 指定数据源。

```yml
spring:
  datasource:
    username: "root"
    password: "9468"
    url: "jdbc:mysql://localhost:3306/mybatis?useUnicode=true&characterEncoding=utf-8"
    driver-class-name: com.mysql.cj.jdbc.Driver
    type: com.alibaba.druid.pool.DruidDataSource
```

3、数据源切换之后，在测试类中注入 DataSource，然后获取到它，输出一看便知是否成功切换；

![image-20210415232602260](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210415232602260.png)

4、切换成功！既然切换成功，就可以设置数据源连接初始化大小、最大连接数、等待时间、最小连接数 等设置项；可以查看源码

```yaml
spring:
  datasource:
    username: "root"
    password: "9468"
    url: "jdbc:mysql://localhost:3306/mybatis?useUnicode=true&characterEncoding=utf-8"
    driver-class-name: com.mysql.cj.jdbc.Driver
    type: com.alibaba.druid.pool.DruidDataSource
    #druid数据源专有配置
    initialSize: 5
    minIdle: 5
    maxActive: 20
    maxWait: 60000
    timeBetweenEvictionRunsMillis: 60000
    minEvictableIdleTimeMillis: 300000
    validationQuery: SELECT 1 FROM DUAL
    testWhileIdle: true
    testOnBorrow: false
    testOnReturn: false
    poolPreparedStatements: true

    #配置监控统计拦截的filters，stat：监控统计、log4j：日志记录、wall：防御sql注入
    #如果允许报错，java.lang.ClassNotFoundException: org.apache.Log4j.Properity
    #则导入log4j 依赖就行
    filters: stat,wall,log4j
    maxPoolPreparedStatementPerConnectionSize: 20
    useGlobalDataSourceStat: true
    connectionProperties: druid.stat.mergeSql=true;druid.stat.slowSqlMillis=500
```

5、导入Log4j 的依赖

```xml
<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.12</version>
</dependency>
```

6、现在需要程序员自己为 DruidDataSource 绑定全局配置文件中的参数，再添加到容器中，而不再使用 Spring Boot 的自动生成了；我们需要 自己添加 DruidDataSource 组件到容器中，并绑定属性；

```java
@Configuration
public class DruidConfig {

    /*
       将自定义的 Druid数据源添加到容器中，不再让 Spring Boot 自动创建
       绑定全局配置文件中的 druid 数据源属性到 com.alibaba.druid.pool.DruidDataSource从而让它们生效
       @ConfigurationProperties(prefix = "spring.datasource")：作用就是将 全局配置文件中
       前缀为 spring.datasource的属性值注入到 com.alibaba.druid.pool.DruidDataSource 的同名参数中
     */
    @ConfigurationProperties(prefix = "spring.datasource")
    @Bean
    public DataSource druidDataSource() {
        return new DruidDataSource();
    }
}
```

### 13.3、配置Druid数据源监控

Druid 数据源具有监控的功能，并提供了一个 web 界面方便用户查看，类似安装 路由器 时，人家也提供了一个默认的 web 页面。

所以第一步需要设置 Druid 的后台管理页面，比如 登录账号、密码 等；配置后台管理；

```java
//后台监控
@Bean
public ServletRegistrationBean statViewServlet() {
    ServletRegistrationBean<StatViewServlet> bean = new ServletRegistrationBean<>(new StatViewServlet(), "/druid/*");

    // 这些参数可以在 com.alibaba.druid.support.http.StatViewServlet 
    // 的父类 com.alibaba.druid.support.http.ResourceServlet 中找到
    Map<String, String> initParameters = new HashMap<>();
    //后台管理界面的登录账号
    initParameters.put("loginUsername","admin");
    //后台管理界面的登录密码
    initParameters.put("loginPassword","123456");
    //后台允许谁可以访问
    //initParams.put("allow", "localhost")：表示只有本机可以访问
    //initParams.put("allow", "")：为空或者为null时，表示允许所有访问
    initParameters.put("allow","");
    //deny：Druid 后台拒绝谁访问
    //initParams.put("kuangshen", "192.168.1.20");表示禁止此ip访问

    //设置初始化参数
    bean.setInitParameters(initParameters);

    return bean;
}
```

![image-20210415233829165](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210415233829165.png)

配置完毕后，我们可以选择访问 ：http://localhost:8080/druid/login.html

![image-20210415233922641](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210415233922641.png)

进入之后

![image-20210415233950867](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210415233950867.png)

**配置 Druid web 监控 filter 过滤器**

```java
//配置 Druid 监控 之  web 监控的 filter
//WebStatFilter：用于配置Web和Druid数据源之间的管理关联监控统计
@Bean
public FilterRegistrationBean webStatFilter() {
    FilterRegistrationBean bean = new FilterRegistrationBean();

    bean.setFilter(new WebStatFilter());

    Map<String,String> initParameters = new HashMap<>();

    //exclusions：设置哪些请求进行过滤排除掉，从而不进行统计
    initParameters.put("exclusions","*.js,*.css,/druid/*,/jdbc/*");

    bean.setInitParameters(initParameters);

    return bean;
}
```

### 13.4、配置log4j

需要在resource目录下新建一个log4j.properties文件

![image-20210415234225169](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210415234225169.png)

```properties
  log4j.logger.druid.sql=warn,stdout
  log4j.logger.druid.sql.DataSource=warn,stdout
  log4j.logger.druid.sql.Connection=warn,stdout
  log4j.logger.druid.sql.Statement=warn,stdout
  log4j.logger.druid.sql.ResultSet=warn,stdout
```

## 14、整合MyBatis


官方文档：http://mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/

Maven仓库地址：https://mvnrepository.com/artifact/org.mybatis.spring.boot/mybatis-spring-boot-starter/2.1.1

![image-20210419195933738](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210419195933738.png)

### 14.1、整合测试

1、导入 MyBatis 所需要的依赖

```xml
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.1.1</version>
</dependency>
```

2、配置数据库连接信息（不变）

```properties
spring.datasource.username=root
spring.datasource.password=9468
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```

3、测试数据库是否连接成功

4、创建实体类，导入 Lombok

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class User {
    private int id;
    private String name;
    private String pwd;
}
```

5、创建mapper目录以及对应的 Mapper 接口

```java
@Mapper
@Repository
public interface UserMapper {

    List<User> queryUserList();

    User queryUserById(int id);

    int addUser(User user);

    int updateUser(User user);

    int deleteUser(int id);

}
```

6、对应的Mapper映射文件

resource/mybatis/mapper/UserMapper.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.lei.mapper.UserMapper">

    <select id="queryUserList" resultType="User">
        select * from mybatis.user
    </select>

    <select id="queryUserById" resultType="User">
        select * from mybatis.user where id = #{id}
    </select>

    <insert id="addUser" parameterType="User">
        insert into mybatis.user (id, name, pwd) VALUES (#{id},#{name},#{pwd})
    </insert>

    <update id="updateUser" parameterType="User">
        update mybatis.user
        set name = #{name},pwd = #{pwd}
        where id = #{id};
    </update>

    <delete id="deleteUser" parameterType="int">
        delete from mybatis.user where id = #{id}
    </delete>

</mapper>
```

7、maven配置资源过滤问题

```xml
<build>
    <resources>
        <resource>
            <directory>src/main/java</directory>
            <includes>
                <include>**/*.xml</include>
            </includes>
            <filtering>true</filtering>
        </resource>
    </resources>
</build>
```

8、编写 UserController 进行测试！

```java
@RestController
public class UserController {
    @Autowired
    private UserMapper userMapper;

    @GetMapping("/queryUserList")
    public String queryUserList(){
        List<User> users = userMapper.queryUserList();
        Gson gson = new Gson();
        String s = gson.toJson(users);
        return s;
    }
}
```

9、启动项目访问进行测试

![image-20210419200816722](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210419200816722.png)

## 15、集成SpringSecurity

### 15.1、安全简介

在 Web 开发中，安全一直是非常重要的一个方面。安全虽然属于应用的非功能性需求，但是应该在应用开发的初期就考虑进来。如果在应用开发的后期才考虑安全的问题，就可能陷入一个两难的境地：一方面，应用存在严重的安全漏洞，无法满足用户的要求，并可能造成用户的隐私数据被攻击者窃取；另一方面，应用的基本架构已经确定，要修复安全漏洞，可能需要对系统的架构做出比较重大的调整，因而需要更多的开发时间，影响应用的发布进程。因此，从应用开发的第一天就应该把安全相关的因素考虑进来，并在整个应用的开发过程中。

市面上存在比较有名的：Shiro，Spring Security ！

这里需要阐述一下的是，每一个框架的出现都是为了解决某一问题而产生了，那么Spring Security框架的出现是为了解决什么问题呢？

首先我们看下它的官网介绍：Spring Security官网地址

Spring Security is a powerful and highly customizable authentication and access-control framework. It is the de-facto standard for securing Spring-based applications.

Spring Security is a framework that focuses on providing both authentication and authorization to Java applications. Like all Spring projects, the real power of Spring Security is found in how easily it can be extended to meet custom requirements

Spring Security是一个功能强大且高度可定制的身份验证和访问控制框架。它实际上是保护基于spring的应用程序的标准。

Spring Security是一个框架，侧重于为Java应用程序提供身份验证和授权。与所有Spring项目一样，Spring安全性的真正强大之处在于它可以轻松地扩展以满足定制需求

从官网的介绍中可以知道这是一个权限框架。想我们之前做项目是没有使用框架是怎么控制权限的？对于权限 一般会细分为功能权限，访问权限，和菜单权限。代码会写的非常的繁琐，冗余。

怎么解决之前写权限代码繁琐，冗余的问题，一些主流框架就应运而生而Spring Scecurity就是其中的一种。

Spring 是一个非常流行和成功的 Java 应用开发框架。Spring Security 基于 Spring 框架，提供了一套 Web 应用安全性的完整解决方案。一般来说，Web 应用的安全性包括用户认证（Authentication）和用户授权（Authorization）两个部分。用户认证指的是验证某个用户是否为系统中的合法主体，也就是说用户能否访问该系统。用户认证一般要求用户提供用户名和密码。系统通过校验用户名和密码来完成认证过程。用户授权指的是验证某个用户是否有权限执行某个操作。在一个系统中，不同用户所具有的权限是不同的。比如对一个文件来说，有的用户只能进行读取，而有的用户可以进行修改。一般来说，系统会为不同的用户分配不同的角色，而每个角色则对应一系列的权限。

对于上面提到的两种应用情景，Spring Security 框架都有很好的支持。在用户认证方面，Spring Security 框架支持主流的认证方式，包括 HTTP 基本认证、HTTP 表单验证、HTTP 摘要认证、OpenID 和 LDAP 等。在用户授权方面，Spring Security 提供了基于角色的访问控制和访问控制列表（Access Control List，ACL），可以对应用中的领域对象进行细粒度的控制。

### 15.2、实战测试

#### 15.2.1、环境搭建

1、新建一个初始的springboot项目web模块，thymeleaf模块

2、导入静态资源

![image-20210419201128228](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210419201128228.png)

3、controller跳转

```java
@Controller
public class RouterController {

    @RequestMapping({"/","/index"})
    public String index(){
        return "index";
    }

    @RequestMapping("/toLogin")
    public String toLogin(){
        return "pages/login";
    }

    @RequestMapping("/level1/{id}")
    public String level1(@PathVariable("id") int id){
        return "pages/level1/"+id;
    }

    @RequestMapping("/level2/{id}")
    public String level2(@PathVariable("id") int id){
        return "pages/level2/"+id;
    }

    @RequestMapping("/level3/{id}")
    public String level3(@PathVariable("id") int id){
        return "pages/level3/"+id;
    }

}
```

#### 15.2.2、认识SpringSecurity

Spring Security 是针对Spring项目的安全框架，也是Spring Boot底层安全模块默认的技术选型，他可以实现强大的Web安全控制，对于安全控制，我们仅需要引入spring-boot-starter-security 模块，进行少量的配置，即可实现强大的安全管理！

记住几个类：

- WebSecurityConfigurerAdapter：自定义Security策略
- AuthenticationManagerBuilder：自定义认证策略
- @EnableWebSecurity：开启WebSecurity模式

Spring Security的两个主要目标是 “认证” 和 “授权”（访问控制）。

**“认证”（Authentication）**

身份验证是关于验证您的凭据，如用户名/用户ID和密码，以验证您的身份。

身份验证通常通过用户名和密码完成，有时与身份验证因素结合使用。

 **“授权” （Authorization）**

授权发生在系统成功验证您的身份后，最终会授予您访问资源（如信息，文件，数据库，资金，位置，几乎任何内容）的完全权限。

这个概念是通用的，而不是只在Spring Security 中存在。

#### 15.2.3、认证和授权

目前，我们的测试环境，是谁都可以访问的，我们使用 Spring Security 增加上认证和授权的功能

1、引入 Spring Security 模块

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

2、编写 Spring Security 配置类

参考官网：https://spring.io/projects/spring-security 

查看我们自己项目中的版本，找到对应的帮助文档：

3、编写基础配置类

```java
package com.lei.config;

import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;

@EnableWebSecurity// 开启WebSecurity模式
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    //授权
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        
    }
}
```

4、定制请求的授权规则

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    //首页所有人可以访问，功能叶只能有权限的人才能访问
    http.authorizeRequests()
            .antMatchers("/").permitAll()
            .antMatchers("/level1/**").hasRole("vip1")
            .antMatchers("/level2/**").hasRole("vip2")
            .antMatchers("/level3/**").hasRole("vip3");
}
```

5、测试一下：发现除了首页都进不去了！因为我们目前没有登录的角色，因为请求需要登录的角色拥有对应的权限才可以

6、在configure()方法中加入以下配置，开启自动配置的登录功能

```java
// 开启自动配置的登录功能
// /login 请求来到登录页
// /login?error 重定向到这里表示登录失败
http.formLogin();
```

7、测试一下：发现，没有权限的时候，会跳转到登录的页面

![image-20210419201640507](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210419201640507.png)

8、查看刚才登录页的注释信息

我们可以定义认证规则，重写configure(AuthenticationManagerBuilder auth)方法

```java
//认证
//密码编码
//在springSecurity 5.0+ 增加了加密方法
@Override
protected void configure(AuthenticationManagerBuilder auth) throws Exception {
    auth.inMemoryAuthentication().passwordEncoder(new BCryptPasswordEncoder())
            .withUser("leige").password("123456").roles("vip2","vip3")
            .and()
            .withUser("root").password("123456").roles("vip1","vip2","vip3");
}
```

9、测试，我们可以使用这些账号登录进行测试！发现会报错！

There is no PasswordEncoder mapped for the id “null”

10、原因，我们要将前端传过来的密码进行某种方式加密，否则就无法登录，修改代码

```java
//认证
//密码编码
//在springSecurity 5.0+ 增加了加密方法
//spring security 官方推荐的是使用bcrypt加密方式
@Override
protected void configure(AuthenticationManagerBuilder auth) throws Exception {
    auth.inMemoryAuthentication().passwordEncoder(new BCryptPasswordEncoder())
            .withUser("leige").password(new BCryptPasswordEncoder().encode("123456")).roles("vip2","vip3")
            .and()
            .withUser("root").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1","vip2","vip3");
}
```

11、测试，发现，登录成功，并且每个角色只能访问自己认证下的规则

#### 15.2.4、权限注销和控制

1、开启自动配置的注销的功能

```java
//定制请求的授权规则
@Override
protected void configure(HttpSecurity http) throws Exception {
   //....
   //开启自动配置的注销的功能
      // /logout 注销请求
   http.logout();
}
```

2、我们在前端，增加一个注销的按钮，index.html 导航栏中

```html
<a th:href="@{/logout}">注销</a>
```

3、我们可以去测试一下，登录成功后点击注销，发现注销完毕会跳转到登录页面

4、但是，我们想让他注销成功后，依旧可以跳转到首页

```java
// .logoutSuccessUrl("/"); 注销成功来到首页
http.logout().logoutSuccessUrl("/");
```

5、测试，注销完毕后，发现跳转到首页OK

6、我们现在又来一个需求：用户没有登录的时候，导航栏上只显示登录按钮，用户登录之后，导航栏可以显示登录的用户信息及注销按钮！还有就是，比如kuangshen这个用户，它只有 vip2，vip3功能，那么登录则只显示这两个功能，而vip1的功能菜单不显示！这个就是真实的网站情况了！该如何做呢？

我们需要结合thymeleaf中的一些功能

sec：authorize="isAuthenticated()":是否认证登录！来显示不同的页面

Maven依赖：

```xml
<dependency>
    <groupId>org.thymeleaf.extras</groupId>
    <artifactId>thymeleaf-extras-springsecurity5</artifactId>
    <version>3.0.4.RELEASE</version>
</dependency>
```

7、修改我们的 前端页面

导入命名空间

```
xmlns:sec="http://www.thymeleaf.org/thymeleaf-extras-springsecurity5"
```

修改导航栏，增加认证判断

```html
<div sec:authorize="!isAuthenticated()">
    <a th:href="@{/login}">请登录</a>
</div>
<div sec:authorize="isAuthenticated()">
    用户名： <span sec:authentication="name"></span>
    角色：<span sec:authentication="principal.authorities"></span>
</div>
<div sec:authorize="isAuthenticated()">
    <a th:href="@{/logout}">注销</a>
</div>
```

8、重启测试，我们可以登录试试看，登录成功后确实，显示了我们想要的页面

9、如果注销404了，就是因为它默认防止csrf跨站请求伪造，因为会产生安全问题，我们可以将请求改为post表单提交，或者在spring security中关闭csrf功能；我们试试：在 配置中增加 `http.csrf().disable();`

```java
http.csrf().disable();//关闭csrf功能:跨站请求伪造,默认只能通过post方式提交logout请求
http.logout().logoutSuccessUrl("/");
```

10、我们继续将下面的角色功能块认证完成

```html
<div sec:authorize="hasRole('vip1')">
    <h3>普通武功秘籍</h3>
    <ul>
        <li><a th:href="@{/level1/1}">罗汉拳</a></li>
        <li><a th:href="@{/level1/2}">武当长拳</a></li>
        <li><a th:href="@{/level1/3}">全真剑法</a></li>
    </ul>
</div>
<div sec:authorize="hasRole('vip2')">
    <h3>高级武功秘籍</h3>
    <ul>
        <li><a th:href="@{/level2/1}">太极拳</a></li>
        <li><a th:href="@{/level2/2}">七伤拳</a></li>
        <li><a th:href="@{/level2/3}">梯云纵</a></li>
    </ul>
</div>
<div sec:authorize="hasRole('vip3')">
    <h3>绝世武功秘籍</h3>
    <ul>
        <li><a th:href="@{/level3/1}">葵花宝典</a></li>
        <li><a th:href="@{/level3/2}">龟派气功</a></li>
        <li><a th:href="@{/level3/3}">独孤九剑</a></li>
    </ul>
</div>
```

#### 15.2.5、记住我

现在的情况，我们只要登录之后，关闭浏览器，再登录，就会让我们重新登录，但是很多网站的情况，就是有一个记住密码的功能，这个该如何实现呢？很简单

1、开启记住我功能

```java
//定制请求的授权规则
@Override
protected void configure(HttpSecurity http) throws Exception {
//。。。。。。。。。。。
   //记住我
   http.rememberMe();
}
```

2、我们再次启动项目测试一下，发现登录页多了一个记住我功能，我们登录之后关闭 浏览器，然后重新打开浏览器访问，发现用户依旧存在

思考：如何实现的呢？其实非常简单

我们可以查看浏览器的cookie

3、我们点击注销的时候，可以发现，spring security 帮我们自动删除了这个 cookie

4、结论：登录成功后，将cookie发送给浏览器保存，以后登录带上这个cookie，只要通过检查就可以免登录了。如果点击注销，则会删除这个cookie

#### 15.2.6、定制登录页

1、在刚才的登录页配置后面指定 loginpage

```java
http.formLogin().loginPage("/toLogin");
```

2、然后前端也需要指向我们自己定义的 login请求

```html
<div sec:authorize="!isAuthenticated()">
    <a th:href="@{/toLogin}">请登录</a>
</div>
```

3、我们登录，需要将这些信息发送到哪里，我们也需要配置，login.html 配置提交请求及方式，方式必须为post:

在 loginPage()源码中的注释上有写明：

```html
<form th:action="@{/login}" method="post">
   用户名:<input name="username"/><br>
   密码:<input name="password"><br/>
   <input type="checkbox" name="remember"> 记住我
   <input type="submit" value="登陆">
</form>
```

4、这个请求提交上来，我们还需要验证处理，怎么做呢？我们可以查看formLogin()方法的源码！我们配置接收登录的用户名和密码的参数！

```java
http.formLogin()
  .usernameParameter("username")
  .passwordParameter("password")
  .loginPage("/toLogin")
  .loginProcessingUrl("/login"); // 登陆表单提交请求
```

5、在登录页增加记住我的多选框

```html
<input type="checkbox" name="remember"> 记住我
```

6、后端验证处理！

```java
//开启记住我，默认保存两周
http.rememberMe().rememberMeParameter("remember");
```

### 15.3、完整配置代码

```java
package com.lei.config;

import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;

/**
 * @author zhulei
 * @create 2021-04-17 20:33
 */
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    //授权
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        //首页所有人可以访问，功能叶只能有权限的人才能访问
        http.authorizeRequests()
                .antMatchers("/").permitAll()
                .antMatchers("/level1/**").hasRole("vip1")
                .antMatchers("/level2/**").hasRole("vip2")
                .antMatchers("/level3/**").hasRole("vip3");

        //没有权限默认会到登录页面
        http.formLogin().
                loginPage("/toLogin").
                loginProcessingUrl("/login");

        http.logout().logoutSuccessUrl("/");

        //开启记住我，默认保存两周
        http.rememberMe().rememberMeParameter("remember");
    }

    //认证
    //密码编码
    //在springSecurity 5.0+ 增加了加密方法
    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication().passwordEncoder(new BCryptPasswordEncoder())
                .withUser("leige").password(new BCryptPasswordEncoder().encode("123456")).roles("vip2","vip3")
                .and()
                .withUser("root").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1","vip2","vip3");
    }
}
```

