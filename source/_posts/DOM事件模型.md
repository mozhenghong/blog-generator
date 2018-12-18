---
title: DOM事件模型
date: 2018-12-17 23:53:10
tags:
---
### onclick和addEventListener

1. 关于onclick

```
function print(){}
<button id="x" onclick="print">A</button>//错误
<button id="y" onclick="print()">B</button>//正确
x.onclick = print//正确
x.onclick = print()//错误
```
- 不能同时添加多个onclick事件，后面添加的会覆盖前面添加的
```
x.onclick = function(){
    console.log(1)
}
x.onclick = function(){
    console.log(2)
}
//最终点击ｘ时会打印出２，因为后一次会覆盖前一次
```
2. 关于addEventListener
- 后一次添加的事件不会覆盖前一次的，会加到前一后面，也就是说可以给同一元素添加多个click事件,每添加一个, 都会进入click的队列里, 然后依次执行,每种事件有各自不同的队列
- removeEventListener
```
x.addEventListener('click',function(){
    console.log(1)
})
x.addEventListener('click',function(){
    console.log(2)
})
//会依次打印出１和２
```

## 事件捕获和事件冒泡

- 有以下一段html内容：

```
<div id="grand">
爷爷
    <div id="parent">
    爸爸
        <div id="son">
        儿子
        </div>
    </div>
</div>

//script
<script>
    grand.addEventListener('click',function f1(){},第三个参数)
    parent.addEventListener('click',function f2(){},第三个参数)
    son.addEventListener('click',function f3(){},第三个参数)
</script>
```
- 当点击儿子时，f1,f2,f3都会被调用
- 若第三个参数为true，则调用顺序为f1,f2,f3 ==>事件捕获
- 若第三个参数不填或者第三个　参数为五个falsy值中的一个，则调用顺序为f3,f2,f1 ==>事件冒泡
- 一般情况下为先捕获再冒泡
- 特例：若儿子有两个click事件，一个为true(捕获)，一个为false(冒泡)，当点击儿子时，儿子上的函数执行顺序会按书写顺序执行，并不会再遵循先捕获再冒泡的规则。
```
son.addEventListener('click',function f3(){})
son.addEventListener('click',function f4(){},true)
son.addEventListener('click',function f5(){},true)
点击son时，会依次执行f3,f4,f5
```