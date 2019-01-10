---
title: ES6-箭头函数
date: 2019-01-10 16:12:20
tags:
---
### 基本语法
1. 当有多个参数时

`(参数１，参数２，...参数n)=>{函数体}`

2. 当只有一个return时,{}可以省略

`(参数１，参数２，...参数n)=>表达式`

3. 当只有一个参数时，（）可以省略

`参数=>{函数体}`

4. 当没有参数时，只写一个（）即可

`()=>{函数体}`

###　箭头函数不绑定this

- 箭头函数不会创建自己的this,它只会从自己的作用域链的上一层继承this。
- 传统函数
```
function Person() {
  // Person() 构造函数定义 `this`作为它自己的实例.
  this.age = 0;

  setInterval(function growUp() {
    // 在非严格模式, growUp()函数定义 `this`作为全局对象, 
    // 与在 Person()构造函数中定义的 `this`并不相同.
    this.age++;
  }, 1000);
}
```
- 箭头函数
```
function Person(){
  this.age = 0;

  setInterval(() => {
    this.age++; // |this| 正确地指向person 对象
  }, 1000);
}
```

### 通过 call 或 apply 调用

- 由于 箭头函数没有自己的this指针，通过 call() 或 apply() 方法调用一个函数时，只能传递参数（不能绑定this)，他们的第一个参数会被忽略。
```
var adder1 = {
  base : 1,
    
  add : function(a) {
    var f = v => v + this.base;
    return f(a);
  },
adder1.add(1) //2

var adder2 = {
  add : function(a) {
    var f = v => v + this.base;
    var b={base:1}
    return f.call(b,a);
  },
adder2.add(1,3) //1会被忽略，a=3,返回4
```