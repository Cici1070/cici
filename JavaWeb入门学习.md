#  JavaWeb入门学习

## javaWeb技术栈

![1656469419377](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656469419377.png)

## 数据库相关概念

### 数据库

存储数据得仓库，数据是有组织得进行存储

英文：DataBase	简称：DB

### 数据库管理系统

管理数据库的大型软件

英文：DataBase Management System.	简称DBMS

### SQL

结构化查询语言

操作关系型数据库的编程语言

定义操作所有关系型数据库的统一标准

### MySQL数据模型

#### 关系型数据库

​	关系型数据库都是建立在关系模型基础上的数据库，简单说，关系型数据库就是建立在多张能互相连接的二维表组成的数据库

##### 优点

​		1.都是使用表结构，格式一致，易于维护

​		2.使用通用的SQL语言操作，使用方便，可用于复杂查询

​		3.数据存储在磁盘中，安全

![1656470125722](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656470125722.png)

#### SQL简介

![1656470525880](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656470525880.png)

#### SQL通用语法

1.SQL语句可以多行或单行书写，以分号结尾

2.MySQL数据库的SQL语句不区分大小写，推荐关键字使用大写

3.注释

​				单行注释  --注释内容	或 #注释内容（MySQL特有）

​				多行注释  /* 注释 */

#### SQL分类

![1656470899046](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656470899046.png)

DDL:操作数据库，表等

DML:对表中数据进行增删改

DQL:对表中数据进行查询

DCL:对数据库进行权限控制



### DDL--操作数据库

#### 1.查询

show databases;

#### 2.创建

create database db1;

create database if not exits db1;

#### 3.删除

drop database db1;

drop database if exits db1;

#### 4.使用

use db1;

#### 5查询正在使用的数据库

select database();



### DDL--操作表

#### 查询表

##### 查询当前数据库下所有表的名称

show tables;

##### 查询表结构

desc 表名称；

#### 创建表

create table 表名称（

​		字段名1  数据类型1,

​		字段名2  数据类型2,

​		...

​		字段名n 数据类型n

）;

**注意：最后一个字段末尾，不能加逗号**

#### 数据类型

MySQL支持多种数据类型，可以分为三类

​			数值

​			日期

​			字符串

![1656472581168](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656472581168.png)

##### 创建案例

![1656472628564](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656472628564.png)

```sql
create table student(
	id int,
	name varchar(10),
	gender char(1),
	birthday date,
	score double(5,2),
	email varchar(64),
	phone varchar(20),
	status tinyint
);
```

#### 删除表

drop table 表名；

drop table if exits 表名；

#### 修改表

##### 1.修改表名

alter table 表名 rename to 新的表名；

##### 2.添加一列

alter table 表名 add 列名 列数据类型；

##### 3.修改数据类型

alter table 表名 modify 列名 新数据类型；

##### 4 修改列名和数据类型

alter table 表名 change 列名 新列名 新数据类型； 

##### 5.删除列

alter table 表名 drop 列名；

### DML

#### 添加数据

##### 1.给指定列添加数据

insert into 表名（列名1，列名2...) values(值1，值2...);

##### 2.给全部列添加数据

insert into 表名 values(值1，值2，...);

##### 3.批量添加数据

insert into 表名(列名1，列名2，...) values(值1，值2，...),(值1，值2，...),(值1，值2，...);

insert into 表名	values (值1，值2，...)，(值1，值2，...)，(值1，值2，...);

#### 修改数据

update 表名 set 列名1=值1，列名2=值2，...[where 条件];

--将张三的性别修改为女

update student set gender = '女' where name = '张三'; 

#### 删除数据

delete from 表名 [where 条件];

### DQL

#### 查询语法

selete

​			字段列表

from

​			表名列表

where

​			条件列表

group   by

​			分组字段

having

​			分组后条件

order    by

​			排序字段

limit

​			分页限定

#### 基础查询

##### 1.查询多个字段

selete	字段列表	from	表名；

selete  *	from	表名；

##### 2.去除重复记录

selete  distinct  字段列表	from	 表名；

##### 3.起别名

AS:AS也可以省略

#### 条件查询

##### 1.条件查询语法

selete 字段列表 from 表名 where 条件列表；

##### 2.条件

![1656481580452](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656481580452.png)

![](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656482183364.png)

