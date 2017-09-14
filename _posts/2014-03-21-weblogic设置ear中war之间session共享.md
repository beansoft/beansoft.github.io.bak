---
id: 3576
title: WebLogic实现不同web应用之间的Session共享(非SSO)
date: 2014-03-21T12:37:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3576
permalink: '/2014/03/21/weblogic%e8%ae%be%e7%bd%aeear%e4%b8%adwar%e4%b9%8b%e9%97%b4session%e5%85%b1%e4%ba%ab/'
views:
  - "12385"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - WebLogic
  - 会话复制
---
<font style="font-size: 12pt">本文系转载, 来源: <a title="http://blog.csdn.net/gaohaiyang/article/details/7407897" href="http://blog.csdn.net/gaohaiyang/article/details/7407897">http://blog.csdn.net/gaohaiyang/article/details/7407897</a> 您也可参考下列文章: <a title="http://maping930883.blogspot.jp/2009/03/wls056earwebsession.html" href="http://maping930883.blogspot.jp/2009/03/wls056earwebsession.html">http://maping930883.blogspot.jp/2009/03/wls056earwebsession.html</a></font>

<font style="font-size: 12pt">由J2EE Servlet规范中，可以知道，正常情况下war之间session是彼此独立的，不可以共享的。 <br />但是现在大部分J2EE服务器，都实现了EAR中war之间的session共享，如weblogic(>=9)、websphere。</font>

<font style="font-size: 12pt">设置weblogic的EAR中war之间session共享有下面两种方法：</font>

<font style="font-size: 12pt">1：设置EAR中的weblogic-application.xml文件，加入如下片段：</font>

<font style="font-size: 12pt">&#160;&#160;&#160; <wls:session-descriptor> <br />&#160; <wls:persistent-store-type>memory</wls:persistent-store-type> <br />&#160; <wls:sharing-enabled>true</wls:sharing-enabled> <br /></wls:session-descriptor> <br />&#160; <br />整个weblogic-application.xml内容如下： <br /><?xml version="1.0" encoding="UTF-8"?> <br /><wls:weblogic-web-app xmlns:wls="</font><font style="font-size: 12pt"><a href="http://www.bea.com/ns/weblogic/90"><font color="#0066cc">http://www.bea.com/ns/weblogic/90</font></a>" xmlns:xsi="<a href="http://www.w3.org/2001/XMLSchema-instance"><font color="#0066cc">http://www.w3.org/2001/XMLSchema-instance</font></a>" xsi:schemaLocation="<a href="http://java.sun.com/xml/ns/j2ee"><font color="#0066cc">http://java.sun.com/xml/ns/j2ee</font></a> <a href="http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"><font color="#0066cc">http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd</font></a> <a href="http://www.bea.com/ns/weblogic/90"><font color="#0066cc">http://www.bea.com/ns/weblogic/90</font></a> <a href="http://www.bea.com/ns/weblogic/90/weblogic-web-app.xsd"><font color="#0066cc">http://www.bea.com/ns/weblogic/90/weblogic-web-app.xsd</font></a>"> <br />&#160;&#160;&#160; <wls:weblogic-version>10.0</wls:weblogic-version> <br />&#160;&#160;&#160; <wls:context-root>testEARweb2</wls:context-root> <br /></font><font style="font-size: 12pt"><strong><span style="color: "><font color="#ff0000">&#160;&#160;&#160; <wls:session-descriptor> <br />&#160; <wls:persistent-store-type>memory</wls:persistent-store-type> <br />&#160; <wls:sharing-enabled>true</wls:sharing-enabled> <br /></wls:session-descriptor></font></span></strong> <br /></wls:weblogic-web-app></font>

<font style="font-size: 12pt">2.设置需要共享session的war内的weblogic.xml文件，例如testEAR内有两个war，testEARweb1和testEARweb2，想让这两个war之间session共享， <br />则需要设置这两个war里面的weblogic.xml文件，同样，加入下面片段即可： <br />&#160;&#160;&#160; <wls:session-descriptor> <br />&#160; <wls:persistent-store-type>memory</wls:persistent-store-type> <br />&#160; <wls:sharing-enabled>true</wls:sharing-enabled> <br /></wls:session-descriptor> <br />设置后testEARweb1的weblogic.xml内容如下：</font>

