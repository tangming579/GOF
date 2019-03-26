C#：

```c#
//双重锁定
class Singleton
{
    private static Singleton instance;
    private static readonly object syncRoot = new object();
    private Singleton(){}
    public static Singleton GetInstance()
    {
        if(instance == null)
        {
         	lock(syncRoot)
            {
                if(instance == null)
                {
                	instance = new Singleton();    
                }
            }   
        }
        return instance;
    }
}
//静态初始化
public sealed class Singleton
{
    private static readonly Signleton instance = new Singleton();
    private Singleton(){}
    public static Singleton GetInstance()
    {
        return instance;
    }
}
```

Java：

```java
//静态初始化
public class MySingleton {
	
	//内部类
	private static class MySingletonHandler{
		private static MySingleton instance = new MySingleton();
	} 
	
	private MySingleton(){}
	 
	public static MySingleton getInstance() { 
		return MySingletonHandler.instance;
	}
}
```

