# 一、子查询

## 1、嵌套查询

- 查询中还有查询
  -  select中嵌套select

## 2、分类

- 子查询结果是一个值【一行一列】

  ```mysql
  -- 查询工资大于108号员工的员工信息
  -- 1.查询108号员工的工资
  SELECT salary FROM t_employees WHERE employee_id = 108
  -- 2.查询大于1.的结果作为条件，查询员工信息
  SELECT * FROM t_employees WHERE salary > 12000
  
  -- 子查询结果是一个值
  -- 先走SQL中内部的select
  SELECT * FROM t_employees WHERE salary > (SELECT salary FROM t_employees WHERE employee_id = 108)
  ```

- 子查询结果是多个值【多行一列】

  ```mysql
  -- 查询与名为'King'同一部门的员工信息
  SELECT `DEPARTMENT_ID` FROM `t_employees` WHERE `LAST_NAME` = 'King'
  SELECT * FROM `t_employees` WHERE `DEPARTMENT_ID` IN (80,90)
  
  -- 子查询结果是多行一列
  SELECT * FROM `t_employees` WHERE `DEPARTMENT_ID` IN (
  	SELECT `DEPARTMENT_ID` FROM `t_employees` WHERE `LAST_NAME` = 'King'
  )
  ```

  ```mysql
  -- 查询员工工资高于100号部门的任意一个员工工资的员工信息
  -- any
  SELECT * FROM t_employees WHERE salary > ANY (SELECT salary FROM t_employees WHERE department_id = 100);
  SELECT * FROM t_employees WHERE salary > (SELECT MIN(salary) FROM t_employees WHERE department_id = 100);
  
  -- 查询员工工资高于100号部门的所有员工工资的员工信息
  -- all
  SELECT * FROM t_employees WHERE salary > ALL (SELECT salary FROM t_employees WHERE department_id = 100);
  SELECT * FROM t_employees WHERE salary > (SELECT MAX(salary) FROM t_employees WHERE department_id = 100);
  ```

- 子查询结果是一张表【多行多列】

  ```mysql
  -- 查询员工表中工资排名前5名的员工信息
  SELECT * FROM (
  	SELECT * FROM `t_employees` ORDER BY `SALARY` DESC
  ) AS emp
  LIMIT 0,5
  ```

   

# 二、合并查询【会用】

- union：会去重
- union all：不去重

```mysql
-- 合并查询
-- 合并查询到的多个结果集
-- union 合并结果集并去重
SELECT * FROM `t_hz_stu` UNION
SELECT * FROM `t_wz_stu`

-- union all 合并结果集不去重
SELECT * FROM `t_hz_stu` UNION ALL
SELECT * FROM `t_wz_stu`
```



# 三、连表查询

- 多个连表连接在一起查询
  - 一定要解决一个问题【笛卡尔积】
    - 产生笛卡尔积问题，就是因为没有加过滤条件
    - 解决方案：加上过滤条件

| 连表查询                                                     |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210607174959579.png" alt="image-20210607174959579" style="zoom:80%;" /> |

## 1、分类

- 内连接
  - 显示内连接
  - 隐式内连接
- 外连接
  - 左外连接
  - 右外连接
  - 满外连接（mysql不支持）



## 2、内连接

- ==查询到的是匹配两个表的条件的相同记录【交集】==

- 隐式内连接：被称为叫等值连接
  - 使用 where  直接指定关联字段相等即可

```mysql
SELECT *
FROM `t_employees`,`t_departments`
WHERE `t_employees`.`DEPARTMENT_ID` = `t_departments`.`DEPARTMENT_ID`
```

- 显示内连接
  - A inner join B on A.关联字段 = B.关联字段

```mysql
-- 显示内连接
-- 查询员工信息及所在部门的信息
SELECT *
FROM `t_employees` INNER JOIN `t_departments`
ON `t_employees`.`DEPARTMENT_ID` = `t_departments`.`DEPARTMENT_ID`
```



## 3、外连接

