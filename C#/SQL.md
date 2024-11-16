# 增

```sql
CREATE DATABASE 数据库名
USE 数据库名
CREATE TABLE 表名(
 	id INT not null AUTO_INCREMENT PRIMARY KEY，-- 不为空，自动递增数字,主键
 	name nvarchar(10) null，-- 可以为空
 	age int not null
);
```

###### 插入数据

```sqL
-- INSERT INTO 表格名/数据库名.表名 (列名1，列名2，列名3) VALUES(数值1，数值2，数值3);
insert into student/class.student (id,name,age) values(4,'Tom',20);
insert into student values(4,'Tom',20);
insert into student values(default,'Ton',null)
```

###### 改变表格

```sql
-- ALTER TABLE 数据库名.表格名
-- ADD 列名 数据类型 默认条件
alter table class.student add name nvarchar not null;
-- UPDATE 数据库名.表名 SET 值 WHERE 条件;
update class.student set age = 21 where name = 'Jean';
```



# 删
```sql
-- DELETE FROM 数据库名.表明
-- WHERE 条件
delete from class.student;
where id = 3;

-- 删除整个表格或者数据库
-- DROP TABLE 数据库名.表格名
-- DROP DATABASE 数据库名
drop table studnet;
drop database class;
```
# 改

```sql
-- ALTER TABLE 数据库名.表名
-- ADD 列名 数据类型 默认条件
alter table class.student;
add name int null;

-- UPDATE 数据库表明，表格名
-- SET 值
-- WHERE 条件
update class.student
set age = 20
where id = 3;
```
# 查

```sql
-- SELECT * FROM 表格名;查看全部内容
-- SELECT 列名1,列名2 FROM 表格名; 查看某列
select * from student;
select name,age,id from student;

-- SELECT DISTINCT * FROM 表格名;数据不重复
select distinct age from student;

-- 排序
-- SELECT * FROM 表格名 ORDER BY 列名 ASC/DESC;
select * from student order by age asc;

-- 过滤
-- SELECT * FROM 表格名 WHERE 条件 ORDER BY 列名 ASC(default)/DESC;
select * from student
where age >= 20 and name != 'Tom'
order by id asc;
-- 取反加NOT
where not age >= 20 and name !='Tom'
-- 取范围 BETWEEN AND
where age between 23 and 30;
-- 用IN表示字符范围
where name in ('Tom','Jean')
-- 用LIKE 进行模糊查询,以某开头以某结尾，_表示任意字符
where name like 'W%'
where name like '%g'
where name like '__g%'
```

<img src="./assets/image-20241029141143866.png" alt="image-20241029141143866" style="zoom:25%;" /><img src="./assets/image-20241029141246089.png" alt="image-20241029141246089" style="zoom:25%;" />

###### 合并表格

```sql
-- INNER JOIN ON 条件 (交集)
select * from student inner join teacher on student.id = teacher.id
-- UNION(并集合并列去重) UNION ALL(不去重)
select id from student union select id from teacher
-- LEFT JOIN(左连接，左边保留完整合并右边符合条件的数据)
select * from student left join teacher on student.id = teacher.id
-- RIGHT JOIN(右连接，右边保留完整合并左边符合条件的数据)
select * from student right join teacher on student.id = teacher.id
-- 语句简写
select * from student as stu
right join teacher as th
on stu.id = th.id
```

<img src="./assets/image-20241030193446696.png" alt="image-20241030193446696" style="zoom:25%;" /><img src="./assets/image-20241030193341199.png" alt="image-20241030193341199" style="zoom:25%;" /><img src="./assets/image-20241030193410678.png" alt="image-20241030193410678" style="zoom:25%;" />
