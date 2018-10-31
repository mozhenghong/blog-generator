---
title: css-BFC
date: 2018-10-31 08:00:41
tags:
---
*BFC(block formatting context):块格式化上下文*

### 理解BFC

1. BFC和堆叠上下文都没有定义，只有特性/功能
   
   满足下列条件之一的就是块格式化上下文：
   
  - 根元素或其它包含它的元素
  - 浮动元素 (元素的 float 不是 none)
  - 绝对定位元素 (元素具有 position 为 absolute 或 fixed)
  - 内联块 (元素具有 display: inline-block)
  - 表格单元格 (元素具有 display: table-cell，HTML表格单元格默认属性)
  - 表格标题 (元素具有 display: table-caption, HTML表格标题默认属性)
  - 具有overflow 且值不是 visible 的块元素，
  - display: flow-root（让当前元素触发BFC，无其他用途）
  - column-span: all 应当总是会创建一个新的格式化上下文，即便具有 column-span: all 的元素并不被包裹在一个多列容器中。

### 功能

1. 功能1：爸爸管儿子

用 BFC 包住浮动元素。(这并不是清除浮动，.clearfix 才是清除浮动）<br>
儿子加float后，爸爸管不住儿子，但是给爸爸加以下其中一种，变为块格式化上下文，就可以管住儿子：

- float
- position:absolute;
- display:inline-block;
- overflow:auto;
- display:table-cell;
- display:flow-root;

2. 功能2：兄弟之间划清界限
   
- 两个BFC之间有界限<br>
  比如给一个`<div>`加float，给另一个兄弟`<div>`加`display:flow-root`就可以实现左右自适应布局。
  
- BFC是某个div的特性，BFC里可以有文档流。

- 如下代码：
```
<div class="parent">
<div class="children"></div>
</div>

.children{
    margin-top:30px;
}
```
parent不会包住children的margin，但如果把parent变为BFC就可以包住；或者给parent加一个border-top也可以。


