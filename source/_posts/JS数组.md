---
title: JS数组
date: 2018-11-20 09:31:11
tags:
---
[Array用法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)

### 基本用法

1. Array(3)//{length:3} ,3表示length

![](https://upload-images.jianshu.io/upload_images/9617841-a9b61fdcc747037f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. Array(3,3) // [3,3] ,第一个3并不表示length了

![](https://upload-images.jianshu.io/upload_images/9617841-c122282b21cd4d22.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 构造函数

- 基本类型==>Number、String、Boolean
    - 不加new，返回基本类型
    - 加new，返回对象

![](https://upload-images.jianshu.io/upload_images/9617841-132d603817f9982d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- 复杂类型==>Array、Function
    - 不加new，返回对象
    - 加new，也返回对象

![](https://upload-images.jianshu.io/upload_images/9617841-7811060a8850d0c1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### Js中数组的本质

- 人类理解：数组就是数据的有序集合
- JS理解：数组就是原型链中有 Array.prototype 的对象
- 伪数组
    - 有 0,1,2,3,4,5...n,length 这些 key 的对象
    - 原型链中没有 Array.prototype
    - 目前知道的伪数组有：<br>
    arguments 对象<br>
    document.querySelectAll('div') 返回的对象

## 数组的API

1. Array.prototype.forEach

forEach() 方法对数组的每个元素执行一次提供的函数。返回值为undefined<br>
forEach()参数必须为一个函数<br>
函数必须有三个参数，一个为数组当前项的值（value），一个为数组当前项的索引（key），一个为数组对象本身

![](https://upload-images.jianshu.io/upload_images/9617841-e8c7cd125f9b2e37.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. Array.prototype.sort

sort() 方法对数组的元素进行排序，并返回数组。默认排序顺序是根据字符串Unicode码点。<br>
<font color="red">sort()是这几个方法中唯一会改变原数组的方法</font><br>
sort()有一个函数作为参数，这是用来指定按某种顺序进行排列的函数。如果省略，元素按照转换为的字符串的各个字符的Unicode位点进行排序。

![](https://upload-images.jianshu.io/upload_images/9617841-f78236beb364d19c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. Array.prototype.join

join() 方法将一个数组（或一个类数组对象）的所有元素连接成一个字符串并返回这个字符串。

![](https://upload-images.jianshu.io/upload_images/9617841-fba21a8564d3f1bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. Array.prototype.concat

concat() 方法用于合并两个或多个数组。此方法不会更改现有数组，而是返回一个新数组.

![](https://upload-images.jianshu.io/upload_images/9617841-348394b630333463.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

5. Array.prototype.toString

toString() 返回一个字符串，表示指定的数组及其元素。Array对象覆盖了Object的 toString 方法。对于数组对象，toString 方法连接数组并返回一个字符串，其中包含用逗号分隔的每个数组元素。

![](https://upload-images.jianshu.io/upload_images/9617841-21580db3dc09576d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6. Array.prototype.map

map() 方法创建一个新数组，其结果是该数组中的每个元素都调用一个提供的函数后返回的结果

![](https://upload-images.jianshu.io/upload_images/9617841-340dd88cb736c641.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

7. Array.prototype.filter

filter() 方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。 

![](https://upload-images.jianshu.io/upload_images/9617841-4c9d9c267ed7d86d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

8. Array.prototype.reduce

reduce() 方法对累计器和数组中的每个元素（从左到右）应用一个函数，将其简化为单个值。

![](https://upload-images.jianshu.io/upload_images/9617841-216d455abd6bd302.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1. Array.prototype.push

push() 方法将一个或多个元素添加到数组的末尾，并**返回该数组的新长度**。

![](https://upload-images.jianshu.io/upload_images/9617841-8b13f339c0ecc379.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

10. Array.prototype.pop

pop()方法从数组中删除最后一个元素，并**返回该元素的值**。此方法更改数组的长度。

![](https://upload-images.jianshu.io/upload_images/9617841-b83fa79fa9aab7dc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)