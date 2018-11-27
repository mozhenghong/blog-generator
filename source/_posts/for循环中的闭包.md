---
title: for循环中的闭包
date: 2018-11-27 14:07:29
tags:
---
1. 问题

- 以下代码中原本是想每次点击对应的目标弹出对应的数字下标0-9，但实际上无论点击哪个目标都会弹出数字10.
```
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <div class="parent">
        <div class="child">0</div>
        <div class="child">1</div>
        <div class="child">2</div>
        <div class="child">3</div>
        <div class="child">4</div>
        <div class="child">5</div>
        <div class="child">6</div>
        <div class="child">7</div>
        <div class="child">8</div>
        <div class="child">9</div>
    </div>
    <script>
       var childArray= document.getElementsByClassName('child')
       for(var i=0;i<childArray.length;i++){
           childArray[i].onclick=function(){
               console.log(i)
           }
       }
    </script>
</body>
</html>
```
<font color="blue">上面代码中，当执行onclick事件时循环已经结束了，这时打印的i是外部定义的i，此时i=10（变量i和这个函数形成了闭包）</font>

2. 解决方法

    - 方案1：将var改为let
    ```
    let childArray = document.getElementsByClassName('child');
        for (let i = 0; i < childArray.length; i++) {
            childArray[i].onclick = function () {
                console.log(i);
            }
        }
    ```
    let定义的变量作用域为块级作用域，只在{}中有效。
    - 方案2：增加闭包
    ```
     for(var i=0;i<childArray.length;i++){
        childArray[i].onclick = function () {
                    var copy = i;
                    return function () {
                        console.log(copy);
                    }
                }();
    }
    ```
    - 方案3：立即执行函数
    ```
    for(var i=0;i<childArray.length;i++){
    (function () {
                var copy = i;
                childArray[i].onclick = function () {
                    console.log(copy);
                };
            })();
    }
    ```
    上述代码每执行一次，就会产生一个对象存储copy和onclick函数
    - 方案4:与方案3相似
    ```
    for(var i=0;i<childArray.length;i++){
        (function (arg) {
        childArray[i].onclick = function () {
            console.log(arg);
        };
        })(i);
     }
    ```