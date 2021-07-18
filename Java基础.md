# Java基础

# 1、Java语言概述

## 1.1、概述

### 1、计算机语言发展迭代史

第一代：机器语言

第二代：汇编语言

第三代：高级语言

- 面向过程：C，Pascal，Fortran
- 面向对象：Java，Js，Python，Scala

### 2、Java语言版本迭代

- 1991年 Green项目，开发语言最初命名为Oak (橡树)
- 1994年，开发组意识到Oak 非常适合于互联网
- 1996年，发布JDK 1.0，约8.3万个网页应用Java技术来制作
- 1997年，发布JDK 1.1，JavaOne会议召开，创当时全球同类会议规模之最
- 1998年，发布JDK 1.2，同年发布企业平台J2EE
- 1999年，Java分成J2SE、J2EE和J2ME，JSP/Servlet技术诞生
- 2004年，发布里程碑式版本：JDK 1.5，为突出此版本的重要性，更名为JDK 5.0
- 2005年，J2SE -> JavaSE，J2EE -> JavaEE，J2ME -> JavaME
- 2009年，Oracle公司收购SUN，交易价格74亿美元
- 2011年，发布JDK 7.0
- 2014年，发布JDK 8.0，是继JDK 5.0以来变化最大的版本
- 2017年，发布JDK 9.0，最大限度实现模块化
- 2018年3月，发布JDK 10.0，版本号也称为18.3
- 2018年9月，发布JDK 11.0，版本号也称为18.9

### 3、Java语言应用领域

- Java Web开发：后台开发
- 大数据开发：
- Android应用程序开发：客户端开发

### 4、Java语言特点

- 面向对象：
  - 两个要素：类、对象
  - 三个特征：封装、继承、多态
- 健壮性：
  - 去除了c语言的指针
  - 自动垃圾回收机制 --> 仍然会出现内存溢出、泄露
- 跨平台性：write once,run anywhere:一次编译，到处运行

功劳归功于：JVM

![image-20210417235339156](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210417235339156.png)

## 1.2、开发环境搭建

### 1、JDK、JRE、JVM的关系

![image-20210417235448786](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210417235448786.png)

### 2、JDK的下载、安装

下载：

- 官网：https://www.oracle.com/java/technologies/javase-downloads.html
- github

注意：安装软件的路径不能包含中文、空格

### 3、Path环境变量配置

**为什么要配置**

path环境变量：windows操作系统执行命令时所要搜寻的路径
为什么要配置path:希望java的开发工具（javac.exe,java.exe)在任何的文件路径下都可以执行成功。

**如何配置**

![image-20210417235947012](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210417235947012.png)

![image-20210418000015835](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418000015835.png)

![image-20210418000115439](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418000115439.png)

在path中把JAVA_HOME配置进去

![image-20210418000215295](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418000215295.png)

在控制台输入：java -version

如果有输出，则说明安装成功

![image-20210418000334271](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418000334271.png)

### 4、注释与API文档

> **注释**

- 分类：
  - 单行注释：//
  - 多行注释：/*   */
  - 文档注释：/**  */
- 作用
  - 对所写的程序进行解释说明，增强可读性。方便自己，方便别人
  - 调试所写的代码
- 特点
  - 单行注释和多行注释，注释了的内容不参与编译。换句话说，编译以后生成的.class结尾的字节码文件中不包含注释掉的信息
  - 注释内容可以被JDK提供的工具 javadoc 所解析，生成一套以网页文件形式体现的该程序的说明文档。
  - 多行注释不可以嵌套使用

> **Java API 文档**

API:application programming interface。习惯上：将语言提供的类库，都称为api.
API文档：针对于提供的类库如何使用，给的一个说明书。类似于《新华字典》

# 2、基本语法

## 2.1、关键字与标识符

### 2.1.1、java关键字的使用

定义：被Java语言赋予了特殊含义，用做专门用途的字符串（单词）

特点：关键字中所字母都为小写

![image-20210418231342617](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418231342617.png)