![1656482202165](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656482202165.png)

![1656482214982](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656482214982.png)

模糊查询 like

![1656482317013](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656482317013.png)

![1656482385293](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656482385293.png)



#### 排序查询

#### 1.排序查询语法

selete 字段列表 from 表名 order by 排序字段名1 [排序方式1]，排序字段名2 [排序方式2]

##### 排序方式

ASC	升序排列（默认）

DESC	降序排列

**注意：如果有多个排序条件，当前边排序条件值一样时，才会根据第二条件排序**

### 聚合函数

#### 1.概念

将一列数据作为一个整体，进行纵向计算

#### 2.聚合函数分类

![1656482913896](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656482913896.png)

#### 3.聚合函数语法：

select 聚合函数名(列名) from 表名；

**注意：null值不参与所有聚合函数运算**

### 分组查询

#### 1.分组查询语法

selete 字段名 from 表名 [where 分组前条件限定] group by分组字段名 [having 分组后条件限定]；

**注意：分组之后，查询的字段为聚合函数和分组字段，其他字段无意义**

![1656483425868](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656483425868.png)

![1656483541234](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656483541234.png)

##### where和having的区别

执行时机不同：where是分组前进行限定，不满足where条件，则不参与分组，having是分组之后对结果进行过滤

可判断的条件不同：where不能对聚合函数进行判断，having可以

##### 执行顺序

where > 聚合函数 >having

### 分页查询

#### 1.分页查询语法

selete 字段列表 from 表名 Limit 起始索引 ，查询条目数；

起始索引：从0开始

![1656483976923](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656483976923.png)

 --起始索引 = （当前页码 - 1） * 每页显示条目数

![1656484104274](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656484104274.png)

## 约束

### 约束的概念和分类

#### 1约束的概念

​	约束是作用于表中列上的规则，用于限制加入表的数据

​	约束的存在保证了数据库中数据的正确性，有效性和完整性

#### 2.约束的分类

![1656485629936](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656485629936.png)

**注意：MySQL不支持检查约束**

##### 例如

```sql
--员工表
CREATE TABLE emp(
	id INT PRIMARY KEY ,-- 员工id,主键且自增长
	ename VARCHAR(50) NOT NULL UNIQUE,-- 员工姓名，非空且唯一
    joindate DATE NOT NULL， -- 入职日期，非空
    salary double(7,2) NOT NULL, -- 工资,非空
    bonus double(7,2) DEFAULT 0 -- 奖金，如果没有默认为0
);
```

##### 主键约束：

非空且唯一

##### 自动增长

auto_increment: 当列是数字类型并且  唯一约束

##### 非空约束

###### 1.概念

​			非空约束用于保证所有数据中不能有Null值

###### 2.语法

​			（1）添加约束

​				创建表时添加约束

​				create table 表名（

​						列名 数据类型  NOT　NULL，

​						．．．

​					）；

​				－－建完表后添加约束

​			　　ALTER  TABLE 表名　MODIFY 字段名 数据类型  NOT NULL；

​				（2）删除约束

​				  ALTER TABLE 表名 MODIFY   字段名  字段类型；

##### 外键约束

###### 	1.概念

​		外键用来让两个表的数据之间建立连接，保证数据的一致性和完整性

 ![1656487683521](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656487683521.png)

###### 2.语法

添加外键

```
--创建表时添加外键
	CREATE TABLE 表名(
		列名 数据类型，
		...
		[CONSTRAINT] [外键名称] FOREIGN KEY(外键列名) REFERENCES 主表(主表列名)
	);
```

![1656488196518](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656488196518.png)

建完表后添加外键

```
--建完表后添加外键
ALTER TABLE 表名 ADD CONSTRAINT 外键名称 FOREIGN KEY (外键字段名称) REFERENCES主表名称(主表列名称)
```

![1656488267108](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656488267108.png)

删除外键

```
ALTER TABLE 表名 DROP FOREIGN KEY 外键名称
```

![1656488115455](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656488115455.png)

### 数据库设计

#### 1.软件研发步骤

![1656489224584](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656489224584.png)

#### 2.数据库设计概念

.数据库设计就是根据业务系统的具体需求，结合我们所选用的DBMS,为这个业务系统构造出最优的数据存储模型

.建立数据库中的表结构以及表与表之间的关联关系的过程

