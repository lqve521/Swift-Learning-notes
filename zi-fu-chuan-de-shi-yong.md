### 字符串的介绍 {#h3-u5B57u7B26u4E32u7684u4ECBu7ECD}

* 字符串在任何的开发中使用都是非常频繁的
* OC和Swift中字符串的区别
  * 在OC中字符串类型时NSString,在Swift中字符串类型是String
  * OC中字符串@””,Swift中字符串””
* 使用`String`
  的原因
  * `String`是一个结构体，性能更高
  * `NSString`是一个`OC`对象，性能略差
  * `String`支持直接遍历
  * `Swift`提供了`String`和`NSString`之间的无缝转换

### 字符的定义 {#h3-u5B57u7B26u7684u5B9Au4E49}

* 定义不可变字符串

```
// 1> 定义不可变字符串 : 使用let修饰
let str : String = "hello swift"
// str = "hello Objective-C" 错误写法
```

* 定义可变字符串

```
// 2> 定义可变字符串 : 使用var修饰
var strM : String = "hello world"
strM = "hello china"
```

### 字符串的使用 {#h3-u5B57u7B26u4E32u7684u4F7Fu7528}

##### 获取字符串的长度 {#h5-u83B7u53D6u5B57u7B26u4E32u7684u957Fu5EA6}

* 获取字符集合,再获取集合的count属性

```
let count = str.characters.count
```

##### 字符串拼接 {#h5-u5B57u7B26u4E32u62FCu63A5}

* 两个字符串的拼接

```
let str1 = "Hello"
let str2 = "World"
let str3 = str1 + str2
```

* 字符串和其他数据类型的拼接\(字符串插值\)

```
let name = "why"
let age = 18
let info = "my name is \(name), age is \(age)"
```

* 字符串的格式化
  * 比如时间03:04

```
let min = 3
let second = 4
let time = String(format: "%02d:%02d", arguments: [min, second])
```

##### 字符串的截取 {#h5-u5B57u7B26u4E32u7684u622Au53D6}

* Swift中提供了特殊的截取方式
  * 该方式非常麻烦
  * Index创建较为麻烦
* 简单的方式是将String转成NSString来使用
  * 在标识符后加:as NSString即可

```
let urlString = "www.520it.com"
// Swift中通过 as 关键字可以将String类型转成NSString的类型
let header1 = (urlString as NSString).substring(to: 3)
let footer1 = (urlString as NSString).substring(from: 10)
let range1 = NSRange(location: 4, length: 5)
let middle1 = (urlString as NSString).substring(with: range1)
```

* swift截取方式

```
let urlString = "www.520it.com"
let headerIndex = urlString.index(urlString.startIndex, offsetBy: 3)
let header2 = urlString.substring(to: headerIndex)
let footerIndex = urlString.index(urlString.endIndex, offsetBy: -3)
let footer2 = urlString.substring(from: footerIndex)
let startIndex = urlString.index(urlString.startIndex, offsetBy: 4)
let endIndex = urlString.index(urlString.startIndex, offsetBy: 9)
let range2 = Range(startIndex..<endIndex)
let middle2 = urlString.substring(with: range2)
```