![image-20210418231347116](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418231347116.png)

### 2.1.2、保留字

现Java版本尚未使用，但以后版本可能会作为关键字使用。

具体哪些保留字：goto 、const
**注意**：自己命名标识符时要避免使用这些保留字

### 2.1.3、标识符的使用

**定义**：凡是自己可以起名字的地方都叫标识符。

涉及到的结构：
包名、类名、接口名、变量名、方法名、常量名

**规则：(必须要遵守。否则，编译不通过)**

- 由26个字母大小写，0-9，_ 和 $ 组成
- 数字不可以开头
- 不可以使用关键字和保留字
- Java中严格区分大小写，长度无限制
- 标识符不能包含空格

**规范：（可以不遵守，不影响编译和运行。但是要求大家遵守）**

- 包名：多单词组成是所有字母都小写：xxxyyyzzz
- 类名、接口名：多单词组成时，所有单词的首字母大写：XxxYyyZzz
- 变量名、方法名：多单词组成时，第一个单词首字母小写，第二个单词开始每个单词首字母大写：xxxYyyZzz
- 常量名：所有字母都大写，多单词时每个单词用下划线连接：XXX_YYY_ZZZ
- 起名时，尽量见名知意

## 2.2、变量的使用

### 2.2.1、变量的分类

**1、按数据类型分类**

![image-20210418232205601](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418232205601.png)

详细说明：

1. 整型：byte(1字节=8bit) \ short(2字节) \ int(4字节) \ long(8字节)
   	① byte范围：-128 ~ 127
   	② 声明long型变量，必须以"l"或"L"结尾
   	③ 通常，定义整型变量时，使用int型。
       ④整型的常量，默认类型是：int型
2. 浮点型：float(4字节) \ double(8字节)
   	① 浮点型，表示带小数点的数值
   	② float表示数值的范围比long还大
   	③ 定义float类型变量时，变量要以"f"或"F"结尾
   	④ 通常，定义浮点型变量时，使用double型。
   	⑤ 浮点型的常量，默认类型为：double
3. 字符型：char (1字符=2字节)
   	① 定义char型变量，通常使用一对'',内部只能写一个字符
   	② 表示方式：1.声明一个字符 2.转义字符 3.直接使用 Unicode 值来表示字符型常量
4. 布尔型：boolean
   	① 只能取两个值之一：true 、 false
   	② 常常在条件判断、循环结构中使用

![image-20210418233805579](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418233805579.png)

![image-20210418233816588](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418233816588.png)



**2、按申明位置分类**

![image-20210418232401368](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418232401368.png)

### 2.2.2、定义变量的格式

```java
//数据类型  变量名 = 变量值;
int i = 1;
String str = "abc";
//数据类型  变量名;
int j;
double k;
//变量名 = 变量值;
j = 2;
```

### 2.2.3、变量使用的注意点

1. 变量必须先声明，后使用
2. 变量都定义在其作用域内。在作用域内，它是有效的。换句话说，出了作用域，就失效了
3. 同一个作用域内，不可以声明两个同名的变量

### 2.2.4、基本数据类型变量间运算规则

1、涉及到的基本数据类型：除了boolean之外的其他7种

