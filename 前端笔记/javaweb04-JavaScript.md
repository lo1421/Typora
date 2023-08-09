javaScript

[TOC]

**复习web标准**

- web标准也成为网页标准，由一系列的标准组成，大部分由W3C（World Wide Web Consortim，万维网联盟）负责制定

- web标准由三个部分组成：

  - HTML ：负责网页的结构（页面元素和内容）
  - CSS：负责网页的表现效果（页面元素的外观，位置等页面样式，如颜色、大小等）。
  - JavaScript：负责网页的行为（交互效果）

  

# 什么是JavaScript?

- JavaScript（简称：JS）是一门跨平台、面向对象的脚本语言。是用来控制网页行为的，它能使页面交互。
- JavaScript和Java是完全不同的语言，不论是概念还是设计。但是基础语法类似。
- JavaScript在1995年由Brendan Eich 发明，并于1997年成为ECMA标准。
- ECMAScript（ES6）是最新的JavaScript版本（发布于2015年）。

脚本语言指的是不需要经过编译，直接经过浏览器的解释就可以运行了，而java编程语言是必须经过编译器编译之后生成.class 字节码文件之后，再经过JVM虚拟机去运行。这样就简化了这个开发的过程，因为不需要进行编译，并且JavaScript是用来控制网页行为的，它能够使网页交互。

这里举一个例子，可以通过JS来完成网页主题的切换。

## JavaScript的总体安排

### js引入方式

JS和HTML的结合方式就是JS的引入方式

#### 内部脚本：

**将js代码定义在HTML页面中**

- JavaScript代码必须位于\<script>\</script>标签之间
- 在HTML文档中，可以在任意地方，放置任意数量的\<script>
- 一般会把脚本置于\<body>元素的底部，可以改善显示速度

#### 外部脚本：

**将JS代码定义在外部JS文件，然后引入到HTML页面中**

- 外部JS文件中，只是包含JS代码，不包含\<script>标签
- \<script>标签不能自动闭合！！！

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



#### 变量

##### ①var全局变量

- **JavaScript中使用var关键字来声明一个变量****，其中var是（variable的缩写）

- JavaScript是一门弱类型的语言，变量可以存放不同类型的值。

- 变量名的命名规则：

  1. 组成字符可以是任何数字、字母、下划线（_）或美元符号（$）
  2. 不能以数字开头
  3. 命名规范：建议使用驼峰方式命名

- 通过var关键字定义的变量，有两个非常重要的特点

  1. ​	var定义出来的变量的作用域比较大，属于全局变量。

     比如js的内容是在大括号中，我们可以在大括号中声明一个var变量x，然后赋值为1，然后紧接着使用alert输出语句将x输出（这是在大括号里面获取代码），那么如果在大括号的外面获取这个变量x，是否能够获取到？刚刚解释过var关键字声明的变量的作用域比较大，而且是全局变量，那么x是var关键字声明的变量，所以x变量的作用域非常的大，我们可以在大括号的外面也获取到。

  2. 通过var定义的变量是可以重复定义的

     意思就是var声明的变量的变量名是可以一样或者重复出现的。而且会把后声明的同名变量的值覆盖掉先定义的同名变量的值。

##### ②新增局部变量let和常量const

- **注意：**
  - ​	**ECMAScript6新增了let关键字来定义变量，它的用法类似于var，但是所声明的变量，只在let关键字所在的代码块中有效，而且不允许重复声明。**
  - ​    **ECMAScript6新增了const关键字，用来声明一个只读的变量，一旦声明，常量的值就不能改变。**



```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>变量定义</title>
</head>
<body>
    <script>
       /*  var a = 100;
        a = "张三";
        // 通过alert，可以将a的值以警告框的形式在浏览器打开的HTML网页中弹出
        if(a=="张三"){
            window.alert(a);
        }
        window.alert(a);//特点一：var声明的变量为全局变量
        var x = 1;
        var x = "A";//可以重复声明
        alert(x);//A */

        //js中let关键字来声明变量是一个局部变量，只在声明的代码块中可以访问。
       /*  {
            let b = 1;
            alert(b);
            //let b = 2;同时let定义的变量不能重复声明，这样编辑器会报错
        } */


        //alert(b);
        //js中使用const关键字声明的变量其实就类似一个常量，一旦声明，其值就不能再改变了
        
        {   
             const PI = 3.14;
            PI = 3.1415926;
            alert(PI);
        }
        // 我们发现没有拿到我们想要的值，我们可以打开浏览器的开发者工具，点击Console，发现我们写的这个程序已经报错了。
</script>
</body>
</html>
```

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230708163431442.png" alt="image-20230708163431442" style="zoom: 25%;" />





#### 数据类型、运算符、流程控制语句

##### 一、数据类型

- 虽然JavaScript中定义变量的时候没有定义变量的类型，但是有数据类型。
- JavaScript中的数据类型分为：**原始类型和引用类型**

引用类型主要指的是JS中的对象，而原始数据类型就类似于java语言中的基本数据类型，主要包括以下五种。

| 原始类型                                                     |
| ------------------------------------------------------------ |
| number：数字（整数、小数、NaN（Not a Number））              |
| string ：字符串，单双引号都可以                              |
| boolean：布尔。true，false                                   |
| null：对象为空                                               |
| undefined：当声明的变量未初始化的时候，该变量的默认值是undefined |

**我们知道js是弱类型的语言，那么我们怎么去知道某个变量的类型是什么呢？在js当中提供了一个运算符” typeof “，通过这个运算符，就可以获取到某个变量的数据类型。**

