## 1、准备工作

安装好MySQL软件之后，这个软件就是客户端，点开之后就会跳出一个黑框框，而这个黑框框就是MySQL自带的客户端，也就是我们未来工作中最主要的使用的客户端，然后这个黑框框就会显示一个“enter password”，这个密码就是你安装数据库的时候配置的，这个密码尽量配置的简单一点，因为到时候解决起来比较麻烦（忘记密码后，可以选择重装，这算是比较好的解决方法了，MySQL的完美卸载比较麻烦，但是老杜教我了哈哈哈）。输入密码之后（123456），你就可以看到你个界面，这个界面就是数据库客户端。

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230811123456855.png" alt="image-20230811123456855" style="zoom: 33%;" />

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230811123658546.png" alt="image-20230811123658546" style="zoom:33%;" />

## 2、查看MySQL的服务器

步骤：在开始处搜索“服务”两个字，点开就可以了，然后你就可以看见MySQL的服务器，当前使用的是5.7版本的，数据库现在最新的是8.0系列，当前的课堂还是不建议使用8.0版本的，因为这个系列很多东西都处理的比较复杂，我们尽量使用更加稳定长久的5.0系列的MySQL版本。（老杜也有教我通过其他方式打开MySQL数据库的服务器）计算机-->右键-->管理-->服务和应用程序-->服务

3、客户端和服务器的关系以及概念

在客户端进行的任何操作，都会通过”网络“传输给服务器，由服务器进行处理，即使我们MySQL的客户端和服务器是在同一个主机上。

- 要是我们电脑现在没有联网，但是我们的MySQL还是还是可以连接上我们的服务器？

  你这里的没有联网指的是你没有连接外面的网络，这不影响你自己主机上的程序之间的通讯。

<img src="C:\Users\14214\Pictures\图片笔记\MySQL\引入MySQL数据库.png"  />

---

## 3、(数据库)SQL命令

汤老师把MySQL、Oracle、MiscroSoft SQL Server等等这些称为数据库，但是在老杜的课堂里把这些软件称作数据库管理系统。老杜讲的是数据库管理系统DBMS去执行SQL语句，然后去操作数据库。而汤老师讲的是在数据库客户端通过SQL语句（命令行客户端）去操作数据库（逻辑上的数据库）。

**sql语句不区分大小写**（但是小写可能更容易看清楚，看个人习惯）

### 1）显示数据库



- **语法：show databases;** 

 显示当前所有的数据库。 (show 和databases之间至少有一个空格，而且还要有一个英文分号结尾；databases是负数)

