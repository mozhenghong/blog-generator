---
title: JSONP
date: 2018-12-17 23:52:40
tags:
---
## 局部刷新

1. 用`<img>`来造get请求

```
button.addEventListener('click', (e)=>{
    let image = document.createElement('img')
    image.src = '/pay'
    image.onload = function(){ // 状态码是 200~299 则表示成功
        alert('成功')
    }
    image.onerror = function(){ // 状态码大于等于 400 则表示失败
        alert('失败')
    }
})
```
2. 用`<script>`来造get请求

```
button.addEventListener('click', (e)=>{
    let script = document.createElement('script')
    script.src = '/pay'
    document.body.appendChild(script)//必须加到html中才可以！！！
    script.onload = function(e){ // 状态码是 200~299 则表示成功
        e.currentTarget.remove()
    }
    script.onerror = function(e){ // 状态码大于等于 400 则表示失败
        e.currentTarget.remove()
    }
})
```

## JSONP

- JSONP就是动态创建`<script>`标签，’src‘指向get请求的’url‘，同时传入一个callback查询参数，然后可以处理获取到的数据。

- 请求方：momo.com的前端程序员（浏览器）
- 响应方：wenwen.com的后端程序员（服务器）
1. 请求方创建 script，src 指向响应方，同时传一个查询参数 ?callbackName=yyy
2. 响应方根据查询参数callbackName，构造形如
    -  yyy.call(undefined, '你要的数据')
    -  yyy('你要的数据')<br>
这样的响应
3. 浏览器接收到响应，就会执行 yyy.call(undefined, '你要的数据')
4. 那么请求方就知道了他要的数据

- 用JSONP做请求
```
button.addEventListener('click', (e)=>{
    let script = document.createElement('script')
    let functionName = 'momo'+ parseInt(Math.random()*10000000 ,10)
    window[functionName] = function(){  // 每次请求之前搞出一个随机的函数
        amount.innerText = amount.innerText - 0 - 1
    }
    script.src = '/pay?callback=' + functionName
    document.body.appendChild(script)
    script.onload = function(e){ // 状态码是 200~299 则表示成功
        e.currentTarget.remove()
        delete window[functionName] // 请求完了就干掉这个随机函数
    }
    script.onerror = function(e){ // 状态码大于等于 400 则表示失败
        e.currentTarget.remove()
        delete window[functionName] // 请求完了就干掉这个随机函数
    }
})
```
后端代码：
```
if (path === '/pay'){
    let amount = fs.readFileSync('./db', 'utf8')
    amount -= 1
    fs.writeFileSync('./db', amount)
    let callbackName = query.callback
    response.setHeader('Content-Type', 'application/javascript')
    response.write(`
        ${callbackName}.call(undefined, 'success')
    `)
    response.end()
}
```

- jQuery中的JSONP
```
  $.ajax({
    url: "http://wenwen.com:8002/pay",//响应方
    dataType: "jsonp",
    success: function( response ) {
        if(response === 'success'){
        amount.innerText = amount.innerText - 1
        }
 }
 })
```

### JSONP为什么不支持POST请求

- JSONP是通过动态创建`<script>`标签实现的，<br>动态创建的`<script>`只能发get请求，不能发post请求