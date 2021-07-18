![image-20210628211637223](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210628211637223.png)

```
linux内核官网
https://www.kernel.org/
```

# VM安装

```
网上找资源

vmware 15.5
```

# VM启动蓝屏问题解决

- ![image-20210703151220264](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703151220264.png)
- ![image-20210703151316548](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703151316548.png)
- 勾选点击确定，然后立即重启

# Centos安装

```
version : 7.9

http://mirrors.aliyun.com/centos/7/isos/x86_64/


```

# 虚拟机克隆

- 直接拷贝一份安装好的虚拟机文件
- 使用VMware的克隆操作
  - 需要先关闭linux系统

# Xshell、Xftp

```
https://www.netsarang.com/en/free-for-home-school/
```

# Vim的一些快捷键记录:

## 一、移动光标

| 按键    | 功能                                              | 说明 |
| ------- | :------------------------------------------------ | :--: |
| h,j,k,l | 上，下，左，右                                    |      |
| ctrl-e  | 移动页面                                          |      |
| ctrl-f  | 上翻一页                                          |      |
| ctrl-b  | 下翻一页                                          |      |
| ctrl-u  | 上翻半页                                          |      |
| ctrl-d  | 下翻半页                                          |      |
| w       | 跳到下一个字首，按标点或单词分割                  |      |
| W       | 跳到下一个字首，长跳，如end-of-line被认为是一个字 |      |
| e       | 跳到下一个字尾                                    |      |
| E       | 跳到下一个字尾，长跳                              |      |
| b       | 跳到上一个字                                      |      |
| B       | 跳到上一个字，长跳                                |      |
| 0       | 跳至行首，不管有无缩进，就是跳到第0个字符         |      |
| ^       | 跳至行首的第一个字符                              |      |
| $       | 跳至行尾                                          | 常用 |
| gg      | 跳至文首                                          | 常用 |
| G       | 调至文尾                                          | 常用 |
| 5gg/5G  | 调至第5行                                         |      |
| gd      | 跳至当前光标所在的变量的声明处                    |      |
| fx      | 在当前行中找x字符，找到了就跳转至                 |      |
| ;       | 重复上一个f命令，而不用重复的输入fx               |      |
| *       | 查找光标所在处的单词，向下查找                    |      |
| #       | 查找光标所在处的单词，向上查找                    |      |

------

## 二、删除复制

| 按键                      | 功能               | 说明 |
| ------------------------- | :----------------- | :--: |
| dd                        | 删除光标所在行     |      |
| dw                        | 删除当前字符至行末 |      |
| D                         | 删除当前字符至行末 |      |
| x                         | 删除当前字符       |      |
| X                         | 删除前一个字符     |      |
| yy                        | 复制一行           |      |
| Y                         | 复制一行           |      |
| yw                        | 复制到行末         |      |
| 按esc后，然后ggvG或者ggVG | 全选（高亮显示）   |      |
| 按esc后，然后ggyG         | 全部复制           |      |
| 按esc后，然后dG           | 全部删除           |      |

------

## 三、插入模式

| 按键 | 功能                                 | 说明 |
| ---- | :----------------------------------- | :--: |
| i    | 从当前光标处进入插入模式             |      |
| I    | 进入插入模式，并置光标于行首         |      |
| a    | 追加模式，置光标于当前光标之后       |      |
| A    | 追加模式，置光标于行末               |      |
| o    | 在当前行之下新加一行，并进入插入模式 |      |
| O    | 在当前行之上新加一行，并进入插入模式 |      |
| Esc  | 退出插入模式                         |      |

------

## 四、编辑

