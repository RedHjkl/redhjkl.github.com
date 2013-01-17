---
layout:    post
title:    文件系统和磁盘分区 
comments:  true
category: linux
tags: [linux]
---

# 磁盘分区与文件系统
## fdisk分区工具

fdisk 基于MBR的分区工具,如果需要GPT，则
无法使用fdisk进行分区.

fdisk 只有超级用户才能够使用
* fdisk -l列出所有安装磁盘以及分区信息
* fdisk /dev/sdb 进行
    常用命令: `l`
	`n`: p primary partion
	`n`: e extend partion
* 分区之后需要`partprobe`更新内核分区信息
	cat proc/patitions 查看分区信息
	fdisk -l 查看分区信息
	ls etc/

----

## 文件系统
> 创建文件系统的过程称为格式化
linux 支持文件系统
    ext2 ext3 ext4 fat vfat
	nfs iso9660 proc gfs jfs

## mke2fs 创建文件系统
    mke2fs -t ext4 /dev/sda3
常用参数
* -b blocksize 指定文件系统块大小
* -c 建立文件系统时检查坏损块
* -L label 制定卷标
* -j 建立文件系统日志 ext3 ext4不需要

## mkfs
    mkfs.ext4 /dev/sdb1

## 查看文件系统信息
    dumpe2fs /dev/sdb1

## journal 日志
带有日志的文件系统可以在出错的时候可以进行恢复 

## e2label 可以添加标签
	e2label /etc/sdb1 查看标签
	e2label /etc/sdb1 SYS 增加标签，约定为大写

## fsck 检测并修复损害文件系统
	fsck /dev/sda2 必须先卸载

* -y 不提示进行修复
* -t fsck默认自动检测文件系统,如果文件系统损害严重最好加上-t
* lost+found损坏数据fsck会将文件放入lost+found文件目录


