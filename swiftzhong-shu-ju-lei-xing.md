# Swift中数据类型 {#h1-swift-}

### Swift类型的介绍 {#h3-swift-}

* Swift中的数据类型也有:整型/浮点型/对象类型/结构体类型等等
* 先了解整型和浮点型
* 整型
  * 有符号
    * Int8 : 有符号8位整型
    * Int16 : 有符号16位整型
    * Int32 : 有符号32位整型
    * Int64 : 有符号64位整型
    * Int : 和平台相关\(默认,相当于OC的NSInteger\)
  * 无符号
    * UInt8 : 无符号8位整型
    * UInt16 : 无符号16位整型
    * UInt32 : 无符号32位整型
    * UInt64 : 无符号64位整型
    * UInt : 和平台相关\(常用,相当于OC的NSUInteger\)\(默认\)
* 浮点型
  * Float : 32位浮点型
  * Double : 64浮点型\(默认\)

```
// 定义一个Int类型的变量m,并且赋值为10
var m : Int = 10
// 定义一个Double类型的常量n,并且赋值为3.14
let n : Double = 3.14
```

### Swift中的`类型推导` {#h3-swift-code-code-}

* Swift是强类型的语言
* Swift中任何一个标识符都有明确的类型
* 注意:
  * 如果定义一个标识符时有直接进行赋值,那么标识符后面的类型可以省略.
  * 因为Swift有类型推导,会自动根据后面的赋值来决定前面的标识符的数据类型
  * 可以通过`option`+`鼠标左键`来查看变量的数据类型

```
/*
 类型推导
    1> Swift中任何一个标识符都有自己明确的类型
    2> 如果定义一个标识符时有直接给该标识符进行赋值，那么标识符后面的类型可以省略
    3> 编译器会自动根据后面赋值的类型，推导出前面标识符的类型
    4> 可以根据option + 鼠标左键，查看标识符的类型
 */
// m是Int类型
let m = 20
// n是Double类型
let n = 2.44
// view是UIView类型
var view = UIView()
// color是UIColor类型
let color = UIColor.red
```

### Swift中基本运算 {#h3-swift-}

* Swift中在进行基本运算时必须保证类型一致,否则会出错
  * 相同类型之间才可以进行运算
  * 因为Swift中没有隐式转换
* 数据类型的转化
  * Int类型转成Double类型:Double\(标识符\)
  * Double类型转成Int类型:Int\(标识符\)

```
import UIKit
let m = 20
let n = 30.5
// 错误写法 :
// Swift中没有隐式转化，不会自动将一个Int类型转成Double类型，因此不同类型之间不能进行运算
// let result = m + n
// 正确做法
// 1> 将Int类型转成Double ： Double(标识符)
// 2> 将Double类型转成Int ： Int(标识符)
let result1 = Double(m) + n
let result2 = m + Int(n)
```



