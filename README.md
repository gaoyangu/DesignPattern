# DesignPattern

## 面向对象的设计原则

1. 依赖倒置原则（DIP）
   - 高层模块（稳定）不应该依赖于低层模块（变化），二者都应该依赖于抽象（稳定）
   - 抽象（稳定）不应该依赖于实现细节（变化），实现细节应该依赖于抽象（稳定）

2. 开放封闭原则（OCP）
   - 对扩展开放，对更改封闭
   - 类模块应该是可扩展的，但是不可修改

3. 单一职责原则（SRP）
    - 一个类应该仅有一个引起它变化的原因
    - 变化的方向隐含着类的责任

4. Liskov 替换原则（LSP）
    - 子类必须能够替换它们的基类（IS-A）
    - 继承表达类型抽象

5. 接口隔离原则（ISP）
    - 不应该强迫客户程序依赖它们不用的方法
    - 接口应该小而完备
  
6. 优先使用对象组合，而不是类继承
   - 类继承通常为“白箱服用”，对象组合通常为“黑箱复用”
   - 继承在某种程度上破坏了封装性，子类父类耦合度高
   - 对象组合只要求被组合的对象具有良好定义的接口，耦合度低

7. 封装变化点
   - 使用封装类创建对象之间的分界层，让设计者可以在分界层的一侧进行修改，而不会对另一侧产生不良的影响，从而实现层次间的松耦合

8. 针对接口编程，而不是针对实现编程
   - 不将变量类型声明为某个特定的具体类，而是声明为某个接口
   - 客户程序无需获知对象的具体类型，只需要知道对象所具有的接口
   - 减少系统中各部分的依赖关系，从而实现“高内聚，低耦合”的类型设计方案

## GOF-23 模式分类
从目的来看：
- 创建型（Creational）模式
- 结构型（Structural）模式
- 行为型（Behavioral）模式

从范围来看：
- 类模式处理类与子类的静态关系
- 对象模式处理对象间的动态关系

## 重构获得模式

重构关键技法：
1. 静态 -> 动态
2. 早绑定 -> 晚绑定
3. 继承 -> 组合
4. 编译时依赖 -> 运行时依赖
5. 紧耦合 -> 松耦合

## 设计模式

### 1. 组件协作

框架与应用程序的划分，组件协作模式通过晚绑定，实现框架与应用程序之间的松耦合

- [模板方法 Template Method](01.模板方法.md)
- [策略模式 Startegy](02.策略模式.md)
- [观察者模式 Observer/Event](03.观察者模式.md)

### 2. 单一职责

软件组织的设计中，如果责任划分的不清晰，使用继承得到的结果往往是随着需求的变化，子类急剧膨胀，同时充斥着重复代码，这时候的关键就是划清责任

- [装饰器模式 Decorator](04.装饰器模式.md)
- [桥模式 Bridge](05.桥模式.md)

### 3. 对象创建

通过“对象创建”模式绕开new，来避免对象创建（new）过程中所导致的紧耦合（依赖具体类），从而支持对象创建的稳定。它是接口抽象之后的第一步工作。

- [工厂方法模式 Factory Method](06.工厂模式.md)
- [抽象工厂模式 Abstract Factory](07.抽象工厂模式.md)
- [原型模式 Prototype](08.原型模式.md) : 较少应用
- [建造者模式 Builder](09.构建器模式.md): 较少应用

### 4. 对象性能

面向对象很好的解决了“抽象”的问题，但是必不可免地要付出一定的代价。通常情况，面向对象的成本大都可以忽略不计。但是某些情况，面向对象所带来的成本必须谨慎处理。

- [单例模式 Singleton](10.单例模式.md)
- [享元模式 FlyWeight](11.享元模式.md)

### 5. 接口隔离

在组件构建过程中，某些接口之间直接的依赖常常会带来很多问题、甚至根本无法实现。采用添加一层间接（稳定）接口，来隔离本来相互紧密关联的接口是一种常见的解决方案。

- [门面模式 Facade](12.门面模式.md)：解耦系统间（单向）的对象关联关系
- [代理模式 Proxy](13.代理模式.md)：由于性能原因，安全原因等
- [适配器模式 Adapter](14.适配器模式.md)：新接口与旧接口
- [中介者模式 Mediator](15.中介者模式.md)：解耦系统内各个对象之间（双向）的关联关系

### 6. 状态变化

在组件构建过程中，某些对象的状态经常面临变化，如何对这些变化进行有效的管理？同时又维持高层模块的稳定？

- [状态模式 State](16.状态模式.md)
- [备忘录模式 Memento](17.备忘录模式.md)

### 7. 数据结构

常常有一些组件在内部具有特定的数据结构，如果让客户程序依赖这些特定的数据结构，将极大地破坏组件的复用。此时，将这些特定数据结构封装在内部，在外部提供统一的接口，来实现与特定数据结构无关的访问，是一种行之有效地解决方案。

- [组合模式 Composite](18.组合模式.md)
- [迭代器模式 Iterator](19.迭代器模式.md)：较少使用
- [职责链模式 Chain of Resposibility](20.职责链模式.md)：较少使用

### 8. 行为变化

在组件的构建过程中，组件行为的变化经常导致组件本身剧烈的变化。“行为变化”模式将组件的行为和组件本身进行解耦，从而支持组件行为的变化，实现两者之间的松耦合。

- [命令模式 Command](21.命令模式.md)
- [访问器模式 Visitor]()

### 9. 领域问题

- [解析器模式]()

## 参考资料

- 李建忠：C++设计模式
- [卡码网设计模式精讲](https://github.com/youngyangyang04/kama-DesignPattern)