# 类型转化 {#h1-u7C7Bu578Bu8F6Cu5316}

### 常见的类型转化符号 {#h3-u5E38u89C1u7684u7C7Bu578Bu8F6Cu5316u7B26u53F7}

* as : 将实例转成某一种类型

### 例子 {#h3-u4F8Bu5B50}

```
// 1.定义数组
let array : [AnyObject] = [12, "why", 1.88]
// 2.取出第二个元素
let objc = array[1]
// 3.将objc转成真正的类型来使用
// 3.1.as? 将AnyObject转成可选类型,通过判断可选类型是否有值,来决定是否转化成功了
let age = objc as? Int
print(age) // 结果:Optional(12)
// 3.2.as! 将AnyObject转成具体的类型,但是注意:如果不是该类型,那么程序会崩溃
let age1 = objc as! Int
print(age1) // 结果:12
```



