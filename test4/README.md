# 实验4：对象管理

## 姓名：殷入风，学号：201810414425

## 实验目的：
了解Oracle表和视图的概念，学习使用SQL语句Create Table创建表，学习Select语句插入，修改，删除以及查询数据，学习使用SQL语句创建视图，学习部分存储过程和触发器的使用。
## - 实验场景：
假设有一个生产某个产品的单位，单位接受网上订单进行产品的销售。通过实验模拟这个单位的部分信息：员工表，部门表，订单表，订单详单表。

## 实验内容：
1.以system身份登录并创建new_yrf角色并授权：

![image](./img/sys登录创建角色并授权.png)

```下面是创建用户new_yrf
CREATE USER new_yrf IDENTIFIED BY 123
DEFAULT TABLESPACE "USERS"
TEMPORARY TABLESPACE "TEMP";

-- QUOTAS
ALTER USER new_yrf QUOTA UNLIMITED ON USERS;
ALTER USER new_yrf QUOTA UNLIMITED ON USERS02;
ALTER USER new_yrf ACCOUNT UNLOCK;

-- ROLES
GRANT "CONNECT" TO new_yrf WITH ADMIN OPTION;
GRANT "RESOURCE" TO new_yrf WITH ADMIN OPTION;
ALTER USER new_yrf DEFAULT ROLE "CONNECT","RESOURCE";

-- SYSTEM PRIVILEGES
GRANT CREATE VIEW TO new_yrf WITH ADMIN OPTION;
```


2.退出登录，查看脚本文件test4.sql: 

```sql
    cat test4.sql
```

![image](./img/运行脚本文件.png) 

3.用自己的账号new_yrf登录,并运行脚本文件 test4.sql: 

```sql
    sqlplus new_yrf/123@localhost/pdborcl
    @test4.sql
```
![image](./img/用自己的账号登录运行脚本.png)







## 查寻表：
开始测试，查询员工：
![image](./img/开始测试，查询员工.png)
查询分区情况和分区索引情况：
![image](./img/查询分区情况和分区索引情况.png)
查询一个分区的数据：
![image](./img/查询一个分区的数据.png)
表空间使用：
![image](./img/表空间使用.png)



## 实验总结
经过本次实验，我学习到了分区表的创建方法，通过实验以及浏览网上相关资料，基本掌握了各种分区方式的使用场景。实验不难，只要跟着老师的调子走，就能顺利完成。