```js
var a = 20;
alert(typeof a);
```

接下来演示五种原始数据类型

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>数据类型</title>
</head>
<body>
    <script>
        //原始数据类型演示
        alert(typeof 3);//拿到的类型是number
        alert(typeof 3.14);//拿到的类型是number

        alert(typeof "A");//拿到的类型是string
        alert(typeof 'Hello');//拿到的类型是string

        alert(typeof true);//boolean
        alert(typeof false);//boolean

        alert(typeof null);//这个拿到的是什么类型？拿到的是一个object类型的变量，object表示拿到的是一个对象
/* 
    为什么这里拿到的不是null而是一个object类型，其实这是因为这里是js早期的一个bug，不过被沿用至今了而已。
我们可以去打开官方文档W3CSchool，点击官方文档首页面的Browser Side，然后点击JavaScript，然后再点击JS教程。找到
JS当中的数据类型，找到页面的底部的课外阅读框中的“ECMAScript原始类型”五种数据类型中有一种就是null，然后注释中
也解释为什么会出现使用typeof运算符查询null的原始类型的时候返回的是一个object类型。现在null被认为是对象的占位符，从而解释了这一矛盾
但是从技术上来说，它仍然是原始值。
 */        var a ;
        alert(typeof a);//这个是没有初始化的变量，那么拿到的值是什么类型的呢？应该即使undefined
    </script>
</body>
</html>
```



##### 二、运算符

 算术运算符：+ , - , * , / , % , ++ , --
 赋值运算符：= , += , -= , *= , /= , %=
 比较运算符：> , < , >= , <= , != , == , === 
 逻辑运算符：&& , || , !
 三元运算符：条件表达式 ? true_value: false_value



- **JS里的运算符几乎全部和java中的运算符一样，只有一个运算符”===“是java中没有的**，三个等号也被称为全等运算符，所以接下来我们需要介绍全等运算符，是通过与两个等号运算符来对比着学习。

- **==会进行类型转换，===不会进行类型转换**

  ==是会先比较运算符两边数据的类型是否一样，如果不一样就会先类型转换，然后再比较值是否相等；而如果使用的是===运算符进行比较的时候，是不会进行类型转换的，全等运算符如果发现两边的数据类型不一样，那么就会直接判断不相等。全等只有在等号两边类型混合数值都相同的情况下才会返回

- 运算符运算的结果是返回boolean类型的值

```js
var a = 10;
alert(a == "10"); //true
alert(a === "10"); //false
alert(a === 10); //true
```



##### 三、JS当中常见的类型的转化

- 字符串类型转为数字：

  ​		将字符串字面值转为数字。 如果字面值不是数字，则转为NaN。

- 其他类型转为boolean：

  Number：0 和 NaN为false，其他均转为true。
  String：空字符串为false，其他均转为true。
  Null 和 undefined ：均转为false。

分析可以发现：

五种原始类型在转换为boolean类型的时候，都有对应的值转换成false，然后剩下的值就都是true，当然这里可以不用考虑boolean这个原始类型的转换，所以就只有四种原始类型转换为boolean类型的情况。

| 原始数据类型 | 转换为boolean类型的时候值为false     |
| ------------ | ------------------------------------ |
| Number       | 0和NaN（Not a number），其它均为true |
| string       | 空的字符串，其它均为true             |
| null         | null                                 |
| undefined    | undefined                            |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-运算符</title>
</head>
<body>
    <script>
        var age = 20;
        var _age = "20";
        var $age = 20;

        alert(age == _age);//true
        alert(age === _age);//false
        alert(age === $age);//true

        //类型转换-字符串转为数字

        // 字符串类类型转换为int型，如果双引号里面是数字那么就类型转换为数字，如果引号里面不是数字那么就转换为NaN
        alert(parseInt("12"));//12
        alert(parseInt("12A45"));//12
        /*
        使用parseInt()将字符串转换成int型的时候，会从第一个数开始判断，
        如果是数字就转换，一旦遇见不是数字的字符就停止转换，所以上述的
        转换的结果就是12，因为检测到A不是数字就停止了转换。
        */
        alert(parseInt("A45"));//NaN(表示Not a number不是一个数字)
       /* 
        由于这里一个开始检测的时候发现一个数字都没有，然后就不进行检测了，
        直接判断该字符中的内容不是数字，然后就直接返回NaN
        */

        //其他类型转换为boolean类型

        //这里是数字类型转换为boolean类型
        if(0){//由于if表达式中是一个boolean类型，那么这里就会有其他类型转换为boolean类型的一个转换
            alert("0 转换为false");
        }
        if(NaN){
            alert("NaN转换为false");
        }
        if(-1){
            alert("除0和NaN其他数字都转换为true");//这一行会输出，这里的if和java当中的if一样，只有if表达式为true才会执行括号里的内容
        }

        //字符串类型转换为boolean类型，只有空的内容的字符串转换为boolean类型的才会是false，其他情况全部都为true
        if(!""){
            alert("空字符串为false，其他都true")
        }

        //null类型转换为boolean类型
        if(!null){
            alert("null 转换为false");
        }
        
        //为声明的类型默认是undefined类型，这个类型转换为boolean类型也是false
        if(!undefined){
            alert("undefined转换为false");
        }

    </script>
</body>
</html>
```



##### 四、流程控制语句

- if…else if …else…
-  switch
-  for 
-  while
-  do … while

这些都是和java当中的控制语句都是一样的，这些流程控制语句可以在W3School官方文档当中查阅。



### js函数

**在java当中称为方法，在js中称为函数**

