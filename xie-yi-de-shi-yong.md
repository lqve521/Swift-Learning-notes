# 协议 {#h1-u534Fu8BAE}

### 协议的格式 {#h3-u534Fu8BAEu7684u683Cu5F0F}

* 协议的定义方式与类，结构体，枚举的定义都非常相似

```
protocol SomeProtocol {
    // 协议方法
}
```

* 遵守协议的格式

```
class SomeClass: SomeSuperClass, FirstProtocol,AnotherProtocol {
    // 类的内容
    // 实现协议中的方法
}
```

### 协议的基本使用 {#h3-u534Fu8BAEu7684u57FAu672Cu4F7Fu7528}

* 定义协议和遵守协议

```
// 1.定义协议
protocol SportProtocol {
    func playBasketball()
    func playFootball()
}
// 2.遵守协议
// 注意:默认情况下在swift中所有的协议方法都是必须实现的,如果不实现,则编译器会报错
class Person : SportProtocol {
    var name : String?
    var age : Int = 0
    // 实现协议中的方法
    func playBasketball() {
        print("人在打篮球")
    }
    func playFootball() {
        print("人在踢足球")
    }
}
```

* 协议之间的继承

```
protocol CrazySportProtocol {
    func jumping()
}
protocol SportProtocol : CrazySportProtocol {
    func playBasketball()
    func playFootball()
}
```

### 代理设计模式 {#h3-u4EE3u7406u8BBEu8BA1u6A21u5F0F}

* 协议继承用于代理设计模式

```
protocol BuyTicketProtocol {
    func buyTicket()
}
class Person {
    // 1.定义协议属性
    var delegate : BuyTicketProtocol
    // 2.自定义构造函数
    init (delegate : BuyTicketProtocol) {
        self.delegate = delegate
    }
    // 3.行为
    func goToBeijing() {
        delegate.buyTicket()
    }
}
class HuangNiu: BuyTicketProtocol {
    func buyTicket() {
        print("买了一张火车票")
    }
}
let p = Person(delegate: HuangNiu())
p.goToBeijing()
```

### 协议中方法的可选 {#h3-u534Fu8BAEu4E2Du65B9u6CD5u7684u53EFu9009}

```
// 1.定义协议
@objc protocol SportProtocol {
     @objc optional func playBasketball()
     @objc optional func playFootball()
}
// 2.遵守协议
class Person : SportProtocol {
    var name : String?
    var age : Int = 0
    // 实现协议中的方法
    func playBasketball() {
        print("人在打篮球")
    }
}
```



