- 注释:通过#号定义
- 多行注释:通过一对三个引号来定义"""注释内容"""

#### 变量

- 格式
  - 变量名=变量值
- 特征:可以改变值

#### 数据类型

- 整型 int 
- string 字符串类型
- float 浮点类型
- type()查看数据类型

#### 数据类型转换

- 格式 int(x) 将x转换为整数

#### 标识符

- 变量,方法,类的名字
- 英文,中文,数字,下划线
- 不可以数字开头
- 区分大小写
- 不能使用关键字

#### 运算符

###### 常见算数

- 加减乘除
- // 取整数
- % 取余
- ** 指数

###### 赋值运算符

+=,-=,*=,/=,//=,%=,**=

#### 字符串

- 单引号双引号三引号
- 三引号若不用变量接收就是注释

#### 字符串的拼接

- 通过+号来拼接包括变量

#### 字符串的格式化

- ```python
  num=str("hello"+" world")
  num2=str("iamasrr")
  tel = 123342342
  print("num+num2+tel %s" %(tel))
  ```

- ```python
  num1=20
  num2=34
  message="第一个数是%s,第二个数是%s"%(num1,num2)
  print(message)
  ```

- %表示我要占位

- s表示:将变量变成字符串放入占位的地方

- d:整型

- f:浮点

#### 字符串格式化精度

- m.n 

- 例 %5.3f:表示宽度控制为5,小数点精度设置为2

- .4f

- ```python
  num1=20.32432452
  message="数是%6.5f" %(num1)
  print(message)
  ```

#### 字符串快速格式化

- 格式:`f"{占位}"`

- 不限数据类型,不做精度控制

- ```python
  num1=20.32432452
  num2=30
  message=f"数是{num1}第二个数是{num2}"
  print(message)
  ```

- 

#### 对表达式进行格式化

- 代码语句,有明确结果

- ```python
  print(f"第一: {2+4}")
  ```