**函数**

- 介绍：函数（方法）是被设计为执行特定的任务的代码块
- 定义：JavaScript函数通过function关键之来进行定义或者声明，语法为：

```js
function functionName(参数1,参数2...){
//方法体或者函数体或者要执行的代码
}
//add函数
function add(a,b){
    return a+b;//是用来运算两个数之和的一个函数或者方法
}
```

- 注意：
  - 形式参数不需要类型，**因为JavaScript是弱类型语言**
  - 返回值也不需要定义类型，可以在函数内部直接使用return返回即可
- 调用：函数名称（实际参数列表）

如果调用的函数又返回值，那么我们就要声明一个变量去接收这个返回值。

例如：

```js
var result = add(10,20);//调用上述的add方法，然后会返回一个数值，我们定义一个变量去接收这个返回值
asert(result);//30
```

JS中的函数还有一种定义的方式：

基本思想就是把定义好的函数的整体当做一个变量，然后使用一个var关键字声明一个变量去接收这个函数

```js
//基本语法
var functionName = function(形参1，形参2...){
//函数体或者方法体或者要执行的代码
}
//具体的实例、函数的定义、两个数相加的函数
var add = function(a,b){//这里的add是自定义的方法名
retrun a+b;
}
//调用这个函数
```

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230708222152290.png" alt="image-20230708222152290" style="zoom:67%;" />



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-函数</title>
</head>
<body>
    <script>
        //我们可以在HTML文件的任意位置引入js代码，js的引入有两种方式，分别为：内部脚本和外部脚本
        /*我们现在采用的就是内部脚本，是通过在html文件中的任意位置，使用HTML中的一个<script>标签来引入的
        这种方式和把CSS样式引入到HTML中的第二种内嵌样式是非常相似的，都是通过一个HTML中专门为CSS和JS提供的
        专属标签来引入对应的代码。  
        */
       
        //定义函数d的第一种方式！
        function add(a,b){
            //js中的函数的形参是不需要指定类型的，js函数的声明也不需要指定返回值的类型，这都是因为JS是一门弱类型的语言
        return a+b;//函数的具体实现就是将传递进来的两个实参相加之后返回一个结果即可。
        }

        //函数的调用
        var value = add(10,20);
        alert(value);

        //函数调用的第二种方式！
        var sum = function(a,b){
            return a+b;
        }

        //函数的调用
        var value = add(10,20.30,40);
        /*函数调用可以传递任意个数的参数，但是方法只接受两个，具体的实现是第一实参传递给了a，第二个实参传给了b，后面两个参数传递的时候没有被方法接收，所以运算的结果依旧是30*/
        alert(value);

    </script>
</body>
</html>
```

- **注意事项**     JS中，函数调用可以传递任意个数的参数。

### js对象

JS当中为我们提供了很多的对象，我们可以打开官方文档，查阅JS的参考书。JS当中的对象可以细分为三类，第一类对象就是JavaScript提供的基础对象，在基础对象当中我们重点关注其中的三类对象

- 第一类对象：Array数组对象，String字符串对象和JSON对象；
- 第二类对象：BOM对象（浏览器对象模型，指的是在JS当中对浏览器的各个组件进行了封装，把浏览器封装成了对象）；
- 第三类对象：DOM对象（文档对象模型，JS当中提供了很多的DOM对象，其实在JS当中DOM对象就是把每一个HTML标签都封装成了一个对象）

#### Array数组对象 

JavaScript中Array对象用于定义数组

###### 一、方式

```JS
/*JS当中数组的定义*/
var 变量名 = new Array(元素列表);//方式一
var arr = new Array(1,2,3,4);

var 变量名 = [];//方式二
var arr = [1,2,3,4];

/*JSd当中数组的访问*/
arr[索引] = 值;
arr[10] = "Hello";
//Js当中数组的访问就和java中的语法一样了
```



###### 二、特点

JS当中的数组类似于java中的集合，那么JS中的数组具有的特点：**长度可变/存放数据的类型也是可变的，而且数组**中没有赋值的元素的值是“undefined”。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>02.JS-对象-Array</title>
</head>
<body>
    <script>
         //定义数组的第一种方式
    var arr = new Array(1,2,3,4);
        //定义数组的第二种方式
    var arr1 =[5,6,7,8,];
    //访问数组中的元素
    console.log(arr[0]);
    console.log(arr[1]);
    console.log(arr1[0]);
    console.log(arr1[1]);
    arr[10] = 50;
    //这代表我要把arr数组中的值赋值为50，但是我们定义的数组的长度是4，
    //这在java中是会报错的，但是在JS的数组中，数组的长度是可变的，值也是可以修改的
    //我们现在向浏览器的控制台输出一下这个数组的值
    console.log(arr[10]);
    //那么这里会有疑问，那么数组当中索引为8、7、6...等等的值又是多少呢？
    //我们可以输出一下索引为9，索引为8的值是什么？
    console.log(arr[9]);//undefined
    console.log(arr[8]);//undefined

    /*现在咱门可以测试一下Js数组当中的元素的类型是否可变，因为之前测试的数组的长度是可变的，
    要是数组的类型也是可变的话，这就意味着数组当中是可以存放不同类型的元素的*/
    //我们把索引为9的arr数组元素的值设置为字符串类型的，看看是否会报错，如果不报错而且成功输出了那么就可以证明
    arr[9] = "school";
    alert(arr[9]);
    </script>
</body>
</html>
```

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230709162302682.png" alt="image-20230709162302682" style="zoom:50%;" />

