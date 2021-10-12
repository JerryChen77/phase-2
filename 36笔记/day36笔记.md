# Day 36笔记

## 一、数据库

### 1.1 现在存储数据的方式

* 甲骨文
* 竹简
* 骨头、青铜器
* 纸
* 胶卷
* 磁带
* 磁盘
* 闪存
* ... ...

### 1.2 存在的问题

* 数据类型没有区分
* 数据容量较小
* 不方便管理、使用



### 1.3 数据库概述

* 数据库是按照数据结构来组织、存储、管理数据的仓库
* 是一个长期存储在计算机内的有组织、有共享的、统一管理的数据集合

### 1.4 数据库管理系统分类

* 网状结构数据库
* 层次结构数据库
* 关系型数据库
* 非关系型数据库

### 1.5 DBMS

Database Management System

## 二、MySQL

### 2.1 概述

* 关系型数据库管理系统
* MySQL是一个**关系型数据库管理系统**，由瑞典MySQL AB 公司开发，属于 [Oracle](https://baike.baidu.com/item/Oracle) 旗下产品。
* 是最流行的关系型数据库管理系统之一
* 免费、使用通用的SQL语言

### 2.2 其他主流数据库

* SQLServer
  * 微软
  * 好用--收费
* Oracle
  * 企业级数据库
  * 好用、功能强大、定制功能
* DB2
  * IBM
* SQLLite
  * 轻量级数据库
  * 使用在Android手机

### 2.3 MySQL下载

* 下载链接
  * https://dev.mysql.com/downloads/installer/
* 推荐版本5.7.XX

### 2.4 MySQL卸载

* 在Windows程序管理界面删除
*  再次运行mysql安装器，选择卸载选项
* 注意：
  * 不要误删数据库中存储的数据

### 2.5 安装MySQL

* 双击安装器
* 选择需要安装的选项
  * 具体操作参考安装教程
* 选择安装位置
* 设置日志文件名称

### 2.6 配置环境变量

* 配置安装目录中的bin到系统的环境变量
* 配置方式参考jdk

## 三、MySQL使用

### 3.1 启动和停止服务

* 图形化界面
  * 服务中的启动和停止
* 使用dos命令
  * 用管理员身份打开命令提示符
  * 启动 
    * net start mysql57
  * 停止
    * net stop mysql57

### 3.2 登录mysql

* 本地登录
  * mysql -u用户名 -p密码
* 远程登录
  * mysql -h 主机地址 -u用户名 -p密码

### 四、数据库级别

### 4.1 查询所有数据库

* show databases;
* 可以看到对当前账户开放的所有数据

### 4.2 创建数据库

* show create database java2103;
* show create database dbname;
  * 使用默认字符编码
* create database java21030  DEFAULT CHARACTER SET utf8;
  * 指定字符编码
* create database if not exists java21030;
  * 如果数据库已经存在避免报错

### 4.3 查看建表语句

* show create database dbname;

### 4.4 切换数据库

* use dbname;

### 4.5 删除数据库

* drop database dbname;

### 4.6 查看当前使用的数据库

* select database();

## 五、SQL可视化工具

### 5.1 Navicat

### 5.2 SQLYog

### 5.3 导入sql文件

* 把别人的数据库结构或者数据导入到我的数据库中

### 5.4 导出数据库

* 把我的数据库结构或者数据导出成sql文件

## 六、查询

### 6.1 基本查询

```
select XX,XXX,XXX from tbname;
```

### 6.2 查询部分列

* SELECT first_name,last_name,hire_date,salary FROM t_employees;

### 6.3 查询全部信息

* SELECT * FROM t_employees;

### 6.4 查询中的运算

```
+
-
*
/
```

* %作为一个独立的符号，在模糊查询中使用

* SELECT first_name,salary*12 from t_employees

### 6.5 列的别名

* 有的列查询之后显示的效果不够理想
* 可以给这些列设置独立的名字
* 使用关键字as
* SELECT first_name as '名字',salary*12 as '年薪' from t_employees

### 6.6 查询结果去重

* distinct
* SELECT DISTINCT t_employees.DEPARTMENT_ID from t_employees

## 七、排序查询

### 7.1 概述

* 排序查询的关键字
  * order by 字段

### 7.2 可以正序或者倒序

* 正序是按照自然顺序--默认的排序方式
  * SELECT t_employees.first_name,salary FROM t_employees ORDER BY salary;
* 正序是可以使用asc放在字段之后
  * SELECT t_employees.first_name,salary FROM t_employees ORDER BY salary ASC;
* 倒序使用desc放在字段之后
  * SELECT t_employees.first_name,salary FROM t_employees ORDER BY salary DESC;

### 7.3 可以使用多列排序

* 先按照员工工资排序
* 如果工资相同，按照id倒序排
* SELECT t_employees.EMPLOYEE_ID,t_employees.FIRST_NAME,salary from t_employees ORDER BY salary desc,t_employees.EMPLOYEE_ID DESC

## 八条件查询 

### 8.1 条件查询

* 使用where关键字 + 条件

### 8.2 等值查询=

* 使用=符号
* SELECT t_employees.EMPLOYEE_ID,t_employees.FIRST_NAME,t_employees.DEPARTMENT_ID FROM t_employees WHERE t_employees.DEPARTMENT_ID=100

### 8.2 逻辑判断

* and
  * 同时满足

```
SELECT t_employees.EMPLOYEE_ID,t_employees.FIRST_NAME,t_employees.MANAGER_ID,t_employees.DEPARTMENT_ID from t_employees WHERE t_employees.MANAGER_ID=108 AND t_employees.DEPARTMENT_ID=100
```

* or
  * 满足其中之一

```
SELECT t_employees.EMPLOYEE_ID,t_employees.FIRST_NAME,t_employees.DEPARTMENT_ID from t_employees where t_employees.DEPARTMENT_ID=60 or t_employees.DEPARTMENT_ID=70 or t_employees.DEPARTMENT_ID=80 ORDER BY t_employees.DEPARTMENT_ID
```

* not
  * 取反

```
SELECT t_employees.EMPLOYEE_ID,t_employees.FIRST_NAME,t_employees.DEPARTMENT_ID FROM t_employees WHERE NOT t_employees.DEPARTMENT_ID=100
```

### 8.3 不等值判断

* ```
  >    >=
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary>=10000 ORDER BY salary ASC;
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary>10000 ORDER BY salary ASC;
  ```

* ```
  <    <=
  
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary<=10000 ORDER BY salary ASC;
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary<10000 ORDER BY salary ASC;
  ```

* ```
  !=   <>
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary!=10000 ORDER BY salary ASC;
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary<>10000 ORDER BY salary ASC;
  ```

### 8.4 区间判断

* ```mysql
  between A and B
  
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary>=6000 and salary<=10000 ORDER BY salary ASC;
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary<=10000 and salary>=6000 ORDER BY salary ASC;
  
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary BETWEEN 6000 and 10000 ORDER BY salary ASC;
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary BETWEEN 10000 and 6000 ORDER BY salary ASC;
  ```

### 8.5 非空判断

```mysql
is null
SELECT EMPLOYEE_ID,first_name,COMMISSION_PCT FROM t_employees where COMMISSION_PCT is null;

```

```
is not null
SELECT EMPLOYEE_ID,first_name,COMMISSION_PCT FROM t_employees where COMMISSION_PCT is not null;
```

### 8.6 枚举查询

```mysql
in(数据1,数据2,数据3...)
SELECT EMPLOYEE_ID,FIRST_NAME,DEPARTMENT_ID from t_employees where DEPARTMENT_ID in (60,90,110);
```

### 8.7 模糊查询

* 使用关键字like 

* ```mysql
  _	任意一个字符
  	SELECT EMPLOYEE_ID,FIRST_NAME,DEPARTMENT_ID from t_employees where EMPLOYEE_ID like '11_';
  
  %	任意个数字符
  	SELECT EMPLOYEE_ID,FIRST_NAME,hire_date from t_employees where hire_date like '1999%';
  ```

  

### 8.8 分支结构查询【面试前背一背】

- 给工资评等级
  - 工资 >= 20000     A
  - 15000 =< 工资 < 20000   B
  - 10000 <= 工资 < 15000   C
  - 5000 <= 工资 < 10000    D
  - 工资 < 5000   E

```mysql
-- 查询语句，不能出现*，公司不允许
SELECT 
	`EMPLOYEE_ID`,
	`LAST_NAME`,
	`SALARY`,
	CASE
		WHEN `SALARY`>=20000 THEN 'A'
		WHEN `SALARY`>=15000 THEN 'B'
		WHEN `SALARY`>=10000  THEN 'C'
		WHEN `SALARY`>=5000  THEN 'D'
		ELSE 'E'
	END AS salary_level
FROM `t_employees`
```



# 九、函数【会用】

## 1、时间函数

### 1.1 获取当前时间

- sysdate()			---  yyyy-MM-dd HH:mm:ss
- now()
- CURDATE()         ---  yyyy-MM-dd
- CURTIME()         ---  HH:mm:ss

```mysql
-- 别名以后不能起中文，英文(xxx_yyy_zzz)
SELECT SYSDATE(),YEAR('2021-12-12') "年",MONTH('2021-12-12') "月",DAY(SYSDATE()) "日",WEEK('2021-12-12') "星期(从一年的第一天开始计算)";
```



### 1.2 时间计算

- 求差值
  - datediff()
- 指定时间进行增减操作
  - adddate()

```mysql
-- 时间差值
-- 参数1：大时间，可以使用字符串
-- 参数2：小时间，可以使用字符串
SELECT DATEDIFF('2021-07-01', '2021-06-01');
SELECT DATEDIFF(SYSDATE(), '2021-06-01 12:00:00');

-- 根据指定时间天数来计算过去或者未来
SELECT ADDDATE(SYSDATE(),30), ADDDATE(SYSDATE(), -30);
```



## 2、字符串

```mysql
SELECT
-- 求长度
  LENGTH('I love mysql'),
  -- 截取字符串，参数1：要操作的字符串，参数2：从哪个位置开始【位置从1开始】，参数3:截取的长度
  SUBSTR('java,mysql,html,js', 5, 6),
  -- 连接
  CONCAT('my', ' ', 'name'),
  -- 转大写
  UPPER('I Love mysql'),
  -- 转小写
  LOWER('China'),
  -- 替换，参数1：要操作的字符串，参数2：要被替换的字符串，参数3:替换的内容
  REPLACE(UUID(),'-','');
```



## 3、时间转字符串

- https://www.cnblogs.com/jhy-ocean/p/5560857.html

```mysql
-- 时间转字符串
SELECT DATE_FORMAT(SYSDATE(), '%y年%m月%d日');
```



## 4、聚合函数【分组函数】【掌握】

> 求和：只能应用于数值类型
>
> 求平分：只能应用于数值类型
>
> 求最大值
>
> 求最小值
>
> 求计数

```mysql
-- 聚合函数
-- 聚合函数在计算时，会去除null值
-- 聚敛函数操作的是多行，返回一个值
SELECT SUM(salary), AVG(salary), MAX(`FIRST_NAME`), MIN(`LAST_NAME`), COUNT(1), COUNT(`COMMISSION_PCT`) FROM t_employees;
```



## 5、分组函数

- group by
  - 就是出现每个，各个这种字眼，那么就代表要按这个字眼

```
select

from

where

group by 分组【分组是在where之后】

order by
```



- 需求：查询每个部门的员工人数及最高工资的员工姓名

```mysql
SELECT 
	-- 分组查询能够出现的字段【聚合函数，被分组的字段】
	`DEPARTMENT_ID`, COUNT(1), MAX(`SALARY`) max_salary,`LAST_NAME`
FROM
	`t_employees`
GROUP BY `DEPARTMENT_ID`
ORDER BY max_salary
```

- 需求：查询每个部门的员工工资总和、平均工资、部门人数

```mysql
SELECT `DEPARTMENT_ID`,`JOB_ID`,COUNT(1), AVG(`SALARY`)
FROM t_employees
GROUP BY `DEPARTMENT_ID`,`JOB_ID`
```

5.1 多字段分组

- 按分组字段从左到右顺序进行分组

```mysql
-- 统计每个部门每个工种的人数及平均工资
SELECT `DEPARTMENT_ID`,`JOB_ID`,COUNT(1), AVG(`SALARY`)
FROM t_employees
GROUP BY `DEPARTMENT_ID`,`JOB_ID`
```

- 分组前条件过滤

```mysql
-- 统计每个部门每个工种工资>5000的人数及平均工资
-- 这个过滤条件是在分组之前执行的
SELECT `DEPARTMENT_ID`,`JOB_ID`,COUNT(1), AVG(`SALARY`)
FROM t_employees
WHERE salary > 5000
GROUP BY `DEPARTMENT_ID`,`JOB_ID`
```

- 分组后条件过滤

```mysql
-- 统计每个部门每个工种工资>5000及平均工资>8000的DEPARTMENT_ID,job_id,人数及平均工资
SELECT 
	DEPARTMENT_ID, job_id, COUNT(1), AVG(salary) avg_salary
FROM t_employees
WHERE salary > 5000
GROUP BY `DEPARTMENT_ID`,`JOB_ID`
-- 分组之后过滤
HAVING avg_salary > 8000
```

- 注意：有些业务场景下，条件过滤器在分组前和分组后都能实现【建议选择使用where】



# 十、限定查询

- 限定查询
  - 有使用两个参数，参数1:起始下标，参数2:显示行数

```mysql
-- 查询工资前5的员工信息
SELECT *
FROM
t_employees
ORDER BY salary DESC 
LIMIT 0,5

-- 查询工资第6名到第10名的员工信息
SELECT *
FROM
t_employees
ORDER BY salary DESC 
LIMIT 5,5
-- limit 代表限定
-- 如果只是查询前几个，可以使用一个值【查询记录数】
-- 如果查的是中间，那么需要使用两个参数，参数1:起始下标，参数2，显示行数

-- 查询工资第11名到第15名的员工信息
SELECT *
FROM
t_employees
ORDER BY salary DESC 
LIMIT 10,5


-- 1   1-5
-- 2   6-10
-- 3   11-15
--  .....

-- 分页：是为了提高用户体验度
-- limit (页码-1)*页大小,页大小
```



# 十一、SQL执行顺序【面试题】

- https://www.cnblogs.com/ziyiFly/archive/2008/09/12/1289614.html

  ```mysql
  FROM ：指定数据来源表
  WHERE : 对查询数据做第一次过滤
  GROUP BY : 分组
  聚合函数
  HAVING : 对分组后的数据第二次过滤
  表达式运算(+ - / *, 函数)
  SELECT : 查询各字段的值
  ORDER BY : 排序
  LIMIT : 限定查询结果
  ```






