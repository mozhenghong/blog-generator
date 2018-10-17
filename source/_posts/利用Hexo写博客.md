---
title: 利用Hexo写博客
date: 2018-10-17 10:10:36
tags:
---
# 安装Hexo,写第一篇博客

1.在 GitHub 上新建一个空仓库，仓库名称是「你的Github用户名.github.io」

2.进入安全目录(例如cd ~/Desktop)，运行`npm install -g hexo-cli`，安装 Hexo

3.运行`hexo init myBlog`然后打开 `cd myBlog`

4.运行`npm i`

5.运行`hexo new 开博大吉`，会看到一个 .md 文件的路径

![](https://upload-images.jianshu.io/upload_images/9617841-9e8acbaed530e51b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

6.运行`xdg-open xxxxxxxxxxxxxxxxxxx.md`（我的是Linux系统，所以用xdg-open打开文件，window系统可用start打开，但是必须将路径中的\改为/。当然用vi打开更方便一点），可以编辑文件（当然也可以直接在VSCode中打开文件夹进行编辑）

7.`xdg-open _config.yml`，编辑网站配置

- 把第 6 行的 title 改成你想要的名字
- 把第 9 行的 author 改成你的大名
- 把最后一行的 type 改成 type: git
- 在最后一行后面新增一行，左边与 type 平齐，加上一行 repo: 仓库地址 （请将仓库地址改为「你的用户名.github.io」对应的仓库地址，仓库地址以 git@github.com: 开头）

8.`npm install hexo-deployer-git --save`，安装 git 部署插件

9.运行`hexo deploy`

10.进入「你的用户名.github.io」对应的仓库，打开 GitHub Pages 功能（点击 Settings，往下滚动页面，选中 master branch 然后点击 Save，右上角出现一个链接，就是预览链接），你应该会看到一个预览链接。用浏览器访问「预览链接/index.html」就应该看到了你的博客！（GitHub Pages 存在延迟，如果没看到，过三分钟再刷新看看）

# 第二篇博客

1.运行`hexo new 博客名`

2.复制显示的路径，使用 `xdg-open 路径` 来编辑它

3.运行`hexo generate`

4.运行`hexo deploy` 然后就可以看新写的博客了

# 上传源代码

*「Github用户名.github.io」上保存的只是你的博客，并没有保存生成博客的程序代码，你需要再创建一个名为 blog-generator 的空仓库，用来保存 myBlog 里面的生成博客的程序代码。*

1.在Github上创建一个空仓库

![](https://upload-images.jianshu.io/upload_images/9617841-128165ddd560273a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.在终端中执行 *…or create a new repository on the command line*下的命令.这样一来，你的博客发布在了「Github用户名.github.io」而你的生成博客的程序代码发布在了「blog-generator」。

3.每次运行完 hexo deploy 之后，要再运行一下add/commit/pull/push 将将程序代码推到Github上。

# 更换主题

1.进入[](https://github.com/hexojs/hexo/wiki/Themes)，找一个主题，进入主题的 GitHub 首页，点击**clone or download**，复制主题地址。

![](https://upload-images.jianshu.io/upload_images/9617841-64daf5a55aece471.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2.终端中运行`cd themes`

3.`git clone 主题地址`

4.`cd ..`

5.将 _config.yml 的第 75 行改为 *theme: hexo-theme-next*

6.`hexo generate`

7.`hexo deploy`，这样你博客主题地址就会更改。

# markdown使用指南

### 标题

在标题前面添加#可以设置标题，几级标题就在前面加几个#，一共可以写到六级标题。（#与标题之间有一个空格）

### 列表

无序列表在文字前面加-即可，有序列表在文字前面加1.即可（-和1.与文字中间有一个空格）

### 插入链接

使用 [显示文本]（链接地址）可插入链接

### 插入图片

使用 ! [] (图片链接)可以插入图片

### 引用
 
 在引用的文字前面加> 即可

### 粗体和斜体

在文字前后各加两个*可以使文字变为粗体。
在文字前后各加一个星号可以使文字变成斜体。

### 代码引用

单行代码引用，只需要在代码前后各加一个 ` 即可。
多行代码引用，只需要在代码前后各加三个 ``` 即可。
