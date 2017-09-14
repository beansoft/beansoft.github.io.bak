---
id: 1602
title: NoMachine远程桌面工具真给力!低速网络首选!
date: 2011-01-18T17:37:10+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1602
permalink: '/2011/01/18/nomachine%e8%bf%9c%e7%a8%8b%e6%a1%8c%e9%9d%a2%e5%b7%a5%e5%85%b7%e7%9c%9f%e7%bb%99%e5%8a%9b%e4%bd%8e%e9%80%9f%e7%bd%91%e7%bb%9c%e9%a6%96%e9%80%89/'
views:
  - "903"
original_post_id:
  - "1602"
categories:
  - Linux/Unix
---
NoMachine NX 是一个快速的终端服务器和虚拟桌面软件，基于 X11 协议, 有免费版本。据说速度比 VNC 还快，甚至可以在只有 10k 的带宽环境下运行。笔者今天亲身体验到NoMachine的威力, 速度远胜于VNC, 因为要操作远在国外的服务器, 的确非常快速. 而且画面也比VNC 的清楚。NoMachine 官网地址：<http://www.nomachine.com/>

使用NoMachine 需要配置服务端和客户端。服务端只支持Linux和Solairs, 桌面环境则支持CDE,KDE, GNOME, XDM等, 客户端支持Windows, Linux, Mac OSX, Solaris, 分辨率则可支持自定义的任意大小.

安装包位于<http://www.nomachine.com/select-package.php?os=linux&id=1>, 下文以32位为例说明, 在Oracle Unbreakable Linux 4 下(兼容RedHat Enterprise Linux 4)下操作:

wget http://64.34.161.181/download/3.4.0/Linux/nxclient-3.4.0-7.i386.rpm

wget http://64.34.161.181/download/3.4.0/Linux/nxnode-3.4.0-14.i386.rpm

wget http://64.34.161.181/download/3.4.0/Linux/FE/nxserver-3.4.0-14.i386.rpm

sudo rpm -i nxclient-3.4.0-7.i386.rpm   
sudo rpm -i nxnode-3.4.0-14.i386.rpm   
sudo rpm -i nxserver-3.4.0-14.i386.rpm 

至此服务器端已经搞定!

客户端安装: <http://www.nomachine.com/download-client-windows.php>

例如Windows下的安装包:

<http://64.34.161.181/download/3.4.0/Windows/nxclient-3.4.0-10.exe>

最后登录即可, 帐号为Linux中的SSH用户帐号, 速度的确NB!

&#160;

相关文章推荐: 

### [瘦客户端那些事 &#8211; NoMachine的秘密](http://www.cnblogs.com/coderzh/archive/2010/10/07/thinclient-secret-of-nomachine.html)

### [远程桌面工具 &#8212; NoMachine](http://blog.csdn.net/tianlesoftware/archive/2010/11/11/6003610.aspx)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [NoMachine远程桌面工具真给力!低速网络首选!](http://www.beansoft.biz/2011/01/18/nomachine%e8%bf%9c%e7%a8%8b%e6%a1%8c%e9%9d%a2%e5%b7%a5%e5%85%b7%e7%9c%9f%e7%bb%99%e5%8a%9b%e4%bd%8e%e9%80%9f%e7%bd%91%e7%bb%9c%e9%a6%96%e9%80%89/)