```mysql
-- 查询所有员工信息关联部门的信息
-- 外连接【左外连接、右外连接】
-- 左外连接，以左为基准，展示全部内容。如果右表能够匹配，则显示匹配的内容，如果右表没有匹配，则以null填充
-- 当查询结果集出现相同列名时，务必要为相同的列名取一个别名，保证不要重复
SELECT
  e.*,
  d.`DEPARTMENT_ID` did, d.`DEPARTMENT_NAME`, d.`LOCATION_ID`, d.`MANAGER_ID`
FROM
  `t_employees` e
  LEFT JOIN `t_departments` d
    ON e.`DEPARTMENT_ID` = d.`DEPARTMENT_ID`
    
-- 右外连接
SELECT
  d.*,
  e.*
FROM
  `t_employees` e
  RIGHT OUTER JOIN `t_departments` d
    ON e.`DEPARTMENT_ID` = d.`DEPARTMENT_ID`
```



## 4、三表及以上的多表连接

```mysql
SELECT *
 FROM
 `t_employees` e INNER JOIN `t_departments` d
 ON e.`DEPARTMENT_ID` = d.`DEPARTMENT_ID`
INNER JOIN `t_jobs` j
ON e.`JOB_ID` = j.job_id
INNER JOIN t_locations l
ON d.`LOCATION_ID` = l.location_id
INNER JOIN t_countries c
ON l.`COUNTRY_ID` = c.`COUNTRY_ID`
-- 后面的sql语法一样，该加条件加条件，该分组就分组，该限定就限定
-- WHERE d.`DEPARTMENT_ID` = 100
```



# 四、DML【增删改】

## 1、增加【insert】

- ==值列表 跟 插入的列名列表要一一对应==

```mysql
-- 语法
insert into 表名 (插入的列名列表) values (值列表);
```

```mysql
-- 向员工表中插入一条记录
INSERT INTO `t_employees`
	(`EMPLOYEE_ID`,`FIRST_NAME`,`LAST_NAME`,`EMAIL`,`SALARY`,`DEPARTMENT_ID`) 
VALUES (301, '三', '张', 'zhangsan@163.com', 9000, '10');
```

```mysql
mysql-- 向员工表中插入一条记录，插入的是全字段，就可以省略插入字段列表【不推荐】
INSERT INTO `t_departments`
VALUES (300, '研发部', 100, 1000);
```

```mysql
-- 语法
insert into 表名 (插入的列名列表) values (值列表1),(值列表2)...;
-- 批量插入
INSERT INTO `t_employees`
	(`EMPLOYEE_ID`,`FIRST_NAME`,`LAST_NAME`,`EMAIL`,`SALARY`,`DEPARTMENT_ID`) 
VALUES 
	(306, '三1', '张', 'zhangsan1@163.com', 9000, '10'),
	(302, '三2', '张', 'zhangsan2@163.com', 9100, '10'),
	(303, '三3', '张', 'zhangsan3@163.com', 9200, '20'),
	(304, '三4', '张', 'zhangsan4@163.com', 9300, '10'),
	(305, '三5', '张', 'zhangsan5@163.com', 9400, '10')
```

```mysql
-- 主键是整形并且是自增的情况下，插入记录时，可以不指定主键，主键会自增增长
INSERT INTO `t_hz_stu` (stu_no, stu_name, stu_score) VALUES ('java0007', '小七', 200.05);
```



## 2、删除【delete】

- 注意事项：务必要加上过滤条件，否则会造成很严重的后果【全表数据删除】

```mysql
-- 语法
delete from 表名 where 条件
```

```mysql
-- 删除
DELETE FROM `t_employees` WHERE `EMPLOYEE_ID` = 301
-- 删除入职时间是2000年之后的员工
DELETE FROM `t_employees` WHERE `HIRE_DATE` > '1999-12-31'
```



## 3、修改【update】

- 注意事项：务必要加上过滤条件，否则会造成很严重的后果【全表数据更新】

```mysql
-- 语法
update 表名 set 列名1=值1, 列名2=值2... where 条件
```

```mysql
-- 更新306号员工的信息，涨薪500，让他去20号部门
UPDATE
  `t_employees`
SET
  salary = salary + 500,
  department_id = '20'
WHERE EMPLOYEE_ID = 306
```



## 4、删除表中的数据

```mysql
-- 删除表中所有数据
DELETE FROM `t_employees`;

-- 删除表中所有的数据【把表删除，再按原先表结构创建一个新表】
TRUNCATE t_employees;
```



## 5、逻辑删除【伪删除】

- 公司中是很少使用delete。
- 逻辑删除，以一个标记性字段来表示当前记录是否被删除

