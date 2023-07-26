# MySQL-day01

## 1.DB、DBMS、SQL

### **数据库**

- ​	（Database简称DB），按照一定的格式储存数据的一些文件的组合，即储存文件的仓库，实际上就是一堆文件，这些文件储存的数据具有一定的格式

### **数据库管理系统**

- (database management  system简称DBMS)，数据库管理系统是专门用来管理数据库中的数据的，数据库管理系统可以对数据库中的数据进行“增删改查”。常见的数据库管理系统：MySQL、Oracle、Ms、sqlServer、DB2、sybase等等

### **SQL**

-  结构化查询语言，程序员需要学习SQL语句，通过编写SQL语言，然后BDMS负责执行SQL语句，最终来完成数据库中数据的“增删改查”

### 三者之间的联系

- DBMS—执行—\>SQL—操作—\>DB

- SQL语言是一个标准，常见的数据库管理系统都可以执行SQL语句，SQL语句是一种通用的标准的语言，是一种编程语言，程序员主要学习的就是SQL语句，这个SQL在mysql中可以使用，也可以在Oracle中使用，在DB2中也可以使用。 

<img src="https://pic1.zhimg.com/80/v2-d0f503193402398e748205dd10bfe944_1440w.webp" alt="img" style="zoom: 80%;" />

**先安装数据库管理系统DBMS（我们这里安装MySQL），然后学习sql语句怎么写，编写sql语句之后，我们的数据库管理系统（DBMS，这里我们使用的是MySQL）对sql语句进行执行，最终完成数据库的数据管理。**

## 2.安装MySQL数据库管理系统

- 第一步：先安装，选择“经典版”

- 第二步：需要进行MySQL数据库实例配置（一路下一步即可！）

其中需要注意的事项：

### 2.1、端口号：

端口号port是任何一个软件/应用都会有的，端口号是应用的唯一代表。端口号通常和IP地址在一块，IP地址用来定位计算机的，端口号port是用来定位计算机上某个服务或者某个应用的！在同一台计算机上，端口号不能重复，具有唯一性。mysql数据库启动的时候，这个服务占有的默认端口号是3306，这是MySQL这个软件唯一代表，是大家都知道的事情。

- 所谓的端口，就好像是门牌号一样，客户端可以通过ip地址找到对应的服务器端，但是服务器端是有很多端口的，每个应用程序对应一个端口号，通过类似门牌号的端口号，客户端才能真正的访问到该服务器。 为了对端口进行区分，将每个端口进行了编号，这就是端口号。
- 什么是网络端口？
  在网络技术中，端口包括逻辑端口和物理端口两种类型。
  物理端口是用于连接物理设备之间的接口，如ADSL Modem、集线器、交换机、路由器上用于连接其他网络设备的接口。
  逻辑端口是指逻辑意义上用于区分服务的端口，比如用于浏览网页服务的80端口，用于FTP服务的21端口等。
  我们这里讲的是逻辑端口。
- 端口的作用
  端口号的主要作用是表示一台计算机中的特定进程所提供的服务。网络中的计算机是通过IP地址来代表其身份的，它只能表示某台特定的计算机，但是一台计算机上可以同时提供很多个服务，如数据库服务、FTP服务、Web服务等，我们就通过端口号来区别相同计算机所提供的这些不同的服务，如常见的端口号21表示的是FTP服务，端口号23表示的是Telnet服务，端口号25指的是SMTP服务等。

### 2.2、字符的编码方式：

设置MySQL数据库中的字符编码方式的时候选择UTF-8。一定要注意先选中第3个单选按钮，然后再选择UTF-8字符集

### 2.3、服务名称：

默认是MySQL，不用修改

### 2.4、选择配置环境path 

path=其他路径;C:\Program Files(x86)\MySQL Server 5.5\bin

### 2.5、mysql超级管理员用户名

不能改，一定得是默认的：root。我们需要设置MySQL数据库超级管理员的密码。在这里我们设置为：123456。设置密码的同时我们可以激活root账户远程访问。（激活：表示root账号可以在外地登录；不激活：表示root账号只能在本机上使用。）我们这里选择了激活。

## 3.MySQL数据库管理系统的完美卸载！

第一步：双击安装包进行卸载删除。

第二步：删除目录：1.把C:\ProgramData下面的MySQL目录干掉。2.把C:\Program Files (x86)下面的MySQL目录给干掉。

## 4.找MySQL服务

