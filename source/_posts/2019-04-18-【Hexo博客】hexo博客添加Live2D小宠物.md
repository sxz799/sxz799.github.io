---
title: hexo博客添加Live2D小宠物
copyright: true
date: 2019-04-18 17:09:30
tags:
- 博客
- hexo
categories:
- 总结
comments:
password:
---


在博客搭建之初这个插件我就用上了，时间久了，难免有些视觉疲劳，所以打算换个宠物。

[项目地址](https://github.com/EYHN/hexo-helper-live2d)
[预览地址](https://huaji8.top/post/live2d-plugin-2.0/)

## 一、安装Live2D插件
`npm install --save hexo-helper-live2d`
`npm install xxxxx`  //xxxxx是包名
下面是提供安装的列表，
```
live2d-widget-model-chitose
live2d-widget-model-epsilon2_1
live2d-widget-model-gf
live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haruto
live2d-widget-model-hibiki
live2d-widget-model-hijiki
live2d-widget-model-izumi
live2d-widget-model-koharu
live2d-widget-model-miku
live2d-widget-model-ni-j
live2d-widget-model-nico
live2d-widget-model-nietzsche
live2d-widget-model-nipsilon
live2d-widget-model-nito
live2d-widget-model-shizuku
live2d-widget-model-tororo
live2d-widget-model-tsumiki
live2d-widget-model-unitychan
live2d-widget-model-wanko
live2d-widget-model-z16
```
## 二、修改配置文件
在博客根目录的_config.yml配置文件中添加下面的内容
```
#Live2D动画
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  debug: false
  model:
    use: live2d-widget-model-shizuku
  display:
    position: right 
    width: 150
    height: 300
  mobile:
    show: true
```
主要参数说明
1. enable   //是否使用
2. model:
    use: live2d-widget-model-shizuku //要使用的模型名称
3. display:    
    position: right  //显示的位置
    width: 150			//宽度
    height: 150			//高度
  mobile:
    show: true			//移动端是否显示
##三、重新编译静态页面
下面的步骤就是Hexo三连
```
hexo clean
hexo g
hexo d
```