小技巧：由于编程中所有的标点符号都是英文，我们可以打开搜狗输入法的设置，然后设置为“中文时使用英文标点”。以后就不用担心标点符号可能会有中英的区别了。

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| bjpowernode        |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)//这里的sec其实是second秒，这里表示小于10ms
```

s时间的单位换算

1s = 1000ms（1秒=1000毫秒）

1ms =1000um（1毫秒=1000微秒）

1um = 1000nm（1微秒=1000纳秒）

1nm = 1000ps（1微秒 = 1000皮秒）



### 2）创建数据库

- **语法：create database 数据库名;** 

   (SQL语句是不支持使用关键字来命令的，但是你如果要使用跟关键字拼写相同单词，就使用反引号把它与关键字区别开来)

- **语法：create database if not exists  数据库名;**

  （这个是判断要创建的数据库名是否已经在服务器的存储器汇总存在，如果存在就不创建该数据库了，如果不存在就可以直接创建）

- 为什么会有这条判断数据库是否已经创建的命令呢？

  这是因为我们通常在工作中执行sql语句的时候，其实不是在命令行（控制台）里一行一行的敲，而是把一组要执行的sql语句写在一个文件中，然后批量执行，而这个时候如果这个文件当中有创建一个数据库这样的命令，如果你使用**create database 数据库名;** 来创建的话，命令行会报错，也就意味着停止，所以这个时候，我们可以使用 **create database if not exists 数据库名;** 来预判一下是否存在，如果存在就不会创建数据库，但是命令行不会停止执行命令，如果不存在就会完成创建。

  

### 3）删除数据库

**语法：drop database 数据库名;**  

注意：执行数据库删除操作将永久删除所有数据库中的数据，操作需谨慎。

![](C:\Users\14214\Pictures\图片笔记\MySQL\关于数据库的操作.png)

### 4）选中数据库

**语法： use 数据库名;**

我们要对数据库进行任何的增删改查等等操作，都必须先选中数据库，然后才能继续进行。

后续的对数据库的操作的前提是你必须选中在服务器的存储器上的外存上的具体哪一个数据库。这就涉及到了选中数据库的sql语句。

### 6）sql命令小技巧  

在客户端输入sql命令的时候，有一些小技巧

- 使用上下方向键，可以找到追溯到上一步和找到下一步执行过的命令

- 如果有一个sql语句输入一半没有终止，你可以按 **ctrl+c**来终止没有执行完的sql语句，回车之后就会显示一个^C（这个符号就表示的是ctrl+C），或者你按**\c**也可以终止没有执行完的sql语句。（ctrl+c是在命令行中终止当前操作/终止当前输入的，在以后的客户端，只要是命令行都可以使用）

- SQL当中的关键字不能拿来命名（关键字是含有特定含义的单词，一般不能拿来作为数据库名、表名、列名等等）。如果实在想使用这些关键字来命名，就可以使用**反引号``**，把你需要使用的跟关键字同样的单词使用反引号括起来然后拿来命名，这是因为反引号括起来的是字符串的形式。

- 反引号的位置：

  反引号在键盘的左上角，tab键的上面，esc键的下面。在sql中，sql是允许我 牌们把反引号括起来的关键字跟关键字拿来区别的。这样就不怕使用关键字命名冲突然后命令行就会报错。

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| bjpowernode        |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
5 rows in set (0.00 sec)

mysql> create database create;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'create' at line 1
//这里的报错信息就准确的告诉你如果要使用create跟关键字相同的单词来命名，你就必须使用反引号以示区分。
mysql> create database `create`;//这里使用反引号来告诉s执行sql语句的数据库管理系统把create与关键字区分开来
Query OK, 1 row affected (0.01 sec)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| bjpowernode        |
| create             |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
6 rows in set (0.00 sec)
//你在删除跟关键字同拼写的数据库名的时候，也要记得使用反引号以示区分，不然也会报错的
mysql> drop database create;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'create' at line 1
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| bjpowernode        |
| create             |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
6 rows in set (0.00 sec)

mysql> drop database `create`;
Query OK, 0 rows affected (0.02 sec)

```

## 4、总结

1. 数据库是什么？
2. 数据库管理系统有哪些？
3. 学习数据库主要学什么？
4. mysql基本组织数据的结构（关系型数据库组织数据都是这种结构）
   1. 客户端服务器结构（服务器是本体）
   2. 一个服务器类似于一台计算机，可以保存多个数据库
   3. 每个数据库的基本单位都是表
   4. 每个表里有很多行（行被称为：记录）
   5. 每一行里有很多列（列被称为：字段）
5. 对数据库的操作
   1. 查看数据库 show databases;
   2. 创建数据库 create database 数据库名;（反引号加以区别关键字）
   3. 选中数据库  use 数据库名;
   4. 删除数据库  drop database 数据库名;（非常危险的操作，特别是在）



---

## 5、常用数据类型

### MySQL中常用的数据类型

MySQL 中定义数据字段的类型对你数据库的优化是非常重要的。

MySQL 支持多种类型，大致可以分为三类：**数值**、**日期/时间和字符串(字符)类型。**

------

### **数值类型**

（这个版本是在MySQL教程看的，其他的就都是在SQL教程的关于MySQL数据库对应的数据类型）

MySQL 支持所有标准 SQL 数值数据类型。

这些类型包括严格数值数据类型(INTEGER、SMALLINT、DECIMAL 和 NUMERIC)，以及近似数值数据类型(FLOAT、REAL 和 DOUBLE PRECISION)。

关键字INT是INTEGER的同义词，关键字DEC是DECIMAL的同义词。

BIT数据类型保存位字段值，并且支持 MyISAM、MEMORY、InnoDB 和 BDB表。

作为 SQL 标准的扩展，MySQL 也支持整数类型 TINYINT、MEDIUMINT 和 BIGINT。下面的表显示了需要的每个整数类型的存储和范围。

