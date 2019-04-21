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

