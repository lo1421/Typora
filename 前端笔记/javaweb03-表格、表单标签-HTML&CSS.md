---

---

# 表格、表单标签

[TOC]



## 表格标签

- **场景**：在网页中以表格（行、列）形式整齐展示数据，如：班级表。

- **标签**：

| 标签     | 描述                             | 属性/备注                                                    |
| -------- | -------------------------------- | ------------------------------------------------------------ |
| \<table> | 定义表格整体、可以包裹多个\<tr>  | border:规定表格边框的宽度                                                                           width：规定表格的宽度                                                                                 cellspacing：规定单元之间的空间 |
| \<tr>    | 表格的行，可以包裹多个\<td>      |                                                              |
| \<td>    | 表格单元格（普通），可以包裹内容 | 如果是表头单元格，可以替换为\<th>                            |

HTML中一个tr标签表示一行，而一行当中可以有多个单元格，而这个单元格就用td标签来表示，如果想要的是表头单元格使用th标签来代替（th可以达到表头字体加粗以及居中展示的效果）。table标签是用来设置表格的，该标签中有border属性使用来设置边框的宽度的，默认值是没有边框。th：t是table表格，h是header头；td是table表格，d是data数据。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML-表格</title>
        <style>
            td{
                text-align :center; /* 单元格内容居中展示 */
            }
        </style>
</head>
    <body>
    <table border="1px" cellspacing="0" width = "600px">
    <tr>
            <th>序号</th>
            <th>品牌logo</th>
            <th>品牌名称</th>
            <th>企业名称</th>
    </tr>
    <tr>
        <td>1</td>
        <td><img src="img/huawei.jpg"  width="100px"></td>
        <td>华为</td>
        <td>华为技术有限公司</td>
    </tr>
    <tr>
        <td>2</td>
        <td><img src="img/alibaba.jpg" width="100px"></td>
        <td>阿里</td>
        <td>阿里巴巴集团控股有限公司</td>
    </tr>
    </table>  
    </body>
</html>
```



## **表单标签**

### 表单标签引入

- 场景：在网页中主要负责信息的采集功能，如注册、登录等数据采集。
- 标签：\<form>
- 表单项：不同类型的input元素、下拉列表、文本域等。
  - \<input>：定义表单项，通过type属性控制输入形式
  - \<select>：定义下拉列表                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       
  - \<textarea>：定义文本域

- 属性：
  - action：规定当提交表单时向何处发送表单数据。URL（地址）
  - method：规定用于发送表单数据的方式。GET、POST



**表单是用来做什么的？**

是用来采集用户输入的数据的，把这些采集的数据可以统一发送到服务端，服务端就可以将这些数据保存起来，而这些被提交到服务端的数据一般来说都会被存到数据库当中，所以表单是HTML当中非常重要的一类标签，主要是完成数据的采集。

**如何定义一个表单？**

1. 先准备一个HTML的空的结构：！+回车（自动生成HTML的结构标签html、head、body等等）。

2. 定义form标签的时候VS Code会提醒使用哪种提交方式method，这里我们先演示采用GET提交的方式。form表单定义好之后，自带了两个属性：action=“  ”和method=“get”。光有表单是没有数据的。

3. 表单项的定义，我们可以在表单里先定义两个表单项。第一个表单项“用户名：”，使用一个input标签，然后指定type属性为“text”（表示当前的表单项是一个文本输入框）。同时，表单项要想成功的采集数据并提交必不可少的一个属性就是name属性（表示表单项的名字）。同理，再定义一个表单项“年龄”，把name属性改为”age“（表示当前的这个表单项是年龄）。

4. 要想这个表单当中的两个表单项能够被提交必须还要定义一个提交按钮“input type = “submit” value = “提交” “。这个input标签中的type属性的值为submit表示是一个**提交按钮**，而这里的value属性则表示按钮的名字就叫**提交**。

5. 打开浏览器就可以看见我们写的表单，但是这个提交按钮提交之后，输入的数据往哪里提交呢？而form标签中的action就是用来制定表单提交表单项的一个url。如果我们不指定url，那么提交的话就是默认提交到当前页面。当我们讲解了web后端开发的时候，这里的action就可以赋一个**“服务端的url地址”**，目前我们就先不指定暂时提交到当前页面。

6. 现在我们看下，如果设置提交表单数据的方式是get方式，那么这个表单数据是如何被提交到当前页面的？

   首先我们先输入数据。如果是以get方式来请求，那么此时提交之后表单数据会在url后面拼接表单的数据，如图。这个URL的长度是限制的，那么通过get方式提交数据是无法提交一个比较大的表单，因为url有长度的限制，当然如果你没有给method赋值的话，那么method的默认值就是“get”，也就是说“get”是method属性的默认值。<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230707133518398.png" alt="image-20230707133518398" style="zoom: 67%;" />

7. 接下来我们将method属性的值改为post的方式来提交表格表单，那么接下来又是如何提交的呢？现在提交之后在url后面就没有携带采集到的拼接的表单数据了。那我们怎么看是如何提交的？此时我们需要打开浏览器开发的工具-直接按F12，找到Network（网络请求）这一栏，然后我们再输入数据之后按提交的按钮。我们就会看见一个网络请求，点击进去，再点击payload就可以看看我们提交的数据；点击view parsed就可以看见原始的数据格式，这个东西我们称呼为**“消息体或者叫做请求体”**，那么通过post方式提交的表单数据是在“消息体”当中传递的。这种方式**传递的表单参数是无大小限制**的。![image-20230707135055281](C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230707135055281.png)



- **注意：表单项必须有name属性才可以提交。**

### 表单项标签

表单里的标签就是表单项标签，主要有三个：input标签、select标签和textarea标签。通过这三个标签就可以衍生出各式各样的表单输入形式，比如文本输入框、单选按钮、复选按钮、下拉列表、文本域等等。

- \<input>：表单项，通过type属性控制输入形式
- \<select>：定义下拉列表<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230707163911451.png" alt="image-20230707163911451" style="zoom: 50%;" />
- \<textarea>：文本域<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230707164006726.png" alt="image-20230707164006726" style="zoom: 50%;" />



接下来我们就来看下通过这三个文本项标签是如何来实现各式各样的表单输入形式的。

- \<input>虽然是一个标签，但是它可以通过其中type属性的取值来控制输入的形式，而且type属性的可取值比较多，通过type属性各种各样的取值，就可以衍生出各种各样的表单形式。![image-20230707163333806](C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230707163333806.png)