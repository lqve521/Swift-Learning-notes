# 可选类型 {#h1-u53EFu9009u7C7Bu578B}

### 可选类型的介绍 {#h3-u53EFu9009u7C7Bu578Bu7684u4ECBu7ECD}

* 注意:
  * 可选类型时swift中较理解的一个知识点
  * 暂时先了解,多利用Xcode的提示来使用
  * 随着学习的深入,慢慢理解其中的原理和好处
* 概念:
  * 在OC开发中,如果一个变量暂停不使用,可以赋值为0\(基本属性类型\)或者赋值为空\(对象类型\)
  * 在swift开发中,nil也是一个特殊的类型.因为和真实的类型不匹配是不能赋值的\(swift是强类型语言\)
  * 但是开发中赋值nil,在所难免.因此推出了可选类型
* 可选类型的取值:
  * 空值
  * 有值

### 定义可选类型 {#h3-u5B9Au4E49u53EFu9009u7C7Bu578B}

* 定义一个可选类型有两种写法
  * 最基本的写法
  * 语法糖\(常用\)

```
// 错误写法
// let string : String = nil
// 正确写法:
// 注意:name的类型是一个可选类型,但是该可选类型中可以存放字符串.
// 写法一:定义可选类型
let name : Optional<String> = nil
// 写法二:定义可选类型,语法糖(常用)
let name : String? = nil
```

### 可选类型的使用 {#h3-u53EFu9009u7C7Bu578Bu7684u4F7Fu7528}

```
// 演练一:给可选类型赋值
// 定义可选类型
var string : Optional<String> = nil
// 给可选类型赋值
// 错误写法:因此该可选类型中只能存放字符串
string = 123
// 正确写法:
string = "Hello world"
// 打印结果
print(string)
// 结果:Optional("Hello world")\n
// 因为打印出来的是可选类型,所有会带Optional
// 演练二:取出可选类型的值
// 取出可选类型的真实值(解包)
print(string!)
// 结果:Hello world\n
// 注意:如果可选类型为nil,强制取出其中的值(解包),会出错
string = nil
print(string!) // 报错
// 正确写法:
if string != nil {
    print(string!)
}
// 简单写法:为了让在if语句中可以方便使用string
// 可选绑定
if let str = string {
    print(str)
}
```

### 真实应用场景 {#h3-u771Fu5B9Eu5E94u7528u573Au666F}

* 目的:让代码更加严谨

```
// 1.将字符串类型转成Int类型
let str = "123"
let result : Int? = Int(str) // nil/Int
// 2.根据文件名称,读取路径
let path : String? = Bundle.main.path(forResource: "123.plist", ofType: nil)
// 3.根据string,创建URL
let url = URL(string: "http://www.520it.com/小码哥")
// 4.从字典中取内容
let dict : [String : Any] = ["name" : "why", "age" : 18]
dict["name"]
dict["height"]
```



