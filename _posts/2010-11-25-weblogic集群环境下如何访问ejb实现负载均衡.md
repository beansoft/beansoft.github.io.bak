---
id: 1430
title: WebLogic集群环境下如何访问EJB实现负载均衡
date: 2010-11-25T21:32:40+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1430
permalink: '/2010/11/25/weblogic%e9%9b%86%e7%be%a4%e7%8e%af%e5%a2%83%e4%b8%8b%e5%a6%82%e4%bd%95%e8%ae%bf%e9%97%aeejb%e5%ae%9e%e7%8e%b0%e8%b4%9f%e8%bd%bd%e5%9d%87%e8%a1%a1/'
views:
  - "8689"
original_post_id:
  - "1430"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
许多初学者测试WebLogic的集群功能时, 总是想当然的以为代理服务器的地址就是集群的地址, 没错, 这个地址是集群地址, 但是它是Web集群的地址, JNDI 本身则并不存在所谓的一个中心集群服务器, 通过JNDI进行访问的EJB, 数据源等也是如此.

WebLogic JNDI 树可以作为集群服务. JNDI的上下文内容已经进行了复制, 因此它可以透明的在集群中的任意受管服务器上实现容灾恢复.要访问WebLogic集群中的EJB, 客户端需要指定一系列使用不同端口和IP的WebLogic Server服务器. 

示意代码如下:

> <font size="4"></font><font face="Consolas">String url = <strong>"t3://IP1:8001,IP2:9001";</strong></font>
> 
> <font face="Consolas">Hashtable<String,String> h = <b>new </b>Hashtable<String,String>(); <br />h.put(Context.INITIAL_CONTEXT_FACTORY,"weblogic.jndi.WLInitialContextFactory"); <br />h.put(Context.PROVIDER_URL, url); <br />InitialContext ctx = new InitialContext(h);</font>
> 
> <font face="Consolas">MyEJB ejb = (MyEJB)ctx.lookUp(“myEJBJNDIPath”);</font>

然而, 将url地址配置为JNDI上的一个全局变量, 可能会是一种更好的实践, 这样系统管理员可很容易的更新Cluster环境的新变动.

更多示例代码参考:**WebLogic 11g安装目录**wlserver_10.3samplesserverexamplessrcexamplesclusterejbstatefulSession

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic集群环境下如何访问EJB实现负载均衡](http://www.beansoft.biz/2010/11/25/weblogic%e9%9b%86%e7%be%a4%e7%8e%af%e5%a2%83%e4%b8%8b%e5%a6%82%e4%bd%95%e8%ae%bf%e9%97%aeejb%e5%ae%9e%e7%8e%b0%e8%b4%9f%e8%bd%bd%e5%9d%87%e8%a1%a1/)