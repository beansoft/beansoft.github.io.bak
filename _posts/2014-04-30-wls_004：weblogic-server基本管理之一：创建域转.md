---
id: 3635
title: 'WLS_004：WebLogic Server基本管理之一：创建域[转]'
date: 2014-04-30T17:54:58+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3635
permalink: '/2014/04/30/wls_004%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%b8%80%ef%bc%9a%e5%88%9b%e5%bb%ba%e5%9f%9f%e8%bd%ac/'
views:
  - "4989"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
[http://maping930883.blogspot.jp/2009/03/wls004weblogic-server.html](http://maping930883.blogspot.jp/2009/03/wls004weblogic-server.html "http://maping930883.blogspot.jp/2009/03/wls004weblogic-server.html")

一般来说，为一组逻辑相关的单元创建一个Domain就够了，但实际情况往往需要为开发、测试、生产环境创建同样配置的Domain，因此就有了创建 Domain Template的功能。   
**1. 创建 Domain Template**   
Windows 环境下：Start > Programs > BEA Products > Tools > Domain Template Builder   
或者运行脚本 [wlserver\_10.x]\common\bin\config\_builder.cmd。   
创建Domain Template中，可以把开发、测试、生产环境中相同配置的部分一次创建好。   
这样创建各自域时，只需要修改不同的部分就可以了。   
创建Domain Template后会生成一个.jar文件，请保存好。   
**2. 创建 Domain**   
Windows 环境下：Start > Programs > BEA Products > Tools > Configuration Wizard.   
或者运行脚本 [wlserver_10.x]\common\bin\config.cmd。   
创建Domain时，可以根据已有的Domain Template。   
**3. 如何删除一个Domain？**   
（1）手工删除[FMW\_home]/user\_projects/domains/[domain_name]目录。   
（2）手工删除[FMW\_home]/user\_projects/applications/[domain_name]目录。   
（3）修改[FMW\_home]/wlserver\_10.3/common/nodemanager/nodemanager.domains内容，去除掉相关的Domain项。   
（4）修改[FMW_home]/utils/ccr/domainlocation.properties内容，去除掉相关的Domain项。   
（5）修改[FMW_home]/domain-registry.xml内容，去除掉相关的Domain项。 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_004：WebLogic Server基本管理之一：创建域[转]](http://www.beansoft.biz/2014/04/30/wls_004%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e4%b8%80%ef%bc%9a%e5%88%9b%e5%bb%ba%e5%9f%9f%e8%bd%ac/)