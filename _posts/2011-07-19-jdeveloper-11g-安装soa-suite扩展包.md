---
id: 2073
title: JDeveloper 11g 安装SOA Suite扩展包
date: 2011-07-19T20:03:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2073
permalink: '/2011/07/19/jdeveloper-11g-%e5%ae%89%e8%a3%85soa-suite%e6%89%a9%e5%b1%95%e5%8c%85/'
views:
  - "8250"
original_post_id:
  - "2073"
categories:
  - SOA/WebService
---
作者: 刘长炯(<BeanSoft@126.com>)

Oracle JDeveloper 11.1.1.5.0默认安装后并不附带有SOA Suite扩展包, 因此如果需要进行SOA相关的开发就需要安装此扩展包. 本文将涵盖下列内容: 在线安装; 离线安装.

1. 在线安装

第一种安装方式是启动后, 通过在线更新来完成进行. 菜单项选择: **<font face="Arial">Help | Check for updates</font>**, 点击 **<font face="Arial">Next</font>**, 然后选择 **Oracle Fusion Middleware Products,** 可过滤列表快速选中 **Oracle SOA Composite Editor** , 点击**Next**后进行下载安装, 最后按照提示进行重启即可.

[<img title="-2011-07-19_104708" style="display:inline;border-width:0;" height="480" alt="-2011-07-19_104708" src="http://www.beansoft.biz/wp-content/uploads/2011/07/20110719_104708_thumb.png" width="640" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/07/20110719_104708.png) 

 <img title="2011-07-15 14 39 27" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="657" alt="2011-07-15 14 39 27" src="http://www.beansoft.biz/wp-content/uploads/2011/07/20110715143927.png" width="655" border="0" />

 <img title="2011-07-15 14 39 35" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="146" alt="2011-07-15 14 39 35" src="http://www.beansoft.biz/wp-content/uploads/2011/07/20110715143935.png" width="396" border="0" />

2. 离线安装

然而在离线状态下, 就无法更新了, 此时可通过先下载扩展包, 保存后在本地更新的方式进行. 首先访问 [Oracle Fusion Middleware Extensions](http://www.oracle.com/ocom/groups/public/@otn/documents/webcontent/156082.xml), 然后找到SOA相关扩展包, 注意版本号要对应. 例如直接下载地址为: [http://download-llnw.oracle.com/otn-pub/jdeveloper/11.1.1.5.0/extensions/soa-jdev-extension.zip](http://download-llnw.oracle.com/otn-pub/jdeveloper/11.1.1.5.0/extensions/soa-jdev-extension.zip "http://download-llnw.oracle.com/otn-pub/jdeveloper/11.1.1.5.0/extensions/soa-jdev-extension.zip"), 安装包约为193MB. 之后, 依然通过Update菜单进行更新, 只需要修改第二屏选择本地的安装包:

<img title="image" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="480" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/07/image6.png" width="640" border="0" />

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JDeveloper 11g 安装SOA Suite扩展包](http://www.beansoft.biz/2011/07/19/jdeveloper-11g-%e5%ae%89%e8%a3%85soa-suite%e6%89%a9%e5%b1%95%e5%8c%85/)