# 第一个java程序helloworld代码的编写

---

[TOC]



>这篇文章归纳在了Java基础这个栏目里面，希望同学们可以持续不断的学习！！

## 一、项目

- 目的：快速入门Java

- 要求说明：

要求开发一个Hello.java 程序，这个程序可以输出“ Hello World！”

- 开发步骤

  1）将Java代码编写到扩展名为 .java的文件中

  2）通过Javac命令对该Java文件进行编译，生成 .class 文件

  3）通过Java命令对生成的class文件进行运行

---

要想能够完成上述项目，我们虽然已经通过上篇《什么是Java？》以及了解到了基础的Java知识，现在我们要完成一个代码的编译和运行，需要提前准备以下几个条件：

首先 **工欲善其事，必先利其器。** 我们必须了解并搭建好项目所需要的开发环境。要编译和运行Java程序，JDK（Java Development Kits）是必备的。下面讲具体介绍下载并安装JDK。

## 二、认识JVM、JRE和JDK

我们已经知道Java程序设计语言有一个特点，就是 **平台无关性**（也可以称为 跨平台性），拥有这个性质就意味着Java语言是可以在不同平台中无缝运行，不受操作系统的限制。那么这是为什么呢？

- 这是因为JVM（Java虚拟机）的存在！

---

### 2.1、JVM是什么？

JVM（Java Virtual Machine Java虚拟机），JVM是Java编程语言的核心组件之一，它负责在不同硬件平台上执行Java字节码（bytecode）。

### 2.2、JVM的主要功能和作用

1. Java字节码执行：Java代码经过编译之后会生成字节码，这些字节码并不是特定于任何平台的机器码，而是一种介于代码和机器码之间的一种中间代码。JVM负责解释和执行这些字节码，使得Java程序可以在不同的操作系统上运行。
2. 平台无关性：JVM的存在使得Java具有“一次编写，到处运行”（ Write Once，Run Anywhere，即WORA）的特性。开发者可以在一台平台上编写Java程序，然后将生成的字节码拷贝到其平台的JVM中运行，而无序重新编译源代码。
3. 安全性：JVM提供了安全管理器（Security Manager），用于限制Java程序的访问权限，防止恶意代码对系统进行非法操作。
4. 辅助工具：JVM提供了丰富的工具和命令行选项，用于监控和调试Java程序的执行过程，例如jconsole、jvisualvm、jstack等。
5. JIT编译器：JVM具有即时编译器（Just-In-Time Compiler，JIT），它将字节码转换成本地机器代码，并在运行时进行优化，以提高程序的执行性能。

以上JVM的功能和作用就很好的交代了我们为什么会需要JVM，因为JVM好比是一个“领域展开”，专门用来解释和执行字节码的一个工具。又因为JVM包含在JDK中，所以，我们需要到官网下载对应版本的JDK，不同版本的JDK也就代表了不同版本的JVM。

---

### 2.3、JRE和JDK

#### JDK基本介绍

1. JDK的全称（Java Development KitsJava开发工具包）
2. JDK = JRE + Java开发工具（Java、javac、javadoc、javap等等）
3. JDK是提供给开发者使用的，其中包含了Java开发工具，也包括了JRE

---

#### JRE基本介绍

1. JRE的全称（Java Runtime Environment 运行时环境）
2. JRE = JVM+Java的核心类库【类】
3. 包括Java虚拟机（Java Virtual Machine）和Java程序所需要的核心类库等，如果想要运行一个开发好的Java程序，计算机当中只需要安装JRE即可。

---

                                                                        **图形化DK、JRE和JVM关系**
