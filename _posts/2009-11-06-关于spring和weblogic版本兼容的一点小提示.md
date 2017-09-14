---
id: 62
title: 关于Spring和WebLogic版本兼容的一点小提示
date: 2009-11-06T14:14:00+00:00
author: 刘长炯
layout: post
guid: http://www.blogjava.net/beansoft/archive/2009/11/06/301429.html
permalink: '/2009/11/06/%e5%85%b3%e4%ba%8espring%e5%92%8cweblogic%e7%89%88%e6%9c%ac%e5%85%bc%e5%ae%b9%e7%9a%84%e4%b8%80%e7%82%b9%e5%b0%8f%e6%8f%90%e7%a4%ba/'
views:
  - "9553"
original_post_id:
  - "62"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - Spring
  - WebLogic
---
<p align="left">
  2009-11-06 关于Spring和WebLogic版本兼容的一点小提示
</p>

<p align="left">
  刘长炯(<a href="mailto:BeanSoft@126.com">BeanSoft@126.com</a>)原创。
</p>

<p align="left">
  首先 WebLogic 的各个版本和 JDK 绑定的很紧, 或者说是专门针对某个 JDK 优化过的代码, 因此, WebLogic 不是说随意修改启动 JDK 都能运行, 高了和低了都不能启动, 举个例子:<br /> WebLogic 8 支持 JDK 1.4, 那么用 JDK 1.5 或者 JDK 1.3 都不能正常启动, 这一点和 Tomcat 是很不一样的.<br /> 为什么要扯这个话题呢? 是因为 Spring 的各个版本也对 JDK 略有限制, 并非各个版本的 Spring 都可以在 WebLogic 上正常运行. 有很多同志还在用 WebLogic 8( JDK 1.4), 那么提醒大家, 现在最新的很多开源框架都是不支持或者不直接支持 JDK 1.4 了, 大部分都需要 JDK 1.5 以上版本, 例如 Spring 2.5, Struts 2(Struts 2 需要一个特殊的包才能跑在 JDK 1.4 上), 至于 JPA, 大家根本不要想它能在 WebLogic 8 上跑, 因为 JPA 依赖于 Java 5 的注解.<br /> 建议用最新版的 WebLogic 来开发项目, 这样BUG和问题都会少的多.<br /> 请参考文末的 Spring 文档的说明: <a href="http://docs.huihoo.com/spring/2.5.x/zh-cn/new-in-2.html">http://docs.huihoo.com/spring/2.5.x/zh-cn/new-in-2.html</a><br /> <strong>Java SE </strong><strong>与</strong><strong> Java EE </strong><strong>支持</strong><br /> Spring Framework继续保持与所有Java版本的兼容性 &#8211; 从Java 1.4.2开始(包括1.4.2)。这意味着spring对Java1.4.2,Java 5和 Java 6都支持， 但是Spring Framework的一些高级功能无法在1.4.2中使用。从Spring 2.5起,Spring框架完全支持Java 6，而Spring 2.0则对Java 5支持比较好。<br /> 此外，Spring延续了对J2EE 1.3及更高版本的兼容性，同时对Java EE 5提供完全支持。也就是说，Spring可以继续在应用服务器中运行，包括 BEA WebLogic 8.1, 9.0, 9.2 和 10, IBM WebSphere 5.1, 6.0 和 6.1, Oracle OC4J 10.1.3 和 11, JBoss 3.2, 4.0 和 4.2, 以及 Tomcat 4.1, 5.0, 5.5 和 6.0, Jetty 4.2, 5.1 和 6.1, Resin 2.1, 3.0 和 3.1 还有 GlassFish V1 和 V2.
</p>

