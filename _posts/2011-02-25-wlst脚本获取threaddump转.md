---
id: 1788
title: 'WLST脚本获取ThreadDump[转]'
date: 2011-02-25T12:20:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1788
permalink: '/2011/02/25/wlst%e8%84%9a%e6%9c%ac%e8%8e%b7%e5%8f%96threaddump%e8%bd%ac/'
views:
  - "4059"
original_post_id:
  - "1788"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
  - 转载区
---
</p> 

**来源: <http://weixd.net/?p=6> 作者: wei**

**1. 创建WLST脚本:Threaddump.py**

<pre>serverName = 'AdminServer'
counter = 0
sleepTime = 5000&#160;&#160; #Threaddump时间间隔是5秒

connect ('weblogic','weblogic','t3://localhost:7001')

for counter in range(3):&#160; #做3个Threaddump
java.lang.Thread.sleep(sleepTime)
fileName = 'dump' + serverName + '_' + (java.util.Calendar.getInstance().getTimeInMillis()).toString() + '.dmp'&#160; #Threaddump文件名
threadDump('true', fileName, serverName)</pre>

**2. 调用脚本**

<pre>java weblogic.WLST ThreadDumps.py</pre>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLST脚本获取ThreadDump[转]](http://www.beansoft.biz/2011/02/25/wlst%e8%84%9a%e6%9c%ac%e8%8e%b7%e5%8f%96threaddump%e8%bd%ac/)