---
title: VMware虚拟机体验koolshare论坛LEDE固件
copyright: true
date: 2019-03-17 21:38:09
tags:
- 虚拟机
- 路由器
- LEDE
categories:
- 教程
comments:
password:
---

​        博主自用的是路由器是斐讯K2P A2版，性能足够满足大多数家庭的需要了，但还是听说koolshare论坛的lede固件功能丰富，是软路由很常用的固件。只是现在用不到，也没有条件使用（毕竟价格接近4位数）。但看论坛截图里丰富的功能有些手痒，就打算在虚拟机里装上过过瘾。

## 一、固件下载
链接：http://firmware.koolshare.cn/LEDE_X64_fw867/
​链接是x64设备用的固件，有img格式和vmdk虚拟机专用的格式，这里选择虚拟机专用格式下载。

<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211318.png" width="800px" />

## 二、安装LEDE
和安装其他虚拟机没有什么区别，有几处需要注意的地方我已经在图中标记出来了。
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211410.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211447.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211507.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211520.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211543.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211600.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317211639.png" width="600px" />
安装到这里就差不多了。主要区别就是选择稍后安装操作系统，然后磁盘选择第一步中下载的文件和添加了一张网卡而已。
安装后不要启动！
安装后不要启动！
安装后不要启动！
## 三、虚拟机网卡配置
和上一篇文章类似，设置VMware虚拟网卡。这里设置桥接网卡为计算机的网卡。nat地址和上一篇文章一样。
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317212324.png" width="600px" />
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317212400.png" width="600px" />
然后设置lede系统的网卡
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317212958.png" width="600px" />
配置好以后启动虚拟机。启动完毕后鼠标点击虚拟机内部
然后输入 
`vi /etc/config/network`
修改lan口的地址
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/QQ%E6%88%AA%E5%9B%BE20190317212511.png" width="600px" />
然后取消勾选本地连接中的ipv4和ipv6协议。  重点！重点！重点！重点！
## 四、配置VMware Network Adapter VMnet8 
和上篇文章不同的是，这里我们的目的是通过虚拟机路由器系统进行上网，所以要配置上网关
如下图
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190320192006.png" width="600px" />

教程结束！
//2019年03月20日19:26:46 更新

转载注明出处 谢谢



