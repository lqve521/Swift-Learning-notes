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



