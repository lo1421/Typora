# js函数

[TOC]

**在java当中称为方法，在js中称为函数**

**函数**

## 介绍：

函数（方法）是被设计为执行特定的任务的代码块

## 定义：

JavaScript函数通过function关键之来进行定义或者声明，语法为：

```js
function functionName(参数1,参数2...){
//方法体或者函数体或者要执行的代码
}
//add函数
function add(a,b){
    return a+b;//是用来运算两个数之和的一个函数或者方法
}
```

## 注意：

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

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230708222152290.png" alt="image-20230708222152290"  />



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