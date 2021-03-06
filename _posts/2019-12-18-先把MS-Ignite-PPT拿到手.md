---
layout:     post
title:      微软 Teams Meeting 系列(1) 
subtitle:  先把MS Ignite PPT拿到手
date:       2019-12-18
author:  Nemo
header-img: img/post-bg-universe.jpg
catalog: true
tags:

- Teams-Meeting
- 
---

> 2020-5-15从51cto迁移至此

在过去的2019年11月，微软举行了Ignite 2019技术大会，里面有非常多的技术干货，相信各位同学都想着怎么把这场技术大会里面的PPT与Video拿到手吧？本文为MS Ignite 2019 系列的开端，为大家带来一个非常直观可行有针对性地下载Ignite PPT的方法（使用Power Query把下载链接爬虫下来）

这个MS Ignite 2019 系列主要针对 Teams Meetings Learning Path Sessions 相关的议题，期待这个系列能在春节前完工啦：

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/m1111118a39e22951768551655a77bceaa7a00a.png)

其实在网上已经有很多国外大牛们使用Poweshell做成的下载脚本，但不太符合我的习惯（Youtu下载，根据session id下载…..），不太直观，而我需要的是根据关键字下载，可以断点续传，按需下载….开门见山，如下方法：

1. 打开Excel, 按以下步骤来使用Excel来抓取Ignite的演讲信息：

https://api-myignite.techcommunity.microsoft.com/api/session/all

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/m222221ffbca97bbe819248f689b9e7dc59125.png)

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/mmmme3a34c8129aef8c8421d68b21cf20f56.png)

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/m4444441c3051b77313b332bc62fc0013498a04.png)

2. 抓取完后，会打开Power Query (MS Excel的最最最有价值的功能)，按以下操作做一下数据处理：

以下数据字段你需要选上：

- title  
- description  
- downloadVideoLink  （video下载链接）
- sessionCode  
- slideDeck  （PPT下载链接）

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/m555557cdd0d72a391b4e8d1bc906b4001f4be.png)

3. 接着，在Title字段下筛选出你关心的技术主题，例如我是选择Teams. 其中第四步，PowerQuery会把数据回传给Excel，生成表格:

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/m66660e573d171f0c681aa82a89739761eb1b.png)

老实说，相比使用Powershell脚本下载来说，它的优点是简单，粗暴，直观，可行，无技术含量的下载方法，同时你又可以学到Excel的新技能Power Query，一举两得。

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/m777778147d5df45d07545190bebbf02789113.png)

------

欢迎添加我的微信，分享您的见解与我的解决方案哦，让我们共同探索。

<img src="https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/nemo-qrcode.jpg" style="zoom:50%;" />