**注意：JavaScript中的数组相当于Java中的集合，即JS中数组的长度是可变的，而JavaScript是弱类型，所以可以储存任意类型的的数据。**

###### 三、属性

由于Array是作为Js中的一个对象，那么作为对象就应该有对应的属性和方法，接下来我们就来学习js的Array数组中的常见的属性和方法。

| 属性   | 描述                                                     |
| ------ | -------------------------------------------------------- |
| length | 设置或者返回数组中储存元素的数量，或者是返回数组的长度。 |



###### 四、方法

| 方法      | 描述                                                 |
| --------- | ---------------------------------------------------- |
| forEach() | 遍历数组中的每个储存值的元素，并调用一次传入的函数。 |
| push()    | 将新元素添加到数组的末尾，并返回新的长度。           |
| splice()  | 从数组中删除元素。                                   |

- 方法：这里的forEach方法是一个有参函数，该函数的参数是一个函数，这个函数是用来处理我们每一次遍历出来的元素，每遍历一个元素，它就会自动调用一次传进来的函数。
- 当你使用for循环去遍历数组和使用forEach方法去遍历数组是有区别的，区别在于for循环遍历数组元素的时候，是无论数组中的元素有没有值，他都会输出（也就是没有保存值的元素输出的值是undefined）；而使用forEach方法的时候，像没有储存指的元素是不会被遍历到的，最后也就不会输出。

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230709165329674.png" alt="image-20230709165329674" style="zoom:50%;" />

- 在ES6中提供了一章函数书写的简化形式：函数的关键字是可以省略的，有点像java中的lambda表达式。在JS中叫做**“箭头函数”**，专门用来简化函数的书写。一下就是一个实例：

```js
var arr = new Array(1,2,3,4);//第一种定义数组的方式

 //forEach方法：遍历数组当中有值的元素
    arr.forEach(function(e){
        console.log(e);
    });//我们直接可以声明一个函数
/*     这个函数forEach的功能就是每遍历一次，那么就会调用一次这个函数function，然后function的具体实现又是
去输出遍历到的元素，那么整体的功能就是遍历数组中有储存值的元素 */    

    //简化形式：使用箭头函数：(...)=>(...)
    arr.forEach((e)=>{
        console.log(e);
    })
```

- push：添加元素到数组尾部的方法

可以一次添加一个或者多个元素

```js
arr.push(7.8.9);//这里是表示一次往数组的尾部添加多个元素
Console.log(arr);//这里是直接把数组中的所有的元素都往浏览器的信息框输出
```

- splice：删除元素

splice的翻译为拼接，是有参函数，有两个参数，第一个是start：number，起始元素的位置，第二个是deleteCount？：要删几个。

```
arr.splice(2,2);//从索引为2的元素开始删，一共删除两个元素
console.log(arr);//输出到元素的控制台上。高度                                               
```

#### String字符串对象

###### 一、方式

- String字符串对象的创建方式有两种：

```js
var 变量名 = new String("...");//方式一
var str = new String("Hello String");

var 变量名 = "...";//方式二
var str = "Hello String";
var str = 'Hello String';
```

二、属性

length：字符串的长度

三、方法

| 方法        | 描述                                             |
| ----------- | ------------------------------------------------ |
| charAt()    | 返回在指定位置的字符。                           |
| indexOf()   | 检索字符串。                                     |
| trim()      | 去除字符串两边的空格。（中间的空格是不会去除的） |
| substring() | 提取字符串中两个指定索引号之间的字符。           |

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-对象-String</title>
</head>
<body>
    <script>
        //创建字符串对象
        //第一种方式
      //  var str = new String("Hello String");
        //第二种方式(明显更加方便)
        var str = "Hello String     ";
         
        
        //length属性
         console.log(str.length);//获取length属性的值：12

         //charAt()获取指定位置的字符
        console.log(str.charAt(4));//o

         //indexOf()检索字符串,传入要检索的元素，获取该元素在数组中的下标
         console.log(str.indexOf('H'));//0

         //trim()去除字符串左右两侧的空格，字符串str的右侧有空格,去除之后又会返回一个新的字符串
        var s = str.trim();
        console.log(s);//Hello String

         //substring(start,end)，截取字符串之后获取一个子字符串的方法,参数：开始索引，结束索引（含头不含尾）
        console.log(s.substring(0,5));//Hello
        

    </script>
</body>
</html>e
```

#### JSON对象

接下来我们来讲解JS基础对象当中的最后一个JSON对象，在讲解JSON对象之前我们先来讲解JavaScript中的自定义对象。

##### JavaScript自定义对象

- 定义格式：

var 对象名 = {

属性名1：属性值1，

属性名2：属性值2，

属性名3：属性值3，

函数名称：function（形参列表）{ }

} ；

```js
var user = {
name :"Tom",
gender:"male",
age:20,
eat :function(){
alert("用膳"~);
}
};
```

- 调用格式：

对象名.属性名；

对象名.函数名；

```js
var name = user.name;
alert(name);
var age = user.age;
alert(age);
var gender = user.gender;
alert(gender);
user.eat();
```

实例：

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-对象.JSON</title>
</head>
<body>
    <script>
        // javascript当中的自定义一个对象是如何实现的呢？
        var person = {
            id:1234567,
            name:"张三",
            sex :false,
            speak: function(){
                alert("在说话");
            }
            //js中自定义的对象中的函数是可以简化的，解下来就写一个简化的版本吧
            study(){
                alert("在学习");
            }
        }
        //自定义的对象的使用，通过调用对象中的属性和函数
        alert(person.name);
        alert(person.id);
        alert(person.sex);
        //调用自定义的方法
        person.speak();
    </script>
</body>
</html>
```



