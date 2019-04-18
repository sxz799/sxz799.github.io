---
title: LEDE软路由&群辉下Docker神器之百度云下载
copyright: true
date: 2019-03-30 14:15:50
tags:
- Docker
- 下载
- LEDE
categories:
- 教程
comments:
password:
---

# 前言
入手了蜗牛星际，安装了lede以后发现酷软中心的aria2和tr都不能正常工作，可能是版本bug，无意间在论坛发现了利用docker这一神奇运行百度云第三方下载，尝试一番发现确实很好用，记录一下折腾的过程。
原贴：`http://koolshare.cn/thread-154383-1-1.html`
我没有使用原贴中的镜像 而是选择了另一位大神oldiy的镜像，下面是他的DockerHub主页和博客。
`https://hub.docker.com/u/oldiy/`
`https://odcn.top/`

# LEDE软路由下使用
## 第一步 LEDE酷软中心安装Docker插件
这里不多解释，直接安装即可
## 第二步 配置Docker插件
按照下图的设置即可
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330142552.png" width="600px" />
## 第三步 下载相关镜像
在注册表页搜索相关镜像即可，如下图为百度云下载
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330143001.png" width="600px" />
## 第四步 创建容器
在镜像页选择已经下载的镜像创建即可。
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330143146.png" width="600px" />
在这里对容器进行相关配置，注意端口，和容器中给定的相同最好
下面这一张图就能看明白端口和目录的设置了
简单来说就是端口号正确且不与lede其他程序冲突就可以进入后台
地址正确才能保证文件下载到你指定的位置
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330151403.png" width="600px" />
然后点击创建即可
## 进入Web页面查看安装情况
启动成功后就可以通过下面的链接进入web页面了
http://你的路由器ip:5299   //这里的5299就是配置容器时的端口，尽量和dockerhub的相同。如果不同应该是进不去相关页面的
使用自己的百度账号登录即可，然后点击右上角的设置
注意这里的目录，不要修改使用默认即可
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330144619.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330144816.png" width="600px" />

# 群辉下使用 （更新内容）
## 第一步 群辉套件中心安装Docker插件
不多解释
## 第二步 下载镜像
在注册表搜索`baidu`下载下图中的镜像
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/1111111.png" width="600px" />
## 第三步 配置镜像
按照下图配置即可，配置完成后会自动启动容器
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/222222.png" width="600px" />
配置下载路径
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/333333.png" width="600px" />
配置端口
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/444444.png" width="600px" />
## 第四步 打开Web管理页面
浏览器输入 `<你的IP>:5299` 进入web页面

## 解决百度云限速
web的设置页面修改appid为265486  
默认工作目录修改为`/apps/baidu_shurufa ` 
百度输入法不限速，所以修改为输入法的id 而默认工作目录就是登陆页面后所展现的目录
把要下载的文件移动到/apps/baidu_shurufa 下载即可
需要操作其他文件的时换回 266719 即可


结束
2019年03月30日15:02:07
更新
2019年04月18日23:24:00