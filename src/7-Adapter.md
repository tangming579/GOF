## 代理模式

**定义**

将一个类的接口转换成客户希望的另外一个接口。Adapter使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。

**UML**

<div>
    <image src="../img/adapter.png"></image>
</div>


C#：

```c#
//客户希望的接口
public class Target
{
    public virtual void Request()
    {
        Console.WriteLine("普通请求");
    }
}
//需要适配的类
public class Adaptee
{
    public void SpecificRequest()
    {
        Console.WriteLine("特殊的请求");
    }
}
public class Adapter : Target
{
	private Adaptee adaptee = new Adaptee();
	public override void Request()
    {
    	adaptee.SpecificRequest();
    }
}
```

Java：

```java
public interface MediaPlayer{
	void Play(string audioType,string fileName);
}
public class AdvanceMediaPlayer{
    public void PlayMP4(string fileName){
        
    }
    public void PlayAvi(string fileName){
        
    }
}

public class MediaAdapter implements MediaPlayer {
    AdvanceMediaPlayer advanceMediaPlayer = new AdvanceMediaPlayer();
    
    @override
    public void Play(string audioType,string fileName){
        if(audioType=="MP4")
            advanceMediaPlayer.PlayMP4(flieName);
        else if(audioType="Avi")
            advanceMediaPlayer.playAvi(fileName);
    }
}
```

