---
id: 1489
title: WebLogic Edoc中关于weblogic.Deployer的一点小问题
date: 2010-12-09T19:12:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1489
permalink: '/2010/12/09/weblogic-edoc%e4%b8%ad%e5%85%b3%e4%ba%8eweblogic-deployer%e7%9a%84%e4%b8%80%e7%82%b9%e5%b0%8f%e9%94%99%e8%af%af/'
views:
  - "8896"
original_post_id:
  - "1489"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
Edoc中说可以通过如下格式部署应用:

<pre>java weblogic.Deployer -adminurl <strong>http://localhost:7001</strong> -user weblogic<br />&#160;&#160; -password weblogic -name mytestear -stage -targets mycluster <br />&#160;&#160; <b>-deploy</b> c:beaweblogic81samplesservermedrecddistphysicianEar</pre>

&#160;

然而, 经过测试, 发现**http://localhost:7001**根本不能连通, 倒是改为**localhost:7001**后运行OK. 测试环境 WebLogic 11gR1(10.3.3).

通过的例子:

<font face="Consolas">java weblogic.Deployer -adminurl <strong>localhost:7001</strong> -user weblogic -password weblogic1 -deploy D:WorkspacesMyEclipsewebtestWebRoot</font>

<font face="Consolas">那么如何才能连通呢? 需要启用AdminServer的HTTP隧道功能, 操作步骤:</font>

### AdminServer的设置&#8211;>**协议**标签&#8211;>**HTTP**标签&#8211;>**启用隧道**复选框(指定是否应为此服务器启用通过 T3, T3S, HTTP, HTTPS, IIOP 和 IIOPS 协议进行的隧道通信。)

即可, 默认情况下未启用HTTP隧道.

相关文档地址: <http://download.oracle.com/docs/cd/E13222_01/wls/docs92/deployment/deploy.html> 中文地址: <http://edocs.weblogicfans.net/wls/docs92/deployment/wldeployer.html>

其它文档(转自forest_hou):

weblogic.Deployer Examples:

To deploy a new application:
    
  
java weblogic.Deployer -adminurl t3://localhost:7001

&#160;&#160;&#160;&#160; -username system -password weblogic&#160;&#160;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; -name app -source /myapp/app.ear

&#160;&#160;&#160;&#160; -targets server1,server2 -deploy

To redeploy an application:

java weblogic.Deployer -adminurl t3://localhost:7001

&#160;&#160;&#160;&#160; -username system -password weblogic -name app –redeploy

To redeploy part of an application:

java weblogic.Deployer -adminurl t3://localhost:7001

&#160;&#160;&#160;&#160; -username system -password weblogic

&#160;&#160;&#160;&#160; -targets server1,server2 -redeploy jsps/*.jsp

To undeploy an application:

java weblogic.Deployer -adminurl t3://localhost:7001

&#160;&#160;&#160;&#160; -username system -password weblogic -undeploy

&#160;&#160;&#160;&#160; -name myapp –targets server1,server2

To list all deployed applications:
    
  
java weblogic.Deployer -adminurl t3://localhost:7001

&#160;&#160;&#160;&#160; -username system -password weblogic -listapps

To list all deployment tasks:

java weblogic.Deployer -adminurl http://localhost:7001

&#160;&#160;&#160;&#160; -username system –password weblogic -listtask

To cancel a deployment task:

java weblogic.Deployer -adminurl http://localhost:7001

&#160;&#160;&#160;&#160; -username system –password weblogic -cancel -id tag

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic Edoc中关于weblogic.Deployer的一点小问题](http://www.beansoft.biz/2010/12/09/weblogic-edoc%e4%b8%ad%e5%85%b3%e4%ba%8eweblogic-deployer%e7%9a%84%e4%b8%80%e7%82%b9%e5%b0%8f%e9%94%99%e8%af%af/)