Java中定义类名：以字母开头，后面可以跟字母和数字的任意组合，但不能使用Java关键字



长整型数值有一个后缀L(100000000L),		十六进制有一个前缀ox(oxACDF)

八进制有一个前缀0（0102）



java7之后，加上前缀0b就可以写二进制数。例如：0b1001 就是9

也可以给数字后面加下划线，如用1_000_000(或0b1111_0100_0010_0100_0000)表示一百万

Java没有任何符号类型（unsigned）



float类型的数值有一个后缀F（3.14F）。没有后缀F的浮点数值，默认为double类型，也可加后缀D



利用关键字final指示常量，final表示这个变量只能被赋值一次，一旦赋值后便不能更改，常量习惯上使用大写  如：final double PAPER_SIZE = 3.24;

如果希望某个常量可以在一个类的多个方法使用，通常将这些常量成为类常量，使用关键字 			static final来设置一个类常量。    public static fianl double MAEF = 2.34;

类常量的定义位于main方法的外部，因此，在同一个类的其他方法中也可以使用这个常量

&&  逻辑”与“			|| 逻辑”或“

如果想对浮点数进行舍入操作，以便得到最接近的整数，常使用Math.round方法；

double x =9.878;

int x = (int) Math.round(x);//x=10

子串：

​		String greeting = "Hello";

​		String   s  = greet.substring(0,3);// s: "Hel"