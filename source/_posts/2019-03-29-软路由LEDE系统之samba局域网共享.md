---
title: 软路由LEDE系统之samba局域网共享
copyright: true
date: 2019-03-29 23:15:56
tags:
- 软路由
- LEDE
- samba
categories:
- 实用教程
comments:
password:
---
## 前言 
上周末看油管的时候发现了一款极具性价比的NAS-蜗牛星际。矿渣nas，三月初就开卖了，当时好像200包邮。我入手有点晚所以价格也高一些。290包邮。不过卖家给改好了双千兆网络。虽然是矿渣，但我这台内部没有多少灰尘。只有风扇上有灰。应该没运行多久。到手后由于没4有显示器和电源线。就去楼下电脑维修店买了根电源线，顺便借老板显示器装了系统。
很久之前就想入手软路由了，但是动不动就上千的售价实在是难以接受。看到这个性价比还不错的就入手了。之前用的是k2p。没有usb接口，局域网共享就很难实现，而且就算有U盘，24小时工作也承受不了。现在终于可以好好享受一下samba带来的便携了。后期应该还会安装黑群辉实现更多的功能。
如果你的软路由主板usb借了移动硬盘或者sata口连接了机械硬盘，这一步是不需要做的。
蜗牛星际主板上带了一个16G的固态硬盘。性能极差。和3.0的U盘速度差不多。装lede还勉强可以接受。现在没有硬盘也只能用这个来代替了。
我安装的是[koolshare论坛](http://koolshare.cn/portal.php)的lede系统，酷软中心很多插件，还是挺好用的。
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190329233210.png" width="600px" />
注：本文借鉴了koolshare论坛的两个帖子 这里简单做了一些总结，和一些自己的经验

http://koolshare.cn/thread-154153-1-1.html
http://koolshare.cn/forum.php?mod=viewthread&tid=110543&highlight=samba

## 一、为安装盘剩余的空间创建新分区
如果你的软路由主板usb借了移动硬盘或者sata口连接了机械硬盘，这一步是不需要做的。
### 先运行分区工具
`fdisk /dev/sda`
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190329233753.png" width="600px" />
### 输入p查看当前分区
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190329234053.png" width="600px" />
### 输入n创建新的分区
这里由于我已经创建 就不在截图了 
直接连续三次回车键，会默认将剩余的空间创建为一个新的分区。
### 输入w保存分区
完成后会退出分区工具
### 使用mkfs命令格式化新建的分区
`mkfs.ext4 /dev/sda5`
说明 etx4是文件系统。如果是固态的话建议修改为f2fs。后面的sda5是新建的分区，分区名根据自己的修改即可。
`mkfs.f2fs /dev/sda5` （固态硬盘推荐使用）
### 赋予新添加的分区权限
`chmod -R a+rwx /mnt/sda5`
### 重启，使分区表生效（好像不重启也可以，不过还是建议重启）
## 二、挂载新创建的分区
如果你的软路由主板usb借了移动硬盘或者sata口连接了机械硬盘，这一步也是不需要做的。
这里就很简单了，打开路由器管理界面简单设置即可
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190329235605.png" width="600px" />
选择挂载点，在自定义位置填入`/mnt/sda5` (挂载器要创建这个空文件夹，注意不要输错了)
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330000544.png" width="600px" />
## 三、将新创建的分区添加到samba的共享目录
这里也很简单 按照下图的设置即可
<img src="https://raw.githubusercontent.com/sxz799/blog_tuchuang/master/img/20190330001456.png" width="600px" />
### 给samba用户添加密码
`smbpasswd -a root` （终端输入）
然后输入密码回车
最后重启一下软路由即可（想偷懒就直接重启samba服务即可）
## 总结
其实对于大多用户来说，都会挂载一个硬盘来当做简易的NAS来使用。
核心内容就是下面三步
1.添加samba用户
2.为用户设置密码
3.添加该用户可以访问的目录
这里我偷懒，加上在家里用，root用户就可以。不必要弄那些复杂的内容。
嗯，就这样
2019年03月30日00:28:30