# java中的IO流

#### 一、初始IO流

1.输入输出是任何程序设计语言都提供的功能，java语言从一开始就支持IO，最初是 通过java.io.*包中的类和接口提供的。

2.IO流中的  I：input；O ：output ；流：stream

3.IO流的分类

第一种方式：以内存或者程序作为参考：将磁盘（硬盘）上的文件读入（输入）内存（程序）中的流就叫输入流，或者叫read；从内存或者程序中出来的就叫输出流，或者叫write。

第二种方式：按照数据的类型分，数据流又可以分为二进制流和文本流，其中二进制流也被称为字节流,一次读入一个字节，也就是8个比特位（一次读入8个二进制），这种流是万能的什么流都可以读取，包括文本文件、图像、音频和视频文件等等......。文本流也被称为字符流,这种流一次读取一个字符，这种流是针对文本文件存在的，不能读取图片、音频和视频等文件只能读取纯文本文件，文件扩展名为.txt，连word文件也不能读取。它们处理信息的基本单位分别是字节和字符。

假设文件file1.txt 中有 a中国bc

采用字节流的方式去读：

第一次读：读一个字节，正好读到'a'

第二次读：读一个字节，正好读到'中'的一半

第三次读：读一个字节，正好读到'中'的另一半

采用字符流的方式去读：

第一次读：读一个字符'a'字符（'a'字符在windows系统中占用一个字节）

第二次读：'中'字读（'中'字符在windows系统中占两个字节）

**注意：**

*在Windows系统中，一个字母通常占用1个字节，使用ASCII编码表示，包括英文字母和一些常见的符号。而一个汉字在Windows系统中通常占用2个字节，使用UTF-16编码表示。UTF-16编码使用16位表示字符，对于基本的拉丁字符（如英文字母）和常见的汉字，每个字符通常占用2个字节。*

*Java 使用 Unicode 字符集来表示字符，而 Unicode 采用了变长编码方案，其中基本的拉丁字符和常见的汉字等字符通常使用 2 个字节（16位）表示。因此，在 Java 中，无论是一个字母还是一个汉字，字符类型 `char` 都占用 2 个字节。*

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230617094925796.png" alt="image-20230617094925796" style="zoom:25%;" />

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230617094959381.png" alt="image-20230617094959381" style="zoom: 25%;" />

#### 二、java中需要重点掌握的java.io.*包中的流

有十六个：

###### 文件专属：(可以观察出文件专属的输入输出流的类名都有File)

java.io.FileInputStream    （字节流/输入流）

java.io.FileOutputStream  （字节流/输出流）

java.io.FileReader     （字符流/输入流）

java.io.FileWriter   （字符流/输出流）

###### 转换流（将字节转换成字符流）

java.io.InputStreamReader   (以reader为后缀属于字符流/输入流)

java.io.OutputStreamWriter   (以writer为后缀属于字符流/输出流)

###### 缓冲流专属：  (buffered 翻译为 adj.缓冲的，v.缓冲 ，buffer的过去分词 )

java.io.BufferedReader  字符流/输入流

java.io.BufferedWriter    字符流/输出流

java.io.BufferedInputStream   字节流/输入流

java.io.BufferedOutputStream  字节流/输出流

###### 数据流专属：

java.io.DateInputStream    （字节流/输入流）

java.io.DateOutputStream  （字节流/输出流)

###### 标准输出流：

java.io.PrintWriter  (字符流)

java.io.PrintStream  （字节流）

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230618210945248.png" alt="image-20230618210945248" style="zoom: 50%;" />

三、输入输出流分别实现什么接口？有什么特点？

1、在 Java 的 `java.io` 包中，几乎所有的输入和输出流都实现了 `Closeable` 接口或其子接口 `AutoCloseable`。这意味着这些流都具有关闭功能，并且可以使用 `close` 方法来显式关闭流。

在使用流时，特别是对于涉及到底层资源（如文件、网络连接等）的流，最好在使用完毕后显式地调用 `close` 方法来关闭流，以确保资源的正确释放和回收。通常会使用 `try-with-resources` 语句块来自动关闭流，该语句块会在代码执行完毕或发生异常时自动关闭流，无需手动调用 `close` 方法。

需要注意的是，并非所有的流都是可关闭的。一些特殊的流，如 `ByteArrayInputStream`、`ByteArrayOutputStream` 等内存流，不会占用底层资源，因此不需要显式地关闭。此外，一些流实现类可能会在其内部自动关闭底层资源，无需用户手动操作。

