---
id: 1477
title: VMWare虚拟机下的RedHat上网视频
date: 2010-12-04T22:34:53+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1477
permalink: '/2010/12/04/vmware%e8%99%9a%e6%8b%9f%e6%9c%ba%e4%b8%8b%e7%9a%84redhat%e4%b8%8a%e7%bd%91%e8%a7%86%e9%a2%91/'
views:
  - "3402"
original_post_id:
  - "1477"
image: /wp-content/uploads/2012/09/cloudy.png
categories:
  - Cloud/VM
---
这个视频是2005-10-28做的，用的虚拟机是RedHet 9，在下面跑Java，测试Linux程序。需要指出的是，现在好多新的Linux发行包例如Fedora，Ubuntu等等都不需要设置，安装完就能在虚拟机里面用自动获取IP的方式工作，所以这个视频仅供参考，操作步骤可以参考BlogJava网友的文章：[VMware中用NAT方式实现FreeBsd/Linux上网](http://www.blogjava.net/pdw2009/archive/2008/03/09/184817.html)

视频下载地址：<http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/video/VMWareLinux%5E_net.swf>

<http://cid-519b3f7aa2172030.office.live.com/embedicon.aspx/Public/video/VMWareLinux_net.swf> 

&#160;

700 K 推荐下载后全屏观看

相关资料:

我用的是VMware版本是 5.5.3，host机器运行的是windows Xp professional 。

1、安装VMware workstation

2、安装guest系统，这里我安装的Red Hat Linux9，安装过程中确保网络连接选择的是NAT方式，当然可以在安装完后进行修改。

3、到windows XP 中，查看所有的网络连接，你应该发现除了原有的网卡之外，又多了Vmnet1和Vmnet8。vmnet1是hostonly的接口，而Vmnet8是就是我们要使用的NAT的网络接口。

4、在win主机上用ipconfig查看VMnet8的IP地址，   
一般是192.168.X.1/255.255.255.0,   
此时VMnet8的设置应该是自动获取IP，现在改成静态IP，并把此IP直接填入VMnet8里，不设网关。

5、同时在VM网络设置里的NAT项中查看VMnet8，一般是192.168.X.2/255.255.255.0   
这个地址就是VMnet8，NAT的网关

6、现在在LINUX下把网卡IP设置成和VMnet8一个网段的IP（192.168.X.Z/255.255.255.0)

7、网关设置成刚才查看的那个IP192.168.X.2即可

8、DNS和你host主机的一样就可以。

9、设置完成后，重新启动linux的网络服务。

10、测试一下,   
ping 网关：ping 192.168.X.2   
ping DNS：ping 你的DNS。

如果能ping通就ok了

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [VMWare虚拟机下的RedHat上网视频](http://www.beansoft.biz/2010/12/04/vmware%e8%99%9a%e6%8b%9f%e6%9c%ba%e4%b8%8b%e7%9a%84redhat%e4%b8%8a%e7%bd%91%e8%a7%86%e9%a2%91/)