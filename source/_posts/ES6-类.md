---
title: ES6-类
date: 2019-01-11 16:24:44
tags:
---
## 原型

- `obj.toString()`等价于<br>`window.Object.prototype.toString.call(obj)`<br>
call里面的obj是this

- 类：拥有相同属性的对象
- 构造函数：用来创建某个类的对象的函数

## 类

#### 类声明
- 要声明一个类，你可以使用带有class关键字的类名
- constructor里面写自由属性
- constructor外面写person类的共有属性

```
class person{
    constructor(name,age){
        this.name = name;
        this.age = age;
    }
    walk(){
        console.log('走两步')
    }    
}
－－－－－－－－－－－－－－－－－－－
var momo = new person('momo',18)
```
- 结果如下：
![](https://upload-images.jianshu.io/upload_images/14473072-da72309af169b818.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

#### 继承

- extends 关键字在类声明中用于创建一个类作为另一个类的一个子类。
- super()用于调用对象的父对象上的函数

```
class Animals{
    constructor(name){
        this.name = name;
    }
    walk(){
        console.log('走两步')
    }
}
class dog extends Animals{
    constructor(age){
        super()　//执行Ａnimals的constructor,将Ａnimals的constructor中的内容弄过来

        this.age = age;
    }
    speak(){
        console.log('旺旺')
    }
}
var p = new dog(3)
```
- 运行结果如下：
  
![](https://upload-images.jianshu.io/upload_images/14473072-5d098d7842491d66.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

####　静态方法

- static 关键字用来定义一个类的一个静态方法.
- 静态方法是可以直接用class后面类名调用的方法，例如　person.xxx

```
class person{
    constructor(name){
        this.name = name;
    }
    static speak(){
        console.log('chinese')
    }
    walk(){
        console.log('walk')
    }
}

person.speak() // 打印出'chinese'

person.walk()  //报错！
```