| 按键   | 功能                                       | 说明 |
| ------ | :----------------------------------------- | :--: |
| J      | 将下一行和当前行连接为一行                 |      |
| cc     | 删除当前行并进入编辑模式                   |      |
| cw     | 删除当前字，并进入编辑模式                 |      |
| c$     | 擦除从当前位置至行末的内容，并进入编辑模式 |      |
| s      | 删除当前字符并进入编辑模式                 |      |
| S      | 删除光标所在行并进入编辑模式               |      |
| xp     | 交换当前字符和下一个字符                   |      |
| u      | 撤销                                       |      |
| ctrl+r | 重做                                       |      |
| ~      | 切换大小写，当前字符                       |      |
| >>     | 将当前行右移一个单位                       |      |
| <<     | 将当前行左移一个单位(一个tab符)            |      |
| ==     | 自动缩进当前行                             |      |

------

## 五、查找替换

| 按键           | 功能                                                         | 说明 |
| -------------- | :----------------------------------------------------------- | :--: |
| /pattern       | 向后搜索字符串pattern                                        |      |
| ?pattern       | 向前搜索字符串pattern                                        |      |
| "\c"           | 忽略大小写                                                   |      |
| "\C"           | 大小写敏感                                                   |      |
| n              | 下一个匹配(如果是/搜索，则是向下的下一个，?搜索则是向上的下一个) |      |
| N              | 上一个匹配(同上)                                             |      |
| :%s/old/new/g  | 搜索整个文件，将所有的old替换为new                           |      |
| :%s/old/new/gc | 搜索整个文件，将所有的old替换为new，每次都要你确认是否替换   |      |

------

## 六、退出编辑器

| 按键 | 功能                                   | 说明 |
| ---- | :------------------------------------- | :--: |
| :w   | 将缓冲区写入文件，即保存修改           |      |
| :wq  | 保存修改并退出                         |      |
| :x   | 保存修改并退出                         |      |
| :q   | 退出，如果对缓冲区进行过修改，则会提示 |      |
| :q!  | 强制退出，放弃修改                     |      |

------

## 七、多文件编辑

| 按键              | 功能                               | 说明 |
| ----------------- | :--------------------------------- | :--: |
| vim file1..       | 同时打开多个文件                   |      |
| :args             | 显示当前编辑文件                   |      |
| :next             | 切换到下个文件                     |      |
| :prev             | 切换到前个文件                     |      |
| :next！           | 不保存当前编辑文件并切换到下个文件 |      |
| :prev！           | 不保存当前编辑文件并切换到上个文件 |      |
| :wnext            | 保存当前编辑文件并切换到下个文件   |      |
| :wprev            | 保存当前编辑文件并切换到上个文件   |      |
| :first            | 定位首文件                         |      |
| :last             | 定位尾文件                         |      |
| ctrl+^            | 快速在最近打开的两个文件间切换     |      |
| :split[sp]        | 把当前文件水平分割                 |      |
| :split file       | 把当前窗口水平分割, file           |      |
| :vsplit[vsp] file | 把当前窗口垂直分割, file           |      |
| :new file         | 同split file                       |      |
| :close            | 关闭当前窗口                       |      |
| :only             | 只显示当前窗口, 关闭所有其他的窗口 |      |
| :all              | 打开所有的窗口                     |      |
| :vertical all     | 打开所有的窗口, 垂直打开           |      |
| :qall             | 对所有窗口执行：q操作              |      |
| :qall!            | 对所有窗口执行：q!操作             |      |
| :wall             | 对所有窗口执行：w操作              |      |
| :wqall            | 对所有窗口执行：wq操作             |      |
| ctrl-w h          | 跳转到左边的窗口                   |      |
| ctrl-w j          | 跳转到下面的窗口                   |      |
| ctrl-w k          | 跳转到上面的窗口                   |      |
| ctrl-w l          | 跳转到右边的窗口                   |      |
| ctrl-w t          | 跳转到最顶上的窗口                 |      |
| ctrl-w b          | 跳转到最底下的窗口                 |      |

------

## 八、多标签编辑

