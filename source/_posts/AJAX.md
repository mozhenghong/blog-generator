---
title: AJAX
date: 2018-12-17 23:50:10
tags:
---
## 发请求的方式

1. `<form method='GET/POST'>`，但是会刷新页面或者新开页面
2. `<a href=" ">`,可以发送get请求，也会刷新页面或者新开页面
3. `<img src=" ">`,可以发送get请求，但是只能以图片形式展示
4. `<link href=" ">`,可以发送get请求，只能以 CSS、favicon 的形式展示
5. `<script src=" ">`,可以发送get请求，但是只能以脚本形式运行

## AJAX

- async javascript and XML(异步的javascript 和XML)
1. 使用XMLHttpRequest发请求
2. 服务器返回XML格式的字符串
3. js解析XML,并更新局部页面

## JSON

- [官方网址](http://json.org/)
- JSON是一门新语言,与JS类似
- JSON与JS的不同：

    - JSON中没有function、undefined以及symbol，其余的几种数据类型都有
    - JSON的字符串首尾必须是双引号“”
    - JSON的对象没有原型链
    - JSON的对象的书写格式：`{"name":"momo"}`

##　同源策略

- 如果JS不是baidu.com页面中的，就不能向baidu.com发送AJAX请求，<font color = "red">只有协议＋端口＋域名一模一样才允许发送AJAX请求</font>
    - `http://baidu.com`不能向`http://www.baidu.com`发送AJAX请求
    - `http://baidu.com:80`不能向`http://baidu.com:81`发送AJAX请求

## CORS跨域=>突破同源策略

- Cross-Origin Resource Sharing
- CORS可以告诉浏览器，我俩是一家的，别阻止它
- 只要在后端代码中添加`response.setHeader('Access-Control-Allow-Origin','url')`即可,后端代码：
```
   if(path==='/xxx'){
    response.statusCode = 200
    response.setHeader('Content-Type', 'text/json;charset=utf-8')
    response.setHeader('Access-Control-Allow-Origin', 'http://momo.com:8001')
    response.write(`
    {
      "note":{
        "to": "xiaowen",
        "from": "momo",
        "heading": "打招呼",
        "content": "hello"
      }
    }
    `) //write()中写入的是字符串！
    response.end()　//一定要加
```

## 使用原生JS写一个AJAX请求

```
let request = new XMLHttpRequest();
request.open('GET/POST','URL');
request.onreadystatechange = ()=>{
    if(request.readyState===4){
        //说明都响应完了
        if(request.status>=200&&request.status<300){
            //说明请求成功了

            let string = request.responseText
            //把符合JSON语法的字符串
            //转化成JS对应的值
            let object = window.JSON.parse(string)
        }
    }
}
request.send();
```
 