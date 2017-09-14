---
id: 653
title: Where to download file wlfullclient.jar?
date: 2010-08-31T19:15:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=653
permalink: /2010/08/31/where-to-download-file-wlfullclient-jar/
views:
  - "18236"
original_post_id:
  - "653"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
As from WebLogic 10.0, the weblogic.jar is no more hold all files needed by the weblogic client, these apps include: using JNDI to visit data source, to visit ejb, etc. Many articles said that we should use a file called wlfullclient.jar, but how can I get this jar? You&#8217;d better take a look at this article:

<http://download.oracle.com/docs/cd/E11035_01/wls100/client/jarbuilder.html>

For WebLogic 10.3, you can simple run this command:

> java -jar C:\bea\wlserver_10.3\server\lib\wljarbuilder.jar
> 
> then the file is out there.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Where to download file wlfullclient.jar?](http://www.beansoft.biz/2010/08/31/where-to-download-file-wlfullclient-jar/)