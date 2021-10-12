# Day 35笔记

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
* MySQL是一个**关系型数据库管理系统****，**由瑞典MySQL AB 公司开发，属于 [Oracle](https://baike.baidu.com/item/Oracle) 旗下产品。
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

* ```
  between A and B
  
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary>=6000 and salary<=10000 ORDER BY salary ASC;
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary<=10000 and salary>=6000 ORDER BY salary ASC;
  
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary BETWEEN 6000 and 10000 ORDER BY salary ASC;
  SELECT t_employees.first_name,salary FROM t_employees WHERE salary BETWEEN 10000 and 6000 ORDER BY salary ASC;
  ```

### 8.5 非空判断

```
is null
SELECT EMPLOYEE_ID,first_name,COMMISSION_PCT FROM t_employees where COMMISSION_PCT is null;

```

```
is not null
SELECT EMPLOYEE_ID,first_name,COMMISSION_PCT FROM t_employees where COMMISSION_PCT is not null;
```

### 8.6 枚举查询

```
in(数据1,数据2,数据3...)
SELECT EMPLOYEE_ID,FIRST_NAME,DEPARTMENT_ID from t_employees where DEPARTMENT_ID in (60,90,110);
```

### 8.7 模糊查询

* 使用关键字like 

* ```
  _	任意一个字符
  	SELECT EMPLOYEE_ID,FIRST_NAME,DEPARTMENT_ID from t_employees where EMPLOYEE_ID like '11_';
  
  %	任意个数字符
  	SELECT EMPLOYEE_ID,FIRST_NAME,hire_date from t_employees where hire_date like '1999%';
  ```

  