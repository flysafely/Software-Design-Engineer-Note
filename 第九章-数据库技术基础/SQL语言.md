### 关系数据库SQL语言
  + 特点
    + 综合统一
    + 高度非过程化
    + 面向集合的操作方式
    + 两种使用方式
    + 语言简洁、易学易用
  + **功能**★★★
    + **数据查询：`SELECT`，`FROM`，`WHERE`**
      > **数据库查询语言DQL**
      + 格式<br>
        SELECT [ALL|DISTINCT]<目标列表达式>[,<目标列表达式2>]...<br>
        FROM <表名或者视图名> [,<表名或视图名>]<br>
        [WHERE <条件表达式>]<br>
        [[GROUP BY <列名 1> [HAVING<条件表达式>]]](https://www.jianshu.com/p/ad92b44b0a82)<br>
        [ORDER BY <列名 2> [ASC|DESC]]<br>
      + 子查询<br>
        > 嵌套查询
        ```SQL
        SELECT Sno,Sname
          FROM S
          WHERE Sno IN(SELECT Sno
                         FROM SC
                         WHERE Cno IN(SELECT Cno
                                        FROM C
                                        WHERE Cname='MS'))
        ```
      + 聚集函数
        > 以一个值的集合为输入，返回单个值的函数
        + 预设聚集函数：
        
        |聚集函数|功能|说明|
        |:--|:--:|:--:|
        |**COUNT**([DISTINCT\|ALL]*)|统计元组的个数|如果使用了GROUP BY<br>则会按照每个分组来统计元组个数|
        |**COUNT**([DISTINCT\|ALL]<列名>)|统计一列中值的个数||
        |**SUM**([DISTINCT\|ALL]<列名>)|计算数值型的一列中值得总和||
        |**AVG**([DISTINCT\|ALL]<列名>)|计算数值型值得平均值||
        |**MAX**([DISTINCT\|ALL]<列名>)|求一列值的最大值||
        |**MIN**([DISTINCT\|ALL]<列名>)|求一列值的最小值||
      + ANY、ALL谓词和聚集函数的等价转换
        > 在子查询中使用聚集函数的效率比直接使用ANY、ALL要高
        
        |谓词表达|聚集函数表达|
        |:--:|:--:|
        |>ANY|>MIN|
        |>ALL|>MAX|
        |<ANY|<MIN|
        |<ALL|<MAX|
        |>=ANY|>=MIN|
        |>=ALL|>=MAX|
        |<=ANY|<=MIN|
        |<=ALL|<=MAX|
        |<>ANY|--|
        |<>ALL|NOT IN|
        |=ANY|IN|
        |=ALL|--|
        
    + **数据操纵：`INSERT`，`UPDATE`，`DELETE`**
      > **数据库定义语言DML**<br>
    + **数据定义：`CREATE`，`DROP`，`ALTER`**
      > **数据库操纵语言DDL**<br>
        SQL数据定义包括对表、视图、索引的创建和删除<br>
        DDL操作是隐性提交的！不能rollback <br>
      + **表**
        + 创建
          ```SQL
          CREATE TABLE SP(Sno CHAR(5) NOT NULL UNIQUE,/*NOT NULL UNIQUE是列级完整性约束条件*/
                          Pno CHAR(30) UNIQUE,/*CHAR(30)是数据类型和长度*/
                          Status CHAR(8),
                          Qty CHAR(20),
                          CONSTRAINT C1 PRIMARY KEY(Sno),/*名为C1为表级完整性约束条件,因为已经在表约束条件中约定Sno为主键，所以NOT NULL UNIQUE可以省略*/
                          CONSTRAINT C2 CHECK (Sno BETWEEN 90000 AND 999999)/*名为C2表级完整性约束条件,自定以约束条件*/
                          CONSTRAINT C3 FOREIGN KEY(Sno) REFERENCES S(Sno),/*名为C3表级完整性约束条件*/
                          CONSTRAINT C4 FOREIGN KEY(Pno) REFERENCES P(Pno));/*名为C4为表级完整性约束条件*/
          ```
        + 修改(谨慎修改)
          ```SQL
          /*修改表名*/
          ALTER TABLE S RENAME NewS
          /*修改多个表名*/
          RENAME TABLE S TO NewS,TABLE M TO NewM
          /*增加列*/
          ALTER TABLE S ADD Zap CHAR(6)
          /*删除列*/
          ALTER TABLE S DROP COLUMN Zap
          /*修改列*/
            /*修改列名称*/
            ALTER TABLE S CHANGE Zap NewZap INT NOT NULL
            /*修改列类型*/
            ALTER TABLE S MODIFY Zap NUMERIC(9)
            /*修改完整性约束*/
            ALTER TABLE Student DROP CONSTRAINT C2;     /*删除原来的完整性约束命名子句C2*/
            ALTER TABLE Student DROP CONSTRAINT C1;     /*删除原来的完整性约束命名子句C1，重定义C1*/
            ALTER TABLE Student ADD CONSTRAINT C1 CHECK (Sno BETWEEN 20000 AND 30000),
          ```
        + 删除
          ```SQL
          /*删除表*/
          DROP TABLE S
          ```
      + **索引**
        + 聚集索引
          > 索引表中的索引项的顺序与表中记录的物理顺序**一致**
        + 非聚集索引
          > 索引表中的索引项的顺序与表中记录的物理顺序**不一致**
        + 创建
        ```SQL
        /*CREATE [索引值唯一] [聚簇索引] INDEX <索引名> ON <表名>(<列名1>[次序][,<列名2>[次序]]...)*/
        CREATE [UNIQUE] [CLUSTER] INDEX SPJ-NO ON SPJ(Sno ASC,Pno DESC,JNO ASC)
        ```
        + 删除
        ```SQL
        DROP INDEX <索引名>
        ```
      + **视图**
        > 视图不是真实存在的基本表，是一个虚拟表，视图对应的数据并不实际以视图结构储存在数据库中，而是存储在视图所引用的表中
        + 创建
        ```SQL
        CREATE VIEW CS-STUDENT
          AS SELECT Sno,Sname,Sage,Sex
          FROM Student
          WHERE SD='CS'
          WITH CHECK OPTION;/*对该视图进行修改、插入操作时DBMS会自动加上SD='CS'的条件，保证该视图中只有计算机系的学生*/
        ```
        + 删除
        ```SQL
        DROP VIEW <视图名>
        ```
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
 
    
 
