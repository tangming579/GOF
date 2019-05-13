## 工厂方法模式

**定义**

定义一个用于创建对象的接口，让子类决定实例化哪一个类。工厂方法使一个类的实例化延迟到其子类。

**UML**

<div>
    <image src="../img/factory.png"></image>
</div>



C#：

```c#
interface IFactory
{
    Operation CreateOpertion()
    {
        
    }
}
class AddFactory : IFactory
{
	public Operation CreateOperation()
    {
    	return new AddOperation();
    }
}
class SubFactory : IFactory
{
	public Operation CreateOperation()
    {
    	return new SubOperation();
    }
}
class Main()
{
    IFactory factory = new AddFacotry();
    Operation oper = factory.CreateOperation();
    oper.Num1 = 1;
    oper.Num2 = 3;
    double = oper.GetResult();
}
```



简单工厂模式的优点在于工厂类中包含了必要的判断逻辑，根据客户端的选择条件动态实例化相关类。对于客户端来说，去除了与具体产品的依赖。工厂方法实现时，客户端需要决定实例化哪一个工厂来实现运算类，选择判断的问题还是存在的。也就是说，工厂方法把简单工厂的内部判断逻辑移动到了客户端代码来进行，想要加功能，本来是改工厂类的，而现在是修改客户端。