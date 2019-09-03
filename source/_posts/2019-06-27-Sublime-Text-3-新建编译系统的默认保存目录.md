---
title: Mac OS 下Sublime Text 3 编译C++
copyright: true
date: 2019-06-27 00:39:45
tags:
- 防痴呆
categories:
- 技巧
comments:
password:
---

## 设置步骤
 1.工具->编译系统->新建编译系统
然后将下面的内容复制到新打开的文件
保存时的文件名为XXX.sublime-build ,其中XXX为工具->编译系统中显示的文件名

Mac下的编译系统文件
```
{
    "cmd": ["g++", "${file}", "-o", "${file_path}/${file_base_name}"],
    "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
    "working_dir": "${file_path}",
    "selector": "source.c, source.c++",

    "variants":
    [
        {
            "name": "Run",
            "cmd": ["bash", "-c", "g++ -std=c++11 '${file}' -o 'a' && open -a terminal '${file_path}/a'"]
        }
    ]
}
```

Win10下的编译系统文件：
```
{   
  "encoding": "utf-8",  
  "working_dir": "$file_path",  
  "shell_cmd": "g++ -Wall \"$file_name\" -o \"$file_base_name\"",   
  "file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",            
  "selector": "source.c++",     
  "variants":   
  [     
    {           
      "name": "Run",            
      "shell_cmd": "g++ -Wall  \"$file\" -o \"$file_base_name\" && start cmd /c \"\"${file_path}/${file_base_name}\" & pause\""     
    }   
  ]
}
```

## Sublime Text 3 新建编译系统的默认保存目录
要先显示隐藏的目录和文件

MAC OS⁩ ▸ ⁨用户⁩ ▸ ⁨sxz ▸ ⁨资源库⁩ ▸ ⁨Application Support⁩ ▸ ⁨Sublime Text 3⁩ ▸ ⁨Packages⁩ ▸ ⁨User⁩
注：
MAC OS修改为你的磁盘名
sxz修改为你的用户名
