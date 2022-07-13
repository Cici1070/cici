# 停掉正在运行的端口号

## 查看所有端口号

netstat ano



## 查看指定端口号谁否被占用

netstat -ano|findstr  8080

![1657609147800](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657609147800.png)



## 查看占用端口号的是哪些服务

//首先根据命令查出端口号的pid,然后在根据查询pid的命令查询出哪个服务

tasklist|findstr 12704

![1657609289843](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657609289843.png)



## 强制停止正在运行的端口号

taskkill -PID 12704 -F

![1657609363808](C:\Users\水星记\AppData\Roaming\Typora\typora-user-images\1657609363808.png)



### 也可以根据PID在任务管理器中找到对应的进程将其关掉