```mysql
-- 逻辑删除
-- 删除2号学生
UPDATE `t_hz_stu` SET deleted = 1 WHERE stu_id = 2;
```



# 五、数据库表操作

## 1、数据库表字段【列】数据类型【掌握】

- MySQL数据库是一个关系型数据库
  - 关系型：二维表【有行有列】

### 1.1 数值类型

| 类型             | 大小                              | 范围（有符号）                                     | 范围（无符号）              | 用途           |
| ---------------- | --------------------------------- | -------------------------------------------------- | --------------------------- | -------------- |
| [INT]()          | 4 字节                            | (-2 147 483 648，2 147 483 647)                    | (0，4 294 967 295)          | 大整数值       |
| DOUBLE           | 8 字节                            | （-1.797E+308,-2.22E-308）                         | (0,2.22E-308,1.797E+308)    | 双精度浮点数值 |
| [DOUBLE(M,D)]()  | 8个字节，M表示长度，D表示小数位数 | 同上，受M和D的约束   DOUBLE(5,2) -999.99 到 999.99 | 同上，受M和D的约束          | 双精度浮点数值 |
| [DECIMAL(M,D)]() | DECIMAL(M,D)                      | 依赖于M和D的值，M最大值为65                        | 依赖于M和D的值，M最大值为65 | 小数值         |



### 1.2 日期类型

| 类型         | 大小 | 范围                                                         | 格式                | 用途                     |
| ------------ | :--- | ------------------------------------------------------------ | ------------------- | ------------------------ |
| [DATE]()     | 3    | 1000-01-01/9999-12-31                                        | YYYY-MM-DD          | 日期值                   |
| TIME         | 3    | '-838:59:59'/'838:59:59'                                     | HH:MM:SS            | 时间值或持续时间         |
| YEAR         | 1    | 1901/2155                                                    | YYYY                | 年份值                   |
| [DATETIME]() | 8    | 1000-01-01 00:00:00/9999-12-31 23:59:59                      | YYYY-MM-DD HH:MM:SS | 混合日期和时间值         |
| TIMESTAMP    | 4    | 1970-01-01 00:00:00/2038 结束时间是第 **2147483647** 秒北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYYMMDD HHMMSS     | 混合日期和时间值，时间戳 |

- date : 年月日，一般适用于生日等
- datetime：年月日时分秒，一般适用于更新时间、创建时间等



### 1.3 字符串类型

| 类型                        | 大小         | 用途                              |
| --------------------------- | ------------ | --------------------------------- |
| [CHAR]()                    | 0-255字符    | 定长字符串  char(10) 10个字符     |
| [VARCHAR]()                 | 0-65535 字节 | 变长字符串  varchar(10)  10个字符 |
| BLOB（binary large object） | 0-65535字节  | 二进制形式的长文本数据            |
| TEXT                        | 0-65535字节  | 长文本数据                        |

> char(18) ：表示定长18位字符串。如果存15位，实际存储也是18位
> varchar(18)：表示变长18位字符串。存15，实际存储也是15

- 大文本、大二进制数据【电影、音频、视频、图片、小说等等，都会存储到文件服务器上】
  - 将来如何找到文件服务器的1.avi电影呢。文件对应都是地址，只需要在数据库中保存该地址即可



## 2、创建表【掌握】

- 语法

```mysql
create table 表名(
	列名1 数据类型(长度) 约束...,
    列名2 数据类型(长度) 约束...,
    列名3 数据类型(长度) 约束...,
);
```

```mysql
-- 创建表
-- 主键：代表表中一行数据的唯一标识，具备唯一且非空的特征
CREATE TABLE tb_person(
    person_id INT(11),
    person_name VARCHAR(30),
    person_gender CHAR(1),
    person_birth DATE,
    person_create_time DATETIME,
    person_update_time DATETIME,
    person_deleted TINYINT(1),
    person_status TINYINT(1)
) charset=utf8;
```



## 3、修改表结构

- 语法

```mysql
alter table 表名 ....
```

### 3.1 增加一列

```mysql
alter table 表名 add 列名 数据类型(长度);
```

```mysql
-- 增加地址列
ALTER TABLE tb_person ADD person_address VARCHAR(60);
```



3.2 删除一列

```mysql
alter table 表名 drop 列名;
```

