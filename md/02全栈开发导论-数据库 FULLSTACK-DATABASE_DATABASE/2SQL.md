# SQL语句

---

## SQL语句概述

  * SQL：Structured Query Language，结构化查询语言，用于操作RDBMS中数据的标准化语言
  * 1986年由ANSI推出；1992年ISO推出SQL92标准；1999年ISO推出SQL99标准
  * SQL被主流的RDBMS所支持，所以相同的SQL语句在大多数RDBMS中都可以顺利执行；但各个厂家在实现的细节与拓展方面有所不同。
    >标准SQL中的语句是一条一条的顺序执行，没有定义循环、选择等其它语言必需的结构控制语句，不同的数据库厂家在这方面都有所扩展。
  * 所有的SQL语句可以分为如下四类：
    * **DDL：Data Define Language**，定义数据的结构
    * **DML：Data Manipulate Language**，操作数据，即增删改
    * **DQL：Data Query Language**，查询数据
    * **DCL：Data Control Language**，控制用户的权限

| DDL      | DML    | DQL    | DCL   |
|----------|--------|--------|-------|
| CREATE   | INSERT | SELECT | GRANT |
| DROP     | DELETE | REVOKE |       |
| ALTER    | UPDATE |        |       |
| TRUNCATE |        |        |       |

## SQL语句规范

  * 与很多其它编程语言不同，MySQL数据库所支持的SQL语句有着比较特别的语法要求：
    * 多行注释为：/* ... */,单行注释以 # 开头。
    * 所有语句都必须以英文分号结尾。
    * 一条语句可以编写在多行中。
    * 单词不区分大小写；推荐编写关键字时都使用大写形式，非关键字都使用小写形式。
      >关键字：keyword，是系统预定义好的有特定功能含义的单词，如SHOW、CREATE等；一般情况下，用户自定义的内容不允许使用系统关键字。

## DDL语句

  * DDL：数据定义语言，用于定义数据的结构
  * CREATE：用于创建数据库对象，如库、表等

    ```sql
    CREATE DATABASE xuezi CHARSET UTF8;
    CREATE TABLE emp(id INT,name VARCHAR(32))
    ```
  
  * DROP:用于丢弃数据库对象，入库、表等

    ```sql
    DROP DATABASE IF EXISTS xuezi;
    DROP TABLE emp;
    ```

  * ALTER:用于修改数据库对象的定义
  * TRUNCATE:用于截断表中所有记录

## DML语句

  * DML：数据操作语言，用于操作数据表中的数据
  * INSERT：向表中插入一行或多行记录

    ```sql
    INSERT INTO emp(id,name) VAlues(88,'king')
    ```

      >SQL中的字符串必须使用引号括起来！
  * DELETE:删除表中的记录

    ```sql
    DELETE FROM emp;/*删除所有记录*/
    DELETE FROM emp WHERE id=88;/*删除一行记录*/
    ```
  
  * UPDATE：修改表中的记录

    ```sql
    UPDATE emp SET name="Kane" WHERE id=88;
    ```

## DQL语句

  * DQL：数据查询语言，用于查询数据
  * SELECT：查询表中的记录

    ```sql
    /*查询所有记录行中的id和name两列上的值*/
    SELECT id name FROM emp;
    /*查询某一行记录中的id和name两列上的值*/
    SELECT id,name FROM emp WHERE id=88;
    ```

### 创建学子商城所需数据表

  * 学子商城用户管理模块中需要保存用户如下信息：编号、登录名、登录密码、邮箱、手机号、头像图片路径、用户名、性别。
  * 为了描述上述信息，创建所需要的SQL脚本。