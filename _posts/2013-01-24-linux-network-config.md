---
layout:    post
title:     linux网络配置
comments:  true
category: linux
tags: [linux]
---
## linux网络配置
* linux 以太网接口被命名为 eth0,eth1
* lspci 查看网卡硬件信息(lsusb查看usb网卡)

lfconfig查看接口信息
    lfconfig -a 查看所有接口
	lfconfig eth0  查看特定接口
ifup ifdown启用、禁用接口
    ifup eth0	启用网卡接口
	ifdown eth0 禁用网卡接口

## 网卡配置文件

    /etc/sysconfig/network-scripts/ifcfg-eth0
dns配置文件 
    /etc/resolv.conf
主机名配置文件
	/etc/sysconfig/network
静态主机名配置文件
	/etc/hosts
## 网络测试命令

测试网络联通性
	ping 192.168.1.1
	print www.google.com
测试DNS解析
	host www.google.com
	dig www.google.com
显示路由表
	ip route
追踪到达目标地址网络路径
	traceroute www.google.com
使用mtr进行网络质量测试
	mtr www.google.com
## 修改主机名
永久修改主机名
    /etc/sysconfig/network
