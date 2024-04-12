#### 基础使用

```sql
from pymysql import Connect
#连接数据库
conn=Connect(
    host="localhost",
    port=3306,
    user='root',
    passwd='20021110lEIgE'
)
# print(conn.get_host_info())
#执行非查询性质sql语句
#获取游标对象
cursor=conn.cursor()
conn.select_db('world')#选择数据库
#执行语句
# cursor.execute("create table demo2(id int);")
#查询性质，获取查询结果
cursor.execute("select * from demo")
#获取结果
resule=cursor.fetchall()
for row in resule:
    print(row)
conn.close()
```

![image-20240124222646150](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240124222646150.png)

#### 数据插入

要产生数据更改需要手动确认

通过.commit对象确认

也可以在连接时设置自动提交

![image-20240124223025388](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240124223025388.png)

#### 例

