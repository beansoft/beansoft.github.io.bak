---
id: 1494
title: mapbar.com网站出错
date: 2010-12-10T19:48:45+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1494
permalink: '/2010/12/10/mapbar-com%e7%bd%91%e7%ab%99%e5%87%ba%e9%94%99/'
views:
  - "2985"
original_post_id:
  - "1494"
categories:
  - 资讯频道
---
今天想搜下公交换乘, 然而输入<http://www.mapbar.com/>后,出现在眼前的是这么一幕熟悉的Tomcat出错画面:

### HTTP Status 500 &#8211;

<hr size="1" noshade="noshade" />

**type** Exception report

**message**<u></u>

**description** <u>The server encountered an internal error () that prevented it from fulfilling this request.</u>

**exception**

<pre>org.apache.jasper.JasperException: /home_beijing.jsp(1,65) File "/common/ipCheck.jsp" not found
	org.apache.jasper.compiler.DefaultErrorHandler.jspError(DefaultErrorHandler.java:83)
	org.apache.jasper.compiler.ErrorDispatcher.dispatch(ErrorDispatcher.java:402)
	org.apache.jasper.compiler.ErrorDispatcher.jspError(ErrorDispatcher.java:126)
	org.apache.jasper.compiler.Parser.processIncludeDirective(Parser.java:384)
	org.apache.jasper.compiler.Parser.parseIncludeDirective(Parser.java:417)
	org.apache.jasper.compiler.Parser.parseDirective(Parser.java:515)
	org.apache.jasper.compiler.Parser.parseElements(Parser.java:1577)
	org.apache.jasper.compiler.Parser.parse(Parser.java:171)
	org.apache.jasper.compiler.ParserController.parse(ParserController.java:247)
	org.apache.jasper.compiler.ParserController.parse(ParserController.java:149)
	org.apache.jasper.compiler.ParserController.parse(ParserController.java:135)
	org.apache.jasper.compiler.Compiler.generateJava(Compiler.java:237)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:456)
	org.apache.jasper.compiler.Compiler.compile(Compiler.java:439)
	org.apache.jasper.JspCompilationContext.compile(JspCompilationContext.java:552)
	org.apache.jasper.servlet.JspServletWrapper.service(JspServletWrapper.java:291)
	org.apache.jasper.servlet.JspServlet.serviceJspFile(JspServlet.java:301)
	org.apache.jasper.servlet.JspServlet.service(JspServlet.java:248)
	javax.servlet.http.HttpServlet.service(HttpServlet.java:856)</pre>

**note** <u>The full stack trace of the root cause is available in the Tomcat logs.</u>

<hr size="1" noshade="noshade" />

##### Apache Tomcat/5.0.16

[<img style="background-image:none;border-bottom:0;border-left:0;padding-left:0;padding-right:0;display:inline;border-top:0;border-right:0;padding-top:0;" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/12/image_thumb2.png" width="756" height="654" />](http://www.beansoft.biz/wp-content/uploads/2010/12/image2.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [mapbar.com网站出错](http://www.beansoft.biz/2010/12/10/mapbar-com%e7%bd%91%e7%ab%99%e5%87%ba%e9%94%99/)