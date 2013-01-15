---
layout:    post
title:    ubuntu && xp 双系统 
comments:  true
category: linux
tags: [linux]
---

# 今天介绍一下ubuntu和xp双系统的安装

## ubuntu的安装

> 引用[ggjucheng]的blog文章太棒了。因为自己有两块硬盘，为了方便家人使用，所以安装xp，Ubuntu双系统，我的台式机有两块硬盘，所以我将grub写到第二块硬盘，参照我后面的menu.list截图，可以自己搜索启动grub引导。

----

## 下载

> 需要下载的东西有两个，一个是[grub4dos]，另一个是[Ubuntu 12.04 LTS]的镜像文件.

----

## 准备工作

> 准备工作 解压grub4dos压缩包，会得到一个名为grub4dos-0.4.4的文件夹，
> 将以下文件拷贝到C盘（其中前两个文件是必需的，后两个文件网上有些资料说不需要，
> 为了保险起见还是放上吧，反正也没什么坏处～）
`grldr`　`menu.lst`　 `grldr.mbr`　 `grub.exe`

> 解压*`ubuntu-12.04-desktop-i386.iso`*中casper文件夹下面的vmlinuz和initrd.lz
> 到C盘，网上也说需要把压缩包中.disk文件夹解压到C盘，好吧，照做！
> *`ubuntu-12.04-desktop-i386.iso`*文件也拷贝到C盘。

----

## 修改文件

> 修改menu.list文件,在末尾添加以下内容
	title Install Ubuntu12.04
	root (hd0,0)
	kernel (hd0,0)/vmlinuz boot=casper iso-scan/filename=/ubuntu-12.04-desktop-i386.iso locale=en_US.UTF-8
	initrd (hd0,0)/initrd.lz
> 其中，title后面的内容随便写就是，kernel后面的显示的就是Ubuntu 12.04
> 的镜像文件，需要与C盘中的文件名对应。

> 修改boot.ini，打开文件后，在文件最后添加如下内容
    c:\grldr=”Ubuntu Install” `boot.ini`文件位于c盘根目录

> 进入ubuntu开始安装之前有一个很重要的步骤需要做，具体如下:
    Alt+Ctrl+t 调出终端，输入指令：sudo umount -l /isodevice

> 如果不将grub写入mbr，则可使用grub4dos来管理启动启动器:
> 将boot.ini文件修改
> c:\grldr=”Ubuntu”
> 记得C盘根目录下面使用grub4dos里四个文件:
> `grldr`　`menu.lst`　 `grldr.mbr` `grub.exe`
> 下面是我的menu.listu 文件
    title ubuntu 12.04  (/boot on single partitionas)
	find --set-root /grub/core.img
	kernel /grub/core.img
	boot

## 先介绍到这里...

[ggjucheng]: http://www.cnblogs.com/ggjucheng/archive/2012/08/18/2645916.html
[grub4dos]: http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download
[Ubuntu 12.04 LTS]: http://www.ubuntu.com/download/desktop