- 看一下计算机上的服务，找一找MySQL的服务在哪里?

  计算机-->右键-->管理-->服务和应用程序-->服务

  MySQL的服务，默认是“启动”的状态，只有启动表示下一次重启操作系统的时候自动启动该服务，同时可以在服务上点击右键：启动、重启服务、停止服务...

  还可以改变服务的默认配置：服务上点击右键，属性，然后可以选择启动的类型方式有：自动、手动、禁用、自动（延迟启动）

## 5、使用命令来启动或关闭mysql服务

在windows操作系统当中，怎么使用命令来启动和关闭mysql服务呢？

使用windows自带的命令框：win+R，然后查询cmd，DOS窗口的命令语法：

net stop 服务名称（停止对应的服务）；（没有分号）

net start  服务名称（启动对应的服务）；（没有分号）

（注意打开cmd的时候要使用管理员的身份打开，不要直接使用win+R然后搜索cmd直接进入，这样的话就不能使用net命令了，要使用管理员的身份打开，主要是我们的环境变量没有C:\Widows\System32这个路径）

这个启停服务的命令不仅仅可以使用在MySQL这个服务，其他的服务都可以使用这个启停的命令。

​                                               <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230716204518913.png" alt="image-20230716204518913"  /> 

​                                                   <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230716204548947.png" alt="image-20230716204548947" style="zoom:50%;" />    

​                 

## 6、登录MySQL

mysql以及安装了，服务也通过net命令启动了，那么我们怎么使用客户端来登录mysql数据库。使用DOS命令窗口来完成mysql的一些命令。在C盘文件下的mysql文件中有一个mysql.exe命令，用这个服务器可以链接mysql数据库服务器。

**登录语法：**

**本地登录（显示密码的形式）:**

**mysql -uroot -p123456**（然后回车，其中u是username ，p是password，这种链接mysql服务器的方式是密码可以直接看到的，也有一种方式是可以输入密码的时候是隐藏的）

**本地登录（隐藏密码的形式）**

**mysql -utoot -p**（然后回车，其中u是user，p是password，回车之后就会出现“Enter password：”然后你直接输入你的密码就可以了，显示的就是*******\*\*\*这种形式）

**登录成功的标志：出现mysql>**

## 7、mysql常用命令

mysql命令都必须在mysql服务处于启动状态，并且必须登录mysql之后才能使用，也就是要出现**mysql>**

- 退出mysql： **exit**（之后命令窗口与就会出现bye，经过测试exit命令也可以以分号结尾，有没有分号都是不报错的）

- 查看/展示mysql中有哪些数据库：**show databases;**（以英文符号结尾，命令窗口就会展示出mysql数据管理系统重的所有的数据库，一定不要忘记了分号）

  

  ```
  mysql> show databases;
  +--------------------+
  | Database           |
  +--------------------+
  | information_schema |
  | mysql              |
  | performance_schema |
  | test               |
  +--------------------+
  5 rows in set (0.00 sec)
  ```

  4 rows in set (0.02 sec)

  （上述表示mysql默认自带了四个数据库）

- 我们怎么选中使用哪个数据库呢: **use 数据库名;**（这里经过测试发现有没有分号都是可行的，使用use加上对应要选择的数据库即可）。

- 如何创建一个数据库： **create database 数据库名;**（这里测试过分号不能漏，这是自创一个数据库，数据库名可以自己选定，建立完数据库之后可以使用show databases; 的语法查看mysql数据库管理系统中有多少个数据库）


```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| bjpowernode        |
| mysql              |
| performance_schema |
| test               |
+--------------------+
5 rows in set (0.00 sec)
```

- 查看数据库下有哪些表：**show tables；**

- 查看mysql数据库的版本号：**select version();**

  ```
  mysql> select version();
  +-----------+
  | version() |
  +-----------+
  | 5.5.36    |
  +-----------+
  1 row in set (0.01 sec)
  ```

  

- 查看当前使用的什么数据库：**select database();**

```
mysql> select database();
+-------------+
| database()  |
+-------------+
| bjpowernode |
+-------------+
1 row in set (0.00 sec)
```

- 如何终止未执行的sql命令：**\c**   (—>这个符号表示sql的命令还没有结束，一旦你\c就可以终止这个未完成的命令，然后继续从mysql>开始)
- 

**注意：1.以上的命令都不区分大小写;2.mysql中end  with ; or  \g**

## 8、BD基本单位：table

数据当中最基本的单元是表table，什么是表？为什么用表table来存储数据呢？

数据库中是以表格的形式来保存数据的，为什么？因为表比较直观，任何一张表都有行和列。

姓名   性别  年龄（列 ：字段）

-------------------------------------------

张三     男    20     ------------->(行：记录) 

李四     女    21 	------------->(行：记录) 

王五     男    22	 ------------->(行：记录) 

行（row）：被称为数据/记录