<p align="left">
  <p align="left">
    <p align="left">
      另外 edoc 上也描述了 WebLogic 9 中运行 Spring 可能出现的问题, 地址:<br /> <a href="http://edocs.weblogicfans.net/wl%20...%20esolved.html#spring">http://edocs.weblogicfans.net/wl &#8230; esolved.html#spring</a><br /> 建议大家没事多阅读 edoc&#8230;<br /> WebLogic Server 上的 Spring Framework<br /> WebLogic Server 上的 Spring Framework
    </p>
    
    <p align="left">
      更改请求编号<br /> 描述和变通方法或解决方案<br /> 找到位置<br /> 解决位置
    </p>
    
    <p align="left">
      CR242675<br /> 在 RMI 类加载器中发生了 NullPointerException。<br /> <strong>变通方法或解决方案</strong>：<br /> 请与 BEA 客户支持联系以获取 WebLogic Server/Spring 合并修补程序。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR236708<br /> 在 Hibernate 3 和 WebLogic Server 之间存在 Antlr 冲突。<br /> <strong>变通方法或解决方案</strong>：<br /> 将 Antlr2.7.5.jar 放在 CLASSPATH 中的 weblogic.jar 之前。<br /> 8.1SP05、9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR242923<br /> T3 运行时无法对包含基元类型的类描述符进行解码。<br /> <strong>变通方法或解决方案</strong>：<br /> 请与 BEA 客户支持联系以获取 WebLogic Server-Spring 合并修补程序。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR242883<br /> IIOP 运行时无法对包含基元类型的类描述符进行解码。<br /> <strong>变通方法或解决方案</strong>：<br /> 请与 BEA 客户支持联系以获取 WebLogic Server-Spring 合并修补程序。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR237532<br /> Spring Framework 存在 Web 应用程序类加载问题。<br /> <strong>变通方法或解决方案</strong>：<br /> 请与 BEA 客户支持联系以获取 WebLogic Server-Spring 合并修补程序。<br /> 8.1SP05、9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR241195<br /> 在 Spring Pet Clinic 示例应用程序中更新记录会导致以下错误：<br /> java.lang.IllegalStateException: Cannot access session scope since the<br /> requested page does not participate in a session. at<br /> weblogic.servlet.jsp.PageContextImpl.getAttribute(PageContextImpl.java:273)<br /> at javax.servlet.jsp.jstl.core.Config.get(Config.java:145) at<br /> javax.servlet.jsp.jstl.core.Config.find(Config.java:393) at<br /> org.apache.taglibs.standard.tag.common.fmt.TimeZoneSupport.getTimeZone(TimeZoneSupport.java:140)<br /> <strong>变通方法或解决方案</strong>：<br /> 将 includes.jsp 文件中的第一行标记为注释。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR244683<br /> HP-UX 需要 jdk150_01，而不是 jdk150_03。<br /> <strong>变通方法或解决方案</strong>：<br /> 在 medrec-spring 目录中，使用 jdk150_01 替换 jdk150_03。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR244693<br /> 当您从远程计算机上访问 MedRec-Spring 时，MedRec-Spring 退出功能不起作用。<br /> <strong>变通方法或解决方案</strong>：<br /> 不从远程计算机访问 MedRec-Spring 应用程序，并且不将 localhost 用于请求重定向。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR244691<br /> 对 WebLogic 管理控制台的 Spring 扩展仅支持 Web 应用程序 (.war) 文件，无法用于监视非 .war 文件（如 MedRec-Spring）中的 Spring Bean。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR243957<br /> 使用 CTRL-C 关闭 WebLogic Server 时，如果正在破坏 bean domainMBeanServerConnection，则可能会发生关闭异常。<br /> <strong>变通方法或解决方案</strong>：<br /> 使用标志 -Dweblogic.slc=true 以便确定启动和停止 domainRuntimeServerService 的时间。<br /> 9.0<br /> 9.2
    </p>
    
    <p align="left">
      CR280985<br /> 无法通过将 countries_mbeans.war 应用程序复制到 WebLogic Server 域目录的 autodeploy 目录来自动部署该应用程序。countries_mbeans.war Web 应用程序是一个 Spring 测试扩展应用程序。<br /> <strong>变通方法或解决方案</strong>：<br /> 使用 WebLogic Server 管理控制台来部署 countries_mbeans.war Web 应用程序，而不是自动部署。<br /> 9.2
    </p>
    
    <p align="left">
      CR301115<br /> 在 Spring Pet Clinic 示例应用程序中运行单元测试会导致以下错误：<br /> 从 weblogic.xml.jaxp.RegistrySAXTransformerFactory 中找不到有效的处理器版本实现<br /> <strong>变通方法或解决方案：</strong><strong> </strong><br /> 通过将以下条目添加到 $java.home/lib/jaxp.properties 文件来定义 XML 解析器类：
    </p>
    
    <ul>
      <li>
        javax.xml.transform.TransformerFactory=org.apache.xalan.processor.TransformerFactoryImpl
      </li>
      <li>
        javax.xml.xpath.XPathFactory=org.apache.xpath.jaxp.XPathFactoryImpl
      </li>
      <li>
        javax.xml.parsers.SAXParserFactory=org.apache.xerces.jaxp.SAXParserFactoryImpl
      </li>
      <li>
        javax.xml.parsers.DocumentBuilderFactory=org.apache.xerces.jaxp.DocumentBuilderFactoryImpl
      </li>
    </ul>
    
    <p align="left">
      9.2
    </p>
    
    <p align="left">
      CR300748<br /> 访问部署到 WebLogic Server 9.2 的 tiles-samples 时会出现异常。<br /> 9.2
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p>
      转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2009/11/06/%e5%85%b3%e4%ba%8espring%e5%92%8cweblogic%e7%89%88%e6%9c%ac%e5%85%bc%e5%ae%b9%e7%9a%84%e4%b8%80%e7%82%b9%e5%b0%8f%e6%8f%90%e7%a4%ba/">关于Spring和WebLogic版本兼容的一点小提示</a>
    </p>