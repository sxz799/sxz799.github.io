---
title: Hexo博客之Valine评论系统及邮件通知插件
copyright: true
date: 2020-02-22 16:18:12
tags:
categories:
comments:
password:
---
在之前的文章中曾经提到过Valine的评论系统，今天来系统的介绍一下使用方法和添加邮件提醒功能。
首先要感谢[Valine](https://valine.js.org/) 开发好用的项目和DesertsP开发的[Valine-Admin](https://github.com/DesertsP/Valine-Admin.git)插件。
## 启用Valine评论系统
1.注册[LeanCloud](https://www.leancloud.cn/)
2.进入控制台创建应用
![](https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/old/2020022220200222164722.png)
3.点击应用-设置-安全中心-Web安全域名，填入你的域名
![](https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/old/2020022220200222164900.png)
4.点击应用-设置-应用Keys找到AppID、AppKey
![](https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/old/2020022220200222165006.png)
5.找到hexo目录内主题文件夹（每个人都不同，我的是next）的_config.yml文件找到Valine，大概在633行附近，修改对应值
![](https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/old/2020022220200222165320.png)
6.hexo三连就可以在文章页面看到评论系统了。
## 启用启用Valine评论系统
原作者的教程很详细了，这里就不简单搬运了，记录一下我遇到的一下小问题吧。
[这是链接](https://github.com/DesertsP/Valine-Admin.git)
1.提前弄明白邮箱的STMP
2.设置好变量后部署，修改变量后要重启实例才可以