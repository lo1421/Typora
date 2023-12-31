🚀Java是什么？

Java是一个跨平台的、面向对象的程序设计语言。该文章主要是让读者对Java语言有一个整体的了解，然后再慢慢学习具体的内容，最后达到完全掌握Java语言的目的。

**通过阅读本章，您可以了解到：**

@[toc]
---

## 一、简述Java语言

Java语言是一门高级的**面向对象**的程序设计语言。使用Java语言编写的程序是**跨平台**的，从pc端到手机端，到处都运行着Java开发的程序和游戏。

>- java是1995年由SUN公司推出的一门极富有创造力的面向对象的程序设计语言，它是由有“Java之父”之称的sun研究院院士詹姆斯·戈士林亲手设计而成的，正是他完成了Java技术的院士编译器和虚拟机。Java最初的名字是oak，在1995年被重命名为Java，并正式发布。
>- Java是一种通用的解释方式来执行的语言，其语法规则和c++类似。同时Java也是一种跨平台的程序设计语言。用Java语言编写的程序，可以运行在任何平台和设备上，如跨越IBM个人电脑、MAC苹果计算机、各种微处理器硬件平台，以及windows、Linux、IOS等系统平台，真正实现“**一次编写，到处运行**”。
>- Java语言编写的程序既是**编译型**的，又是**解释型**的。程序代码经过编译之后转换为一种称为Java字节码的中间语言，Java虚拟机（JVM）将对字节码进行解释和运行。编译只进行一次，而解释在每次运行程序时都会进行。编译后的字节码采用一种针对JVM优化过的机器码形式保存，虚拟机将字节码解释为机器码，然后再计算机上运行。


![在这里插入图片描述](https://img-blog.csdnimg.cn/4092905e92de4799b1bc70fcef5ae4fc.png)

                                   java语言程序代码的编译和运行过程如图1.1



## 二、Java的版本

按照Java应用的范围的版本分为三个版本：javaSE、JavaEE和JavaME。

**1、javaSE**

javaSE是Java的标准版，主要用于桌面应用程序的开发，同时也是Java的基础，它包含Java语言基础、JDBC（Java数据库连接性）操作、I/O（输入输出）、网络通信、多线程等技术。（javaSE结构如图1.2所示）

![第一章 初识java - 1.5 Java SE的结构 - 《Java程序设计基础》 - 书栈网 · BookStack](https://img-blog.csdnimg.cn/img_convert/cfad832e4f181d0a656bb0405d8730a2.png)

                                          图1.2 javaSE的结构

**2、javaEE**

JavaEE是Java的企业版，主要用于开发企业级分布式的网络程序，如电子商务网站和ERP（企业资源规划）系统，其核心为EJB（企业Java组件模型）。（javaEE结构如图1.3所示）

![在这里插入图片描述](https://img-blog.csdnimg.cn/addc61f0ce7142cdbf918e55b2d5bc4b.jpeg)



                                           图1.3 javaEE的结构


**3、JavaME**

JavaME主要用于嵌入式系统开发，如掌上电脑、手机等移动通信电子设备，现在大部分手机厂商所生产的手机都支持Java技术。（javaME结构如图1.3所示）

<img src="https://ts1.cn.mm.bing.net/th/id/R-C.aafbc6c3757287f154583bd91106338c?rik=8svHd91y57m3VA&amp;riu=http%3a%2f%2fstatic.oschina.net%2fuploads%2fspace%2f2014%2f0109%2f233755_j3WD_852488.jpg&amp;ehk=RemDRntoRv6tfDAieHDtKtUms9GA0X3UVInk5W8b83U%3d&amp;risl=&amp;pid=ImgRaw&amp;r=0" alt="JAVA学习笔记——第一章 初始JAVA_James Zhang's Blog-CSDN博客" style="zoom:150%;" />

                                             图1.4 javaME的结构

## 三、Java API文档

- Java API文档是Java编程语言的官方应用程序接口（Application Programming Interface）文档。它包含了Java标准库中的所有类、接口、方法和常量的详细说明，以及它们的用法、参数和返回值等信息。
- Java API文档由Oracle公司提供，我们在进行Java开发的时候，Java API文档是必不可少的参考资料。

## 四、Java语言的特性

3.1 **简单易学**

- Java采用了C和C++语言的语法，使其易于学习和使用。同时，Java也避免了一些复杂的特性，使得程序编写更加简洁明了。

3.2 **面向对象**

- Java是一种面向对象的编程语言，支持封装、继承和多态等面向对象的特性，使得程序设计更加灵活和模块化。

3.3 **平台无关性**

- Java程序可以在不同的平台上运行，不受操作系统的限制。这得益于Java虚拟机（JVM），它负责将Java程序转换为特定平台的机器码。

3.4 **自动内存管理**

- Java提供垃圾回收机制，自动管理内存分配和释放，使得开发者无需手动管理内存，降低了内存泄漏和空悬指针等错误的风险。

3.5**安全性**

- Java的安全性得到了很高的重视，其安全模型可以防止许多安全漏洞，如缓冲区溢出和指针操作等。

3.6 **多线程支持**

- Java天生支持多线程编程，通过线程机制可以实现并发处理，提高程序的效率。

3.7 **开放性和可移植性**

- Java采用开放标准，有众多开源库和框架，使得开发者可以轻松地进行开发，并且Java程序可以在不同平台上无缝运行。

3.8 **异常处理**

- Java提供了强大的异常处理机制，可以更好地处理错误情况，增加了程序的稳定性和可靠性。

3.9 **高性能**

- 尽管Java是解释执行的语言，但通过即时编译技术（JIT）和优化，Java程序的性能已经接近于编译型语言。

3.10 **大型生态系统**

- Java拥有庞大的生态系统，有大量的第三方库、框架和工具，可以帮助开发者快速构建复杂的应用程序。

---

备注：该文章如有任何不妥之处或者疑问以及见解，欢迎读者在评论区积极提出建议！

下篇文章：《第一个java程序helloworld代码的编写》

