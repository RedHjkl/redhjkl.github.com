---
layout:    post
title:     selinux基本使用
comments:  true
category: linux
tags: [linux]
---
## SELinux 基本信息

	ls -Z 查看文件的上下文
	ps -Z 查看进程的域

## 策略

Centos/RHEL 使用预置的目标(target)策略
目标(Target) 策略定义只有目标进程受到SELinux限制 其它进程运行在非限制模式下

## SELinux有三种工作模式

配置文件:
/etc/sysconfig/selinux

* 强制(enforcing) 违反策略的行为都被禁止 
* 允许(permissive) 违反策略的行动不会被禁止
* 禁用(disabled) 禁用SELINUX

### 常用命令: 
	getenforce 查看selinux工作状态
    setenforce 临时设置selinux工作状态
	restorecon -R -v /var/www 恢复文件默认的上下文
	chcon --reference=/etc/named.conf.orig /etc/named.conf 改变文件的上下文
selinux 报错信息保存在/var/log/audit/audit.log
