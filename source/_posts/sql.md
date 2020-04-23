---
title: sql
date: 2020-04-17 13:48:22
categories: sql
summary: 记录sql一些常用方法操作注意等
tags:
 - sql
---

 1. in 查询结果排序
 ```sql oracle
   select * from   TFAPP_TEST_BASE  where ID in(117,118,116,144)  ORDER BY DECODE(ID, 117,1, 118,2,116,3,144,4)
 ```

 