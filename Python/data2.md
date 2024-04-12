#### 获取键盘输入

- input语句

- 格式:input()

- ```python
  name=input("君の名字是:")
  print("Hello,",type(name))
  #默认接收字符串,需要类型转换
  ```

- ```python
  name=input("您的账户名称:")
  passwd=int(input("请输入您的密码"))
  print("您的账户是%s,您的密码锁%d"%(name,passwd))
  print(type(passwd))
  ```

#### 判断语句

- 布尔类型
- true or false



#### If-Else语句

- 基本格式

- ```python
  num1=29
  num2=33
  if num1>num2:
      print("num1 is greater than num2")
      print("num2 is hahah")
      ......
  else:
      print("num1 is less than num2")
      ......
  ```

- 案列

- ```python
  age=int(input("欢迎来到游乐场您的年龄是:"))
  if age>=18:
      print("您已成年,游玩需要10元")
      ......
  else:
      print("小屁孩,滚出去")
      ......
  ```

#### if-elif-else

- ```python
  age=int(input("欢迎来到游乐场您的年龄是:"))
  if age>=18:
      print("您已成年,游玩需要10元")
      ......
  elif age>12 :
       print("你干嘛诶呦")   
  else:
      print("小屁孩,滚出去")
      ......
  ```

  