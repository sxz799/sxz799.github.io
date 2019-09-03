---
title: CentOS更换国内yum源
copyright: true
date: 2019-08-28 12:49:45
tags:
- 防痴呆
categories:
- Linux
comments:
password:
---

每次都去百度地址太费劲了，所以整理一下地址
## 更换方法
1.备份默认yum源
```
cd /etc/yum.repos.d
mv CentOS-Base.repo CentOS-Base.repo.bak
```
2.下载更换国内yum源
阿里
```
wget http://mirrors.aliyun.com/repo/Centos-7.repo
mv Centos-7.repo CentOS-Base.repo
```
网易
```
wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
mv CentOS7-Base-163.repo CentOS-Base.repo
```
3.清理缓存
```
yum clean all
```
4.重建缓存
```
yum makecache
```

