# LINQ

- 语言集成查询(Language-Integrated Query)

### 用途

- .NET原生集合(List,Array,Dictionary,etc)
- SQL数据库(搭配ORM)
- XML文档
- JSON文档(Newtonsoft_Json)

### 常用功能

- 排序，筛选，选择
- 分组，聚合，合并
- 最大值，最小值，求和，求平均，求数量

### 两种形式

- 查询表达式query expression结尾必须是group或者select
- 链式表达式chained expression

  - ```c#
    var lst = new List<int>{1,2,3,5,8,4,7,9}
    
    //even,>= 2 and sort 
    //传统命令式编程
    var res = new List<int>();
    foreach(var n in lst)
        if(n%2==0&&n>=2)
            res.Add(n);
    res.Sort();
    res.Dump();
    //查询表达式
    var res =
        from n in lst
        where n%2==0
        orderby n
        select n;//表示语句完结
    res.Dump();
    //链式表达式
    var res = lst
        //筛选每一个为n
        .Where(n=>n%2==0&&n>=2)
        .OrderBy(n=>n)
    res.Dump();
    ```

    ```c#
    var arr1 = new int[] { 1, 2, 3, 31, 4, 5, 6 };
    var arr2 = new int[] { 2, 2, 3, 3, 42, 5, 69 };
    
    //var res1 = arr1.Intersect(arr2).Dump();
    
    var res1 =
        from n in arr1
        where arr2.Contains(n)
        select n;
    res1.Dump();
    ```

    ```csharp
    var rnd = new Random(1232);
    var arr = Enumerable.Range(0, 300).Select(_ => rnd.Next(30));
    
    var res = arr
        .GroupBy(x => x)
        //.Select(g => new { g.Key, Count = g.Count })
        .ToDictionary(g=>g.Key,g=>g.Count())
        .Dump;
    
    var res =
        from x in arr
        group x by x into g
        select new {g.key,Count=g.Count()};
    res.Dump();
    ```
    

### 查询表达式的延迟执行与消耗

1. 延迟执行

   - ```c#
     var query=list.Select(x=>{
     	Thread.Sleep(1000);
     	return x*x;
     });
     "finish".Dump();//不执行上面代码
     query.Dump();//执行上述代码
     ```

     

- 遍历

- ToList(),ToArray(),ToDictionary()

- Count(),Min(),Max(),Sum()

- LINQ不仅仅是可枚举类型的拓展方法

  - IENmuerable

  - IOrderedEnumerable

  - IQueryable

  - ParallelQuery

  - ```c#
    var arr = Enumerable
    	.Range(1,10);
    	.ToArray()
    	.AsParallel()
    	.AsOrdered()
    	.Select(x=>{
    		Thread.Sleep(500)
    		return x*x;
    	})
    	.AsSequential()
    	.Dump();
    ```

    ```c#
    //展平
    var mat = new int[] []{
        new[]{1,2,3,4,5},
        new[]{5,3,2,5,6},
        new[]{7,6,8,6,4}
    };
    
    //var res=
    //    from row in mat
    //    from n in row
    //    select n;
    //res.ToArray().Dump();
    
    var res=mat
        .SelectMany(n=>n);
    res.ToArray().Dump();
    ```

    ```c#
    //字母频率
    var words = new string[]{
        "jean","yang","wang","tom","jean","zhang","yang","tom","tom"
    };
    //查询表达式
    var quer =
        from w in words
        from c in w
        group c by c into g
        select new{g.Key,Count=g.Count()} into a
        orderby a.Count descending
        select a;
    //链式表达式
    var query=words
        .SelectMany(c=>c)
        .GroupBy(c=>c)
        .Select(g=>new{g.Key,Count=g.Count})
        .OrderBy(g=>g.Count);
    query.Dump();
    ```

### 常见错误
- <img src="./assets/image-20241027161747339.png" alt="image-20241027161747339" style="zoom:50%;" />

- <img src="./assets/image-20241027162134511.png" alt="image-20241027162134511" style="zoom:50%;" />

### 反射和特性
在 C# 中，**反射**（Reflection）和**特性**（Attributes）是两个重要的概念，常用于动态获取类型信息和为程序元素添加元数据。以下是它们的详细介绍和示例。

