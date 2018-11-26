---
title: 函数
date: 2018-11-21 10:14:52
tags:
---
## 函数的5种声明

1. 具名函数
```
 function f(x,y){
     return x+y
 }
 f.name // 'f'
```

2. 匿名函数
```
 var f
 f = function(x,y){
     return x+y
 }
 f.name // 'f'
```

3. 具名函数赋值
```
 var f
 f = function f2(x,y){ return x+y }
 f.name // 'f2'
 console.log(f2) // undefined
```

4. window.Function
```
 var f = new Function('x','y','return x+y')
 f.name // "anonymous"（匿名）
```

5. 箭头函数
```
 var f = (x,y) => {
     return x+y
 }
 var sum = (x,y) => x+y
 var n2 = n => n*n
```

## 调用函数

- f.call(asThis, input1,input2)<br>
其中 asThis 会被当做 this<br>
[input1,input2] 会被当做 arguments

### <font color="red">call/apply/bind</font>

1. call/apply
    - 改变this值
    - 操作参数
    - apply可以以数组形式传值

```
function print(b,c){

}
print.call({a:2},'hi','hello')
print.apply({a:2},['hi','hello'])
//{a:2}为this，b为‘hi’，c为‘hello’
```
2. bind
    - 切换上下文，第一个参数传this值
    - 科里化
    - 返回另一个函数

```
function fn(b,c){

}
let curryfn = fn.bind({a:2},'hi')
curryfn('hello')
//{a:2}为this，b为‘hi’，c为‘hello’
```

## this 和arguments

```
function f(){
    'use strict'//开启严格模式，才能显示出this的值，否则会显示this为Window
    console.log(this)
    console.log(arguments)
    return undefined
}
f.call(1,2,3) // this 为 1，arguments 为 [2,3]
```

## call stack

[普通调用](http://latentflip.com/loupe/?code=ZnVuY3Rpb24gYSgpewogICAgY29uc29sZS5sb2coJ2EnKQogIHJldHVybiAnYScgIAp9CgpmdW5jdGlvbiBiKCl7CiAgICBjb25zb2xlLmxvZygnYicpCiAgICByZXR1cm4gJ2InCn0KCmZ1bmN0aW9uIGMoKXsKICAgIGNvbnNvbGUubG9nKCdjJykKICAgIHJldHVybiAnYycKfQoKYS5jYWxsKCkKYi5jYWxsKCkKYy5jYWxsKCk%3D!!!)

[嵌套调用](http://latentflip.com/loupe/?code=ZnVuY3Rpb24gYSgpewogICAgY29uc29sZS5sb2coJ2ExJykKICAgIGIuY2FsbCgpCiAgICBjb25zb2xlLmxvZygnYTInKQogIHJldHVybiAnYScgIAp9CmZ1bmN0aW9uIGIoKXsKICAgIGNvbnNvbGUubG9nKCdiMScpCiAgICBjLmNhbGwoKQogICAgY29uc29sZS5sb2coJ2IyJykKICAgIHJldHVybiAnYicKfQpmdW5jdGlvbiBjKCl7CiAgICBjb25zb2xlLmxvZygnYycpCiAgICByZXR1cm4gJ2MnCn0KYS5jYWxsKCkKY29uc29sZS5sb2coJ2VuZCcp!!!)

[递归调用](http://latentflip.com/loupe/?code=ZnVuY3Rpb24gc3VtKG4pewogICAgaWYobj09MSl7CiAgICAgICAgcmV0dXJuIDEKICAgIH1lbHNlewogICAgICAgIHJldHVybiBuICsgc3VtLmNhbGwodW5kZWZpbmVkLCBuLTEpCiAgICB9Cn0KCnN1bS5jYWxsKHVuZGVmaW5lZCw1KQ%3D%3D!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)

## 作用域

拿到代码，先变量提升

1. 实例1

```
var a = 1
function f1(){
    alert(a) // 是多少
    var a = 2
}
f1.call()
```
变量提升==>
```
function f1(){
    var a 
    alert(a) // 是undefined
    a = 2
}
```
2. 实例2
```
var a = 1
function f1(){
    var a = 2
    f2.call()
}
function f2(){
    console.log(a) // 是1，因为f2属于全局变量，f1中的var a=2是局部变量，只在f1中有效
}
f1.call()
```
3. 实例3

```
var liTags = document.querySelectorAll('li')
for(var i = 0; i<liTags.length; i++){
    liTags[i].onclick = function(){
        console.log(i) // 点击第3个 li 时，打印 2 还是打印 6？==>6
    }
}
```

## 闭包

[参考网站](https://zhuanlan.zhihu.com/p/22486908)

- 如果一个函数使用了它范围外的变量，那么（这个函数+这个变量）就叫做闭包

```
var a=1
function f(){
    console.log(a)
}
f和a就组成了一个闭包
```

