---
title: 修改transmission配置，实现远程访问transmission
copyright: true
date: 2019-09-03 16:50:52
tags:
- transmission
- 远程
- 防痴呆
categories:
- 实用教程
comments:
password:
---

# 前言
如果没有修改下面设置也是能打开transmission的web界面，但是你会发现一片空白，提示正在连接服务器。
transmission实现远程访问要开启rpc-authentication-required
# 设置方法
找到transmission安装目录内的settings.json文件
使用notepad++或者sublime等文本编辑软件打开
修改以下地方：（大约在第43行开始）
1.将rpc-authentication-required和rpc-enabled修改为true，启用认证功能
2.rpc-username后设置为你的登录用户名
3.rpc-password后设置为你的密码
4.其他的就按下面的配置修改即可
```
    "rpc-authentication-required": true,
    "rpc-bind-address": "0.0.0.0",
    "rpc-enabled": true,
    "rpc-host-whitelist": "",
    "rpc-host-whitelist-enabled": true,
    "rpc-password": "123456",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "admin",
    "rpc-whitelist": "",
    "rpc-whitelist-enabled": false,
```
这个配置的用户名为admin 密码为123456
注：密码修改后重启transmission，然后打开settings.json文件，rpc-password会变成了一串加密密钥。