.有哪些表？表里有哪些字段？表与表之间有什么关系？

#### 3.数据库设计实施的步骤

##### 	1.需求分析

​		数据是什么？数据有哪些属性？数据与属性之间的特点是什么？

##### 	2.逻辑分析

​		通过ER图对数据库进行逻辑建模，不需要考虑我们所选用的数据库操作系统

![1656489811117](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656489811117.png)

##### 	3.物理设计

​		根据数据库自身的特点把逻辑设计转换为物理设计

##### 	4.维护设计

###### 		1对新的需求进行建表

###### 		2表优化

#### 表关系

.一对一

如：人和身份证

一对多（多对一）

如：部门和员工

多对多

如：商品和订单



##### 表关系之一对多

一对多（多对一）

如：部门和员工

一个部门对应多个员工，多个员工对应一个部门



###### 实现方式：在多的一方建立外键，指向一的一方的主键

![1656490282563](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656490282563.png)

##### 表关系之多对多

多对多

如：商品和订单

一个商品对应多个订单，一个订单包含多个商品



###### 实现方式：建立第三张中间表，中间表至少包含两个外键，分别对应两个表的主键



![1656490492254](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656490492254.png)

###### 创建表

![1656490544306](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656490544306.png)

###### 创建中间表并添加外键

![1656490566629](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656490566629.png)

##### 表关系之一对一

.一对一

如：用户和用户详情

一对一关系多用于表的拆分，将一个实体中经常使用的字段放一张表，不经常使用的字段放另一张表，以此来提升查询的性能

###### 实现方式

在任意一方设置外键，关联另一方的主键，并且设置外键唯一(UNIQUE)

###### 拆分前

![1656490786582](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656490786582.png)

###### 拆分后

![1656490826240](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656490826240.png)

![1656492726371](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656492726371.png) 

#### 多表查询

select * from 表1，表2；

##### 笛卡尔积

有A，B两个集合，取A,B的所有组合情况

select * from 表1，表2；

![1656493384190](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656493384190.png)

##### 连接查询

###### 内连接

相当于查询A,B交集数据 

```sql
--隐式内连接	
	selete 字段列表 from 表1，表2... where条件；
	
	查询emp和dept的数据，emp.dep_id = dept.did
	select * from emp,dept where emp.dep_id = dept.did;
	
--显示内连接
	select 字段列表 from 表1 [INNER] join 表2 ON 条件；
	
	select * from emp inner join dept on emp.dep_id = dept.did;
```



###### 外连接

​	左外连接：查询A表所有数据和交集部分数据

```
select * from emp left join dept on emp.dep_id = dept.did;
```

​	右外连接：查询B表所有数据和交集部分数据

```
select * from deptleft join emp on emp.dep_id = dept.did;
```



##### 子查询

![1656496388939](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656496388939.png)

![1656496466334](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656496466334.png)

![1656506893859](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656506893859.png)

多行多列

![1656507086277](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656507086277.png)



##### 多表查询案例



![1656679700323](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656679700323.png)

 ![1656680482677](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656680482677.png)





### 事物

#### 事物简介

数据库的事物是一种机制，一个操作序列，包含了一组数据库操作命令

事物把所有的命令作为一个整体一起向系统提交或撤销操作请求，即这一组数据库命令要么同时成功，要么同时失败

事物是一个不可分割的工作逻辑单元



#### 事物操作简介

开启事物

START   TRANSACTION	或者BEGIN

提交事务

COMMIT

回滚

ROLLBACK



#### 事物四大特征

原子性(A)：事物是不可分割的最小操作单位，要么同时成功，要么同时失败

一致性(C):    事物完成时，必须使所有的数据都保持一致状态

隔离性(I):    多个事物之间，操作的可见性

持久性(D):	事物一旦提交或者回滚，他对数据库中的数据的改变就是永久的



查询事物默认提交方式

select   @@autocommit

修改事物默认提交方式为手动

set     @@autocommit = 0



## JDBC

### JDBC概念：

JDBC就是用java语言操作数据库的一套 API

### JDBC本质：

官方（sun公司）定义的一套操作所有关系型数据库的规则，即接口

各个数据库厂商去实现这套接口，提供数据库驱动jar包

我们可以使用这套接口编程，真正执行的代码是驱动jar包中的实现类

