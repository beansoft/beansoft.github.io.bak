---
id: 2989
title: '[转]Configure Apache Webserver with Weblogic Server'
date: 2012-07-26T19:06:00+00:00
author: 刘长炯
layout: post
guid: http://weblogic.clawz.com/?p=2989
permalink: '/2012/07/26/%e8%bd%acconfigure-apache-webserver-with-weblogic-server/'
views:
  - "2463"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Apache
  - WebLogic
---
**From: <http://weblogic-wonders.com/weblogic/2010/12/11/configure-apache-webserver-with-weblogic-server/>** 

**Step 1)** Make sure the Apache server runs on port 8080.( This is because sometimes IIS, or some antivirus s/w runs on that port).This can be done by modifying the httpd.conf present at   
D:\Program Files\Apache Group\Apache2\conf   
Modify the Listen port to 8080

Listen 8080

**Step 2)** Copy the mod\_wl\_20.so from <bea\_home>\wlserver\_10.3\server\plugin\win\32 to   
D:\Program Files\Apache Group\Apache2\modules

**Step 3)** Add these lines in the httpd.conf file

LoadModule weblogic\_module modules/mod\_wl_20.so

<Location />   
SetHandler weblogic-handler   
</Location>

<IfModule mod_weblogic.c>   
WebLogicCluster localhost:7003,localhost:7005   
Debug ON   
WLLogFile c:/temp/wlproxy.log   
WLTempDir c:/temp   
</IfModule>

**Step 4)** Restart Apache and access the application deployed on the Cluster using

http://localhost:8080/YourApp

This will forward the request to the Weblogic Cluster

You can check the headers sent and received to WLS in wlproxy.log file.

Let me know if you face any issues.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [[转]Configure Apache Webserver with Weblogic Server](http://www.beansoft.biz/2012/07/26/%e8%bd%acconfigure-apache-webserver-with-weblogic-server/)