2、关闭流的原因

1. 资源回收：许多流操作会涉及底层资源，如文件、网络连接、数据库连接等。关闭流可以确保这些资源在使用完毕后被及时释放，避免资源泄漏和浪费。

2. 数据完整性：某些流操作可能需要将数据缓冲或刷新到目标位置，例如将数据写入文件或发送到网络。在关闭流之前，通过调用相应的刷新方法，可以确保数据被正确写入或发送，避免数据丢失或不完整。

3. 避免文件锁定：在某些情况下，如果流没有被关闭，底层资源（如文件）可能会保持锁定状态，这可能导致其他进程无法访问或修改该资源。通过关闭流，可以释放对资源的锁定，使其它进程能够正常操作相关文件或资源。

4. 提高性能：打开的流可能占用系统资源，如果不关闭它们，会导致资源的浪费和系统负担。通过及时关闭流，可以释放这些资源，提高系统性能和效率。

   ​      关闭流是一种良好的编程习惯，可以保证资源的正确释放和回收，确保数据的完整性，避免文件锁定问题，并提高系统性能。尽量在不需要使用流时及时关闭，可以使用`try-with-resources`语句块自动关闭流，或者在适当的地方显式调用流的`close`方法来关闭流。

四、文件字节输入流的使用FileInputStream

```java
package june.selfStudy.IO;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
/*
java 中的流的四大家族：
java.io.InputStream;字节输入流
java.io.OutputStream;字节输出流
java.io.Writer;字符输出流
java.io.Reader;字节输入流

注意：java中的大部分接触底层资源的输入或者输出流在使用完之后都必须要关闭，而关闭的方式可以手动调用实现Closeable接口中的close方法来手动关闭
流。或者使用实现Closeable子接口AutoCloseable接口中的try-with-resources语句块来显式的关闭流资源
java中的输出流在使用完之后都必须使用从flushable接口中实现的flush方法来实现对流的刷新，所有的流都实现了java.io.Flushable接口，这意味着所有的
输出流都是可以刷新的，都有flush方法，养成一个好习惯，输出流在最终输出之后，一定要记得flush方法刷新一下，这个刷新表示将通道或者管道中的剩余的
未输出的数据强行输出成功，也就是清空管道，刷新的作用的作用就是清空管道，如果没有使用flush方法去清空输出流管道，就会导致数据丢失。

 注意：在java中但凡是以Stream结尾的都是字节流，以reader和writer结尾的都是字符流。
 java中必须掌握的流有16个：
 文件专属流：
 java.io.FileInputStream
 java.io.FileOutputStream
 java.io.FileWriter
 java.io.FileReader
 缓冲流专属：
 java.io.BufferedInputStream
 java.io.BufferedOutputStream
 java.io.BufferedReader
 java.io.BufferedWriter
 转换流：字节流转换为字符流
 java.io.InputStreamReader
 java.io.OutputStreamWriter
 数据流专属：
 java.io.DataInputStream
 java.io.DataOutputStream
 对象专属流：
 java.io.ObjectInputStream
 java.io.ObjectOutputStream
 标准输出流：默认往控制台输出，其中有特定的方法可以完成对输出方向的改变
 java.io.PrintWriter标准字符输出流
 java.io.PrintStream标准字节输出流
 */

/**
 * 文件专属输入流和文件专属输出流的使用
 * java.io.FileInputStream
 * java.io.FileOutputStream
 * java.io.FileWriter
 * java.io.FileReader
 * 输入流中有读文件的方法，输出流当中有写文件的方法，字符流是一次读取或者写入一个字符，字节流是一次读取或者写入一个字节
 * 在windows系统中英文字母采用的是ASCII编码，一个英文要一个字节，而一个汉字使用UTF-6编码要两个字节。
 * 而使用字符的话，那么不论是一个英文字母还是一个汉字都是一个字符，使用字符流/文本流，就是一次读取一个字符即可
 */
public class FileInputStreamTest03 {
    public static void main(String[] args){
        //先声明一个文件专属的字符输入流，输入是Input或者reader，表示将磁盘上的文件读取到内存中，或者程序中
        FileInputStream fis = null;//此处声明的是一个文件输入字节流，如果读取汉字：例如'中'，那么读一次就只能把这个汉字读一半，而‘a’这个
        //字母可以一次读完，因为在windows系统中英文字母占一个字节
        //创建文件输入流对象
        try {
            fis = new FileInputStream("tempfile01");
            //在这里可以使用度文件袋呃方法，然后可以输出到控制台上，可以先使用read()无参数的读的方法，一次读取一个字节
           int readValue = fis.read();//返回的就是读取的int型的值，例如文件中的a，读取出来就是97，但是这个方法会抛出一个IOException
            System.out.println(readValue);//空格读出来是32
             readValue = fis.read();
            System.out.println(readValue);//p读出来是112
            /*
            现在使用有参数的read(byte[] bytes)方法来一次读取指定长度的字节，但是这种方式不建议读太大的数据量，因为是读到byte数组中
            ，而byte数组不能储存非常大的数据量
            要使用这种往byte数组当中的read方法，就必须提前准备一个byte数组，准备好byte数组之后，就可以调用read（byte[] bytes）方法，把byte数组
            传进去，然后要想把读到byte数组中的内容打印到控制台上，就必须调用String类中的一个构造方法，这个构造方法是将一个byte数组传到
            有参构造方法当中，然后转换成一个字符串对象，也就是相当于返回一个字符串。
            当然，你可以搭配着循环语句一起使用。
             */
            int readValue1  = 0;
            byte[] bytes = new byte[4];//这表示调用有参read方法的时候，一次读取四个字节到byte数组当中
            //read方法都是当读到文件末尾的时候，无法继续读下去的时候就会返回-1，那么-1就可以作为我们循环语句当中的一个判断条件
            while((readValue1 = fis.read(bytes))!=-1){
                System.out.print(new String(bytes));//由于当中有中文，所以有的时候会一个汉字两个字节读不完，感觉如果是汉字的话，
                //还是使用字符输出流可能会好点
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        }catch(IOException e){//在这里继续捕捉即可，因为一个try可以搭配多个catch语句
            e.printStackTrace();
        }finally{
            //在这里需要关闭使用完的流！！
            if(fis!=null){//这里提前判断是否为空，是为了防止出现空指针异常，如果引用是空的那么就没有必要再调用关闭流的方法了
                try {
                    fis.close();//这里会报错IOException，继续在finally语句中使用try-catch语句
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
    }
}

```

