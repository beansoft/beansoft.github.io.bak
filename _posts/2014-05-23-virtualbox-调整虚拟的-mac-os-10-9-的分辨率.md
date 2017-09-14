---
id: 3652
title: VirtualBox 调整虚拟的 Mac OS 10.9 的分辨率
date: 2014-05-23T18:58:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3652
permalink: '/2014/05/23/virtualbox-%e8%b0%83%e6%95%b4%e8%99%9a%e6%8b%9f%e7%9a%84-mac-os-10-9-%e7%9a%84%e5%88%86%e8%be%a8%e7%8e%87/'
views:
  - "10022"
categories:
  - iOS
tags:
  - VirtualBox
---
VBoxManage setextradata "Mac OS 10.9" VBoxInternal2/EfiGopMode 5

测试通过, 5 是 1920&#215;1080, 其中 "Mac OS 10.9" 是虚拟机的名称. 如果把末尾的5修改成0到4, 那么分别对应下面的分辨率:

0 – 640×480   
1 – 800×600   
2 – 1024×768   
3 – 1280×1024   
4 – 1440×900   
5&#160; &#8211; 1920&#215;1200

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [VirtualBox 调整虚拟的 Mac OS 10.9 的分辨率](http://www.beansoft.biz/2014/05/23/virtualbox-%e8%b0%83%e6%95%b4%e8%99%9a%e6%8b%9f%e7%9a%84-mac-os-10-9-%e7%9a%84%e5%88%86%e8%be%a8%e7%8e%87/)