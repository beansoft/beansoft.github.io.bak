---
id: 122
title: WebLogic 11g 如何修改 Console 的端口
date: 2010-04-23T22:10:55+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=122
permalink: '/2010/04/23/weblogic-11g-%e5%a6%82%e4%bd%95%e4%bf%ae%e6%94%b9-console-%e7%9a%84%e7%ab%af%e5%8f%a3/'
views:
  - "5492"
original_post_id:
  - "122"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
这个问题很简单, 乍看上去是需要修改 Console 的端口, 实际上是需要修改 AdminServer的端口.

可编辑 C:beauser_projectsdomainsmydomain(您自己的domain)configconfig.xml 来修改其端口, 如下所示:

&#160; <server>   
&#160;&#160;&#160; <name>AdminServer</name>   
&#160;&#160;&#160; **<listen-port>8888</listen-port>**   
&#160;&#160;&#160; <listen-address>192.168.0.4</listen-address>   
&#160; </server> 

另外, 通过 Configuration Wizard 创建新的 Domain 时, 也可以修改Admin Server的端口, 不过, 需要打开如下提示才可: 

[<img style="display:inline;border-width:0;" title="1L240EXL}7ZFA]TE}MRP~QG" border="0" alt="1L240EXL}7ZFA]TE}MRP~QG" src="http://www.beansoft.biz/wp-content/uploads/2010/04/1l240exl7zfatemrpqg_thumb.jpg" width="105" height="37" />](http://www.beansoft.biz/wp-content/uploads/2010/04/1l240exl7zfatemrpqg.jpg) 

然后可看到如下修改界面:

<img style="display:inline;border-width:0;" title="clip_image002" border="0" alt="clip_image002" src="http://www.beansoft.biz/wp-content/uploads/2010/04/clip_image002.jpg" width="553" height="395" />

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic 11g 如何修改 Console 的端口](http://www.beansoft.biz/2010/04/23/weblogic-11g-%e5%a6%82%e4%bd%95%e4%bf%ae%e6%94%b9-console-%e7%9a%84%e7%ab%af%e5%8f%a3/)