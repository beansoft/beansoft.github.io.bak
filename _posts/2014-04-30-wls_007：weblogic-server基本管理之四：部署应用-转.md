---
id: 3641
title: 'WLS_007：WebLogic Server基本管理之四：部署应用 [转]'
date: 2014-04-30T18:01:29+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3641
permalink: '/2014/04/30/wls_007%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e5%9b%9b%ef%bc%9a%e9%83%a8%e7%bd%b2%e5%ba%94%e7%94%a8-%e8%bd%ac/'
views:
  - "3335"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: [http://maping930883.blogspot.jp/2009/03/wls007weblogic-server.html](http://maping930883.blogspot.jp/2009/03/wls007weblogic-server.html "http://maping930883.blogspot.jp/2009/03/wls007weblogic-server.html")

WebLogic Server版本：10.3.5。   
**1. 发布应用**   
[domain_name]->Deployments   
重点步骤参数说明：   
**1.1 Choose targeting style**   
（1）Install this deployment as an application   
（2）Install this deployment as a library   
**1.2 Select deployment targets**   
选择要Deploy到哪个Server上。   
**1.3 Security**   
What security model do you want to use with this application?   
（1）DD Only: Use only roles and policies that are defined in the deployment descriptors.   
用户的安全角色与安全策略全部定义在DD中，也就是说只定义在web.xml和weblogic.xml中。   
此时，只根据DD中的配置来执行安全策略，不管Administration Console中是如何定义的。   
（2）Custom Roles: Use roles that are defined in the Administration Console; use policies that are defined in the deployment descriptor.   
用户的安全角色定义在Administration Console中，安全策略全部定义在DD中。   
（3）Custom Roles and Policies: Use only roles and policies that are defined in the Administration Console.   
用户的安全角色与安全策略全部定义在Administration Console中。   
此时，只根据Administration Console中的配置来执行安全角色和安全策略，不管DD（web.xml和weblogic.xml）中是如何定义的。   
（4）Advanced: Use a custom model that you have configured on the realm&#8217;s configuration page.   
**1.4 Source accessibility**   
How should the source files be made accessible?   
（1）Use the defaults defined by the deployment&#8217;s targets   
（2）Copy this application onto every target for me   
（3）I will make the deployment accessible from the following location   
**2. 启动Managed Server，启动应用**   
（1）启动Managed Server：：\[domain\_name]\bin\startManagedWebLogic.cmd [server\_name\] \[admin_url\]   
例如：startManagedWebLogic.cmd dizzy1 http://127.0.0.1:7001   
（2）选择应用，点击 Start -> Servicing All Requests 或 Start -> Servicing only administration requests。   
**3. 测试应用**   
点击benefits应用，选择Testing Tab，点击应用的入口URL：http://localhost:7003/benefits。   
[<img border="0" alt="" src="http://1.bp.blogspot.com/-NBY6-Rqcs90/TtoG7m5eI5I/AAAAAAAACPc/_pp85MKlQf4/s400/1.GIF" />](http://1.bp.blogspot.com/-NBY6-Rqcs90/TtoG7m5eI5I/AAAAAAAACPc/_pp85MKlQf4/s1600/1.GIF)   
如果你想把benefits应用作为默认应用，修改\WEB-INF\weblogic.xml文件：   
<weblogic-web-app>   
<context-root>/</context-root>   
</weblogic-web-app>   
这样访问http://localhost:7003/时，就会直接显示出该应用的页面，不需要输入应用的路径。   
Project 下载：[1. benefits.war](http://java-never-die.googlecode.com/files/benefits.war) [2. benefits\_as\_default.war](http://java-never-die.googlecode.com/files/benefits_as_default.war)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_007：WebLogic Server基本管理之四：部署应用 [转]](http://www.beansoft.biz/2014/04/30/wls_007%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e5%9b%9b%ef%bc%9a%e9%83%a8%e7%bd%b2%e5%ba%94%e7%94%a8-%e8%bd%ac/)