输出结果

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230628105029947.png" alt="image-20230628105029947" style="zoom:50%;" />

文件tempfile01，是保存在当前工程下的，所有在创建输入流对象的时候，采用有参构造方法传入一个String类型的文件路径的时候，就直接写的"tempfile01"，因为IDEA当中的当前路径就是跟项目相同等级的路径，而绝对路径就要填写完整的路径。

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230628110551389.png" alt="image-20230628110551389" style="zoom: 50%;" />



五、文件专属字节输出流的使用FileOutputStream

```java
package june.selfStudy.IO;

import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

/**
 * 在这里将对java中文件专属字节输出流进行测试FileOutputStream
 * 输出指的是从程序将内容输出到磁盘中，输入输出都是针对的内存/程序
 */
public class FileOutputStreamTest01 {
    public static void main(String[] args){
        //先声明一个文件字节输出流的变量
        FileOutputStream fos = null;
        try {
            //创建一个输出流对象，这个构造方法会抛出一个FileNotFoundException编译时异常，所以我们需要对编译时的异常进行处理
            fos = new FileOutputStream("tempfile02");//这里会在当前的工程下生成一个tempfile02.txt的文件
            //接下来就可以开始写文件了
            byte[] bytes = "我们现在在学习Java中的IO流！".getBytes();
            fos.write(bytes,0,bytes.length);
            //养成一个好习惯，输出流使用完之后，要手动的刷新管道，防止资源浪费和泄露
            if(fos!=null) {
                fos.flush();//这个方法也会抛出来一个异常
            }
        } catch (FileNotFoundException e) {
           e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }finally{
            //养成一个好习惯，流使用完毕之后要关闭，无论是手动关或者自动关闭
            if(fos!=null){
                try {
                    fos.close();//这个方法也会报错，所以要对编译时的异常进行处理
                } catch (IOException e) {
                    throw new RuntimeException(e);
                }
            }
        }
    }
}

```

运行之后，就会在IDEA的当前工程的目录下生成一个txt文件，然后这个文件tempfile01中有你写进去的内容。

<img src="C:\Users\14214\AppData\Roaming\Typora\typora-user-images\image-20230628112938137.png" alt="image-20230628112938137" style="zoom:67%;" />

