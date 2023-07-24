**作为程序员要求掌握最基本的windows相关的DOS命令（详细版）**

# 一、DOS命令、cmd、windows操作系统中保留的DOS命令分别是什么？



> **1.DOS命令是什么？**
>
> - DOS命令，计算机术语，是指DOS操作系统的命令，是一种面向磁盘的操作命令，主要包括目录操作类命令、磁盘操作类命令、文件操作类命令和其它命令。
> - 大家常用的操作系统有[windows 10](https://baike.baidu.com/item/windows 10/6877791?fromModule=lemma_inlink),[windows 7](https://baike.baidu.com/item/windows 7/1083761?fromModule=lemma_inlink)等，都是图形化的界面。在有这些系统之前的人们使用的操作系统是DOS系统。
>
> **2.windows命令提示符是什么？**
>
> - Windows命令提示符（Command Prompt）是Windows操作系统中的一个命令行工具，用于执行各种系统命令和操作。通过命令提示符，用户可以直接输入命令来与计算机进行交互，执行文件操作、管理系统设置、运行程序等。
>
> - *如何打开windows命令提示符（cmd.exe）*?
>
>   详情请查看这篇博客：[DOS窗口怎么打开（详细）]()
>
> **3.什么是windows操作系统中支持的DOS命令？**
>
> - 虽然现代Windows操作系统已经远离了纯粹的DOS操作系统，但为了向后兼容性和支持特定的任务，Windows仍然保留了许多经典的DOS命令和功能。同时，Windows也提供了更先进的图形用户界面（GUI）和更强大的命令行工具（如PowerShell），让用户可以根据需要选择不同的操作方式。



---

*该文章旨在教会刚学习java的同学如何使用windows系统的命令行，并掌握最基本的windows相关的DOS命令。接下里就将介绍我们之后的编程过程中会遇到哪些要用到的DOS命令。*

# 二、常见的DOS命令有哪些？

- exit：退出DOS窗口

- cls：清屏，清空当前dos窗口所有的内容（clear screen）
- dir：列出当前目录下所有的子文件/子目录（directory）
- 磁盘+回车 ：切换盘符，例如C:+enter切换到c盘下 、F：+enter切换到F盘下

- del \*.扩展名：删除文件或者目录，例如 del*.class 表示删除当前目录下的所有.class扩展名的文件，这是模糊匹配

- del ： 文件或者目录：指定删除一个或多个文件或目录的列表。 如果指定了目录，则将删除该目录中的所有文件。

- cd：显示当前目录的名称或更改当前目录。 如果仅与驱动器号一起使用（例如，`cd C:`），cd 将显示指定驱动器中当前目录的名称。

-  如果使用时不带参数，cd 将显示当前驱动器和目录。（change directory）

- 如果使用时带有参数，则有以下几种参数可以选择

  —cd..			回到上级目录

  —cd \			直接回到当前根目录

  —cd  [path]  	cd+目录的路径（包括绝对路径和相对路径）

  <img src="C:\Users\14214\Documents\IO图\cd命令介绍.drawio.png" style="zoom:80%;"  >

- ipconfig :ip地址配置信息

- inconfig  /all ：在ipconfig命令后面添加一个/all参数可以查看跟家详细的信息，其中包括网卡的物理地址，例如DC-21-48-75-C8-8F，这个物理地址具有全球唯一性，物理地址通常被称为：MAC地址

- ping ：查看两台计算机是否可以通信，格式就是“ping+ip地址“ 或者“ping+域名”

  例如: ping www.baidu.com或者ping  61.135.169.121

  **补充：如果使用“ping  ip地址  -t”这个命令就会一直ping，除非主动暂停，否则就会一直ping，那么我们如何完成停止呢？这涉及到在DOS命令窗口如果有一个命令一直在执行，我们想要强行终止，该怎么办？**

  ***ctrl+c组合键***



<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230724222243339.png" alt="image-20230724222243339" style="zoom:50%;" />

[![百度搜索](https://bkimg.cdn.bcebos.com/pic/a044ad345982b2b708da85313fadcbef77099bfa?x-bce-process=image/watermark,image_d2F0ZXIvYmFpa2U5Mg==,g_7,xp_5,yp_5/format,f_auto)]([DOS命令_百度百科 (baidu.com)](https://baike.baidu.com/item/DOS命令#:~:text=DOS命令，计算机术语，是指DOS操作系统的命令，是一种面向磁盘的操作命令，主要包括目录操作类命令、磁盘操作类命令、文件操作类命令和其它命令。. 大家常用的操作系统有windows10%2Cwindows 7等，都是图形化的界面。.,在有这些系统之前的人们使用的操作系统是DOS系统。. 中文名. DOS命令. 外文名.))

总结：