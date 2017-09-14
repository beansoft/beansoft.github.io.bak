---
id: 1484
title: 'weblogic.Admin[转]'
date: 2010-12-07T18:49:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1484
permalink: '/2010/12/07/weblogic-admin%e8%bd%ac/'
views:
  - "4521"
original_post_id:
  - "1484"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
  - 转载区
---
来自folin(forest_hou)的BLOG: <http://blog.csdn.net/forest_hou/archive/2010/04/09/5468239.aspx>

通过命令行远程方式来连接weblogic服务完成监控和管理weblogic   
&#8211;weblogic自身提供多种途径的监控管理方式，下面就简单介绍，主要对命令行方式做一个详细的总结   
1、采用图形化方式console控制台来进行管理，通过浏览器输入地址/console就可访问，需要管理员用户名和口令；   
2、采用jrockit自己提供的监控调试工具；   
>首先激活管理服务，在执行java项加入-Xmanagement,重新启动weblogic即可；   
>命令进入jrockit所在的bin路径下，执行命令行console回车，稍等即可弹出监控控制台；   
3、采用命令行的方式；   
>命令行进入jrockit所在的bin路径下，执行命令格式java weblogic.Admin -username weblogic -password weblogic -url ip:port [参数项]；   
>比如：   
java weblogic.Admin -username weblogic -password weblogic -url localhost:7001 GET -pretty -type JDBCConnectionPoolRuntime   
返回连接池的使用情况，只是返回此时时间点的快照   
java weblogic.Admin -username weblogic -password weblogic -url localhost:7001 GET -pretty -type JVMRuntime   
返回jvm的使用情况，只能是看到此时快照；   
java weblogic.Admin -username weblogic -password weblogic -url localhost:7001 GET -pretty -type ExecuteQueueRuntime   
javaweblogic.Admin -username weblogic -password weblogic -urllocalhost:7001 GET -pretty -mbean"LhtForum:Location=myserver,Name=weblogic.kernel.Default,ServerRuntime=myserver,Type=ExecuteQueueRuntime"   
lhtforum代表域，必须与实际的域名相同，如果是集群这个域名就是集群的域名，myserver就是节点的服务名   
返回线程池的使用情况，只能是看到此时快照；   
详解：   
============================================================================================   
命令行管理（URL 例如：localhost:7001）   
&#160; java weblogic.Admin -username unmae -password pwd -url URL COMMAND arguments   
一些weblogic.Admin   
&#160;&#160;&#160;&#160; PING&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 证实weblogic server是否正常   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL PING count bytes&#160;   
&#160;&#160;&#160;&#160; CONNECT&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 计算连接数和每次往返所需要的总时间   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL CONNECT count   
&#160;&#160;&#160;&#160; LICENSES&#160;&#160;&#160;&#160;&#160;&#160;&#160; 列出weblogic server实例当前的许可产品   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL LICENSES   
&#160;&#160;&#160;&#160; VERSION&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 列出所安装weblogic server产品的当前版本   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL VERSION   
&#160;&#160;&#160;&#160; HELP&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 为命令提供语法和使用的帮助   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin HELP COMMAND   
&#160;&#160;&#160;&#160; START&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 启动一个远程的被管理的服务器   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL START tagetserver   
&#160;&#160;&#160;&#160; DISCOVER&#160;&#160;&#160;&#160;&#160;&#160;&#160; 查找一个被管理服务器，使管理服务器建立到被管理服务器的控制   
&#160;&#160;&#160;&#160; MANAGED SERVER&#160; 例如：java weblogic.Admin -url URL DISCOVERMANAGEDSERVER   
&#160;&#160;&#160;&#160; SHUTDOWN&#160;&#160;&#160;&#160;&#160;&#160;&#160; 关闭weblogic server实例&#160;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL SHUTDOWEN targetserver   
&#160;&#160;&#160;&#160; FORCE SHUTDOWN&#160; 强迫关闭weblogic server实例，不必等待完成当前的会话   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL FORCESHUTDOWN   
&#160;&#160;&#160;&#160; RESUME&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 将服务器从STANDBY状态（挂起状态）转为运行状态   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL RESUME targetserver   
&#160;&#160;&#160;&#160; GETSTATE&#160;&#160;&#160;&#160;&#160;&#160;&#160; 返回weblogic server当前状态   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL GETSTATE   
&#160;&#160;&#160;&#160; SERVERLOG&#160;&#160;&#160;&#160;&#160;&#160; 显示具体服务器产生的日志文件   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL SERVERLOG starttime endtime   
&#160;&#160;&#160;&#160; THREAD_DUMP&#160;&#160;&#160;&#160; 当前运行weblogic server线程的实时快照（排错时时常使用）   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL THREAD_DUMP   
&#160;&#160;&#160;&#160; MIGRATE&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 在集群中迁移JMS或JTA服务   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL MIGRATE   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; -jta -migratabletarget servername -destination servername   
&#160;&#160;&#160;&#160; LIST&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 列出JNDI命名树节点绑定的情况   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 例如：java weblogic.Admin -url URL LIST context

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [weblogic.Admin[转]](http://www.beansoft.biz/2010/12/07/weblogic-admin%e8%bd%ac/)