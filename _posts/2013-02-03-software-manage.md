---
layout:    post
title:     软件管理
comments:  true
category: linux
tags: [linux]
---

## 源代码安装
* 1-./configure 检测编译环境，相关库文件，以及配置参数并生成makefile
* 2- make 对源代码进行编译，生存可执行文件
* 3- make install 将生成的可执行文件安装到计算机中

## RPM(redhat package manager)软件包管理

### RPM软件命名规范 
name-版本号-el6-i686-rpm

### RPM基础命令:
    -安装软件:rpm -l software.rpm
	-卸载软件:rpm -e software
	-升级形式安装:rpm -U software-new rpm
	-http ftp 协议安装:rpm -lvh url
### 参数:

* -v 显示相关信息
* -h 显示进度条

### rpm查询功能:

* rpm -qa 列出所有rpm软件
* rpm -qi software 查询特定软件
* rpm -ql 列出所有属于这个软件的文件
* rpm -qf 列出文件属于的rpm包
* rpm -qip 查询未安装的文件信息
* rpm -qlp 查询未安装的创建的文件

### rpm验证
导入验证
    rpm --import RPM-GPG-KEY-CentOs-6
验证rpm文件
    rpm -K 
验证已安装文件
    rpm -V
