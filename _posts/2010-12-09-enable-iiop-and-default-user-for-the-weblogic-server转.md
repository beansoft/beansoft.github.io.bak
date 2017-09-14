---
id: 1488
title: 'Enable IIOP and default user for the WebLogic server[转]'
date: 2010-12-09T16:58:59+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1488
permalink: '/2010/12/09/enable-iiop-and-default-user-for-the-weblogic-server%e8%bd%ac/'
views:
  - "3651"
original_post_id:
  - "1488"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
  - 转载区
---
作者: Tony Xu 来源: <http://www.tonyxu.net/weblogic/201012397/enable-iiop-weblogic.html> 

Enable IIOP and default user for the WebLogic server是让weblogic应用得到监控的方式之一，操作方法如下：

**1、Enable Anonymous Admin Lookup**

_The Anonymous Admin Lookup Enabled option specifies whether anonymous, read-only access to WebLogic Server MBeans should be allowed from the MBean API. With this anonymous access, you can see the value of any MBean attribute that is not explicitly marked as protected by the Weblogic Server MBean authorization process. This option is enabled by default to assure backward compatibility. For greater security, you should disable this anonymous access._

这里以weblogic923为例：

[<img title="截图12" height="384" alt="截图12" src="http://www.tonyxu.net/wp-content/uploads/2010/12/12_thumb.png" width="839" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/12/12.png)

勾选已启用匿名Admin查找项，保存并激活。

说明：

<a name="security.domain.domainconfiggeneral.securityconfiguration.crossdomainsecurityenabled.label"></a>

指定是否为域启用跨域安全

如果启用跨域安全，则需要添加一个或多个跨域用户，并指定一个凭据映射，该映射包含授权访问此域的每个远程域用户的凭据。

**2、Enable IIOP Protocol for Admin Server and Application Servers**

  * In the Server Settings’ Protocol tab, check “Enable IIOP”
  * Enter the Default IIOP Username and Default IIOP Password.

[<img title="截图13" height="316" alt="截图13" src="http://www.tonyxu.net/wp-content/uploads/2010/12/13_thumb.png" width="948" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/12/13.png)

说明：

<a name="core.server.serverprotocolsiiop.iiopenabled.label"></a>   
<a name="getIIOPEnabled"></a><a name="IIOPEnabled"></a>

指定是否为此服务器的常规（非 SSL）和 SSL 端口都启用了 IIOP 支持。

MBean 特性:   
`<a href="http://192.168.0.57:8001/">ServerMBean.IIOPEnabled</a>`

[更改将在重新部署模块或重新启动服务器后生效。](http://192.168.0.57:8001/console-help/doc/zh-cn/com/bea/wlserver/core/restart.html)

[<img title="截图14" height="162" alt="截图14" src="http://www.tonyxu.net/wp-content/uploads/2010/12/14_thumb.png" width="835" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/12/14.png)

说明：

<a name="core.server.serverprotocolsiiop.defaultiiopuser.label"></a>   
<a name="getDefaultIIOPUser"></a><a name="DefaultIIOPUser"></a>

默认 IIOP 用户的用户名。（需要启用 IIOP。）

MBean 特性:   
`<a href="http://192.168.0.57:8001/">ServerMBean.DefaultIIOPUser</a>`

[更改将在重新部署模块或重新启动服务器后生效。](http://192.168.0.57:8001/console-help/doc/zh-cn/com/bea/wlserver/core/restart.html)

<a name="core.server.serverprotocolsiiop.defaultiioppassword.label"></a>   
<a name="getDefaultIIOPPassword"></a><a name="DefaultIIOPPassword"></a>

默认 IIOP 用户的密码。（需要启用 IIOP。）

自 8.1 sp4 起，获取此属性的值时 WebLogic Server 将执行下列操作：

  1. 检索 `DefaultIIOPPasswordEncrypted` 属性的值。
  2. 将值解密并将解密后的密码以“字符串”形式返回。

使用此属性 (`DefaultIIOPPassword`) 存在潜在的安全风险，因为在垃圾收集删除 String 对象（包含未加密的密码）并重新分配内存之前，该对象仍将位于 JVM 内存中。视 JVM 中的内存分配方式，从内存中删除这些未加密的数据可能要花费很长的时间。

请不要使用此属性，而是使用 `DefaultIIOPPasswordEncrypted`。

MBean 特性:   
`<a href="http://192.168.0.57:8001/">ServerMBean.DefaultIIOPPassword</a>`

[更改将在重新部署模块或重新启动服务器后生效。](http://192.168.0.57:8001/console-help/doc/zh-cn/com/bea/wlserver/core/restart.html)

**3、别忘了重启weblogic server，使设置生效**

通过jconsole进行连接

**service:jmx:rmi:///jndi/iiop://192.168.0.57:8001/weblogic.management.mbeanservers.runtime**

[<img title="截图16" height="691" alt="截图16" src="http://www.tonyxu.net/wp-content/uploads/2010/12/16_thumb.png" width="885" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/12/16.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Enable IIOP and default user for the WebLogic server[转]](http://www.beansoft.biz/2010/12/09/enable-iiop-and-default-user-for-the-weblogic-server%e8%bd%ac/)