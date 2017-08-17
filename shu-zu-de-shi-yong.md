# 数组 {#h1-u6570u7EC4}

### 数组的介绍 {#h3-u6570u7EC4u7684u4ECBu7ECD}

* 数组（Array）是一串有序的由相同类型元素构成的集合
* 数组中的集合元素是有序的，可以重复出现
* Swift中的数组
  * swift数组类型是Array，是一个泛型集合

### 数组的初始化 {#h3-u6570u7EC4u7684u521Du59CBu5316}

* 数组分成:可变数组和不可变数组

  * 使用let修饰的数组是不可变数组
  * 使用var修饰的数组是可变数组

* 定义不可变数组

```
let array : [Any] = ["why", 18, 1.88]
```

* 定义可变数组

```
var arrayM = [Any]()
```

### 对数组的基本操作 {#h3-u5BF9u6570u7EC4u7684u57FAu672Cu64CDu4F5C}

```
// 添加数据
array.append("yz")
// 删除元素
array.removeFirst()
// 修改元素
array[0] = "why"
// 取值
array[1]
```

### 数组的遍历 {#h3-u6570u7EC4u7684u904Du5386}

```
// 遍历数组
for i in 0..<array.count {
    print(array<i>)
}
// forin方式
for item in array {
    print(item)
}
// 设置遍历的区间
for item in array[0..<2] {
    print(item)
}
// 遍历数组的同时获取下标值
let names = ["why", "yz", "lnj", "lmj"]
for (index, name) in names.enumerate() {
    print(index)
    print(name)
}
```

### 数组的合并 {#h3-u6570u7EC4u7684u5408u5E76}

```
// 数组合并
// 注意:只有相同类型的数组才能合并
var array = ["why", "lmj","lnj"]
var array1 = ["yz", "wsz"]
var array2 = array + array1;

// 不建议一个数组中存放多种类型的数据 
var array3 = [2, 3, "why"]
var array4 = ["yz", 23]
array3 + array4 //错误
```



