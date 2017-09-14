---
id: 2994
title: 入门:选择正确的安装包来安装Oracle Weblogic Server
date: 2012-07-15T20:18:00+00:00
author: 刘长炯
layout: post
guid: http://weblogic.clawz.com/?p=2994
permalink: '/2012/07/15/%e5%85%a5%e9%97%a8%e9%80%89%e6%8b%a9%e6%ad%a3%e7%a1%ae%e7%9a%84%e5%ae%89%e8%a3%85%e5%8c%85%e6%9d%a5%e5%ae%89%e8%a3%85oracle-weblogic-server/'
views:
  - "4355"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Install
  - WebLogic
---
###### Selecting the correct installer to install Oracle Weblogic Server

来源: [https://blogs.oracle.com/WeblogicConfigurations/entry/selecting\_the\_correct\_installer\_to](https://blogs.oracle.com/WeblogicConfigurations/entry/selecting_the_correct_installer_to)

###### By PratikS &#8212; Oracle on [Jun 29, 2012](https://blogs.oracle.com/WeblogicConfigurations/entry/selecting_the_correct_installer_to#)

当我们开始学习一个软件的时候, 第一件事就是拿到安装包然后安装好程序.

在我们开始问 "如何安装 Oracle Weblogic Server?", 让我们首先了解Oracle Weblogic Server各种不同的安装包并选择合适的安装包.   
目前有三种不同的WebLogic安装包:

  1. 完整安装包

  2. 开发人员版及支持安装包

  3. 升级安装包

**1) 完整安装包:   
** 如果您从未安装过Oracle Weblogic Server, 并且是初次尝试安装, 推荐您使用完整安装包.   
不过需要注意的是一共有两种完整安装包, 试列举如下:   
a) 通用完整安装包:

  * 不包含Java虚拟机. (使用此安装包之前必须下载并安装匹配版本的JDK)

  * 如果想在**64位 Java虚拟机上安装WebLogic, 那么必须使用**此"通用完整安装包",包含所有32或64位的WebLogic本地库文件.

  * "通用完整安装包" 不依赖于特定的平台, 并且可用来安装到任何受支持的32位或64位系统上,如AIX,zLinux,HP UX等.

b) 操作系统特定的完整安装包

  * 如名称所示安装包是针对特定操作系统的.

  * **只附带有32位JDK**及相应的WebLogic本地库.

  * 同时捆绑了 SUN 和 JROCKIT 32 位 JDK, 所以安装时无需单独下载JDK.

**2) 开发专用及相关支持包:**

  * 如果不需要在生产机上使用Oracle Weblogic Server , 只想用来做项目开发, 不需要很大的完整安装包, 则可使用此安装包.

  * 下载ZIP压缩包, 解压缩即可使用.

**3) 升级安装包:**

  * 升级安装包可用来将WebLogic从一个小版本升级到更高的另一个小版本.

  * 目前没有主版本间的升级包, 虽然域升级向导在每个版本都提供.

备注:   
下面是升序排列的不同版本的 Oracle Weblogic Server (不包含低于WLS 9.2的老版本):

  * WLS 9.2.x

  * WLS 10.0.x

  * WLS 10.3.x

  * WLS 12.1.x

字母"x" 表示小版本, 9.2, 10.0,10.3 和12.1 是主版本号.&#160;   
所以升级安装包可以将 WLS 10.3.1 升级到 10.3.6, 或者10.0.1 升至10.0.2.

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;-

如何下载 Oracle Weblogic Server 安装包的步骤参考文档(英文):

[Downloading the Installer From Oracle E-Delivery](http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/prepare.htm#autoId2)

[Downloading the Installer From Oracle Technology Network](http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/prepare.htm#autoId3)

[Downloading an Upgrade Installer From My Oracle Support](http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/prepare.htm#autoId4) 

参考链接:

  * [Oracle Weblogic Server Documentation](http://www.oracle.com/technetwork/middleware/weblogic/documentation/index.html)

  * [Supported Configuration](http://www.oracle.com/technetwork/middleware/ias/downloads/fusion-certification-100350.html)

  * [Installation Guide for Oracle WebLogic Server](http://docs.oracle.com/cd/E23943_01/doc.1111/e14142/overview.htm#BABIGEFB)

附图:

![weblogic 10.3.4安装说明](/wp-content/uploads/2011/01/weblogic10-3-4.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [入门:选择正确的安装包来安装Oracle Weblogic Server](http://www.beansoft.biz/2012/07/15/%e5%85%a5%e9%97%a8%e9%80%89%e6%8b%a9%e6%ad%a3%e7%a1%ae%e7%9a%84%e5%ae%89%e8%a3%85%e5%8c%85%e6%9d%a5%e5%ae%89%e8%a3%85oracle-weblogic-server/)