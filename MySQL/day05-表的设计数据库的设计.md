# 表的设计/数据库的设计

> 引入：
>
> 如果面试官问你：谈谈你的xx项目里面，数据库是如何设计的？
>
> 这个问题问的是什么？
>
> 问的是你的数据库里有几个表，每个表都是干啥的；每个表里都有哪些列，这些列又是干嘛的。其实面试官问你这个问题，是想问这个项目是不是自己实现的，调项目里的细节问你，就能看出这个项目是你自己做的，还是照抄的。（简历一定要实事求是，只写会的，不会的不熟悉的就不写）。对于不实事求是的行为一般都认为是非常严重的问题（零容忍），公司里的逻辑和学校都很不一样！！

## 设计思路

数据库的设计，主要思路

1、根据需求，找到“实体”

2、梳理清楚，实体之间的关系

找到实体，就类似于面向对象程序设计，“找对象”- 需求中的关键性的名词，实体找完之后，就找出这些实体中的关系（一对一，一对多，多对多，没关系）。一般来说，我们每个实体都会安排一个表，表的设计样受到表与表之间的关系的影响。关键性的名词都可以作为实体。

## 实体间关系

- 一对一关系：

例如：学生信息，账号信息（学生和账号就是一对一的关系）

一个学生对应一个账号 （学生信息：学号、姓名、班级、性别...）

一个账号对应一个学生 （账号信息：注册时间、账号、密码...）

上述的一对一的关系就有多种方式

1. 所有的信息都放在一个表中 

   student-account（学号、姓名、性别、密码、用户名...）。缺点就是学生和账户的耦合度过高，不利于观察

2. 在学生表里，把账号id作为一个记录

   student（studentId，name，gender，accountId）

   account（accountId，password，username）

3. 或者，可以在账号表张加一个学生Id，也就是把学生Id作为账号里的一个记录

   student（name，gender，studentId）

   account（studentId，password，accountId）

- 一对多关系：

  班级-学生

  一个班级，可以包含多个学生

  一个学生，只能属于一个班级

  1) ×

  student（studentId，name，gender...）

  class（classId，classname，studentList）

  这种不太好，因为在MySQL中没有“数组”这种类型，这种很难去表示 。

  2) √

  student（name，gender，classId）

  class（classId，classname ）

  这种方式是更加常见的方式

- 多对多关系：

  学生-课程

  一个学生，可以选择多个课程

  一个课程，可以被多个学生选择

  **多对多的表结构，通常需要使用一个“关联表”，把两个实体表给关联起来。**

  student(sudentId,name,gender)

  course(courseId,name)

  关联表

  student_course(studentId,coruseId)

  ---

  除此之外就没有其他的关系了。如果两个实体之间不属于上述任何一种关系，那么两者之间就没有关系了。没有关系的表就正常设计，不用做特殊处理了。

  如果是复杂的场景，复杂的需求，实体就可能非常的多，关系也更加的错综复杂。

  **判定两个实体的关系**

  准备工作就是提前找好实体，然后如果要找两个实体之间的关系，那么就直接造句，看看是几对几的关系。

  为了解决这种复杂的问题，程序员就发明了ER（实体关系图），ER图通常在学校的课程上都会重点讲的，而且一定是期末考试的一道大题。

  ![](C:\Users\14214\Pictures\图片笔记\MySQL\实体对应关系png.png)

  ---

## 查询-新增

这是更加复杂的新增，其实说这个事新增，但是本质还是 查询，只不过是把我们查询的结果 插入到另一个表中。（相当于是把两个sql语句组合了一下）

![](C:\Users\14214\Pictures\图片笔记\MySQL\查询（新增）— 联合使用.png)



## 聚合查询

查询的时候带表达式，也就是表达式查询，我们会把列和列放到一起进行计算，然后利用表达式查询。现在我们的“聚合查询”则是把行和行放到一起进行计算。

聚合函数

SQL中提供了一些函数，也就是 “聚合函数”，通过这些函数，就可以进行 ”行和行“的计算

| 函数                 | 说明                                      |
| -------------------- | ----------------------------------------- |
| COUNT(DISTINCT expr) | 返回查询到的数据的 数量                   |
| SUM(DISTINCT  expr)  | 返回查询到的数据的 总和，不是数字没有意义 |
| AVG(DISTINCT  expr)  | 返回查询到数据的 平均值，不是数字没有意义 |
| MAX(DISTINCT  expr)  | 返回查询到数据的 最大值，不是数组没有意义 |
| MIN(DISTINCT  expr)  | 返回查询到数据的 最小值，不是数字没意义   |



