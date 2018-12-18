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
 
## AJAX的所有功能

- 客户端的JS发送请求（浏览器上的）
- 服务端的JS发送响应（Ｎode.js上的）
- JS 可以设置任意请求 header :
    - 第一部分 request.open('get', '/xxx')
    - 第二部分 request.setRequestHeader('content-type','x-www-form-urlencoded')
    - 第四部分 request.send('a=1&b=2')
- JS 可以获取任意响应 header :
    - 第一部分 request.status //200<br> request.statusText//ok
    - 第二部分 request.getResponseHeader('content-type') / request.getAllResponseHeaders()
    - 第四部分 request.responseText

## 自己实现AJAX

```
window.jQuery.ajax=function({url,method,body,headers}){
    //成功就调用 resolve，失败就调用 reject
    return new Promise(function(resolve,reject){
        let request = new XMLHttpRequest()
        request.open('method','url')//配置request
        for(key in headers){
            let value = headers[key]
            request.setRequestHeader(key,value)
        }
        request.onreadystatechange = ()=>{
            if(request.readyState===4){
                if(request.status>=200&&request.status<300){
                    resolve.call(undefined,request.responseText)
                }else if(request.status>=400){
                    reject.call(undefined,request)
                }
            }
        }
        request.send(body)

    })
}

//使用AJAX
button.addEventListener('click',(e)=>{
    let promise = window.jQuery.ajax({
        url:'/xxx',
        method: 'get',
        headers:{
            'content-type':'application/x-www-form-urlencoded',
            'age': '18'
        }
    })
    promise.then(
        (text)=>{console.log(text)},
        (request)=>{console.log(request)}
    )
})

//=>链式操作
window.jQuery.ajax().then(success, fail).then(success, fail)
```
