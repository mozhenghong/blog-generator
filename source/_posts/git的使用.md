---
title: git的使用
date: 2018-10-17 08:42:46
tags:
---
  *使用git的前提是已经配置好git和github*

# 只在本地使用

1.创建项目目录`mkdir demo` ，进入项目目录`cd demo`

2.运行`git init`，初始化本地仓库 .git（在demo里创建一个.git目录）

3.在demo目录中添加文件，
  ```
  mkdir css
  touch index.html css/style.css
  ```

  4.运行`git status -sb` ，可以显示当前所有文件的状态，可以看到文件名前面有??

  5.运行`git add .  `可以将变动加到暂存区。 （如果想一个一个文件add 可以运行`git add index.html`）

  6.再次运行`git status -sb`可以看到文件前面的？？变成了A

  7.运行`git commit -m“信息" `，可以将add过的内容正式上传到本地仓库（.git就是本地仓库）。
  
  8.运行`git log`可以查看历史变动。

  9.假如改变了其中的某个文件 就需要再次运行`git add .`和`git commit -m"信息"`。

  # 将本地仓库上传到GitHub

  1.在GitHub上新建一个空仓库，名称与本地目录一致，为demo。（只修改name即可）

  ![](https://upload-images.jianshu.io/upload_images/9617841-c746b266aa0240f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  2.点击**create repository** ，出现以下界面,运行「…or push an existing repository from the command line」下面的代码即可。（ 运行之前一定要点以下SSH，使地址变成git@github.com 开头的格式）

  ![](https://upload-images.jianshu.io/upload_images/9617841-f81f5e4958105146.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  # 直接在 GitHub 创建一个仓库，然后下载到本地

  1.在Github上创建一个仓库（这次不是空仓库了,是自带 README 和 Lisence 的仓库），按照下图填写

  ![](https://upload-images.jianshu.io/upload_images/9617841-75d12846896c9d72.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  2.点击**create repository** ，可以看到仓库自动拥有三个文件[.gitignore](http://gitbook.liuhui998.com/4_1.html)、README.md、LISENCE

  ![](https://upload-images.jianshu.io/upload_images/9617841-1a47890c0afedfde.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  3.点击绿色按钮「clone or download」，可以得到一个弹出层：(要确保弹出层的地址为SSH地址，如果不是，点一下 Use SSH)

  ![](https://upload-images.jianshu.io/upload_images/9617841-b14ec58a6d2cadf9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  4.复制地址，打开终端，找一个安全的目录，运行`git clone 刚才复制的地址`，可以看到该目录下多出demo目录，进入demo目录，运行`ls -la`可以看到仓库中的文件都出现在demo目录中了。

  ## 上传更新

本地文件有变动，按照下列顺序运行代码 即可上传更新。

```
  git add 文件路径
  git commit -m "信息"
  git pull 
  git push
```
 