### JDBC好处：

各数据库厂商使用相同的接口，Java代码不需要针对不同数据库进行开发

可随时替换底层数据库，访问数据库的Java代码基本不变

### JDBC过程

![1656818796905](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656818796905.png)

JDBC	API详解

#### DriverManager

DriverManager（驱动管理类）作用：

​	1.注册驱动

​	2.获取数据库连接

![1656831920779](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656831920779.png)

#### Connection

Connection（数据库连接对象)作用：

​	1.获取执行Sql的对象

![1656832165412](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656832165412.png)

​	2.管理事物 

![1656832196180](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656832196180.png)

####  Statement

![1656853822568](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656853822568.png)

#### ResultSet

![1656856358575](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656856358575.png)

#### PreparedStatement

![1656921358457](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656921358457.png)





### 数据库连接池

#### 数据库连接池简介

​		数据库连接池是个容器，负责分配，管理数据库连接

​		它允许应用程序重复使用一个现有的数据库连接，而不是重新在建一个

​		释放空闲时间超过最大空闲时间的数据库连接来避免因为没有释放数据库连接而引起的数据库连接纰漏

好处

​		资源重用

​		提升系统响应速度

​		避免数据库连接纰漏

![1656923434349](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656923434349.png)



## Maven

Maven是专门用于管理和构建Java项目的工具，他的主要功能有：

​		提供了一套标准化的项目结构

​		提供了一套标准化的构建流程（编译，测试，打包，发布。。。）

​		提供了一套依赖管理机制

![1656924919374](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656924919374.png)

### 依赖管理

![1656927801025](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656927801025.png)

![1656928067702](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656928067702.png)



## MyBatis

### 什么是MyBatis？

​	MyBatis是一款优秀的持久层框架，用于简化JDBC开发

​	MyBatis本是Apache的一个开源项目IBatis



### 持久层

​	负责将数据保存到数据库的那一层代码

​	JavaEE三层架构：表现层，业务层，持久层

### 框架

框架就是一个半成品的软件，是一套可重用的，通用的，软件基础代码模型

在框架的基础上构建软件编写更加高效，规范，通用，可扩展

![1656932208547](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656932208547.png)

![1656936531585](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656936531585.png)

 

![1656938203267](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656938203267.png)

### 使用Mybatis完成增删改查

![1656986679882](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656986679882.png)

![1656999792790](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1656999792790.png)

#### 参数占位符

1、#{}：会将其替换为？  为了防止SQL注入

2. ${}:拼sql,会存在sql注入问题

3. 3.使用时机：

   1. 参数传递的时候：#{}
   2. 表名或者列名不固定的情况下，${}会存在SQL注入问题

   参数类型：parameterType:可以省略

   特殊字符处理：

   ​	1.转义字符

   ​	2.CDATA区



动态条件查询

​			if：条件判断

​				test:逻辑表达式

​			问题：

​				恒等式

​				<where> 替换where关键字

## HTML

HTML是一门语言，所有的网页都是用HTML这门语言编写出来的

HTML(HyperText Markup Language):超文本标记语言

​	超文本：超越了文本的限制，比普通文本更加强大。除了文字信息，还可以定义图片，音频，视频等内容

​	标记语言：由标签构成的语言

HTML运行在浏览器上，HTML标签由浏览器来解析

HTML标签都是预定义好的。例如：使用<img>展示图片

W3C标准：网页主要由三部分构成

​				结构：HTML

​				表现：CSS

​				行为：JavaScript

### HTML快速入门

![1657089449683](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657089449683.png)

### 		基础标签

 <h1>--<h6>  		定义标题，h1最大，h6最小
<font></font>		定义文本的字体，字体尺寸，字体颜色（过时的标签）
     <b></b>		定义粗体文本
     <i></i>		定义斜体文本
     <u></u>		定义文本下划线

     <center></center>	定义文本居中
     <p>

​         

     </p>			定义段落
     <br>			定义换行
     <hr>			定义水平线
### 图片,音频，视频标签

img:定义图片

