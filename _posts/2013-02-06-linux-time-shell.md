---
layout:    post
title:     linux定时任务命令
comments:  true
category: shell
tags: [shell]
---

## crontab
`crontab` [-u user] -e -l -r
 常用命令:
* -u 用户名
* -e 编辑crontab文件
* -l 列出crontab文件中的内容
* -r 删除crontab文件内容
  惯用法:
每晚21:30运行/apps/bin
	30 21 * * * /apps/bin/cleanup.sh

每月1 10 22 日的4:45运行/apps/bin目录下的backup.sh
	45 4 1,10,22 * * /apps/bin/backup.sh

每周六、日的1:10运行一个find命令
	10 1 * * 6,0 /bin/find -name "core" -exec rm { } \
每天18：00至23:00之间每隔30分钟运行/apps/bin下的dbcheck.sh
	0,30 18-23 * * * /apps/bin/dbcheck.sh
每星期六23：00pm运行/apps/bin目录下的qtrend.sh
	0 23 * * 6 /apps/bin/qtrend.sh

## at 命令
