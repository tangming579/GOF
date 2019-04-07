## 观察者模式

**定义**

定义了一种一对多的依赖关系，让多个观察者对象同时监听某一个主题对象。这个主题对象在状态发生改变时，会通知所有观察者对象，使他们能够自己更新自己。

**UML**

<div>
    <image src="../img/observer.jpg"></image>
</div>

C#：

```c#
abstract class Subject
{
    private IList<Observer> observers = new IList<Observer>();
    //增加观察者
    public void Add(Observer observer)
    {
        observers.Add(observer);
    }
    //移除观察者
    public void Remove(Observer observer)
    {
        observers.Remove(observer);
    }
    //通知
    public void Notify()
    {
        foreach(var observer in observers)
        {
            observer.update();
        }
    }
}
abstract class Observer
{
    public abstract void Update();
}
```

**观察者模式的不足**

“抽象通知者”依赖“抽象抽象观察者”，解耦度不高。

可以使用C#中的委托机制降低耦合度，可降低耦合度，使其完全解耦

**发布-订阅模式**

发布-订阅模式是对观察者模式的进一步解耦，消息队列以及C#中的事件、委托，都是发布订阅模式