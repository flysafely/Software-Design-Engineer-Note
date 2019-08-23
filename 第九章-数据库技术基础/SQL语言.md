### 关系数据库SQL语言
  + 功能
    + **数据查询：`SELECT`，`FROM`，`WHERE`**
      > **数据库查询语言DQL**
    + **数据操纵：`INSERT`，`UPDATE`，`DELETE`**
      > **数据库定义语言DML**<br>
    + **数据定义：`CREATE`，`DROP`，`ALTER`**
      > **数据库操纵语言DDL**<br>
        DDL操作是隐性提交的！不能rollback 
    + **数据控制：`GRANT`授权，`REVORK`取消授权，`ROLLBACK`回滚，`COMMIT`提交**
      > **数据库控制语言DCL**<br>
        **提交方式：**<br>
        **1.显式提交**<br>
          用COMMIT命令直接完成的提交为显式提交。其格式为：<br>
          SQL>COMMIT；<br>
        **2.隐式提交**<br>
          用SQL命令间接完成的提交为隐式提交。这些命令是：<br>
          ALTER，AUDIT，COMMENT，CONNECT，CREATE，DISCONNECT，DROP，<br>
          EXIT，GRANT，NOAUDIT，QUIT，REVOKE，RENAME<br>
        **3.自动提交**<br>
          若把AUTOCOMMIT设置为ON，则在插入、修改、删除语句执行后，<br>
          系统将自动进行提交，这就是自动提交。其格式为：<br>
          SQL>SET AUTOCOMMIT ON；<br>
  + 特点
    + 综合统一
    + 高度非过程化
    + 面向集合的操作方式
    + 两种使用方式
    + 语言简洁、易学易用
 
    
 
