---
layout:    post
title:     管道和重定向
comments:  true
category: linux
tags: [linux]
---

## 管道及重定向

* STDIN 0 标准输入 键盘
* STDOUT 1 标准输出 终端
* STERR 2 标准错误 终端

## 重定向

    > 将STDOUT重定向到文件(覆盖) 
    >> 将STDOUT重定向到文件(追加)
	2> 将标准错误重定向到文件
	2>&1 STDERR与STDOUT结合
	< 重定向STDIN

## 管道

	| 将一个命令的STDOUT作为另一个命令的STDIN
