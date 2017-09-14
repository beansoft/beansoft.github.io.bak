---
id: 61
title: WebLogic JDBC 驱动的配置
date: 2009-11-09T10:15:00+00:00
author: 刘长炯
layout: post
guid: http://www.blogjava.net/beansoft/archive/2009/11/09/301658.html
permalink: '/2009/11/09/weblogic-jdbc-%e9%a9%b1%e5%8a%a8%e7%9a%84%e9%85%8d%e7%bd%ae/'
views:
  - "3334"
original_post_id:
  - "61"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
问: weblogic 有自带的哪些数据库的驱动程序吗？

答: C:beawlserver_10.0serverext 下有

默认只有Oracle和mysql, sqlserver的

其它驱动 可以扔到目录里

C:beawlserver_10.0serverlib

这是全局的

另外

C:beauser\_projectsdomainsbase\_domainlib

这是每个domain下的共享目录

如果是weblogic 8 对不起 只能手工改启动脚本了 加到 classpath 里

.. oracle 安装目录下 都有一个 jdbc 目录

驱动包classes12.jar用于JDK 1.2和JDK 1.3，而ojdbc14.jar用于JDK 1.4及以上

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic JDBC 驱动的配置](http://www.beansoft.biz/2009/11/09/weblogic-jdbc-%e9%a9%b1%e5%8a%a8%e7%9a%84%e9%85%8d%e7%bd%ae/)