##### JSON-介绍

- 概念：JavaScript Object Notation，java对象标记法。
- JSON是通过JavaScript对象标记法书写的文本。
- 网上有JSON格式校对的工具
- JS本身就是文本语言，而JSON是字符串的形式也就不奇怪了。但是必须使用双引号。
- JSON对象的语法是比较简单的，就是被大括号括起来的key和value键值对的形式存在，只不过key必须使用字符串（只能是双引号不能说单引号）的格式。
- 由于JSON语法简单，层次结构鲜明，现多用于作为数据载体，在网络中进行数据传输。那么JSON具体是在哪里使用呢？由于前端人员开发的前端程序要请求后端人员开发的服务端java程序，那如果前端在请求服务端的时候要携带比较复杂的数据，我们就需要选择合理的数据载体。比如XML语言，就可以作为数据载体来存储数据，但是我们会看到XML在传递数据的时候会非常的臃肿，数据倒不多但标签一大堆，所以现在在前后端的交互当中基本上就不会使用XML语言，而是采用JSON这种数据格式来传递数据，现在在前端请求服务端的时候，需要携带比较复杂的数据的时候，我们就可以使用JSON来作为数据载体，而如果服务端想要给前端响应比较复杂的数据的时候也可以采用JSON数据格式来传递数据。

##### JSON-基础语法

- **定义**

- var 变量名 = '{"key1":value1,"key2":value2,...}';
- 实例：var userStr ='{"name":"Jerry","age":18,"addr":["北京","上海",西安] }';
- 我们可以直接通过var来直接定义一个变量，而我们刚刚提到JSON是一个文本，所以我们要为这个变量赋一个JSON对象的值，使用单引号引起来才是一个字符串，而JSON里面的若干个可以值就必须使用双引号引起来，而value值就根据具体的数据类型的不同对应做变换。

- **value 的数据类型为：**
  数字（整数或浮点数）
  字符串（在双引号中）
  逻辑值（true 或 false）
  数组（在方括号中）
  对象（在花括号中）
  null

很显然就算我们使用var关键字把JSON文本给声明出来之后，这里面的key是不可以访问的，因为此时的JSON还是一个被引号括起来的字符串，这个时候怎么办？JS中就给我们提供了两个方法。是完成JSON字符串和JS对象互相转换的方法。

1. JSON字符串转为JS对象的方法

   ```js
   var jsObject = JSON.parse(userStr);
   ```

2. JS对象转为JSON字符串的方法

```js
var jsonStr = JSON.stringfy(jsObject);
```



#### BOM对象

##### ①概念

Browser Object Model浏览器对象模型，允许JavaScript与浏览器对话，JavaScript将浏览器的各个组成部分封装为对象。 （那么BOM当中究竟提供了哪些浏览器对象呢？我们可以直接打开JavaScript的参考手册，点击JavaScript，一直往下翻我们就会看见出现DOM和BOM，我们来看BOM），BOM中主要提供的对象主要有五个WIndows、Screen、Location、History和Navigater。那这五个BOM对象主要代表什么意思呢？由于BOM对象是JS中提供的将浏览器各个部分封装起来的，那么BOM主要提供的这五个对象就应该是跟浏览器的组成有关，而这些队形对象中肯定有对应的属性和方法。

##### ②组成

-  Window：浏览器窗口对象
- Navigator：浏览器对象
- Screen：屏幕对象
- History：历史记录对象
- Location：地址栏对象

- 对于我们来说，我们只用了解两个对象，一个是window浏览器窗口对象，另一个location地址栏对象。

##### 浏览器窗口对象window

- 介绍：浏览器窗口对象

- 获取：直接使用window，其中" window. "可以省略。 window.alert("Hello Window"); 或者alert("Hello Window");
- 属性（通过使用“window.”的方式去获取这些属性之后会返回对应的BOM对象）
  - history：对于History对象的只读引用。请参阅History对象。
  - location：对于窗口或者框架的Location对象。请参阅Location对象。
  - navigator：对Navigator对象的只读引用。请参阅Navigator对象。
- 方法
  - alert ( ) : 显示带有一段消息和一个确认按钮的警告框。
  - confirm()：显示一段消息以及确认按钮和取消按钮的对话框。
  - setIntrval（）：按照指定的周期（以毫秒计）来调用函数或者计算表达式。
  - setTimeout（）：在指定的毫秒数后调用函数或者计算表达式。

获取window对象，直接吧window写出来就已经算是获取到了window对象了，然后调用里面的方法。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-对象-BOM</title>
</head>
<body>
    <script>
        //获取
    /*  window.alert("Hello BOM");
        alert("Hello BOM Window"); */
        //方法
        //confirm()方法被调用之后，会在浏览器弹出一个对话框，然后在对话框中弹出一个提示的信息
    // confirm("您确认删除该记录吗？");
        //由于有两个选项，一个是确认，一个是取消，选择不同的选项的结果是不一样的，那么我们要如何知道用户选择的是什么呢？
        // 其实这个confirm（）方法有一个返回值的，那么这个返回值到底是什么呢？
    var flag = window.confirm("您确定要删除该文件吗？");
    //直接使用alert方法把这个值弹出来，看看返回的是什么值？
    alert(flag);
    // 当我们点击确定的时候，返回值是true；然后再刷新一下，点击取消的按钮，返回的值是false。

    //定时器-setInterval（）：周期性的执行某一个函数。
    //这个方法中有两个参数，一个是定期执行哪个函数，第二个是间隔多少毫秒去执行一次前面的那个函数
    var i= 0;
    setInterval(function(){
        i++;
    console.log("定时器执行的次数为："+i);
    },1000);

    //定时器-setTimeout（）：延迟指定时间执行一次，注意真的就只是执行一次。
    //这个方法也是有参函数，当中有两个参数，第一个参数是要执行的函数，第二个是延迟多少时间才去执行。
    setTimeout(function(){
alert("JS");
    },3000);//表示3秒之后就要执行这个函数了。
    
    </script>   
