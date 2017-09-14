---
id: 294
title: Weblogic 8和MyEclipse 5.5 整合 Web 开发
date: 2008-06-04T23:57:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=294
permalink: '/2008/06/04/weblogic-8%e5%92%8cmyeclipse-5-5-%e6%95%b4%e5%90%88-web-%e5%bc%80%e5%8f%91/'
views:
  - "3890"
original_post_id:
  - "294"
image: /wp-content/uploads/2012/09/clip_image002_thumb1.jpg
categories:
  - MyEclipse/Eclipse
---
Weblogic 8和MyEclipse 5.5 整合 Web 开发 

本文为原创作品，转载请注明作者：BeanSoft（刘长炯）和出处。 

启动WebLogic: 

[<img height="214" alt="clip_image002" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image002_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image002.jpg) 

Server 服务器是通用组件 

Domain 域, 是一组Weblogic的服务器实例,配置信息以及发布的应用的组合,可以有多个. 多个Domain的监听端口不能相同. 通过 Configuration Wizard 来修改或者创建Domain. 

Weblogic的不同版本支持的JSP版本,以及配套的JDK都不同,不能互相更改. 

Domain 目录（不同操作系统上是一致的） 

Config.xml 配置了服务器的信息，相当于Tomcat的conf/server.xml，可以修改里面的监听端口： 

<Server ListenAddress="" ListenPort="7001" Name="myserver" 

Applications等价于Tomcat的webapps。 

startWebLogic.cmd 启动脚本 

stopWebLogic.cmd 关闭脚本 

[<img height="518" alt="clip_image004" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image004_thumb.jpg" width="345" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image004.jpg) 

Weblogic 8 支持的 Servlet 2.3 和 JSP 1.2, 不支持 EL 表达式, 只能用 JDK 1.4 来启动, 写的程序不能使用 Java 5 的泛型等功能. 必需修改开发工具的编译器等级为1.4. Weblogic 9 支持 J2EE 1.4和 JDK 1.5；Weblogic 10支持最新的Java EE 5和 JDK 1.5:JSF（Java ServerFace），JPA（Java Persistence API，Java持久性API），标注式开发。Weblogic是商业软件，个人使用，学习和开发免费，但是最多只能同时连5个IP。 

Weblogic启动： 

[<img height="357" alt="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image006_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image006.jpg) 

进入Weblogic控制台：<http://localhost:7001/console/> 

控制台使用了Applet，所以必需安装了浏览器Java插件（JDK安装的最后一项有选择）并且启用后才能正常浏览。Windows2003的IE安全级别比较高，不能使用。可以用Firefox,Opera等其他浏览器。 

[<img height="329" alt="clip_image008" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image008_thumb.jpg" width="554" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image008.jpg) 

用户名和密码输入配置Domain的时候指定的用户名和密码。 

[<img height="551" alt="clip_image010" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image010_thumb.jpg" width="455" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image010.jpg) 

&#160; 

[<img height="108" alt="clip_image013" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image013_thumb.jpg" width="206" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image013.jpg) 

Deployments显示发布的应用，包括EAR（Applications下面），EJB模块，Web应用模块，连接器模块。   
监控服务器的Performance（性能）：内存，CPU，线程列表等。 

[<img height="325" alt="clip_image015" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image015_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image015.jpg) 

MyEclipse 整合 Weblogic 开发 

[<img height="155" alt="clip_image017" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image017_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image017.jpg) 

[<img height="401" alt="clip_image019" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image019_thumb.jpg" width="554" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image019.jpg) 

Domain目录是 C:beauser_projectsdomainsmydomain 

JDK 必需用JDK 1.4 

[<img height="497" alt="clip_image021" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image021_thumb.jpg" width="536" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image021.jpg) 

配置成功后在Servers视图中出现Weblogic图标。 

[<img height="96" alt="clip_image023" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image023_thumb.jpg" width="436" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image023.jpg) 

新建Web项目J2EE 版本必须用1.3。 

[<img height="500" alt="clip_image025" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image025_thumb.jpg" width="500" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image025.jpg) 

发布项目：最终项目发布到C:beauser_projectsdomainsmydomainapplications项目名下面。另外在config.xml中加入了配置信息： 

<Application Name="\_appsdir\_weblogictest_dir" 

Path="C:beauser_projectsdomainsmydomainapplications" 

StagingMode="nostage" TwoPhase="true"> 

<WebAppComponent Name="weblogictest" Targets="myserver" URI="weblogictest"/> 

</Application> 

</Domain> 

[<img height="484" alt="clip_image027" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image027_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image027.jpg) 

发布成功的检查，先看Console中的Web模块列表，垃圾桶图标可用来删除发布。 

[<img height="211" alt="clip_image029" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image029_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image029.jpg) 

[<img height="124" alt="clip_image031" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image031_thumb.jpg" width="554" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image031.jpg) 

重新发布 Redeploy 停止 Stop 

访问：<http://localhost:7001/weblogictest/> 检查运行结果。 

如果要写类文件，必须把编译器级别设置成JDK 1.4： 

菜单 Project > Properties 

[<img height="185" alt="clip_image033" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image033_thumb.jpg" width="554" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image033.jpg) 

Weblogic的JSP表单参数中文问题不论GET还是POST，都通过request.setCharacterEncoding("GBK"); 即可解决。 

查看JNDI树： 

[<img height="372" alt="clip_image035" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image035_thumb.jpg" width="258" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image035.jpg) 

[<img height="152" alt="clip_image037" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image037_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image037.jpg) 

JNDI绑定： 

javax.naming.InitialContext ctx = **new** javax.naming.InitialContext ();// 打开 JNDI 树 

Object o = ctx.lookup("NameService");// 找文件 

out.println(o); 

// 创建目录（Context) 

ctx.createSubcontext("beijing");// 先创建上级目录 

ctx.createSubcontext("beijing/2008");// 创
  
建下级目录 

// 绑定对象 

ctx.rebind("beijing/2008/赞助商", "本拉登"); 

ctx.rebind("beijing/问题", **new** String[] {"物价飞涨", "交通阻塞"} ); 

[<img height="270" alt="clip_image039" src="http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image039_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/clip_image039.jpg)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Weblogic 8和MyEclipse 5.5 整合 Web 开发](http://www.beansoft.biz/2008/06/04/weblogic-8%e5%92%8cmyeclipse-5-5-%e6%95%b4%e5%90%88-web-%e5%bc%80%e5%8f%91/)