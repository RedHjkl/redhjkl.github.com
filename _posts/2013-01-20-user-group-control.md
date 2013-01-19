---
layout:    post
title:     用户和组管理
comments:  true
category: linux 
tags: [linux]
---

## 用户、组

* 每个用户拥有一个`userid` 操作系统使用的是用户ID，而非用户名
* 每个用户有一个主组,属于一个或多个附属组
* 每个组拥有一个GroupID
* 每个进程以一个用户身份运行，接受该用户的访问权限
* 每个用户有一个shell

## 用户

Id 32位 Id限制在60000以下
用户分以下三种:

* root 所有ID为0为root用户
* 系统用户 (1-499) 没有shell 为程序服务使用
* 普通用户(500以上)

### 显示用户命令
    id命令可以显示当前用户信息
    passwd 修改用户密码

### 用户相关文件

* /etc/passwd -用户信息
* /etc/shadow -用户密码
* /etc/group -组信息 

## 查看登录的用户
    whoami 显示当前用户
    who 显示当前那些用户登录到系统上
    w 显示用户，和用户正在执行的操作


`useradd` yanwh 创建一个用户

    -d 家目录
    -s 登录shell
	-u userid
	-g 主组
	-G 附属组(最多31，用","分割)

`passwd` yanwh 修改用户密码

### 新建用户执行操作

* 在/etc/passwd中添加用户信息 
* 如果使用passwd命令创建密码,即将密码加密保存在/etc/shadow中
* 为用户创建一个新的家目录/home/*
* 将/etc/skel中的文件复制到用户家目录中
* 建立一个与用户用户名相同的组,新建用户默认属于这个同名组

##  修改用户信息

命令`usermod`用来修改用户信息

### 格式:usermod 参数 username
命令的参数:

    -l 新用户名
	-u 新userid
	-d 用户家目录位置
	-g 用户所属主组
	-G 用户所属附属组
	-L 锁定用户使其不能登录
	-U 接触锁定

## 删除用户

    userdel 用户名 (不删除家目录)
    userdel -r 用户名 (删除用户家目录)

----

## 组

* 每个组有一个组id
* 组信息保存在/etc/group中
* 每个用户拥有一个主组,同时还可以拥有最多31个附属组

## 创建、修改、删除组

    groupadd 组名 创建用户组

    groupmod -n 新组名 旧组名 修改组名
    groupmod -g 新组id 旧组id 修改组id

    groupdel 组名 删除组


