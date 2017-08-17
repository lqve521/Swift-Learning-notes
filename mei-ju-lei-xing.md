# 枚举类型 {#h1-u679Au4E3Eu7C7Bu578B}

### 枚举类型的介绍 {#h3-u679Au4E3Eu7C7Bu578Bu7684u4ECBu7ECD}

* 概念介绍
  * 枚举定义了一个通用类型的一组相关的值，使你可以在你的代码中以一个安全的方式来使用这些值。
  * 在 C/OC 语言中枚举指定相关名称为一组整型值
  * Swift 中的枚举更加灵活，不必给每一个枚举成员提供一个值.也可以提供一个值是字符串，一个字符，或是一个整型值或浮点值
* 枚举类型的语法
  * 使用enum关键词并且把它们的整个定义放在一对大括号内
    ```
    enum SomeEnumeration {
    // enumeration definition goes here
    }
    ```

### 枚举类型的定义 {#h3-u679Au4E3Eu7C7Bu578Bu7684u5B9Au4E49}

* 以下是指南针四个方向的一个例子
  * case关键词表明新的一行成员值将被定义
  * 不像 C 和 Objective-C 一样，Swift 的枚举成员在被创建时不会被赋予一个默认的整数值
  * 在上面的CompassPoints例子中，North，South，East和West不是隐式的等于0，1，2和3

```
enum CompassPoint {
  case North
  case South
  case East
  case West
}
```

* 定义方式二:多个成员值可以出现在同一行上

```
enum Planet {
  case Mercury, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
}
```

### 给枚举类型赋值 {#h3-u7ED9u679Au4E3Eu7C7Bu578Bu8D4Bu503C}

* 枚举类型赋值可以是字符串/字符/整型/浮点型
  * 注意如果有给枚举类型赋值,则必须在枚举类型后面明确说明具体的类型

```
// 1.枚举类型的赋值
enum CompassPoint : Int {
  case North = 1
  case South = 2
  case East = 3
  case West = 4
}
enum Planet {
  case Mercury = 1, Venus, Earth, Mars, Jupiter, Saturn, Uranus, Neptune
}
// 2.枚举类型的使用
let p = Planet(rawValue: 3)
if let p = p {
    switch p {
    case .Mercury:
        print("Mercury")
    case .Venus:
        print("Venus")
    case .Earth:
        print("Mercury")
    case .Mars:
        print("Mars")
    case .Jupiter:
        print("Jupiter")
    case .Saturn:
        print("Saturn")
    case .Uranus:
        print("Uranus")
    case .Neptune:
        print("Neptune")
    }
}
```

## Playground

```
import UIKit

/*
 1.枚举类型的常见定义方式
 2.创建枚举具体的值
 3.给枚举类型绑定值
 4.枚举类型另外一种定义方式
 */

// 1.枚举类型的定义
enum MethodType : String {
    case get = "get"
    case post = "post"
    case put = "put"
    case delete = "delete"
}


// 2.创建枚举具体的值
let type1 : MethodType = .get
let type2 = MethodType.post
let type3 = MethodType(rawValue: "put") // 值/nil
let str = type3?.rawValue

let btn = UIButton()
btn.setTitle("123", for: UIControlState.normal)


// 3.给枚举类型进行赋值
enum Direction : Int {
    case east = 0
    case west = 1
    case north = 2
    case south = 3
}

let d1 : Direction = .east
let d2 = Direction(rawValue: 1)


// 4.枚举类型定义方式二:
enum Type : Int {
    case get = 0, post, put, delete
}
```



