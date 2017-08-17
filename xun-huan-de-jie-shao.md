### 循环的介绍 {#h3-u5FAAu73AFu7684u4ECBu7ECD}

* 在开发中经常会需要循环
* 常见的循环有:for/while/do while.
* 这里我们只介绍for/while,因为for/while最常见

### for循环的写法 {#h3-for-}

* 区间for循环

```
for i in 0..<10 {
    print(i)
}
for i in 0...10 {
    print(i)
}
```

* 特殊写法
  * 如果在for循环中不需要用到下标i

```
for _ in 0..<10 {
    print("hello")
}
```

### while和do while循环 {#h3-while-do-while-}

* while循环
  * while的判断句必须有正确的真假,没有非0即真
  * while后面的\(\)可以省略

```
var a = 0
while a < 10 {
    a++
}
```

* do while循环
  * 使用repeat关键字来代替了do

```
let b = 0
repeat {
    print(b)
    b++
} while b < 20
```



