---
id: 3586
title: 'WLS_002：WebLogic Server 基本概念[转]'
date: 2014-04-30T17:44:19+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3586
permalink: '/2014/04/30/wls_002%ef%bc%9aweblogic-server-%e5%9f%ba%e6%9c%ac%e6%a6%82%e5%bf%b5%e8%bd%ac/'
views:
  - "3277"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: [http://maping930883.blogspot.jp/2009/03/wls002weblogic-server.html](http://maping930883.blogspot.jp/2009/03/wls002weblogic-server.html "http://maping930883.blogspot.jp/2009/03/wls002weblogic-server.html")

[<img style="background-image: none; border-bottom: 0px; border-left: 0px; padding-left: 0px; padding-right: 0px; display: inline; border-top: 0px; border-right: 0px; padding-top: 0px" title="Image" border="0" alt="Image" src="http://www.beansoft.biz/wp-content/uploads/2014/04/Image.jpg" width="400" height="378" />](http://3.bp.blogspot.com/_vtOtDKeW4LM/SXA4saFT0iI/AAAAAAAAAPg/T5OqIpsMcXk/s1600-h/%C3%A6%C5%93%C2%AA%C3%A5%E2%80%98%C2%BD%C3%A5%EF%BF%BD%EF%BF%BD.JPG)

**1. 域 (Domain)**

相关联的一组WebLogic服务器资源，作为一个单元来管理。

一个域可以包含一或多个WebLogic服务器，以及WebLogic服务器集群。

在[weblogic\_server\_install_dir]/config/

/config.xml文件中定义了域的配置。

对应用而言，域是透明的（发布应用时无需指定域）。

域中的所有WebLogic服务器必须是同一版本的（major and minor version）。

**2. 服务器 (Server)**

一个服务器是一个weblogic.Server类的实例，运行在JVM中，支持多线程。

应用和资源发布到服务器上。

服务器分为两种：管理服务器和受管服务器。

**3. 管理服务器 (Admin Server)**

运行管理服务的WebLogic服务器称为管理服务器。

管理服务器集中管理并监控域中的所有资源。

如果要对某个域执行管理操作，该域的管理服务器必须处于运行状态。

一个域中只能有一个管理服务器，一个管理服务器只能管理一个域。

建议，在生产环境中，不要把应用和资源发布到管理服务器上，这样，如果管理服务器出现故障，并不会影响受管服务器上的应用。

**4. 受管服务器 (Managed Server)**

从管理服务器获取配置信息，负责运行应用。

管理服务器负责保存域的配置信息，包括所有的受管服务器在域中的配置。

每个受管服务器本地保留一份配置信息的复制版本。

当受管服务器启动时，它将连接管理服务器并同步配置信息。

如果配置信息被修改了，管理服务器将发送改变后的配置信息给受管服务器。

**5. 集群 (Cluster)**

一组受管服务器同时一起工作，用于提供高可用性（High Availability）和负载均衡（Load balancing）。

扩展性（scalability）和可靠性（reliability）。

对客户端而言，集群是透明的（感觉就和一个Weblogic Server一样）。

Clusters enable some advanced features, such as Whole Server Migration, Service Migration, and clustered JMS destinations.

**6. 机器 (Machine)**

含有WebLogic Server(s)的一台物理机器。

WebLogic服务器利用机器的配置来决定使用集群中哪个服务器最适合做HTTP session 复制。

管理服务器利用机器上定义的节点管理器远程启动WebLogic Server实例。

**7. 节点管理器 （Node Manager）**

在生产环境中，服务器实例可能分布在不同的域、机器、以及地理位置。

节点管理器是Weblogic Server的一个工具，用于远程启动、停止、重启管理服务器或受管服务器。

节点管理器进程与域无关，只与机器有关。

你可以使用同一个节点管理器进程控制该机器上的所有服务器，无论它们是否是同一个域的。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_002：WebLogic Server 基本概念[转]](http://www.beansoft.biz/2014/04/30/wls_002%ef%bc%9aweblogic-server-%e5%9f%ba%e6%9c%ac%e6%a6%82%e5%bf%b5%e8%bd%ac/)