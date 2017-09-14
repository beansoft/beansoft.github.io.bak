---
id: 2196
title: WEBLOGIC JMS 点对点配置详解
date: 2011-08-26T22:14:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2196
permalink: '/2011/08/26/weblogic-jms-%e7%82%b9%e5%af%b9%e7%82%b9%e9%85%8d%e7%bd%ae%e8%af%a6%e8%a7%a3/'
views:
  - "5425"
original_post_id:
  - "2196"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - JMS
  - WebLogic
---
作者: BeanSoft

来源: [WebLogic中文博客](http://www.beansoft.biz/)

日期: 2011-8

本文将会展示如何简单的通过队列实现WebLogic JMS 点对点功能.

#### JMS概念简介

JMS 支持两种消息模式: **point-to-point (PTP,****点对点)** 和 **publish/subscribe (pub/sub,** **发布/订阅)**. 这些消息模式非常类似, 主要区别简列如下:

  * 点对点消息模式有且只能有一个收件人收到传送的消息.
  * 发布/订阅模式可以将一条消息传送到多个收件人.

点对点消息模式可以使一个应用程序向另一个发送消息. 点对点消息应用通过使用**Queues(****队列)** 来发送和接收消息. 队列发送者 (producer,生产者) 向指定的队列发送消息. 队列接收者 (consumer,消费者) 从指定的队列接收消息.

&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;

下载本文(右键另存为): <a href="http://www.beansoft.biz/wp-content/uploads/2011/08/jms.swf" target="_blank">http://www.beansoft.biz/wp-content/uploads/2011/08/jms.swf</a> 613KB

提示: 点击最右上角的 **回** 按钮全屏阅读 

<http://www.beansoft.biz/wp-content/uploads/2011/08/jms.swf>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WEBLOGIC JMS 点对点配置详解](http://www.beansoft.biz/2011/08/26/weblogic-jms-%e7%82%b9%e5%af%b9%e7%82%b9%e9%85%8d%e7%bd%ae%e8%af%a6%e8%a7%a3/)