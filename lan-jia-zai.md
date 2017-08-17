# 懒加载 {#h1-u61D2u52A0u8F7D}

### 懒加载的介绍 {#h3-u61D2u52A0u8F7Du7684u4ECBu7ECD}

* swift中也有懒加载的方式
  * \(苹果的设计思想:希望所有的对象在使用时才真正加载到内存中\)
* 和OC不同的是swift有专门的关键字来实现懒加载
* lazy关键字可以用于定义某一个属性懒加载

### 懒加载的使用 {#h3-u61D2u52A0u8F7Du7684u4F7Fu7528}

* 格式

```
lazy var 变量: 类型 = { 创建变量代码 }()
```

* 懒加载的使用

```
  // 懒加载的本质是,在第一次使用的时候执行闭包,将闭包的返回值赋值给属性
    // lazy的作用是只会赋值一次
   // lazy var names : [String] = ["why", "lmj", "lnj"]
    lazy var names : [String] = {
        let names = ["why", "lmj", "lnj"]
        
        print("-----")
        
        return names
    }()
    
    // 方式一: 仅仅能创建Btn
    // lazy var btn : UIButton = UIButton()
    
    // 方式二: 可以设置更多btn的属性
    lazy var btn : UIButton = {
        let btn = UIButton()
        
        btn.setTitle("按钮", for: .normal)
        btn.setImage(UIImage(named: ""), for: .normal)
        
        return btn
    }()

```



