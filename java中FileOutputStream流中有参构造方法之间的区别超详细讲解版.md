### java中FileOutputStream流中有参构造方法之间的区别超详细讲解版

##### 1.创建FileOutputStream流对象

使用有参构造方法，FileOutputStream流中的有参构造方法分别有：

public FileOutputStream(File file)：创建一个文件输出流写入指定的File对象表示的文件

public FileOutputStream(File file,boolean append)：创建一个文件输出流写入指定的FileInputStream对象表示的文件

public FileOutputStream(String filename,boolean append)：创建一个文件输出流，用指定的名称写入文件

public FileOutputStream(String filename)：创建一个文件输出流，用指定的名称写入文件

##### 2.使用文件目录的方式创建输入流对象有无append形参的区分

示例一：有append形参的构造方法分析

```java
package june.selfStudy.IO;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class HaveAppend {
    public static void main(String[] args) {
        //创建输入字节流对象
        FileOutputStream fos = null;
        try {
            //如果tempfile04文件不存在，那么就会自动生成一个tempfile04
            fos = new FileOutputStream("tempfile04",true);
            //准备一个byte[]数组
            byte[] bytes  = {97,98,99,100,101};
            //第一次写入：将byte数组的全部字节全部写入文件中
            fos.write(bytes);//tempfile04的文件在IDEA的当前的工程目录下生成，并且写入了abcde
            //第二次写入:指定长度的将数组中的内容写入文件中
            fos.write(bytes,0,2);//从数组索引为0开始，写进去两个字节,tempfile04文件中被写入了abcdeab
            //第三次写入：使用String转成byte数组的方式写入
            byte[] bs = "我们在学习FileOutputStream流中有参构造方法（包含append形参）".getBytes();
            fos.write(bs);//abcdeab我们在学习FileOutputStream流中有参构造方法（包含append形参）
            //输出流使用完之后必须刷新
            fos.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally{
            //养成一个关闭流的好习惯
            if(fos!=null){
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

    }
}

```

###### 通过上述程序我们可以总结出什么？

当使用含有append参数的构造方法去创建输出流对象的时候，往文件中写内容的时候，是不会把第一次写入或者第二次写入的内容清空然后新建一个文件去写入新的内容，同时我们可以试着理解append的翻译是“追加”,则表示后来写入文件的东西是以追加的方式写入的，如果append传入的是true，那么将字节写入文件的末尾处，而不是写入文件的开始处，就不会清空原文件的内容。

###### 示例二：无append形参的构造方法分析

```java
package june.selfStudy.IO;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

public class NoAppend {
    public static void main(String[] args) {
        FileOutputStream fos = null;
        try {
            fos = new FileOutputStream("tempfile05");
            //准备byte数组
            byte[] bytes = {97,98,99,100,101};
            //第一次写入
            //fos.write(bytes);//abcde
            //第二次写入
            fos.write(bytes,0,2);//ab
            //输出流使用完之后要刷新，养成好习惯
            fos.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally{
            if(fos!=null){
                try {
                    fos.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }

    }
}

```

总结：当使用`FileOutputStream(String name, boolean append)`构造方法并将`append`参数设置为`false`时，与使用`FileOutputStream(String name)`构造方法效果是一样的，都会在写入数据之前清空文件。

这是因为在`FileOutputStream`的源码中，当`append`参数为`false`时，会先检查文件是否存在，如果存在则删除文件内容，然后创建一个新的空文件，再进行写入操作。所以无论是使用`FileOutputStream(String name, boolean append)`构造方法还是使用`FileOutputStream(String name)`构造方法并设置`append`参数为`false`，都会清空文件内容并写入新的数据。

##### 3.使用文件的方式创建输入流对象有无append形参的区分

File file是文件的方式创建文件，String name是通过路径创建文件，所以可以同理可知有无append形参的区别。