|     类型     |                    大小                    | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| :----------: | :----------------------------------------: | :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------- |
|   TINYINT    |                  1 Bytes                   | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
|   SMALLINT   |                  2 Bytes                   | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
|  MEDIUMINT   |                  3 Bytes                   | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER |                  4 Bytes                   | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
|    BIGINT    |                  8 Bytes                   | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
|    FLOAT     |                  4 Bytes                   | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
|    DOUBLE    |                  8 Bytes                   | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
|   DECIMAL    | 对DECIMAL(M,D) ，如果M>D，为M+2，否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |

翻译：（tiny小小）（small小）  （medium中等）（int大）  （decimal十进制）

---

### Number 类型（同上）

| 数据类型        | 描述                                                         |
| :-------------- | :----------------------------------------------------------- |
| TINYINT(size)   | 带符号-128到127 ，无符号0到255。                             |
| SMALLINT(size)  | 带符号范围-32768到32767，无符号0到65535, size 默认为 6。     |
| MEDIUMINT(size) | 带符号范围-8388608到8388607，无符号的范围是0到16777215。 size 默认为9 |
| INT(size)       | 带符号范围-2147483648到2147483647，无符号的范围是0到4294967295。 size 默认为 11 |
| BIGINT(size)    | 带符号的范围是-9223372036854775808到9223372036854775807，无符号的范围是0到18446744073709551615。size 默认为 20 |
| FLOAT(size,d)   | 带有浮动小数点的小数字。在 size 参数中规定显示最大位数。在 d 参数中规定小数点右侧的最大位数。 |
| DOUBLE(size,d)  | 带有浮动小数点的大数字。在 size 参数中规显示定最大位数。在 d 参数中规定小数点右侧的最大位数。 |
| DECIMAL(size,d) | 作为字符串存储的 DOUBLE 类型，允许固定的小数点。在 size 参数中规定显示最大位数。在 d 参数中规定小数点右侧的最大位数。 |



---

### Text 类型

| 数据类型         | 描述                                                         |
| :--------------- | :----------------------------------------------------------- |
| CHAR(size)       | 保存固定长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的长度。最多 255 个字符。 |
| VARCHAR(size)    | 保存可变长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的最大长度。最多 255 个字符。**注释：**如果值的长度大于 255，则被转换为 TEXT 类型。 |
| TINYTEXT         | 存放最大长度为 255 个字符的字符串。                          |
| TEXT             | 存放最大长度为 65,535 个字符的字符串。                       |
| BLOB             | 用于 BLOBs（Binary Large OBjects）。存放最多 65,535 字节的数据。 |
| MEDIUMTEXT       | 存放最大长度为 16,777,215 个字符的字符串。                   |
| MEDIUMBLOB       | 用于 BLOBs（Binary Large OBjects）。存放最多 16,777,215 字节的数据。 |
| LONGTEXT         | 存放最大长度为 4,294,967,295 个字符的字符串。                |
| LONGBLOB         | 用于 BLOBs (Binary Large OBjects)。存放最多 4,294,967,295 字节的数据。 |
| ENUM(x,y,z,etc.) | 允许您输入可能值的列表。可以在 ENUM 列表中列出最大 65535 个值。如果列表中不存在插入的值，则插入空值。**注释：**这些值是按照您输入的顺序排序的。可以按照此格式输入可能的值： ENUM('X','Y','Z') |
| SET              | 与 ENUM 类似，不同的是，SET 最多只能包含 64 个列表项且 SET 可存储一个以上的选择。 |

翻译：var 变量

---



>**注意：**以上的 size 代表的并不是存储在数据库中的具体的长度，如 int(4) 并不是只能存储4个长度的数字。
>
>实际上int(size)所占多少存储空间并无任何关系。int(3)、int(4)、int(8) 在磁盘上都是占用 4 btyes 的存储空间。就是在显示给用户的方式有点不同外，int(M) 跟 int 数据类型是相同的。
>
>例如：
>
>1、int的值为10 （指定zerofill）
>
>```sql
>int（9）显示结果为000000010
>int（3）显示结果为010
>```
>
>就是显示的长度不一样而已 都是占用四个字节的空间

---

