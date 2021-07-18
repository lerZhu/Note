# Mybatis

环境：

- jdk 1.8
- Mysql 5.7
- maven 3.6.3
- IDEA

最好方式：看官网https://mybatis.org/mybatis-3/zh/index.html

## 1、简介

### 1.1、什么是MyBatis

![image-20210324131959610](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324131959610.png)

- MyBatis 是一款优秀的**持久层框架**
- 它支持自定义 SQL、存储过程以及高级映射
- MyBatis 免除了几乎所有的 JDBC 代码以及设置参数和获取结果集的工作
- MyBatis 可以通过简单的 XML 或注解来配置和映射原始类型、接口和 Java POJO（Plain Old Java Objects，普通老式 Java 对象）为数据库中的记录。
- MyBatis 本是apache的一个开源项目iBatis, 2010年这个项目由apache software foundation 迁移到了google code，并且改名为MyBatis 。
- 2013年11月迁移到Github。

如何获得mybatis

- Maven

  ```xml
  <!-- https://mvnrepository.com/artifact/org.mybatis/mybatis -->
  <dependency>
      <groupId>org.mybatis</groupId>
      <artifactId>mybatis</artifactId>
      <version>3.5.2</version>
  </dependency>
  
  ```

  

- GitHub：https://github.com/mybatis/mybatis-3/releases

- 中文文档：https://mybatis.org/mybatis-3/zh/index.html

### 1.2、持久化

数据持久化

- 持久化就是将程序在持久状态和瞬时状态转化的过程
- 内存：**断电即失**

- 数据库（JDBC），io文件持久化
- 生活：冷藏、罐头

**为什么需要持久化**：

- 有一些对象不能丢掉
- 内存太贵



###  1.3、持久层

DAO、Service、Controller......

- 完成持久化工作的代码块
- 层是界限明显的



### 1.4、为什么需要MyBatis

- 方便
- 帮助程序员将数据存入数据库中
- 传统的JDBC代码太复杂。简化、框架。自动化
- 不用MyBatis也可以。更容易上手。
- 优点：
  - 简单易学
  - 灵活
  - sql和代码的分离，提高了可维护性
  - 提供映射标签，支持对象与数据库的orm字段关系映射
  - 提供对象关系映射标签，支持对象关系组建维护
  - 提供xml标签，支持编写动态sql



## 2、第一个MyBatis程序

### 2.1、搭建环境

搭建数据库

```sql
USE `mybatis`;

CREATE TABLE `user`(
	`id` INT(20) NOT NULL PRIMARY KEY,
	`name` VARCHAR(30) DEFAULT NULL,
	`pwd` VARCHAR(30) DEFAULT N`user`ULL	
)ENGINE=INNODB DEFAULT CHARSET=utf8;

INSERT INTO `user`(`id`,`name`,`pwd`) VALUES
(1,'磊哥','123456'),
(2,'张三','123456'),
(3,'李四','123456');
```

新建项目

1. 新建一个普通Maven项目

   ![image-20210324135256561](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324135256561.png)

2. 删除src目录

3. 导入Maven依赖

```xml
<!--导入依赖-->
    <dependencies>
        <!--mysql驱动-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.47</version>
        </dependency>
        <!--mybatis-->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.2</version>
        </dependency>
        <!--junit-->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>
    </dependencies>
```

### 2.2、创建一个模块

- 编写MyBatis核心配置文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<!--configuration核心配置文件-->
<configuration>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=true&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
                <property name="username" value="root"/>
                <property name="password" value="9468"/>
            </dataSource>
        </environment>
    </environments>
</configuration>
```

- 编写MyBatis工具类

```java
//SqlSessionFactory --> SqlSession
public class MybatisUtils {

    private static SqlSessionFactory sqlSessionFactory;

