# 元组 {#h1-u5143u7EC4}

### 元组的介绍 {#h3-u5143u7EC4u7684u4ECBu7ECD}

* 元组是Swift中特有的,OC中并没有相关类型
* 它是什么呢?
  * 它是一种数据结构，在数学中应用广泛
  * 类似于数组或者字典
  * 可以用于定义一组数据
  * 组成元组类型的数据可以称为“元素”

### 元组的定义 {#h3-u5143u7EC4u7684u5B9Au4E49}

* 元组的常见写法
  ```
  // 使用元组描述一个人的信息
  ("1001", "张三", 30, 90)
  // 给元素加上元素名称,之后可以通过元素名称访问元素
  (id:"1001", name:"张三", english_score:30, chinese_score:90)
  ```

### 元组的简单使用 {#h3-u5143u7EC4u7684u7B80u5355u4F7Fu7528}

* 用元组来描述一个HTTP的错误信息

```
// 元组:HTTP错误
// let array = [404, "Not Found"]
// 写法一:
let error = (404, "Not Found")
print(error.0)
print(error.1)
// 写法二:
let error = (errorCode : 404, errorInfo : "Not Found")
print(error.errorCode)
print(error.errorInfo)
// 写法三:
let (errorCode, errorIno) = (404, "Not Found")
print(errorCode)
print(errorIno)
```



