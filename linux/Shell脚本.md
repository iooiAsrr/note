### Corn定时任务

![image-20240226115337841](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240226115337841.png)









### 概念

![image-20240218133349060](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218133349060.png)

#### 基础用法

![image-20240218133410175](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218133410175.png)

![image-20240218134020080](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218134020080.png)

 

![image-20240218135554093](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218135554093.png)

![image-20240218141145173](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218141145173.png)

![image-20240218142039679](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218142039679.png)

![image-20240218141021818](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218141021818.png)



![image-20240218144211236](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218144211236.png)

![image-20240218144138469](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218144138469.png)

### 脚本编写







![image-20240218154829559](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218154829559.png)

![image-20240218154910334](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218154910334.png)





![image-20240218155530247](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218155530247.png)

![image-20240218160126080](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218160126080.png)

![image-20240218160151813](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218160151813.png)

![image-20240218160910595](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218160910595.png)

![image-20240218161103549](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240218161103549.png)

### 分支与循环

![image-20240226104613324](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240226104613324.png)

![image-20240226104640941](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240226104640941.png)

```sh
case 
...
esac
```



##### for循环

```sh
sum=0
for sum in 1 2 3 4 5 6 7 8 9 10; do
	#sum= `expr @sum + $i`
	#let sum=sum+i
	#let sum+=i
	((sum+=i))
done
echo "$sum"
```





![image-20240226105956190](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240226105956190.png)





### 函数和数组

![image-20240226112054366](https://raw.githubusercontent.com/iooiAsrr/picture/main/Typora/image-20240226112054366.png)