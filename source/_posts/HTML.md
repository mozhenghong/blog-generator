---
title: HTML
date: 2018-10-24 09:28:56
tags:
---
## HTML

 1. Hyper Text Markup Language(超文本标记语言)
 
 2. 除了`<div>`和`<span>`,其它标签都有默认样式。

##### 空元素

-  HTML中，有以下常见的空元素：
```
<hr>  水平分割线 
<br>  回车
<img src="">
<input type="" value="">
<meta charset="UTF-8">
<link href="" rel="stylesheet">
<col width="">  定义列宽
```

##### `<head>`

-  `<head>`中包含以下元素：

```
<meta>
<link>
<title>
<style>
<scripe>
<noscript> 定义脚本未被执行的替代内容
<base> 指定用于一个文档中包含的所有相对URL的基本URL，一个HTML中只能有一个<base>空标签
```

###### 描述列表

- 结构一般如下：

```
<dl>   description list 
<dt>   description term
<dd></dd>    description definition
</dt>
</dl>
```

##### 可替换元素

-  在css里，可替换元素的展现不是由css控制的，这些元素外观渲染独立于css的外部对象。

- 可替换原宿主要有以下几个

```
<img>
<object>
<video>
<textarea>
<input>
```
##### `<iframe>`

- HTML内联框架元素表示嵌套的浏览上下文，有效地将另一个HTML页面嵌入到当前页面中。默认高度50px，宽度100px.(width可以为100%，height不可以为100%)

- 属性:

1. name ==> 嵌入的浏览上下文（框架）的名称。该名称可以用作*`<a>`标签*，*`<form>`标签*的`target`属性值。

2. frameborder = 0；清除 iframe 的默认border。
src ==> 可以写相对路径。src = './index2.html'

##### `<a>`

- 可以创建一个到其他网页、文件、同一页面内的位置、电子邮件地址或任何其他URL的超链接。[ 跳转页面（HTTP GET 请求）[ 会把参数放到查询参数中 ] ]

- 属性：

```
1. target = '_blank'：在新窗口打开
   target = '_self'：在自身窗口打开
   target = '_parent'：在父窗口打开
   target = '_top'：在顶层窗口打开

2. download：此属性指示浏览器下载URL而不是导航到URL，因此将提示用户将其保存为本地文件。

(下载文件两种方法:
a. HTTP 响应：`Content-Type:application/octet-stream`，浏览器将以下载的形式接收请求。
b. 如果HTTP 响应：`Content-Type: text/html` 时，可以使用 `dowmload `属性告知浏览器进行下载文件。)

3. href：`qq.com` 不会跳转到 `qq.com` ，因为 `qq.com` 是相对地址，会跳转到 `/qq.com` 路径。`//qq.com` 浏览器默认添加协议，协议为当前文件为什么协议就使用什么协议。
 
(因此要安装`http-server`，用http打开index.html文件：

1.运行`npm i -g http-server`

2. 运行 http-server -c-1 不要缓存)

"" 空，跳转自身，页面刷新，发起请求。

#xxx 锚点（页面内的跳转）。不会发起请求。当锚点为 空 时，会跳转到顶部。
 
 ?name=xxx 查询字符串。发起 GET 请求

javascript:; javascript伪协议（ javascrip: alert(1) ,弹出alert 警告框）。'javascript:;' ==> 点击 a 标签不会做任何事情
```

##### `<form>`

- form 表示了文档中的一个区域，这个区域包含有交互控制元件，用来向web服务器提交信息。[ 跳转页面（HTTP POST 请求 [ 会把参数放到 form data 中 ]） ]

- 属性：

```
action：规定提交表单时，向何处发送表单数据。
method：浏览器使用这种 HTTP 方式来提交 form。值为 POST 或者 GET（不用）
target：和 a 标签相同
```

- form表单必须有提交按钮，下面为提交按钮的形式：
```
 1.<input type= 'submit' value= '提交' >
 2.<button>提交</button>（条件为：form 表单中只有这一个按钮，且没有写 type ，则 button 会升级为 submit ，若有 type= 'button' ，则 button只是一个单纯的按钮，没有提交作用，form 表单没有提交按钮。）
```

##### `<input>`

1. type属性：

type="checkbox" 复选框

`<label><input type="checkbox" name="xxx">xxx</label>`

*一组选项中 input的name值相同才可以实现多选*

type="radio"单选

`<label><input type="radio" name="xxx">xxx</label>`

*一组选项中input的name值相同才可实现单选*

2. 下拉菜单

```
<select name="分组" multiple>
<option value="xxx">1</option>
<option value="xxx" disabled>2</option>
<option value="xxx" selected>3</option>
</select>
```
*上面示例中，multiple的意思为可多选；disabled的意思为不可选；selected的意思为默认选中*

###### `<textarea>`

- 属性：
```
-  name：元素的名称。必须提供，提交表单时 `name` 的值作为参数提交给服务器。
- resiz : none：去掉文本域右下角的默认的灰色斜杠。
- cols：文本域的可是宽度。必须为正数，默认为20 (HTML5)。[ 大概估计，推荐使用 CSS ]
- rows：元素的输入文本的行数（显示的高度）。[ 大概估计，推荐使用 CSS ]
```

##### `<table>`

```
<table border = 1 style= 'border-collapse:collapse'> 
  <colgroup>
    <col width = 100>
    <col width = 100>
    <col width = 100>
    <col width = 100>
  </colgroup>
  <thead>
    <tr>
      <th></th><th>数学</th><th>语文</th><th>英语</th>
    <tr>
  </thead>
  <tbody>
    <tr>
      <th>小王</th><td>90</td><td>88</td><td>95</td>
    </tr>
    <tr>
      <th>小赵</th><td>70</td><td>90</td><td>86</td>
    </tr>
    <tr>
      <th>小李</th><td>99</td><td>76</td><td>80</td>
    </tr>
  </tbody>
  <tfooter>
    <tr>
      <th>总分</th><td>339</td><td>342</td><td>353</td>
    </tr>
    <tr>
      <th>平均分</th><td>84.75</td><td>85.5</td><td>88.25</td>
    </tr>
  </tfooter>
</table>
```
   