列（column）：被称为字段

数据库当中的每个字段都有字段名、数据类型、约束等属性。（例如你注册账号的的时候，输入用户名有时候会要求用户名不能重复，就会在对应字段处设置约束）。其中字段名就是一个见名之意的名称，数字类型有字符串、数字、日期等等，约束也有很多（其中有一个叫做唯一性约束，这种数据一旦添加之后该字段中的数据就不能重复了）

拓展的知识点：

### **1、命令行客户端**

- 命令行客户端是通过命令行界面和特定的程序或者服务器进行交互的工具。（这里例如数据库管理系统中，通过命令行界面与数据库进行交互）。在mysql数据库管理系统中，mysql命令行客户端是官方提供的命令行界面工具，该命令行客户端允许用户在命令行输入各种MySQL语句或者SQL查询完成跟mysql服务器的通信和操作，只用命令行客户端，可以在控制台上直接执行，完成对数据库的管理和查询。

- Mysql命令行客户端可以通过命令行界面与Mysql服务器进行交互（直接在客户端连接到mysql服务器），	选择数据库之后，可以执行查询、更新数据、创建表、创建数据库、管理用户访问权限等多种功能。它是一种十分强大和灵活的工具，尤其适合那些喜欢使用控制台（命令行界面）进行数据库操作的开发人员和系统管理人员。	

## 9、SQL查询语言的分类

SQL语言（Structure Query Language）是数据库的核心语言，SQL是一个标准的数据库语言，是面向集合的描述性非过程化语言，它功能强，效率高，易学易维护，但由于SQL是描述性而非过程化语言，即大多数语句都是独立执行的，与上下文无关，而绝大部分的应用都是一个完整的过程，显然用SQL完全实现这些功能是很困难的。

由于sql查询语言有很多的语句，所以进行了分门别类，这样更加便于记忆，分为：

**DQL**：

​		**数据查询语言**（凡是带有select关键字的都是查询语句）

​		select...

**DML**：

​		**数据操作语言**（凡是对表当中的数据继续增删改的都是DML）

​		insert delete update

​		insert    增 

​		delete   删

​		update 改

**DDL**：

​		**数据定义语言**

​		凡是带有create、drop、alter的都是DDL

​		DDL主要操作的是表的结构（例如字段或者记录）而不是表中的数据

​		create：新建（等同于增）

​		drpp：删除

​		alter：修改（等同于改）

​		这里的增删改主要针对的是对表结构进行操作，与DML不同

**TCL：**

​			**事务控制语言**

​			包括：

​			事务提交（commit）

​			事务回滚（rollback）

**DCL：**

​			**数据控制语言**

​			例如：授权（grant）、撤销权限（revoke）...

补充版本

sql语言介绍

sql（Structure Query language）语言是数据库语言，sql是一个标准的数据库语言，是面向集合的描述性而非过程化的语言，它功能性强，效率高，易学易维护，但是由于sql是面向集合的描述性而非过程化的语言，即大多数语句都是独立执行的，与上下文无关，而绝大多部分的应用都是一个完整的过程，显然用sql完全实现这些功能是很困难的。

Structure结构，query查询，language语言。

sql语言分类

1.DQL(database query language)数据查询语言：对数据查询操作

语句:称为数据库检索语句，用于从表格中获取数据，保留字select，SELECT是dql中用的最多的动词，其他的dql保留字有WHERE（子查询where）、ORDERBY（orderby以...排序），GROUP（分组）和HAVING（having）

2.DML（database manipulation language）数据操作语言：对数据插入、删除和更新三种操作

语句：包括动词insert、update和delet，分别用于增改删

3.DCL（database control  language）数据控制语言：对用户访问数据的控制基本表现和视图的授权以及回收

语句：通过grant授予权限，通过revoke收回权限

4.DDL（database definition language）数据定义语言：定义数据库的逻辑结构，包括表，视图，索引和数据库四个部分。

语句：包括动词（create创造）、（alert修改）和（drop删除）

5.TCL（transaction control language）事务控制语句：对事务的提交和回流

语句：为了确保被DML语句影响的表现及时更新，包括commit（提交命令）、savepoint（保存点命令），rollback（回滚命令）

## 10.往数据库中导入数据

我们如何在我们create的bjpowernode这个数据库中导入我们提前准备好的数据呢？

bjpowernode.sql这个文件中是提前准备好的为大家练习用的数据库表，然后现在我们需要把这个表格导入到我们指定的数据库中，使用一个sql命令 

语法： source  数据的绝对磁盘路径

注意：这个路径当中不能出现中文！！！C:\Users\14214\Documents\bjpowernode

