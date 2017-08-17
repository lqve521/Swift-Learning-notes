# 类的构造函数 {#h1-u7C7Bu7684u6784u9020u51FDu6570}

### 构造函数的介绍 {#h3-u6784u9020u51FDu6570u7684u4ECBu7ECD}

* 构造函数类似于OC中的初始化方法:init方法
* 默认情况下载创建一个类时,必然会调用一个构造函数
* 即便是没有编写任何构造函数，编译器也会提供一个默认的构造函数。
* 如果是继承自NSObject,可以对父类的构造函数进行重写

### 构造函数的基本使用 {#h3-u6784u9020u51FDu6570u7684u57FAu672Cu4F7Fu7528}

##### 构造函数的基本使用 {#h5-u6784u9020u51FDu6570u7684u57FAu672Cu4F7Fu7528}

* 类的属性必须有值
* 如果不是在定义时初始化值,可以在构造函数中赋值

```
class Person: NSObject {
    var name : String
    var age : Int
    // 重写了NSObject(父类)的构造方法
    override init() {
        name = ""
        age = 0
    }
}
// 创建一个Person对象
let p = Person()
```

##### 初始化时给属性赋值 {#h5-u521Du59CBu5316u65F6u7ED9u5C5Eu6027u8D4Bu503C}

* 很多时候,我们在创建一个对象时就会给属性赋值
* 可以自定义构造函数
* 注意:如果自定义了构造函数,会覆盖init\(\)方法.即不在有默认的构造函数

```
class Person: NSObject {
    var name : String
    var age : Int
    // 自定义构造函数,会覆盖init()函数
    init(name : String, age : Int) {
        self.name = name
        self.age = age
    }
}
// 创建一个Person对象
let p = Person(name: "why", age: 18)
```

##### 字典转模型\(初始化时传入字典\) {#h5--}

* 真实创建对象时,更多的是将字典转成模型
* 注意:
  * 去字典中取出的是NSObject,任意类型.
  * 可以通过as!转成需要的类型,再赋值\(不可以直接赋值\)

```
class Person: NSObject {
    var name : String
    var age : Int
    // 自定义构造函数,会覆盖init()函数
    init(dict : [String : NSObject]) {
        name = dict["name"] as! String
        age = dict["age"] as! Int
    }
}
// 创建一个Person对象
let dict = ["name" : "why", "age" : 18]
let p = Person(dict: dict)
```

##### 字典转模型\(利用KVC转化\) {#h5--kvc-}

* 利用KVC字典转模型会更加方便
* 注意:
  * KVC并不能保证会给所有的属性赋值
  * 因此属性需要有默认值
    * 基本数据类型默认值设置为0
    * 对象或者结构体类型定义为可选类型即可\(可选类型没有赋值前为nil\)

```
class Person: NSObject {
    // 结构体或者类的类型,必须是可选类型.因为不能保证一定会赋值
    var name : String?
    // 基本数据类型不能是可选类型,否则KVC无法转化
    var age : Int = 0
    // 自定义构造函数,会覆盖init()函数
    init(dict : [String : NSObject]) {
        // 必须先初始化对象
        super.init()
        // 调用对象的KVC方法字典转模型
        setValuesForKeysWithDictionary(dict)
    }
}
// 创建一个Person对象
let dict = ["name" : "why", "age" : 18]
let p = Person(dict: dict)
```

## Playground

```
import UIKit


/*
 @interface Person : NSObject
 
 @property (nonautomic, copy) NSString *name;
 @property (nonautomic, assign) NSInteger age;
 
 - (instanceType)initWithName:(NSString *)name age:(NSInteger)age;
 - (instanceType)initWithDict:(NSDictionary *)dict;
 
 @end
 
 
 Person *p = [Person alloc] init];
 Person *p = [Person alloc] initWithName:@"why" age:18];
 */

class Person {
    var name : String = ""
    var age : Int = 0
    
    // 在Swift开发中, 如果在对象函数中, 用到成员属性, 那么self.可以省略
    // 注意: 如果在函数中, 有和成员属性重名的局部变量,那么self.不能省略
    
    
    
    // 注意: 如果有自定义构造函数, 那么会将系统提供的构造函数覆盖掉
    init() {
        
    }
    
    init(name : String, age : Int) {
        self.name = name
        self.age = age
    }
    
    // Dictionary<String, Any> --> [String : Any]
    init(dict : [String : Any]) {
        /*
        let dictName = dict["name"]
        name = dictName as! String
        */
        if let name = dict["name"] as? String {
            self.name = name
        }
        
        if let age = dict["age"] as? Int {
            self.age = age
        }
    }
}


let p1 = Person()
let p2 = Person(name: "why", age: 18)
let p3 = Person(dict: ["name" : "why", "age" : 18])

print(p3.name, p3.age)
```

```
import UIKit

/*
 使用KVC条件
    1> 必须继承自NSObject
    2> 必须在构造函数中,先调用super.init()
    3> 调用setValuesForKeys
    4> 如果字典中某一个key没有对应的属性, 则需要重写setValue forUndefinedKey方法
 */

class Person : NSObject {
    var name : String = ""
    var age : Int = 0
    var height : Double = 0
    
    init(dict : [String : Any]) {
        /*
        if let name = dict["name"] as? String {
            self.name = name
        }
        
        if let age = dict["age"] as? Int {
            self.age = age
        }
        
        if let height = dict["height"] as? Double {
            self.height = height
        }
        */
        super.init()
        setValuesForKeys(dict)
    }
    
    override func setValue(_ value: Any?, forUndefinedKey key: String) {}
}

//let p = Person()

let p = Person(dict: ["name" : "why", "age" : 18, "height" : 1.88, "phoneNum" : "+86 110"])
print(p.age, p.name, p.height)
```



