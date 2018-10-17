---
title: HTTP入门
date: 2018-10-17 12:17:20
tags:
---
# 请求与响应

- 浏览器负责发起请求
- 服务器在 80 端口接收请求
- 服务器负责返回内容（响应）
- 浏览器负责下载响应内容
*HTTP 的作用就是指导浏览器和服务器如何进行沟通*

## 请求

1. 运行`curl -s -v -H "momo: xxx" -- "https://www.baidu.com"`得到：

![](https://upload-images.jianshu.io/upload_images/9617841-83490cf11a0bd2ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

请求的内容为：

![](https://upload-images.jianshu.io/upload_images/9617841-db595e7112c6ac85.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 运行`curl -X POST -s -v -H "momo: xxx" -- "https://www.baidu.com"`

请求的内容为：

！![](https://upload-images.jianshu.io/upload_images/9617841-da2f6eac6b73f53d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. 运行`curl -X POST -d "1234567890" -s -v -H "momo: xxx" -- "https://www.baidu.com"`

请求的内容为：
![](https://upload-images.jianshu.io/upload_images/9617841-9a294a72b2840eca.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 所以请求的格式为：
- 1 动词 路径 协议/版本
- 2 Key1: value1
- 2 Key2: value2
- 2 Key3: value3
- 2 Content-Type: application/x-www-form-urlencoded
- 2 Host: www.baidu.com
- 2 User-Agent: curl/7.54.0
- 3 
- 4 要上传的数据

*请求最多包含四部分，最少包含三部分。（也就是说第四部分可以为空）；第三部分永远都是一个回车（\n）；动词有 GET POST PUT PATCH DELETE 等； 路径包括「查询参数」，但不包括「锚点」，如果你没有写路径，那么路径默认为 /
第 2 部分中的 Content-Type 标注了第 4 部分的格式*

## 响应

上面个三个请求得到的响应分别为：

1. ![](https://upload-images.jianshu.io/upload_images/9617841-ec0aeb00d4189ebf.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. ![](https://upload-images.jianshu.io/upload_images/9617841-12141ea44074104d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

3. ![](https://upload-images.jianshu.io/upload_images/9617841-e05da003bfc86952.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

4. 响应的格式为：

- 1 协议/版本号 状态码 状态解释
- 2 Key1: value1
- 2 Key2: value2
- 2 Content-Length: 17931
- 2 Content-Type: text/html
- 3
- 4 要下载的内容（内容特别长）

状态码要记住：[状态码](https://zh.wikipedia.org/wiki/HTTP%E7%8A%B6%E6%80%81%E7%A0%81)

*第 2 部分中的 Content-Type 标注了第 4 部分的格式;第 2 部分中的 Content-Type 遵循 MIME 规范*

## 用 Chrome 查看请求与响应

1. 打开浏览器，右键，检查，打开 Network
2. 输入网址
3. 选中第一个响应
4. 查看 request Headers，点击「view source」，可以看到请求的前三部分了，如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到
5. 查看 Response Headers，点击「view source」，你会看到响应的前两部分，查看 Response 或者 Preview，你会看到响应的第 4 部分
