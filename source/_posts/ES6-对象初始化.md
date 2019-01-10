---
title: ES6-对象初始化
date: 2019-01-10 23:37:03
tags:
---
### 产生一个新对象（对象初始化）

1. `var a = new Object()`产生了一个空对象，有__proto__属性指向object

2. `var b = Object,create(null)`,产生了一个空对象，但是没有__proto__

3. `var c = Object.create(Object,prototype)`产生一个空对象，有__proto__

4. `var d = {}`,产生一个空对象，有__proto__

### 属性定义

```
var a = 1;
var b = 2;
var obj = {
    a:a,
    b:b
} 
// obj = {a: 1,b: 2}

//转为ES6的写法
var obj = {a,b}  //a的值为a,b的值为b
```
- 属性名可以是表达式

```
var name = 'a'
var obj = {[name]:1}  //obj={a:1}
用属性放在[]中，表示引用变量
```
### 方法定义

- get 、set
```
var o ={
    _age = 18,
    get age(){return o._age},
    set age(value){
        if(value<100){
            o._age = value
        }else{
            o._age = 100
        }
    }
}

o.age   //返回１８
o.age = 1000  // 0.age返回100
```
### Object.defineProperty()

```
var a;
var i = 0;
Object.defineProperty(window,'a',{
    get(){
        i+=1;
        return i
    }
})

// a===1&&a===2&&a===3成立
```
### Object,assign()

- 将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。

```
var obj1 =　{a:1,b:2,c:3}
var obj2 = Object.assign({},obj1)
obj2  //{a:1,b:2,c:3}

//把obj1中的每一个key,value都复制到{}中，然后返回这个对象
//实现浅拷贝，改变obj2.a不影响obj1.a

－－－－－－－－－－－－－－－－－－
var obj3 = {...obj1}
//实现的效果与obj２相同
```

###　writable 、configurable 、enumerable

- writable
    - 要实现属性只读有两种常见方法：
```
//只写get方法，不写set方法
var o = {
    get name(){return 'leo'}
}
//将writable设为false
Object.defineProperty(o,'name',{value:'leo',writable:false})

o.name  //’leo‘
o.name = 'tom'  //o.name还是’leo‘
```
- configurable
    - 是否可配置 
- enumerable
  - 是否可枚举（是否能被遍历）
```
var o={a:1,c:3}
Object.defineProperty(o,'b',{value:2,enumerable:false})
for(let key in o){
    console.log(key)   //打印出a、c
}
``` 
- `Object.getOwnPropertyDescriptor(o,'b')`可以查看对象ｏ中的'b'属性是否可写、可枚举、可配置等详细信息