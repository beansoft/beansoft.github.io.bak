---
id: 425
title: Oracle SOA Suite 11g环境搭建手册(一)及视频(转载)
date: 2010-07-22T22:45:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=425
permalink: '/2010/07/22/oracle-soa-suite-11g%e7%8e%af%e5%a2%83%e6%90%ad%e5%bb%ba%e6%89%8b%e5%86%8c%e4%b8%80/'
views:
  - "5085"
original_post_id:
  - "425"
categories:
  - SOA/WebService
tags:
  - Oracle
  - SOA/WebService
---
[Oracle SOA Suite 11g环境搭建手册(一).pdf](https://skydrive.live.com/redir.aspx?cid=519b3f7aa2172030&resid=519B3F7AA2172030!1461&parid=519B3F7AA2172030!1459)

相关视频: [http://www.itjaj.com/v/liujin/ORACLE\_SOA\_SUITE\_11G\_INSTALL\_GUIDE1/ORACLE\_SOA\_SUITE\_11G\_INSTALL\_GUIDE1.html](http://www.itjaj.com/v/liujin/ORACLE_SOA_SUITE_11G_INSTALL_GUIDE1/ORACLE_SOA_SUITE_11G_INSTALL_GUIDE1.html "http://www.itjaj.com/v/liujin/ORACLE_SOA_SUITE_11G_INSTALL_GUIDE1/ORACLE_SOA_SUITE_11G_INSTALL_GUIDE1.html")

版权归原作者liu.jin所有.

  * 转载自: [http://www.itjaj.com/thread-4341-1-1.html](http://www.itjaj.com/thread-4341-1-1.html "http://www.itjaj.com/thread-4341-1-1.html")

内容目录   
文档控制 ii   
1. 前期准备 2   
1.1. 硬件平台 2   
1.2. 软件平台 2   
2. 详细实施步骤 3   
2.1. Oracle数据库11g安装 3   
2.2. RCU(Repository Creation Utility)安装 16   
2.3. WebLogic 11g安装 22   
2.4. Oracle SOA Suite 11g安装及配置 27   
2.5. 环境搭建注意事项 39   
3. 未结与已结问题 41   
未结问题 41   
已结问题 41

  * 前期准备   
    本文讲述了在Windows平台上搭建Oracle Fusion Middleware 11g中的Oracle SOA Suite 11g系统，下面列出了软硬件前提。   
    安装Oracle SOA Suite 11g需要先安装以下Oracle产品： 
      * Oracle Database 11.1.0.7
      * Oracle WebLogic Server 10.3.1
      * Repository Creation Utility (RCU)
      * Oracle SOA Suite 11g

  * 硬件平台   
    安装以上产品至少需要物理内存1G，硬盘20G空间   
    为了保证运行的稳定，至少2G物理内存。

  * 软件平台   
    Windows平台，包括Windows XP，Windows 2003，Windows 2008。

  * 详细实施步骤   
    安装Oracle SOA Suite 11g之前需要安装Oracle Database 11g，该数据库做为控制数据库。后面讲到的RCU也是需要安装到该控制数据库。   
    下面依次介绍安装Oracle SOA Suite 11g所需要的产品。

  * Oracle数据库11g安装   
    到Oracle产品中心下载Oracle DataBase 11g

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Oracle SOA Suite 11g环境搭建手册(一)及视频(转载)](http://www.beansoft.biz/2010/07/22/oracle-soa-suite-11g%e7%8e%af%e5%a2%83%e6%90%ad%e5%bb%ba%e6%89%8b%e5%86%8c%e4%b8%80/)