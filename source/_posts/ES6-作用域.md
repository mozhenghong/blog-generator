---
title: ES6-作用域
date: 2019-01-10 11:27:44
tags:
---
## 块级作用域

- 通过var声明的变量没有块级作用域，var会变量提升，只有函数才能包住var
  - 例如：
```
var a = 1;
{
    var a = 2
}
console.log(a)//2
```
- let和const有块级作用域
    - 例如：
```
let a = 1;
{
    let a = 2;
}
console.log(a)//1
```
```
const a = 1;
{
    const a = 2;
}
console.log(a)//1

注意：作用域里的常量声明 const a = 2 并不会抛出SyntaxError: Identifier 'a' has already been declared这样的语法错误，因为这是一个新的作用域。
```
### let

- 特点
  - let的作用域在最近的{}之间，let不会变量提升
  - 如果在let a　之前使用a，那么报错
  - 如果重复let a，那么报错。
- let的暂存死区
    - 在同一个作用域中，用let重复定义一个变量，将引起TypeError

```
if(x){
    let foo;
    let foo; // TypeError thrown.
}
```
- 在 ECMAScript 2015(ES6) 中，let 绑定不受变量提升的约束，这意味着 let  声明不会被提升到当前执行上下文的顶部，在块中的变量初始化之前，引用它将会导致 ReferenceError（而使用 var 声明变量则恰恰相反，该变量的值是 undefined ）。这个变量处于从块开始到 let 初始化处理的”暂存死区“之中。
```
function fn(){
    console.log(a);  //undefined
    console.log(b); //ReferenceError: b is not defined
    var a = 1;
    let b = 2;
}
```
### const

- 特点
  - const的作用域在最近的{}之间
  - 如果在const a　之前使用a，那么报错
  - 如果重复const a，那么报错
  - const只有一次赋值机会，声明变量时必须赋值，赋值后将无法改变。

- 注意
```
const a = 7;

//(1)
a = 20; //再次赋值会报错

//(2)
const a = 20; // 尝试再次声明会报错
var a =20;
let a =20;//不管用什么声明都会报错

//(3)
if(a===7){
    let a =20 //这个a只在{}这个块级作用域中
    console.log(a) //20
}

const obj = {name: 'momo'}
obj = {NAME:'MOMO'} //报错，不可以再次赋值
obj.name = 'tom' //成功！！
```
<font color ="red">const定义变量之后，我们不可以修改stack上的内容，但是可以修改heap上的内容</font>