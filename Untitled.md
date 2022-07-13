/**
 * 从内存中写出数据到硬盘的文件里
 * 
 * 说明：
 * 1.输出操作，对应的file可以不存在的。并不会报异常
 * 			如果不存在：在输出的过程中，会自动的创建此文件
 * 			如果存在：
 * 					如果流使用的构造器是FileWrietr(file,false)/FileWriter(file):对原有文件的覆盖
 * 					如果流使用的构造器是FileWriter(file,true)：不会对原有文件覆盖，而是在原有文件上追加内容
 * @author 水星记
 *
    */

/**
 * 处理流之一：缓冲流的使用
 * 
 * 1.缓冲流：
 *处理字节
 * BufferedInputStream	read(byte [] buffer)
 * BufferedOutputStream		write(byte [] buffer,0,len)
 * 处理字符
 * BUfferedReader（read(char[]cbuf)
 * BUfferedWriter(write char [] cbuf,0,len)
 * 
 * 2.作用：提供流的读取，写入的速度
 * 		提高读写速度的原因：内部提供了一个缓冲区
 * 
 * 3.处理流：就是“套接”在已有流的基础上
 * 
 * @author 水星记
 *
    */





其他流的使用：

1.标准的输入，输出流

2.打印流

3.数据流



1.标准的输入,输出流

1.1

System.in :标准的输入流，默认从键盘输入

System.out : 标准的输出流，默认从控制台输出

1.2

System类的setIn(InputStream  is) / setOut(PrintStream  ps)方式重新指定输入和输出的流