---
title: css-移动端页面（响应式）
date: 2018-10-30 14:07:44
tags:
---
### media query 媒体查询

```
<style>
    @media(条件1)and(条件2){
        选择器{属性：属性值；}
    }
</style>
```
*写在后面的优先级大*

### 隐藏元素

- `display:none;`

- 不同屏幕大小切换状态==>@media
- 同一屏幕切换状态==>js
  
### 手机端要加一个meta

```
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

### 手机端的交互方式

- 没有hover
- 有touch事件，click==>touch
- 没有resize
- 没有滚动条
