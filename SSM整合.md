# 							SSM整合

## 数据库

### 创建数据库

```mysql
create database ssmbuild

```

### 使用数据库

```mysql
use ssmbuild
```

### 创建表

```mysql
create table books(
	bookID int(10) not null  auto_increment comment '书id',
	bookName varchar(100) not null comment '书名',
	bookCounts int(11) not null comment '数量',
	detail  VARCHAR(200) not null comment '描述',
	key `bookID` (`bookID`)
)	engine = innodb default charset= utf8
```

### 插入数据

```mysql

insert into books(bookID,bookName,bookCounts,detail) values
(1,'Java',1,'从入门到放弃'),
(2,'MySQL',10,'从删库到跑路'),
(3,'Linux',5,'从进门到进牢');
```



## 创建Maven工程

### 导入依赖

```xml
<!--  依赖：junit,数据库驱动，连接池，servlet,Jsp,mybatis,mybatis-spring,spring  -->

    <dependencies>
        <!--Junit-->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>

        <!--数据库驱动-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.18</version>
        </dependency>

        <!--数据库连接池-->
        <dependency>
            <groupId>com.mchange</groupId>
            <artifactId>c3p0</artifactId>
            <version>0.9.5.2</version>
        </dependency>

        <!--Servlet Jsp-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>servlet-api</artifactId>
            <version>2.5</version>
        </dependency>
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>jsp-api</artifactId>
            <version>2.2</version>
        </dependency>
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
            <version>1.2</version>
        </dependency>

        <!--Mybatis-->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.2</version>
        </dependency>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
            <version>2.0.2</version>
        </dependency>

        <!--spring-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
            <version>5.2.1.RELEASE</version>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
            <version>5.2.1.RELEASE</version>
        </dependency>
    </dependencies>
```



### 静态资源导出问题

```xml
<!--静态资源导出问题-->
    <build>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.properties</include>
                    <include>**/*.xml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
        </resources>
    </build>
```



## Mybatis层

pojo包下创建对应数据库实体类

dao层和service层对应model层，

连接数据库配置

```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis_plus?
serverTimezone=GMT%2B8
spring.datasource.username=root
spring.datasource.password=abc123
```

配置mybatis-config.xml

![1657510055094](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657510055094.png)

在dao层创建Mapper接口，定义基础方法逻辑

![1657510094714](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657510094714.png)

使用注解方式实现基本操作

![1657510126127](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657510126127.png)



在service层定义接口，

![1657510178922](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657510178922.png)

定义实现类

service层调dao层

![1657510203743](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657510203743.png)