## 11.认识导入的表

关于导入的这几张表的认识

我们通过把bjpowernode.sql这个文件导入到我们创建的数据库中之后，那么我们现在可以看看我们导入的数据（表）有什么些内容，我们可以使用一个命令查看表格。

- 查看数据库中有哪些表格的语法：**show  tables;**

```
mysql> show tables;
+-----------------------+
| Tables_in_bjpowernode |
+-----------------------+
| dept                  |
| emp                   |
| salgrade              |
+-----------------------+
3 rows in set (0.00 sec)
```

其中，dept是部门表department，emp是雇员表employee，salgrade是工资等级表salarygrade。关于导入的这几张表，我们想查看表中的数据，改怎么查看？

- 统一查看某个表中的具体数据的SQL语句语法：**SELECT  *  from 表名;**（表示从数据库中某个指定的表中查询所有的数据，这其实是算dql数据查询语言）

```
mysql> select * from dept;
+--------+------------+----------+
| DEPTNO | DNAME      | LOC      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)

mysql> select * from emp
    -> ;//Welcome to the MySQL monitor.  Commands end with ; or \g.
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
14 rows in set (0.00 sec)

mysql> select * from salgrade;
+-------+-------+-------+
| GRADE | LOSAL | HISAL |
+-------+-------+-------+
|     1 |   700 |  1200 |
|     2 |  1201 |  1400 |
|     3 |  1401 |  2000 |
|     4 |  2001 |  3000 |
|     5 |  3001 |  9999 |
+-------+-------+-------+
5 rows in set (0.00 sec)
```

12.查询表结构

- 不如果我们不查看表中的具体的数据，只是去查看表的结构，有一个sql命令：**desc 表名;**

```
mysql> desc emp;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| EMPNO    | int(4)      | NO   | PRI | NULL    |       |员工编号
| ENAME    | varchar(10) | YES  |     | NULL    |       |员工名字
| JOB      | varchar(9)  | YES  |     | NULL    |       |工作岗位
| MGR      | int(4)      | YES  |     | NULL    |       |上级编号
| HIREDATE | date        | YES  |     | NULL    |       |入职日期
| SAL      | double(7,2) | YES  |     | NULL    |       |工资
| COMM     | double(7,2) | YES  |     | NULL    |       |补助
| DEPTNO   | int(2)      | YES  |     | NULL    |       |部门编号
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.02 sec)

mysql> desc dept;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| DEPTNO | int(2)      | NO   | PRI | NULL    |       |部门编号
| DNAME  | varchar(14) | YES  |     | NULL    |       |部门名字
| LOC    | varchar(13) | YES  |     | NULL    |       |地理位置
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.02 sec)

mysql> desc salgrade;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| GRADE | int(11) | YES  |     | NULL    |       |工资等级
| LOSAL | int(11) | YES  |     | NULL    |       |最高工资
| HISAL | int(11) | YES  |     | NULL    |       |最低工资
+-------+---------+------+-----+---------+-------+
3 rows in set (0.01 sec)
```

如果后续然你查询员工薪资，查询工资等级等等，如果记不住表中列（字段）的话，就可以使用desc这个命令去查询某个数据库中某个表的结构，然后就能找到某某表中都有哪些字段。然后再去写sql语句。其实这desc这个命令值的describe描述的缩写，所以”desc 表名“就是描述表的结构。

## 13.简单查询

**13.1、查询一个字段？**

- select 字段名 from 表名;
- 其中要注意：select和from都是关键字，字段名和表名都是标识符。
- 强调：对于sql语句来说这几点都是通用的：所有的sql语句以“；”结尾，并且sql语句是不区分大小写的。

查询部门名字？

```
mysql> select DNAME from dept;
+------------+
| DNAME      |
+------------+
| ACCOUNTING |
| RESEARCH   |
| SALES      |
| OPERATIONS |
+------------+
4 rows in set (0.00 sec)
```

**13.2、如果想在某个表中一次select两个或者多个字段该怎么办？**

使用逗号隔开字段，即同时查找部门编号和部门名。

```
mysql> select DNAME from dept;
+------------+
| DNAME      |
+------------+
| ACCOUNTING |
| RESEARCH   |
| SALES      |
| OPERATIONS |
+------------+
4 rows in set (0.00 sec)

mysql> select dname,deptno from dept;
+------------+--------+
| dname      | deptno |
+------------+--------+
| ACCOUNTING |     10 |
| RESEARCH   |     20 |
| SALES      |     30 |
| OPERATIONS |     40 |
+------------+--------+
4 rows in set (0.00 sec)
```

**13.3、查询所有的字段怎么办？**

