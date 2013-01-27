---
layout:    post
title:     linux文本处理命令
comments:  true
category: shell
tags: [shell]
---

## 基于关键字搜索
使用grep关键字搜索文本
grep 'username' /etc/passwd 
find / -user username| grep Video

* -i 搜索忽略大小写
* -n 显示结果所在行数
* -v 输出不带关键字的行
* -Ax 在输出的时候包含结果所在行之后的指定行数
* -Bx 在输出的时候包含结果所在行之前的指定行数

## 基于列处理文本
命令cut用以基于列处理文本内容
例子:
	cut -d: -f1 /etc/passwd
	grep yan /etc/passwd | cut -d: -f3

常用参数:

* -d 指定分割字符
* -f 制定输出的列号
* -c 基于字符进行分割
	cut -c2-6 /etc/passwd 只显示2-6

## 文本统计
命令wc 进行文本统计
常用参数:

* -l 只统计行数
* -w 只统计单词
* -c 只统计字节数
* -m 只统计字符数

## 文本排序
命令sort用以对文本内容进行排序

* -r 进行到序排序
* -n 基于数字进行排序
* -f 忽略大小写
* -u 删除重复行
* -t c 使用c作为分割符分割为列排序
* -k x 当进行基于指定字符分割为列的排序时，制定基于那个列排序

uniq可以用于删除重复行

## 文本比较

命令diff比较文件的区别

* -i 忽略大小写
* -b 葫芦额空格数量的改变
* -u 统一显示比较信息

diff -u 1.txt 1-new.txt > *.patch

## 检查拼写
命令aspell用以显示检查英文拼写
    kspell check linux
    aspell list < linux

## 处理文本内容
* 删除关键字
	-tr -d 'TMD' 1.txt
* 转化大小写
	-tr 'a-z' 'A-Z' < 1.txt

## 搜索替换
命令sed用以搜索并替换文本
	sed 's/linux/unit/g' 1.txt
	sed '1,50 s/linux/unit/g' 1.txt

常用参数:
* -e 替换多个
* -f sededit 1.txt

