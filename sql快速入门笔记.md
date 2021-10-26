# Chaper1. 需要知道的

## 一. 概念

- 什么是数据库

  > 数据存储的仓库，数据的集合。
  >
  > 当然,数据库中的数据:1.有序的  2.有组织 方便管理数据

- 为什么需要?

  > 大数据时代,高效存储和访问信息
  >
  > 如Excel无法批量处理大量信息

- SQL与数据库的关系

  > SQL(Structured Query Language)结构化查询语言
  >
  > 三大主流关系型数据库（MsSQL，MySQL，Oracle）的通用操作语言
  >
  > MsSQL (微软)数据库、MySQL (甲骨文)数据库、Oracle (甲骨文)数据库 都指不同的数据库管理系统(DBMS)
  >
  > 数据库管理系统--一套软件,帮助用户管理数据
  >
  > **总:**SQL用于操作数据库

- 数据存储格式:表(table)

  | **name** | **age** | **sex** | **height** | **birthday** |
  | -------- | ------- | ------- | ---------- | ------------ |
  | 张三     | 20      | 男      | 180        | 2000-01-01   |
  | 李四     | 18      | 女      | 170        | 2002-01-01   |
  | 王五     | 25      | 男      | 165        | 1995-01-01   |

- [数据库中的键（码）](https://blog.csdn.net/xyzyhs/article/details/99438912)  

  - 关系型数据库中,关系=表;键是表的逻辑部分(非物理)
  - 键是区分一个组的唯一标识
  - 主键是候选键中被选择的一个
  - 外键:在一个关系A中，有一个属性b不是关系A主键或候选键，但是是另一关系B的主键，则属性b是关系A中的外键

- 约束:作用于表的列,规定表中数据存储规则,不符合约束则不能录入

  > **NOT NULL** - 指示某列不能存储 NULL 值，即空，什么都没有。
  >
  > **UNIQUE** - 保证每行的某一列必须具有唯一的值，不能重复。
  >
  > **PRIMARY KEY** 
  >
  > **FOREIGN KEY** - 能使用外键约束的列，其数据在另一个表中必须是主键(候选键)。数据库正是通过外键来建立表与表之间的联系。
  >
  > **CHECK** - 保证列中的值符合指定的条件，确保数据的合理性。
  >
  > **DEFAULT** - 规定没有给列赋值时的默认值。

- SQL语句的格式

  > SQL :命令式语言，语法简单，一条命令=一条语句，
  >
  > 大小写不敏感，建议统一小写。
  >
  > **四大类命令**:
  >
  > A：DDL（Data Definition Language）数据定义语言
  >
  > 　　　　　　主要命令包括：create（创建）、alter（修改）、drop（删除）
  >
  > B：DQL（Data Query Language）数据查询语言
  >
  > 　　　　　　主要命令包括：select 
  >
  > C：DML（Data Manipulation Language）数据操纵语言
  >
  > 　　　　　　主要命令包括：insert（插入）、update（修改），delete（删除）
  >
  > 很多时候，select 命令也被认为是 DML 语言的一种，所以，如果你在其他地方听到这种说法时，不必感到诧异。
  >
  > D：DCL（data Control Language）数据控制语言
  >
  > 主要命令包括：grant（授权）、revoke（回收）、commit（提交）、rollback（回滚）等

- SQL和NoSQL

  > SQL用于RDBMS关系型数据库
  >
  > NoSQL用于非关系型数据库

- 区分概念:![image-20210929193410469](C:\Users\31219\Documents\Typora Markdown\LeetCode刷题笔记\sql系统学习笔记.assets\image-20210929193410469.png)

  > @localhost 一个数据源data source;并非一台主机上只能作为一个数据源
  >
  > schema : mysql的一种数据格式而已
  >
  > easyproject:当前数据源下的一个数据库
  >
  > table:表

- 数据库列类型:

  | 数值类型  | 描述                     | 内存           |
  | --------- | ------------------------ | -------------- |
  | tinyint   | 微小的整数               | 1Byte          |
  | smallint  | 小的整数                 | 2Byte          |
  | mediumint | 中等大小的整数           | 3Byte          |
  | * int     | 标准大小的整数(常用整数) | 4Byte          |
  | bigint    | 较大的整数               | 8Byte          |
  | float     | 单精度浮点数             | 4Byte          |
  | double    | 双精度浮点数             | 8Byte          |
  | decimal   | 字符串形式的浮点数       | 金融计算时使用 |

  | 字符串类型数据 | 描述           | 大小                                   |
  | -------------- | -------------- | -------------------------------------- |
  | *char          | 字符串固定大小 | 0~255                                  |
  | *varchar       | 可变字符串     | 0~65535 常用的变量  等同于java的String |
  | *tinytext      | 微型文本       | 2^8-1                                  |
  | *text          | 文本串         | 2^16-1   保存大文本                    |

  | 时间日期 类型数据 | 格式               | 描述                               |
  | ----------------- | ------------------ | ---------------------------------- |
  | *date             | YYYY-MM-DD         | 日期格式                           |
  | *time             | HH:mm:ss           | 时间格式                           |
  | *datetime         | YYY-MM-DD HH:mm:ss | 最常用的时间格式                   |
  | *timestamp        | 时间戳             | 1970.01.01到现在的毫秒数  较为常用 |
  | *year             | 年份表示           | 年份表示                           |

- 数据库引擎(driver)

  |              | MYISAM(早些年使用) | INNODB(默认使用) |
  | ------------ | ------------------ | ---------------- |
  | 事务支持     | 不支持             | 支持             |
  | 数据行锁定   | 不支持,只支持表锁  | 支持             |
  | 外键约束     | 不支持             | 支持             |
  | 全文索引     | 支持               | 支持             |
  | 表空间的大小 | 较小               | 较大,约为2倍     |

  - MYISAM:节省空间,速度快
  - INNODB:安全性高,事务处理,多表多用户操作

- 数据库在物理空间存在的位置

  > 1. 所有的数据库文件都存储在\data目录下,其本质还是文件的存储
  >
  > 2. 可以看到 .ibd文件
  >
  >    ![image-20210930085619558](C:\Users\31219\Documents\Typora Markdown\LeetCode刷题笔记\sql系统学习笔记.assets\image-20210930085619558.png)



## 二. 

- 入门命令

  ```
  //启动请求的服务
  net start mysql
  //登录命令
  mysql -u[admin] -p[password]
  
  D:\mysql-8.0.26-winx64\bin>mysql -u root -p  123456
  Enter password: ******
  ERROR 1049 (42000): Unknown database '123456'//123456被识别为了数据库
  //正确输入
  mysql -u root -p123456
  -- 注意分号
  create database if not exists easyproject;
  show databses;
  drop database if exists easyproject;
  show databases;
  use test_db;
  show tables;
  describe users;
  
  //退出 也可键入ctr+z
  exit
  //清空mysql服务,等同于删库跑路
  sc delete mysql
  ```

  ```
  -- 这是单行注释
  /*
  这是多行注释
  */
  -- 如果表名或字段名是特殊字符,加\''(由于name column等是SQL内部有的字段,类似Java 关键字不能用作变量名,SQL会把这些同名的加上单引号以区分。 保险起见,全加)
  -- 一个完整对话
  D:\mysql-8.0.26-winx64\bin>mysql -uroot -p123456
  mysql: [Warning] Using a password on the command line interface can be insecure.
  Welcome to the MySQL monitor.  Commands end with ; or \g.
  Your MySQL connection id is 757
  Server version: 8.0.26 MySQL Community Server - GPL
  
  Copyright (c) 2000, 2021, Oracle and/or its affiliates.
  
  Oracle is a registered trademark of Oracle Corporation and/or its
  affiliates. Other names may be trademarks of their respective
  owners.
  
  Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
  
  mysql> show databases;
  +--------------------+
  | Database           |
  +--------------------+
  | easyproject        |
  | information_schema |
  | mysql              |
  | performance_schema |
  | sys                |
  | test_db            |
  +--------------------+
  6 rows in set (0.01 sec)
  
  
  mysql> show create database easyproject;
  +-------------+---------------------------------------------------------------------------------------------------------------------------------------+
  | Database    | Create Database                                                                                                                       |
  +-------------+---------------------------------------------------------------------------------------------------------------------------------------+
  | easyproject | CREATE DATABASE `easyproject` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci */ /*!80016 DEFAULT ENCRYPTION='N' */ |
  +-------------+---------------------------------------------------------------------------------------------------------------------------------------+
  1 row in set (0.00 sec)
  
  mysql> use easyproject
  Database changed
  mysql> show tables
      -> ;
  +-----------------------+
  | Tables_in_easyproject |
  +-----------------------+
  | easyuser              |
  | mainmenu              |
  | submenu               |
  +-----------------------+
  3 rows in set (0.00 sec)
  
  mysql> show create table easyuser
      -> ;
  +----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  | Table    | Create Table                                                                                                                                                                                                                                                                                                                                   |
  +----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  | easyuser | CREATE TABLE `easyuser` (
    `id` int NOT NULL AUTO_INCREMENT COMMENT '主键',
    `username` varchar(255) NOT NULL,
    `password` varchar(255) NOT NULL,
    `email` varchar(255) NOT NULL,
    `role` varchar(255) NOT NULL,
    `state` tinyint NOT NULL DEFAULT '0',
    PRIMARY KEY (`id`)
  ) ENGINE=InnoDB AUTO_INCREMENT=11 DEFAULT CHARSET=utf8mb3   |
  +----------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
  1 row in set (0.00 sec)
  
  mysql> desc easyuser
      -> ;
  +----------+--------------+------+-----+---------+----------------+
  | Field    | Type         | Null | Key | Default | Extra          |
  +----------+--------------+------+-----+---------+----------------+
  | id       | int          | NO   | PRI | NULL    | auto_increment |
  | username | varchar(255) | NO   |     | NULL    |                |
  | password | varchar(255) | NO   |     | NULL    |                |
  | email    | varchar(255) | NO   |     | NULL    |                |
  | role     | varchar(255) | NO   |     | NULL    |                |
  | state    | tinyint      | NO   |     | 0       |                |
  +----------+--------------+------+-----+---------+----------------+
  6 rows in set (0.01 sec)
  
  mysql> exit
  Bye
  ```

- alter 是DDL语句，是修改数据库中对象（表，数据库，视图...）的语句。

  ```
  如需在表中添加列，请使用下面的语法:
  ALTER TABLE table_name
  ADD column_name datatype
  
  如需删除表中的列，请使用下面的语法（请注意，某些数据库系统不允许这种在数据库表中删除列的方式）：
  ALTER TABLE table_name
  DROP COLUMN column_name
  
  要改变表中列的数据类型，请使用下面的语法：
  ALTER TABLE table_name
  MODIFY COLUMN column_name datatype
  ```

  update是DML语句，是修改表中数据的语句。

  ```
  UPDATE table_name SET field1=new-value1, field2=new-value2
  [WHERE Clause]
  ```

- 外键

  - 两张表之间建立索引,如:

    > 已有父表grade:
    >
    >  ![image-20211002162437626](C:\Users\31219\Documents\Typora Markdown\LeetCode刷题笔记\sql系统学习笔记.assets\image-20211002162437626.png)
    >
    > 从表students中的grade(称为从表的外键)与grade中的gradeId(必须是父表的主键)关联:
    >
    > ![image-20211002162344111](C:\Users\31219\Documents\Typora Markdown\LeetCode刷题笔记\sql系统学习笔记.assets\image-20211002162344111.png)

    

  - 在建表时添加外键constraint

    ```
    create table students
    (
        name   varchar(50) not null,
        id     int auto_increment
            primary key,
        gender varchar(50) null,
        grade  int         null,
        -- 添加外键约束
        constraint FK_grade
            foreign key (grade) references grade (gradeId)
                on update cascade on delete cascade
                
    );
    ```

  - 为创建好的表添加外键constraint

    ```
    alter table students
    	add constraint FK_grade
    		foreign key (grade) references grade (gradeId)
    			on update cascade on delete cascade;
    
    ```

    ![image-20211002163016245](C:\Users\31219\Documents\Typora Markdown\LeetCode刷题笔记\sql系统学习笔记.assets\image-20211002163016245.png)

  - 在父表上进行update/delete以更新或删除在子表中有一条或多条对应匹配行的候选键时，父表的行为取决于：在定义子表的外键时指定的on update/on delete子句。

    | 关键字    | 含义                                                         |
    | --------- | ------------------------------------------------------------ |
    | CASCADE   | 删除包含与已删除键值有参照关系的所有记录                     |
    | SET NULL  | 修改包含与已删除键值有参照关系的所有记录，使用NULL值替换(只能用于已标记为NOT NULL的字段) |
    | RESTRICT  | 拒绝删除要求，直到使用删除键值的辅助表被手工删除，并且没有参照时(这是默认设置，也是最安全的设置) |
    | NO ACTION | 啥也不做                                                     |

