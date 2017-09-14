---
id: 1300
title: WebLogic JSP Servlet 线程超时设置参数
date: 2010-10-09T12:30:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1300
permalink: '/2010/10/09/weblogic-jsp-servlet-%e7%ba%bf%e7%a8%8b%e8%b6%85%e6%97%b6%e8%ae%be%e7%bd%ae%e5%8f%82%e6%95%b0/'
views:
  - "5652"
original_post_id:
  - "1300"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
**作者: <BeanSoft@WebLogic> 日期: 2010-10-09 转载本站文章请务必注明出处!**

****

**案例:** jsp页面请求超时问题 <http://bbs.weblogicfans.net/viewthread.php?tid=3062>   
请教高手，该问题如何解决。 

####<Sep 20, 2010 8:05:08 PM GMT+08:00> <Error> <WebLogicServer> <dls_1> <csp1> <[STANDBY] ExecuteThread: &#8217;21&#8217; for queue: &#8216;weblogic.kernel.Default (self-tuning)&#8217;> <<WLS Kernel>> <>   
<> <1284984308770> <BEA-000337> <[STUCK] ExecuteThread: &#8216;4&#8217; for queue: &#8216;weblogic.kernel.Default (self-tuning)&#8217; has been busy for "671" seconds working on the request "Http Request:   
/CspWeb/csp/integrateAccept/custManage/selectCustomer.do", which is more than the configured time (StuckThreadMaxTime) of "600" seconds. Stack trace:   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; java.lang.ClassLoader.loadClass(ClassLoader.java:563)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.utils.classloaders.GenericClassLoader.loadClass(GenericClassLoader.java:161)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.utils.classloaders.FilteringClassLoader.findClass(FilteringClassLoader.java:83)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.utils.classloaders.FilteringClassLoader.loadClass(FilteringClassLoader.java:68)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; java.lang.ClassLoader.loadClass(ClassLoader.java:589)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; java.lang.ClassLoader.loadClass(ClassLoader.java:589)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; java.lang.ClassLoader.loadClass(ClassLoader.java:563)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; sun.misc.Unsafe.defineClass(Native Method)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; sun.reflect.ClassDefiner.defineClass(ClassDefiner.java:63)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; sun.reflect.MethodAccessorGenerator$1.run(MethodAccessorGenerator.java:399)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; java.security.AccessController.doPrivileged(AccessController.java:193)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; sun.reflect.MethodAccessorGenerator.generate(MethodAccessorGenerator.java:395)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; sun.reflect.MethodAccessorGenerator.generateMethod(MethodAccessorGenerator.java:77)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:52)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; java.lang.reflect.Method.invoke(Method.java:615)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; javax.faces.component.UIComponentBase$AttributesMap.get(UIComponentBase.java:1545)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.faces.renderkit.html_basic.TextRenderer.getEndTextToRender(TextRenderer.java:85)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.faces.renderkit.html_basic.HtmlBasicRenderer.encodeEnd(HtmlBasicRenderer.java:204)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; javax.faces.component.UIComponentBase.encodeEnd(UIComponentBase.java:836)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.faces.renderkit.html_basic.HtmlBasicRenderer.encodeRecursive(HtmlBasicRenderer.java:279)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.faces.renderkit.html_basic.TableRenderer.encodeBegin(TableRenderer.java:157)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; javax.faces.component.UIComponentBase.encodeBegin(UIComponentBase.java:788)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; javax.faces.component.UIData.encodeBegin(UIData.java:879)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.RendererBase.renderChild(RendererBase.java:280)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.RendererBase.renderChildren(RendererBase.java:262)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.html.AjaxOutputPanelRenderer.encodeChildren(AjaxOutputPanelRenderer.java:78)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; javax.faces.component.UIComponentBase.encodeChildren(UIComponentBase.java:812)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.RendererBase.renderChild(RendererBase.java:282)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.AjaxChildrenRenderer.encodeAjaxComponent(AjaxChildrenRenderer.java:124)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.AjaxChildrenRenderer.encodeAjaxChildren(AjaxChildrenRenderer.java:67)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.AjaxChildrenRenderer.encodeAjaxComponent(AjaxChildrenRenderer.java:115)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.AjaxChildrenRenderer.encodeAjaxChildren(AjaxChildrenRenderer.java:67)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.AjaxChildrenRenderer.encodeAjaxComponent(AjaxChildrenRenderer.java:115)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.renderkit.AjaxContainerRenderer.encodeAjax(AjaxContainerRenderer.java:123)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.component.AjaxViewRoot.encodeAjax(AjaxViewRoot.java:682)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.component.AjaxViewRoot.encodeChildren(AjaxViewRoot.java:553)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; javax.faces.component.UIComponent.encodeAll(UIComponent.java:886)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.facelets.FaceletViewHandler.renderView(FaceletViewHandler.java:592)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.application.ViewHandlerWrapper.renderView(ViewHandlerWrapper.java:108)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.application.AjaxViewHandler.renderView(AjaxViewHandler.java:196)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.faces.lifecycle.RenderResponsePhase.execute(RenderResponsePhase.java:106)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.faces.lifecycle.LifecycleImpl.phase(LifecycleImpl.java:251)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.sun.faces.lifecycle.LifecycleImpl.render(LifecycleImpl.java:144)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; javax.faces.webapp.FacesServlet.service(FacesServlet.java:245)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.StubSecurityHelper$ServletServiceAction.run(StubSecurityHelper.java:227)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.StubSecurityHelper.invokeServlet(StubSecurityHelper.java:125)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.ServletStubImpl.execute(ServletStubImpl.java:283)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.TailFilter.doFilter(TailFilter.java:26)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.FilterChainImpl.doFilter(FilterChainImpl.java:42)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter$FilterChainImpl.doFilter(SeamFilter.java:83)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.tydic.sso.client.filter.UrlFilter.verifyUrl(UrlFilter.java:124)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.tydic.sso.client.filter.UrlFilter.doFilter(UrlFilter.java:113)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; com.tydic.sso.client.filter.AbstractUrlFilter4Seam.doFilter(AbstractUrlFilter4Seam.java:42)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter$FilterChainImpl.doFilter(SeamFilter.java:69)   
&#160;&#160;&#160;&#16
  
