---
title: 豆瓣SDK doubanOAuth
date: 2013-01-20 13:53:00
urlname: douban-sdk-doubanOAuth
cover: https://cdn.jsdelivr.net/gh/cath-gh/pictures@main/Obsidian/cath-gh.github.io/douban.webp
thumbnail: https://cdn.jsdelivr.net/gh/cath-gh/pictures@main/Obsidian/cath-gh.github.io/douban.webp
categories:
  - [旧文]
  - [IT]
tags:
  - 豆瓣
  - doubanOAuth
  - cath.dnip.net
---
### 原文
基于豆瓣API V2提供的接口，使用C#做了下简单的封装。实现了全部已知的方法，大部分已调通，个别实现还存在一些问题。

+ 各种传图的方法，`image`参数无效，后续版本待修改
+ Mail，发豆邮频率过大导致需要输入验证码部分未实现
+ Shuo，block用户不可用（希望有了解`block`参数设置的同学帮忙）
+ Note，更新日记返回`json`字符串而不是对象，暂时未处理

<!--more-->

本代码需要.Net4.0的支持，最初是为了应用`dynamic`解决`photos`的字段命名问题，后来发现用`object`可以代替，不过可选参数确实需要4.0的支持。

关于更新：我当然希望把这个sdk做好，只是在这个过程中感到豆瓣提供的信息很少，困难很多。考虑到V1的api即将停用，估计V2版本会有较大程度的更新，我也会适时的跟进

关于代码：

+ 所有的方法的是static的，调用比较方便，对于有洁癖的同学或许有点不适，我也在想改进的办法
+ `HttpWebRequest`的构造中，`referer`用了我自己小站的地址，不喜欢的可以修改代码
+ 提供了`Common.LastError` 以查阅最新的错误信息，按说应该提供事件支持的，我还没想好是采用事件还是`Exception`的方式，以后会完善
+ 方法名前缀缩写说明

|  |  |
| ------------- | ------------- |
| User | Usr |
| Authentic | Auth |
| Book | Bk |
Music|Mus
Movie|Mov
Collection|Col
Annotation|Anno
Event| Evt
Discussion|Disc
Online| Onl
Photo|Pho
Comment|Comm

关于文档：我不善于写文档，却对文档有着精品情节。对于现在这样一个姑且称之为半成品的东西，文档暂时没有，好在代码里注释还算丰富，也尽量做到了自解释命名

---

源码：[https://github.com/cath-gh/doubanOAuth](https://github.com/cath-gh/doubanOAuth)

### 再读旧文
> 以上内容为旧文搬运，文中链接、图片、方法均已不可考，仅做个人记录  
> 日期：2022年2月26日