| 按键            | 功能                   | 说明 |
| --------------- | :--------------------- | :--: |
| :tabedit file   | 在新标签中打开文件file |      |
| :tab split file | 在新标签中打开文件file |      |
| :tabp           | 切换到前一个标签       |      |
| :tabn           | 切换到后一个标签       |      |
| :tabc           | 关闭当前标签           |      |
| :tabo           | 关闭其他标签           |      |
| gt              | 到下一个tab            |      |
| gT              | 到上一个tab            |      |
| 0gt             | 跳到第一个tab          |      |
| 5gt             | 跳到第五个tab          |      |

------

## 九、执行shell命令

| 按键                                                         | 说明 |
| ------------------------------------------------------------ | :--: |
| 1、在命令模式下输入":sh"，可以运行相当于在字符模式下，到输入结束想回到VIM编辑器中用exit，ctrl+D返回VIM编辑器 |      |
| 2、可以"!command"，运行结束后自动回到VIM编辑器中             |      |
| 3、用“Ctrl+Z“回到shell，用fg返回编辑                         |      |
| 4、:!make -> 直接在当前目录下运行make指令                    |      |

------

## 十、VIM启动项|

| 按键  |             说明             |
| ----- | :--------------------------: |
| -o[n] | 以水平分屏的方式打开多个文件 |
| -O[n] | 以垂直分屏的方式打开多个文件 |

------

## 十一、自动排版

| 按键                                                      | 说明 |
| --------------------------------------------------------- | :--: |
| 在粘贴了一些代码之后，vim变得比较乱，只要执行gg=G就能搞定 |      |

------

## 十二、如何在vim中编译程序

| 按键                                                         | 说明 |
| ------------------------------------------------------------ | :--: |
| 在vim中可以完成make,而且可以将编译的结果也显示在vim里，先执行 :copen 命令，将结果输出的窗口打开，然后执行 :make编译后的结果就显示在了copen打开的小窗口里了，而且用鼠标双击错误信息，就会跳转到发生错误的行。 |      |

------

## 十三、buffer操作

| 按键          |         说明         |
| ------------- | :------------------: |
| 1、buffer状态 |                      |
| -             |  （非活动的缓冲区）  |
| a             | （当前被激活缓冲区） |
| h             |   （隐藏的缓冲区）   |
| %             |   （当前的缓冲区）   |
| #             |    （交换缓冲区）    |
| =             |    （只读缓冲区）    |
| +             | （已经更改的缓冲区） |

------

## 十四、 VIM 操作目录

| 按键                       |                             说明                             |
| -------------------------- | :----------------------------------------------------------: |
| 1.打开目录                 |                                                              |
| vim .                      |                                                              |
| vim a-path/                |                                                              |
| 2.以下操作在操作目录时生效 |                                                              |
| p,P,t,u,U,x,v,o,r,s        |                                                              |
| c                          |                 使当前打开的目录成为当前目录                 |
| d                          |                           创建目录                           |
| %                          |                           创建文件                           |
| D                          |                        删除文件/目录                         |
| -                          |                         转到上层目录                         |
| gb                         |               转到上一个 bookmarked directory                |
| i                          |                     改变目录文件列表方式                     |
| ^l                         |                      刷新当前打开的目录                      |
| mf -                       |                           标记文件                           |
| mu -                       |                   unmark all marked files                    |
| mz -                       |               Compress/decompress marked files               |
| gh                         |               显示/不显示隐藏文件( dot-files)                |
| ^h                         |                       编辑隐藏文件列表                       |
| a                          |              转换显示模式, all - hide - unhide               |
| qf                         |                 diplay infomation about file                 |
| qb                         | list the bookmarked directories and directory traversal history |
| gi                         |                 Display information on file                  |
| mb                         |                                                              |
| mc                         |                                                              |
| md -                       |            将标记的文件(mf标记文件)使用 diff 模式            |
| me -                       |        编辑标记的文件,只显示一个，其余放入 buffer 中         |
| mh                         |                                                              |
| mm -                       |      move marked files to marked-file target directory       |
| mc -                       |                             copy                             |
| mp                         |                                                              |
| mr                         |                                                              |
| mt                         |                                                              |
| vim 中复制,移动文件        |                                                              |
| 1, mt -                    |                         移动到的目录                         |
| 2, mf -                    |                       标记要移动的文件                       |
| 3, mc -                    |                          移动/复制                           |
| R 移动文件                 |                                                              |
| 打开当前编辑文件的目录     |                                                              |
| :Explore                   |                                                              |
| :Hexplore                  |                                                              |
| :Nexplore                  |                                                              |
| :Pexplore                  |                                                              |
| :Sexplore                  |                                                              |
| :Texplore                  |                                                              |
| :Vexplore                  |                                                              |



