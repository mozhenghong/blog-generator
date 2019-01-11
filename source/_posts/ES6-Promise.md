---
title: ES6-Promise
date: 2019-01-11 15:24:02
tags:
---
## 回调

- `function(callback){callback()}`
- 把一个函数Ａ传给另一个函数Ｂ调用，那么Ａ就是回调函数。

- 回调地狱：回调套回调，套很多层。promise可以解决回调地狱。 

## Promise

- Promise 对象用于表示一个异步操作的最终状态（完成或失败），以及其返回的值。
  
- 语法：成功调用resolve(),失败调用reject()

```
function x(){
    return new Promise(function(resolve,reject){
        resolve('momo')
    })
}

//调用
x().then().then()
```
