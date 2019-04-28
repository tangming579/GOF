## 模板方法模式

**定义**

定义一个操作中的算法骨架，而将一些步骤延迟到子类中。模板方法使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。

**UML**

<div>
    <image src="../img/template.png"></image>
</div>



C#：

```c#
abstract class AbstractClass
{
    public abstract void PrimitiveOperation1();
    public abstract void PrimitiveOperation2();    
    public void TemplateMethod()
    {
        PirmitiveOperation1();
        primitiveOperation2();
        Console.WriteLine("");
    }
}
class ConcreteClassA : AbstractClass
{
	public override void PrimitiveOperation1()
    {
    	Conslole.WriteLine("具体类A方法1实现")
    }
    public override void PrimitiveOperation2()
    {
    	Conslole.WriteLine("具体类A方法2实现")
    }
}
class ConcreteClassB : AbstractClass
{
	public override void PrimitiveOperation1()
    {
    	Conslole.WriteLine("具体类B方法1实现")
    }
    public override void PrimitiveOperation2()
    {
    	Conslole.WriteLine("具体类B方法2实现")
    }
}
static void Main(string[] args)
{
    AbstractClass c;
    c = new ConcreteClassA();
    c.TemplateMethod();
    
    c = new ConcreteClassB();
    c.TemplateMethod();
}
```

Java：

```java
public abstract class Game{
    abstract void initialize();
    abstarct void startPlay();
    abstract void endPlay();
    //模板方法
	public  final void play(){
    	initialize();
    	startPlay();
    	endPlay();
	}
}

public class cricket extends Game{
    @Overrice
    void endPlay(){
        System.out.println("Cricket Game Finished!");
    }
    @Override
    void initialize(){
        System.out.println("Cricket Game Finished!");
    }
    @Overrice
    void startPlay(){
        System.out.println("Cricket Game Finished!");
    }
}
public class Football extends Game{
    @Overrice
    void endPlay(){
        System.out.println("Football Game Finished!");
    }
    @Override
    void initialize(){
        System.out.println("Football Game Finished!");
    }
    @Overrice
    void startPlay(){
        System.out.println("Football Game Finished!");
    }
}
public static void main(String[] args){
    Game game = new Cricket();
    game.play();
    
    game = new Football();
    game.play();
}
```

