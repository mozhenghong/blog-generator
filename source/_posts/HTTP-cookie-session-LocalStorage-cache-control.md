---
title: HTTP--cookie+session+LocalStorage+cache-control
date: 2018-12-29 13:15:29
tags:
---
## cookie

- cookie特点：
  1. 服务器通过 Set-Cookie 头给客户端一串字符串
  2. 客户端每次访问相同域名的网页时，必须带上这段字符串
  3. 客户端要在一段时间内保存这个Cookie
  4. Cookie 默认在用户关闭页面后就失效，后台代码可以任意设置 Cookie 的过期时间
  5. 大小大概在 4kb 以内
-  前端设置cookie:
```
let  allCookie = document.cookie //读取cookie
document.cookie = newCookie //设置一个新的cookie
//实例：
document.cookie = "someCookieName=true; expires=Fri, 31 Dec 9999 23:59:59 GMT; path=/";
```
-  后端设置cookie

`response.setHeader('Set-Cookie', 'xxx' ) // xxx 就是一个身份证`

-  用户可以随意篡改cookie!!!

## session

- session特点:
  1. 将 SessionID（随机数）通过 Cookie 发给客户端
  2. 客户端访问服务器时，服务器读取 SessionID
  3. 服务器有一块内存（哈希表）保存了所有 session
  4. 通过 SessionID 我们可以得到对应用户的隐私信息，如 id、email
  5. 这块内存（哈希表）就是服务器上的所有 session
- 后端代码

```
//在内存中开辟一个空间，用来存储 Session
let sessions = {}

//当用户登录成功时,设置一个sessionID，把信息储存到session中。

let sessionId = Math.random() * 1000000
sessions[ sessionId ] = { key: value } 
response.setHeader( 'Set-Cookie', `sessionId = ${ sessionId }` ) 

//当登录过的用户访问首页时，遍历 Cookie，将所有 Cookie 存储到一个 hash（哈希表）中

let mySession = sessions[ hash.sessionId ]
let username
if( mySession ){
    username = mySession.用户信息  // 用户信息表示 sessions 中的{ key: value }
}

```
## LocalStorage

- 特点：
    1. LocalStorage 跟 HTTP 无关
    2. HTTP 不会带上 LocalStorage 的值
    3. 只有相同域名的页面才能互相读取 LocalStorage（没有同源那么严格）
    4. 每个域名 localStorage 最大存储量为 5Mb 左右（每个浏览器不一样）
    5. 常用场景：记录有没有提示过用户（没有用的信息，不能记录密码）
    6. LocalStorage 永久有效，除非用户清理缓存(Ctrl+Shift+Delete)

- API

    - window.localStorage.setItem() ==> 接收一个键名和值作为参数，把键值对添加到存储中，如果键名存在，则更新其对应的值，接收的参数必须是字符串
    - window.localStorage.getItem() ==> 接收一个键名作为参数，返回键名对应的值
    - window.localStorage.removeItem() ==> 接收一个键名作为参数，并把该键名从存储中删除
    - window.localStorage.clear() ==> 清空存储中的所有键名
- 对象的存储
    - 由于window.localStorage.setItem()接收的参数必须是字符串，如果传入对象，浏览器会自动转化成对象`[object,Object]`,所以要使用JSON将对象转化成字符串。
    `localStorage.setItem( 'object', JSON.stringify({ name: 'obj' }))`

##　sessionStorage

- 特点:
    1. LocalStorage 跟 HTTP 无关
    2. HTTP 不会带上 LocalStorage 的值
    3. 只有相同域名的页面才能互相读取 LocalStorage（没有同源那么严格）
    4. 每个域名 localStorage 最大存储量为 5Mb 左右（每个浏览器不一样）
    5. SessionStorage 在用户关闭页面（会话结束）后就失效。

## HTTP缓存
###  cache-control

- Cache-Control 通用消息头被用于在 HTTP 请求和响应中通过指定指令来实现缓存机制。
- ` response.setHeader( 'Cache-Control', 'max-age = 30' ) `<br>
  以上代码的意思是最大缓存时间为30s,用户30s内再次刷新页面（发请求），浏览器不会再发请求，直接拿缓存好的东西，这样下载时间就为０，但是30s后再刷新，就要重新请求。
