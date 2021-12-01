---
title: MySQL：结构化查询语言
date: 2021-12-01 10:49:07
categories:
- MySQL
tags:
- MySQL
- 面试
---
###### 表中记录清空
delete from 表名
###### 查看数据库
show databases；
###### 使用数据库
use  库名；
###### 查看有哪些表
show tables；
###### 查看表中所有数据
select * from 表名；
###### 查看表结构
desc 表名；

###### sql语句的执行顺序
sql语句的执行过程是：from --> where --> group by --> having -->  order by --> select -->limit
###### 表中增加字段
alter table 表名 add 字段名称 类型；  
###### 表中修改字段
alter table 表名 modify 字段名称 类型；
###### 修改表数据
update 表名 set  字段 = 数据 where 条件；

###### order by 字段
升序：asc (可省略)
降序：desc
###### having和where的用法区别
1.having只能用在group by之后，对分组后的结果进行筛选(即使用having的前提条件是分组)。
2.where肯定在group by 之前。
3.where后的条件表达式里不允许使用聚合函数，而having可以。
###### 例题
1、查询表中重复数据删除至一条
select * from t1 where name in(select name from t1 group by name HAVING count(*)>1)