---
layout:    post
title:     linux启动管理
comments:  true
category: linux
tags: [linux]
---

## grub
* grub相关文件保存在/boot/grub目录中
* grub配置文件为/boot/grub/grub.conf

## init
init是linux系统中运行的第一个进程
调用/etc/rc.d/rc.sysinit负责对系统进行初始化，
挂载文件系统，并且根据运行级别启动相应服务

linux运行级别:

* -0 关机
* -1 单用户模式
* -2 不带网络的多用模式
* -3 多用户模式
* -4 未使用
* -5 图形化模式
* -6 重新启动

 命令`dmesg`可以查看本次启动时内核的输出信息

 可以通过/etc/inittab配置文件默认运行级别

 配置文件保存在/etc/init文件夹 

 每个运行基本的服务保存在/etc/rc.d/rc[0123456].d中

## 单用户修改root密码
* 为内核传递参数"1"或"single"进入单用户模式
* 单用户模式下不启动任何服务
* 使用passwd修改root密码

## GRUB加密
password --md5 md5加密后的密码

加密后的密码可以通过grub-md5-cypt生成
