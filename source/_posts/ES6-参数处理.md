---
title: ES6-参数处理
date: 2019-01-10 16:53:36
tags:
---
## 默认参数值

- 函数默认参数允许在没有值或undefined被传入时使用默认形参。

```
function sum(a=0,b=0){
    return a+b    
}
sum()   //0+0=0
```

- 传入undefined或者其它假值
  - 只有传入undefined时候才会用默认值，传入其它假值，用的都是假值 
```
function fn(a=1,b=2){
    console.log(a,b)
}
fn(undefined,null) //1,null
```

- 在函数被调用时，参数默认值就会被解析，调用一次，解析一次
```
function append(value, array = []) {
  array.push(value);
  return array;
}

append(1); //[1]
append(2); //[2], 1不会保留在里面，再次解析array为[],所以返回的不是[1,2]
```

- 非默认参数位于默认参数之后
```
function fn(x=1,y){
    return[x,y]
}

fn()   //[1,undefined]
```

## 剩余参数

- 剩余参数语法允许我们将一个不定数量的参数表示为一个数组。

#### 语法
```
function (a,b,...args){

}
```
如果函数的最后一个命名参数以...为前缀，则它将成为一个由剩余参数组成的<font color="red">真数组</font><br>
上面例子中args将收集该函数的第三个参数（因为第一个参数被映射到a，而第二个参数映射到b）和所有后续参数。

#### 剩余参数和arguments对象的区别

- 剩余参数只包含那些没有对应形参的实参，而arguments对应了传给函数的所有实参。
- arguments是一个伪数组，而剩余参数是一个真数组

####　arguments从伪数组变成真数组

1. `let args = Array.prototype.slice.call(arguments)`

2. `let args = Array.from(arguments)`

3. `let args = [...arguments]` 

## 展开运算符

#### 在函数调用时使用展开语法
- 等价于apply的方法
```
funtion fn(x,y,z){

}
let args = [1,2,3];
fn.apply(null,args);
//等价于
fn(...args)
```

#### 构造字面量数组时使用展开语法
```
var array1 = [1,2,3,4,5,6]
var [,,,...array2]=array1  //array2=[4,5,6]
var arr3=[0,...array1,7]   //array3=[1,2,3,4,5,6,7]
```
#### 构造字面量对象时使用展开语法
```
var obj1 = {name: 'leo',age: 14}
var obj2 = {name:'tom', x:26}
var obj3 = {...obj1}  　//{name: 'leo',age: 14}
var obj4={...obj1,...obj2}    //{name:'tom',age: 14 ,x:26}
//由于先传入obj1，再传入obj2，所以obj2会覆盖与obj1中相同的部分
```