# 自动引用计数 {#h1-u81EAu52A8u5F15u7528u8BA1u6570}

### 工作机制 {#h3-u5DE5u4F5Cu673Au5236}

* Swift和OC一样,采用自动引用计数来管理内容
  * 当有一个强引用指向某一个动向时,该对象的引用计数会自动+1
  * 当该强引用消失时,引用计数会自动-1
  * 当引用计数为0时,该对象会被销毁

### 循环引用 {#h3-u5FAAu73AFu5F15u7528}

* 在通常情况下,ARC是会自动帮助我们管理内存的
* 但是在开发中我们经常会出现循环引用的问题,比如下面的示例
  * Student对Book对象有一个强引用
  * 而Book对Student有一个强引用
  * 在两个对象都指向nil时,依然不会被销毁,就形成了循环引用

```
// 1.创建类
class Student {
    var book : Book?
    deinit {
        print("Student -- deinit")
    }
}
class Book {
    var owner : Student?
    deinit {
        print("Book -- deinit")
    }
}
// 2.创建对象
var stu : Student? = Student()
var book : Book? = Book()
// 3.相互引用
stu?.book = book
book?.owner = stu
// 4.对象置nil
stu = nil
book = nil
```

* 解决方案
  * swift提供了两种解决方案
    * weak : 和OC中的\_\_weak一样是一个弱引用.当指向的对象销毁时,会自动将指针指向nil
    * unowned : 和OC中的\_\_unsafe\_unretained.当对象销毁时依然指向原来的位置\(容易引起野指针\)

```
// 1.创建类
class Student {
    weak var book : Book?
    // unowned var book : Book = Book()
    deinit {
        print("Student -- deinit")
    }
}
class Book {
    var owner : Student?
    deinit {
        print("Book -- deinit")
    }
}
// 2.创建对象
var stu : Student? = Student()
var book : Book? = Book()
// 3.相互引用
stu?.book = book!
book?.owner = stu
// 4.对象置nil
stu = nil
book = nil
```

## Playground

```
import UIKit

// 1.创建类
class Person {
    var name : String = ""
    var book : Book?
    
    deinit {
        print("Person -- deinit")
    }
}

class Book {
    var price : Double = 0
    /*
     OC中表示弱引用
        __weak/__unsafe_unretained(野指针错误)
     Swift中表示弱引用
        weak/unowned(野指针错误)
    */
    // weak var owner : Person?
    // unowned 不能用于修饰可选类型
    unowned var owner : Person = Person()
    
    deinit {
        print("Book -- deinit")
    }
}


// 2.创建两个对象
var person : Person? = Person()
person!.name = "why"
var book : Book? = Book()
book!.price = 60.0

person!.book = book
book!.owner = person!


person = nil
book = nil

```



