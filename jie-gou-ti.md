# 结构体 {#h1-u7ED3u6784u4F53}

### 结构体的介绍 {#h3-u7ED3u6784u4F53u7684u4ECBu7ECD}

* 概念介绍
  * 结构体\(struct\)是由一系列具有相同类型或不同类型的数据构成的数据集合
  * 结构体\(struct\)指的是一种数据结构
  * 结构体是值类型,在方法中传递时是值传递
* 结构的定义格式

```
struct 结构体名称 {
    // 属性和方法
}
```

### 结构体的使用 {#h3-u7ED3u6784u4F53u7684u4F7Fu7528}

* 定义&使用结构体

```
// 初始化结构体
struct Location {
    var x : Double
    var y : Double
}
// 创建结构体
let location = Location(x: 90, y: 90)
```

### 结构体的增强 {#h3-u7ED3u6784u4F53u7684u589Eu5F3A}

* 扩充构造函数
  * 默认情况下创建Location时使用Location\(x: x值, y: y值\)
  * 但是为了让我们在使用结构体时更加的灵活,swift还可以对构造函数进行扩充
  * 扩充的注意点
    * 在扩充的构造函数中必须保证成员变量是有值的
    * 扩充的构造函数会覆盖原有的构造函数

```
struct Location {
    var x : Double
    var y : Double
    init(x : Double, y : Double) {
        self.x = x
        self.y = y
    }
    init(xyString : String) {
        let strs = xyString.componentsSeparatedByString(",")
        x = Double(strs.first!)!
        y = Double(strs.last!)!
    }
}
let location = Location(x: 100, y: 100)
let location1 = Location(xyString: "100,100")
```

* 为结构体扩充方法
  * 为了让结构体使用更加灵活,swift的结构体中可以扩充方法
  * 例子:为了Location结构体扩充两个方法
    * 向水平方向移动的方法
    * 向垂直方向移动的方法

```
struct Location {
    var x : Double
    var y : Double
    init(x : Double, y : Double) {
        self.x = x
        self.y = y
    }
    init(xyString : String) {
        let strs = xyString.componentsSeparatedByString(",")
        x = Double(strs.first!)!
        y = Double(strs.last!)!
    }
    mutating func moveH(x : Double) {
        self.x += x
    }
    mutating func moveV(y : Double) {
        self.y += y
    }
}
```

* 注意:
  * 如果我们使用的Location不是自己定义的，但是我们仍旧希望在自己的项目里扩展Location的操作
  * Swift也能帮我们达成，这个机制，叫做extension

```
extension Location {
    mutating func moveH(x : Double) {
        self.x += x
    }
    mutating func moveV(y : Double) {
        self.y += y
    }
}
```

## Playground

```
import UIKit


/*
 1.定义结构体
 2.创建结构体对应的值
 3.创建系统结构体方式
 4.给结构体扩充方法
 5.给结构体扩充构造函数
 */

// 1.定义结构体
struct Location {
    // 属性
    var x : Double
    var y : Double
    // var z : Double
    
    // 方法
    // 最普通的函数: 该函数是没有用到成员属性
    func test() {
        print("结构体中的test函数")
    }
    
    // 改变成员属性 : 如果在函数中修改了成员属性, 那么该函数前必须加上mutating
    mutating func moveH(_ distance : Double) {
        self.x += distance
    }
    
    
    // 给结构体扩充构造函数
    // 1> 默认情况下, 系统会为每一个结构体提供一个默认的构造函数, 并且该构造函数, 要求给每一个成员属性进行赋值
    // 2> 构造函数都是以init开头, 并且构造函数不需要返回值
    // 3> 在构造函数结束时, 必须保证所有的成员属性有被初始化
    init(x : Double, y : Double) {
        self.x = x
        self.y = y
    }
    
    init(xyStr : String) {
        // 20,30 --> ["20", "30"]
        let array = xyStr.components(separatedBy: ",")
        let item1 = array[0]
        let item2 = array[1]
        
        /*
        if let x = Double(item1) {
            self.x = x
        } else {
            self.x = 0
        }
        
        if let y = Double(item2) {
            self.y = y
        } else {
            self.y = 0
        }
        */
        
        // ?? 判断前面的可选类型是否有值
        // 有值, 则解包, 没有值,则使用后面的值
        self.x = Double(item1) ?? 0
        self.y = Double(item2) ?? 0
    }
}

// 2.创建结构体对应的值
var center = Location(x: 20, y: 30)
// let ceter = Location(x: 20, y: 30, z: 40)

// 3.系统结构体的创建方式
let rect = CGRect(x: 0, y: 0, width: 100, height: 100)
let size = CGSize(width: 20, height: 20)
let point = CGPoint(x: 0, y: 0)
let range = NSRange(location: 0, length: 3)


// 4.给结构体扩充方法
center.test()
//center.moveH(distance: 20)
center.moveH(20)
print(center)


// 5.给结构体扩充构造函数
Location(x: 20, y: 30)

Location(xyStr : "20,30")
```



