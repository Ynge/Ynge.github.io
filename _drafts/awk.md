---
layout: post
title: awk实用片段
categories: [后端,awk]
description: awk
keywords: awk,shell
---
## navicat 导出sql表和数据,批量修改表名
```shell
cat  *.sql |grep -v 'INSERT\|DROP\|--'|awk '{gsub(/`b_/,"`demolition_");gsub(/BTREE,/,"BTREE");if($1!="INDEX" && $1!="CONSTRAINT"){print;}}'i > tables.sql
```
