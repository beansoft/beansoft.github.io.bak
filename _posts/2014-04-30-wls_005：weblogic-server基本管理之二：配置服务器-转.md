---
id: 3637
title: 'WLS_005：WebLogic Server基本管理之二：配置服务器 [转]'
date: 2014-04-30T17:56:14+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3637
permalink: '/2014/04/30/wls_005%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%ba%8c%ef%bc%9a%e9%85%8d%e7%bd%ae%e6%9c%8d%e5%8a%a1%e5%99%a8-%e8%bd%ac/'
views:
  - "3365"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: [http://maping930883.blogspot.jp/2009/03/wls005weblogic-server_02.html](http://maping930883.blogspot.jp/2009/03/wls005weblogic-server_02.html "http://maping930883.blogspot.jp/2009/03/wls005weblogic-server_02.html")

**1. 启动管理服务器：[domain_name]\startWebLogic.cmd**   
如果在生产模式下，启动时会询问你用户名/口令。   
如果不想输入用户名/口令，可以按照如下方式操作：   
创建一个boot.properties文件，放到[domain\_name]\servers\[server\_name]\security目录下。   
内容为两行：   
username=[username]   
password=[password]   
**2. 启动受管服务器：\[domain\_name]\bin\startManagedWebLogic.cmd [server\_name\] \[admin_url\]**   
例如：startManagedWebLogic.cmd dizzy1 http://127.0.0.1:7001   
其中，127.0.0.1:7001 指向管理服务器的IP地址和端口。   
这里因为AdminServer就在本机，所以使用127.0.0.1:7001。   
如果AdminServer就在本机，可以省略http://127.0.0.1:7001。   
**3. 配置受管服务器**   
[domain_name]->Environment-> Servers：点击New，创建新的Managed Server。   
**4. 配置机器**   
[domain_name]->Environment-> Machines：点击New，创建新的Machine。   
（1）增加受管服务器到机器上。   
点击Machine，选择Servers Tab，点击Add，选择Managed Server。   
（2）配置机器上的节点管理器。   
点击Machine，选择Node Manager Tab，设置Node Manager属性。   
[<img border="0" alt="" src="http://3.bp.blogspot.com/-poUlyxHFecQ/TtisabEDpwI/AAAAAAAACOs/uPRzKvqnBb4/s400/1.GIF" />](http://3.bp.blogspot.com/-poUlyxHFecQ/TtisabEDpwI/AAAAAAAACOs/uPRzKvqnBb4/s1600/1.GIF)   
**5. 通过节点管理器远程启动服务器**   
（1）启动机器上的节点管理器Java进程   
\[wlserver\_10.x]\server\bin\startNodeManager.cmd [ip\_address\] \[port\]   
例如：startNodeManager.cmd 127.0.0.1 5555   
注意，127.0.0.1 5555 是NodeManager所在机器的IP地址和端口。   
因为这里的NodeManager就在本机，所以使用127.0.0.1 5555。   
生产环境中，NodeManager与AdminServer不在同一台机器上。   
（2）使用控制台启动远程启动服务器   
[domain\_name]->Environment-> Servers->[server\_name]->Control->Start/Stop 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_005：WebLogic Server基本管理之二：配置服务器 [转]](http://www.beansoft.biz/2014/04/30/wls_005%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%ba%8c%ef%bc%9a%e9%85%8d%e7%bd%ae%e6%9c%8d%e5%8a%a1%e5%99%a8-%e8%bd%ac/)