# 逻辑分支 {#h1-u903Bu8F91u5206u652F}

### 一. 分支的介绍 {#h3--}

* 分支即if/switch/三目运算符等判断语句
* 通过分支语句可以控制程序的执行流程

### 二. if分支语句 {#h3--if-}

* 和OC中if语句有一定的区别
  * 判断句可以不加\(\)
  * 在Swift的判断句中必须有明确的真假
    * 不再有非0即真
    * 必须有明确的Bool值
    * Bool有两个取值:false/true

```
// 演练一:
let a = 10
// 错误写法:
//if a {
//    print("a")
//}
// 正确写法
if a > 9 {
    print(a)
}
// 演练二:
let score = 87
if score < 60 {
    print("不及格")
} else if score <= 70 {
    print("及格")
} else if score <= 80 {
    print("良好")
} else if score <= 90 {
    print("优秀")
} else {
    print("完美")
}
```

### 二.guard的使用 {#h3--guard-}

* guard是Swift2.0新增的语法
* 它与if语句非常类似，它设计的目的是提高程序的可读性
* guard语句必须带有else语句，它的语法如下：
  * 当条件表达式为true时候跳过else语句中的内容，执行语句组内容
  * 条件表达式为false时候执行else语句中的内容，跳转语句一般是return、break、continue和throw

```
guard 条件表达式 else {
    // 条换语句
    break
}
语句组
```

* 例子

```
var age = 18
func online(age : Int) -> Void {
    guard age >= 18 else {
        print("回家去")
        return
    }
    print("可以上网")
}
online(age)
```

### 三.switch分支 {#h3--switch-}

##### switch的介绍 {#h5-switch-}

* Switch作为选择结构中必不可少的语句也被加入到了Swift中
* 只要有过编程经验的人对Switch语句都不会感到陌生
* 但苹果对Switch进行了大大的增强，使其拥有其他语言中没有的特性

##### switch的简单使用 {#h5-switch-}

* 基本用法和OC用法一致
* 不同之处:
  * switch后可以不跟\(\)
  * case后可以不跟break\(默认会有break\)
* 例子:

```
let sex = 0
switch sex {
case 0 :
    print("男")
case 1 :
    print("女")
default :
    print("其他")
}
```

* 简单使用补充:
  * 一个case判断中,可以判断多个值
  * 多个值以`,`隔开

```
let sex = 0
switch sex {
case 0, 1:
    print("正常人")
default:
    print("其他")
}
```

* 简单使用补充:
  * 如果希望出现之前的case穿透,则可以使用关键字`fallthrough`

```
let sex = 0
switch sex {
case 0:
    fallthrough
case 1:
    print("正常人")
default:
    print("其他")
}
```

##### switch支持区间判断 {#h5-switch-}

* 什么是区间?
  * 通常我们指的是数字区间:0~10,100~200
* swift中的区间常见有两种
  * 半开半闭区间:0..
    &lt;
    10 表示:0~9,不包括10
  * 闭区间:0…10 表示:0~10

```
let score = 88
switch score {
case 0..<60:
    print("不及格")
case 60..<80:
    print("几个")
case 80..<90:
    print("良好")
case 90..<100:
    print("优秀")
default:
    print("满分")
}
```



