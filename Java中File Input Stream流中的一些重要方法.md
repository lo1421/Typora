#### Java中File Input Stream流中的一些重要方法

```java
package june.selfStudy.IO;

import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

/**
 * FileInputStream类中的其它的常用的方法
 * int available（） 返回下一次对此输入流方法可以不受阻塞地从此输入流中读取或者跳过的估计剩余字节数/返回流当中剩余的字节数（剩余表示没有读到）
 * long skip（long n） 从输入流中跳过并丢弃n个字节的数据/跳过几个字节不读
 */
//available 可获得的，空闲的 adj
//skip 跳，跳跃 verb
public class FileInputStreamTest04 {
    public static void main(String[] args){
        //创建一个输入流的对象
        FileInputStream  fis = null;
        try {
            fis = new FileInputStream("tempfile03");
            //可以先试着读
            int readValue = fis.read();//97
            System.out.println(readValue);
            //现在就可以看看这个文件中还剩下几个可以读取的字节
            System.out.println("剩下的未读取的字节的个数："+fis.available());//5,这表示文件中还有五个字节没有读取
            /*
            那么FileInputStream这个类中的available方法有什么作用呢？
            1.可以在文件还没有被读取的时候获取文件的总的字节数量
            2.这样在使用参数为byte[]数据的read（byte[] bytes）方法的时候就可以提前计划好new一个指定长度的byte[]数组
            这样就不用使用循环再搭配byte[] 数组的方式了，或者也不用使用循环搭配read()方法直到返回一个-1的这种方式去循环地读取文件当中的字节
            例如 ：
           准备一个byte[]数组
           byte[] bytes = new byte[fis.available];
           当然这里了的fis希望是还没有被读取的文件，因为还没有被读取的文件调用available的方法的时候，返回的就是文件的大小也就是整个字节数目
           然后就可以调用String类中的传入一个byte数组的有参构造方法
           System.out.println（new String（bytes））;
          通过上述的方式就可以一次性读完文件中所有的字节，但是这种方式不是太使用于大文件，因为byte[]数组不能太大
             */
            /*
            skip()方法可以指定跳过几个字节然后再去读
            例如：
            fis.skip(3);//这里表示跳过3个字节，然后再去读这个文件，我们现在来看看又会是什么样的结果？
             int i = fis.read();
            System.out.println(i);
             */
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

```

