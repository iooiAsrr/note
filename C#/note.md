## ?运算符

```csharp
//三目运算符
bool ? "true":"fasue"
bool ? "true": bool ? "true":"fasue"
//可为空的值类型Nullable value types
int? a=null;
int?[] arr1;
int[]? arr2;//可为空的引用类型
int?[]? arr3;
List<int>? lst1;
List<int?>? lst2;
//?.空应用传播
object?.child?.Name;
if(object==null)return;
if(child==null)retuen;
//??空合并
int GetValue(){
    int?x=null;
    return x??1;//如果x为空则赋值x=1；
    
    int?y=null;
    return x??=1;
}
```

## override和new

```c#
//override子类无法直接调用父类方法,反射也无法调用只能用base.调用
//new不影响父类只是隐藏
//override会真正覆盖父类方法，而new只是进行隐藏
BaseClass ob = new ObjectClass();
```

#### 如何选择

1. 想要覆盖某个类型的方法，但并不是virtual时候，需要考虑用new

## readonly和const

```c#
//都可以声明常量,无法修改
//readonly可以在构造函数初始化和修改，const必须在声明进行初始化
//readonly只能用于声明类的字段，const还可以声明局部常量
//值类型数值无法修改，引用类型引用指向的对象不能发生变化
//readonly是语法，const则本质是字面常量，一旦初始化无法修改,本质是静态的
class Myclass{
    public readonly int value =10;
    //构造函数可以修改，也可以通过反射修改
    Myclass{
    value=20;    
    }
}
//readonly的初始化不必是编译时常量，const必须是字面常量
//readonly struct & ref readonly method
//结构体内所有成员初始化后无法更改
 readonly struct Mycircle{
     public readonly int Field=10;
     public string ClassName{get;init;}=nameof(MyCircle);//可以不写set或者写init
 }
//readonly members,不会对本地属性字段进行修改,只能用于struct类型不能用于类类型
// const string + string interpolation
public const string A="a";
public const string B="b";
public const string C=$"{A},{B}";
```









