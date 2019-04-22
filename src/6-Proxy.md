## 代理模式

**定义**

为其他对象提供一种代理以控制对这个对象的访问

**UML**

<div>
    <image src="../img/proxy.png"></image>
</div>

C#：

```c#
//Subject类，定义了RealSubject和Proxy的共用接口
abstract class Subject
{
    public astract void Request();
}

class RealSubject:Subject
{
	public override void Request()
    {
    	Console.WriteLine("真实的请求");
    }
}
class Proxy:Subject
{
	RealSubject realSubject;
	public override void Request()
    {
    	if(realSubject==null)
    		realSubject=new RealSubject();
    	realSubject.Request();
    }
}
```

Java：

```java
public interface Subject{
    void Request();
}
public class RealSubject implements Subject{
    @Override
    public void Request(){
        
    }
}
public class ProxySubject implements Subject{
    private RealSubject realSubject;
    @Override
    public void Request{
        if(realSubject==null)
            realSubject=new RealSubject();
        realSubject.Request();
    }
}
```

### C#中的代理模式

1. 远程代理：为一个对象在不同的地址空间提供局部代表，这样可以隐藏一个对象存在于不同地址的事实，例如：.NET中的WebService引用添加

2. 虚拟代理：根据需要创建开销较大的对象。通过它来存放实例化需要很长时间的真实对象
3. 安全代理：用来控制真实对象访问时的权限
4. 智能指引：指当调用真实的对象时，代理处理另外一些事

### JDK自带的动态代理

-  java.lang.reflect.Proxy:生成动态代理类和对象；
-  java.lang.reflect.InvocationHandler（处理器接口）：可以通过invoke方法实现

对真实角色的代理访问。

[Cglib](http://www.runoob.com/w3cnote/cglibcode-generation-library-intro.html) 动态代理是针对代理的类, 动态生成一个子类, 然后子类覆盖代理类中的方法, 如果是private或是final类修饰的方法,则不会被重写。