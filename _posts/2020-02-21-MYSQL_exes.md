---
layout: post
title:  mysql与tushare的基金数据
categories: 
  - 笔记
tags:
  - mysql
excerpt:  mysql查询好慢
comments: true
---

将基金历年净值全部拷入到mysql中，查询卡到死。

200万行左右。

下次得优化一下表。

```sql

SELECT COUNT(DISTINCT ts_code) FROM fund_o
3593
4.412s

# 2
SELECT COUNT(ts_code) FROM fund_o
980000
0.982s

SELECT COUNT(*) FROM fund_o
980000
0.48
```