# 用户管理

## 添加用户

- useradd 用户名

- 当创建用户成功后，会自动的创建和用户同名的家目录

- 也可以通过 useradd -d 指定目录 新的用户名，给新创建的用户指定家目录

  ![image-20210703151832027](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703151832027.png)

## 指定、修改密码

- passwd 用户名

  ![image-20210703152007329](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703152007329.png)

## 删除用户

- 删除用户保留家目录：userdel 用户名

  ![image-20210703152519957](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703152519957.png)

- 删除用户同时删除家目录：userdel -r 用户名

  ![image-20210703152732041](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703152732041.png)

## 查询用户信息

- id 用户名

  ![image-20210703170953352](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703170953352.png)

![image-20210703171059309](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703171059309.png)

## 切换用户

- su - 切换用户名
- 从权限高的用户切换到权限低的用户不需要输入密码
- 返回原来的用户使用：logout

## 查看当前用户信息

- whoami 

  ![image-20210703171514381](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703171514381.png)

- who am i

  ![image-20210703171541375](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703171541375.png)

## 用户组

- 类似于角色，系统可以对有共性/权限的多个用户进行统一的管理
- 新增组：groupadd 组名
  - 新增用户是直接加上组：useradd -g 用户组 用户名
  - 不指定组，以自己为一个组
- 删除组：groupdel 组名
- 修改用户的组：usermod -g 用户组 用户名

## 用户和组的相关文件

- /etc/passwd
  - 用户的配置文件，记录用户的各种信息
  - 每行的含义：用户名：口令：用户标识号：注释性描述：主目录：登录Shell
- /etc/shadow
  - 口令的配置文件
  - 每行的含义：登录名：加密口令：最后一次修改时间：最小时间间隔：最大时间间隔：警告时间：不活动时间：失效时间：标志
- /etc/group
  - 组的配置文件，记录linux包含的组的信息
  - 每行含义：组名：组标识号：组内用户列表

# 实用指令

## 指定运行级别

- 运行级别说明
  - 0：关机
  - 1：单用户【找回丢失密码】
  - 2：多用户状态没有网络服务
  - 3：多用户状态有网络服务
  - 4：系统未使用保留给用户
  - 5：图形界面
  - 6：系统重启
  - 常用运行级别是3和5，也可以指定默认运行级别
- 指定运行级别：init [0123456]
- 查看当前运行级别：systemctl get-default
- 设置默认运行级别：systemctl set-default TARGET.target

## 找回root密码（centos7）

1. 启动系统，进入开机界面，在界面中按 “e” 进入编辑界面

   ![image-20210703210241121](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703210241121.png)

2. 进入编辑界面，使用键盘上的上下键把光标向下移动，找到以 “Linux16”开头内容所在的行数，在行的最后输入：init=/bin/sh

   ![image-20210703210457494](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703210457494.png)

3. 输入完成后，直接按快捷键Ctrl + x 进入单用户模式

4. 接着，在鼠标光标闪烁的位置中输入：mount -o remount,rw / ，完成后回车

   ![image-20210703210809887](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703210809887.png)

5. 在新的一行最后面输入passwd，完成后回车。输入密码，然后再次确认密码即可，密码修改完成后，会显示passwd......的样式，说明密码修改成功

   ![image-20210703211013824](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703211013824.png)

   ![image-20210703211043435](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703211043435.png)