### Date 类型

| 数据类型    | 描述                                                         |
| :---------- | :----------------------------------------------------------- |
| DATE()      | 日期。格式：YYYY-MM-DD**注释：**支持的范围是从 '1000-01-01' 到 '9999-12-31' |
| DATETIME()  | *日期和时间的组合。格式：YYYY-MM-DD HH:MM:SS**注释：**支持的范围是从 '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59' |
| TIMESTAMP() | *时间戳。TIMESTAMP 值使用 Unix 纪元('1970-01-01 00:00:00' UTC) 至今的秒数来存储。格式：YYYY-MM-DD HH:MM:SS**注释：**支持的范围是从 '1970-01-01 00:00:01' UTC 到 '2038-01-09 03:14:07' UTC |
| TIME()      | 时间。格式：HH:MM:SS**注释：**支持的范围是从 '-838:59:59' 到 '838:59:59' |
| YEAR()      | 2 位或 4 位格式的年。**注释：**4 位格式所允许的值：1901 到 2155。2 位格式所允许的值：70 到 69，表示从 1970 到 2069。 |

*即便 DATETIME 和 TIMESTAMP 返回相同的格式，它们的工作方式很不同。在 INSERT 或 UPDATE 查询中，TIMESTAMP 自动把自身设置为当前的日期和时间。TIMESTAMP 也接受不同的格式，比如 YYYYMMDDHHMMSS、YYMMDDHHMMSS、YYYYMMDD 或 YYMMDD。



## 6、（数据表）SQL命令

我们在进入客户端之后，进入并操作好数据库之后，然后就可以开始操作数据表了。

以下是一些围绕着数据表的相关操作

1. 创建表
2. 查看有哪些表
3. 查看指定表的结构
4. 删除表

我们在操作数据表之前要先具备一个前置知识，那就是要先认识一下mysql里的**“数据类型”**有哪些？这里的数据类型其实也可java等等编程语言一样都是对数据进行了分类。

- **代码编辑器**

  我们可以把SQL命令写在一个文件中，这个文件可以以SQL作为扩展名，然后我们就可以使用IDEA等等工具打开，然后开始编写SQL命令写好之后就可以复制粘贴到我们的终端上（命令行客户端），然后开始执行，这样的好处是便于编写而且可以随时修改，如果我们只在客户端进行一句一句的执行MySQL语句的话，这样很容易一旦出现了一个错误，就不能往上行进行修改操作。（—>这个符号是指向当前行的，所以你的编辑只能在当前行，如果你发现之前写的有错，你就必须把这整个SQL语句执行的命令都退出才可以，所以这个时候就体现出来吧SQL命令写在文件中复制粘贴到文本文件中的好处）。

  可代码编辑器可以使用IDEA、VSCode等等其他代码编辑器，工作中也经常把SQL写成文件，目的是为了后续在其他机器上批量执行。我们写的SQL代码也可以保存在SQL文件里，然后上传到github上。

- **SQL注释**

  - 语法：**comment  注释**

  使用在创建表的时候，可以在每个列数据类型后逗号前的地方写上注释。可以在每个列这里加上comment注释，不影响SQL执行，只是起到解释说明的作用。只能用在建表的时候，增加字段的说明。

  - 语法： **-- 注释**   

  注意--后面必须有空然后再开始写注释的内容。这种注释方式更加的常见。（两个横线和注释之间必须添加空格）

### 1）创建表

- **语法：**

**create table 表名(列名 数据类型,列名  数据类型 ......);**

**create table 表名;**

```sql
create table table_name(
field1 datatype,
field2 datatype,
filed3 datatype
);
```

```sql
create table stu_test(
id int,
name varchar(20) comment '姓名', 
password varchar(50) comment '密码',
age int,
sex varchar(1),
birthday timestamp,
amout decimal(13,2),
resume text comment '恢复'
);-- 添加注释的方法，可以在创建表的时候，给字段添加注释，comment增加字段说明，只能在这个时候用。
```

![image-20230813193843286](C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230813193843286.png)