![在这里插入图片描述](https://img-blog.csdnimg.cn/71f71c5b05d94d87939fad55e13cbace.png)



## 三、Java开发工具

Java开发工具是一些用于编写、调试和运行Java程序的软件工具。这些工具提供了丰富的功能和功能，帮助开发者更高效地开发Java应用程序。以下是一些常用的Java开发工具：

### 3.1、种类

editplus  官网链接：<https://www.editplus.com/>

notepad++ 官网链接：<https://notepad-plus-plus.org/>

Sublime Text 官网链接：<https://www.sublimetext.com/>

Visual Studio Code  官网链接：<https://code.visualstudio.com/>

IntelliJ IDEA  官网链接：<https://www.jetbrains.com/zh-cn/idea/>

eclipse 官网链接：<https://www.eclipse.org/downloads/>



### 3.2、工具的选择

建议最初开始学习Java基础的同学使用集成度不太高的工具，我们可以先选择使用文本编辑器，等到您对Java有一定的了解之后，我们再使用IDEA和Eclipse开发工具。

---
如果推荐使用编辑器而不是集成开发环境（IDE），以下是一些适合初学者的轻量级代码编辑器，它们可以用来编写Java代码：

1. Visual Studio Code：Visual Studio Code（VS Code）是一个免费的轻量级代码编辑器，支持多种编程语言，包括Java。它具有丰富的插件生态系统，可以通过插件增强Java开发功能，如语法高亮、代码提示和调试等。
2. Sublime Text：Sublime Text是另一个流行的轻量级代码编辑器，它简洁、快速，并且支持多种编程语言。虽然它不是专门为Java开发设计的，但可以通过安装插件来实现Java代码的编写。
3. Notepad++：Notepad++是一个免费的Windows平台代码编辑器，支持多种编程语言，并且可以通过插件增强功能。虽然它功能相对简单，但对于初学者来说是一个不错的选择。

这些编辑器都是轻量级的，运行速度快，适合初学者学习Java编程和进行小型项目开发。如果你希望更简洁、更自由的编辑器，这些都是不错的选择。

（接下来的文章我们使用的是notepad++编辑器，来写Java代码）

### 3.4、好处

初学者选择轻量级的编辑器有以下几个好处：

1. 深刻的理解Java技术，培养代码感
2. 有利于公司面试
3. 页面简洁、运行快速，同时支持多种编程语言

## 四、搭建Java环境

> 工欲善其事，必先利其器。

在学习Java语言之前，必须了解并搭建好它所需要的开发环境。要编译和执行Java程序，JDK（Java Development Kits）是必备的。因为JDK中包含了JRE和Java开发工具。下面将具体介绍下载并安装JDK



### 1、下载JDK：

前往Oracle官网下载适合你操作系统的JDK安装包。确保下载的版本是适合你的操作系统和位数（32位或64位）的。我这里使用的是win10,x64的17.0.8版本的JDK。官网地址：<https://www.oracle.com/cn/java/technologies/downloads/>
![在这里插入图片描述](https://img-blog.csdnimg.cn/22157107c865492ebe47073740f939e8.png)

### 2、运行安装程序：

双击下载的JDK安装包，运行安装程序。可以直接点下一步。

### 3、设置安装路径：

在安装过程中，你可能会被要求选择JDK的安装路径。一般情况下，你可以接受默认的安装路径。如果你希望自定义安装路径，请选择一个合适的目录。（**注意事项：安装路径名称不可以包含中文或者特殊符号如空格等，提示你安装JRE与否的时候，可以选择安装。**）

### 4、完成安装：

安装程序将会继续安装JDK到你选择的路径中。等待安装完成。

### 5、配置环境变量（可选）：

对于Windows用户，安装JDK后，你可能需要手动配置系统环境变量。在系统环境变量中添加JDK的bin目录路径，这样你就可以在命令行中运行Java和Javac命令了。对于Linux和Mac用户，环境变量的配置过程可能略有不同，请查阅相应的文档。

### 6、验证安装：

打开命令行（Windows用户打开命令提示符，Linux和Mac用户打开终端），（我这里由于是windows操作系统，所以我使用快捷键win+r ，然后输入cmd就可以打开命令提示符），步骤如下图

- 快捷键win+R，输入cmd

![在这里插入图片描述](https://img-blog.csdnimg.cn/5a34708ee8c545d2917d5096b8af3dc7.png)


- 出现命令行提示符（黑框框）

![在这里插入图片描述](https://img-blog.csdnimg.cn/0a331e6f4309455f9a20f237c2391096.png)


- 输入Java工具包中的命令,这些命令是存在于你刚刚安装好的JDK的bin目录当中的，你可以在bin目录下找到Javac.exe和java.exe,这两个命令分别是编译和运行的命令，如果你能成功使用这两个命令则表明你正确了安装JDK。

![<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230801125346074.png" alt="image-20230801125346074" style="zoom: 33%;" />](https://img-blog.csdnimg.cn/79575abc380c46d1bbb825b3d3b0b3cb.png)




### 7、输入以下命令来验证JDK是否正确安装：

```
javac
java
```
如果正确安装，你将会看到Java和Javac的版本信息。很显然，你这里会发现报错了，会出现以下的错误：

![在这里插入图片描述](https://img-blog.csdnimg.cn/091264e9d5c3482b8f3201375ace7e6c.png)


### 8、分析原因：

当前执行的程序在当前目录下如果不存在的话，那么会在win10系统中已有一个名为path的环境变量指定的目录中查找，如果仍旧没有找到的话，会出现以上错误的提示“Java或者javac不是内部或外部命令，也不是可运行的程序或批处理文件”。这样的错误提示信息。所以，现在，如果我们进入到我们安装好的jdk软件的目录之下，去找到Java.exe和Javac.exe 这两个命令存在的bin目录下，我们直接在这里进入DOS命令窗口，我们再使用Java.exe和javac.exe这两个命令，会发生什么呢？

![在这里插入图片描述](https://img-blog.csdnimg.cn/146c8de703ff40cd98b31cfc91d0b013.png)


#### 8.1、检验示意图
![在这里插入图片描述](https://img-blog.csdnimg.cn/d2bca150804a4f51b87e90030f4e0ce6.png)

---

### 9、配置环境变量path

刚刚我们提出了一个疑问：我们现在是通过哪种方式完成Java工具包中命令的执行的？很显然我们是通过当前目录来完成的，现在，有没有一劳永逸的方法，在任何目录下我们都可以执行Java和javac这些命令呢？我们就只需要配置环境变量，手动给系统指一条路去找bin目录下的Java命令。

#### 9.1 、步骤

①我的电脑——>右键——>属性——>高级系统设置——> 环境变量——>找到系统变量中的path，点击进去——>新建——>把bin绝对路径添加进去——>一直点击确定

#### 9.2、示意图

![在这里插入图片描述](https://img-blog.csdnimg.cn/95ccbe95c9e84ec1b1b4f27283453f4b.png)

---

## 10、完成项目

#### 10.1、快速入门Java

现在我们就可以完成文章开头的Java程序的开发，现在我们就快速入门，写一个Java程序，这个Java程序可以输出Hello World！

---

- 打开notepad++编辑器，由于notepad++支持多种编程语言，而我们需要的是Java语言，那么我们就可以选择设置一下语言，这样的话，就可以有一些专属于Java语言的高亮颜色提示。这是利于我们编写代码的。
- 步骤：打开notepad++编辑器，点击语言（L），然后找到J这个字母，选择Java即可。
-![在这里插入图片描述](https://img-blog.csdnimg.cn/b9a5f3a7ea834dc5850fa8a68d915456.png)

---

- 语言设置对照
![请添加图片描述](https://img-blog.csdnimg.cn/1a37acb852d3464bb92c34713500cc35.png)



---

- 开始编译Java源文件

这里有个快捷方式可以直接运行当前的代码，就是你点击notepad++页面左上角的“文件”，然后选择“打开所在文件夹”，然后点击命令行，这样就可以直接出现dos命令窗口，这个窗口就是当前Java源文件的目录，所以你可以直接使用Javac命令去编译Java源文件，编译成功之后就可以直接使用Java命令进行对字节码文件的解释和运行。

---

若以下结果出现，那么就代表我们完成了项目的所有的要求！！！！
![在这里插入图片描述](https://img-blog.csdnimg.cn/d24dfb9a3e5e4710a71f3020a431384b.png)



---

总结：

1. 认识了JDK、JRE以及JVM
2. 选择了Java开发工具notepad++
3. 为Java搭建环境
4. 完成项目