- 特点：
    1. 让浏览器在一段时间内不访问服务器，不发送请求，直接使用本地硬盘 | 内存作为响应，从而减少请求时间
    2. 首页（入口文件 + HTML）不设置 Cache-Control，因为在缓存的这段时间内，用户不能获取最新网页
    3. 其他文件（css + js）会缓存很久（10年，甚至更久），如要更新，只需要改变入口文件（HTML）的 URL 即可，之后浏览器就会缓存最新版的文件
    4. URL 改变实现方式：+ 查询参数 | + 随机数
   
### Expires

- Expires 头指定了一个日期 | 时间， 在这个日期 | 时间之后，HTTP响应被认为是过时的
-  `response.setHeader( 'Cache-Control', 'sun,04 Feb 2018 14:39:05 GM') `
-  Expires 的问题在于，它的过期时间是本地的时间，如果本地时间错乱，可能导致用户一直不能使用缓存，从而影响用户体验
-  Cache-Control 设置缓存时长，Expires 设置缓存过期时间点。如果两者同时设置，Cache-Control 优先使用

### ETag

#### MD5
- MD5 指摘要算法，它可以把一个文件转化成一个字符串。若文件内容相同，则字符串相同。文件内容差异越小，字符串（算出来的结果）差异越大
- 安装 MD5 `npm install md5`，然后 node.js 使用 MD5
- 后端代码：

```
else if( path === '/js/main.js' ){
    let string = fs.readFileSync( './js/main.js', 'utf-8' )
    let fileMd5 = md5( string )
    response.setHeader( 'ETag', fileMd5 )  // 响应头中有 ETag ==> ETag: md5 值
    // 当设置了 ETag 响应头，下次刷新时，请求中会多一个 If-None-Match 的请求头，值为 ETag 的值（md5 值）
    if( request.header[ 'if-none-match' ] === fileMd5 ){  // 如果请求的版本号（md5 值） === 浏览器的 If-None-Match 的值（md5 值） ==> 相同版本不需要下载
        // 没有响应体
        response.statusCode = 304  
        // 304 Not Modified 表示资源未被修改，因为请求头指定的版本If-Modified-Since或If-None-Match。在这种情况下，由于客户端仍然具有以前下载的副本，因此不需要重新传输资源。
    } else{
        response.statusCode = 200
        // 有响应体
        response.write( string )
    }
    response.end()
}
```
## 区别与联系

### Cookie + Session

- Cookie 指某些服务器在浏览器终端的一些数据（通常经过加密），一般为了辨别用户身份，也可以储存少量信息
- Session 是指服务器通过某种方式确定了用户身份后的会话状态，一般表现为服务器为每个用户单独存储的一部分数据
- Session 是基于 Cookie 实现的，Cookie 是 Session 的基石
- Cookie 存储在浏览器本地，用户可以看到内容。Session 存储在服务器，用户无法查看内容，一般 Session 的内容是进程\线程间共享的
- Cookie 不安全，而 Session 解决了 Cookie 不安全的痛点

### Cookie + Storage

- Cookie 和 Storage 都存储在本地的一个文件中
- 两者都可以做跨页面通信，两者都不能跨域访问
- Cookie 的每次请求相同域名时，都会带上 Cookie 里的所有内容去访问服务器
- Storage 与 HTTP 无关，不会被带给服务器
- Cookie 在做跨页面通信时，由于带上所有内容，导致上传数据 + 请求变慢，Storage 的出现解决了 Cookie 的痛点，只要将一些不敏感信息存储在 Storage 中即可
- JS 调用 Cookie 比较麻烦，一般都用库进行封装。Storage 调用起来比较简单，也可以再次封装达到更好的效果
- Cookie 大小 4K 左右，Storage 大小 5M 左右
- 后台代码可以任意设置 Cookie 的过期时间。Storage 中的 LocalStorage 永久有效，除非用户删除，Storage 中的 SessionStorage 在用户关闭页面（Session 结束）后就失效

### LocalStorage + SessionStorage

- 两者与 HTTP 无关
- 每个域名的 LocalStorage | sessionStorage 有最大存储量，因浏览器而异
- 只有相同域名的页面才能互相读取 LocalStorage。SessionStorage 只在同一浏览器窗口中共享
- LocalStorage 本地存储， SessionStorage 会话存储
- LocalStorage 永久有效，除非用户删除。SessionStorage 在用户关闭页面（Session 结束）后就失效

### Cache-Control + ETag

- 两者都是 HTTP 响应头，都可以实现加快请求 | 响应速度
- Cache-Control 是直接使用本地缓存，不会发送请求
- ETag 发送请求，如果 MD5 值相同，则没有响应体





