# 字典 {#h1-u5B57u5178}

### 字典的介绍 {#h3-u5B57u5178u7684u4ECBu7ECD}

* 字典允许按照某个键来访问元素
* 字典是由两部分集合构成的，一个是键（key）集合，一个是值（value）集合
* 键集合是不能有重复元素的，而值集合是可以重复的，键和值是成对出现的
* Swift中的字典
  * Swift字典类型是Dictionary，也是一个泛型集合

### 字典的初始化 {#h3-u5B57u5178u7684u521Du59CBu5316}

* Swift中的可变和不可变字典
  * 使用let修饰的数组是不可变字典
  * 使用var修饰的数组是可变字典

```
// 定义一个可变字典
var dict1 : [String : Any] = [String : Any]()
// 定义一个不可变字典
let dict2 : [String : Any] = ["name" : "why", "age" : 18]
```

### 字典的基本操作 {#h3-u5B57u5178u7684u57FAu672Cu64CDu4F5C}

```
// 添加数据
dict["height"] = 1.88
dict["weight"] = 70.0
dict
// 删除字段
dict.removeValueForKey("height")
dict
// 修改字典
dict["name"] = "lmj"
dict.updateValue("lmj", forKey: "name")
dict
// 查询字典
dict["name"]
```

### 字典的遍历 {#h3-u5B57u5178u7684u904Du5386}

```
// 遍历字典中所有的值
for value in dict.values {
    print(value)
}
// 遍历字典中所有的键
for key in dict.keys {
    print(key)
}
// 遍历所有的键值对
for (key, value) in dict {
    print(key)
    print(value)
}
```

### 字典的合并 {#h3-u5B57u5178u7684u5408u5E76}

```
// 字典的合并
var dict1 = ["name" : "yz", "age" : 20]
var dict2 = ["height" : 1.87, "phoneNum" : "+86 110"]
// 字典不可以相加合并
for (key, value) in dict1 {
    dict2[key] = value
}
```