​			src:规定显示图像的URL(统一资源定位符）

​			height:定义图像的高度

​			width:定义图像的宽度

audio:定义音频，支持的音频格式：MP3，WAV，OGG

​			src:规定的音频URL

​			controls:显示播放控件

video:定义视频，支持的音频格式：MP3，WebM，OGG

​    		src：规定视频的URL

​			controls:显示播放控件



### 资源路径

1.绝对路径：完整路径

2.相对路径：相对位置关系

​	当前目录下./xxx

​	上一级目录下../xxx/



### 超链接标签

<a>   		定义超链接，用于连接另一个资源

​	href:指定访问资源的URL

​	target:指定打开资源的方式

​				_self:默认值，在当前页面打开

​				_blank:在空页面打开



### 列表标签

有序列表（order list）  <ol>

1.xxx

2.xxx

3.xxx



无序列表（unorder list)   <ol>

xxx

xxx

xxx



<li>   定义列表项



### 表格标签

table :定义表格

​			border:规定表格边框的宽度

​			width:规定表格的宽度

​			cellspacing:规定单元格之间的空白

tr: 定义行

​			align:定义表格行的对齐方式

td:定义单元格

​			rowspan:规定单元格可横跨的行数

​			colspan:规定单元格课横跨的列数 



### 布局标签

div：			定义HTML文档中的一个区域部分，经常与CSS一起使用，用来布局网页

span：		用于组合行内元素



### 表单标签

from:定义表单

​			action：规定当提交表单时向何处发送表单数据，URL

​							表单项数据要想被提交，则必须指定其name属性 

​			method：规定当用于发送表单的数据方式

​							get: 浏览器会将数据直接附在表单的action URL之后。 大小有限制  4KB左右

​							post:浏览器会将数据放到http请求消息体中。大小无限制

表单标签--表单项

​		input 		表单项，通过type属性控制输入形式

​		select		定义下拉列表，<option>    定义列表项

​		textarea    文本域



type取值：

text:				默认值，定义单行的输入字段

password		定义密码字段

readio			定义单选按钮

checkbox		定义复选框

file					定义文件上传按钮

hidden			定义隐藏的输入字段

submit			定义提交按钮，提交按钮会把表单数据发送到服务器

reset				定义重置按钮，重置按钮会清除表单中的所有数据

button			定义可点击按钮

![1657095815495](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657095815495.png)

![1657095985721](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657095985721.png)

![1657096180895](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657096180895.png)

## CSS

CSS是一门语言，用于控制网页表现

CSS（Cascading  Style  Sheet）层叠样式表

### CSS导入方式

1、内联样式:在标签内部使用Style属性，属性值是css的键值对

2，内部样式：定义style标签，在标签内部定义css样式

3,	外部样式：定义link标签，引入外部的css文件 

![1657097311200](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657097311200.png)

### CSS选择器

概念：选择器是选取需设置样式的元素（标签）

![1657097901953](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657097901953.png)

1.元素选择器												

2.id选择器    以#开头   唯一

3.类选择器	以.开头    可同时选择多个

优先级排序：id选择器  >   类选择器  >   元素选择器

### CSS属性

参考文档手册使用



## JavaScript

JavaScript是一门跨平台，面向对象的脚本语言，来控制网页行为，它能使网页可交互

JavaScript和Java是完全不同的语言，不论是概念还是设计。但是基础语法类似



### JavaScript引入方式

1.内部脚本：将JS代码定义在HTML页面中

![1657098848848](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657098848848.png)

2.外部脚本：将JS代码定义在外部JS文件中，然后引入到HTML页面中

![1657099051766](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657099051766.png)

### JavaScript基础语法

#### 书写语法： 

1.区分大小写：与java一样，变量名，函数名以及其他一切东西都是区分大小写的

2.每行结尾的分号可有可无

3.注释：

​				单行注释：//		注释内容

​				多行注释：/* 注释内容 */

4.大括号表示代码块



#### 输出语句：

使用window.alert()	写入警告框

document.write():	写入HTML输出

console.log():	写入浏览器控制台



#### 变量：

JavaScript中用var关键字来声明变量

![1657100073622](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657100073622.png)

var test = 20;

#### 数据类型：

JavaScript中分为：原始类型和引用类型

5种原始类型：

​			number:数字（整数，小数，NaN（Not  a  Number））

​			string: 字符，字符串，单双引皆可

​			boolean:  布尔  true   false

​			null:对象为空

​			undefined：当声明的变量未初始化时，该变量的默认值是undefined

使用typeof运算符可以获取数据类型

​			alert(typeof  age);