    static {
        try {
            //使用MyBatis第一步：获取SqlSessionFactory对象
            String resource = "mybatis-config.xml";
            InputStream inputStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    //既然有了 SqlSessionFactory，顾名思义，我们可以从中获得 SqlSession 的实例。
    // SqlSession 提供了在数据库执行 SQL 命令所需的所有方法。
    public static SqlSession getSqlSession() {
        return sqlSessionFactory.openSession();
    }

}
```

### 2.3、编写代码

- 实体类

```java
package com.lei.pojo;

/**
 * @author zhulei
 * @create 2021-03-24 14:30
 */
public class User {

    private int id;
    private String name;
    private String pwd;

    public User() {
    }

    public User(int id, String name, String pwd) {
        this.id = id;
        this.name = name;
        this.pwd = pwd;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getPwd() {
        return pwd;
    }

    public void setPwd(String pwd) {
        this.pwd = pwd;
    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", pwd='" + pwd + '\'' +
                '}';
    }
}

```

- DAO接口

  ```java
  public interface UserMapper {
  
      List<User> getUserList();
  
  }
  ```

- 接口实现类   由原来的UserDaoImpl转换为一个Mapper文件

  ```xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <!--namespace绑定一个对应的DAO/Mapper接口-->
  <mapper namespace="com.lei.dao.UserMapper">
      <select id="getUserList" resultType="com.lei.pojo.User">
          select * from mybatis.user
      </select>
  </mapper> 
  ```

### 2.4、测试

注意点：

org.apache.ibatis.binding.BindingException: Type interface com.lei.dao.UserMapper is not known to the MapperRegistry.

**MapperRegistry？**

核心配置文件中注册Mappers

- junit测试

  ```java
  public class UserDaoTest {
  
      @Test
      public void test() {
          //获得sqlSession对象
          SqlSession sqlSession = MybatisUtils.getSqlSession();
  
          //方式一：getMapper
          UserMapper mapper = sqlSession.getMapper(UserMapper.class);
          List<User> userList = mapper.getUserList();
  
          for (User user : userList) {
              System.out.println(user);
          }
  
          //关闭sqlSession
          sqlSession.close();
      }
  
  }
  ```

**maven导出资源问题**

在bulid中配置resours，防止资源导出失败

```xml
<build>
    <resources>
        <resource>
            <directory>src/main/resources</directory>
            <includes>
                <include>**/*.properties</include>
                <include>**/*.xml</include>
            </includes>
        </resource>
        <resource>
            <directory>src/main/java</directory>
            <includes>
                <include>**/*.properties</include>
                <include>**/*.xml</include>
            </includes>
            <filtering>true</filtering>
        </resource>
    </resources>
</build>
```

Cause:com.sun.org.apache.xerces.internal.impl.io.MalformedByteSequenceExcep

在pom.xml中配置

```xml
<properties>
	<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
</properties>
```

![image-20210324153109785](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324153109785.png)

## 3、CRUD

### 1、namespace

namespace中的包名要和Mapper接口的包名一致

### 2、select

选择、查询语句

- id：对应的namespace中的方法名
- resultType：sql语句的返回值 
- parameterType：参数类型

1. 编写接口

   ```java
   //根据id查询用户
       User getUserById(int id);
   ```

2. 编写对应的mapper中的sql语句

   ```xml
   <select id="getUserById" resultType="com.lei.pojo.User" parameterType="int">
           select * from mybatis.user where id = #{id}
       </select>
   ```

3. 测试

   ```java
   @Test
       public void testGetUserById() {
           SqlSession sqlSession = MybatisUtils.getSqlSession();
           UserMapper mapper = sqlSession.getMapper(UserMapper.class);
           User user = mapper.getUserById(1);
           System.out.println(user);
           sqlSession.close();
       }
   ```

   

### 3、insert

### 4、update

### 5、delete

**注意：增删改操作要提交事务才能生效**

1. 编写接口

   ```java
   //添加用户
   int addUser(User user);
   //修改用户
   int updateUser(User user);
   //删除用户
   int deleteUser(int id);
   ```

2. 编写对应的Mapper中的sql语句

   ```xml
   <!--对象中的属性可以直接取-->
       <insert id="addUser" parameterType="com.lei.pojo.User">
           insert into mybatis.user (id,name,pwd) values (#{id},#{name},#{pwd})
       </insert>
   
       <update id="updateUser" parameterType="com.lei.pojo.User">
           update mybatis.user set name = #{name},pwd = #{pwd} where id = #{id};
       </update>
   
       <delete id="deleteUser" parameterType="int">
           delete from mybatis.user where id = #{id};
       </delete>
   ```

3. 测试

   ```java
   //增删改需要提交事务
       @Test
       public void testAddUser() {
           SqlSession sqlSession = MybatisUtils.getSqlSession();
   
           UserMapper mapper = sqlSession.getMapper(UserMapper.class);
   
           mapper.addUser(new User(4,"王五","123456"));
   
           //提交事务
           sqlSession.commit();
   
           sqlSession.close();
       }
   
       //增删改需要提交事务
       @Test
       public void testUpdateUser() {
           SqlSession sqlSession = MybatisUtils.getSqlSession();
   
           UserMapper mapper = sqlSession.getMapper(UserMapper.class);
   
           mapper.updateUser(new User(4,"小狗","123456"));
   
           //提交事务
           sqlSession.commit();
   
           sqlSession.close();
       }
   
       //增删改需要提交事务
       @Test
       public void testDeleteUser() {
           SqlSession sqlSession = MybatisUtils.getSqlSession();
   
           UserMapper mapper = sqlSession.getMapper(UserMapper.class);
   
           mapper.deleteUser(4);
   
           //提交事务
           sqlSession.commit();
   
           sqlSession.close();
       }
   ```

### 6、万能Map

假设，实体类、或者数据库中的表、字段或者参数过多，我们应当考虑使用map

1. 编写接口

   ```java
   int addUser2(Map<String, Object> map);
   ```

2. 编写对应的Mapper中的sql语句

   ```xml
   <insert id="addUser2" parameterType="map">
           insert into mybatis.user (id,name,pwd) values (#{userId},#{userName},#{passWord})
       </insert>
   ```

3. 测试

   ```java
   //增删改需要提交事务
       @Test
       public void testAddUser2() {
           SqlSession sqlSession = MybatisUtils.getSqlSession();
   
           UserMapper mapper = sqlSession.getMapper(UserMapper.class);
   
           Map<String, Object> map = new HashMap<String, Object>();
   
           map.put("userId","4");
           map.put("userName","王五");
           map.put("passWord","123123");
   
           mapper.addUser2(map);
   
           //提交事务
           sqlSession.commit();
   
           sqlSession.close();
       }
   ```

Map传递参数，直接在sql中取出key即可

对象传递参数，直接在sql中取对象的属性即可

只有**一个**基本类型参数的情况下，可以直接在sql中取到

多个参数用Map或**注解**

### 7、模糊查询

1.Java代码执行的时候，传递通配符%%

```java
List<User> userList = mapper.getUserLike("%李%");
```

2.在sql拼接中使用通配符

```xml
<select id="getUserLike" resultType="com.lei.pojo.User">
        select * from mybatis.user where name like "%"#{value}"%"
</select>
```

## 4、配置解析

### 1、核心配置文件

- mybatis-config.xml![image-20210325083345504](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325083345504.png)

- MyBatis 的配置文件包含了会深深影响 MyBatis 行为的设置和属性信息。

  configuration（配置）

  - properties（属性）
  - settings（设置）
  - typeAliases（类型别名）
  - typeHandlers（类型处理器）
  - objectFactory（对象工厂）
  - plugins（插件）
  - environments（环境配置）
    - environment（环境变量）
      - transactionManager（事务管理器）
      - dataSource（数据源）
  - databaseIdProvider（数据库厂商标识）
  - mappers（映射器）

**注意**：在xml中，标签有规定顺序

![image-20210325090249661](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325090249661.png)



### 2、环境配置（environments）

MyBatis 可以配置成适应多种环境。

**不过要记住：尽管可以配置多个环境，但每个 SqlSessionFactory 实例只能选择一种环境。**

学会使用配置多套运行环境。

Mybatis默认的事务管理器是**JDBC**，连接池**POOLED**。

https://mybatis.org/mybatis-3/zh/configuration.html#environments

### 3、△属性（properties）

通过使用properties属性来实现引用配置文件。

这些属性可以在外部进行配置，并可以进行动态替换。你既可以在典型的 Java 属性文件中配置这些属性，也可以在 properties 元素的子元素中设置。【db.properties】

1、编写一个配置文件

db.properties

```properties
driver=com.mysql.jdbc.Driver
url=jdbc:mysql://localhost:3306/mybatis?useSSL=true&useUnicode=true&characterEncoding=UTF-8
username=root
password=9468
```

2、在核心配置文件中引入

```xml
<properties resource="org/mybatis/example/config.properties">
  <property name="username" value="dev_user"/>
  <property name="password" value="F2Fa3!33TYyg"/>
</properties>
```

- 可以直接引入外部文件
- 可以在其中增加属性配置
- 如果两个文件有同一个字段，优先使用外部文件中的配置

### 4、△类型别名（typeAliases）

- 类型别名可为 Java 类型设置一个缩写名字
- 仅用于 XML 配置，意在降低冗余的全限定类名书写

```xml
<typeAliases>
    <typeAlias alias="User" type="com.lei.pojo.User"/>
</typeAliases>
```

```xml
<select id="getUserList" resultType="User">
    select * from mybatis.user
</select>
```

- 也可以指定一个包名，MyBatis 会在包名下面搜索需要的 Java Bean，比如：

```xml
<typeAliases>
    <package name="com.lei.pojo"/>
</typeAliases>
```

在没有注解的情况下，会使用 Bean 的首字母小写的非限定类名来作为它的别名。若有注解，则别名为其注解值。

```java
@Alias("author")
public class Author {
    ...
}
```

在实体类比较少的情况下使用第一种方式

实体类较多则使用第二种

### 5、△设置（settings）

![image-20210325093856658](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325093856658.png)

![image-20210325093911415](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325093911415.png)

### 6、其他配置

- typeHandlers（类型处理器）
- objectFactory（对象工厂）
- plugins（插件）

### 7、△映射器（mappers）

MapperRegistry：注册绑定Mapper文件

**方式一：【推荐使用】**

```xml
<!--每一个mapper.xml都需要在Mybatis的核心配置文件中注册-->
<mappers>
    <mapper resource="com/lei/dao/UserMapper.xml"></mapper>
</mappers>
```

方式二：使用class文件绑定注册

```xml
<mappers>
    <mapper class="com.lei.dao.UserMapper"/>
</mappers>
```

注意：

- 接口和他的Mapper配置文件必须同名
- 接口和他的Mapper配置文件必须在同一包下

方式三：使用包扫描

```xml
<mappers>
    <package name="com.lei.dao"/>
</mappers>
```

注意：

- 接口和他的Mapper配置文件必须同名
- 接口和他的Mapper配置文件必须在同一包下

### 8、生命周期和作用域

![image-20210325151937498](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325151937498.png)

作用域和生命周期是至关重要的，因为错误的使用会导致非常严重的**并发问题**。

**SqlSessionFactoryBuilder**

- 一旦创建了 SqlSessionFactory，就不再需要它了
- 局部变量

**SqlSessionFactory**

- 可以理解为数据库连接池
- 一旦被创建就应该在应用的运行期间一直存在，**没有任何理由丢弃它或重新创建另一个实例**
- 因此 SqlSessionFactory 的最佳作用域是**应用作用域**
- 最简单的就是使用单例模式或者静态单例模式。

**SqlSession**

- 连接到连接池的一个请求
- SqlSession 的实例不是线程安全的，因此是不能被共享的，所以它的最佳的作用域是请求或方法作用域
- 使用完后需要赶紧关闭，否则资源被占用

![image-20210325152624490](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325152624490.png)

每一个mapper代表一个具体的业务

## 5、解决属性名和字段名不一致的问题

### 1、问题

数据库中的字段

![image-20210325153332641](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325153332641.png)

属性名

```java
private int id;
private String name;
private String password;
```

测试出现问题

![image-20210325153728362](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210325153728362.png)

解决方案：

起别名

```xml
<select id="getUserById" resultType="user" parameterType="int">
    select id,name,pwd as password from mybatis.user where id = #{id}
</select>
```

不改sql的方法见下

### 2、ResultMap

结果集映射

```java
id	 name	pwd
id	 name	password
```

```xml
<!--结果集映射-->
<resultMap id="UserMap" type="User">
    <!--column数据库中的字段，property实体类中的属性-->
    <result column="id" property="id"/>
    <result column="name" property="name"/>
    <result column="pwd" property="password"/>
</resultMap>

<select id="getUserById" resultMap="UserMap" parameterType="int">
    select * from mybatis.user where id = #{id}
</select>
```

- `resultMap` 元素是 MyBatis 中最重要最强大的元素
- ResultMap 的设计思想是，对简单的语句做到零配置，对于复杂一点的语句，只需要描述语句之间的关系就行了
- `ResultMap` 的优秀之处——你完全可以不用显式地配置它们

## 6、日志

### 6.1、日志工厂

如果数据库操作出现异常，我们需要排错。日志就是最好的助手

曾经：sout，debug

现在：日志工厂

| 设置名  | 描述                                                  | 有效值                                                       | 默认值 |
| :------ | :---------------------------------------------------- | :----------------------------------------------------------- | :----- |
| logImpl | 指定 MyBatis 所用日志的具体实现，未指定时将自动查找。 | SLF4J \| **LOG4J【掌握】** \| LOG4J2 \| JDK_LOGGING \| COMMONS_LOGGING \| **STDOUT_LOGGING 【掌握**】\| NO_LOGGING | 未设置 |

在Mybatis中具体使用哪一个日志实现，在设置中设定

**STDOUT_LOGGING标准日志输出**

在核心配置文件中，配置日志

```xml
    <settings>
        <setting name="logImpl" value="STDOUT_LOGGING"/>
    </settings>
```

![image-20210326092203964](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326092203964.png)

### 6.2、Log4j

什么是Log4j？

- Log4j是Apache的一个开源项目，通过使用Log4j，我们可以控制日志信息输送的目的地是控制台、文件、GUI组件
- 我们可以控制每一条日志的输出格式
- 通过定义每一条日志信息的级别，我们能够更加细致地控制日志的生成过程
- 可以通过一个配置文件来灵活地进行配置，而不需要修改应用的代码

1.先导包

```xml
<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version>
</dependency>
```

2.log4j.properties

```properties
#将等级为DEBUG的日志信息输出到console和file两个目的地，console和file的定义在下面的代码
log4j.rootLogger=DEBUG,console,file

#控制台输出相关设置
log4j.appender.console = org.apache.log4j.ConsoleAppender
log4j.appender.console.Target = System.out
log4j.appender.console.Threshold = DEBUG
log4j.appender.console.layout = org.apache.log4j.PatternLayout
log4j.appender.console.layout.ConversionPattern = [%c]-%m%n

#文件输出相关设置
log4j.appender.file = org.apache.log4j.RollingFileAppender
log4j.appender.file.File = ./log/lei.log
log4j.appender.file.MaxFileSize = 10mb
log4j.appender.file.Threshold = DEBUG
log4j.appender.file.layout = org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern = [%p][%d{yy-MM-dd}][%c]%m%n

#日志输出级别
log4j.logger.org.mybatis = DEBUG
log4j.logger.java.sql = DEBUG
log4j.logger.java.sql.Statement = DEBUG
log4j.logger.java.sql.ResultSet = DEBUG
log4j.logger.java.sql.PreparedStatement = DEBUG
```

3.配置log4j为日志的实现

```xml
<settings>
    <setting name="logImpl" value="LOG4J"/>
</settings>
```

4.log4j的使用。直接测试运行

![image-20210326100502297](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326100502297.png)



**简单使用**

1.在要使用log4j的类中导入包

```java
import org.apache.log4j.Logger;
```

2.日志对象，参数为当前类的class

```java
static Logger logger = Logger.getLogger(UserDaoTest.class);
```

3.日志级别

```java
logger.info("info:进入了testLog4j方法");
logger.debug("debug:进入了testLog4j方法");
logger.error("error:进入了testLog4j方法");
```



### IDEA中log文件显示问号且双击无法打开

在MyBatis项目的xml配置文件里，不要使用package来指定要用的包，不然就会在log文件里产生乱码，从而打不开！
解决方法:typeAliases里使用typeAlias，mapper里使用class或者resource来导包。

## 7、分页

**为什么要分页：**

- 减少数据处理量



### 7.1、使用Limit分页

```sql
select * from user limit startIndex,pageSize;
select * from user limit 3; #[0,3]
```



使用Mybatis实现分页，核心sql

1.接口

```java
    //分页
List<User> getUserByLimit(Map<String,Object> map);
```

2.mapper.xml

```xml
<select id="getUserByLimit" resultMap="UserMap" parameterType="map">
    select * from mybatis.user limit #{startIndex},#{pageSize}
</select>
```

3.测试

```java
@Test
public void testGetUserByLimit() {
    SqlSession sqlSession = MybatisUtils.getSqlSession();
    UserMapper mapper = sqlSession.getMapper(UserMapper.class);
    Map<String, Object> map = new HashMap<String, Object>();
    map.put("startIndex",0);
    map.put("pageSize",2);
    List<User> users = mapper.getUserByLimit(map);
    for (User user : users) {
        System.out.println(user);
    }
    sqlSession.close();
}
```



### 7.2、RowBounds分页

不再使用SQL实现分页

1. 接口

   ```java
   List<User> getUserByRowBounds();
   ```

2. mapper.xml

   ```xml
   <select id="getUserByRowBounds" resultMap="UserMap">
       select * from mybatis.user
   </select>
   ```

3. 测试

   ```java
   @Test
   public void testGetUserByRowBounds() {
       SqlSession sqlSession = MybatisUtils.getSqlSession();
   
       //RowBounds实现
       RowBounds rowBounds = new RowBounds(1, 2);
   
       //通过Java代码层面实现分页
       List<User> users = sqlSession.selectList("com.lei.dao.UserMapper.getUserByRowBounds",null,rowBounds);
       for (User user : users) {
           System.out.println(user);
       }
   
       sqlSession.close();
   }
   ```

### 7.3、分页插件

![image-20210326135214956](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326135214956.png)

了解即可

## 8、使用注解开发

### 8.1、面向接口编程

- 在真正的开发中，很多时候我们会选择面向接口编程
- **根本原因：解耦，可拓展，提高复用，分层开发中，上层不用管具体的实现，大家遵守相同的标准，使开发更容易，规范性更好**
- 在一个面向对象的系统中，系统的各种功能是由许许多多的不同对象协作完成的。在这种情况下，各个对象内部是如何实现自己的，对系统设计人员来讲就不是那么重要
- 各个对象之间的写作关系就成为系统设计的关键，小到不同类之间的通信，大到各个模块之间的交互，在系统设计之初都是要着重考虑的，这也是系统设计的主要工作内容
- 面向接口编程就是按照这种思想来编程



**关于接口的理解**

- 接口从更深层次的理解，应是定义（规范、约束）与实现（名实分离的原则）的分离
- 接口的本身反映了系统设计人员对系统的抽象理解
- 接口应有两类：
  - 第一类是对一个个体的抽象，它可对应为一个抽象体（abstract class）
  - 第二类是一个个体某一方面的抽象，即形成一个抽象面（interface）
- 一个个体可能有多个抽象面。抽象体与抽象面是有区别的



**三个面向区别**

- 面向对象是指，考虑问题时，以对象为单位，考虑他的属性以及方法
- 面向过程是指，考虑问题时，以一个具体的流程（事务过程）为单位，考虑它的实现
- 接口设计与非接口设计是针对复用技术而言的，与面向对象（过程）不是一个问题，更多的体现是对系统整体的架构



### 8.2、使用注解开发

1、在接口上实现

```java
    @Select("select * from user")
    List<User> getUsers();
```

2、在核心配置文件中绑定接口（mybatis-config.xml）

```xml
<!--绑定接口-->
<mappers>
    <mapper class="com.lei.dao.UserMapper"/>
</mappers>
```

3、测试



本质：反射机制实现

底层：动态代理



Mybatis详细执行流程

![图片](https://mmbiz.qpic.cn/mmbiz_png/uJDAUKrGC7LZwwtchlelS8kzAAyVia5uNvhic22X8ahJy5BdOfjy1LlDRfo8Nf3GOAzwALgvriau4SzmXZIhUUd2A/640?wx_fmt=png&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)





### 8.3、注解完成CRUD

可以在工具类创建的时候实现自动提交事务

```java
public static SqlSession getSqlSession() {
    return sqlSessionFactory.openSession(true);
```

编写接口，增加注解

```java
//方法存在多个参数，所有的参数前必须加上@Param注解
@Select("select * from user where id = #{id}")
User getUserById(@Param("id") int id);

@Insert("insert into user(id,name,pwd) values (#{id},#{name},#{password})")
int addUser(User user);

@Update("update user set name=#{name},pwd=#{password} where id=#{id}")
int updateUser(User user);

@Delete("delete from user where id=#{id}")
int deleteUser(@Param("id")int id);
```

测试类

**注意**：必须将接口绑定到核心配置配置文件中



**关于@Prarm()注解**

- 基本类型的参数和String类型，需要加上
- 引用类型不需要加
- 如果只有一个基本类型，可以忽略，但是建议都加上
- 我们在SQL中引用的就是我们这里的@Prarm()中设定的属性名



## 9、Lombok

![image-20210326154539114](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326154539114.png)

使用步骤

1.在IDEA中安装Lombok插件

![image-20210326154950906](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326154950906.png)

2.在项目中导入Lombok的jar包

```xml
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.10</version>
</dependency>
```

3.在实体类上加注解

```java
@Data
@AllArgsConstructor
@NoArgsConstructor
public class User {

    private int id;
    private String name;
    private String password;

}
```

![image-20210326160114427](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326160114427.png)



```java
@Getter and @Setter
@FieldNameConstants
@ToString
@EqualsAndHashCode
@AllArgsConstructor, @RequiredArgsConstructor and @NoArgsConstructor
@Log, @Log4j, @Log4j2, @Slf4j, @XSlf4j, @CommonsLog, @JBossLog, @Flogger, @CustomLog
@Data
@Builder
@SuperBuilder
@Singular
@Delegate
@Value
@Accessors
@Wither
@With
@SneakyThrows
@val
@var
```



```java
@Data：无参构造、get、set、toString、hashcode、equals
@AllArgsConstructor；有参构造
@NoArgsConstructor：无参构造
@EqualsAndHashCode
@ToString
```

## 10、多对一的处理

多对一：

![image-20210326160634877](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326160634877.png)

- 多个学生，对应一个老师
- 对于学生而言，关联     多个学生关联一个老师（多对一）
- 对于老师而言，集合    一个老师有很多学生（一对多）

![image-20210326161900885](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326161900885.png)

SQL：

```sql
CREATE TABLE `teacher` (
  `id` INT(10) NOT NULL,
  `name` VARCHAR(30) NOT NULL,
  PRIMARY KEY(`id`)
)ENGINE=INNODB DEFAULT CHARSET=utf8;

INSERT INTO teacher(`id`,`name`) VALUES (1,'秦老师');

CREATE TABLE `student` (
  `id` INT(10) NOT NULL,
  `name` VARCHAR(30) NOT NULL,
  `tid` INT(10) DEFAULT NULL,
  PRIMARY KEY(`id`),
  KEY `fktid` (`tid`),
  CONSTRAINT `fktid` FOREIGN KEY (`tid`) REFERENCES `teacher`(id)
)ENGINE=INNODB DEFAULT CHARSET=utf8;


INSERT INTO `student` (`id`,`name`,`tid`) VALUES ('1','小明','1');
INSERT INTO `student` (`id`,`name`,`tid`) VALUES ('2','小红','1');
INSERT INTO `student` (`id`,`name`,`tid`) VALUES ('3','小张','1');
INSERT INTO `student` (`id`,`name`,`tid`) VALUES ('4','小李','1');
INSERT INTO `student` (`id`,`name`,`tid`) VALUES ('5','小王','1');
```



### 测试环境搭建

1. 导入lombok

   在pom.xml中配置依赖

   ```xml
   <dependency>
       <groupId>org.projectlombok</groupId>
       <artifactId>lombok</artifactId>
       <version>1.18.10</version>
   </dependency>
   ```

   如果在父工程中已经配置可以跳过

2. 新建实体类Teacher和Student

   ```java
   @Data
   public class Student {
       private int id;
       private String name;
       //学生需要关联一个老师
       private Teacher teacher;
   }
   ```

   ```java
   @Data
   public class Teacher {
   
       private int id;
       private String name;
   
   }
   ```

3. 建立Mapper接口

   ![image-20210326165327495](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326165327495.png)

4. 建立mapper.xml

   ![image-20210326165345415](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210326165345415.png)

5. 在核心配置文件中绑定mapper

   ```xml
   <mappers>
       <mapper class="com.lei.dao.TeacherMapper"/>
       <mapper class="com.lei.dao.StudentMapper"/>
   </mappers>
   ```

6. 测试查询是否成功

   ```java
   @Test
   public void testGetTeacher() {
       SqlSession sqlSession = MybatisUtils.getSqlSession();
       TeacherMapper mapper = sqlSession.getMapper(TeacherMapper.class);
       Teacher teacher = mapper.getTeacher(1);
       System.out.println(teacher);
       sqlSession.close();
   }
   ```



### 按照查询嵌套处理

```xml
<!--
    1.查询所有学生信息
    2.根据查询出来的学生的tid查询对应的老师
    -->
<select id="getStudent" resultMap="StudentTeacher">
    select * from student;
</select>
<resultMap id="StudentTeacher" type="Student">
    <result property="id" column="id"/>
    <result property="name" column="name"/>
    <!--复杂的属性需要单独处理
            对象：association
            集合：collection
        -->
    <association property="teacher" column="tid" javaType="Teacher" select="getTeacher"/>
</resultMap>

<select id="getTeacher" resultType="Teacher">
    select * from teacher where id = #{id};
</select>
```





### 按照结果嵌套处理

```xml
<!--按照结果嵌套处理-->
<select id="getStudent2" resultMap="StudentTeacher2">
    select s.id sid,s.name sname,t.name tname
    from student s,teacher t
    where s.tid = t.id;
</select>

<resultMap id="StudentTeacher2" type="Student">
    <result property="id" column="sid"/>
    <result property="name" column="sname"/>
    <association property="teacher" javaType="Teacher">
        <result property="name" column="tname"/>
    </association>
</resultMap>
```



回顾MySQL多对一查询方式：

- 子查询
- 连表查询



## 11、一对多的处理

比如：一个老师拥有多个学生

对于老师而言，就是一对多的关系



### 测试环境搭建

**实体类**

```java
@Data
public class Teacher {

    private int id;
    private String name;
    //一个老师拥有多个学生
    private List<Student> students;

}
```

```java
@Data
public class Student {
    private int id;
    private String name;
    private int tid;
}
```



### 按结果嵌套查询

```xml
<!--按结果嵌套查询-->
<select id="getTeacher" resultMap="TeacherStudent">
    select s.id sid, s.name sname, t.name tname, t.id tid
    from student s,teacher t
    where s.tid = t.id and t.id = #{tid}
</select>

<resultMap id="TeacherStudent" type="Teacher">
    <result property="id" column="tid"/>
    <result property="name" column="tname"/>
    <!--
        javaType:指定属性的类型
        集合中的泛型类型，我们使用ofType获取
        -->
    <collection property="students" ofType="Student">
        <result property="id" column="sid"/>
        <result property="name" column="sname"/>
        <result property="tid" column="tid"/>
    </collection>
</resultMap>
```



### 按照查询嵌套处理

```xml
<select id="getTeacher2" resultMap="TeacherStudent2">
    select * from teacher where id = #{tid}
</select>

<resultMap id="TeacherStudent2" type="Teacher">
    <collection property="students" javaType="ArrayList" ofType="Student" select="getStudentByTeacherId" column="id"/>
</resultMap>

<select id="getStudentByTeacherId" resultType="Student">
    select * from student where tid = #{tid}
</select>
```



### 小结

1. 关联：association 多对一
2. 集合：collection 一对多
3. javaType  &  ofType
   1. javaType用来指定实体类中属性的类型
   2. ofType用来指定映射到List或集合中的pojo类型，就是泛型中的约束类型



注意点：

- 保证SQL的可读性，尽量保证通俗易懂
- 注意一对多和多对一中，属性名和字段的问题
- 如果问题不好排查错误，可以使用日志，建议使用Log4j



## 12、动态SQL

**什么是动态SQL：根据不同的条件生成不同的SQL语句**

如果你之前用过 JSTL 或任何基于类 XML 语言的文本处理器，你对动态 SQL 元素可能会感觉似曾相识。在 MyBatis 之前的版本中，需要花时间了解大量的元素。借助功能强大的基于 OGNL 的表达式，MyBatis 3 替换了之前的大部分元素，大大精简了元素种类，现在要学习的元素种类比原来的一半还要少。

- if
- choose (when, otherwise)
- trim (where, set)
- foreach

### 搭建环境

```sql
CREATE TABLE `blog`(
  `id` VARCHAR(50) NOT NULL COMMENT '博客id',
  `title` VARCHAR(100) NOT NULL COMMENT '博客标题',
  `author` VARCHAR(30) NOT NULL COMMENT '博客作者',
  `create_time` DATETIME NOT NULL COMMENT '创建时间',
  `views` INT(30) NOT NULL COMMENT '浏览量'
)ENGINE=INNODB DEFAULT CHARSET=utf8
```



创建一个基础工程

1. 导包

2. 编写配置文件

3. 编写实体类

   ```java
   @Data
   public class Blog {
       private int id;
       private String title;
       private String author;
       private Date createTime;
       private int views;
   }
   ```

4. 编写实体类对应的mapper接口和mapper.xml文件

5. 在核心配置文件中绑定mapper





### IF

使用动态 SQL 最常见情景是根据条件包含 where 子句的一部分。比如：

```xml
<select id="queryBlogIf" parameterType="map" resultType="Blog">
    select * from blog
    <where>
        <if test="title != null">
            and title = #{title}
        </if>
        <if test="author != null">
            and author = #{author}
        </if>
    </where>
</select>
```

```java
@Test
public void testQueryBlogIf() {
    SqlSession sqlSession = MybatisUtils.getSqlSession();
    BlogMapper mapper = sqlSession.getMapper(BlogMapper.class);

    Map<String,Object> map = new HashMap<String, Object>();
    //map.put("title","Java如此简单");

    List<Blog> blogs = mapper.queryBlogIf(map);

    for (Blog blog : blogs) {
        System.out.println(blog);
    }

    sqlSession.close();
}
```



### choose、when、otherwise

```xml
<select id="queryBlogChoose" parameterType="map" resultType="Blog">
    select * from blog
    <where>
        <choose>
            <when test="title != null">
                title = #{title}
            </when>
            <when test="author != null">
                and author = #{author}
            </when>
            <otherwise>
                and views = #{views}
            </otherwise>
        </choose>
    </where>
</select>
```



### trim、where、set

*where* 元素只会在子元素返回任何内容的情况下才插入 “WHERE” 子句。而且，若子句的开头为 “AND” 或 “OR”，*where* 元素也会将它们去除。

```xml
<select id="queryBlogIf" parameterType="map" resultType="Blog">
    select * from blog
    <where>
        <if test="title != null">
            and title = #{title}
        </if>
        <if test="author != null">
            and author = #{author}
        </if>
    </where>
</select>
```

*set* 元素会动态地在行首插入 SET 关键字，并会删掉额外的逗号（这些逗号是在使用条件语句给列赋值时引入的）。

```xml
<update id="updateBlog" parameterType="map">
    update blog
    <set>
        <if test="title != null">
            title = #{title},
        </if>
        <if test="author != null">
            author = #{author}
        </if>
    </set>
    where id = #{id}
</update>
```



### SQL片段

有的时候我们可能会将一些功能的部分抽取出来，方便复用

1. 使用sql标签抽取公共的部分
2. 在需要使用的地方使用include标签引用

```xml
<sql id="if-title-author">
    <if test="title != null">
        title = #{title},
    </if>
    <if test="author != null">
        and author = #{author}
    </if>
</sql>

<select id="queryBlogIf" parameterType="map" resultType="Blog">
    select * from blog
    <where>
        <include refid="if-title-author"></include>
    </where>
</select>
```

注意事项：

- 最好基于单表来定义sql片段
- 不要存在where标签

### ForEach

![image-20210327140712987](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210327140712987.png)

```xml
<select id="queryBlogForEach" parameterType="map" resultType="Blog">
    select * from blog
    <where>
        <foreach collection="ids" item="id" open="and (" separator="or" close=")">
            id = #{id}
        </foreach>
    </where>
</select>
```

![image-20210327141952803](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210327141952803.png)





**动态SQL就是在拼接SQL语句，我们只要保证SQL的正确性，按照SQL的格式，去排列组合就好了**



tips：

- 现在MySQL中写好sql，再对应的去修改成动态SQL



## 13、缓存

### 13.1、简介

1. 什么是缓存（Cache）
   - 存在内存中的临时数据
   - 将用户经常查询的数据放在缓存（内存）中，用户去查询数据就不用从磁盘上（关系型数据可数据文件）查询，从缓存中查询，提高查询效率，解决高并发系统的性能问题
2. 为什么使用缓存
   - 减少和数据库的交换次数，减少系统开销，提高系统效率
3. 什么样的数据能使用缓存
   - 经常查询并且不经常改变的数据【可以使用缓存】

### 13.2、Mybatis缓存

- MyBatis包含一个非常强大的查询缓存的特性，它可以非常方便地定制和配置缓存。缓存可以极大的提升查询效率
- MyBatis系统中默认定义了两极缓存：一**级缓存**和**二级缓存**
  - 默认情况下，只有一级缓存开启（SqlSession级别的缓存，也称为本地缓存）
  - 二级缓存需要手动开启和配置，他是基于namespace级别的缓存
  - 为了提高扩展性，MyBatis定义了缓存接口Cache。我们可以通过实现Cache接口来定义二级缓存

### 13.3、一级缓存

- 一级缓存也叫本地缓存：
  - 与数据库同一次会话期间查询 到的数据会放在本地缓存中
  - 以后如果需要获取相同的数据，直接从缓存中拿，没必要再去查询数据库

测试步骤：

1. 开启日志

   ```xml
   <settings>
       <!--标准日志工厂-->
       <setting name="logImpl" value="STDOUT_LOGGING"/>
   </settings>
   ```

2. 在一次session中查询两次相同记录，查看日志

   ```java
   @Test
   public void test1() {
       SqlSession sqlSession = MybatisUtils.getSqlSession();
       UserMapper mapper = sqlSession.getMapper(UserMapper.class);
   
       User user = mapper.queryUsersById(1);
   
       System.out.println(user);
   
       User user1 = mapper.queryUsersById(1);
   
       System.out.println(user1 == user);
   
   
       sqlSession.close();
   }
   ```

   ![image-20210327151313358](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210327151313358.png)

   

3. 缓存失效的情况

   1. 查询不同的东西
   2. 增删改操作可能会改变原来的数据，必定会刷新缓存
   3. 查询不同的Mapper.xml
   4. 手动清理缓存



一级缓存默认是开启的，只在一次sqlsession中有效，也就是拿到连接到关闭连接这个区间

### 13.4、二级缓存

- 二级缓存也叫全局缓存，以及缓存作用域太低了，所以诞生了二级缓存
- 基于namespace级别的缓存，一个名称空间，对应一个二级缓存
- 工作机制
  - 一个会话查询一条数据，这个数据就会被放在当前会话的一级缓存中
  - 如果当前会话关闭了，这个会话对应的一级缓存就没了，但是我们想要的是，会话关闭了，一级缓存中的数据被保存到二级缓存中去
  - 新的会话查询信息，就可以从二级缓存中获取内容



步骤：

1. 开启全局缓存

   ![image-20210327160237091](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210327160237091.png)

   ```xml
   <settings>
       <setting name="cacheEnabled" value="true"/>
   </settings>
   ```

   

2. 在要使用二级缓存的mapper中开启

   ```xml
   <!--在当前Mapper.xml中使用二级缓存-->
   <cache/>
   ```

   也可以自定义一些参数

   ```xml
   <!--在当前Mapper.xml中使用二级缓存-->
   <cache eviction="FIFO"
          flushInterval="60000"
          size="512"
          readOnly="true"/>
   ```

   这个更高级的配置创建了一个 FIFO 缓存，每隔 60 秒刷新，最多可以存储结果对象或列表的 512 个引用，而且返回的对象被认为是只读的

3. 测试

   1. 问题：我们需要将实体类序列化，否则会报错

      ```java
      Caused by: java.io.NotSerializableException: com.lei.pojo.User
      ```

      ```java
      public class User implements Serializable {
          private int id;
          private String name;
          private String pwd;
      }
      ```



小结：

- 只要开启了二级缓存，在同一个mapper下就有效
- 所有数据都会先存在一级缓存中
- 只有当前会话提交，或者关闭，才会提交到二级缓存中

### 13.5、缓存原理

![image-20210327162750466](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210327162750466.png)

### 13.6、自定义缓存-ehcache

Ehcache是一种广泛使用的开源Java分布式缓存。主要面向通用缓存



在程序中使用

1. 导包

   ```xml
   <!-- https://mvnrepository.com/artifact/org.mybatis.caches/mybatis-ehcache -->
   <dependency>
       <groupId>org.mybatis.caches</groupId>
       <artifactId>mybatis-ehcache</artifactId>
       <version>1.1.0</version>
   </dependency>
   ```

2. 