6. 接着，在鼠标闪烁的位置中输入：touch /.autorelabel ，完成后回车

7. 继续在光标闪烁的位置中，输入：exec /sbin/init，完成后回车，等待系统自动修改密码，完成后，系统会自动重启，新密码生效

## 帮助指令

- man 获得帮助信息

  - man [命令或配置文件]

  - 选项可以组合使用，如：ls -la

  - 如：man ls

    ![image-20210703212153750](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703212153750.png)

- help指令

  - help 命令 （获取shell内置命令的帮助信息）

  - 如：help cd

    ![image-20210703212332240](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210703212332240.png)

## 文件目录类

- pwd
  - pwd （显示当前工作目录的绝对路径）
- ls
  - ls [选项] [目录或文件]
  - 常用选项
    - -a：显示当前目录所有的文件和目录，包括隐藏的
    - -l：以列表的方式显示信息
- cd
  - cd [参数] （切换到指定目录）
  - cd ~ 或者 cd：回到当前用户的家目录
  - cd.. 回到当前目录的上一级目录
- mkdir
  - mkdir [选项] 要创建的目录
  - 创建目录
  - 常用选项
    - -p：创建多级目录
- rmdir
  - rmdir [选项] 要删除的目录
  - rmdir删除的是空目录，如果目录下有内容时是无法删除的
  - 如果需要删除非空目录，需要使用 rm -rf 要删除的目录
- touch
  - touch 文件名称
  - 创建一个空文件
- cp
  - 拷贝文件到指定目录
  - 基本语法：cp [选项] source dest
  - 常用选项：-r 递归赋值整个文件夹
  - 强制覆盖不提示的方法：\cp
- rm
  - rm [选项] 要删除的文件或目录
  - 常用选项
    - -r：递归删除整个文件夹
    - -f：强制删除不提示
- mv
  - 移动文件与目录或重命名
  - 基本语法
    - mv oldNameFile newNameFile（重命名）
    - mv /temp/movefile /targetFolder（移动文件）
- cat
  - cat [选项] 要查看的文件
  - 常用选项
    - -n：显示行号
  - cat只能查看文件，不能修改文件，为了浏览方便，一般会带上 管道命令 | more
- less
  - 用来分屏查看内容，功能与more类似，但是比more更加强大，支持各种显示终端。less指令在显示文件内容时，并不是一次将整个文件加载后才显示，而是根据显示需要加载内容，对于显示大型文件具有较高的效率
  - less 要查看的文件
- echo
  - 输出内容到控制台
  - echo [选项] [输出内容]
- head
  - 用于显示文件的开头部分内容，默认情况下head指令显示文件的前10行内容
  - 基本语法：
    - head 文件（查看文件头的10行内容）
    - head -n 5 文件（查看文件头5行内容）
- ">"  和 ">>"
  - ls -l > 文件 （列表的内容写入文件中（覆盖写））
  - ls -al >> 文件（列表的内容追加到文件的末尾）
  - cat 文件1 > 文件2（将文件1的内容覆盖到文件2）
  - echo “内容” >> 文件
- ln
  - 软连接，也称符号连接，类似于windows里的快捷方式，主要存放了链接其他文件的路径
  - 基本语法：
    - ln -s [原文件或目录] [软链接名] （给原文件创建一个软链接）
  - 
- history
  - 查看历史操作命令

## 时间日期类

- data
  - 基本语法
    - data（显示当前时间）
    - data +%Y（显示当前年份）
    - data +%m（显示当前月份）
    - data +%d（显示当前天）
    - data “+%Y-%m-%d %H:%M:%S”（显示年月日时分秒）
- cal
  - 显示本月月历

## 搜索查找类

