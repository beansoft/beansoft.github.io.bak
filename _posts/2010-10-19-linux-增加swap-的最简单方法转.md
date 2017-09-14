---
id: 1326
title: 'Linux 增加swap 的最简单方法[转]'
date: 2010-10-19T12:26:52+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1326
permalink: '/2010/10/19/linux-%e5%a2%9e%e5%8a%a0swap-%e7%9a%84%e6%9c%80%e7%ae%80%e5%8d%95%e6%96%b9%e6%b3%95%e8%bd%ac/'
views:
  - "2966"
original_post_id:
  - "1326"
categories:
  - Linux/Unix
---
[http://blogs.oracle.com/longchun/2009/06/linux_swap.html](http://blogs.oracle.com/longchun/2009/06/linux_swap.html "http://blogs.oracle.com/longchun/2009/06/linux_swap.html")

By [longchun.zhu](http://zhulch.itpub.net) on June 19, 2009 11:56 AM 

1. 查看现在的SWAP的使用情况   
free -m

2.格式化空间给SWAP   
dd if=/dev/zero of=/OVS/swap bs=1024 count=1024000   
3.创建SWAP   
mkswap /OVS/swap   
4.激活SWAP   
swapon /OVS/swap   
5.写到守侯进程中   
/etc/fstab   
（/VOS/swap swap swap defaults 0 0 ）

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Linux 增加swap 的最简单方法[转]](http://www.beansoft.biz/2010/10/19/linux-%e5%a2%9e%e5%8a%a0swap-%e7%9a%84%e6%9c%80%e7%ae%80%e5%8d%95%e6%96%b9%e6%b3%95%e8%bd%ac/)