关于java.long.Class类的理解

1.类的加载过程：

程序经过javac.exe命令以后，会生成一个或多个字节码文件（ .class结尾）。接着我们使用

java.exe命令对某个字节码文件进行解释运行。相当于将某个字节码文件加载到内存中。

此过程就称为类的加载。加载到内存中的类，我们就称为运行时类，此运行时类，就作为

Class的一个实例。

2.换句话说。Class的实例就对应着一个运行时类。

3.加载到内存中的运行时类，会缓存一定的时间。在此时间之内，我们可以通过不同的方式

来获取此运行时类。



/**
 * 了解类的加载器
 * @author 水星记
 *
  */
 public class ClassLoaderTest {
	public static void main(String[] args) {
		//对于自定义类，使用系统类加载器进行加载
		ClassLoader classLoader = ClassLoaderTest.class.getClassLoader();
		System.out.println(classLoader);
		//调用系统类加载的getParent():获取扩展类加载器
		ClassLoader classLoader1 = classLoader.getParent();
		System.out.println(classLoader1);
		//调用扩展类加载器的getParent():无法获取引导类加载器
		ClassLoader classLoader2 = classLoader1.getParent();
		System.out.println(classLoader2);
		
	
		ClassLoader classLoader3 = String.class.getClassLoader();
		System.out.println(classLoader3);
	
 }
 }



newInstance():调用此方法，创建对应的运行时类的对象。内部调用了运行时类的空参的构造器

要想此方法正常的创建运行时类的对象，要求：

1。运行时类必须提供空参的构造器

2.空参的构造器的访问权限得够。通常，设置为public。



在javabean中要求提供一个Public的空参构造器。原因：

1.便于通过反射，创建运行时类的对象

2.便于子类继承此运行时类时，默认调用super（）时，保证父类有此构造器
