Comparable接口的使用举例： 自然排序

1.像String  ，包装类等实现了Comparable接口，重写了conpareTo(obj)方法，给出了两个比较对象

2.像String  ，包装类等类重写conpareTo（）方法以后，进行了从小到大的排列

3.重写compare（obj）的规则：

​			如果当前对象this大于形参对象obj，则返回正整数，

​			如果当前对象this小于形参对象Obj,  则返回负整数，

​			如果当前对象this等于形参对象obj，则返回零



4.对于自定义类来说，如果需要排序，我们可以让自定义类实现comparable接口，重写conpareTo()方法

​	在compare(obj)方法中指明如何排序