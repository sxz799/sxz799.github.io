---
title: Centos配置本地yum源
copyright: true
date: 2019-06-19 00:35:12
tags:
- Linux
categories:
- 实用教程
comments:
password:
---

一、挂载镜像文件
```
mkdir /mnt/cdrom
mount /dev/cdrom /mnt/cdrom
```
二、修改yum源配置文件
```
cd /etc/yum.repo.d
rm -rf *.repo
vi /etc/yum.repo.d/Localyum.repo
```
内容为：
```
[localyum]
name=localyum
baseurl=file:///mnt/cdrom
gpgcheck=0
enabled=1
```
三、清空并重建缓存
```
yum clean all
yum makecache
```