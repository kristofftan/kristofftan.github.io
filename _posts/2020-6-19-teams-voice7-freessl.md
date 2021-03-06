---
layout:     post
title:      为测试Teams Direct Routing的时候申请免费的公网证书
subtitle:  
date:       2020-6-19
author:  Nemo
header-img: img/post-bg-universe.jpg
catalog: true
tags:

- Teams-Other
- 
---

当你想测试Teams Direct Routing的时候，其中的一个前置条件就是你需要为本地的测试SBC配置一张公网证书，但是我知道大家PoC阶段都不想有太多的投入就可以验证这个方案的可行性，包括今天所讲的这张公网证书。

至于有哪些比较好的公网证书供应商呢，可以参考那些经过[Teams Direct Routing认证的证书](https://docs.microsoft.com/en-us/MicrosoftTeams/direct-routing-plan#public-trusted-certificate-for-the-sbc)，其中的Godaddy是我比较推荐的（便宜，可靠，技术支持到位）

> The certificate needs to be generated by one of the following root certificate authorities:
>
> - AffirmTrust
> - AddTrust External CA Root
> - Baltimore CyberTrust Root
> - Buypass
> - Cybertrust
> - Class 3 Public Primary Certification Authority
> - Comodo Secure Root CA
> - Deutsche Telekom
> - DigiCert Global Root CA
> - DigiCert High Assurance EV Root CA
> - Entrust
> - GlobalSign
> - Go Daddy
> - GeoTrust
> - Verisign, Inc.
> - SSL.com
> - Starfield
> - Symantec Enterprise Mobile Root for Microsoft
> - SwissSign
> - Thawte Timestamping CA
> - Trustwave
> - TeliaSonera
> - T-Systems International GmbH (Deutsche Telekom)
> - QuoVadis

那今天的话题是要免费的，所以介绍其中一种申请免费公网证书的途径，有很多云平台厂家都可以提供公网证书的购买代理，例如你可以一站式在云平台厂家把云服务器，域名，证书一并购买并统一管理，同时在公网证书这一块通常都会有免费的单域名证书可以申请，例如今天我介绍的七牛云，其实在阿里云，腾讯云的管理后台都可以申请到，可以举一反三，灵活选择哈

首先在七牛云注册一个帐号，并登陆

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/20200520101441.png)

进入七牛云管理后台，进入SSL证书服务，就会发现可以申请一张免费的一年单域名证书，厂家是TrustAsia（免费的就凑合着用吧）

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/20200520101455.png)

完成支付流程后，一张空的证书就出来了，我们需要把需要的域名录入到证书当中，点击补全

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/20200520101508.png)

输入Teams Direct Routing中我们使用的PSTN Gateway FQDN名字，就是你本地的SBC的FQDN

选择DNS验证

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/20200520101521.png)

### 免费证书验证指南

添加TXT记录前，`请先获取您的证书信息`，您可以在`订单详情`中获取证书的验证信息。

![](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/20200520101536.png)

然后打开您的购买域名的厂商控制台，进入主域名的添加解析页面，您需要填写主机记录 _dnsauth ，选择记录类型 TXT ，并将 TXT 值复制到记录值中，如下图所示。

![img](https://dn-odum9helk.qbox.me/FhUEhqyHO6bH6KHc3nLQSNhiIw38)

解析添加正确后，正常检测系统会循环自动验证，最长不超过24小时，验证通过后等待一段时间，证书就会进行签发。



有了这张证书之后，你就可以继续配置本地SBC与Direct Routing之间的对接了 https://tangx007.github.io/2019/07/19/teams-voice5-sbc/ ，例如

![image-20200619162705603](https://cdn.jsdelivr.net/gh/tangx007/tangx007.github.io/img/image-20200619162705603.png)



参考：

https://portal.qiniu.com/certificate/ssl/