</body>
</html>
```

##### 地址栏对象Location

- 介绍：地址栏对象
- 获取：使用window.location.获取，其中window.可以省略。

window.lcation.属性；  或者location.属性

- ​	属性：

  - herf：设置返回完整的URL。

  如果不赋值的话，那么就获取的是当前网页的url信息。
  
  location.herf = "http://www.itcast.cn";
  
  当我们为这个herf属性赋值之后，那么打开浏览器之后，浏览器首先是会先将默认的当前页面的url地址信息弹出来，然后会将URl赋值为我们现在新设置的url地址，并且自动跳转到我们后面指定值对应的网页。

#### DOM对象

**概念：Document Object Model ，文档对象模型。**



将标记语言的各个组成部分封装为对应的对象：

- Document：整个文档对象（代表的就是整个被封装的HTML文档对应的JS中的文档对象）
- Element：元素对象（将HTML文档中的每一个标签都会封装成为JS中的元素对象）
- Attribute：属性对象（标签当中的属性也会被封装为JS中的属性对象）
- Text：文本对象（是HTML当中定义的文本也会被封装为JS当中的文本对象）
- Comment：注释对象（如果标记语言中有注释那么也会把注释封装为JS中的对象）

以上五类对象就是DOM当中最基础的五类对象，HTML文档被浏览器加载并解析以后就会被封装为这五类对象，同事在浏览器的内存当中也会形成一个**“DOM结构“**，而这个DOM结构被我们称为“DOM树”，在这个文档当中会有一个对应的元素对象也就是html元素对象（同时也是根元素），而在根元素之间还有两个元素。

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230710171330723.png" alt="image-20230710171330723" style="zoom: 67%;" />

```html
<html>
    <head>
        <title>DOM</title>
    </head>
    <body>
        <h1>DOM对象标题</h1>
        <a href="https://itcast.cn">传智教育</a>
    </body>
</html>
```



**在JS当中，通过DOM主要是来操作什么呢？能够解决什么问题呢？我们为什么要学习这个DOM呢？**

其实我们之前一直在讲JS是用来控制网页的行为的，那么网页的行为的控制主要就是通过JS当中的DOM以及后续要学习的事件监听来实现的。

 JavaScript 通过DOM，就能够对HTML进行操作：

- 改变 HTML 元素的内容
- 改变 HTML 元素的样式（CSS）
- 对 HTML DOM 事件作出反应
- 添加和删除 HTML 元素

##### DOM的组成部分

- DOM是W3C（万维网联盟）的标准，定义了访问HTML和XML文档的标准，分为三个不同的部分：
  1. Core DOM-所有文档类型的标准模型(核心DOM)
     - Document：整个文档对象
     - Element：元素对象
     - Attribute：属性对象
     - Text：文本对象
     - Comment：注释对象
  2. XML DOM-XML文档的标准模型（XML DOM）
  3. HTML DOM-HTML文档的标准模型（HTML DOM）
     - image：\<img>
     - Button:\<input type = 'button'>

```html
<html>
    <head>
        <title>DOM</title>
    </head>
    <body>
        <h1>DOM对象标题</h1>
        <a href="https://itcast.cn">传智教育</a>
    </body>
</html>