- 给当前的数据库建一个表，创建表的时候可以指定多个列，多个列使用逗号隔开。也可以不指定列。
- 我们通常在java、C++、C语言中都是类型在前，变量名在后。但是在我们的SQL中是刚好相反的，我们可以自定义的标识符列名就先写，然后对应的数据类型就写在变量名的后面。Go、Python/TypeScript等等这些也是类型在后，变量名在前。
- **注意事项：**
  - 创建表的时候需要保证在同一个数据库中不能有同名的表；
  - 创建表的时候需要保证表明不和关键字重复，但是你可以使用反引号``把跟关键字拼写相同的单词引起来加以区分。
  - 由于我们在建表的时候因为建表语句比较长，我们可以把SQL语句分成多行来写，不过还是写在SQL文档中，因为你很有可能在写的过程中写的很僵硬，写错之后不好修改，光标不容易回到前一行，所以我们还不如写在SQL文本文档中然后我们就复制粘贴到客户端（命令行/终端/控制台）里执行，更方便去编辑。

### 2）查看表

**语法：show tables;**

查看当前数据库的所有的表，显示的格式跟你查看MySQL服务器上所有的数据库一样。

### 3）查看表结构

**语法：desc 表名;**

这里desc是describe的缩写，是专门用来描述表结构的SQL命令

实例：

```sql
mysql>  show tables;
+-------------------+
| Tables_in_java105 |
+-------------------+
| stu_test          |
| student           |
+-------------------+
2 rows in set (0.00 sec)
mysql> desc student;
+-------+--------------+------+-----+---------+-------+
| Field | Type         | Null | Key | Default | Extra |
+-------+--------------+------+-----+---------+-------+
| id    | int(11)      | YES  |     | NULL    |       |
| name  | varchar(200) | YES  |     | NULL    |       |
+-------+--------------+------+-----+---------+-------+
2 rows in set (0.00 sec)
```





### **4）删除表**

**语法： drop  table 表名;**

- 删表需谨慎，比删库甚至可能更严重，因为删了之后，访问数据库的时候不一定能及时发现表被删了。

---

### 5)总结

数据库操作

1. 创建数据库  create database 数据库名;
2. 显示数据库  show  databases;
3. 选中数据库  use 数据库名;
4. 删除数据库   drop database  数据库名；

表操作

1. 创建表  create table 表名;
2. 查看表  show tables;
3. 查看表结构 desc 表名;
4. 删除表  drop table 表名;

---

## 7、数据库编码问题

- **ASCII码**

>ASCII（American Standard Code for Information Interchange，美国信息互换标准代码）是一套基于拉丁字母的字符编码，共收录了 128 个字符，用一个字节就可以存储，它等同于国际标准 ISO/IEC 646。
>
>ASCII 编码于 1967 年第一次发布，最后一次更新是在 1986 年，迄今为止共收录了 128 个字符，包含了基本的拉丁字母（英文字母）、阿拉伯数字（也就是 1234567890）、标点符号（,.!等）、特殊符号（@#$%^&等）以及一些具有控制功能的字符（往往不会显示出来）。
>
>ASCII 编码是美国人给自己设计的，他们并没有考虑欧洲那些扩展的拉丁字母，也没有考虑韩语和日语，我大中华几万个汉字更是不可能被重视。计算机也是美国人发明的，起初使用的就是 ASCII 码，只能显示英文字符。各个国家为了让本国公民也能正常使用计算机，开始效仿 ASCII 开发自己的字符编码，例如 ISO/IEC 8859（欧洲字符集）、shift_Jis（日语字符集）、GBK（中文字符集）等。



---

- 我们常用的汉字就有4000多个，然后还有什么生僻字/繁体字有6w多个，对于计算机来说这个数量也不是很多，但是按照ASCII码的发明的思路，我们还是用数字来表示汉字。只不过需要一个容量更大的表，来表示汉字和数字之间的关系，像这种表示汉字的表有很多个版本：Unicode 、GBK、utf8（是Unicode压缩的一个版本，有一定的联系，但是还是视为不同版本）。

- 那么我们可以设置不同版本的字符集来表示汉字，但是在数据库中如果我们使用了不匹配的字符集，就会出现乱码的问题。（数据库默认的字符集是拉丁文，这个不支持汉字）。

