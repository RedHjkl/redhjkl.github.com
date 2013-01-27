---
layout:    post
title:    ubuntu tips 
comments:  true
category: ubuntu
tags: [ubuntu]
---

## 修复ibus 输入标志
    ibus-daemon -x -r -d

`virtualbox` <kbd>sudo apt-get install virtual</kbd>

### Linux下HTML文件转化为pdf
`wkhtmltopdf`	
    下载地址http://code.google.com/p/wkhtmltopdf/
使用方法:
    wkhtmltopdf-i386 --use-xserver 网址

## axel下载工具
    安装:sudo apt-get install axel
    一般使用：axel url（下载文件地址）
    限速使用：加上 -s 参数，如 -s 10240，即每秒下载的字节数，这里是 10 Kb
    限制连接数：加上 -n 参数，如 -n 5，即打开 5 个连接

