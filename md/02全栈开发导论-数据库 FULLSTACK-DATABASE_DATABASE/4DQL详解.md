# 简单查询

---

## 基本查询

  * 只查询特定的列：
    `SELECT eid, ename FROM emp;`
  * 查询所有的列：
    `SELECT * FROM emp;`
  * 为列取别名：

    ```sql
    SELECT eid AS i,ename AS n FROM emp;
    SELECT eid i,ename n FROM emp;
    ```

      >AS 关键字可以省略

  * 只显示不同的值，重复的值仅显示一次：
    `SELECT DISTINCT depId FROM emp;`
  * 查询过程中执行算术运算：
    `SELECT salary*12+comm AS annualsalary FROM emp;`

## 查询排序

  * 可以使用 ORDER BY 子句对查询结果集进行排序。
  * 升序排列——ASC:

    ```sql
    SELECT * FROM emp
    ORDER BY salary ASC;
    ```

      >ASC 关键字可以省略

  * 降序排列——DESC:
  
    ```sql
    SELECT * FROM emp
    ORDER BY DESC;
    ```

  * 按多列排序：

    ```sql
    SELECT * FROM emp
    ORDER BY deptId, age DESC;
    ```

## 条件查询

  * 条件查询，实现根据特定的条件对结果集进行筛选。
  * 进行相等或不等判断：

    ```sql
    SELECT * FROM emp WHERE eid = 81;
    SELECT * FROM emp WHERE ename = 'Tom';
    SELECT * FROM salary WHERE salary > 6000;
    SELECT * FROM emp WHERE salary < 6000;
    SELECT * FROM emp WHERE salary >= 6000;
    SELECT * FROM emp WHERE salary <= 6000;
    SELECT * FROM emp WHERE depId != 20;
    ```

  * 条件查询过程中，可以使用 AND、OR 关键字实现多个查询条件的“并”、“或”。
  * 多查询条件的“并”——同时都满足：
  
    ```sql
    SELECT * FROM emp
    WHERE age>40 AND depId=10;
    ```

    ```sql
    SELECT * FROM epm
    WHERE age BETWEEN 20 AND 30;
    ```

  * 多查询条件的“或”——只要满足其中之一即可：

    ```sql
    SELECT * FROM emp
    WHERE salary>8000 OR salary<4000;
    ```

    ```sql
    SELECT * FROM emp
    WHERE depId IN (10,30,40);
    ```

  * 条件查询过程中，可以使用 NOT 关键字实现查询条件的“非”：

    ```sql
    SELECT * FROM emp
    WHERE depId NOT IN (10,30,40);
    ```
  
  * 条件查询过程中，可以使用 LIKE 关键字实现模糊查询：

    ```sql
    SELECT * FROM emp
    WHERE ename LIKE '_e%';
    ```

## 分页查询

  * 不同数据库的分页查询语法各不相同。MySQL 使用 LIMIT 关键字实现分页查询。
  * 基本语法：

    ```sql
    SELECT * FROM emp
    [WHERE ...]
    [ORDER BY ...]
    LIMIT start, count;
    ```

      >start 指定从哪一行开始获取记录，第一行下标为0；count 指定一次最多可以获取的记录行数。

  * 假设每页最多显示 20 条记录，则获取各页对应数据可以使用如下语句：

    ```sql
    SELECT * FROM emp LIMIT 0,20;#第 1 页
    SELECT * FROM emp LIMIT 20,20;#第 2 页
    SELECT * FROM emp LIMIT 40,20;#第 3 页
    ...
    SELECT * FROM emp LIMIT (n-1)*20,20;#第n页
    ```

### 练习简单查询

  * 根据学子商城中“笔记本电脑表”中的相关数据，查询出首页中必需的商品的集合。

# 复杂查询

---

## 分组查询

  * MySQL提供了五个聚合函数，可以对查询结果集进行特定的运算：MAX、MIN、SUM、COUNT、AVG。

  * 查询指定列上的最大值：
    `SELECT MAX(salary) FROM emp;#查询工资最大值`
  * 查询指定列上的最小值：
    `SELECT MIN(salary) FROM emp;#查询工资最小值`
  * 查询指定列上数据的总和：
    `SELECT SUM(salary) FROM emp;#查询工资总和`
  * 查询指定列上数据的数量：
    `SELECT COUNT(salary) FROM emp;#查询工资数量`
  * 查询指定列上数据的平均值：
    `SELECT AVG(salary) FROM emp;#查询工资平均值`
  * 分组查询，指将指定列上值相同的记录划分在一组，在组内进行聚合运算：

    ```sql
    SELECT MAX(salary) FROM emp
    GROUP BY depId;

    SELECT SUM(salary) FROM emp
    GROUP BY depId;

    SELECT COUNT(salary) FROM emp
    GROUP BY depId;

    SELECT avg(salary) FROM emp
    GROUP BY depId;
    ```

## 子查询

  * 子查询，是在一个查询语句中的某个或多个字句子中包含其它的查询语句，是一种复合的查询语句。

    ```sql
    SELECT * FROM emp
    WHERE depId = (
      SELECT did FROM dept
      WHERE dname ="研发部"
    )；
    ```

  * 子查询也经常出现在 DML 语句中：

    ```sql
    UPDATE emp
    SET salary = salary*1.1
    WHERE DEPId = (
      SELECT did FROM dept
      WHERE dname = '研发部'
    );
    ```

## 跨表查询

  * 跨表查询，也称多表查询，指一次查询的结果集中出现来自多个表中的多个列。
  * 在SQL-92标准中，采用如下的形式：

    ```sql
    SELECT ename,dname
    FROM emp AS e,dept AS d
    WHERE e.depId = d.did;
    ```

      >若不指定相等条件，会产生“笛卡尔积”
      >
      >注意：SQL-92标准中的跨表拆线呢语句无法查询出两个表中判定条件上值为NULL的记录！
  * SQL-99标准中的跨表查询解决了 SQL-92 中的问题，将跨表查询具体分为下述四种：
    * (1)内连接(INNER JOIN):

      ```sql
      SELECT ename,dname
      FROM emp INNER JOIN dept
      ON emp.depId = dept.did;
      ```

    * (2)左外连接(LEFT OUTER JOIN):

      ```sql
      SELECT ename,dname
      FROM emp LEFT JOIN dept
      ON emp.depId = dept.did;
      ```

        >LEFT OUTER JOIN 可以简写为 LEFT JOIN
    * (3)右外连接(RIGHT OUTER JOIN):
  
      ```sql
      SELECT ename,dname
      FROM emp RIGHT JOIN dept
      ON emp.depId = dept.did;
      ```

        >LEFT OUTER JOIN 可以简写为 LEFT JOIN
    * (4)全连接(FULL JOIN):
      >MySQL 不支持全连接语法！
      >只能使用查询结果集的合并来实现类似效果。

## 结果集合并

  * UNION 关键字用于将两个查询结果集合并为一个大的结果集。
  * 合并结果集，重复数据仅显示一遍：

    ```sql
    SELECT ename FROM emp_cn
    UNION
    SELECT ename FROM emp_us;
    ```
  
  * 合并结果集，允许出现重复数据：

    ```sql
    SELECT ename FROM emp_cn
    UNION ALL
    SELECT ename FROM emp_us;
    ```

### 练习复杂查询

* 查询出价格在3000~5000之间的所有笔记本电脑的数量；
* 查询出笔记型号家族名称中包含“联想”的所有笔记本信息；
* 查询出每个笔记本商品的主标题以及其对应的型号家族的名称。