#### 运算符：

​			==

​				1.判断类型是否一样，如果不一样，则进行类型转换

​				2.再去比较是否相等



​			===：全等于

​				1.判断类型是否相同，如果不同则直接返回false，若相同则比较是否相等



类型转换：

​				其他类型转为number

​						1.string:按照字符串的字面值，转为数字，如果字面值不是数字则转为NaN,一般使用parseInt

​						2.boolean:	true转为1，false转为0



​				其他类型转为boolean:

​						1.number:	0和NaN转为false,其他转为1

​						2.string:	空字符串转为false,其他字符串转为true

​						3.null:	false

​						4.undefined:	false



#### 函数

#### ![1657158235329](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657158235329.png)		

#### Array

![1657158935014](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657158935014.png)

####  String

![1657160575414](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657160575414.png)

#### 自定义对象

```js
var person = {    
    name:"zhangsan",    
    age:23,    
    eat: function(){    
        alert("干饭~");    
    }
};
alert(person.name);
person.eat();
```

#### BOM:

![1657162433298](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657162433298.png)

![1657162482565](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657162482565.png) 

![1657164524314](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657164524314.png)

![1657164550208](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657164550208.png)

#### DOM:

**![1657171884264](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657171884264.png)**



##### 获取Element

Element：元素对象

获取：使用Document对象的方法来获取

​	1.getElementById：根据id属性值获取，返回一个Element对象

​	2.getElementsByTagName:根据标签名称获取，返回Element对象数组

​	3.getElementsByName:根据name属性值获取，返回Element对象数组

​	4.getElementByClassName:根据class属性值获取，返回Element对象数组



style:设置元素css样式

innerHTML：设置元素内容

**使用**：**查阅文档**



#### 事件监听

事件：HTML事件是发生在HTML元素上的"事情"。比如：

​		按钮被点击

​		鼠标移动到元素之上

​		按下键盘按键

事件监听：JavaScript可以在事件被侦测到时执行代码 



###### 事件绑定：

事件绑定有两种方式：

方式一：通过HTML标签中的时间属性进行绑定

<input type = "button" onclick = 'on()'>



function on(){

​	alert("我被点了");

}

方式二：通过DOM元素属性绑定

<input type = "button " id="btn">

document.getElementById("btn").onclick = function(){

​	alert("我被点了");

}

![1657176780469](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657176780469.png)



## JavaWeb

web:全球局域网，也称为万维网，是可以直接通过浏览器访问到的网站

JavaWeb:是用Java技术来解决相关Web互联网领域的技术栈

### JavaWeb技术栈

B/S架构：Brower/Server，浏览器/服务器 架构模式，它的特点是，客户端只需要浏览器，应用程序的逻辑和数据都存储在服务器端。浏览器只需要请求服务器，获取Web资源，服务器把Web资源发送给浏览器即可。

​		好处：易于维护升级：服务器端升级后，客户端无需任何部署就可以使用到最新的版本

静态资源：HTML，CSS，JavaScript，图片等。负责页面展现

动态资源：JSP，Servlet等。负责逻辑处理

数据库：负责存储数据

HTTP协议：定义通信规则

Web服务器：负责解析HTTP协议，解析请求数据，并发送响应数据



### HTTP:

概念：超文本传输协议，规定了浏览器和服务器之间数据传输的规则

HTTP协议特点：

​	1.基于TCP协议，面向连接，安全

​	2.基于请求--响应模型：一次请求对应一次响应

​	3.HTTP协议是无状态的协议：对于事物处理没有记忆能力。每次请求-响应都是独立的

​				缺点：多次请求之间不能共享数据。Java中使用会话（Cookie,Session）来解决这个问题

​				优点：速度快



#### HTTP--请求数据格式

请求数据分为3个部分

​		1.请求行：请求数据的第一行。其中GET表示请求方式，/表示请求资源路径，HTTP/1.1表示协议版本

​		2.请求头：第二行开始，格式 为key : value形式

​		3.POST请求的最后一部分，存放请求参数

![1657199226702](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657199226702.png)

GET请求和POST请求的区别：

​	1.GET请求请求参数在请求行中，没有请求体。

​		POST请求请求参数在请求体中

​	2.GET请求请求参数大小有限制，POST没有

#### HTTP--响应数据格式

