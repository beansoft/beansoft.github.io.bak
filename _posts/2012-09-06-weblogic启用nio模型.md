---
id: 3027
title: WebLogic启用NIO模型
date: 2012-09-06T21:07:16+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3027
permalink: '/2012/09/06/weblogic%e5%90%af%e7%94%a8nio%e6%a8%a1%e5%9e%8b/'
views:
  - "5030"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Muxer
  - WebLogic
---
JDK 1.4之后引入了NIO（非阻塞的New IO），而WebLogic默认则会自动选择本地代码IO（Native IO）或Java IO。可通过如下参数指定您想使用的Muxer实现为NIO：

-Dweblogic.MuxerClass=weblogic.socket.NIOSocketMuxer

注意这样做可能会有风险存在。

下图显示了几种WebLogic中的Muxer实现类：

<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2012/09/image.png" width="209" height="150" />

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic启用NIO模型](http://www.beansoft.biz/2012/09/06/weblogic%e5%90%af%e7%94%a8nio%e6%a8%a1%e5%9e%8b/)