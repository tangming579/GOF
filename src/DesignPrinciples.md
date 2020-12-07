### 开放封闭原则

**对扩展开放，对修改封闭**

在程序需要进行拓展的时候，不能去修改原有的代码，实现一个热插拔的效果。所以一句话概括就是：为了使程序的扩展性好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类。

### 单一职责原则

一个类或者一个方法只负责一项职责，尽量做到类的只有一个行为原因引起变化；

### 依赖倒转原则

**依赖抽象而不是依赖实现。抽象不应该依赖细节，细节应该依赖抽象。**

### 接口分离原则

**多个特定的客户端接口要好于一个通用性的总接口。**

### 里氏代换原则

子类可以扩展父类的功能，但不能改变原有父类的功能

### 迪米特法则

最少知道原则，尽量降低类与类之间的耦合；