2、自动类型转换(只涉及7种基本数据类型）

结论：当容量小的数据类型的变量与容量大的数据类型的变量做运算时，结果自动提升为容量大的数据类型。

byte 、char 、short --> int --> long --> float --> double 

**特别的**：当byte、char、short三种类型的变量做运算时，结果为int型

**说明**：此时的容量大小指的是，表示数的范围的大和小。比如：float容量要大于long的容量

3、强制类型转换(只涉及7种基本数据类型）：自动类型提升运算的逆运算。

1）需要使用强转符：()
2）注意点：强制类型转换，可能导致精度损失。

4、String与8种基本数据类型间的运算

1. String属于引用数据类型,翻译为：字符串
2. 声明String类型变量时，使用一对""
3. String可以和8种基本数据类型变量做运算，且运算只能是连接运算：+
4. 运算的结果仍然是String类型

## 2.3、运算符

### 2.3.1、算数运算符

![image-20210418233303319](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418233303319.png)

**要注意的问题**

- 如果对负数取模，可以把模数负号忽略不记，如：5%-2=1。 但被模数是 负数则不可忽略。此外，取模运算的结果不一定总是整数。
- 对于除号“/”，它的整数除和小数除是有区别的：整数之间做除法时，只 保留整数部分而舍弃小数部分。 例如：int x=3510;x=x/1000*1000; x的 结果是？3000
- “+”除字符串相加功能外，还能把非字符串转换成字符串.例如： System.out.println(“5+5=”+5+5); //打印结果是？ 5+5=55

### 2.3.2、赋值运算符

- 符号：= 

  当“=”两侧数据类型不一致时，可以使用自动类型转换或使用强制 类型转换原则进行处理

  支持连续赋值

- 扩展赋值运算符： +=, -=, *=, /=, %=

### 2.3.3、比较运算符

![image-20210418234021232](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418234021232.png)

- 比较运算符的结果都是boolean型，也就是要么是true，要么是false
- 比较运算符“==”不能误写成“=”

### 2.3.4、逻辑运算符

![image-20210418234153931](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418234153931.png)

**【注意】**

- 逻辑运算符用于连接布尔型表达式，在Java中不可以写成33 & x<6 
- “&”和“&&”的区别： 
  - 单&时，左边无论真假，右边都进行运算
  - 双&时，如果左边为真，右边参与运算，如果左边为假，那么右边不参与运算
- “|”和“||”的区别同理，||表示：当左边为真，右边不参与运算
- 异或( ^ )与或( | )的不同之处是：当左右都为true时，结果为false。理解：异或，追求的是“异”

### 2.3.5、位运算符

![image-20210418234508374](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418234508374.png)

![image-20210418234524961](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418234524961.png)

### 2.3.6、三元运算符

- 格式

  ![image-20210418234719791](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418234719791.png)

- 表达式1和表达式2为同种类型
- 三元运算符与if-else的联系与区别：
  - 三元运算符可简化if-else语句 
  - 三元运算符要求必须返回一个结果
  - if后的代码块可有多个语句

ex：

```java
//获取两个数中的较大数
int a,b;
int res = a > b ? a : b;
//获取三个数中的较大数
int m,n,k;
int res = (m > n ? m : n) > k ? (m > n ? m : n) : k;
```

## 2.4、流程控制

### 2.4.1、顺序结构

程序从上到下执行。

### 2.4.2、分支结构

#### **1、if-else**

![image-20210418235359869](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418235359869.png)

![image-20210418235407204](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418235407204.png)

![image-20210418235416095](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418235416095.png)

**说明：**

-  条件表达式必须是布尔表达式（关系表达式或逻辑表达式）、布尔变量 
- 语句块只有一条执行语句时，一对{}可以省略，但建议保留 
- if-else语句结构，根据需要可以嵌套使用  当if-else结构是“多选一”时，最后的else是可选的，根据需要可以省略 
- 当多个条件是“互斥”关系时，条件判断语句及执行语句间顺序无所谓 当多个条件是“包含”关系时，“小上大下 / 子上父下”

#### 2、switch-case

![image-20210418235716208](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210418235716208.png)

**说明：**

- switch(表达式)中表达式的值必须是下述几种类型之一：byte，short， char，int，枚举 (jdk 5.0)，String (jdk 7.0)
- case子句中的值必须是常量，不能是变量名或不确定的表达式值
- 同一个switch语句，所有case子句中的常量值互不相同
-  break语句用来在执行完一个case分支后使程序跳出switch语句块；如 果没有break，程序会顺序执行到switch结尾 
- default子句是可任选的。同时，位置也是灵活的。当没有匹配的case时， 执行default

### 2.4.3、循环结构

#### 1、循环结构四要素

-  ①初始化条件
-  ②循环条件  --->是boolean类型
-  ③循环体
-  ④迭代条件

说明：通常情况下，循环结束都是因为②中循环条件返回false了。

#### 2、三种循环结构

##### 1、for循环

```java
for(①;②;④){
	③
}
执行过程：① - ② - ③ - ④ - ② - ③ - ④ - ... - ②
```

##### 2、while循环

```java
①
while(②){
	③;
	④;
}
执行过程：① - ② - ③ - ④ - ② - ③ - ④ - ... - ②
说明：
写while循环千万小心不要丢了迭代条件。一旦丢了，就可能导致死循环！
```

for和while循环总结：
1. 开发中，基本上我们都会从for、while中进行选择，实现循环结构。
2. for循环和while循环是可以相互转换的！ 
    区别：for循环和while循环的初始化条件部分的作用范围不同。
3. 我们写程序，要避免出现死循环。

##### 3、do-while循环结构

```java
①
do{
	③;
	④;
}while(②);
执行过程：① - ③ - ④ - ② - ③ - ④ - ... - ②
```

说明：

- do-while循环至少会执行一次循环体！
- 开发中，使用for和while更多一些。较少使用do-while

#### 3、“无限循环”结构

while(true) 或 for(;;)

总结：如何结束一个循环结构？

- 方式一：当循环条件是false时
- 方式二：在循环体中，执行break

#### 4、嵌套循环

1.嵌套循环:将一个循环结构A声明在另一个循环结构B的循环体中,就构成了嵌套循环

​	内层循环：循环结构A

​	外层循环：循环结构B

2.说明：

​	① 内层循环结构遍历一遍，只相当于外层循环循环体执行了一次

​	② 假设外层循环需要执行m次，内层循环需要执行n次。此时内层循环的循环体一共执行了m * n次

​	③ 外层循环控制行数，内层循环控制列数

### 2.4.4、特殊关键字的使用

![image-20210419000757912](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210419000757912.png)

![image-20210419000740135](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210419000740135.png)

- break只能用于switch语句和循环语句中。 
- continue 只能用于循环语句中。 
- 二者功能类似，但continue是终止本次循环，break是终止本层循环。 
- break、continue之后不能有其他的语句，因为程序永远不会执行其后的语句。 
- 标号语句必须紧接在循环的头部。标号语句不能用在非循环语句的前面。 
- 很多语言都有goto语句，goto语句可以随意将控制转移到程序中的任意一条 语句上，然后执行它。但使程序容易出错。Java中的break和continue是不同 于goto的。

# 3、数组

## 3.1、数组概述

1. 数组的理解：数组(Array)，是多个相同类型数据一定顺序排列的集合，并使用一个名字命名，并通过编号的方式对这些数据进行统一管理。
2. 数组相关的概念：
   - 数组名
   - 元素
   - 角标、下标、索引
   - 数组的长度：元素的个数
3. 数组本身是引用数据类型，而数组中的元素可以是任何数据类型，包括 基本数据类型和引用数据类型。
4. 创建数组对象会在内存中开辟一整块连续的空间，而数组名中引用的是 这块连续空间的首地址。
5. 数组的长度一旦确定，就不能修改。
6. 我们可以直接通过下标(或索引)的方式调用指定位置的元素，速度很快。
7. 数组的分类：
   - 按照维度：一维数组、二维数组、三维数组、…
   - 按照元素的数据类型分：基本数据类型元素的数组、引用数据类型元素的数组(即对象数组）

## 3.2、一维数组

### 1、声明

type var[] 或 type[] var；

```java
int a[];
int[] a1;
double b[];
String[] c;//引用类型变量数组

//Java语言中声明数组时不能指定其长度(数组中元素的数)， 例如： 
int a[5]; //非法
```

### 2、初始化

**动态初始化：**数组声明且为数组元素分配空间与赋值的操作分开进行

```java
int[] arr = new int[3];
arr[0] = 1;
arr[1] = 2;
arr[2] = 4;
```

**静态初始化：**在定义数组的同时就为数组元素分配空间并赋值

```java
int[] arr = new int[3]{1,2,4};
int[] arr = {1,2,4};
```

### 3、数组元素的引用

定义并用运算符new为之分配空间后，才可以引用数组中的每个元素

数组元素的引用方式：**数组名[数组元素下标]**

- 数组元素下标可以是整型常量或整型表达式。如a[3] , b[i] , c[6*i];
- 数组元素下标从0开始；长度为n的数组合法下标取值范围: 0 —>n-1；如int a[]=new  int[3]; 可引用的数组元素为a[0]、a[1]、a[2]

每个数组都有一个属性length指明它的长度，例如：a.length 指明数组a的长 度(元素个数)

- 数组一旦初始化，其**长度是不可变**的

### 4、一维数组元素的默认初始化值

- 数组元素是整型：0
- 数组元素是浮点型：0.0
- **数组元素是char型：0或'\u0000'，而非'0'**
- 数组元素是boolean型：false
- 数组元素是引用数据类型：null

### 5、一维数组的内存解析

```java
int[] arr = new int[]{1,2,3};
String[] arr1 = new String[4];
arr1[1] = “刘德华”;
arr1[2] = “张学友”;
arr1 = new String[3];
sysout(arr1[1]);//nul
```

![image-20210420235659471](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210420235659471.png)

## 3.3、二维数组

Java 语言里提供了支持多维数组的语法。

如果说可以把一维数组当成几何中的线性图形， 那么二维数组就相当于是一个表格，像右图Excel 中的表格一样。

对于二维数组的理解，我们可以看成是一维数组 array1又作为另一个一维数组array2的元素而存 在。其实，从数组底层的运行机制来看，其实没 有多维数组。

### 1、二维数组的声明与初始化

```java
//正确的方式：
int[] arr = new int[]{1,2,3};//一维数组
//静态初始化
int[][] arr1 = new int[][]{{1,2,3},{4,5},{6,7,8}};
//动态初始化1
String[][] arr2 = new String[3][2];
//动态初始化2
String[][] arr3 = new String[3][];
//也是正确的写法：
int[] arr4[] = new int[][]{{1,2,3},{4,5,9,10},{6,7,8}};
int[] arr5[] = {{1,2,3},{4,5},{6,7,8}};//类型推断
//错误的方式：
//		String[][] arr4 = new String[][4];
//		String[4][3] arr5 = new String[][];
//		int[][] arr6 = new int[4][3]{{1,2,3},{4,5},{6,7,8}};
```

### 2、如何调用二维数组元素

```java
System.out.println(arr1[0][1]);//2
System.out.println(arr2[1][1]);//null

arr3[1] = new String[4];
System.out.println(arr3[1][0]);
System.out.println(arr3[0]);//
```

### 3、二维数组的属性

```java
System.out.println(arr4.length);//3
System.out.println(arr4[0].length);//3
System.out.println(arr4[1].length);//4
```

### 4、遍历二维数组元素

```java
for(int i = 0;i < arr4.length;i++){

    for(int j = 0;j < arr4[i].length;j++){
        System.out.print(arr4[i][j] + "  ");
    }
    System.out.println();
}
```

### 5、二维数组元素的默认初始化值

```java
规定：二维数组分为外层数组的元素，内层数组的元素
    int[][] arr = new int[4][3];
外层元素：arr[0],arr[1]等
内层元素：arr[0][0],arr[1][2]等

⑤ 数组元素的默认初始化值 
针对于初始化方式一：比如：int[][] arr = new int[4][3];
外层元素的初始化值为：地址值
内层元素的初始化值为：与一维数组初始化情况相同

针对于初始化方式二：比如：int[][] arr = new int[4][];
外层元素的初始化值为：null
内层元素的初始化值为：不能调用，否则报错。
```

### 6、二维数组的内存结构

![image-20210421000916550](C:\Users\朱磊\AppData\Roaming\Typora\typora-user-images\image-20210421000916550.png)