```mysql
ALTER TABLE tb_person DROP person_address;
```



3.3 修改数据类型

```mysql
alter table 表名 modify 原列名 新数据类型;
```

```mysql
ALTER TABLE tb_person MODIFY person_gender INT(1);
```



3.4 修改列名和数据类型

```mysql
alter table 表名 change 原列名 新列名 数据类型;
```

```mysql
ALTER TABLE tb_person CHANGE person_gender person_sex CHAR(1);
```



## 4、删除表

```mysql
drop table [IF EXISTS] 表名;
```

```mysql
-- 删除表
DROP TABLE IF EXISTS aaa;
```



## 5、查看表结构【掌握】

```mysql
desc 表名;
```



# 六、约束

## 1、分类

- 实体完整性约束
  - 表中的一行数据代表一个实体（entity），实体完整性的作用即是标识每一行数据不重复、实体唯一。
- 域完整性约束
  - 限制列的单元格的数据正确性。

## 2、主键约束

- 非空且唯一，是表示当前行记录唯一的一个标识
  - MySQL的主键有两种类型：整形【可以自增】、字符串

```mysql
CREATE TABLE tb_person1(
    person_id INT(11) PRIMARY KEY AUTO_INCREMENT,
    person_name VARCHAR(30),
    person_gender CHAR(1),
    person_birth DATE,
    person_create_time DATETIME,
    person_update_time DATETIME,
    person_deleted TINYINT(1),
    person_status TINYINT(1)
) CHARSET=utf8;
-- 主键是自增时，插入可以不用指定主键，因为自增增长，不会重复
INSERT INTO tb_person1 (person_name) VALUES ('AA');
INSERT INTO tb_person1 (person_id,person_name) VALUES (111,'AA');

CREATE TABLE tb_person2(
    person_id VARCHAR(36) PRIMARY KEY,
    person_name VARCHAR(30),
    person_gender CHAR(1),
    person_birth DATE,
    person_create_time DATETIME,
    person_update_time DATETIME,
    person_deleted TINYINT(1),
    person_status TINYINT(1)
) CHARSET=utf8;

INSERT INTO tb_person2 (person_id, person_name) VALUES (UUID(), 'AA');
```

## 3、唯一约束

- 唯一性，可以为空（只能一个空值）

## 4、非空约束

- 不能为空

## 5、默认约束

- 当没有给这个列赋值时，使用默认值

```mysql
-- 行内约束
CREATE TABLE tb_user(
	user_id INT(11) PRIMARY KEY AUTO_INCREMENT,
	username VARCHAR(30) UNIQUE,  #唯一
	`password` VARCHAR(60) NOT NULL DEFAULT '123123',  #非空,默认约束
	gender VARCHAR(1) DEFAULT '0'
) CHARSET=utf8;
```



## 6、外键约束【了解】

- 基于两个表之间是有关联关系的，那么如何表示两个表之间是有关系的呢。
  - 可以通过外键来建立这种关联关系
    - 主表：没有外键的表
    - 从表：有外键的表

```mysql
-- 创建主表
CREATE TABLE t_class(
	class_id INT(11) PRIMARY KEY AUTO_INCREMENT,
	class_name VARCHAR(30) NOT NULL
);

-- 创建从表，同时创建外键，必须先把主表创建好，才能创建从表
-- 如果创建了外键，那么这两个表就产生了强大的约束关系，所以在操作主表，一定要考虑到从表的数据。
-- 尤其是在删除主表数据时，如果从表有关系到主表，那么主表是不能删除的，会失败
CREATE TABLE t_student(
	student_id INT(11) PRIMARY KEY AUTO_INCREMENT,
	student_name VARCHAR(30) NOT NULL,
	t_class_id INT(11),
	# CONSTRAINT 外键名 FOREIGN KEY(外键列) REFERENCES 主表名(主键列) 
	CONSTRAINT fk_t_class_class_id FOREIGN KEY(t_class_id) REFERENCES t_class(class_id) 
);

-- 逻辑外键：没有建立外键，但是有外键意义的列存在
```



# 七、表与表之间关联关系

## 1、一对多

- 班级 对 学生
- 部门 对 员工
- 品牌 对 产品
- 公司 对 部门

## 2、多对一

- 学生 对 班级

## 3、一对一

==在有外键字段的表，设置外键字段唯一约束即可==

