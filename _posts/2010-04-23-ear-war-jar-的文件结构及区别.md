---
id: 114
title: EAR, WAR, JAR 的文件结构及区别
date: 2010-04-23T22:08:49+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=114
permalink: '/2010/04/23/ear-war-jar-%e7%9a%84%e6%96%87%e4%bb%b6%e7%bb%93%e6%9e%84%e5%8f%8a%e5%8c%ba%e5%88%ab/'
views:
  - "7350"
original_post_id:
  - "114"
image: /wp-content/uploads/2012/09/ear2_thumb.png
categories:
  - Java EE
---
问:Weblogic8中 部署新应用程序 .应用程序 EJB 模块&#160;&#160;&#160;&#160; Web 应用程序模块&#160; 连接器模块&#160; ，他们有什么差别啊？ 

&#160;

如果一个应用中有EJB，JSP，SERVLET，其部署步骤如下:   
（1）生成EJB的JAR文件，最好一个JAR文件对应一个EJB   
（2）生成WEB APPLICATION的WAR文件，在web.xml，weblogic.xml中登记，配置SERVLET，JSP等。   
（3）创建一个application.xml文件，设置该应用的属性.把application.xml，\*.JAR， \*.WAR，打包成一个*.EAR   
（4）WebLogic的控制台中登记该应用或把该EAR文件拷到application目录下

&#160;

下面列出了这几种文件的结构

[<img style="display:inline;border-width:0;" title="ear 2" border="0" alt="ear 2" src="http://www.beansoft.biz/wp-content/uploads/2010/04/ear2_thumb.png" width="495" height="298" />](http://www.beansoft.biz/wp-content/uploads/2010/04/ear2.png) 

EAR 文件结构

说明: EAR 文件中的 sun-application.xml是厂商特定的文件, 例如 weblogic.xml, jboss.xml 都可

例如一个典型的EAR文件结构为:

myApp.ear

> myEJB1.jar
> 
> myEJB2.jar
> 
> myWeb.war
> 
> META-INF/application.xml
> 
> myRes.rar

&#160;

&#160;

[<img style="display:inline;border-width:0;" title="ejb" border="0" alt="ejb" src="http://www.beansoft.biz/wp-content/uploads/2010/04/ejb_thumb.png" width="384" height="296" />](http://www.beansoft.biz/wp-content/uploads/2010/04/ejb.png) 

&#160;

EJB 文件结构

说明: sun-ejb-jar.xml 也是特定的, 随服务器种类而变化

&#160;

[<img style="display:inline;border-width:0;" title="web module" border="0" alt="web module" src="http://www.beansoft.biz/wp-content/uploads/2010/04/webmodule_thumb.png" width="456" height="429" />](http://www.beansoft.biz/wp-content/uploads/2010/04/webmodule.png) 

Web 模块文件结构

说明: sun-web.xml 也是特定的, 随服务器种类而变化</p> </p> 

&#160;

其它问题:

再问：mydomain/applications/app1 myserver.wlnotdeleteextractmyserver_app1 后者是前者的缓存? 

&#160;

是的, WebLogic 在生产机模式下只会访问编译后的内容. 只有设置了参数, WLS 才会自动更新编译后的文件.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [EAR, WAR, JAR 的文件结构及区别](http://www.beansoft.biz/2010/04/23/ear-war-jar-%e7%9a%84%e6%96%87%e4%bb%b6%e7%bb%93%e6%9e%84%e5%8f%8a%e5%8c%ba%e5%88%ab/)