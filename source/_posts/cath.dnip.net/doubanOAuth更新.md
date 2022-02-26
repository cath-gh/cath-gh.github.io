---
title: doubanOAuth更新
date: 2013-01-26 17:30:00
cover: https://s2.loli.net/2022/02/26/2pr5btu9mi1kvQn.jpg
thumbnail: https://s2.loli.net/2022/02/26/2pr5btu9mi1kvQn.jpg
categories:
- [旧文]
- [代码]
tags:
- 豆瓣
- C#
- doubanOAuth
- cath.dnip.net
---
### 原文
源码：[https://github.com/cath-gh/doubanOAuth](https://github.com/cath-gh/doubanOAuth)

2013.01.26

终于调通了发图的部分，另外增加了`ErrorCatched`事件。

<!--more-->

关于发图：

+ 首先说给书记写笔记时，图片顺序无所谓，但是图片编号必须从`1`开始，且不间断
+ 发日记中带图，`pids`参数传递图片编号，类型为`List<int>`，不要求起始数字，也不需要连续。`layout`、`desc`、`imagePath`要求其数量与`pids`一致。

已知问题：

+ Shuo，block用户仍然不行，依然需要知情人的帮助
+ 日记发图，不清楚为什么在日记内容末端会自动添加所包含的图片

### 再读旧文
> 以上内容为旧文搬运，文中链接、图片、方法均已不可考，仅做个人记录  
> 日期：2022年2月26日