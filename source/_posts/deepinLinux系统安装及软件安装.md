---
title: deepinLinux系统安装及软件安装
date: 2018-10-15 11:13:20
tags:
---
# deepin Linux系统安装

我选择的为U盘安装

![](https://upload-images.jianshu.io/upload_images/9617841-ff1eb5a1e5e963fb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

从[官方网站](https://www.deepin.org/) 下载Linux镜像文件，解压到当前文件夹，可以看到深度启动盘制作工具，图标如下：

![](https://upload-images.jianshu.io/upload_images/9617841-35aa7d818d6c2dcb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

打开深度启动盘制作工具，插入你的U盘，勾选格式化硬盘，等待写入完成。

![](https://upload-images.jianshu.io/upload_images/9617841-31ee52ebddb9a960.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

启动盘制作完成后，在U盘插入的情况下，关机重启电脑，以下是一些电脑的U盘装系统启动热键，在开机时按相应的按键。

![](https://upload-images.jianshu.io/upload_images/9617841-716d48f92ddf997f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

进入安装界面,选择需要安装的语言:

![](https://upload-images.jianshu.io/upload_images/9617841-4cc5fd75d961a6ff.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

进入账户界面，输入用户名和密码:

![](https://upload-images.jianshu.io/upload_images/9617841-81afd78441b14b9a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

选择安装位置 :

![](https://upload-images.jianshu.io/upload_images/9617841-e2f2c816135ca691.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

点击安装，安装完成后，拔掉U盘，重启计算机即可而。

# 软件安装

## 命令行安装 atool 压缩软件

**搜索软件**
`apt-cache search atool`
**安装软件**
`sudo apt-get install atool`

  *安装软件是需要超级权限的，在命令前面加上 sudo ，回车后需要输入你的密码。第一次使用 linux 的朋友需要注意，这里，输入密码是看不见的（连星号都不会有），盲输入。*

## 安装nodejs

在终端中输入以下命令，便可安装node：
`sudo apt-get install -y nodejs`

此时运行 node 是没有作用的，必须要输入 nodejs 才能进入 node 环境，此时你可以更改映射。
终端中输入：`cd ~`
          `ls -a`
可以看到 .bash_profile 文件，如下图所示：

![](https://upload-images.jianshu.io/upload_images/9617841-9a7bccca60717900.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

编辑 .bash_profile 文件（可以用 vi 编辑，命令` vi .bash_profile`）
然后输入： `alias node="nodejs"`
如果发现不能输入，可以按ESC,然后按I键，便能插入了。
然后狂按 Esc ，输入:wq 保存退出。

输入以下命令使刚刚的命令生效，然后便可以输入 node 进入环境了。
` ~/.bash_profile`

然后安装npm包管理器，在终端中输入：
`sudo apt-get install -y npm`

最后，输入`node -v` 和 `npm -v` ，可以查看node和npm版本


## VSCode的安装与配置

从[官放网站](https://code.visualstudio.com/)下载安装包。

**安装插件**

按 Ctrl + Shift + X 打开扩展面板，然后在商店中搜索以下常用插件，点击第一个结果的「安装」按钮，安装完成后，点击重载以启用

```
Auto close Tag  // 自动闭合标签
Auto Rename Tag  // 自动更改标签
Beautify css/sass/scss 
Bracket Pair Colorizer  // 括号不同颜色
Color Highlight  // 颜色显示
Guides  // 缩进
HTML CSS Support
JavaScript（ES6） code snippets
markdownlint
open in browser
Path Intellisense
seti-icons
TODO Highlight
Vetur
```
## 配置GitHub

进入[](https://github.com/settings/keys)

点击 New SSH key，我们需要输入 Title 和 Key，Title自己输入即可，要得到key，需要点击*generating SSH keys* ,进入**Connecting to GitHub with SSH**页面，然后下滑，点击*Generating a new SSH key and adding it to the ssh-agent*

![](https://upload-images.jianshu.io/upload_images/14473072-761b9b402eb05656.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

进入到以下页面：

![](https://upload-images.jianshu.io/upload_images/14473072-2f22648fb49b67c1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在终端中输入给出的命令，把邮箱改为自己的邮箱，按三次回车，出现以下页面

![](https://upload-images.jianshu.io/upload_images/14473072-70e76d4179ed9143.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

然后运行`cat ~/.ssh/id_rsa.pub` ，得到一串东西，完整的复制这串东西，在key中粘贴这串东西。

点击 Add SSH key

回到终端，运行 `ssh -T git@github.com`  ，输入yes，回车。如果你看到 *Permission denied (publickey)*. 就说明你失败了，就要从头开始；如果你看到*Hi FrankFang! You've successfully authenticated, but GitHub does not provide shell access.*就说明你成功了！


## git的配置

首先，打开终端，在命令行中输入以下命令：

```
git config --global user.name 你的英文名字
git config --global user.email 你的常用邮箱
git config --global push.default simple
git config --global core.quotepath false
git config --global core.editor "vim"
```







