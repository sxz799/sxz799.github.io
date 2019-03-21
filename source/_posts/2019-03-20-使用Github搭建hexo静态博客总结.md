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
- 教程
comments:
password:
---

第一次搭建博客大约是在18年6月份。当时是在腾讯云vps上安装宝塔，然后宝塔内部一键安装WordPress博客。在18年12月份发现Github+hexo这一神奇组合，果断尝试。然后又经历了期末和过年，博客也算是搁置了一段时间。前几天才重新捡起，然后又系统的学习了一下Git。所以打算写这个博客简单记录一下最基础的内容。

## 一、什么是Git、Github、Hexo？

首先要知道这是完全不同的三个东西，但三者结合起来就会发生奇妙的反应。

### 什么是Git？

Git是一个的分布式版本控制系统。

###什么是Github？

Github是一个提供免费服务的代码托管网站。

###什么是Hexo？

Hexo 是一个快速、简洁且高效的博客框架。Hexo 使用 [Markdown](http://daringfireball.net/projects/markdown/)（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。(摘抄自hexo官网)

如果对github和git的关系感兴趣，可以去这个网站简单了解一下

1.https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137402760310626208b4f695940a49e5348b689d095fc000



## 二、安装Git、Node.js和hexo
	### Git官网下载地址 https://www.git-scm.com/download/
	### node.js官网下载地址 https://nodejs.org/en/ （建议下载LTS版本）
	### hexo安装
	安装好git和node.js后新建一个你要放置博客的文件夹，然后鼠标右键点击 Git bash here，在弹出的窗口输入
		npm install -g hexo-cli //实际上在任意文件夹下都可以 ，hexo安装的目录由node.js的配置决定
## 三、Hexo博客相关内容
		### 安装hexo
		在博客目录鼠标右键点击 Git bash here 在弹出的窗口输入
		hexo init //初始化博客
		npm install //安装hexo需要的依赖包
		这时就可以写博客了
		hexo new 博客文章名
		hexo g
		hexo s //本地服务器，可以实时预览博客
		完成这一步 在浏览器输入
		localhost:4000
		就可以看见博客了 //ctrl+c 可以关闭服务
		hexo d //同步博客到github远程仓库，这里不需要输入，因为还没有部署git
		服务搭建在本地是没有什么意义的，我们需要发布到互联网。可以选择购买服务器，自行搭建git服务器，也可以用github免费的代码托管服务
		### 注册github并新建博客仓库
		github官网 https://github.com/
		自行注册
		然后新建一个名为 xxx.github.io 的仓库 //xxx为你的github用户名，这里不能错！！！不能自定义。
## 四、Git相关内容



