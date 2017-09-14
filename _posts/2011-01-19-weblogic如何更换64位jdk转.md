---
id: 1611
title: 'WebLogic如何更换64位JDK[转]'
date: 2011-01-19T09:53:06+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1611
permalink: '/2011/01/19/weblogic%e5%a6%82%e4%bd%95%e6%9b%b4%e6%8d%a264%e4%bd%8djdk%e8%bd%ac/'
views:
  - "9607"
original_post_id:
  - "1611"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
  - 转载区
---
来源: <http://fm928.blog.163.com/blog/static/74813520110695435495/> 作者: 踏雪无痕

&#160;

使用32位JDK时，JVM一般设置最大设置为1.7G，而现在服务器普遍内存都很大，当然可以通过多个server建立垂直集群来更好的利用资源，但不妨使用64位JDK。虽然WebLogic可以直接在setDomainEnv里指定JAVA\_HOME来更改JDK，但肯定会遇到BEA-000438的错，原因在于缺少对应64位JDK的native io libaray（位于weblogic/server/native）。一种方式是从别处拷贝一份过来，还有一种是下载wls\_generic.jar形式的安装文件，而不是已经带有JDK的。然后下载64位JDK安装（[Jrockit下载](http://www.oracle.com/technology/software/products/jrockit/index.html)），用java –jar wls_generic.jar来安装就可以了。   
————————————————————————————   
附一个错误分析，和native libaray相关，但并不是由于64位的关系，而是没有执行权限。   
启动过程中发现   
<Apr 28, 2010 6:27:15 PM GMT+08:00> <Error> <Socket> <**BEA-000438**> <**Unable to loa   
d performance pack. Using Java I/O instead**. Please ensure that a native performa   
nce library is in: ‘/opt/java1.5/jre/lib/IA64N:/opt/java1.5/jre/lib/IA64N/server   
:/opt/java1.5/jre/../lib/IA64N::/opt/weblogic/bea/weblogic90/server/native/hpux1   
1/IPF64:/opt/weblogic/bea/weblogic90/server/native/hpux11/PA_RISC:/opt/weblogic/   
bea/weblogic90/server/native/hpux11/PA\_RISC/oci920\_8:/usr/lib’   
没有启动native io，导致系统性能低下（这里要注意HP-UX里IA64N下的是32位JDK，IA64W下的才是64位JDK），而且java io配置的值较小，产生如下报错   
<Apr 28, 2010 6:15:03 PM GMT+08:00> <Warning> <Socket> <**BEA-000402**> <There are:   
5 active sockets, but the maximum number of socket reader threads allowed by the   
configuration is: 4. You may want to alter your configuration.>   
在应用使用过程中从而出现   
<Apr 28, 2010 6:14:10 PM GMT+08:00> <Error> <Console> <BEA-240003> <Console enco   
untered the following error javax.servlet.jsp.JspException: Broken pipe (errno:3   
2)   
&#160;&#160;&#160;&#160;&#160;&#160; at com.bea.console.taglib.html.tree.TreeTag.print(TreeTag.java:231)   
&#160;&#160;&#160;&#160;&#160;&#160; at com.bea.console.taglib.html.tree.TreeTag.doEndTag(TreeTag.java:192)   
观察控制台的thread信息   
Self-Tuning Thread Pool&#160;&#160;&#160;&#160;   
Active Execute Threads Execute Thread Total Count Execute Thread Idle Count Queue Length Pending User Request Count Completed Request Count Hogging Thread Count Standby Thread Count Throughput Health   
16 58 15 6048 0 144840 4 38 4.577865205875421 OK   
排队的请求数多达6000个，导致了OutOfMemory，在JAVA堆还很空的情况下   
观察发现/opt/weblogic/bea/weblogic90/server/native/hpux11/IPF32下面和native io相关的libmuxer.so没有执行权限，chmod +x 后再次启动错误信息不再出现

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic如何更换64位JDK[转]](http://www.beansoft.biz/2011/01/19/weblogic%e5%a6%82%e4%bd%95%e6%9b%b4%e6%8d%a264%e4%bd%8djdk%e8%bd%ac/)