---
layout:    post
title:    文件系统和磁盘分区 
comments:  true
category: linux
tags: [linux]
---

## 1.fdisk分区工具

fdisk 基于MBR的分区工具,如果需要GPT，则
无法使用fdisk进行分区.

fdisk 只有超级用户才能够使用

* fdisk -l列出所有安装磁盘以及分区信息
* fdisk /dev/sdb 进行

常用命令: `l` `n`: 

    p primary partion
    e extend partion

分区之后需要`partprobe`更新内核分区信息
    cat proc/patitions 查看分区信息
    fdisk -l 查看分区信息
    ls etc/

----

## 2.文件系统
创建文件系统的过程称为格式化
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

----

## mount挂载操作
linux系统需要手工挂载或者配置自动挂载
最好挂载到/mnt

常用参数

* -t 制定文件系统类型 
* -o 制定挂载选项 
        ro; rw 只读/读写方式挂载
		sync 代表不使用缓存,而是对所有操作直接写入磁盘
		async 代表使用缓存 默认是async
		noatime 代表每次访问时不更新文件访问时间
		atime 代表每次访问文件时更新文件的访问时间
		remount 重新挂载系统

卸载操作
    umount /dev/sdb1

如果无法卸载
    fuser -m /mnt 查看那些文件系统被进程使用
    lsof 查看正在使用的文件

## 自动挂载

	配置文件/etc/fstab用来定义需要自动挂载的文件系统

    /dev/sdb1	/mnt	ext4	default	0 0
    需要挂载的设备 挂载点  文件系统   挂载选项  dump fsck选项

	自动挂载时的/dev/sdb1 修改为卷标挂载LABEL=卷标
