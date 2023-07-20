### javaWeb的学习

#### 1.什么是javaweb？

web：全球广域网，也称为万维网（www：World Wide Web），能够通过浏览器访问的网站

#### 2.学习web开发的目的？

使用java这门语言来开发这样的网站（web），这也是目前最主流的企业级应用方式

例如：使用java开发的网站就有很多：淘宝、京东、唯品会（电商系统）；CRM、OA、ERP（企业内部管理系统）等......

#### 3.那么具体学什么？

##### ①web网站的工作流程

web的工作流程有两种模式：前后端分离开发：前后端混合开发 = 7:3 （通过市场调研）

###### 前后端分离开发：

前端程序和后端程序的开发和部署是分离的开发模式被称为分离开发

<img src="C:\Users\14214\Documents\IO图\前后端分离开发.drawio.png" alt="前后端分离开发" style="zoom:80%;" />

------

前后端混合开发：

前端程序和后端程序开发和部署都是混合在一起的这种模式被称为混合开发

<img src="C:\Users\14214\Documents\IO图\前后端混合开发.drawio.png" style="zoom:80%;" />



##### ②web开发课程安排

前端web开发（能看懂，会修改即可），*前端不仅仅包含PC端，还根据项目的性质，定位的不同，可能包含Android端、iOS端、移动端、小程序端等等*

- HTML、CSS、javaScript
- Vue、Element、Nginx

后端web程序开发 （是学习的重点）

- Maven

- Spring

- MySQL

- SpringBoot Mybatis

- SpringBoot web基础篇

- SpringWeb进阶篇

  ------

  

#### 4.初始web前端

1. 网页由哪些部分组成？

   文字、图片、音频、视频、超链接......

2. 我们看到的网页，其背后的本质是什么？

   程序员写的前端代码

3. 前端代码是如何转换成用户眼中的网页的？

   通过浏览器转换（解析和渲染）成用户看到的网页，浏览器通过对代码进行解析渲染的部分称为浏览器的内核

#### 5.web标准

*不同的浏览器其内核不同，对于相同的前端代码解析的效果会存在差异（对于前段开发人员写的相同的代码在不同的浏览器解析出来的效果就会存在差异，但这并不是我们希望看到的，我们不希望看到不同的用户在不同的浏览器访问我们的网站看到的效果是不同的，我们希望的是内核不同的浏览器解析相同的前端代码的效果是相同的），为了达到这个目的我们就需要共同遵守一套规则，而这套规则已经被制定好了，那就是“web标准”*

- web标准也被称为网页标准，由一系列的标准组成，大部分由W3C（World Wide Web Consortium ）万维网联盟负责指定的。
- 三个组成部分：

1. HTML：负责网页的结构（页面元素和内容）
2. CSS：负责网页的表现（页面元素的外观、位置等页面样式，例如颜色、大小等）
3. JavaScript：负责网页的行为（负责交互效果）

#### 6.web前端开发的学习安排

- HTML、CSS
- javaScript、Vue
- Ajax、Axios、Element、Nginx

#### 7.什么是HTML、CSS？

HTML（HyperText Markup Language）:超文本标记语言

①超文本：超越了文本的限制，比普通文本更强大，除了文字信息，还可以定义图片、音频、视频等内容

②标记语言：由标签构成的语言

*HTML中的标签都是预定义好的，例如：使用\<a>展示超链接，使用\<img>展示图片，\<video>展示视频，而且HTML代码直接在浏览器中运行，HTML标签由浏览器解析*

CSS（Cascading Style Sheet）：层叠样式表，用于控制页面样式或者表现

#### 8.学习HTML、CSS中的什么？

- 学习HTML主要学习预定义好的标签，这些标签可以通过浏览器进行解析
- 学习CSS主要学习CSS中预定义好的常见的样式
- （那么HTML中有哪些预定义好的标签呢？CSS中有哪些预定义好的常见的样式呢？我们可以打开W3 School官方文档进行查看）
- HTML5是是现在的主流版本，点击“参考书”就可以查看HTML的所有标签
- CSS教程，点击“参考书”，其中就罗列了所有的CSS的样式（表现）

### Test01

#### HTML的快速入门：制作一个网页程序

- [x] 新建文本文件，后缀名改为html（然后以记事本的形式打开）

  ###### <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230702111520702.png" alt="image-20230702111520702" style="zoom:80%;" />

- [x] 编写一HTML结构标签

  ###### <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230702111743686.png" alt="image-20230702111743686" style="zoom:80%;" />

- [x] 在<body>中填写内容

###### <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230702111655938.png" alt="image-20230702111655938" style="zoom: 67%;" />   

- [x] 使用浏览器的打开方式打开这个扩展名为html的文件

######   <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230702111956833.png" alt="image-20230702111956833" style="zoom: 50%;" />

#### HTML标签的特点：

HTML标签不严格区分大小写

HTML标签的属性单引号、双引号都可以

HTML语法较为松散

![Escola Online de Java Completo - Posts | Facebook](https://th.bing.com/th/id/OIP.cq4FdlE_XscezeSEvCBFdQAAAA?pid=ImgDet&rs=1)

