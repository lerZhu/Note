# JavaWeb

## Maven配置

### 下载安装Maven

https://maven.apache.org/

![image-20210324100905707](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324100905707.png)

![image-20210324100954064](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324100954064.png)

### 配置环境变量

M2_HONE：MAVEN安装目录下的\bin

![](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324101033080.png)

MAVEN_HOME:MAVEN安装目录

![image-20210324101159199](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324101159199.png)

path：%MAVEN_HOME%\bin

![image-20210324101244294](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324101244294.png)

### 阿里云镜像

![image-20210324101322136](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324101322136.png)

![image-20210324101340493](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324101340493.png)

<mirrors>标签中配置

```xml
<mirror>
        <id>nexus-aliyun</id>
		<mirrorOf>*,!jeecg,!jeecg-snapshots</mirrorOf>
        <name>Nexus aliyun</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public</url></mirror>
```

### 本地仓库

建一个本地仓库

![image-20210324101604969](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324101604969.png)

```xml
<localRepository>D:\JAVA\apache-maven-3.6.3\maven-repo</localRepository>
```

### IDEA中使用Maven

1.创建一个MavenWeb项目

![image-20210324103059554](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324103059554.png)

![image-20210324103315839](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324103315839.png)

2.第一次创建会下载一些包，等自动下载完成

![image-20210324103444000](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324103444000.png)

3.IDEA中的MAVEN设置

​	IDEA项目创建成功后，看一眼MAVEN的配置

![image-20210324103714957](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324103714957.png)

### 创建一个普通的Maven项目

![image-20210324104048611](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324104048611.png)

![image-20210324104223969](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324104223969.png)

### 标记文件夹功能

![image-20210324104722480](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324104722480.png)

### 在IDEA中配置TOMCAT

![image-20210324105137496](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324105137496.png)

![image-20210324105359866](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324105359866.png)

解决Warning

![image-20210324105503490](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324105503490.png)

![image-20210324105527766](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324105527766.png)

警告消失

？访问网站需要指定一个文件夹的名字

![image-20210324105548572](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210324105548572.png)

### pom文件

pom.xml是maven的核心配置文件

maven由于他的约定大于配置，之后会遇到我们写的配置文件，无法被导出或者生效的问题，解决方案:

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

