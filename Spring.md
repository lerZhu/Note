# Spring

## 1、了解Spring

### 1.1、简介

官网：https://spring.io/

官方下载地址：https://repo.spring.io/release/org/springframework/spring/

GitHub地址：https://github.com/spring-projects/spring-framework



```xml
<!-- https://mvnrepository.com/artifact/org.springframework/spring-webmvc -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.2.0.RELEASE</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.springframework/spring-jdbc -->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>5.2.0.RELEASE</version>
</dependency>
```



### 1.2、优点

- 开源，免费的框架
- 轻量级的非入侵式的框架
- 控制反转（IOC）、面向切片编程（AOP）
- 支持事务的处理，对框架整合的支持



### 1.3、组成

![image-20210328090924609](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210328090924609.png)



### 1.4、拓展

现代化的java开发就是基于Spring开发

- Spring Boot
  - 一个快速开发的脚手架
  - 基于SpringBoot可以快速的开发单个微服务
  - 约定>配置
- Spring Cloud
  - SpringCloud是基于SpringBoot实现的



大多数公司都在使用SpringBoot进行快速开发，学习SpringBoot的前提，需要完全掌握Spring以及SpringMVC



弊端：发展了太久之后，违背了原来的理念，配置十分繁琐，人称配置地狱



## 2、IoC理论推导

1. UserDao接口
2. UserDaoImpl实现类
3. UserService业务接口
4. UserServiceImpl业务实现类

在之前的业务中，用户的需求可能会影响我们原来的代码，我们需要根据用户的需求去修改源代码，如果程序的代码量很大，修改的代价很昂贵

![image-20210328094000126](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210328094000126.png)

我们使用一个Set接口实现

```java
private UserDao userDao;

//利用set进行动态实现值得注入
public void setUserDao(UserDao userDao) {
    this.userDao = userDao;
}
```

- 之前是程序主动创建对象，控制权在程序员手上
- 使用set注入后，程序不再具有主动性，被动接收对象



这种思想，从本质上解决了问题，程序员不用再去管理对象的创建，系统的耦合性大大降低，可以更加专注在业务的实现上。这是IOC的原型

![image-20210328094009412](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210328094009412.png)



### IoC本质

**控制反转IoC（Inversion of Control），是一种设计思想，DI（依赖注入）是实现IoC的一种方法。**没有IoC的程序中，我们使用面向对象编程，对象的创建与对象间的依赖关系完全硬编码在程序中，对象的创建由程序自己控制，控制反转后把对象的创建移交给第三方，控制反转就是获得依赖对象的方式反转了。

采用xml方式配置Bean的时候，Bean的定义信息是和实现分离的，而采用注解的方式可以把两者合为一体，Bean的定义信息直接以注解的形式定义在实现类中，从而达到了零配置的目的。

**控制反转是一种通过描述（XML或注解）并通过第三方去生产或者获取特定对象的方式，在Spring中实现控制反转的是IoC容器，其实现方法是依赖注入（Dependency Injection，DI）**



## 3、HelloSpring

### 实体类

```java
public class Hello {

    private String str;

    public String getStr() {
        return str;
    }

    public void setStr(String str) {
        this.str = str;
    }

    @Override
    public String toString() {
        return "Hello{" +
                "str='" + str + '\'' +
                '}';
    }
}
```

### 配置文件

```xml
    <!--使用Spring来创建对象

   类型 变量名 = new 类型();

    bean = 对象    new Hello()

    id = 变量名
    class = new 的对象
    property 相当于给对象中的属性设置一个值
    -->
    <bean id="hello" class="com.lei.pojo.Hello">
        <property name="str" value="Spring"/>
    </bean>
```

### 测试

```java
public class MyTest {
    public static void main(String[] args) {
        //获取Spring的上下文对象
        ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
        //我们的对象现在都在Spring中管理，我们要使用，直接取
        Hello hello = (Hello) context.getBean("hello");
        System.out.println(hello.toString());
    }
}
```

### 思考

- Hello对象是谁创建

  Hello对象是由Spring创建

- Hello对象的属性是怎么设置的

  Hello对象的属性是由Spring容器设置的

这个过程就叫控制反转

