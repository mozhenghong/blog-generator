---
title: css基础
date: 2018-10-29 14:53:41
tags:
---
### 引入css
- 内联样式，style属性，在HTML标签中写入style=“属性：属性值”

- 内嵌样式，style标签，将style标签写到head标签中：
```
<style>
选择器{
    属性：属性值；
}
</style>
```

- 外联式，link标签
  ```
  <link rel="stylesheet" herf="./a.css">
  ```

- 在 a.css 中写:
  ```
  @import url(./b.css)
  ```

### 横向布局 ==>浮动

- 子元素：float：left；

- 父元素：class=“clearfix”

- 清除浮动：
```
.clearfix::after{
    content:"";
    display:block;
    clear:both;
}
```

#### 去除默认样式

- `<ul>、<ol>`一般要加`list-style:none;`

- `<a>`一般加`text-decoration:none;`

- 一般在css中加`*{margin:0;padding:0;}`
  
- font-weight:bold; 加粗
  
  font-weight:normal;不加粗

#### 下划线

- 要做到鼠标悬浮在上面时有下划线，并且不会出现别的格式变动：
```
a{border-bottom:2px solid transparent;}
a:hover{border-bottom:2px solid red;}
```

## 用css画三角形

利用border画三角形：
```
div{
    border:10px solid transparent;
    width:0px;
    border-left-color:red;
    border-top-width:0px;
}
```

## 伪元素

- 不是真元素，但相当于一个隐藏的内联元素，可用伪元素代替div。
```
div::before{
    content:"";
    dispaly:block;
    ......
}
div::after{
    content:"";
    display:block;
    ......
}
```
#### generator

1. 线性渐变生成器：搜索css3 linear gradient generator

2. 阴影生成器：搜索css shadow generator

### 帧动画

1. 关键帧
```
@keyframes name{
    0%{transform:rotate(0deg)}
    100%{transform:rotate(360deg)}
}
```
2. 属性
   
- animation-name:定义动画名称。
- animation-duration:定义动画播放时间。
- animation-timing-function:linear 定义动画类型。
- animation-iteration-count:infinite/number定义动画播放次数。
- animation-direction:alternate 定义动画来回播放。

#### 进度条

1. `<progress max=" "  value=" ">`
2. 两个div嵌套，加不同的background，父元素height确定，子元素height：100%

### 盒模型

定义显示方式：

1.box-sizing:content-box;<br>
width/height=content;<br>
2.box-sizing:border-box;<br>
width/height=border+padding+content<br>

### 伪类

:link ==>:visited ==>:hover ==>active<br>
:focus<br>
:first-child 选择第一个元素<br>
:last-child<br>
;nth-child()

