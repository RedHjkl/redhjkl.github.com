---
layout:   post
title:    linux权限控制 
comments: true
category: linux
tags:	  [linux] 
---

## 权限

限制资源进行访问的机制
	对文件的影响	对目录的影响
* r 可读取文件内容	可列出目录内容
* w 可以修改文件内容 可在目录中创建删除文件
* x 可以作为命令执行 可以访问目录内容

tip: 对于目录必须同时具有rx权限 

## UGO模型

* U:user G:Group O:Other
* 权限三个一组(rwx)

修改文件所属用户、组
    命令chown用于改变文件所属用户
	chown 用户名 FILE...
	-R 递归修改所有用户
	命令chgrp用于改变文件的所属组
	
## 修改权限
命令chmod用以修改文件的权限
chmod 模式 文件
格式
	u、g、o分别代表用户，组和其它
	a可以代表ugo
	+、-代表加入或删除对应的权限
	r、w、x代表三种权限
示例:
	chmod u+rw FILE
	chmod g-x FILE
	chmod go+r FILE
	chmod a-x FILE
	chmod -R a-x FILE 递归修改文件夹内部

权限也可以用三个数字表示
r:4 w=2 x=1
    chmod 660 FILE 对应 rw-rw----
	chmod 775 FILE 对应 rwxrwxr-x

----

## linux扩展权限 
umask用数字权限方式

* 目录的默认权限是:777-umask
* 文件的默认权限是:666-umask
* 一般，普通用户默认umask 002,
  root用户的默认权限是022

命令umask用以查看设置umask值
	umask 值 

## 特殊权限

* suid: 以文件所属用户身份执行,而非执行用户 例:passwd
* sgid: 以文件所属组身份执行在该目录创建任意新文件所属组与该目录所属组相同
* sticky:	对目录拥有写入权限用户仅可以删除自己的文件
						

## 设置特殊权限

设置suid:
	chmod u+s 文件名
设置sgid:
	chmod g+s 文件名
设置sticky:
	chmod o+t 文件名
特殊权限也可以使用数字表示
	SUID = 4
	SGID = 2
	Sticky = 1
命令:
	chmod 4755 文件名
