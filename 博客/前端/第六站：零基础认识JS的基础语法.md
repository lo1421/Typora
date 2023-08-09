欢迎来到《JavaWeb的奇妙冒险》教学系列！在这里，我们将继续探索Web开发的精彩世界，本站将为你揭开JavaScript的神秘面纱。让我们在学习的过程中既轻松愉快，又能掌握高质量的知识。准备好进入第六站的学习之旅了吗？让我们开始吧！

# 第六站：零基础认识JS的基础语法

[TOC]



### js基础语法

#### 书写语法

- 区分大小写：与java一样，变量名、函数名以及其他所有的东西全部都严格区分大小写
- 每行结尾的分号可有可无（但是建议在编写js代码的时候还是把分号写上，这样更加严谨一点）
- 注释：(也可以利用VS Code中我们安装的插件，使用快捷键：多行注释ctrl+shift+左斜杠，单行注释ctrl+左斜杠)
  1. ​	单行注释：//注释内容
  2. 多行注释/\*注释内容\*/
- 大括号表示代码块

```js
if(count==3){//如果条件满足，则执行代码块，表示弹出conut的值
	alert(count);
}
```

##### 输出语句

- **使用window.alert()写入警告框**

  (window.是可以省略的，输出的语句是会在网页中以警告框的形式弹出来)

  <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230708155252429.png" alt="image-20230708155252429" style="zoom:50%;" />

- **使用document.write()  写入HTML输出**

  （直接将我们要写出的信息直接写入HTML文件当中然后在浏览器当中展示出来，最终会在HTML页面中直接看见输出的语句）

  <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230708155355468.png" alt="image-20230708155355468" style="zoom:50%;" />

- **使用console.log()写入浏览器控制台**

  （console是浏览器中的控制对象，调用该对象当中的log方法，就可以数据写入到浏览器的控制台，然后我们可以打开浏览器的控制台，然后点击到Console，看到我们输出的数据）

  <img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230708155640189.png" alt="image-20230708155640189" style="zoom:50%;" />

  <u>如何快速打开浏览器的控制台呢?</u>

  <u>点击鼠标右键选择"检查"或者点击快捷键F12。</u>

```javascript
<script>
	window.alert("Hello JS");//浏览器弹出警告框
	
	document.write("Hello JS");//写入HTML，在浏览器展示
	
	console.log("Hello JS");//写入浏览器控制台
<script>
```

