# 函数 {#h1-u51FDu6570}

### 函数的介绍 {#h3-u51FDu6570u7684u4ECBu7ECD}

* 函数相当于OC中的方法
* 函数的格式如下

```
func 函数名(参数列表) -> 返回值类型 {
    代码块
    return 返回值
}
```

* func是关键字,多个参数列表之间可以用逗号（,）分隔，也可以没有参数
* 使用箭头“-&gt;”指向返回值类型
* 如果函数没有返回值，返回值为Void.并且“-&gt;返回值类型”部分可以省略

### 常见的函数类型 {#h3-u5E38u89C1u7684u51FDu6570u7C7Bu578B}

```
// 1.没有参数,没有返回值的函数
func about() -> Void {
    print("iPhone7")
}
about()
func about1() {
    print("iPhone7")
}
about1()
// 2.有参数, 没有返回值的函数
func callPhone(phoneNum : String) {
    print("打电话给\(phoneNum)")
}
callPhone(phoneNum: "+86 110")
// 3.没有参数, 有返回值的函数
func readMsg() -> String {
    return "吃饭了吗?"
}
let msg = readMsg()
// 4.有参数有返回值的函数
func addTwoNum(num1 : Int, num2 : Int) -> Int {
    return num1 + num2
}
let result = addTwoNum(num1: 20, num2: 30)
```

### 函数的使用注意 {#h3-u51FDu6570u7684u4F7Fu7528u6CE8u610F}

* 注意一: 外部参数和内部参数
  * 在函数内部可以看到的参数,就是内部参数
  * 在函数外面可以看到的参数,就是外部参数
  * 默认所有的参数都是外部参数和内部参数
  * 如果不想要外部参数,可以在参数名称前加\_

```
// 1.内部参数&外部参数
/*
func sum(num1 : Int, num2 : Int) -> Int {
    return num1 + num2
}
sum(num1: 20, num2: 30)
*/
/*
func sum(_ num1 : Int,_ num2 : Int) -> Int {
    return num1 + num2
}
sum(20, 30)
*/
func sum(abc num1 : Int, cba num2 : Int) -> Int {
    return num1 + num2
}
sum(abc: 20, cba: 30)
// sum(20, 30)
```

* 注意二: 可变参数
  * swift中函数的参数个数可以变化，它可以接受不确定数量的输入类型参数
  * 它们必须具有相同的类型
  * 我们可以通过在参数类型名后面加入（…）的方式来指示这是可变参数

```
// 2.可变参数
func sum(nums : Int...) -> Int {
    var total = 0
    for num in nums {
        total += num
    }
    return total
}
sum(nums: 20, 30, 40, 50)
func myPrint(_ items : Any...) {
    var strM : String = "\(items[0])"
    for i in 1..<items.count {
        strM = strM + " " + "\(items<i>)"
    }
    print(strM)
}
print(20, 30, 40)
myPrint(20, 30, 40)
```

* 注意三: 默认参数
  * 某些情况,如果没有传入具体的参数,可以使用默认参数

```
func makeCoffee(coffeeName : String = "雀巢") {
    print("制作了一杯爱心\(coffeeName)咖啡")
}
makeCoffee(coffeeName: "拿铁")
makeCoffee(coffeeName: "摩卡")
makeCoffee()
```

* 注意四: 引用类型\(指针的传递\)
  * 默认情况下,函数的参数是值传递.如果想改变外面的变量,则需要传递变量的地址
  * 必须是变量,因为需要在内部改变其值
  * Swift提供的inout关键字就可以实现
  * 对比下列两个函数

```
// 4.指针参数
var m = 20
var n = 30
func swapNum(num1 : inout Int, num2 : inout Int) {
    let temp = num1
    num1 = num2
    num2 = temp
}
swap(&m, &n)
print("m:\(m) n:\(n)")
```



