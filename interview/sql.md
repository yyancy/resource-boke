# sql面试题
## 1.常见sql面试题

## 1.用一条SQL 语句 查询出每门课都大于80 分的学生姓名
```sql
 name   kecheng   fenshu
 张三    语文        81
 张三     数学       75
 李四     语文       76
 李四     数学       90
 王五     语文       81
 王五     数学       100
 王五     英语       90

select name 
from table 
group by name 
having min(fenshu)>80  

select distinct name 
from table 
where name not in (
 select distinct name 
 from table 
 where fenshu<=80)
```
## 删除除了自动编号不同, 其他都相同的学生冗余信息
2. 学生表 如下:
```sql
自动编号   学号   姓名 课程编号 课程名称 分数
1        2005001 张三 0001      数学    69
2        2005002 李四 0001      数学    89
3        2005001 张三 0001      数学    69

delete tablename 
where 自动编号 not in(
 select min( 自动编号) 
 from tablename 
 group by学号, 姓名, 课程编号, 课程名称, 分数)
```
## 用一条sql 语句显示所有可能的比赛组合.
一个叫 team 的表，里面只有一个字段name, 一共有4 条纪录，分别是a,b,c,d, 对应四个球对，现在四个球对进行比赛，用一条sql 语句显示所有可能的比赛组合.
```sql
select a.name,b.name 
from team a,team b 
where a.name < b.name
```
## .面试题：怎么把这样一个表儿
```sql
year   month amount
1991   1     1.1
1991   2     1.2
1991   3     1.3
1991   4     1.4
1992   1     2.1
1992   2     2.2
1992   3     2.3
1992   4     2.4  

-- 查成这样一个结果
year m1   m2   m3   m4
1991 1.1  1.2  1.3  1.4
1992 2.1  2.2  2.3  2.4 

select year,
(select amount from aaa a where month=1 and a.year=aaa.year) m1,
(select amount from aaa a where month=2 and a.year=aaa.year) m2,
(select amount from aaa a where month=3 and a.year=aaa.year) m3,
(select amount from aaa a where month=4 and a.year=aaa.year) m4
from aaa group by year
```
## mysql 复制表
1. 只复制表结构到新表
```sql
1 CREATE TABLE 新表 SELECT * FROM 旧表 WHERE 1=2;

2 CREATE TABLE 新表 LIKE 旧表 ;
```
注意上面两种方式，前一种方式是不会复制时的主键类型和自增方式是不会复制过去的，而后一种方式是把旧表的所有字段类型都复制到新表。

2. 复制表结构及数据到新表
```sql
CREATE TABLE 新表 SELECT * FROM 旧表
```
3. 复制旧表的数据到新表(假设两个表结构一样) 
```sql
INSERT INTO 新表 SELECT * FROM 旧表
```
4. 复制旧表的数据到新表(假设两个表结构不一样)
```sql 
INSERT INTO 新表(字段1,字段2,.......) SELECT 字段1,字段2,...... FROM 旧表
```