```

- DOM被分成Core DOM（核心部分）、XML DOM（XML部分）和HTML DOM (HTML部分)。第一个核心DOM部分指的是针对于任何”**标记语言**“的标记模型，不论你是XML标记语言还是HTML标记语言都一定会包含这些标准的DOM对象（或者说标准的DOM对象适用于任何的标记语言，是具有普遍性的、概括性的模型），而我们主要学的就是刚刚学的五种DOM对象：Document文档对象、Element元素对象、Attribute属性对象、Text文本对象和Comment注释对象。

- XML   XML -DOM是核心DOM的子集，定义了XML文档的标准模型。

- HTML HTML-DOM是在核心DOM的基础上进行了扩充，把所有的HTML的标签都封装成了一个单独的元素对象，可以查看W3school 文档。我们学习HTML-DOM主要学习两点：获取元素对象和调用元素对象当中的属性和方法，从而来操作HTML当中的元素对象。

  - 如何获取HTML-DOM当中的指定的元素对象

    - HTML中的Element对象可以通过Document对象获取，而Document对象是通过Window对象获取的。    

    - Document对象提供了以下获取Element元素对象的函数

      1.根据id属性值获取，返回单个Element对象(这里是没有s的，因为id是不会重复的)

      ```js
      var h1 = document.getElementsById('h1');
      ```

      2.根据标签名称获取，返回Element对象**数组**

      ```js
      var divs =document.getElementsByTagNmae('div');
      ```

      3.根据name属性值获取，返回Element对象**数组**

      ```js
      var hobbys = document.getElementsByName('hobby');
      ```

      4.根据class属性值获取，返回Element对象**数组**

      ```js
      var clss = document.getElementsByClassName('cls');
      ```

**代码实现：**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-对象-DOM</title>
</head>
<body>
    <img  id = 'h1' src="D:\HTML\img\off.gif"> <br><br>

    <div class="cls">传智教育</div> <br>
    <div class = "cls ">黑马程序员</div> <br>

    <input type="checkbox" name="hobby"> 电影
    <input type="checkbox" name="hobby">旅游
    <input type="checkbox" name="hobby">游戏 
</body>
<script>
    //1.获取Element元素
    //1.1获取元素-根据ID获取
   /* var img = document.getElementById('h1');
   alert(img);//可以弹出来看看我们是否获取到了封装好的元素对象,获取到了=>[object HTMLImageElement]
 */
    //1.2获取元素-根据标签获取(返回的是一个对象类型的数组，所以是复数的形式)
   /*  var divs =  document.getElementsByTagName('div');
   for (let i = 0; i < divs.length; i++) {
    alert(divs[i]);
   } */

    //1.3获取元素-根据name属性获取(由于name属性也不是唯一的，所以就直接返回一个数组)
  /* var ins =   document.getElementsByTagName('hobby');
    for (let j = 0; j < ins.length; j++) {
        alert(ins[j]);
    } */
    
    //1.4获取元素-根据class属性获取（由于class属性的值是可以重复的，所以返回的值就也是一个储存元素对象的数组）
   /*  var divs = document.getElementsByClassName('cls');
    for (let j = 0; j < divs.length; j++) {
        alert(divs[j]);   
    } */
    //通过上述操作，我们已经可以获取到任何一个被封装成元素的属性了。
    // 现在就可以通过一些属性或者方法来对我们获取到的元素对象进行一些操作来修改了
    //由于返回来的divs是一个数组，我们现在的业务是修改第一个div
    var divs = document.getElementsByClassName('cls');
   /*  我们可以去官方文档的JS中的HTML DOM对象，然后找到被封装好的div标签的对象，
    然后再看看里面有什么方法和属性可以被我们利用然后来修改元素的内容。然后我们就
    发现了一个element.InnerHTML这个属性是用来“返回元素的内容或者设置元素的内容的” */
    
    //声明一个变量去接收数组中的第一个元素同时也是一个对象，当中有属性也有方法
    var div1 = divs[0];
    //设置这个元素
    div1.innerHTML ="传智教育很厉害";

</script>
</html>
```

##### JS-对象-DOM案例

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230710210630908.png" alt="image-20230710210630908" style="zoom:50%;" />

##### 代码实现

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-对象-DOM</title>
    <style>
        span{
            color: red;
        }
    </style>
</head>
<body>
    <img  id = 'h1' src="D:\HTML\img\off.gif"> <br><br>

    <div class="cls">传智教育</div> <br>
    <div class = "cls ">黑马程序员</div> <br>

    <input type="checkbox" name="hobby"> 电影
    <input type="checkbox" name="hobby">旅游
    <input type="checkbox" name="hobby">游戏 
</body>
<script>
    //1.点亮灯泡：改变src的属性值
    var img = document.getElementById('h1');
    img.src = "../img/on.gif";

    //2.将所有div标签后面加上：very good（红色字体）或者可以使用  "<font color = 'red'>very good</font>"
    var divs = document.getElementsByTagName('div');
    for (let i = 0; i < divs.length; i++) {
    divs[i].innerHTML+="<span >very good</span>";
    }
    //3.使所有的复选框呈现选中的状态
    var ins = document.getElementsByName('hobby');
    for (let i = 0; i < ins.length; i++) {
       ins[i].checked = true; //选中状态
    }
</script>
</html>
```



### js事件监听

要想了解JS当中的事件监听，就必须事先知道“**事件**”是什么？

- 事件：HTML 事件是发生在HTML元素上的“事情”。比如：
  - 按钮被点击
  - 鼠标移动到元素上
  - 按下键盘按键
- 事件监听：JavaScript可以在事件被侦测到时去 “执行代码”。

JS当中的事件绑定就是如何让事件发生之后来执行指定的代码，第一部分要学习的是事件绑定，第二部分是学常见的事件，第三部分是完成一个案例（通过DOM操作配合着事件监听来控制网页的行为）。

##### 事件绑定

事件的两种绑定的方式

方式一：通过 HTML标签中的事件属性进行绑定

```html
<input type="button" onclick="on()" value="按钮1">

<script>
    function on(){
        alert('我被点击了!');
    }
</script>

```

方式二：通过 DOM 元素属性绑定

```html
<input type="button" id="btn" value="按钮2">

<script>
    document.getElementById('btn').onclick=function(){
        alert('我被点击了!');
    }
</script>

```

第一种事件绑定的方式，例如我们要绑定一个按钮的单击事件，我们通过一个事件属性onclick来绑定，当这个按钮被点击的时候，那么就会执行onclick这个时间属性所绑定的方法on()。将JS的代码和HTML的代码耦合在一起了，可以从第一个例子中看出来，通过HTNL当中的onclick属性，然后这个属性绑定了on（）方法，然后在JS的代码中就会执行on（）方法。

第二种事件绑定的方式，我们可以通过document来获取指定的元素，然后再通过这个获取的元素对象中的时间属性onclick来完成事件绑定，为这个onclick来绑定一个函数，一旦这个按钮被点击了，就会自动调用这个函数。

**代码示例**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-事件-事件绑定</title>
</head>
<body>
    <input type="button" id ="btn1" value="事件绑定1" onclick="on()">
    <input type="button" id="btn2" value="事件绑定2">
    <script>
        function on(){
            alert("按钮1被点击了...");
        }

        document.getElementById('btn2').onclick =function(){
            alert("按钮2被点击了...");
        }
    </script>
</body>
</html
```

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230712202727260.png" alt="image-20230712202727260" style="zoom: 50%;" />![image-20230712202802001](C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230712202802001.png)

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230712202851032.png" alt="image-20230712202851032" style="zoom: 33%;" />



