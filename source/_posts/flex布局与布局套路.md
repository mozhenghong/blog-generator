---
title: flex布局与布局套路
date: 2018-10-30 14:21:35
tags:
---
## flex布局

1. flex container属性（父元素的属性）

- flex-direction:确定主轴方向
  - row从左到右
  - row-reverse从右到左
  - column从上到下
  - column-reverse从下到上

- flex-wrap:是否换行
  - nowrap不换行
  - wrap换行
  - wrap-reverse
- flex-flow:flex-direction与flex-flex-wrap的简写

- justify-content:主轴方向对齐方式
  - space-between两端无空隙
  - space-around
  - flex-start
  - flex-end
  - center
  
- alian-items:侧轴方向对齐方式
  - stretch：所有元素跟最高的一样高
  - flex-start
  - flex-end
  - center
  - baseline
  
- align-content:多行多列的对齐方式

2. flex item 的属性（子元素属性）
   
- flex-grow:增长比例（空间过多时，多余部分按子元素增长比例分配给各个子元素）

- flex-shrink：收缩比例（空间不够用时）

- flex-basis：默认的各个元素大小

- flex：flex-grow、flex-shrink、flex-basis的缩写

- align-self:自身的对齐方式

### 布局套路

1. 如果要支持IE8，就使用float布局，定宽；如果不需要支持IE8，就用flex布局，弹性宽度。

2. float
- 子元素全加 float: left （right）
- 父元素加 .clearfix
  
3. flex
- 父元素加 display: flex
- 父元素加 justify-content: space-between;
  
4. 如果宽度不够，可以用 margin: 0 -4px;

5. 使用calc

`width:calc(25%-8px)`

6. class不能为ad，否则会被当成广告屏蔽