<img src="https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240124171433924.png" alt="image-20240124171433924" style="zoom:50%;" />

#### 命令

```shell
show databases;#查看有哪些数据库
use 数据库名 #使用某个数据库
show tables#查看数据库内有哪些表
exit #退出命令环境
```

#### 基础语法

- 不区分大小写
- 可以单行或者多行书写以分号结尾 `;`
- 单行注释： -- 注释   或者 # 注释
- 多行注释： /*  注释  */

#### 数据定义:DDL(Data Definition Language)

- 库的创建删除，表的创建删除

  ```sql
  #查看数据库
  show database;
  #用数据库
  use 数据库名;
  #创建数据库，中括号可选
  create database 数据库名 [charset UTF8];
  #删除数据库
  drop database 数据库名
  #查看当前使用的数据库
  select database();
  ```

  ```sql
  #查看有哪些表
  show tables;
  #创建表
  creat table 表名(
  		列名称 列类型，
  		列名称 列类型，
  		......

  	);
                  /*int 整数
                  float 浮点数
                  varchar(长度) 文本，长度为数字，做最大长度限制，
                  date 日期类型
                  timestamp 时间戳类型
                  */
  #删除表
  drop table 表名称；
  drop table if exists 表名称；
  ```

#### 数据操纵:DML(Data Manipulation Language)

- 新增数据，删除数据，修改数据等

  ```sql
  #插入insert into 表[(列1，列2,...)] values(值1,值2,...)[,(值1,值2,...)...,(值1,值2,...)]
  #例
  use world;
  create table demo(
  	id int,
  	name varchar(10),
  	age int
  );
  insert into demo (id) values(1),(299324),(3);
  insert into demo [(id,name,age)] values(1,'小明',14),(2,'在周杰伦',14);
  #数据删除
  delete from 表名  [where 条件判断]
  #例
  delete from demo where id <=6
  #数据更新
  update 表名 set 列=值  [where 条件判断]
  #例
  update demp set id=666 where age=14
  ```

#### 数据控制:DCL(Data Control Language)

- 新增用户，删除用户，密码修改，权限管理等

#### 数据查询DQL(Data Query Language)

- 基于需求查询和计算数据

```sql
#从表中,选择某些列进行展示
select 字段列表|* from 表 [where 条件判断]
#例
select id,name from demo 
```

```sql
#分组聚合
select 字段|聚合函数 from 表 [where 条件] group by 列
/*聚合函数
sum(列) 求和
avg(列) 求平均值
min(列) 求最小值
max(列) 求最大值
count(列|*) 求数量
*/
#例
select age,sum(age),min(age),max(age) from demo group by age;
```

```sql
#结果排序
select 列|聚合函数|* from 表
where ...
group by ...
order by ... [asc|desc]#指定列排序,asc从小到大,desc从大到小
limit n[,m] #使用limit关键字进行数量现在或者分页显示
#例
select * from demo limit 5;#限制5条
select * from demo limit 10,5#跳过10条从11条开始输出5条
```

![image-20240124220545935](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240124220545935.png)
