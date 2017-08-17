# 常量&变量 {#h1--amp-}

### 什么是常量和变量 {#h3-u4EC0u4E48u662Fu5E38u91CFu548Cu53D8u91CF}

* 在Swift中规定：在定义一个标识符时必须明确说明该标识符是一个常量还是变量
* 使用let来定义常量，定义之后不可以修改
* 使用var来定义变量，定义之后可以修改

### 变量的基本使用 {#h3-u53D8u91CFu7684u57FAu672Cu4F7Fu7528}

```
import UIKit
let a : Int = 10
// 错误写法,当一个标识符定义为常量时是不可以修改的
// a = 20
var b : Int = 20
// 因为b定义为变量,因此是可以修改的
b = 30
```

### 常量和变量的使用注意: {#h3--}

* 注意:
  * 在真实使用过程中,建议先定义常量,如果需要修改再修改为变量\(更加安全\)
  * 是指向的对象不可以再进行修改.但是可以通过指针获得对象后,修改对象内部的属性

```
import UIKit
/*
 常量使用注意：
    1> 优先使用常量
    2> 常量的本质
 */
// 1.注意一：在开发中let/var在选择时优先使用常量，防止不小被修改掉（let）
// 如果一个标识符不需要修改，但是声明称了变量，那么编译器会报警告
// 2.常量的本质：
// 含义：指向的内存地址不可以修改，但是可以通过内存地址，找到对应的对象，之后修改对象内部的属性
/*
 OC中创建对象：
    UIView *view = [[UIView alloc] init];
    view = [[UIView alloc] init];
 Swift中创建对象：
    var view : UIView = UIView()
 */
/*
 变量的做法
    var view : UIView = UIView()
    view = UIView()
 */
// 创建常量View
let view = UIView()
// view = UIView() 错误做法
view.alpha = 0.5
// Swift中创建结构体：结构体类型()
view.frame = CGRect(x: 0, y: 0, width: 100, height: 100)
// Swift中调用方法，统一使用点语法
view.backgroundColor = UIColor.red
```

### 创建对象补充 {#h3-u521Bu5EFAu5BF9u8C61u8865u5145}

* 创建UIView对象，并且在UIView中添加UIButton

```
import UIKit
// 1.创建UIView对象
// OC : [[UIView alloc] initWithFrame:CGRect]
let viewRect = CGRect(x: 0, y: 0, width: 100, height: 100)
let view : UIView = UIView(frame: viewRect)
// 2.设置UIView的属性
view.backgroundColor = UIColor.orange
// 3.创建UIButton
let btn : UIButton = UIButton(type: .custom)
// 4.设置UIButton的属性
btn.frame = CGRect(x: 0, y: 0, width: 50, height: 50)
btn.backgroundColor = UIColor.purple
/*
 Swift中枚举类型：
 1> 如果可以根据上下文推导出类型可以直接.具体的类型
 2> 如果根据上下文推导不出具体的类型，则需要：类型.具体的类型
 */
btn.setTitle("按钮", for: .normal)
btn.setTitleColor(UIColor.white, for: .normal)
// 5.将btn添加到UIView中
view.addSubview(btn)
```