- 为什么utf8字符编码使用比较广泛？

  GBK中两个字节表示一个汉字（2个字节，16位，65536种状态，取值范围为【-32768,32767】），虽然65535种状态几乎能够把汉字表示完但是其他的语言文字就够呛了，因为相当于GBK就只能表示汉字了，而无力表示其他语言文字了，所以GBK这个字符集还不够。但是utf8能够解决GBK不能解决的问题，这是因为utf8是**“变长编码”**，表示的范围比GBK更多，不仅能表示汉字，而且能表示全世界任意一种语言文字。

- 在mysql中的utf8其实是个”假的“utf8，不是一个“完备的”，有时候有的字符是符合标准的utf8字符编码的额，但是还是无法正常表示，后来mysql又提供了一个utf8mb4版本，这个版本才是真正的完备的utf8，但是呢utf8这个足够用了，只是有些特殊字符比如表情等不适用，所以两个版本都可以使用。

所以我上次想给数据库输入中文的时候，会发现出现了乱码，那么这个时候的解决办法就是在创建指定数据库的视乎指定字符集（是可以修改的）。如果不提前指定的话，数据库就会采取默认字符集。**创建数据库的时候就可以进行对数据库的编码进行设置！！！！**

---

![](C:\Users\14214\Pictures\图片笔记\MySQL\MySQL增删改查.png)

 MySQL中的数据库的编码问题的解决方式有两种：一次性的和永久的。

#### 一次性

**语法：**

**create database 数据库名 character set utf8;**

**create database [if not exists]  数据库名 default character set utf8;**

**CREATE DATABASE   数据库名  DEFAULT CHARSET utf8 COLLATE utf8_general_ci;**

备注：[ ]里的内容是可写可不写的

在创建数据库的同时设置当前数据库的字符编码，该方式有一个特点就是当前字符编码的设置只对当前正在建的数据库有效，不影响其它数据库的字符编码。

![image-20230814165249929](C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230814165249929.png)

#### 永久性

**修改MySQL的配置文件**

见图：

![](C:\Users\14214\Pictures\图片笔记\MySQL\MySQL的配置文件的修改.png)



## 8、练习题（商场）

题目：有一个商店的数据，记录客户及购物情况，由一下三个表组成：

1. 商品goods（商品编号goods_id,商品名goods_name,单价unit_price,商品类别category，供应商provider）
2. 顾客customer（客户号customer_id,姓名name，住址address，邮箱email，性别sex，身份证Card_id）
3. 购买purchase（购买订单order_id,客户号customer_id,商品号goods_id,购买数量nums）

SQL答案：

```sql
-- 题目：有一个商店的数据，记录客户及购物情况，由一下三个表组成：
   -- 1. 商品goods（商品编号goods_id,商品名goods_name,单价unit_price,商品类别category，供应商provider）
   -- 2. 顾客customer（客户号customer_id,姓名name，住址address，邮箱email，性别sex，身份证Card_id）
   -- 3. 购买purchase（购买订单order_id,客户号customer_id,商品号goods_id,购买数量nums）

   -- 创建数据库，设置数据库编码
   create database if not exists supermarket
   default character set utf8 ;
   -- 选择数据库
   use supermarket;
   -- 创建数据库表
   -- 商品
   create table if not exists goods
   (
   goods_id int comment '商品编号',
   goods_name varchar(20) comment '商品名称',
   unit_price int comment '单价，单位分',
   category varchar(20) comment '商品类别',
   provider varchar(20) comment '供应商名称'
   );
-- unit_price 这个是表示单价，是跟钱挂钩的数据，那么我们应该使用很精确的数据类型才可以,使用float和double都不够，要使用decimal

   -- 顾客
   create table if not exists customer
   (
   customer_id int comment '客户编号',
   name varchar(20) comment '客户姓名',
   address varchar(100) comment '客户住址',
   email varchar(50) comment '客户邮箱',
   gender varchar(1) comment '客户性别',
   card_id varchar(100) comment '客户id'
   );
   -- 购买
   create table if not exists purchase
   (
   order_id int comment ' 购买订单',
   customer_id int comment '客户号',
   goods_id int comment '商品号',
   nums int comment '购买数量'
   );
   -- 查看当前数据库中所有的的表
  show tables;
```

![](C:\Users\14214\Pictures\图片笔记\MySQL\SQL操作.png)