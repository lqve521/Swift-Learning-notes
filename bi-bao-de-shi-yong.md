# 闭包 {#h1-u95EDu5305}

### 闭包的介绍 {#h3-u95EDu5305u7684u4ECBu7ECD}

* 闭包和OC中的block非常相似
  * OC中的block是匿名的函数
  * Swift中的闭包是一个特殊的函数
  * block和闭包都经常用于回调
* 注意:闭包和block一样,第一次使用时可能不习惯它的语法,可以先按照使用简单的闭包,随着学习的深入,慢慢掌握其灵活的运用方法.

### 闭包的使用 {#h3-u95EDu5305u7684u4F7Fu7528}

##### block的用法回顾 {#h5-block-}

* 定义网络请求的类

```
@interface HttpTool : NSObject
- (void)loadRequest:(void (^)())callBackBlock;
@end
@implementation HttpTool
- (void)loadRequest:(void (^)())callBackBlock
{
    dispatch_async(dispatch_get_global_queue(0, 0), ^{
        NSLog(@"加载网络数据:%@", [NSThread currentThread]);
        dispatch_async(dispatch_get_main_queue(), ^{
            callBackBlock();
        });
    });
}
@end
```

* 进行网络请求,请求到数据后利用block进行回调

```
- (void)touchesBegan:(NSSet<UITouch *> *)touches withEvent:(UIEvent *)event
{
    [self.httpTool loadRequest:^{
        NSLog(@"主线程中,将数据回调.%@", [NSThread currentThread]);
    }];
}
```

* block写法总结:

```
block的写法:
    类型:
    返回值(^block的名称)(block的参数)
    值:
    ^(参数列表) {
        // 执行的代码
    };
```

##### 使用闭包代替block {#h5--block}

* 定义网络请求的类

```
class HttpTools: NSObject {
    func requestData(finishedCallback : @escaping (_ jsonData : String, _ age : Int) -> ()) {
        // 1.创建全局队列, 发送异步请求
        DispatchQueue.global().async {
            print("发送网络请求:\(Thread.current)")
            DispatchQueue.main.async {
                print("回调主线程:\(Thread.current)")
                finishedCallback("123", 30)
            }
        }
    }
}
```

* 进行网络请求,请求到数据后利用闭包进行回调

```
  override func touchesBegan(_ touches: Set<UITouch>, with event: UIEvent?) {
        httpTools.requestData { (jsonData :String, age : Int) in
            print("回到控制器,获取到数据")
        }
    }
```

* 闭包写法总结:

```
闭包的写法:
    类型:(形参列表)->(返回值)
    技巧:初学者定义闭包类型,直接写()->().再填充参数和返回值
    值:
    {
        (形参) -> 返回值类型 in
        // 执行代码
    }
```

* 尾随闭包写法:
  * 如果闭包是函数的最后一个参数,则可以将闭包写在\(\)后面
  * 如果函数只有一个参数,并且这个参数是闭包,那么\(\)可以不写

```
 httpTool.loadRequest() {
        print("回到主线程", NSThread.currentThread());
    }
```

```
  // 开发中建议该写法
    httpTool.loadRequest {
        print("回到主线程", NSThread.currentThread());
    }
```

### 闭包的循环引用 {#h3-u95EDu5305u7684u5FAAu73AFu5F15u7528}

* 如果在HttpTool中有对闭包进行强引用,则会形成循环引用
* 补充:在Swift中检测一个对象是否销毁,可以实现对象的
  `deinit`函数

```
// 析构函数(相当于OC中dealloc方法)
    deinit {
        print("ViewController----deinit")
    }
```

* 循环引用的\(实现\)
  * 该实现是为了产生循环引用,而产生的循环引用

```
class HttpTools: NSObject {
    var finishedCallback : ((_ jsonData : String, _ age : Int) -> ())?
    func requestData(finishedCallback : @escaping (_ jsonData : String, _ age : Int) -> ()) {
        self.finishedCallback = finishedCallback
        // 1.创建全局队列, 发送异步请求
        DispatchQueue.global().async {
            print("发送网络请求:\(Thread.current)")
            DispatchQueue.main.async {
                print("回调主线程:\(Thread.current)")
                finishedCallback("123", 30)
            }
        }
    }
}
```

* swift中解决循环引用的方式
* 方案一:
  * 使用weak,对当前控制器使用弱引用
  * 但是因为self可能有值也可能没有值,因此weakSelf是一个可选类型,在真正使用时可以对其强制解包\(该处强制解包没有问题,因为控制器一定存在,否则无法调用所在函数\)

```
    // 解决方案一:
    weak var weakSelf = self
    httpTool.loadData {
        print("加载数据完成,更新界面:", NSThread.currentThread())
        weakSelf!.view.backgroundColor = UIColor.redColor()
    }
```

* 方案二:
  * 和方案一类型,只是书写方式更加简单
  * 可以写在闭包中,并且在闭包中用到的self都是弱引用

```
  httpTool.loadData {[weak self] () -> () in
        print("加载数据完成,更新界面:", NSThread.currentThread())
        self!.view.backgroundColor = UIColor.redColor()
    }
```

* 方案三:\(常用\)
  * 使用关键字`unowned`
  * 从行为上来说 unowned 更像OC中的 unsafe\_unretained
  * unowned 表示:即使它原来引用的对象被释放了，仍然会保持对被已经释放了的对象的一个 “无效的” 引用，它不能是 Optional 值，也不会被指向 nil

```
httpTool.loadData {[unowned self] () -> () in
        print("加载数据完成,更新界面:", NSThread.currentThread())
        self.view.backgroundColor = UIColor.redColor()
    }
```



