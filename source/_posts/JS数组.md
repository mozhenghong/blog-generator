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

- for...of可以遍历数组,得到value

![](https://upload-images.jianshu.io/upload_images/9617841-db503fb1228e3fc1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

1. Array.prototype.sort

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

9. Array.prototype.push/Array.prototype.unshift()

- push() 方法将一个或多个元素添加到数组的末尾，并**返回该数组的新长度**。
- unshift()将一个或多个元素添加到数组的开头，并返回该数组的新长度。

![](https://upload-images.jianshu.io/upload_images/9617841-8b13f339c0ecc379.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

10. Array.prototype.pop/Array.prototype.shift()

- pop()方法从数组中删除最后一个元素，并**返回该元素的值**。此方法更改数组的长度。
- shift() 方法从数组中删除第一个元素，并返回该元素的值。此方法更改数组的长度。

![](https://upload-images.jianshu.io/upload_images/9617841-b83fa79fa9aab7dc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

11. Array.prototype.includes()

- 用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回 true，否则返回false
- 第一个参数为需要查找的参数值，第二个参数（可选）表示从哪个位置开始查找，如果值为负数，则整个数组都会被搜索。

![](https://upload-images.jianshu.io/upload_images/9617841-5229cf3ed2d534c5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

12.  Array.prototype.indexOf()

- 返回在数组中可以找到一个给定元素的第一个索引，如果存在，返回这个元素所在的位置；如果不存在，则返回-1.
- 相当于严格相等===去找是否存在某元素，例如两个对象值一样，但地址不一样，则不会被找到。

![](https://upload-images.jianshu.io/upload_images/9617841-c6ac59398101157e.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

13.  Array.prototype.lastIndexOf()

- 返回指定元素（也即有效的 JavaScript 值或变量）在数组中的最后一个的索引，如果不存在则返回 -1。

![](https://upload-images.jianshu.io/upload_images/9617841-a9ff01808ccb62d4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

14.  Array.prototype.find()
    
- 返回数组中满足提供的测试函数的第一个元素的值。否则返回 undefined。返回的是找到的值

![](https://upload-images.jianshu.io/upload_images/9617841-cf80ed21f10b4b41.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

15. Array.prototype.findIndex()

- 返回数组中满足提供的测试函数的第一个元素的索引。否则返回-1。返回的是找到的值的位置。

![](https://upload-images.jianshu.io/upload_images/9617841-af07bc56cb96214a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

16. Array.prototype.some()

- 判断数组里是否有任意一个元素满足回调，找到了一个就不再往下执行。 

![](https://upload-images.jianshu.io/upload_images/9617841-01b83341271af7a5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

17. Array.prototype.every()

- 判断数组里是否所有元素都满足回调。

![](https://upload-images.jianshu.io/upload_images/9617841-d1fdae4c086933d9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

18. Array.prototype.slice()

- 截取数组的一部分,如下[2,3)

![](https://upload-images.jianshu.io/upload_images/9617841-c112cf364a6afb9f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

19. Array.prototype.splice()

- splice()方法通过删除现有元素和/或添加新元素来修改数组,返回被删除的内容。

![](https://upload-images.jianshu.io/upload_images/9617841-795c795e9cc8e0df.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)