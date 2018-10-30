---
title: css-堆叠上下文
date: 2018-10-30 11:05:57
tags:
---
### 堆叠顺序

1. 当父元素未被定位时(从里到外)：
   
   (1)z-index为负

   (2)background

   (3)border

   (4)div

   (5)float

   (6)文字、内联

   (7)position (z-index:0)

   (8)z-index大于0

   *同级相互比较，谁出现后谁靠前*

2. 当父元素被定位时(relative)（成立了一个堆叠上下文）

从里到外的顺序为(2)=>(3)=>(1)=>(4)=>(5)=>(6)=>(7)=>(8)

### 堆叠上下文(the stacking context)

**我们只知道一些属性会触发堆叠上下文，但并不知道堆叠上下文是什么，若满足下列条件之一的就是堆叠上下文：**

- 根元素 (HTML),
- z-index 值不为 "auto"的 绝对/相对定位，
- 一个 z-index 值不为 "auto"的 flex 项目 (flex item)，即：父元素 display: flex|inline-flex，
- opacity 属性值小于 1 的元素（参考 the specification for opacity），
- transform 属性值不为 "none"的元素，
- mix-blend-mode 属性值不为 "normal"的元素，
- filter值不为“none”的元素，
- perspective值不为“none”的元素，
- isolation 属性被设置为 "isolate"的元素，
- position: fixed
- 在 will-change 中指定了任意 CSS 属性，即便你没有直接指定这些属性的值
- -webkit-overflow-scrolling 属性被设置 "touch"的元素
