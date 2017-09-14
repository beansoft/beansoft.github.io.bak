---
id: 1337
title: 'MyEclipse 6开发JDK6和Struts 2冲突的问题真实原因及解决办法[原创]'
date: 2010-10-23T11:48:37+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1337
permalink: '/2010/10/23/myeclipse-6%e5%bc%80%e5%8f%91jdk6%e5%92%8cstruts-2%e5%86%b2%e7%aa%81%e7%9a%84%e9%97%ae%e9%a2%98%e7%9c%9f%e5%ae%9e%e5%8e%9f%e5%9b%a0%e5%8f%8a%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95%e5%8e%9f%e5%88%9b/'
views:
  - "6273"
original_post_id:
  - "1337"
image: /wp-content/uploads/2012/09/clip_image0026_thumb.jpg
categories:
  - Struts
---
整理: 本文发表于 2008-10-13, 作者: 刘长炯(<beansoft@126.com>)

前一阵子在开发一个Struts2的原型SCM项目, 用Struts 2+Hibernate开发. 再次遇到了 Struts 2+JDK 6的冲突问题.

&#160;

出错信息: Illegal access: this web application instance has been stopped already. Could not load org.xml.sax.SAXException. The eventual following stack trace is caused by an error thrown for debugging purposes as well as to attempt to terminate the thread which caused the illegal access, and has no functional impact. 

<u>java.lang.IllegalStateException</u> 

at org.apache.catalina.loader.WebappClassLoader.loadClass(<u>WebappClassLoader.java:1244</u>) 

at org.apache.catalina.loader.WebappClassLoader.loadClass(<u>WebappClassLoader.java:1204</u>) 

at java.lang.ClassLoader.loadClassInternal(<u>ClassLoader.java:319</u>) 

at org.apache.xerces.jaxp.DocumentBuilderFactoryImpl.newDocumentBuilder(Unknown Source) 

at com.sun.org.apache.xalan.internal.xsltc.trax.SAX2DOM.<init>(<u>SAX2DOM.java:69</u>) 

at com.sun.org.apache.xalan.internal.xsltc.runtime.output.TransletOutputHandlerFactory.getSerializationHandler(<u>TransletOutputHandlerFactory.java:187</u>) 

at com.sun.org.apache.xalan.internal.xsltc.trax.TransformerImpl.getOutputHandler(<u>TransformerImpl.java:392</u>) 

