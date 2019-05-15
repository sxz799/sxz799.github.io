---
title: Docker神器之迅雷远程下载(群辉 & Linux)
copyright: true
date: 2019-04-15 22:22:31
tags:
- 迅雷
- Docker
- 经验
categories:
- 教程
comments:
password:
---

镜像作者Docker[链接](https://registry.hub.docker.com/u/yinheli/docker-thunder-xware/)

# 群辉下安装和使用
## 一、Docker下载迅雷远程镜像
注册表搜索 thunder-xware 并下载箭头指向的镜像:yinheli/docker-thunder-xware
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190425-2016142x.png" width="600px" />
## 二、安装镜像
1. 勾选使用高权限执行容器
2. 点击高级设置
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190415-222913%402x-min.png" width="600px" />
3. 在卷属性卡中点击添加文件，并选择你期望远程迅雷的下载位置（自定义）
4. 装载路径为 /TDDOWNLOAD （不可更改！！！）
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190415-223001%402x-min.png" width="600px" />
5. 网络选择左下角的与Docker Host使用相同的网络
6. 点击应用创建容器
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190415-223020%402x-min.png" width="600px" />
7. 点开Docker页面左侧的容器选项卡，点击刚创建的容器，然后点击左上角的详情
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190415-223057%402x-min.png" width="600px" />
8. 在弹出的页面中选择日志选项卡，找到最下面的`THE ACTIVE CODE IS: aabbcc` ,记录后面的代码
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ20190415-223150%402x-min.png" width="600px" />
9. 点击这个[链接](http://yuancheng.xunlei.com) http://yuancheng.xunlei.com 登陆迅雷后输入刚才得到的代码即可。

# Linux系统下安装和使用
## 一、安装Docker下载迅雷远程镜像
关于Docker的安装不在多说，请自行搜索安装教程
在终端中输入`docker pull yinheli/docker-thunder-xware:latest` 下载镜像
## 二、安装镜像
mkdir data  创建一个文件夹用于存放迅雷下载的资源
```
docker run -d --privileged=true \
        --name=xware \
        --net=host \
        -v <自己选择要存放的位置>:/app/TDDOWNLOAD \
        yinheli/docker-thunder-xware
```
注意这里命令中的data就是上面创建的文件夹，如果不同名记得修改命令中的地址
`docker ps`   //查看当前运行的容器
`docker logs xware`  //查看迅雷远程的日志
在日志的后几行会看到`THE ACTIVE CODE IS: aabbcc`这样一行代码，记录后面的代码。也就是设备CODE
点击这个链接http://yuancheng.xunlei.com 登陆迅雷后输入刚才得到的代码即可。