- 第一种方式：可以把表中的所有字段都写出来，并且使用逗号隔开。select  字段1，字段2 ，... from  表名;
- 第二种方式：可以使用模糊匹配的概念，用*代替某表中所有的字段。select * from 表名;

第二种方式的缺点是：可读性比较差，效率低，在实际开发中不建议使用这种方式，可以自己在DOS命令窗口中使用这个命令来快速查看一下全表中的数据，效率低是因为*会先一个一个转化成所有字段然后再展示出来。

**13.4、如何给查询的列起别名？**

- 也就是给查询的字段起一个别名，现在我们想查询部门的名字和部门的编号，然后把其中的DNMAE修改为DEPTNAME。使用as关键字来给查询的列起别名，也就是给要查询的字段起个别名。

- 注意：select语句是永远不会对数据库中的数据做任何更改操作的，select语句只负责起查询作用，所以我们这里的在查询字段的时候使用了as关键字之后，只是将查询出俩结果的列名显示为deptname，数据库中的dname依旧是dname。可以使用select分别验证一下哪个有效。

- 其中as关键字可以省略吗 ？可以，但是不能把as换成逗号，直接省略，变成改名前和改名后之间只有一个空格就可以了。

  select deptno，dname  deptname from dept；

- 假设起别名的时候，这个别名中有空格怎么办？

  mysql>select   deptno ,dname dept name from dept;

  DBMS看到这样的语句，进行sql语句的编译会发现不符合语法，编译就会报错，因为这里当识别到deptno之后就看到逗号了，然后知道后面的也是一个要查询的字段dname，然后继续识别发现一个空格，就会把接下来的dept当做是dname要修改成dept的列的别名，然后识别到空格就期待出现from关键字，但是没有发现from关键字，所以就会报错。**所以怎么解决，只需要把dept name这个有空格的列别名用单引号括起来就可以规避这个报错。**
  
  **mysql>select deptno,dname 'dept name' from dept;**
  
  ---
  
- ***注意：在所有的数据库当中，字符串统一使用单引号括起来，单引号是标准，字符串用双引号括起来在mysql数据库中可以使用，但是在Oracle数据库中无法使用。所以：数据库中的字符串标准表示方法就是用单引号括起来。***

```
mysql> select deptno,dname as deptname from dept;//未省略as关键字给列起别名
+--------+------------+
| deptno | deptname   |
+--------+------------+
|     10 | ACCOUNTING |
|     20 | RESEARCH   |
|     30 | SALES      |
|     40 | OPERATIONS |
+--------+------------+
4 rows in set (0.00 sec)

mysql> select detpname from dept;//测试起给列起别名会不会修改数据库的字段名？不会
ERROR 1054 (42S22): Unknown column 'detpname' in 'field list'
mysql> select dname from dept;
+------------+
| dname      |
+------------+
| ACCOUNTING |
| RESEARCH   |
| SALES      |
| OPERATIONS |
+------------+
4 rows in set (0.01 sec)
mysql> select deptno,dname deptname from dept;
//省略as关键字，但不能使用逗号隔开，可以直接省略，变成空格
+--------+------------+
| deptno | deptname   |
+--------+------------+
|     10 | ACCOUNTING |
|     20 | RESEARCH   |
|     30 | SALES      |
|     40 | OPERATIONS |
+--------+------------+
4 rows in set (0.02 sec)

mysql> select deptno,dname dept name from dept;
//要起的别名是个短语（或者自带空格）的话，这样会报错
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'name from dept' at line 1
mysql> select deptno,dname 'dept name'from dept;//遇到别名是短语的时候可以使用''或者""即可 
+--------+------------+
| deptno | dept name  |
+--------+------------+
|     10 | ACCOUNTING |
|     20 | RESEARCH   |
|     30 | SALES      |
|     40 | OPERATIONS |
+--------+------------+
4 rows in set (0.00 sec)
```

13.5、计算员工的年薪？

年薪：sal*12-->查询员工的工资并且乘上12-->**select ename,sal\*12 from emp;**

**结论：字段可以参与运算，即字段可以使用数学表达式**，也就是字段可以使用加减乘除运算的。

但是这样显示出来的年薪的使用sal\*12表示的，我们为了看起来更加直观，可以在给字段运用数学表达式的时候，起个别名。但是如果这个别名是一个短语或者中文的话，你就必须使用单引号括起来，英文字符串的数据库中字符串的表示方式就是使用单引号括起来。

## 14.条件查询

14.1、什么是条件查询？  

什么是条件查询，条件查询不是某个数据库中的某个表中的所有的数据都一次性全部查出来，而是有选择的只查询出来符合条件的。

