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
/*
 定义协议时, 协议后面最好跟上 : class
 delegate的属性最好用weak, 用于防止产生循环引用
 */
protocol BuyTicketDelegate : class {
    func buyTicket()
}


class Person {
    
    // 定义代理属性
    weak var delegate : BuyTicketDelegate?
    
    func goToBeijing() {
        delegate?.buyTicket()
    }
}



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

## Playground

```
import UIKit


/*
 1> 协议的定义
 2> 如何类遵守协议
 3> 协议在代理设计模式中如何使用
 4> 协议中方法的可选性
    protocol前面需要加上@objc
    方法前面加上 @objc optional
 */

// 1.协议的定义
protocol SportProtocol {
    // 默认情况下协议中的方法都是必须实现的方法
    func playBasketball()
    func playFootball()
}

// 2.定义类,并且遵守协议
class Teacher : SportProtocol {
    func playFootball() {
        print("踢足球")
    }
    
    func playBasketball() {
        print("打篮球")
    }
}


class Student : NSObject, SportProtocol {
    func playFootball() {
        print("踢足球")
    }
    
    func playBasketball() {
        print("打篮球")
    }
}


// 3.协议在代理设计模型中的使用
/*
 定义协议时, 协议后面最好跟上 : class
 delegate的属性最好用weak, 用于防止产生循环引用
 */
protocol BuyTicketDelegate : class {
    func buyTicket()
}


class Person {
    
    // 定义代理属性
    weak var delegate : BuyTicketDelegate?
    
    func goToBeijing() {
        delegate?.buyTicket()
    }
}


// 4.如何让协议中的方法是可选方法
// optional属于OC特性, 如果协议中有可选的方法, 那么必须在protocol前面加上@objc, 也需要在optional前面加上@objc
@objc protocol TestProtocol {
    @objc optional func test()
}


class Dog : TestProtocol {
    func test() {
        
    }
}

```