- 学生 对 班级
- 老公 对 老婆
- 人 跟 身份证
- 旅客 跟 护照
- 车 跟 车牌

## 4、多对多

==需要一个中间表，该中间表至少有两个字段，一个字段关联A表，另一个字段关联B表，这两个组合成一个联合主键==

- 老师 对 学生
- 程序员 对 项目

| 老师对学生【多对多关系】                                     |
| ------------------------------------------------------------ |
| <img src="pictures/image-20210608175118988.png" alt="image-20210608175118988" style="zoom:80%;" /> |



# 八、数据库三范式【了解】

- 目的：为了保证在创建表的时候，能够尽量的完美
  - 一个表：尽量不要出现冗余的列，尽量不要出现冗余的数据......

```mysql
CREATE TABLE t_student(
	student_id INT(11) PRIMARY KEY AUTO_INCREMENT,
	student_name VARCHAR(30) NOT NULL,
	class_id INT(11),
	class_name VARCHAR(30) NOT NULL
);
```

- 但是：现在已经很少有人完全遵循三范式设计数据库了。
  - 因为我们在一些业务场景下，为了提高应用的性能，方便我们快速得到数据，就会在某些表中设计一些冗余的字段



# 九、视图

## 1、概念

- 视图是一张虚拟表

## 2、特征

- 是根据原表的结构创建出来的
- 视图本身没有数据，数据来源于原表
- 修改视图中的数据，就会改变原表中的数据

## 3、作用

- 为了辅助查询
  - 屏蔽敏感数据
  - 主分同步

## 4、操作视图

### 4.1 创建视图【掌握】

- 语法

```mysql
create view 视图名 as select语句
```

```mysql
-- 创建视图
CREATE VIEW v_emp AS
SELECT
  `EMPLOYEE_ID`,
  `FIRST_NAME`,
  `LAST_NAME`,
  `EMAIL`,
  `PHONE_NUMBER`,
  `MANAGER_ID`,
  `DEPARTMENT_ID`
FROM
  `t_employees`;
```



### 4.2 修改视图

- 语法

```mysql
create or replace view 视图名 as select语句
```

```mysql
-- 创建或替换
CREATE OR REPLACE VIEW v_emp AS 
SELECT `EMPLOYEE_ID`,`FIRST_NAME`,`LAST_NAME`,`EMAIL`,`PHONE_NUMBER`,`SALARY`,`DEPARTMENT_ID` FROM `t_employees`;
```



### 4.3 查看视图【掌握】

- 跟操作表一模一样

```mysql
-- 通常用于查询，所以用select即可
SELECT * FROM v_emp WHERE DEPARTMENT_ID = 90;
```



### 4.4 删除视图

```mysql
-- 删除视图
DROP VIEW v_emp;
```



# 十、事务

## 1、概述

- 是一个原子性操作，是最小执行单元【整个操作是不可分割的】
- 是由一个或多个SQL组成，完成一个完整业务功能。这个业务功能中只要一步失败，那么整个业务就会失败。只有所有的步骤都成功，整个业务才算成功。

## 2、案例

- 转账

> 1. 原账户要存在
> 2. 原账户余额 >= 转账金额
> 3. 目标账户要存在
> 4. 原账户 - 转账金额   成功
> 5. 目标账户 + 转账金额   成功

- 实现sql

```mysql
-- 需求：a001 给 b001 转1分钱

-- 查询原账户是否存在？
SELECT * FROM t_account WHERE account_num = 'a001';
-- 判断余额是否够？ 将来可以在java代码中写if

-- 查询目标账户是否存在？
SELECT * FROM t_account WHERE account_num = 'b002';

-- 转钱
-- a001 - 1
UPDATE t_account SET account_balance = account_balance - 1 WHERE account_num = 'a001';
-- b002 + 1
UPDATE t_account SET account_balance = account_balanc + 1 WHERE account_num = 'b002';
```



## 3、事务特征

- ACID

> - [Atomicity(原子性)]()
>
> 　　　表示事务是一个完整的操作单元，不可分割。事务中所有操作要么全部成功，要么全部失败。
>
> - [Consistency(一致性)]()
>
>   ​	数据一致性。事务开始前和事务结束后，整个数据总量不变
>
> - [Isolation(隔离性)]()
>
> 　　　不同的事务之间是相互隔离的，互不影响。
>
> - [Durability(持久性)]()
>
> 　　　事务一旦提交，数据就会永久的写入数据库。