### 1. 反射（Reflection）
**反射**允许程序在运行时检查和操作类型信息，包括类、方法、属性等。可以通过反射获取类的类型信息，并访问其成员（例如方法和属性），即使在编译时不清楚类型。

#### 反射的使用场景
- **插件系统**：在不知道具体类型的情况下加载和使用外部程序集中的类型。
- **序列化和反序列化**：通过反射可以将对象的属性和值进行动态序列化。
- **动态调用**：运行时调用特定方法，或者获取/设置属性值。

#### 示例代码
```csharp
using System;
using System.Reflection;

public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }

    public void SayHello()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {Age} years old.");
    }
}

class Program
{
    static void Main()
    {
        // 1. 获取类型信息
        Type personType = typeof(Person);

        // 2. 创建对象
        object personInstance = Activator.CreateInstance(personType);

        // 3. 获取并设置属性值
        PropertyInfo nameProperty = personType.GetProperty("Name");
        PropertyInfo ageProperty = personType.GetProperty("Age");

        nameProperty.SetValue(personInstance, "John");
        ageProperty.SetValue(personInstance, 30);

        // 4. 调用方法
        MethodInfo sayHelloMethod = personType.GetMethod("SayHello");
        sayHelloMethod.Invoke(personInstance, null); // 输出: Hello, my name is John and I am 30 years old.
    }
}
```

在上面的示例中，通过 `Activator.CreateInstance` 创建 `Person` 类的实例，使用反射获取属性 `Name` 和 `Age`，并动态设置它们的值，最后调用 `SayHello` 方法。

### 2. 特性（Attributes）
**特性**是用于向代码元素（类、方法、属性等）添加额外信息的注解。特性允许在编译时或者运行时获取元数据，用于控制代码行为、生成文档或进行验证等。

#### 自定义特性示例
首先，我们定义一个自定义特性 `DeveloperInfoAttribute`，用于存储开发人员的姓名和版本信息：

```csharp
using System;

// 定义自定义特性
[AttributeUsage(AttributeTargets.Class | AttributeTargets.Method, AllowMultiple = true)]
public class DeveloperInfoAttribute : Attribute
{
    public string Developer { get; }
    public string Version { get; }

    public DeveloperInfoAttribute(string developer, string version)
    {
        Developer = developer;
        Version = version;
    }
}

// 应用特性
[DeveloperInfo("Alice", "1.0")]
[DeveloperInfo("Bob", "1.1")]
public class SampleClass
{
    [DeveloperInfo("Alice", "1.0")]
    public void SampleMethod()
    {
        Console.WriteLine("This is a sample method.");
    }
}
```

#### 使用反射读取特性
通过反射，我们可以读取特性的信息。

```csharp
class Program
{
    static void Main()
    {
        // 获取类型上的特性
        Type type = typeof(SampleClass);
        var attributes = type.GetCustomAttributes(typeof(DeveloperInfoAttribute), false);

        foreach (DeveloperInfoAttribute attr in attributes)
        {
            Console.WriteLine($"Class Developer: {attr.Developer}, Version: {attr.Version}");
        }

        // 获取方法上的特性
        var methodInfo = type.GetMethod("SampleMethod");
        var methodAttributes = methodInfo.GetCustomAttributes(typeof(DeveloperInfoAttribute), false);

        foreach (DeveloperInfoAttribute attr in methodAttributes)
        {
            Console.WriteLine($"Method Developer: {attr.Developer}, Version: {attr.Version}");
        }
    }
}
```

#### 输出结果：
```
Class Developer: Alice, Version: 1.0
Class Developer: Bob, Version: 1.1
Method Developer: Alice, Version: 1.0
```

### 总结
- **反射**：允许在运行时获取和操作类型信息，适合需要动态执行代码或插件系统。
- **特性**：用于为代码元素添加额外信息，通常结合反射在运行时读取特性数据，从而控制程序行为或提供元数据。

```c#
//特性忽略属性输出
[JsonIgnore]
private bool true;
//反射
//反射获取属性标记的特性
```

### 自定义特性:Attribute

```c#
//继承Attribute
//定义特性使用限制,限制到属性和类
用特性修饰特性[AttributeUsage(AttributeTargets.Protertype | AttributeTargets.Class)]
```

