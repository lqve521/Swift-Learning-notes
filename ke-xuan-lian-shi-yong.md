# 可选链 {#h1-u53EFu9009u94FE}

### 可选连的概念 {#h3-u53EFu9009u8FDEu7684u6982u5FF5}

* 它的可选性体现于请求或调用的目标当前可能为空（nil）
  * 如果可选的目标有值，那么调用就会成功；
  * 如果选择的目标为空（nil），则这种调用将返回空（nil）
* 多次调用被链接在一起形成一个链，如果任何一个节点为空（nil）将导致整个链失效。
* 可选链的使用
  * 在可选类型后面放一个问号，可以定义一个可选链。
  * 这一点很像在可选值后面放一个叹号来强制拆得其封包内的值
    * 它们的主要的区别在于当可选值为空时可选链即刻失败
    * 然而一般的强制解析将会引发运行时错误。
  * 因为可选链的结果可能为nil,可能有值.因此它的返回值是一个可选类型.
    * 可以通过判断返回是否有值来判断是否调用成功
    * 有值,说明调用成功
    * 为nil,说明调用失败

### 可选链的示例 {#h3-u53EFu9009u94FEu7684u793Au4F8B}

* 从可选链中取值
  * 示例描述: 人\(Person\)有一个狗\(Dog\),狗\(Dog\)有一个玩具\(Toy\),玩具有价格\(price\)
  * 使用代码描述上述信息

```
// 1.定义类
class Person {
    var name : String
    var dog : Dog?
    init(name : String) {
        self.name = name
    }
}
class Dog {
    var color : UIColor
    var toy : Toy?
    init(color : UIColor) {
        self.color = color
    }
    func runing() {
        print("跑起来")
    }
}
class Toy {
    var price : Double = 0.0
}
// 2.创建对象,并且设置对象之间的关系
// 2.1.创建对象
let person = Person(name: "小明")
let dog = Dog(color: UIColor.yellow)
let toy = Toy()
toy.price = 100.0
// 2.2.设置对象之间的关系
person.dog = dog
dog.toy = toy
```

* 需求:获取
  `小明的大黄宠物的玩具价格`
  * 取出的值为可选类型,因为可选链中有一个可选类型为nil,则返回nil
  * 因此结果可能有值,可能为nil.因此是一个可选类型

```
let price = person.dog?.toy?.price
print(price) // Optional(100.0)\n
```

* 需求:给小明的大黄一个新的玩具
  * 相当于给可选类型赋值

```
person.dog?.toy = Toy()
```

* 需求:让小明的狗跑起来
  * 如果可选类型有值,则会执行该方法
  * 如果可选类型为nil,则该方法不会执行

```
person.dog?.runing()
```