![1657199796978](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657199796978.png)

##### 响应状态码

![1657199892961](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657199892961.png)

![1657200167245](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657200167245.png)

#### Web服务区

Web服务器是一个应用程序（软件），对HTTP协议的操作进行封装，使得程序员不必直接对协议进行操作，让web开发更加便捷。主要功能是"提供网上信息浏览服务"。

#### Tomcat

![1657241617225](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657241617225.png)



Web服务器作用：

​			1.封装HTTP协议操作，简化开发

​			2.可以将web项目部署到服务器上，对外提供网上浏览服务

Tomcat是一个轻量级的Web服务器，支持Servlet/Jsp少量的JavaEE规范，也称为Web容器，Servlet容器



#### Tomcat --基本使用

![1657242001433](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657242001433.png)

IDEA中创建Maven Web项目

![1657244004675](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657244004675.png)

#### Servlet

![1657247628136](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657247628136.png)

快速入门

![1657248196181](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657248196181.png)

##### Servlet生命周期

![1657249345867](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657249345867.png)

###### 初始化方法：

![1657249720832](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657249720832.png)



###### 销毁方法：

![1657249688167](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657249688167.png)

##### Servlet方法：

![1657249864109](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657249864109.png)

##### Servlet体系结构

![1657250186596](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657250186596.png)

##### Servlet urlPattern配置

Servlet要想被访问，必须要配置其访问路径（urlPattern）

​	1.一个Servlet，可以配置多个urlPattern

​	@WebServlet(urlPattern = {"/demo1","/deno2"})

​	2.urlPattern配置规则

​		精确匹配

​		目录匹配

​		扩展名匹配

​		任意匹配

![1657259754417](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657259754417.png)

##### XML配置方式编写Servlet

![1657260101123](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657260101123.png)

#### Requse t&& Response

Request:获取请求数据

Response:设置响应对象



##### Requset继承体系

ServletRequset						Java提供的请求对象根接口

HttpServletRequest				Java提供的对Http协议封装请求对象接口

RequestFacade						Tomcat定义的实现类



1.Tomcat需要解析请求数据，封装为request对象，并且创建request对象传递到service方法中

2.使用request对象，查阅JavaEE API文档中的HttpServletRequest接口



##### Request获取请求数据

![1657262182056](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657262182056.png)

##### Request通用方式获取请求参数

请求参数获取方式

​			GET方式

​					String getQueryString()

​			POST方式

​					BufferedReader  getReader()

![1657264554889](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657264554889.png) 

![1657265347519](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657265347519.png)



Request请求参数中文乱码处理

请求参数中如果存在中文数据，则会乱码

​	解决方案：

​				POST:设置输入流的编码

​				req.setCharacterEncoding("UTF-8")





​				GET,获取参数的方式：getQueryString

​				乱码原因：tomcat进行URL解码，默认的字符集ISO-8859-1

​						先对乱码数据进行编码，转为字符数组		xxx.getBytes(StandardCharests.ISO-8859-1)

​						字节数组解码（转为字符串）

​						new String(bytes, StandardCharests.UTF-8)



**username = new String(username.getBytes(StandardCharests.ISO-8869-1),StandardCharests.UTF-8)**						



#### 请求转发

![1657269338174](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657269338174.png)



#### Response

Response设置响应数据功能介绍

​	响应数据分为3部分：

![1657272253145](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657272253145.png)

##### Response完成重定向

 ![1657272221161](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657272221161.png)



##### 路径问题

明确路径谁使用？

​			1.浏览器使用：需要加虚拟目录（项目访问路径）

​			2.服务端使用：不需要加虚拟目录

简化完成重定向以及动态获取虚拟目录

![1657272945437](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657272945437.png)



##### Response 响应字符数据



使用：

获取字符输出流

//设置响应格式以及编码格式

response.setContentType("text/html;charset=utf-8");

PrintWriter	writer  = response.getWriter();

writer.writer("aaa");

**注意：**

​	该流不需要关闭，随着响应结束，response对象销毁，由服务器关闭

​	中文数据乱码：原因通过Response获取的字符输出流默认编码：ISO-8859-1

​	response.setContentType("text/html;charset=utf-8");



##### Response 响应字节数据

![1657273866049](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657273866049.png)

还要导入坐标

![1657273964412](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657273964412.png)