---
title: 使用Github搭建hexo静态博客总结
copyright: true
date: 2019-03-20 23:57:50
tags:
- 总结
- 经验
- 博客
- hexo
- git
categories:
- 总结
comments:
password:
---

第一次搭建博客大约是在18年6月份。当时是在腾讯云vps上安装宝塔，然后宝塔内部一键安装WordPress博客。在18年12月份发现Github+hexo这一神奇组合，果断尝试。然后又经历了期末考试和过年，博客也算是搁置了一段时间。前几天才重新捡起，然后又系统的自学了一下Git。所以打算写这个博客简单记录一下最基础的内容，可能有些小白看不懂，后期可能会慢慢完善的。

## 一、什么是Git、Github、Hexo？

首先要知道这是完全不同的三个东西，但三者结合起来就会发生奇妙的反应。

### 什么是Git？

Git是一个的分布式版本控制系统。

### 什么是Github？

Github是一个提供免费服务的代码托管网站。

### 什么是Hexo？

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](http://daringfireball.net/projects/markdown/(或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。(摘抄自hexo官网)

如果对github和git的关系感兴趣，可以去这个网站简单了解一下

https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137402760310626208b4f695940a49e5348b689d095fc000

## 二、安装Git、Node.js和hexo

在以下网址下载软件
Git官网下载地址 https://www.git-scm.com/download/
node.js官网下载地址 https://nodejs.org/en/ （建议下载LTS版本）
这两款软件选好安装目录使用默认设置即可

### hexo安装
安装好git和node.js后新建一个你要放置博客的文件夹，然后鼠标右键点击 Git bash here，在弹出的窗口输入
`npm install -g hexo-cli		 //实际上在任意文件夹下都可以 ，hexo安装的目录由node.js的配置决定 `

## 三、Hexo博客相关内容

### 初始化hexo博客

在博客目录鼠标右键点击 Git bash here 在弹出的窗口依次输入
`hexo init //初始化博客 `
`npm install //安装hexo需要的依赖包 	`
`npm  install hexo-deployer-git  --save    // 安装部署到github所需要的依赖包`
这时就可以写博客了（建议先了解一下md语法然后下载一个md编辑器进行创作）
```	
hexo n 博客文章名			//在source/_post目录生成对应md文件
hexo g 					//hexo转化为静态网页
hexo s 					//本地服务器，可以实时预览博客
```
建议先了解一下md语法然后下载一个md编辑器进行创作
完成这一步 在浏览器打开下面的链接

` http://localhost:4000/ `

就可以看见系统默认的一篇博客了和你写的博客了

到这里博客就大致成型了
但是服务搭建在本地是没有什么意义的，我们需要发布到互联网。可以选择购买服务器，自行搭建git服务，也可以用github免费的代码托管服务

### 注册github并新建博客仓库
github官网 https://github.com/
自行注册
然后新建一个名为 xxx.github.io 的仓库 //xxx为你的github用户名，这里不能错！！！不能自定义，必须要和github用户名相同

<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190324-140631%402x.png" width="600px" />

### 生成ssh密钥并将公钥添加到github

在命令提示符输入

`ssh-keygen -t rsa -C "注册github时的email"`
打开用户目录下隐藏的.ssh文件夹，打开id_rsa.pub文件，复制全部内容，粘贴到github的ssh处

<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190324-140304%402x.png" width="600px" />

<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190324140332.png" width="600px" />

### 修改博客配置文件

配置博客目录下的_config.yml配置文件

<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190324140126.png" width="600px" />

这时就可以通过下面的命令将博客同步到github的仓库中

`hexo d` //发布博客

接下来就可以在链接到互联网的设备中输入下面链接访问你的博客了

http://xxxxx.github.io   //xxxxx为你的用户名

## 四、添加DNS个性化域名并使用cdn加速

### 注册一个域名

这一步不详细介绍了，域名自己选购

### 添加域名解析
域名解析的记录类型为CNAME 记录值为xxxxx.github.io   //xxxxx为你的用户名

在博客目录的source文件夹添加一个CNAME文件 没有.txt或者其他

文件内容为**个人域名**(注意：没有http://和www)

然后一系列的命令同步到github远程仓库

```
hexo clean
hexo g
hexo d
```
等域名解析更新后就可以通过域名访问博客了

## 新电脑上继续写博客

现在新电脑上安装Git 、 node.js 、 Hexo
`git clone -b 分支名 git@github.com:xxxx/xxxx.github.io.git  //克隆远程代码到本地`
`npm install hexo --save`   //安装hexo
`npm install` 				//安装hexo需要的依赖包
`npm  install hexo-deployer-git  --save`  // 安装部署到github所需要的依赖包

然后就是正常些博客的步骤了



关于博客的个性化可以看我的另一篇文章[这是链接](https://sxz799.ml/2019/04/13/Hexo%E5%8D%9A%E5%AE%A2%E4%B8%AA%E6%80%A7%E5%8C%96%E5%AE%9A%E5%88%B6/)

转载注明出处 谢谢