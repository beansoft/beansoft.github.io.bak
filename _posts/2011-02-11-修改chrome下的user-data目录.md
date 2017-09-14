---
id: 1702
title: 修改Chrome下的User Data目录默认路径
date: 2011-02-11T20:16:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1702
permalink: '/2011/02/11/%e4%bf%ae%e6%94%b9chrome%e4%b8%8b%e7%9a%84user-data%e7%9b%ae%e5%bd%95/'
views:
  - "6001"
original_post_id:
  - "1702"
tagazine-media:
  - 'a:7:{s:7:"primary";s:0:"";s:6:"images";a:0:{}s:6:"videos";a:0:{}s:11:"image_count";s:1:"0";s:6:"author";s:8:"27534716";s:7:"blog_id";s:8:"27979815";s:9:"mod_stamp";s:19:"2011-02-11 12:16:00";}'
categories:
  - 软件使用与下载
---
如何修改Chrome下的用户数据目录路径呢?

&#160;

Chrome浏览器虽然启动速度超快, 然而其用户数据文件目录却是超大, 对于C盘紧张的朋友来说, 不是个好消息. 而且Chrome奇异的地方是只要是新启动的进程, 只会认识系统盘的那个默认用户数据目录, 这让通过命令行加指定用户目录的企图归于失败.

&#160;

首先, 确保系统盘分区和目标盘分区均为NTFS目录, 然后, 请您下载微软出品的目录符号链接工具Junction(<a href="http://technet.microsoft.com/zh-cn/sysinternals/bb896768.aspx" target="_blank">介绍</a> <a href="http://download.sysinternals.com/Files/Junction.zip" target="_blank">直接下载</a>), 并将其解压缩到D盘下. 下面我将尝试将C盘的Chrome用户目录移动到D盘, 请执行如下命令:

mkdir "D:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome"

将在D盘创建一个Chrome目录, 接着, 将目录

C:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome\User Data

下的文件剪切到D:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome下.

执行命令

junction "C:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome\User Data" "D:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome\User Data"

大功告成. 如果此时打开目录C:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome\User Data, 可以发现竟然有一个User Data目录, 实际上这个目录只是D盘的User Data目录的镜像.

如果想还原, 首先执行

junction -d "C:\Documents and Settings\%USERNAME%\Local Settings\Application Data\Google\Chrome\User Data"

, 然后将数据文件再剪切回去就OK了.

参考第三方详细说明: <http://pheyoung.blogbus.com/logs/73288353.html> 彻底转移chrome的数据文件.

Win7用户请参考命令 mklink.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [修改Chrome下的User Data目录默认路径](http://www.beansoft.biz/2011/02/11/%e4%bf%ae%e6%94%b9chrome%e4%b8%8b%e7%9a%84user-data%e7%9b%ae%e5%bd%95/)