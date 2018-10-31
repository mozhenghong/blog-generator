---
title: CSS-REM
date: 2018-10-31 07:56:46
tags:
---
### 单位

- px ==>像素
- em ==>一个m的宽度，一个汉字的宽度
- rem ==>root em ,根元素（HTML）的font-size
- vh ==>viewport height 视口高度
- vw ==>视口宽度
  
**注意：**

1. 网页默认的font-size为16px；
2. 如果chrome设置了最小字号为12px，就算在css中设置了font-size：6px，也会显示为12px
   
#### rem和em的区别

- rem：HTML的font-size
- em：自己的font-size

### 手机端使用REM

- 所有手机显示的界面都是一样的，只是大小不同，所以把一切单位以宽度为基准就可以完美还原设计。
- 使用js动态调整REM，使1 rem == viewport width；
```
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
 <script>
     var pageWidth = window.innerWidth
     document.write('<style>html{font-size:'+pageWidth+'px;}</style>')
 </script>
```

- rem可以和其它单位一起使用。

## 在 SCSS 里使用 PX2REM

1. 安装node-sass
- npm config set registry https://registry.npm.taobao.org/hanshu
- touch ~/.bashrc
- echo 'export 
SASS_BINARY_SITE="https://npm.taobao.org/mirrors/node-sass"' >> ~/.bashrc
- source ~/.bashrc
- npm i -g node-sass

*如果安装时出现权限方面的错误，则可以运行*<br>
`sudo npm install --unsafe -perm -g node-sass`

2. 使用node-sass将scss转换为css

- mkdir ~/Desktop/scss-demo
- cd ~/Desktop/scss-demo
- mkdir scss css
- touch scss/style.scss
- start scss/style.scss
- node-sass -wr scss -o css
- 编辑 scss 文件就会自动得到 css 文件<br>
在 scss 文件里添加:
```
@function px( $px ){
  @return $px/$designWidth*10 + rem;
}
```
然后在css中将需要写长度的地方引用函数 px（设计稿的宽度）即可。