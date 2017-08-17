# 类的析构函数 {#h1-u7C7Bu7684u6790u6784u51FDu6570}

### 析构函数 {#h3-u6790u6784u51FDu6570}

* Swift 会自动释放不再需要的实例以释放资源
  * Swift 通过自动引用计数（ARC）处理实例的内存管理
  * 当引用计数为0时,系统会自动调用析构函数\(不可以手动调用\)
  * 通常在析构函数中释放一些资源\(如移除通知等操作\)
* 析构函数的写法

```
deinit {
    // 执行析构过程
}
```

### 示例练习 {#h3-u793Au4F8Bu7EC3u4E60}

```
class Person {
    var name : String
    var age : Int
    init(name : String, age : Int) {
        self.name = name
        self.age = age
    }
    deinit {
        print("Person-deinit")
    }
}
var p : Person? = Person(name: "why", age: 18)
p = nil
```



