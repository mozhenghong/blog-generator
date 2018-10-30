---
title: css-宽度与高度
date: 2018-10-30 10:29:49
tags:
---

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

2. 内联元素居中：<br>给父元素加text-align:center;<br>
*内联元素是无法设置宽高的，宽高可以用padding代替，或者设dispaly:inline-block*

#### 空格

- HTML中的内联元素不能靠空格或回车来加空格，不管加多少回车和空格都会被默认为只有一个空格。**要使用&nbsp来添加空格**

#### 单行文字两端对齐

  ```
  span::after{
      content:'';
      display:inline-block;
      width:100%;
  }
  ```
### 文字溢出省略

1. 单行文本多出以...来显示

```
white-space:nowrap;
overflow:hidden;
text-overflow:ellipsis;
```

2. 多行文本溢出省略
   
   *可搜索 `css multi line text ellipsis`得到css代码*

```
overflow: hidden;
display: -webkit-box;
-webkit-line-clamp: 3（行数）;
-webkit-box-orient: vertical; 
```

#### 文字垂直居中

`padding-top = padding-bottom`<br>

*尽量不要写height*

### 宽高不确定时实现居中

```
display:flex;
justify-content:center;
align-items:center;
```

#### 实现一个与浏览器1:1的div

`padding-top: 100%;`