![](C:\Users\14214\Pictures\图片笔记\MySQL\聚合查询.png)

---

## 分组查询

分组查询/聚合

语法 group by 列名

根据查询的结果，进行分组，把值相同的记录，分成一组，然后就可以针对每一组，分别进行聚合

补充：系统内置的数据库是非常重要的，不要删掉，也不要随意改动，一旦删掉就不能使用了，不然就只能重装mysql了。

---

![](C:\Users\14214\Pictures\图片笔记\MySQL\分组查询.png)

---

## 多表查询

多表查询也叫联合联合查询（同时多个表查询：把多个表变成一个表也就是求笛卡尔积）

### **定义：**

交叉连接(笛卡尔积)返回被连接的两个表所有数据行的笛卡尔积，返回结果集合中的数据行数等于第一个表中符合查询条件的数据行数乘以第二个表中符合查询条件的数据行数。

简单解释一下**笛卡尔积**

设A,B为集合，用A中元素为第一元素，B中元素为第二元素构成有序对，所有这样的有序对组成的集合叫做A与B的笛卡尔积，记作AxB.

笛卡尔积的符号化为：

AxB={<x,y>|x∈A∧y∈B}

例如，A={a,b},B={0,1,2},则

AxB={<a,o>,<a,1>,<a,2>,<b,0>,<b,1>,<b,2>,}

BxA={<0,a>,<0,b>,<1,a>,<1,b>,<2,a>,<2,b>}



### **笛卡尔积**

- 由于 笛卡尔积 行数是一个 相乘 的结果，那么如果原来的行数很多的时候，一旦相乘，那么获得的笛卡尔积 就会是行数很庞大的表。
- 所以我们在进行“**联合查询**”的时候，就是在计算笛卡尔积的过程，当表比较大的时候，如果进行多表查询，就会非常的低效，甚至成为“危险操作”。实际工作中，有可能会用，有可能不会用，实际情况还是要看进行联合查询的表的量度是多少。
- 笛卡尔积是一种比较低效的操作，表的记录比较少的时候，体会不明显，一旦表的记录非常的多，那么就能感觉出来这种“多表查询”效率越来越低了。工作中大概率不会用上 聚合查询（多表查询），但是面试会考，**因为多表查询比较难**

笛卡尔积 就是两个表记录，排列组合的结果

笛卡尔积的列数，是两个表的列数之和

笛卡尔积的行数，是两个表的行数之积



---

![](C:\Users\14214\Pictures\图片笔记\MySQL\联合查询或多表查询.png)

### **内外链接**

- 语法：

from 表1，表2......(内连接)

from 表1 join 表2 on 条件......（外连接 使用join，可以作为内连接也可以作为外连接。直接写join 或者 inner join 是内连接；写作left join 左外连接，写作right join 表示右外连接）外连接其实就是左外连接和右外连接。

- 如果两张表上的数据都是一一对应的时候，其实外连接和内连接看不出来任何的区别，但是如果表上的数据不再一一对应，区别就非常明显了。

- 如果两张表不是一一对应的时候，那么当我们使用左外连接的时候，左边的表为主,如果左边表格中的数据在右边没有对应的话,那么此时左边的数据就会显现出来,但是右边的数据由于通过连接条件没有对应,那么就会显示为空，而且会尽量把右侧的表显示完整。
- 当然使用右外链接也是类似的这种情况。

![](C:\Users\14214\Pictures\图片笔记\MySQL\多表查询—内外连接.png)

### **自连接**

自连接是行和行之间做笛卡尔积

我们之前的所有的条件查询都是进行列与列之间的比较，而没有涉及到行与行的比较，怎么办？那就是 把 行 转换成 列 ，然后再进行比较。这就是 **自连接** 能够做到的。

![](C:\Users\14214\Pictures\图片笔记\MySQL\自连接.png)

---

## 子查询（查询+查询）

子查询可以理解为套娃。

本质上就是把多个查询语句，给组合成一个查询语句。用一个查询结果的临时表，基于这临时表再发起新的一组查询。



