策略模式与状态模式的UML图是一样的：

<div>
    <image src="../img/state.png"></image>
</div>

```c#
public interface IState
{
    void Handle(Context context);
}
public class Context
{
    private IState state;
    //定义Context的初始状态
    public Context(State state)
    {
        this.state = state;
    }
    //可读写的状态熟悉，用于读取当前状态和设置新状态
    public State State
    {
        get { return state;}
        set
        {
        	state = value;
            Console.WriteLine("Current State is " + state.GetType().Name);
        }
    }
    public void Request()
    {
        //对请求做处理，并设置下一状态
        state.Handle(this);
    }
}
public class ConcreteStateA : IState
{
	public void Handle(Context context)
    {
    	context.State = new ConcreteStateB();
    }
}
public class ConcreteStateB : IState
{
	public void Handle(Context context)
    {
    	context.State = new ConcreteStateA();
    }
}

static void Main(string[] args)
{
    //设置Context的初始状态为ConcreteStateA
    Context c = new Context(new ConcreteStateA());
    //不断请求，同时更改状态
    c.Request();
    c.Request();
    c.Request();    
    Console.ReadKey();
}
```

Java：

```
public interface State{
    public void doAction(Context context);
}
public class StartState implements State{
    public void doAction(Context context){
        System.out.println("Player is in Start state");
        context.setState(this);
    }
    public String toString(){
        return "Start State";
    }
}
public class StopState implements State{
    public void doAction(Context context){
        System.out.println("Player is in Stop state");
        context.setState(this);
    }
    public String toString(){
        return "Stop State";
    }
}
```

