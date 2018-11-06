---
title: scss基础
date: 2018-11-05 23:05:26
tags:
---
## 学习环境
1. 安装parcel

- 在终端打开要编写scss的文件夹
- 运行以下命令安装parcel：

```
npm init -y
npm i -g parcel-bundler
```
- 运行`npx parcel index.html`得到网址，打开网址预览scss，可直接将scss转换为css

2. 在线学习环境
   
[codepen](https://codepen.io/)
## 语法

 1. 嵌套选择器
```
ul{
    属性：属性值；
    >li{
        属性：属性值；
    }
}
```
2. 变量

例如:<br>
```
$color:red;
body{
    border: 1px solid $color;
    div{
        background:$color;
    }
}
```
3. mixin

```
@mixin xxx($color){
border: 1px solid $color;
}
body{
    @include xxx(red);
}
```
4. placeholder

```
%box{
    box-shadow:0 0 3px block;
}
body{
    div{
        @extend %box;
    }
}
```

### scss相关

1. BEM（css命名法）
  
   Block Element Modifior

2. &符号

    可以用&代替父元素的class值

```
UserCard{
    UserCard-name{}
}
取代为：
UserCard{
    &-name{}
}
```
3. 嵌套属性
```
font:{
    size:16px;
    weight:blod;
}
```
4. 注释

```
单行：//xxxxxxx
多行：/*xxxx
      xxxx*/
```
5. 变量作用域

- 将变量放到某个选择器的{}中，作用域为这个选择器
- 作用域覆盖，就近原则
- `&red:#f60 !global`强制变为全局变量
- `$red-color`和`$red_color`被看作是一个变量

6. 运算

- css:`calc(200px / 2)`
- scss:直接做加、减、乘、模（100%3   //1）
- 除要满足其中一个条件:<br>
  .该值存在一个变量，例如`$red/3`<br>
  .用括号括起来，例如：`（100px/3）`<br>
  .该值作为另一个表达式的一部分，例如`100px/3-0`

7. 颜色相关运算

- `darken(颜色，10%)`颜色加深10%.
- 
 ```
 $red:#ff0000;
 color:$red+#888888;
 ==>color:#ff8888;
 ```
 8. 字符串插值

- `#{$red}`插入`#ff0000`字符串。

9. 循环
```
$step:25%
$n:10%
@keyframes animationname{
    @for $i from 0 to 4{
        #{$i*$step}{
            @if $i%2==0{
                transforrm:translateX(-$n)
                }else{
                    transform:translateX($n)
                }
        }
    }
}
```
### scss响应式

1. 动态缩放--单位：vw

- scss函数：
```
@function px($npx){
    @return $npx/375*100vw;
}
```
- 调用：

`width: px(61)`//宽度为61px，转换为vw单位。