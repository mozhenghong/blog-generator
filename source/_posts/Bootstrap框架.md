---
title: Bootstrap框架
date: 2018-10-31 11:48:25
tags:
---
### 概述

*Bootstrap 是一个用于前端开发的开源工具包，Bootstrap 可以适配所有设备，主要就是采用了媒体查询功能*

[bootstrap中文官网](http://www.bootcss.com/)<br>
[bootstrap英文官网](https://getbootstrap.com/)

## 起步

1. 下载

进入bootstrap中文官网后，点击起步，会出现下载方式,根据需求选择下载方式：

![](https://upload-images.jianshu.io/upload_images/14473072-c3ed754a6884930b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 生产环境：程序所在的机器 | 操作系统面向真实的用户
- 开发环境：只给自己 | 内部人员使用的程序，例如 http-server

2. 引入bootstrap

将bootstrap里面的三个文件夹移到自己的项目文件夹下，然后在HTML中插入如下代码：

```
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">

<!-- 最新版本的 Bootstrap 核心 CSS 文件 -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">

<script src="./js/jquery-3.3.1.min"></script>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js" integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa" crossorigin="anonymous"></script>
```

- bootstrap 的所有 JavaScript 插件都依赖 jQuery，因此 jQuery 必须在 Bootstrap 之前引入（可以去[官方网站](http://jquery.com/)下载，或者在终端中运行`npm i jquery`安装，安装完成后，把文件放在项目文件夹的js目录下）

- Bootstrap 是移动设备优先的。所以添加meta标签，通过为视口（viewport）设置 meta 属性为 user-scalable=no 可以禁用其缩放（zooming）功能。

### 栅格系统

- Bootstrap 提供了一套响应式、移动设备优先的流式栅格系统，随着屏幕或视口（viewport）尺寸的增加，系统会自动分为最多12列。
- 栅格系统用于通过一系列的行（row）与列（column）的组合来创建页面布局，你的内容就可以放入这些创建好的布局中。
- “行（row）”必须包含在 .container （固定宽度）或 .container-fluid （100% 宽度）中，以便为其赋予合适的排列（aligment）和内补（padding）。
- 通过“行（row）”在水平方向创建一组“列（column）”。
- 你的内容应当放置于“列（column）”内，并且，只有“列（column）”可以作为行（row）”的直接子元素。

- 栅格参数(通过下表可以详细查看 Bootstrap 的栅格系统是如何在多种屏幕设备上工作的)：

![](https://upload-images.jianshu.io/upload_images/14473072-cf03784a87b0160d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 使用方法

- 去官方网站根据需求的样式复制粘贴代码，不要自己写代码！如果非要加一些 CSS 属性，此时需要加一层 div ，用来添加自己的样式
