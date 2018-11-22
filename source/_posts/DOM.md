---
title: DOM
date: 2018-11-22 10:47:04
tags:
---
## DOM

- <font color="blue">DOM是一棵树（tree），树上有Node，</font>Node 分为 Document（html）、Element（元素）和 Text（文本），以及其他不重要的。
- DOM中的O指的是Object,他是在内存中,按照树型结构,通过构造函数(如Node,Element(翻译为标签比较好),Document三个构造函数),构造出对象,将 DOM 展现到内存中。
- DOM树形结构如下，其中<font color="blue">每个节点(包括矩形节点和椭圆形节点)都是Node类型！</font>

![](https://upload-images.jianshu.io/upload_images/9617841-a5ee96193393ef7b.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

- document节点是Document构造函数的一个实例对象,document节点代表了整个文档(整个树型结构,我们可以通过直接输入`document`来获取document节点;html节点是Element构造函数的一个实例对象,html节点又叫根节点我们可以通过输入`document.documentElement`来获得html节点;
椭圆形的文本节点:"请输入文字" 是Text构造函数的一个实例对象(文本节点是Text构造函数的一个实例对象)

- Node Element Text 的关系如下图所示：

![](https://upload-images.jianshu.io/upload_images/9617841-dfadc5bdd4e4ebf6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## Node类型的一些属性和方法
### Node属性

1. 节点本身某些特征的属性:
    - Node.nodeName:
        - 看着DOM,如果你不确定某个Node节点是什么类型(不确定某个Node节点是矩形还是椭圆形)，例如document.body.nodeName//'BODY'
        - 返回节点类型,返回的值是大写的HTML元素名, 只有'svg'返回小写。
    - Node.nodeType:
        - 根据Node类型返回某些数字
        - Element类型,返回的数字是1
        - Text类型,返回的数字是3
        - Document类型,返回的数字的9
    - Node.textContent
        - 返回当前节点及其所有后代的文本内容
        - 值得注意的是,因为Node.textContent是Node属性,所以文本节点也是有textContent的，innerHTML和innerText是Element的属性,所以TextNode.innerHTML返回的是undefined,注意,并不是返回null
        - innerText也会返回当前节点及其所有后代的文本内容，但是会跳过script和style！
  
2. 节点结构关系属性
    - 兄弟关系
        - Node.nextSibling
        - Node.previousSibling
        - 以上两个属性可能会获取到空格（text节点）
    - 儿子关系
        - Node.childNodes（返回的是一个伪数组,里面是Node节点,并且伪数组内的值是动态变化的）
        - Node.firstChild
        - Node.lastChild
    - 父关系
        - Node.parentNode

### Node 方法

- Node.appendChild()

- Node.hasChildNodes()
    - 返回true或false

- Node.cloneNode()
    - （）中是什么也没有，或者值为false，则为浅拷贝，只拷贝当前节点
    - （）中值为true，则为深拷贝，会拷贝节点和节点中的所有内容 

- Node.insertBefore()

- Node.removeChild()

- Node.replaceChild()

- Node.contains()

- Node.isEqualNode()
    - 判断两个节点是否是相同的节点

- Node.isSameNode()
    -判断两个节点是否为同一个节点，类似于严格相等 

- Node.normalize()
    - 使常规化 

## document节点的一些属性和方法

### document属性

1. 用于指向其他节点(快捷获取某些特殊节点)的属性
   
    - document.documentElement指向 DOM 的 html节点
    - document.activeElement指向获得焦点的那个节点
  
2. 返回文档特定元素的伪数组集合的属性

    - document.links
        - 返回所有a标签
    - document.forms
    - document.images
    - document.embeds
3. 返回文档信息的属性
    - document.location
    - document.readyState返回的是当前文档的状态,
    
### document方法

1. 获取节点
    - document.querySelector(AAAA)
        - 返回的是第一个符合CSS选择器AAAA条件的节点 
        - 除了是 document ,还可以是某个 Node 节点
    - document.querySelectorAll(AAAA)
        - 除了是 document ,还可以是某个 Node 节点 
        - 返回的是伪数组,里面包含了所有符合选择器的节点 
        - 返回的结果不是动态的,不会实时反映元素节点的变化
    - document.getElementById()
    - document.getElementsByClassName()
    - document.getElementsByName()
        - 通过name属性获取节点 
    - document.getElementsByTagName()

2. 生成节点
    - document.createElement("div")生成Element节点，也就是div标签
    - document.createTextNode("你好")生成Text节点

3. 添加节点

    - xxx.appendChild（'div'）
        - 给id为xxx的元素添加div标签
        - 也可以添加文本节点