---
title: js里的数据类型转换
date: 2018-11-13 10:20:08
tags:
---
## 转为字符串

1. toString()
   ```
   var n=1
   n.toString()//"1"
   ```
*不可以转null和undefined*

2. string（）

   ```
   var n=1
   window.string(n)//"1"
   ```
   *可以转null和undefined*

3. +''

```
1+''  //'1'
null+''  //'null'
obj+''  //'[object,Object]'
```
*可以转null和undefined*

## 转为Boolean

1. Boolean()

   - falsy值：0、NaN、''、null、undefined、false
   - Boolean（falsy值）返回false，其余返回true

2. 取返两次

   - !!1  //true
   - !!null //false

## 转为Number

1. Number('1')===1

2. parseInt('1',10)===1
   - 用于将字符串转化为整数，第二个参数为被解析的值的进制
   - 如果字符串头部有空格，空格会被自动去除
   - 如果参数不是字符串，会先转化为字符串再转化
   - 字符串转为整数时，是一个一个字符依次转换，如果遇到不能转换的字符，就不再进行下去，返回已经转好的部分
   - 如果字符串第一个字符不能转换为数字（+、-除外），返回NaN

3. parseFloat(1.23)===1.23
    - 将一个字符串转化为浮点数
    - 空字符串‘’会转化为NaN

4. 字符串减去0：`'1'-0 ` //1
5. 取正：`+'1'`//1;`+'-1'`//-1


# 内存图

- 买一个 8G 的内存条<br>
操作系统开机即占用 512MB<br>
Chrome 打开即占用 1G 内存<br>
Chrome 各每个网页分配一定数量的内存<br>
这些内存要分给页面渲染器、网络模块、浏览器外壳和 JS 引擎（V8引擎）<br>
JS 引擎将内存分为代码区和数据区<br>
我们只研究数据区,数据区分为 Stack（栈内存） 和 Heap（堆内存）<br>
<font color="red">简单类型的数据直接存在 Stack 里<br>
复杂类型的数据是把 Heap 地址存在 Stack 里</font><br>

## 实例（画图解决）

1. 实例1
```
var a = 1
var b = a
b = 2
请问 a 显示是几？//1
``` 
2. 实例2
```
var a = {name: 'a'}
var b = a
b = {name: 'b'}
请问现在 a.name 是多少？//'a'
```
3. 实例3
```
var a = {name: 'a'}
var b = a
b.name = 'b'
请问现在 a.name 是多少？//'b'
```
4. 实例4
```
var a = {name: 'a'}
var b = a
b = null
请问现在 a 是什么？//{name: 'a'}
```

## 深拷贝&&浅拷贝
1. 深拷贝
```
var a = 1
var b = a
b = 2 //这个时候改变 b
a 完全不受 b 的影响
那么我们就说这是一个深拷贝
```
- 对于简单类型的数据来说，赋值就是深拷贝。
对于复杂类型的数据（对象）来说，才要区分浅拷贝和深拷贝。

2. 浅拷贝

```
var a = {name: 'frank'}
var b = a
b.name = 'b'
a.name === 'b' //对 b 操作后，a 也变了
```