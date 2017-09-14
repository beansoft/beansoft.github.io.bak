---
id: 3064
title: Oracle发布VirtualBox 4.2.0
date: 2012-09-20T09:30:54+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3064
permalink: '/2012/09/20/oracle%e5%8f%91%e5%b8%83virtualbox-4-2-0/'
views:
  - "3617"
image: /wp-content/uploads/2012/03/vbox_logo2_gradient.png
categories:
  - Cloud/VM
tags:
  - VirtualBox
---
来自官方<http://www.oracle.com/us/corporate/press/1842885>的消息，Oracle在2012年9月13日发布了 Oracle VM VirtualBox 4.2.0。效率增强，网络改进和更多的平台支持。个人觉得最有用的就是VM自动启动功能了，这个可以给很多云计算提供商或者虚拟主机提供商省去很多管理上的麻烦。新平台支持也很有用：Windows 8, Mac OS X 10.8 "Mountain Lion" 和Oracle Linux 6.3.

下载地址：<http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html>或<https://www.virtualbox.org/wiki/Downloads>。

&#160;

  * **增强管理功能，增加VM分组功能** 

[<img style="background-image: none; border-right-width: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2012/09/image_thumb.png" width="638" height="329" />](http://www.beansoft.biz/wp-content/uploads/2012/09/image1.png)

  * **更方便的启动** 

无需用户交互的虚拟机现在可以和普通虚拟机一样启动了。另外所有类型的虚拟机都可以设置为随宿主系统自动启动，这样虚拟机的管理就和其他主机一样了。

#### 注意，不支持Windows，参考帮助文档： 9.24. Starting virtual machines during system boot：<a name="autostart"></a>

Starting with VirtualBox 4.2.0 it is possible to start VMs automatically during system boot on Linux, Solaris and Mac OS X for all users.

  * **网络改进** 

最大虚拟网卡数从8增加到了36个，这样无需昂贵的硬件设备就可以进行复杂的网络模拟。

新增网络带宽控制功能。

虚拟网卡现在支持VLAN标记，可参与VLAN环境。

  * **新平台支持** 

Windows 8, Mac OS X 10.8 "Mountain Lion" 和Oracle Linux 6.3。搞iOS开发的不用再买苹果笔记本了。

![](http://www.oracle.com/us/corporate/vm-latest-platforms-large-1843205.jpg?iframe=true&width=640&height=500)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Oracle发布VirtualBox 4.2.0](http://www.beansoft.biz/2012/09/20/oracle%e5%8f%91%e5%b8%83virtualbox-4-2-0/)