## 4、事务执行

- 分三步【要是12，要是13】

> 1. 开启事务【begin（START TRANSACTION）】
> 2. 提交事务【commit】
> 3. 回滚事务【rollback】

- mysql的事务默认是自动提交的
  - 先运行begin,然后进行操作
  - 然后按照实际情况
    - 一切顺利就再运行commit提交
    - 否则运行rollback回滚
- 完整的转账事务

```mysql
BEGIN; -- 设置事务为手动提交
-- 需求：a001 给 b001 转1分钱

-- 查询原账户是否存在？
SELECT * FROM t_account WHERE account_num = 'a001';
-- 判断余额是否够？ 将来可以在java代码中写if

-- 查询目标账户是否存在？
SELECT * FROM t_account WHERE account_num = 'b002';

-- 转钱
-- a001 - 1
UPDATE t_account SET account_balance = account_balance - 1 WHERE account_num = 'a001';
-- b002 + 1
UPDATE t_account SET account_balance = account_balance + 1 WHERE account_num = 'b002';

COMMIT;

ROLLBACK;
```



# 十一、权限管理【了解】

- 目前我们操作数据库，具备最大的权限，因为你是通过root用户登录的，而root是超级管理员，具备所有权限。

- 真实企业开发，是不可能让我们去使用root用户操作数据库的。

## 1、用户操作

- mysql对用户管理在名为mysql数据库的表名为user的表中进行管理

### 1.1 创建用户

- 同时需要指定密码

```mysql
CREATE USER 用户名 IDENTIFIED BY 密码;

-- 创建用户，必须有创建用户的权限
CREATE USER 'lucy' IDENTIFIED BY '123456';
```

### 1.2 删除用户

```mysql
drop user 用户名

DROP USER 'lucy';
```

## 2、权限操作

### 2.1 授权

```mysql
GRANT ALL ON 数据库.表 TO 用户名;

-- 授权
GRANT ALL ON `mybatisdb`.`t_employee` TO 'lucy';
```

```mysql
REVOKE ALL ON 数据库.表 FROM 用户名;

-- 撤权
REVOKE ALL ON `mybatisdb`.`t_employee` FROM 'lucy';
```



# 十二、SQL语言分类

> - 数据查询语言DQL（Data Query Language）：select、where、order by、group by、having 。
> - 数据定义语言DDL（Data Definition Language）：create、alter、drop。
> - 数据操作语言DML（Data Manipulation Language）：insert、update、delete 。
> - 事务处理语言TPL（Transaction Process Language）：begin、commit、rollback 。
> - 数据控制语言DCL（Data Control Language）：grant、revoke。



# 十三、综合练习

```mysql
CREATE TABLE IF NOT EXISTS USER(
	userID INT PRIMARY KEY AUTO_INCREMENT,
	username VARCHAR(20) NOT NULL,
	PASSWORD VARCHAR(18) NOT NULL,
	address VARCHAR(100),
	phone VARCHAR(11)
);

CREATE TABLE IF NOT EXISTS category(
	cid VARCHAR(32) PRIMARY KEY,
	cname VARBINARY(100) NOT NULL
);

CREATE TABLE IF NOT EXISTS products(
	pid VARCHAR(32) PRIMARY KEY,
	NAME VARCHAR(40),
	price DOUBLE(7,2),
	category_id VARCHAR(32),
	CONSTRAINT fk_products_category_id FOREIGN KEY(category_id) REFERENCES category(cid)
);

CREATE TABLE IF NOT EXISTS orders(
	oid VARCHAR(32) PRIMARY KEY,
	totalprice DOUBLE(12,2),
	userId INT,
	CONSTRAINT fk_order_userId FOREIGN KEY(userId) REFERENCES USER(userId)
);


CREATE TABLE IF NOT EXISTS orderitem(
	oid VARCHAR(32),
	pid VARCHAR(32),
	num INT,
	PRIMARY KEY(oid,pid),
	CONSTRAINT fk_orderitem_oid FOREIGN KEY(oid) REFERENCES orders(oid),
	CONSTRAINT fk_orderitem_pid FOREIGN KEY(pid) REFERENCES products(pid)
);




```