- find
  - 从指定目录向下递归遍历各个子目录，将满足条件的文件或者目录显示在终端
  - find [搜索范围] [选项]
  - 选项说明
    - -name 查询方式（按照指定的文件名查找文件）
    - -user 用户名（查找属于指定用户的所有文件）
    - -size 文件大小（按照指定文件大小查找文件）
- locate
  - 快速定位文件路径
  - 由于locate指令基于数据库进行查询，所以第一次运行前，必须使用updatedb指令创建locate数据库
- grep和管道符号 |
  - 过滤查找，管道符，“|”，表示将前一个命令的处理结果输出传递给后面的命令处理
  - 基本语法：
    - grep [选项] 查找内容 源文件
  - 常用选项：
    - -n：显示匹配行及行号
    - -i：忽略字母大小写


## 压缩和解压类

- gzip/gunzip
  - gzip用于压缩文件，gunzip用于解压
  - 基本语法：
    - gzip 文件（压缩文件，只能将文件压缩为*.gz文件）
    - gunzip 文件.gz

- zip/unzip
  - zip用于压缩文件，unzip用于解压，在项目打包中很有用
  - 基本语法：
    - zip [选项] xxx.zip 将要压缩的内容（压缩文件和目录的命令）
    - unzip [选项] xxx.zip（解压缩文件）
  - zip常用选项
    - -r：递归压缩，即压缩目录
  - unzip常用选项
    - -d<目录>：指定解压后文件存放的目录
- tar
  - tar指令是打包指令，最后打包的文件是.tar.gz的文件
  - 基本语法：
    - tar [选项] XXX.tar.gz 打包的内容
  - 选项说明
    - -c或--create 建立新的备份文件
    - -v或--verbose 显示指令执行过程
    - -f<备份文件>或--file=<备份文件> 指定备份文件
    - -z或--gzip或--ungzip 通过gzip指令处理备份文件
    - -x或--extract或--get 从备份文件中还原文件

# 组管理和权限管理

## 组基本介绍

### 文件/目录 所有者

一般为文件的创建者

- 查看文件所有者：ls -ahl

  ![image-20210707224043819](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210707224043819.png)

- 修改文件所有者：chown 用户名 文件名

### 组的创建

- groupadd 组名

### 文件/目录 所在组

当用户创建了一个文件后，这个文件所在组就是该用户所在的组

- 查看文件/目录所在组：ls -ahl

  ![image-20210707224547936](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210707224547936.png)

- 修改文件所在的组：chgrp 组名 文件名

### 改变用户所在组

在添加用户时，可以指定将该用户添加到哪个组中，同样的用root的管理权限可以改变某个用户所在的组

- 改变用户所在组
  - usermod -g 新组名 用户名
  - usermod -d 目录名 用户名 改变该用户登录的初始目录。特别说明：用户需要有进入到新目录的权限

## 权限基本介绍

![image-20210708201436866](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210708201436866.png)

0-9位说明

- 第0位确定文件类型（d，-，l，c，b）
  - l：链接，相当于快捷方式
  - d：目录，文件夹
  - c：字符设备文件，鼠标键盘
  - b：块设备，硬盘
- 1-3位确定所有者拥有该文件的权限
- 4-6位确定所属组拥有该文件的权限
- 7-9确定其他用户拥有该文件的权限

### rwx权限详解

rwx作用到文件：

- r：代表可读
- w：可写，可以修改单不代表可以删除，删除一个文件的前提是对该文件所在的目录有写的权限
- x：代表可执行

rwx作用到目录：

- r：可读
- w：可写，对目录内创建+删除+重命名目录
- x：可执行，可以进入该目录

### 修改权限-chmod

chmod指令，可以修改文件或者目录的权限

- +，-，= 变更权限

  u：所有者，g：所有组，o：其他人，a：所有人

  - chmod u=rwx,g=rx,o=x
  - chmod o+w
  - chmod a-x

### 修改文件所有者-chown

基本介绍