##### 常见事件

| **事件名**  | **说明**                 |
| ----------- | ------------------------ |
| onclick     | 鼠标单击事件             |
| onblur      | 元素失去焦点             |
| onfocus     | 元素获得焦点             |
| onload      | 某个页面或图像被完成加载 |
| onsubmit    | 当表单提交时触发该事件   |
| onkeydown   | 某个键盘的键被按下       |
| onmouseover | 鼠标被移到某元素之上     |
| onmouseout  | 鼠标从某元素移开         |



实际代码：事件绑定的方式一

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-事件-事件绑定</title>
</head>
<body  onload="load()">
    <form action="" style="text-align: center;"  onsubmit="subfu()">

    <input type="text" name="username" onfocus="ffn()" onblur="bfn()" onkeydown="kfn()">

    <input id="b1" type="submit" value="提交">

    <input  id="b1" type="button" value="单击事件" onclick="fn1()">

    </form>
    <br><br><br>
    <table  width = "800px"  border="1" cellspacing = "0"  align="center"  onmouseover="over()" onmouseout="out()">
        <tr>
            <th>学号</th>
            <th>姓名</th>
            <th>分数</th>
            <th>评价</th>
        </tr>
        <tr align="center">
            <td>001</td>
            <td>张三</td>
            <td>90</td>
            <td>很优秀</td>
        </tr>
        <tr align="center">
            <td>002</td>
            <td>李四</td>
            <td>92</td>
            <td>优秀</td>
        </tr>
    </table>
</body>
 <script>
        //onload：页面元素加载完成之后触发（这个方法和body标签绑定使用，一旦body加载完成之后，就会执行该方法）
        function load(){
            console.log("页面加载完成...")
        }

        //onclick : 鼠标点击事件（）
        function fn1(){
            console.log("我被点击了...");
        }

        //onblur：失去焦点事件
        function bfn(){
            console.log("失去焦点...");
        }

        //onfocus:元素获得焦点
        function ffn(){
            console.log("获得焦点...");
        }

        //onkeydown：某个键盘键被按下
        function kfn(){
            console.log("键盘被按下了...");
        }

        //onmouseover:鼠标移动到某元素之上
        function over(){
            console.log("鼠标移入了...");
        }

        //onmouseout：鼠标从某元素上移除了
        function out(){
            console.log("鼠标移除了...");
        }
        //onsubmit：提交表单事件
        function subfu(){
            alert("表单被提交了...");
        }

 </script>   
</html>
```



##### 案例

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230712215932019.png" alt="image-20230712215932019" style="zoom:80%;" />

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS-事件-案例</title>
</head>
<body>
    <!-- 这里是先使用HTML中的标签完成页面的内容也就是元素 -->
    <img src="../img/off.gif" id="light" >
    <br>
    <input type="button" value="点亮" onclick="on()">
    <input type="button" value="熄灭" onclick="off()">
    <br><br>
    <input type="text"  id = "name" value="ITCAST"  onfocus = "lower()" onblur="upper()" >
    <br><br>
    <input type="checkbox" name="hobby">电影
    <input type="checkbox" name="hobby">旅游
    <input type="checkbox" name="hobby">游戏
    <br>
    <input type="button" value="全选" onclick="checkAll()" >
    <input type="button" value="反选" onclick="reverse()">
</body>
<script>
    //1.点击“点亮”按钮，点亮灯泡；点击“熄灭”按钮，熄灭灯泡；--onclick事件作为一个属性绑定一个DOM对象里的方法
    function on(){
        //先获取DOM封装好的img元素对象
        var img = document.getElementById("light");
        //然后利用获取的对象中的属性来完成src属性的修改
        img.src ="../img/on.gif";
    }
    function off(){
        //获取DOM中的img元素对象
        var img = document.getElementById("light");
        img.src ="../img/off.gif";
    }
    //2.输入框聚焦之后，展示小写；输入框离焦之后，展示大写 --onfocus ,onblur
    function  lower(){
        //聚焦文本框之后展示小写
        //利用DOM对象，来获取输入框元素对象，然后访问对象中的方法或者属性
        var input = document.getElementById("name");
        //将值转为小写,这里的值就是value，这里涉及到字符串的大小写的转换
        input.value = input.value.toLowerCase();
    }
    function upper(){
        var input = document.getElementById("name");
        input.value = input.value.toUpperCase();
    }
    //3.点击“全选”按钮使所有的复选框呈现选中状态；点击“反选”按钮是所有的复选框呈现取消勾选的状态
    function checkAll(){//全选
//要获取所有的元素的对象
var hobbys = document.getElementsByName("hobby");//返回的是一个对象的数组
//通过for循环获取当中的一个一个的元素
for (let i = 0; i < hobbys.length; i++) {
   //然后访问对象中的方法或者属性，完成全选
    const element = hobbys[i];
    element.checked = true;
}

    }
    function reverse(){//反选
//要获取所有的元素的对象
var hobbys = document.getElementsByName("hobby");//返回的是一个对象的数组
//通过for循环获取当中的一个一个的元素
for (let i = 0; i < hobbys.length; i++) {
   //然后访问对象中的方法或者属性，完成反选
    const element = hobbys[i];
    element.checked = false;
}

    }
    
</script>
</html>
```