0;&#160;&#160;&#160; org.jboss.seam.web.MultipartFilter.doFilter(MultipartFilter.java:85)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter$FilterChainImpl.doFilter(SeamFilter.java:69)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.web.RedirectFilter.doFilter(RedirectFilter.java:45)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter$FilterChainImpl.doFilter(SeamFilter.java:69)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.web.ExceptionFilter.doFilter(ExceptionFilter.java:64)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter$FilterChainImpl.doFilter(SeamFilter.java:69)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.webapp.BaseXMLFilter.doXmlFilter(BaseXMLFilter.java:177)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.webapp.BaseFilter.handleRequest(BaseFilter.java:267)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.webapp.BaseFilter.processUploadsAndHandleRequest(BaseFilter.java:380)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.ajax4jsf.webapp.BaseFilter.doFilter(BaseFilter.java:507)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.web.Ajax4jsfFilter.doFilter(Ajax4jsfFilter.java:60)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter$FilterChainImpl.doFilter(SeamFilter.java:69)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.web.LoggingFilter.doFilter(LoggingFilter.java:58)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter$FilterChainImpl.doFilter(SeamFilter.java:69)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; org.jboss.seam.servlet.SeamFilter.doFilter(SeamFilter.java:158)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.FilterChainImpl.doFilter(FilterChainImpl.java:42)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.WebAppServletContext$ServletInvocationAction.run(WebAppServletContext.java:3242)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.security.acl.internal.AuthenticatedSubject.doAs(AuthenticatedSubject.java:321)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.security.service.SecurityManager.runAs(SecurityManager.java:121)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.WebAppServletContext.securedExecute(WebAppServletContext.java:2010)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.WebAppServletContext.execute(WebAppServletContext.java:1916)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.servlet.internal.ServletRequestImpl.run(ServletRequestImpl.java:1366)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.work.ExecuteThread.execute(ExecuteThread.java:209)   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; weblogic.work.ExecuteThread.run(ExecuteThread.java:181)   
>

&#160;

**解决方案:** WebLogic 默认的超时参数是600秒, 导致处理结果无法正常返回. 如何修改此超时设置?   
答案: [http://download.oracle.com/docs/cd/E13222_01/wls/docs92/ConsoleHelp/taskhelp/tuning/TuningExecuteThreads.html](http://download.oracle.com/docs/cd/E13222_01/wls/docs92/ConsoleHelp/taskhelp/tuning/TuningExecuteThreads.html "http://download.oracle.com/docs/cd/E13222_01/wls/docs92/ConsoleHelp/taskhelp/tuning/TuningExecuteThreads.html")   
中文版: 调整阻塞线程检测行为 <http://edocs.weblogicfans.net/wls/docs92/ConsoleHelp/taskhelp/tuning/TuningExecuteThreads.html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic JSP Servlet 线程超时设置参数](http://www.beansoft.biz/2010/10/09/weblogic-jsp-servlet-%e7%ba%bf%e7%a8%8b%e8%b6%85%e6%97%b6%e8%ae%be%e7%bd%ae%e5%8f%82%e6%95%b0/)