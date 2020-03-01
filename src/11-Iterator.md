## 迭代器模式

**定义**

提供了一种方法顺序访问一个聚合对象中各个元素，而又不暴露该对象的内部表示。

```csharp
//调用代码：
static void Main()
{
    IList<string> a = new List<string>();
    a.Add("a");
    a.Add("b");
    a.Add("c");
    
    foreach(string item in a)
    {
        Console.WriteLine(item);
    }
}
//内部实现方式：
IEnumerator<string> e = a.GetEnumerator();
while(e.MoveNext())
{
	Console.WriteLine(e.Current);    
}

```

迭代器模式就是分离了集合对象的遍历行为，抽象了一个迭代器类来负责，这样既可以做到不暴露集合的内部结构，又可让外部代码透明地访问集合内部数据。