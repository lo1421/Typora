#### java中FileOutputStream字节输出流的学习

###### 第一步：完成FileOutputStream字节输出流的创建

###### 第二步:调用FileOutputStream字节输出流中的方法，完成写入的操作

FileOutputStream流中有哪些方法？

void close();	关闭此输入流并释放与流有关的任何系统资源

void flush();	刷新输出流，使缓存数据被写入到流

void write(byte[] b);	写b.length字节输出流

void write(byte[] b,int off,int len);	将len字节从指定的byte数组起始偏移off到输出流

void write(int b);	将指定的byte到输出流	

其中所有的方法都会抛给调用者IOException编译是异常，调用者在调用的时候记得对编译时的异常进行处理，可以选择throws关键字上抛，也可以选择try-catch语句进行捕捉。

```java
package june.selfStudy.IO;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

/**
 * FileOutputStream是字节输出流，目的是将程序中的内容往磁盘上输出
 * 输出流在使用完之后，必须清空管道即调用实现的flushable接口中的flush方法来实现对管道的强行刷新。
 */
public class FileOutputStreamTest02 {
    public static void main(String[] args){
        FileOutputStream  fos  = null;
        try {
            //创建输出流对象，调用FileOutputStream当中的构造方法
            fos = new FileOutputStream("tempfile04",true);
            //查看API文档，看FileOutputStream输出流中都有什么写入的方法
            byte[] bytes = {97,98,99,100,101,102};
            //将指定数组的长度进行写入
            //第一次写入
            fos.write(bytes,0,2);//ab
            //第二次写入
            fos.write("我在学习".getBytes());//abab我在学习
            //输出流使用完之后必须强行将流管道刷新
            fos.flush();
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally{
            //关闭流资源
            //关闭流之前先判断流是否为空，如果流对象的引用为空，那么也就没有必要关闭了
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

###### 第四步：输出流使用完之后一定要养成刷新的习惯

调用flush方法强行对管道进行刷新

###### 第五步：当流使用完之后在finally语句中完成流的关闭