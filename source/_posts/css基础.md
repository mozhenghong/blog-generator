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

## 文档流

- 文档内元素的流动方向。<br>
  内联元素：从左到右；<br>
  块级元素：从上到下，每块占一行。

- 块级元素高度由其内部文档流高度总和决定（不一定相等）。<br>内联元素高度与字体有关。（设计师设计字体时有建议行高）。

## 脱离文档流

- 父级元素高度不再受脱离文档流的子元素的高度控制。

1. float
2. position:fixed;
3. 绝对定位：
  - 父元素：position:relative;
  - 子元素：position：absolute；
4. 绝对定位是相对于父元素定位，若要通过定位实现居中，可以：<br>top:50%;<br>transform:translateY(-50%);<br>消除自身原本高度带来的不居中。
   
#### 居中

1. 块级元素居中：<br>margin-left:auto;<br>margin-right:auto;

2.内联元素居中：<br>给父元素加text-align:center;<br>
*内联元素是无法设置宽高的，宽高可以用padding代替，或者设dispaly:inline-block*

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

