## 装饰模式

**定义**

允许向一个现有的对象添加新的功能，同时又不改变其结构。

意图：动态地给一个对象添加一些额外的职责。就增加功能来说，装饰器模式相比生成子类更为灵活。

主要解决：一般的，我们为了扩展一个类经常使用继承方式实现，由于继承为类引入静态特征，并且随着扩展功能的增多，子类会很膨胀。

**UML**

<div>
    <image src="../img/decorator.png"></image>
</div>

C#：

```c#
abstract class Component
{
    public abstract void Operation();
}
class ConcreteComponent:Component
{
    public override void Operation()
    {
    	
    }
}
abstract class Decorator:Component
{
	protected Component component;
	public void SetComponent(Component component)
    {
    	this.component=component;
    }
    public override void Operation()
    {
    	if(component!=null)
    		component.Operation();
    }
}
```

Java：

```java
public interface Shape{
    void draw();
}
public class Rectangle implements shape{
    @override
    public void draw(){
        
    }
}
public abstract class ShapeDecorator implements Shape{
    protected Shape decoratedShape;
    public ShapeDecorator(Shape decoratedShape){
        this.decoratedShape=decoratedShape;
    }
    public void draw(){
        decoratedShape.draw();
    }
}
public class RedShapeDecorator extends ShapeDecorator{
    public RedShapeDecorator(Sahpe decoratedShape){
        super(decoratedShape);
    }
    @Override
    public void draw(){
        decoratedShape.draw();
        setRedBorder(decoratedShape);
    }
    private void setRedBorder(Shape decoratedShape){
        System.out.println("Border Color: Red");
    }
}
```

### 总结

当系统需要新功能的时候，如果向旧的类中添加新的代码，增加了主类的复杂度。而这些新加入的东西仅仅是为了满足一些只在某种特定情况下才会执行的特殊行为的需要。而装饰模式却提供了一个非常的解决方案，它把每个要装饰的功能放在单独的类中，并让这个类包装他所要装饰的对象，因此，当需要执行特殊行为时，客户代码就可以在运行时根据需要有选择地、按顺序地使用装饰功能包装对象了。

这样最大的好处是，有效地把类的核心职责和装饰功能区分开了，而且可以去除相关勒种重复的装饰逻辑。

装饰模式的顺序是很重要的，比如加密数据和过滤词汇都可以是数据持久化前的装饰功能，但若先加密了数据再用过滤功能就会出问题，最理想的情况，是保证装饰类之间彼此独立，这样就可以以任意的顺序进行组合了。