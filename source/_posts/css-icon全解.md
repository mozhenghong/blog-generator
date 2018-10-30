---
title: css-icon全解
date: 2018-10-30 11:23:50
tags:
---
#### Photoshop

1. 拿到的设计图为psd格式要转换成png格式的单个图标

在图上右键==>点击要选的图层，得到图层==>在图层上右键，复制图层（duplicate layer）==>image ==>trim(裁剪)==>image==>canvas size(修改画布大小)==>file==>export==>quick export png(导出png格式)

2. 拿到png格式设计图

用Photoshop打开png==>选中其中一个图标==>image==>crop(剪切)==>选择魔法棒工具==>选中要选择的区域==>右键==>select inverse==>按delete键删除==>右键==>decelect==>image==>trim==>image==>canvas size(修改画布大小)==>file==>export==>quick export png(导出png格式)

## icon的各种做法

1. `<img>`法

可自适应宽高，改变宽，高也会自动改变，会保持原本的默认比例。

2. `<background>`法

3. SVG 法（推荐）

（1）在[iconfont网站](http://iconfont.cn)搜索想要的矢量图，加入购物车

（2）点击添加至项目

![](https://upload-images.jianshu.io/upload_images/14473072-fc9ac8b16ef187d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

(3）点击symbol，将下方代码复制到script的src中

![](https://upload-images.jianshu.io/upload_images/14473072-60d921b2cd9d245c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

(4)点击使用帮助，然后按照symbol引用下的要求做即可。