- chown newowner 文件/目录（改变所有者）
- chown newowner:newgroup 文件/目录（改变所有者和所在组）
- -R（如果是目录，则使其下所有子文件或目录递归生效）

### 修改文件/目录所在组-chgrp

chgrp newgroup 文件/目录（改变所在组）

# 定时任务调度

## crond任务调度

crontab 进行定时任务设置

### 概述

任务调度：是指系统在某个时间执行的特定的命令或程序

任务调度分类：

- 系统工作：有些重要的工作必须周而复始的执行，如病毒扫描
- 个别用户工作：个别用户可能希望执行某些程序，比如对mysql数据库的备份

### 基本语法

- crontab [选项]
- service crond restart （重启任务调度）

### 常用选项

- -e：编辑crontab定时任务
- -l：查询crontab任务
- -r：删除当前用户所有的crontab任务

如：

```
*/1 * * * * ls -l /etc/ > /tmp/to.txt
意思是每小时的每分钟执行ls -l /etc/ > /tmp/to.txt
```

| 项目     | 含义                 | 范围                  |
| -------- | -------------------- | --------------------- |
| 第一个 * | 一小时当中的第几分钟 | 0-59                  |
| 第二个 * | 一天当中的第几小时   | 0-23                  |
| 第三个 * | 一个月当中的第几天   | 1-31                  |
| 第四个 * | 一年当中的第几个月   | 1-12                  |
| 第五个 * | 一周当中的周几       | 0-7（0和7都代表周日） |

### 特殊符号说明

| 特殊符号 | 含义                                                         |
| -------- | ------------------------------------------------------------ |
| *        | 代表任何时间，比如第一个*就代表一小时中没分红执行一次的意思  |
| ,        | 表示不连续的时间。比如“0,8,12,16 * * *”，就代表每天的8点12点16点执行一次命令 |
| -        | 代表连续的时间范围。比如“0 5 * * 1-6”，代表在周一到周六5点执行命令 |
| */n      | 代表每隔多久执行一次。“*/10 * * * *”，代表每隔10分钟执行一次 |

## at定时任务

### 基本介绍

1. at命令是一次性定时计划任务，at的守护进程atd会以后台模式运行，检查作业队列来运行

2. 默认情况下，atd守护进程没60秒检查作业队列，有作业时，会检查作业运行时间，如果时间与当前时间匹配，则运行此作业

3. at命令是一次性定时计划任务，执行完一个任务后不再执行此任务

4. 在使用at命令的时候，一定要保证atd进程的启动，可以使用相关指令查看

   ps -ef

   ![image-20210712204748868](https://zltyporapic.oss-cn-beijing.aliyuncs.com/typoraimgimage-20210712204748868.png)

### at命令格式

at [选项] [时间]

Ctrl + D 结束at命令的输入

### at命令选项

| 选项          | 描述                                                     |
| ------------- | -------------------------------------------------------- |
| -m            | 当指定的任务被完成后，将给用户发送邮件，即使没有标准输出 |
| -I            | atq的别名                                                |
| -d            | atrm的别名                                               |
| -v            | 显示任务将被执行的时间                                   |
| -c            | 打印任务的内容到标准输出                                 |
| -V            | 显示版本信息                                             |
| -q <队列>     | 使用指定的队列                                           |
| -f <文件>     | 从指定文件读入任务而不是从标准输入读入                   |
| -t <时间参数> | 以时间参数的形式提交要运行的任务                         |

### at时间定义

1. 接受在当天的hh:mm式的时间指定。加入该时间已经过去，那么就在第二天执行。
2. 使用midnight，noon，teatime等比较模糊的词语来指定时间
3. 指定12小时计时制，即在时间后面加上AM或PM来说明是上午还是下午
4. 指定命令执行的具体日期，指定格式为month day或mm/dd/yy或dd.mm.yy，指定的日期必须跟在指定的时间后面
5. 使用相对计时法，指定格式为：now + count time-units
6. 直接使用today、tomorrow来指定