控制：谁来控制对象的创建，传统应用程序的对象是由程序本身控制创建的，使用Spring后，对象是由Spring来创建的

反转：程序本身不创建对象，而变成被动的接收对象

依赖注入：就是利用set方法来进行注入

IoC是一种编程思想，由主动的编程变成被动的接收

可以通过new ClassPathXmlApplicationContext去浏览底层源码

**所谓IoC，就是：对象有Spring来创建，管理，装配**



## 4、IoC创建对象的方式

1. 使用无参构造创建对象，默认实现

   ```xml
   <bean id="user" class="com.lei.pojo.User">
       <property name="name" value="磊哥"/>
   </bean>
   ```

2. 建设我们要使用有参构造创建对象

   1. 下标赋值

      ```xml
      <bean id="user" class="com.lei.pojo.User">
          <constructor-arg index="0" value="磊哥"/>
      </bean>
      ```

   2. 通过类型创建【不推荐使用】

      ```xml
      <bean id="user" class="com.lei.pojo.User">
          <constructor-arg type="java.lang.String" value="磊哥"/>
      </bean>
      ```

   3. 直接通过参数名

      ```xml
      <bean id="user" class="com.lei.pojo.User">
          <constructor-arg name="name" value="磊哥"/>
      </bean>
      ```



在配置文件加载的时候，容器中管理的对象就以及初始化了



## 5、Spring配置

### 5.1、别名

```xml
<!--    如果添加了别名，我们也可以使用别名来获取这个对象-->
    <alias name="user" alias="userNew"/>
```

仍然可以通过原名来获取对象

### 5.2、Bean的配置

id ：bean的唯一标识符，相当于对象名

class：bean对象所对应的全限定名：包名+类名

name：也是别名，而且name可以取多个别名

```xml
<bean id="userT" class="com.lei.pojo.User" name="user2 user3">
    <property name="name" value="磊哥"/>
</bean>
```

### 5.3、import

一般用于团队开发使用，他可以将多个配置文件，导入合并为一个



## 6、DI依赖注入

### 6.1、构造器注入

### 6.2、Set方式注入【重点】

- 依赖注入：Set注入
  - 依赖：bean对象的创建依赖于容器
  - 注入：bean对象中的所有属性由容器注入



【环境搭建】

1. 复杂类型

   ```java
   public class Address {
       private String address;
   
       public String getAddress() {
           return address;
       }
   
       public void setAddress(String address) {
           this.address = address;
       }
   }
   ```

2. 真实测试对象

   ```java
   public class Student {
       private String name;
       private Address address;
       private String[] book;
       private List<String> hobbies;
       private Map<String,String> card;
       private Set<String> games;
       private String wife;
       private Properties info;
   }
   ```

3. beans.xml

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://www.springframework.org/schema/beans
           https://www.springframework.org/schema/beans/spring-beans.xsd">
   
       <bean id="address" class="com.lei.pojo.Address"/>
   
       <bean id="student" class="com.lei.pojo.Student">
           <!--第一种普通值注入，value-->
           <property name="name" value="磊哥"/>
           <!--第二种bean注入，ref-->
           <property name="address" ref="address"/>
           <!--数组-->
           <property name="book">
               <array>
                   <value>红楼梦</value>
                   <value>西游记</value>
                   <value>水浒传</value>
                   <value>三国演义</value>
               </array>
           </property>
           <!--list-->
           <property name="hobbies">
               <list>
                   <value>听歌</value>
                   <value>看电影</value>
               </list>
           </property>
           <!--map-->
           <property name="card">
               <map>
                   <entry key="身份证" value="111111111111111111"/>
                   <entry key="银行卡" value="62737819274"/>
               </map>
           </property>
           <!--Set-->
           <property name="games">
               <set>
                   <value>仙剑奇侠传</value>
                   <value>古剑奇谭</value>
                   <value>轩辕剑</value>
               </set>
           </property>
           <!--Set-->
           <property name="wife">
               <null/>
           </property>
           <!--Properties-->
           <property name="info">
               <props>
                   <prop key="学号">41092443832</prop>
               </props>
           </property>
       </bean>
   
   </beans>
   ```

4. 测试类

### 6.3、拓展方式

可以使用p命名空间和c命名空间进行注入

官方解释：https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-p-namespace

https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-c-namespace

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:p="http://www.springframework.org/schema/p"
       xmlns:c="http://www.springframework.org/schema/c"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <!--p命名空间注入，可以注入属性的值-->
    <bean id="user" class="com.lei.pojo.User" p:name="磊哥" p:age="18"/>

    <!--c命名空间注入，通过构造器注入-->
    <bean id="user2" class="com.lei.pojo.User" c:name="磊子哥" c:age="19"/>

</beans>
```



