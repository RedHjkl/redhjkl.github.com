---
layout:    post
title: 磁盘基本概念     
comments:  true
category: linux
tags: [linux]
---

## 磁盘基本概念 

* cylinder(柱面)
* sector(扇区)
* head(磁头)

## 磁盘在linux中的表示

* linux所有设备抽象为一个文件保存在/dev
* IDE:hd[a-z],
* SATA、SCSI、[SAS]、USB:sd[a-z]

## 分区概念
将整个磁盘分为几个区，每个区当作独立磁盘

* 不同分区用:设备名称+分区号 分区表示:sda1、sda2
* 主流分区 MBR GPT

## MBR
MBR(Master Boot Record) 是传统的分区机制，应用与绝大多数BIOS的PC设备。

* MBR支持32bit和64bit系统
* MBR支持分区数量有限
* MBR支持不超过2T的硬盘

## MBR 分区

* MBR最多支持4个主分区
* 扩展分区占用一个主分区位置
* 逻辑分区 linux支持63个IDE分区,和15个SCSI分区

## GPT 分区机制
GPT (GUID Partition Table) 十一个新的分区机制,解决了MBR很多缺点

* 支持超过2T磁盘
* 向后兼容** MBR **
* 必须在支持UEFI硬件上使用
* 必须使用64bit
* Mac,Linux都支持GPT分区格式

[SAS]: http://zh.wikipedia.org/wiki/%E4%B8%B2%E5%88%97SCSI