<font style="font-size: 12pt"><?xml version="1.0" encoding="UTF-8"?> <br /><wls:weblogic-web-app xmlns:wls="</font><font style="font-size: 12pt"><a href="http://www.bea.com/ns/weblogic/90"><font color="#0066cc">http://www.bea.com/ns/weblogic/90</font></a>" xmlns:xsi="<a href="http://www.w3.org/2001/XMLSchema-instance"><font color="#0066cc">http://www.w3.org/2001/XMLSchema-instance</font></a>" xsi:schemaLocation="<a href="http://java.sun.com/xml/ns/j2ee"><font color="#0066cc">http://java.sun.com/xml/ns/j2ee</font></a> <a href="http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"><font color="#0066cc">http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd</font></a> <a href="http://www.bea.com/ns/weblogic/90"><font color="#0066cc">http://www.bea.com/ns/weblogic/90</font></a> <a href="http://www.bea.com/ns/weblogic/90/weblogic-web-app.xsd"><font color="#0066cc">http://www.bea.com/ns/weblogic/90/weblogic-web-app.xsd</font></a>"> <br />&#160;&#160;&#160; <wls:weblogic-version>10.0</wls:weblogic-version> <br />&#160;&#160;&#160; <wls:context-root>testEARweb1</wls:context-root> <br /><span style="color: "><font color="#ff0000">&#160;&#160; </font></span><strong><span style="color: "><font color="#ff0000"><wls:session-descriptor> <br />&#160; <wls:persistent-store-type>memory</wls:persistent-store-type> <br />&#160; <wls:sharing-enabled>true</wls:sharing-enabled> <br /></wls:session-descriptor></font></span> <br /></strong></wls:weblogic-web-app> <br />&#160; <br />testEARweb2的weblogic.xml内容如下：&#160; <br /><?xml version="1.0" encoding="UTF-8"?> <br /><wls:weblogic-web-app xmlns:wls="<a href="http://www.bea.com/ns/weblogic/90"><font color="#0066cc">http://www.bea.com/ns/weblogic/90</font></a>" xmlns:xsi="<a href="http://www.w3.org/2001/XMLSchema-instance"><font color="#0066cc">http://www.w3.org/2001/XMLSchema-instance</font></a>" xsi:schemaLocation="<a href="http://java.sun.com/xml/ns/j2ee"><font color="#0066cc">http://java.sun.com/xml/ns/j2ee</font></a> <a href="http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"><font color="#0066cc">http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd</font></a> <a href="http://www.bea.com/ns/weblogic/90"><font color="#0066cc">http://www.bea.com/ns/weblogic/90</font></a> <a href="http://www.bea.com/ns/weblogic/90/weblogic-web-app.xsd"><font color="#0066cc">http://www.bea.com/ns/weblogic/90/weblogic-web-app.xsd</font></a>"> <br />&#160;&#160;&#160; <wls:weblogic-version>10.0</wls:weblogic-version> <br />&#160;&#160;&#160; <wls:context-root>testEARweb2</wls:context-root> <br />&#160;&#160; </font><font style="font-size: 12pt"><strong><span style="color: "><font color="#ff0000"><wls:session-descriptor> <br />&#160; <wls:persistent-store-type>memory</wls:persistent-store-type> <br />&#160; <wls:sharing-enabled>true</wls:sharing-enabled> <br /></wls:session-descriptor></font> <br /></span></strong></wls:weblogic-web-app></font>

<font style="font-size: 12pt">这样，EAR内的war之间就可以共享session了。</font>

<font style="font-size: 12pt">对于WAS，需要设置ibm-application-ext.xmi文件，</font>

<font style="font-size: 12pt"><applicationext:ApplicationExtension xmi:version="2.0" xmlns:xmi="</font><font style="font-size: 12pt"><a href="http://www.omg.org/XMI"><font color="#0066cc">http://www.omg.org/XMI</font></a>" xmlns:applicationext="applicationext.xmi" xmlns:application="application.xmi" xmlns:xsi="<a href="http://www.w3.org/2001/XMLSchema-instance"><font color="#0066cc">http://www.w3.org/2001/XMLSchema-instance</font></a></font><font style="font-size: 12pt">" xmi:id="Application_ID_Ext" sharedSessionContext="true">&#160; </font>

<font style="font-size: 12pt">其中sharedSessionContext="true",就是说明要开启共享session。</font>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic实现不同web应用之间的Session共享(非SSO)](http://www.beansoft.biz/2014/03/21/weblogic%e8%ae%be%e7%bd%aeear%e4%b8%adwar%e4%b9%8b%e9%97%b4session%e5%85%b1%e4%ba%ab/)