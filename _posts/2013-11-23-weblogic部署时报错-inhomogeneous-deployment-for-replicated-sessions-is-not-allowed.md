---
id: 3468
title: 'weblogic部署时报错&#8211;Inhomogeneous deployment for replicated sessions is not allowed'
date: 2013-11-23T22:34:30+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3468
permalink: '/2013/11/23/weblogic%e9%83%a8%e7%bd%b2%e6%97%b6%e6%8a%a5%e9%94%99-inhomogeneous-deployment-for-replicated-sessions-is-not-allowed/'
views:
  - "7548"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - WebLogic
  - 部署
---
一个集群里有N>3台受管服务器，将项目部署在所有集群中的所有服务器能成功正常运行，但部署在集群的一部分（比如其中一到三台）出现了[HTTP Session:100083]，Inhomogeneous deployment for replicated sessions is not allowed. 的错误.

激活更改期间出错, 有关详细信息, 请查看日志。

Failed to load webapp: &#8216;xxx.war&#8217;

[HTTP Session:100083]The webapp: xxx.war in application: am has PersistenceStoreType set to: replicated for http sessions, but the target list does not contain all members of cluster: Cluster-1. Inhomogeneous deployment for replicated sessions is not allowed.

原因：

应用war包的weblogic.xml添加了

<session-descriptor>   
<persistent-store-type>replicated</persistent-store-type>   
<sharing-enabled>true</sharing-enabled>   
</session-descriptor>

或者

<session-descriptor>

<persistent-store-type>replicated\_if\_clustered</persistent-store-type>   
</session-descriptor>

代码的意思是如果有集群则session复制，但是问题是它会复制到集群下的所有server上，如果你的应用没有部署到集群的所有server上，只是集群下的部分server上，这时就会报此错误。实际上是，它在该集群下的其他server上找不到你的应用。

解决办法：

将应用部署到集群下的所有server上，或者该集群下只放部署该应用的server不放其他server。

&#160;

参考资料:

[http://blog.sina.com.cn/s/blog_656977f401019nrd.html](http://blog.sina.com.cn/s/blog_656977f401019nrd.html "http://blog.sina.com.cn/s/blog_656977f401019nrd.html")&#160;

[https://forums.oracle.com/thread/2139175?start=0](https://forums.oracle.com/thread/2139175?start=0 "https://forums.oracle.com/thread/2139175?start=0")

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [weblogic部署时报错&#8211;Inhomogeneous deployment for replicated sessions is not allowed](http://www.beansoft.biz/2013/11/23/weblogic%e9%83%a8%e7%bd%b2%e6%97%b6%e6%8a%a5%e9%94%99-inhomogeneous-deployment-for-replicated-sessions-is-not-allowed/)