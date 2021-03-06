---
layout:    post
title:     linux 常用命令 
comments:  true
category:  linux
tags:      [linux]
---

# 时间命令

## 查看系统时间
    date
* date -u 查看UTC时间
* date +%Y--%m--%d 格式化显示
* date -s "20:20:20"

## 查看硬件时间
	hwclock(clock) 任一皆可

## 查看日历
	cal

## 查看系统运行时间
	uptime

----

# 输入输出命令

## 显示输入内容
	echo

## 显示文件内容
	cat

## 翻页命令查看
	more 只可下翻页，不可上翻页
	less 可向上翻页

## 显示几行
	head 显示开头十行
*   -n 指定行数 
	tail 
*	-n 指定末尾行数
	-f 追踪显示文件的更新(用于查看日志)

##  查看磁盘文件使用情况
	du -sh
常用参数:
	-s 不统计子目录,只显示当前目录
	-h 容易读的形式显示

----

# 硬件信息查看

## 查看PCI设备
	lspci 
*   -v 查看详细信息

## 查看USB设备
	lsusb 
*   -v 查看详细信息

## 查看加载的模块
    lsmod

----

# 关机重启

## 关机重启计算机
	shutdown [-h,-r] 时间

*   -h 关闭计算机
*   -r 重启
*	shutdown -h now 立即关机
*	shutdown -h +10 10分钟关机
*	shutdown -h 23:30 23:30分关机
*	power off 立即关机
*	reboot 立即重启

----

# 压缩解压缩

## 归档、压缩

	命令zip压缩文件
	zip *.zip myfile
	unzip *.zip 
	命令gzip压缩
	gzip linuxcast.net
	归档文件
* tar -cvf out.tar myfile
* tar -xvf out.tar
* tar -zcvf *.tar.gz /mycat -z参数将归档后的归档文件进行gzip压缩以减少大小
* tar -xzvf *.tar.gz -C 目录 将文件解压缩到 目录 中

----

# 查找

## 快速查找
	locate fienname 命令预先建立数据库,数据库默认每天更新一次
	updatedb 手工更新数据库

## 高级查找文件、文件夹
	find 查找位置 查找参数
*   find . -name *name*
*	find / -name *.conf
*   find / -perm 777 所有权限只能使用数组
*	find / -type d 查找所有目录
*	find . -name "a*" -exec ls -l {} \;查找所有文件名以a开头文件执行ls -l
*	常用查找的条件
*	-name
*	-perm
*	-user 所有用户
*	-group 所有组
*	-ctime
*	-type
*	-size

----

## linux帮助

command -h --help 查看命令帮助 

## man

man 文档类型

* 1	用户命令
* 2 内核系统调用
* man -k 关键字 查看该关键字的文档

## info

info 与man类似，类似网页形式

man和info 都可以使用/进行搜索

## DOC

统一保存在/usr/share/doc