注意：p命名空间和c命名空间不能直接使用，需要导入约束

```xml
xmlns:p="http://www.springframework.org/schema/p"
xmlns:c="http://www.springframework.org/schema/c"
```

### 6.4、bean的作用域

| Scope                                                        | Description                                                  |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [singleton](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes-singleton) | (Default) Scopes a single bean definition to a single object instance for each Spring IoC container. |
| [prototype](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes-prototype) | Scopes a single bean definition to any number of object instances. |
| [request](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes-request) | Scopes a single bean definition to the lifecycle of a single HTTP request. That is, each HTTP request has its own instance of a bean created off the back of a single bean definition. Only valid in the context of a web-aware Spring `ApplicationContext`. |
| [session](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes-session) | Scopes a single bean definition to the lifecycle of an HTTP `Session`. Only valid in the context of a web-aware Spring `ApplicationContext`. |
| [application](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-scopes-application) | Scopes a single bean definition to the lifecycle of a `ServletContext`. Only valid in the context of a web-aware Spring `ApplicationContext`. |
| [websocket](https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#websocket-stomp-websocket-scope) | Scopes a single bean definition to the lifecycle of a `WebSocket`. Only valid in the context of a web-aware Spring `ApplicationContext`. |

1. 单列模式（Spring默认机制）

   ![image-20210328222137735](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210328222137735.png)

   ```xml
   <bean id="user2" class="com.lei.pojo.User" c:name="磊子哥" c:age="19" scope="singleton"/>
   ```

2. 原型模式（每次从容器中get的时候都会产生新对象）

![image-20210328222147834](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210328222147834.png)

```xml
<bean id="user2" class="com.lei.pojo.User" c:name="磊子哥" c:age="19" scope="prototype"/>
```

3.其余的request、session、application、websocket这些只能在web中使用



## 7、bean的自动装配

- 自动装配是Spring满足bean依赖的一种方式
- Spring会在上下文中自动寻找，并自动给bean装配属性



在Spring中有三种装配的方式

- 在xml中显示的配置
- 在java中显示配置
- 隐式的自动装配bean



### 7.1、测试

环境搭建：一个人有两个宠物

```java
public class Person {

    private Cat cat;
    private Dog dog;
    private String name;
}

public class Dog {
    public void shout() {
        System.out.println("汪汪汪~~~");
    }
}

public class Cat {
    public void shout() {
        System.out.println("喵喵喵~~~");
    }
}
```

```xml
<bean id="cat" class="com.lei.pojo.Cat"/>

<bean id="dog" class="com.lei.pojo.Dog"/>

<bean id="person" class="com.lei.pojo.Person" autowire="byName">
    <property name="name" value="磊哥"/>
    <property name="cat" ref="cat"/>
    <property name="dog" value="dog"/>
</bean>
```

### 7.2、ByName自动装配

```xml
<bean id="cat" class="com.lei.pojo.Cat"/>
<bean id="dog" class="com.lei.pojo.Dog"/>
<!--
byname：会自动在容器上下文中查找，和自己对象set方法后面的值对应的beanid
-->
<bean id="person" class="com.lei.pojo.Person" autowire="byName">
    <property name="name" value="磊哥"/>
</bean>
```

需要保证所有bean的id唯一，并且这个bean需要和自动注入的属性的set方法的值一致。

### 7.3、ByType自动装配

需要保证所有bean的class唯一，并且这个bean需要和自动注入的属性的类型一致。

```xml
<bean id="cat" class="com.lei.pojo.Cat"/>
<bean id="dog11" class="com.lei.pojo.Dog"/>
<!--
bytype: 会自动在容器上下文中查找，和自己对象类型相同的bean
-->
<bean id="person" class="com.lei.pojo.Person" autowire="byType">
    <property name="name" value="磊哥"/>
</bean>
```

### 7.4、使用注解实现自动装配

jdk1.5支持注解，spring2.5就支持注解

使用注解须知

1. 导入约束

2. 配置注解的支持

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
           https://www.springframework.org/schema/beans/spring-beans.xsd
           http://www.springframework.org/schema/context
           https://www.springframework.org/schema/context/spring-context.xsd">
   
       <context:annotation-config/>
   
   </beans>
   ```





#### @Autowired

直接在属性上使用，也可以在set方法上使用

使用Autowire我们可以不用编写Set方法，前提这个自动装配的属性在IoC（Spring）容器中存在且符合名字byname

```java
public class Person {

    //如果显示定义了Autowired的required属性为false，说明这个对象可以为null，否则不允许为空
    @Autowired(required = false)
    private Cat cat;
    @Autowired
    private Dog dog;
    private String name;
}
```



如果Autowired自动装配的环境比较复杂，自动装配无法通过一个注解@Autowired完成的时候，可以使用@Qualifier(value = "xxx")去配置@Autowired的使用，指定唯一一个bean对象注入

```java
public class Person {
    @Autowired
    private Cat cat;
    
    @Autowired
    @Qualifier(value = "dog")
    private Dog dog;
    private String name;
}
```

#### @Resource

```java
public class Person {
    @Resource
    private Cat cat;
    
    @Resource(name = "dog")
    private Dog dog;
    private String name;
}
```



@Resource和@Autowired的区别

- 都是自动装配，都可以放在属性字段上
- @Autowired通过bytype方式实现，这个对象必须存在
- @Resource默认通过byname的方式实现，如果找不到名字，通过bytype实现。如果两个都找不到，就报错
- 执行顺序不同



## 8、使用注解开发

在Spring4之后，使用注解开发，必须保证aop的包导入了

![image-20210329092542817](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210329092542817.png)

使用注解需要导入context约束，增加注解的支持

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        https://www.springframework.org/schema/context/spring-context.xsd">

    <context:annotation-config/>

</beans>
```



### 1.bean

@Component

```java
//等价于<bean id="user" class="com.lei.pojo.User"/>
@Component
public class User {

    public String name = "磊哥";

}
```

### 2.属性如何注入

@Value

```java
@Value("磊哥")
public String name;
```

```java
public String name;
@Value("磊哥")
public void setName(String name) {
    this.name = name;
}
```

### 3.衍生的注解

@Component有几个衍生注解，我们在web开发中会按照MVC三层架构分层

- dao【@Repository】
- service【@Service】
- controller【@Controller】

这四个注解功能是一样的，都是代表将某个类注册到Spring中，装配Bean

### 4.自动装配

见上

### 5.作用域

```java
@Component
@Scope("singleton")
public class User {
    public String name;
    @Value("磊哥")
    public void setName(String name) {
        this.name = name;
    }
}
```

### 6.小结

xml与注解

- xml更加万能，适用于任何场合，维护简单
- 注解 不是自己的类使用不了，维护相对复杂

xml与注解的最佳实践

- xml用来管理bean

- 注解只负责完成属性的注入

- 在使用的过程中，只需要注意一个问题：必须让注解生效，就需要开启注解的支持

  ```xml
  <!--指定要扫描的包，这个包下的注解就会生效-->
  <context:component-scan base-package="com.lei.*"/>
  <context:annotation-config/>
  ```



## 9、使用java的方式配置Spring

完全不使用Spring的xml配置，全权交给Java来做

实体类

```java
package com.lei.pojo;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;

/**
 * @author zhulei
 * @create 2021-03-29 10:18
 */
//这个注解的意思是这个类被Spring接管了，注册到了容器中
@Component
public class User {

    private String name;

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                '}';
    }

    public String getName() {
        return name;
    }

    //属性注入值
    @Value("磊哥")
    public void setName(String name) {
        this.name = name;
    }
}

```

配置类

```java
@Configuration
@ComponentScan("com.lei.pojo")
@Import(MyConfig2.class)
public class MyConfig {

    //注册一个bean，相当于之前写得一个bean标签
    //这个方法的名字就相当于bean标签中的id属性
    //返回值，就相当于class属性
    @Bean
    public User getUser() {
        return new User();
    }

}

```

测试类

```java
import com.lei.config.MyConfig;
import com.lei.pojo.User;
import org.junit.Test;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.AnnotationConfigApplicationContext;

/**
 * @author zhulei
 * @create 2021-03-29 10:22
 */
public class MyTest {

    @Test
    public void test1() {
        //如果完全使用了配置类方式去做，我们就只能通过AnnotationConfigApplicationContext上下文来获取容器，通过配置类的class对象加载
        ApplicationContext context = new AnnotationConfigApplicationContext(MyConfig.class);
        User getUser = context.getBean("getUser", User.class);

        System.out.println(getUser.getName());
    }
}
```

这种纯java的配置方式，在SpringBoot中随处可见



## 10、代理模式

为什么要学习代理模式？以为这就是SpringAOP的底层。

代理模式的分类：

- 静态代理
- 动态代理

![image-20210329145207863](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210329145207863.png)



### 10.1、静态代理

角色分析：

- 抽象角色：一般会使用接口或抽象类来解决
- 真实角色：被代理的角色
- 代理角色：代理真实角色，代理真实角色后，我们一般会做一些附属操作
- 客户：访问代理对象的人



代码步骤：

1. 接口

   ```java
   //租房
   public interface Rent {
       public void rent();
   }
   ```

2. 真实角色

   ```java
   public class Host implements Rent{
       public void rent() {
           System.out.println("房东要出租房子");
       }
   }
   ```

3. 代理角色

   ```java
   public class Proxy implements Rent{
       private Host host;
   
       public Proxy() {
       }
   
       public Proxy(Host host) {
           this.host = host;
       }
   
       public void rent() {
           seeHouse();
           host.rent();
           fare();
           hetong();
       }
   
       //看房
       public void seeHouse() {
           System.out.println("中介带你看房");
       }
   
       //收中介费
       public void fare() {
           System.out.println("收中介费");
       }
   
       //签合同
       public void hetong() {
           System.out.println("签租赁合同");
       }
   }
   ```

4. 客户端访问代理角色

   ```java
   public class Client {
       public static void main(String[] args) {
           //房东要租房子
           Host host = new Host();
           //代理，中介帮房东租房子，代理角色一般会有一些附属操作
           Proxy proxy = new Proxy(host);
           //不用面对房东，直接找中介租房
           proxy.rent();
       }
   }
   ```



代理模式的好处：

- 可以使真实角色的操作更加纯粹，不用去关注一些公共的业务
- 公共业务交给代理角色，实现了业务的分工
- 公共业务发生扩展的时候，方便集中管理

缺点：

- 一个真实角色就会产生一个代理角色；代码量会翻倍



### 10.2、加深理解

![image-20210329152723355](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210329152723355.png)



### 10.3、动态代理

- 动态代理和静态代理角色一样
- 动态代理的代理类是动态生产的，不是我们直接写好的
- 动态代理分为两大类：基于接口的动态代理，基于类的动态代理
  - 基于接口：jdk的动态代理【用这个】
  - 基于类：cglib
  - java字节码实现：javassist



需要了解两个类：Proxy：代理，InvocationHandler：调用处理程序



动态代理的好处：

- 可以使真实角色的操作更加纯粹，不用去关注一些公共的业务
- 公共业务交给代理角色，实现了业务的分工
- 公共业务发生扩展的时候，方便集中管理
- 一个动态代理类代理的是一个接口，一般就是对应的一类业务
- 一个动态代理类可以代理多个类，只有实现同一个接口即可



## 11、AOP

### 11.1、什么是AOP

AOP（Aspect Oriented Programming）意为面向切面编程，通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。AOP是OOP的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，是函数式编程的一种衍生范型。利用AOP可以对业务逻辑的各个部分进行分离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重复性，同时提高开发效率。

![image-20210329163958922](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210329163958922.png)



### 11.2、AOP在Spring中的作用

提供声明式事务，允许用户自定义切面

- 横切关注点：跨越应用程序多个模块的方法或功能，即是，与我们业务逻辑无关的，但是我们需要关注的部分，就是横切关注点，如日志、安全、缓存、事务等等
- 切面（ASPECT）：横切关注点被模块化的特殊对象，它是一个类
- 通知（Advice）：切面必须要完成的工作。即，它是类中的一个方法
- 目标（Target）：被通知的对象
- 代理（Proxy）：向目标对象应用通知之后创建的对象
- 切入点（PointCut）：切面通知执行的”地点“的定义
- 连接点（JoinCut）：与切入点匹配的执行点

![image-20210329164625514](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210329164625514.png)



### 11.3、使用Spring实现AOP

【重点】使用AOP织入，需要导入一个依赖包

```xml
<!-- https://mvnrepository.com/artifact/org.aspectj/aspectjweaver -->
<dependency>
    <groupId>org.aspectj</groupId>
    <artifactId>aspectjweaver</artifactId>
    <version>1.9.4</version>
</dependency>
```



方式一：使用Spring的API接口【主要SpringAPI接口实现】

1. 接口

   ```java
   public interface UserService {
       void add();
       void delete();
       void update();
       void select();
   }
   ```

2. 实现类

   ```java
   public class UserServiceImpl implements UserService{
       public void add() {
           System.out.println("增加了一个用户");
       }
   
       public void delete() {
           System.out.println("删除了一个用户");
       }
   
       public void update() {
           System.out.println("修改了一个用户");
       }
   
       public void select() {
           System.out.println("查询了一个用户");
       }
   }
   ```

3. 日志操作（增强操作）

   ```java
   public class log implements MethodBeforeAdvice {
   
       //method:要执行的目标对象的方法
       //args：参数
       //target：目标对象
       public void before(Method method, Object[] args, Object target) throws Throwable {
           System.out.println(target.getClass().getName()+"的"+method.getName());
       }
   }
   ```

   ```java
   public class AfterLog implements AfterReturningAdvice {
   
       //returnValue:返回值
       public void afterReturning(Object returnValue, Method method, Object[] objects, Object o1) throws Throwable {
           System.out.println("执行了" + method.getName() + "返回结果为" + returnValue);
       }
   }
   ```

4. 配置文件

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xmlns:aop="http://www.springframework.org/schema/aop"
          xsi:schemaLocation="http://www.springframework.org/schema/beans
           https://www.springframework.org/schema/beans/spring-beans.xsd
           http://www.springframework.org/schema/aop
           https://www.springframework.org/schema/aop/spring-aop.xsd">
   
       <!--注册bean-->
       <bean id="userService" class="com.lei.service.UserServiceImpl"/>
       <bean id="log" class="com.lei.log.log"/>
       <bean id="afterLog" class="com.lei.log.AfterLog"/>
   
       <!--使用原生的api接口-->
       <!--配置aop:需要导入aop的约束需要-->
       <aop:config>
           <!--切入点-->
           <aop:pointcut id="pointcut" expression="execution(* com.lei.service.UserServiceImpl.*(..))"/>
           <!--执行环绕增强-->
           <aop:advisor advice-ref="log" pointcut-ref="pointcut"/>
           <aop:advisor advice-ref="afterLog" pointcut-ref="pointcut"/>
       </aop:config>
   
   </beans>
   ```

5. 测试

   ```java
   public class MysTest {
       public static void main(String[] args) {
           ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
           UserService userService = context.getBean("userService", UserService.class);
           userService.add();
       }
   }
   ```



方式二：自定义来实现AOP【主要是切面】

1. diy类

   ```java
   public class DiyPointCut {
   
        public void before(){
            System.out.println("方法执行前");
        }
   
        public void after(){
            System.out.println("方法执行后");
        }
   
   }
   ```

2. 配置文件

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xmlns:aop="http://www.springframework.org/schema/aop"
          xsi:schemaLocation="http://www.springframework.org/schema/beans
           https://www.springframework.org/schema/beans/spring-beans.xsd
           http://www.springframework.org/schema/aop
           https://www.springframework.org/schema/aop/spring-aop.xsd">
   
       <!--注册bean-->
       <bean id="userService" class="com.lei.service.UserServiceImpl"/>
       <bean id="log" class="com.lei.log.log"/>
       <bean id="afterLog" class="com.lei.log.AfterLog"/>
   
       <!--方式二-->
       <bean id="diy" class="com.lei.diy.DiyPointCut"/>
       <aop:config>
           <!--自定义切面，ref引用的类-->
           <aop:aspect ref="diy">
               <!--切入点-->
               <aop:pointcut id="point" expression="execution(* com.lei.service.UserServiceImpl.*(..))"/>
               <!--通知-->
               <aop:before method="before" pointcut-ref="point"/>
               <aop:after method="after" pointcut-ref="point"/>
           </aop:aspect>
       </aop:config>
   
   </beans>
   ```



方式三：使用注解实现

```java
@Aspect // 标注这个类是一个切面
public class AnnotationPointCut {

    @Before("execution(* com.lei.service.UserServiceImpl.*(..))")
    public void before() {
        System.out.println("方法执行前");
    }

    @After("execution(* com.lei.service.UserServiceImpl.*(..))")
    public void after() {
        System.out.println("方法执行后");
    }

    //在环绕增强中，我们可以给定一个参数，代表我们要获取处理切入的点
    @Around("execution(* com.lei.service.UserServiceImpl.*(..))")
    public void around(ProceedingJoinPoint joinPoint) throws Throwable {
        System.out.println("环绕前");
        Object proceed = joinPoint.proceed();
        System.out.println("环绕后");
    }
}
```

```xml
<!--方式三-->
<bean id="annotationPointCut" class="com.lei.diy.AnnotationPointCut"/>
<!--开启注解支持-->
<aop:aspectj-autoproxy/>
```



## 12、整合Mybatis

步骤：

1. 导入相关jar包

   - junit

     ```xml
     <dependency>
         <groupId>junit</groupId>
         <artifactId>junit</artifactId>
         <version>4.12</version>
     </dependency>
     ```

   - mybatis

     ```xml
     <dependency>
         <groupId>org.mybatis</groupId>
         <artifactId>mybatis</artifactId>
         <version>3.5.2</version>
     </dependency>
     ```

   - mysql数据库

     ```xml
     <dependency>
         <groupId>mysql</groupId>
         <artifactId>mysql-connector-java</artifactId>
         <version>5.1.46</version>
     </dependency>
     ```

   - spring相关

     ```xml
     <dependency>
         <groupId>org.springframework</groupId>
         <artifactId>spring-webmvc</artifactId>
         <version>5.2.0.RELEASE</version>
     </dependency>
     <dependency>
         <groupId>org.springframework</groupId>
         <artifactId>spring-jdbc</artifactId>
         <version>5.2.0.RELEASE</version>
     </dependency>
     ```

   - aop织入

     ```xml
     <dependency>
         <groupId>org.aspectj</groupId>
         <artifactId>aspectjweaver</artifactId>
         <version>1.9.4</version>
     </dependency>
     ```

   - mybatis-spring

     ```xml
     <dependency>
         <groupId>org.mybatis</groupId>
         <artifactId>mybatis-spring</artifactId>
         <version>2.0.2</version>
     </dependency>
     ```

2. 编写配置文件

3. 测试



### 12.1、回忆Mybatis

1. 编写实体类
2. 编写核心配置文件
3. 编写接口
4. 编写Mapper.xml
5. 测试



### 12.2、Mybatis-Spring

#### 第一种整合方法

![image-20210330231101776](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210330231101776.png)

1. 编写数据源配置

   ![image-20210330231047865](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210330231047865.png)

   ```xml
   <!--    DataSource:使用Spring的数据源替换Mybatis的配置
           我们这里使用Spring提供的jdbc
   -->
   <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
       <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
       <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=true&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
       <property name="username" value="root"/>
       <property name="password" value="9468"/>
   </bean>
   ```

2. SQLSessionFactory

   ![image-20210330231042456](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210330231042456.png)

   ```xml
   <!--    sqlSessionFactory-->
   <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
       <property name="dataSource" ref="dataSource" />
       <!--绑定mybatis配置文件-->
       <property name="configLocation" value="classpath:mybatis-config.xml"/>
       <property name="mapperLocations" value="classpath:com/lei/mapper/UserMapper.xml"/>
   </bean>
   ```

3. SQLSessionTemplate

   ![image-20210330231039318](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210330231039318.png)

   ```xml
   <!--SqlSessionTemplate就是我们使用的sqlSession-->
   <bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
       <!--只能使用构造器注入，没有set方法-->
       <constructor-arg index="0" ref="sqlSessionFactory"/>
   </bean>
   ```

4. 需要给接口加实现类

   ![image-20210330231017267](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210330231017267.png)

   ```java
   package com.lei.mapper;
   import com.lei.pojo.User;
   import org.mybatis.spring.SqlSessionTemplate;
   import java.util.List;
   
   public class UserMapperImpl implements UserMapper {
       //所有操作，原来都使用sqlSession来执行，现在全部使用sqlSessionTemplate
       private SqlSessionTemplate sqlSessionTemplate;
   
       public void setSqlSessionTemplate(SqlSessionTemplate sqlSessionTemplate) {
           this.sqlSessionTemplate = sqlSessionTemplate;
       }
   
       public List<User> selectUser() {
           UserMapper mapper = sqlSessionTemplate.getMapper(UserMapper.class);
           return mapper.selectUser();
       }
   }
   ```

5. 将自己写的实现类注入到Spring中，测试使用即可

   ![image-20210330231003079](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210330231003079.png)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/aop
        https://www.springframework.org/schema/aop/spring-aop.xsd">
    
    <import resource="spring-dao.xml"/>

    <bean id="userMapper" class="com.lei.mapper.UserMapperImpl">
        <property name="sqlSessionTemplate" ref="sqlSession"/>
    </bean>

</beans>
```



#### 第二种整合方法

继承SqlSessionDaoSupport

`SqlSessionDaoSupport` 是一个抽象的支持类，用来为你提供 `SqlSession`。调用 `getSqlSession()` 方法你会得到一个 `SqlSessionTemplate`，之后可以用于执行 SQL 方法，就像下面这样:

```java
public class UserMapperImpl2 extends SqlSessionDaoSupport implements UserMapper {
    public List<User> selectUser() {
        return getSqlSession().getMapper(UserMapper.class).selectUser();
    }
}
```

```xml
<bean id="userMapper2" class="com.lei.mapper.UserMapperImpl2">
    <property name="sqlSessionFactory" ref="sqlSessionFactory"/>
</bean>
```



## 13、声明式事务

### 1、回顾事务

- 把一组业务当成一个业务来做，要么都成功，要么都失败
- 事务在项目中十分重要，涉及到数据的一致性问题
- 确保完整性和一致性



事务的ACID原则

- 原子性
- 一致性
- 隔离性
  - 多个业务可能操作同一个资源，防止数据损坏
- 持久性
  - 事务一旦提交，系统无论发生什么问题，结果都不会被影响，被持久化的写到存储器中



### 2、Spring中的事务管理

- 声明式事务：AOP

  ```xml
  <!--配置声明式事务-->
  <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
      <constructor-arg ref="dataSource" />
  </bean>
  
  <!--结合AOP实现事务的织入-->
  <!--配置事务通知-->
  <tx:advice id="txAdvice" transaction-manager="transactionManager">
      <!--给哪些方法配置事务-->
      <!--配置事务的传播特性-->
      <tx:attributes>
          <tx:method name="add" propagation="REQUIRED"/>
          <tx:method name="delete" propagation="REQUIRED"/>
          <tx:method name="update" propagation="REQUIRED"/>
          <tx:method name="query" read-only="true"/>
          <tx:method name="*" propagation="REQUIRED"/>
      </tx:attributes>
  </tx:advice>
  
  <!--配置事务切入-->
  <aop:config>
      <aop:pointcut id="txPoint" expression="execution(* com.lei.mapper.*.*(..))"/>
      <aop:advisor advice-ref="txAdvice" pointcut-ref="txPoint"/>
  </aop:config>
  ```

- 编程式事务：需要在代码中进行事务的管理





为什么需要事务？

- 不配置事务，可能存在数据提交不一致的情况
- 如果不再Spring中配置声明式事务，我们就需要在代码中手动配置
- 在项目的开发中十分重要，涉及到事务的完整性和一致性

