at com.sun.org.apache.xalan.internal.xsltc.trax.TransformerHandlerImpl.setResult(<u>TransformerHandlerImpl.java:137</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.setup(<u>DomHelper.java:213</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.<init>(<u>DomHelper.java:198</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.<init>(<u>DomHelper.java:189</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.<init>(<u>DomHelper.java:175</u>) 

at com.opensymphony.xwork2.util.DomHelper.parse(<u>DomHelper.java:115</u>) 

at com.opensymphony.xwork2.config.providers.XmlConfigurationProvider.loadConfigurationFiles(<u>XmlConfigurationProvider.java:830</u>) 

at com.opensymphony.xwork2.config.providers.XmlConfigurationProvider.loadDocuments(<u>XmlConfigurationProvider.java:131</u>) 

at com.opensymphony.xwork2.config.providers.XmlConfigurationProvider.init(<u>XmlConfigurationProvider.java:100</u>) 

at com.opensymphony.xwork2.config.impl.DefaultConfiguration.reload(<u>DefaultConfiguration.java:130</u>) 

at com.opensymphony.xwork2.config.ConfigurationManager.getConfiguration(<u>ConfigurationManager.java:52</u>) 

at org.apache.struts2.dispatcher.Dispatcher.init_PreloadConfiguration(<u>Dispatcher.java:395</u>) 

at org.apache.struts2.dispatcher.Dispatcher.init(<u>Dispatcher.java:452</u>) 

at org.apache.struts2.dispatcher.FilterDispatcher.init(<u>FilterDispatcher.java:201</u>) 

at org.apache.catalina.core.ApplicationFilterConfig.getFilter(<u>ApplicationFilterConfig.java:275</u>) 

at org.apache.catalina.core.ApplicationFilterConfig.setFilterDef(<u>ApplicationFilterConfig.java:397</u>) 

at org.apache.catalina.core.ApplicationFilterConfig.<init>(<u>ApplicationFilterConfig.java:108</u>) 

at org.apache.catalina.core.StandardContext.filterStart(<u>StandardContext.java:3696</u>) 

at org.apache.catalina.core.StandardContext.start(<u>StandardContext.java:4343</u>) 

at org.apache.catalina.core.StandardContext.reload(<u>StandardContext.java:3086</u>) 

at org.apache.catalina.manager.ManagerServlet.reload(<u>ManagerServlet.java:912</u>) 

at org.apache.catalina.manager.HTMLManagerServlet.reload(<u>HTMLManagerServlet.java:523</u>) 

at org.apache.catalina.manager.HTMLManagerServlet.doGet(<u>HTMLManagerServlet.java:113</u>) 

at javax.servlet.http.HttpServlet.service(<u>HttpServlet.java:690</u>) 

at javax.servlet.http.HttpServlet.service(<u>HttpServlet.java:803</u>) 

at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(<u>ApplicationFilterChain.java:290</u>) 

at org.apache.catalina.core.ApplicationFilterChain.doFilter(<u>ApplicationFilterChain.java:206</u>) 

at org.apache.catalina.core.StandardWrapperValve.invoke(<u>StandardWrapperValve.java:233</u>) 

at org.apache.catalina.core.StandardContextValve.invoke(<u>StandardContextValve.java:175</u>) 

at org.apache.catalina.authenticator.AuthenticatorBase.invoke(<u>AuthenticatorBase.java:525</u>) 

at org.apache.catalina.core.StandardHostValve.invoke(<u>StandardHostValve.java:128</u>) 

at org.apache.catalina.valves.ErrorReportValve.invoke(<u>ErrorReportValve.java:102</u>) 

at org.apache.catalina.core.StandardEngineValve.invoke(<u>StandardEngineValve.java:109</u>) 

at org.apache.catalina.connector.CoyoteAdapter.service(<u>CoyoteAdapter.java:263</u>) 

at org.apache.coyote.http11.Http11AprProcessor.process(<u>Http11AprProcessor.java:852</u>) 

at org.apache.coyote.http11.Http11AprProtocol$Http11ConnectionHandler.process(<u>Http11AprProtocol.java:584</u>) 

at org.apache.tomcat.util.net.AprEndpoint$Worker.run(<u>AprEndpoint.java:1508</u>) 

at java.lang.Thread.run(<u>Thread.java:619</u>) 

2008-9-19 0:08:34 org.apache.catalina.core.StandardContext filterStart 

严重: Exception starting filter struts2 

Caught exception while loading file struts-default.xml &#8211; [unknown location] 

at com.opensymphony.xwork2.config.providers.XmlConfigurationProvider.loadConfigurationFiles(<u>XmlConfigurationProvider.java:839</u>) 

at com.opensymphony.xwork2.config.providers.XmlConfigurationProvider.loadDocuments(<u>XmlConfigurationProvider.java:131</u>) 

at com.opensymphony.xwork2.config.providers.XmlConfigurationProvider.init(<u>XmlConfigurationProvider.java:100</u>) 

at com.opensymphony.xwork2.config.impl.DefaultConfiguration.reload(<u>DefaultConfiguration.java:130</u>) 

at com.opensymphony.xwork2.config.ConfigurationManager.getConfiguration(<u>ConfigurationManager.java:52</u>) 

at org.apache.struts2.dispatcher.Dispatcher.init_PreloadConfiguration(<u>Dispatcher.java:395</u>) 

at org.apache.struts2.dispatcher.Dispatcher.init(<u>Dispatcher.java:452</u>) 

at org.apache.struts2.dispatcher.FilterDispatcher.init(<u>FilterDispatcher.java:201</u>) 

at org.apache.catalina.core.ApplicationFilterConfig.getFilter(<u>ApplicationFilterConfig.java:275</u>) 

at org.apache.catalina.core.ApplicationFilterConfig.setFilterDef(<u>ApplicationFilterConfig.java:397</u>) 

at org.apache.catalina.core.ApplicationFilterConfig.<init>(<u>ApplicationFilterConfig.java:108</u>) 

at org.apache.catalina.core.StandardContext.filterStart(<u>StandardContext.java:3696</u>) 

at org.apache.catalina.core.StandardContext.start(<u>StandardContext.java:4343</u>) 

at org.apache.catalina.core.StandardContext.reload(<u>StandardContext.java:3086</u>) 

at org.apache.catalina.manager.ManagerServlet.reload(<u>ManagerServlet.java:912</u>) 

at org.apache.catalina.manager.HTMLManagerServlet.reload(<u>HTMLManagerServlet.java:523</u>) 

at org.apache.catalina.manager.HTMLManagerServlet.doGet(<u>HTMLManagerServlet.java:113</u>) 

at javax.servlet.http.HttpServlet.service(<u>HttpServlet.java:690</u>) 

at javax.servlet.http.HttpServlet.service(<u>HttpServlet.java:803</u>) 

at org.apache.catalina.core.ApplicationFilterChain.internalDoFilter(<u>ApplicationFilterChain.java:290</u>) 

at org.apache.catalina.core.ApplicationFilterChain.doFilter(<u>ApplicationFilterChain.java:206</u>) 

at org.apache.catalina.core.StandardWrapperValve.invoke(<u>StandardWrapperValve.java:233</u>) 

at org.apache.catalina.core.StandardContextValve.invoke(<u>StandardContextValve.java:175</u>) 

at org.apache.catalina.authenticator.AuthenticatorBase.invoke(<u>AuthenticatorBase.java:525</u>) 

at org.apache.catalina.core.StandardHostValve.in
  
voke(<u>StandardHostValve.java:128</u>) 

at org.apache.catalina.valves.ErrorReportValve.invoke(<u>ErrorReportValve.java:102</u>) 

at org.apache.catalina.core.StandardEngineValve.invoke(<u>StandardEngineValve.java:109</u>) 

at org.apache.catalina.connector.CoyoteAdapter.service(<u>CoyoteAdapter.java:263</u>) 

at org.apache.coyote.http11.Http11AprProcessor.process(<u>Http11AprProcessor.java:852</u>) 

at org.apache.coyote.http11.Http11AprProtocol$Http11ConnectionHandler.process(<u>Http11AprProtocol.java:584</u>) 

at org.apache.tomcat.util.net.AprEndpoint$Worker.run(<u>AprEndpoint.java:1508</u>) 

at java.lang.Thread.run(<u>Thread.java:619</u>) 

Caused by: <u>java.lang.ClassCastException</u>: org.apache.xerces.parsers.XML11Configuration cannot be cast to org.apache.xerces.xni.parser.XMLParserConfiguration 

at org.apache.xerces.parsers.DOMParser.<init>(Unknown Source) 

at org.apache.xerces.parsers.DOMParser.<init>(Unknown Source) 

at org.apache.xerces.jaxp.DocumentBuilderImpl.<init>(Unknown Source) 

at org.apache.xerces.jaxp.DocumentBuilderFactoryImpl.newDocumentBuilder(Unknown Source) 

at com.sun.org.apache.xalan.internal.xsltc.trax.SAX2DOM.<init>(<u>SAX2DOM.java:69</u>) 

at com.sun.org.apache.xalan.internal.xsltc.runtime.output.TransletOutputHandlerFactory.getSerializationHandler(<u>TransletOutputHandlerFactory.java:187</u>) 

at com.sun.org.apache.xalan.internal.xsltc.trax.TransformerImpl.getOutputHandler(<u>TransformerImpl.java:392</u>) 

at com.sun.org.apache.xalan.internal.xsltc.trax.TransformerHandlerImpl.setResult(<u>TransformerHandlerImpl.java:137</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.setup(<u>DomHelper.java:213</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.<init>(<u>DomHelper.java:198</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.<init>(<u>DomHelper.java:189</u>) 

at com.opensymphony.xwork2.util.DomHelper$DOMBuilder.<init>(<u>DomHelper.java:175</u>) 

at com.opensymphony.xwork2.util.DomHelper.parse(<u>DomHelper.java:115</u>) 

at com.opensymphony.xwork2.config.providers.XmlConfigurationProvider.loadConfigurationFiles(<u>XmlConfigurationProvider.java:830</u>) 

&#8230; 31 more 

2008-9-19 0:08:34 org.apache.catalina.core.StandardContext start 

**现象****:** 第一次能运行, reload就不行. 启动不行. 

**解决思路****:** 排除法. 

先试了Struts2自带的blank包, 没问题. 

那基本可断定是其他jar包有冲突, 应该是XML解析包有冲突. 

检查发布后的WEB-INF/lib有两个XML解析包: xml-apis.jar和xerces-2.6.2.jar 

这种错误真正原因不是JDK 6和Struts 2冲突, 而是 MyEclipse Hibernate 类库中多了两个包: xml-apis.jar和xerces-2.6.2.jar, 这两个包的功能和JDK的冲突了. 解决办法: 1. 删除发布后目录的 WEB-INF/lib/ 下的这两个文件; 2. 或者使用JDK 1.5来启动Tomcat 6. 

方案1的详细操作步骤: 

a. 先把MyEclipse Hibernate 3.2 Core Lib从BuildPath去掉; 

[<img title="clip_image002[6]" style="display:inline;border-width:0;" height="216" alt="clip_image002[6]" src="http://www.beansoft.biz/wp-content/uploads/2010/10/clip_image0026_thumb.jpg" width="553" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/10/clip_image0026.jpg) 

b. 不要重新发布应用, 从发布后的目录复制全部的jar文件到开发工具下项目的WEB-INFlib目录下, 不要复制其中的xml-apis.jar和xerces-2.6.2.jar. 

c. 停止Tomcat, 重新发布应用或者删除发布后的目录下的WEB-INFlib下的xml-apis.jar和xerces-2.6.2.jar. 

小提示: MyEclipse 自带类库有很多问题, 建议读者自行下载官方网站jar包进行开发, 比较保险. 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [MyEclipse 6开发JDK6和Struts 2冲突的问题真实原因及解决办法[原创]](http://www.beansoft.biz/2010/10/23/myeclipse-6%e5%bc%80%e5%8f%91jdk6%e5%92%8cstruts-2%e5%86%b2%e7%aa%81%e7%9a%84%e9%97%ae%e9%a2%98%e7%9c%9f%e5%ae%9e%e5%8e%9f%e5%9b%a0%e5%8f%8a%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95%e5%8e%9f%e5%88%9b/)