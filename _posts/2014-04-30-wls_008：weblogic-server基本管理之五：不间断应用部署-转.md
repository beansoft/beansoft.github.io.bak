---
id: 3643
title: 'WLS_008：WebLogic Server基本管理之五：不间断应用部署 [转]'
date: 2014-04-30T18:03:31+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3643
permalink: '/2014/04/30/wls_008%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%ba%94%ef%bc%9a%e4%b8%8d%e9%97%b4%e6%96%ad%e5%ba%94%e7%94%a8%e9%83%a8%e7%bd%b2-%e8%bd%ac/'
views:
  - "5202"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: [http://maping930883.blogspot.jp/2009/03/wls008weblogic-server.html](http://maping930883.blogspot.jp/2009/03/wls008weblogic-server.html "http://maping930883.blogspot.jp/2009/03/wls008weblogic-server.html")&#160;

WebLogic Server版本：10.3.5。   
在生产环境中，一些重要的应用要求7&#215;24小时运行，如何升级这些正在运行的应用是一个让人头疼的问题。   
Weblogic Server能够在不停止现有应用的情况下部署新版本。   
这时，如果还有用户访问旧版本应用，那么可以继续访问；新来的用户将访问新版本的应用。   
所有旧版本的用户访问完毕后，旧版本应用将自动“退休”。   
[<img border="0" alt="" src="http://2.bp.blogspot.com/-8KvwDf3UBwE/TtoVS2Ny-GI/AAAAAAAACQY/EitFSszGeng/s400/1.GIF" />](http://2.bp.blogspot.com/-8KvwDf3UBwE/TtoVS2Ny-GI/AAAAAAAACQY/EitFSszGeng/s1600/1.GIF)   
**1. 使用java weblogic.Deployer 实现不间断应用部署**   
注意：使用此种方式实现不间断应用部署，要求应用第1次部署时也使用此种方式。   
否则，如果第1次使用Console部署，第2次使用此种方式，将会报告如下错误：   
You cannot deploy application, &#8216;benefits&#8217;, with version &#8216;v2&#8217;. The application was previously deployed without version.   
（1）第1次发布 benefits应用，版本号：v1   
运行如下命令之前，先运行[domain_name]\bin\setDomainEnv.cmd设置运行环境。   
java weblogic.Deployer -adminurl t3://localhost:7001 -user weblogic -password welcome1 -deploy -name benefits -source benefits.war -targets dizzy1 -appversion v1   
[<img border="0" alt="" src="http://1.bp.blogspot.com/-e8GG-I3pUzg/TtoVSVt_P0I/AAAAAAAACQQ/lOWXI-CmGck/s400/2.GIF" />](http://1.bp.blogspot.com/-e8GG-I3pUzg/TtoVSVt_P0I/AAAAAAAACQQ/lOWXI-CmGck/s1600/2.GIF)   
访问效果如下图（列表是黄颜色的背景）：   
[<img border="0" alt="" src="http://3.bp.blogspot.com/-rM7rbNT3IYg/TtoVSJhKI_I/AAAAAAAACP8/5K_YDr1LpQI/s400/3.GIF" />](http://3.bp.blogspot.com/-rM7rbNT3IYg/TtoVSJhKI_I/AAAAAAAACP8/5K_YDr1LpQI/s1600/3.GIF)   
（2）第2次发布 benefits应用，版本号：v2   
与第1个版本的benefits应用相比，只是把welcome.html中的table的background从yellow改成了green。   
java weblogic.Deployer -adminurl t3://localhost:7001 -user weblogic -password welcome1 -redeploy -name benefits -source benefits.war -targets dizzy1 -appversion v2   
注意，版本v2发布成功后，版本v1就自动“退休”了。   
[<img border="0" alt="" src="http://3.bp.blogspot.com/-XI6lOxWKzT0/TtoVR2tXyUI/AAAAAAAACP0/cEKVp1pEWQs/s400/4.GIF" />](http://3.bp.blogspot.com/-XI6lOxWKzT0/TtoVR2tXyUI/AAAAAAAACP0/cEKVp1pEWQs/s1600/4.GIF)   
访问效果如下图（列表是绿颜色的背景）：   
[<img border="0" alt="" src="http://3.bp.blogspot.com/-LKUWonqvfUs/TtoVR6d7mEI/AAAAAAAACPo/YWgrABUXseo/s400/5.GIF" />](http://3.bp.blogspot.com/-LKUWonqvfUs/TtoVR6d7mEI/AAAAAAAACPo/YWgrABUXseo/s1600/5.GIF)   
（3）如果发现新发布的应用有问题，可以“切换”回旧应用   
java weblogic.Deployer -adminurl t3://localhost:7001 -user weblogic -password welcome1 -redeploy -name benefits -source benefits.war -targets dizzy1 -appversion v1   
[<img border="0" alt="" src="http://2.bp.blogspot.com/-9tzavhojshM/Ttotq0Eed7I/AAAAAAAACQk/AnBKp3-TbCY/s400/6.GIF" />](http://2.bp.blogspot.com/-9tzavhojshM/Ttotq0Eed7I/AAAAAAAACQk/AnBKp3-TbCY/s1600/6.GIF)   
**2. 在META-INF\MANIFEST.MF文件中指定版本**   
除了使用java weblogic.Deployer在-appversion中指定版本外，你还可以在META-INF\MANIFEST.MF文件中指定版本。   
设置Weblogic-Application-Version的值，举例如下：   
Manifest-Version: 1.0   
Created-By: 1.5.0_03 (Sun Microsystems Inc.)   
Weblogic-Application-Version: v1   
你可以通过Console发布应用的第1个版本，然后使用java weblogic.Deployer发布更新版本。   
参考文献：   
1. http://bbs.rsky.com.cn/TopicOther.asp?t=5&BoardID=22&id=4785   
2. http://docs.oracle.com/cd/E13222_01/wls/docs90/programming/versioning.html 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_008：WebLogic Server基本管理之五：不间断应用部署 [转]](http://www.beansoft.biz/2014/04/30/wls_008%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%ba%94%ef%bc%9a%e4%b8%8d%e9%97%b4%e6%96%ad%e5%ba%94%e7%94%a8%e9%83%a8%e7%bd%b2-%e8%bd%ac/)