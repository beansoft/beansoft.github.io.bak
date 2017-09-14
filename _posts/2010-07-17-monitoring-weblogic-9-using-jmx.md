---
id: 364
title: Monitoring WebLogic 9 using JMX
date: 2010-07-17T17:49:28+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=364
permalink: /2010/07/17/monitoring-weblogic-9-using-jmx/
views:
  - "6722"
original_post_id:
  - "364"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - JMX
  - Monitor
  - WebLogic
---
From: <http://www.performanceengineer.com/blog/monitoring-weblogic-using-jmx/> 

<span class="Apple-style-span" style="word-spacing:0;font:medium simsun;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:12px;color:rgb(102,102,102);font-family:verdana, arial, helvetica, sans-serif;"> </p> 

<h2 style="font-size:16px;color:rgb(0,116,158);line-height:20px;margin:0;padding:0;">
  <a title="Permanent Link: Monitoring WebLogic using JMX" style="color:rgb(0,116,158);text-decoration:none;" href="http://www.performanceengineer.com/blog/monitoring-weblogic-using-jmx/" rel="bookmark">Monitoring WebLogic using JMX</a>
</h2>

<p>
  <abbr title="2007-03-16T13:29:00-0700">March 16, 2007 – 1:29 pm</abbr>
</p>

<p>
  It&#8217;s not as straightforward as you might think or expect, but once setup, gives a lot more insight into the behavior of your applications. Use your favorite<span class="Apple-converted-space">&#160;</span><a class="IMM_Glossary_-_Trigger A" id="8" title="JMX" style="border-top-width:0;border-left-width:0;color:rgb(0,116,158);border-bottom:1px solid;border-right-width:0;text-decoration:none;padding:0;" href="http://www.performanceengineer.com/blog/monitoring-weblogic-using-jmx/#">JMX</a><span class="Apple-converted-space">&#160;</span>client (jconsole, jManage, SiteScope, MC4J, etc.) to monitor thread pools, database connections, memory usage and any other MBean attributes.
</p>

<p>
  There are two ways (that I know of) to enable a WebLogic application for monitoring using JMX.
</p>

<ul>
  <li>
    Enable IIOP and default user for the WebLogic server
  </li>
  <li>
    Use the Java 5 JMX remote capabilities
  </li>
</ul>

<h4>
  Enable IIOP and default user for the WebLogic server
</h4>

<h5>
  Step 1: Enable Anonymous Admin Lookup
</h5>

<p>
  From the<span class="Apple-converted-space">&#160;</span><a style="color:rgb(0,116,158);text-decoration:none;" href="http://e-docs.bea.com/wls/docs92/secmanage/domain.html#wp1174144">WebLogic documentation</a>:
</p>

<p>
  <em>The Anonymous Admin Lookup Enabled option specifies whether anonymous, read-only access to WebLogic Server MBeans should be allowed from the MBean API. With this anonymous access, you can see the value of any MBean attribute that is not explicitly marked as protected by the Weblogic Server MBean authorization process. This option is enabled by default to assure backward compatibility. For greater security, you should disable this anonymous access.</em>
</p>

<p>
  To verify the setting of the Anonymous Admin Lookup Enabled option through the WebLogic Administration Console, see the Domain: Security: General page in the Administration Console or the SecurityConfigurationMBean.AnonymousAdminLookupEnabled attribute.
</p>

<h5>
  Step 2: Enable IIOP Protocol for Admin Server and Application Servers
</h5>

<ul>
  <li>
    In the Server Settings&#8217; Protocol tab, check "Enable IIOP"
  </li>
  <li>
    Enter the Default IIOP Username and Default IIOP Password.
  </li>
</ul>

<p>
  If you don&#8217;t do this, you will get an error similar to the following when you try to establish an rmi connection: <br />org.omg.CORBA.NO_PERMISSION: User does not have permission on weblogic.management.mbeanservers to perform lookup operation. vmcid: 0 completed: No
</p>

<p>
  Then you can use the JMX URL to connect to an individual application server: <br />service:jmx:rmi:///jndi/iiop://127.0.0.1:7001/weblogic.management.mbeanservers.runtime
</p>

<p>
  or if you connect to the Admin server, you can view the MBeans for all the servers in the cluster using this URL: <br />service:jmx:rmi:///jndi/iiop://127.0.0.1:7001/weblogic.management.mbeanservers.domainruntime
</p>

<p>
  See also:<span class="Apple-converted-space">&#160;</span><a style="color:rgb(0,116,158);text-decoration:none;" href="http://edocs.bea.com/wls/docs92/ConsoleHelp/taskhelp/channels/EnableAndConfigureIIOP.html" target="_blank">Enable and configure IIOP</a>
</p>

<h4>
  Use Java 5 JMX remote
</h4>

<p>
  Add the following command-line options to the start script for the WebLogic server you want to monitor: <br />-Dcom.sun.management.jmxremote <br />-Dcom.sun.management.jmxremote.port=8888 <br />-Dcom.sun.management.jmxremote.ssl=false <br />-Dcom.sun.management.jmxremote.authenticate=false
</p>

<p>
  Then, you can connect using this JMX URL: <br />service:jmx:rmi:///jndi/rmi://127.0.0.1:8888/jmxrmi <br />and you will got not only the com.bea MBeans, but all of the Java 5 MBeans, also.
</p>

<h4>
  Troubleshooting
</h4>

<p>
  If there are a large number of MBeans in your monitored application, you may run into a problem using Windows where the IIOP connection will timeout. You may see an error like this:
</p>

<pre>Internal communication failed. (in getResults) org.omg.CORBA.COMM_FAILURE:
vmcid: SUN  minor code: 208 completed: Maybe</pre>

<p>
  In this case you can set the com.sun.CORBA.transport.ORBTCPReadTimeouts property to adjust the transport read tcp timeout property, which is a colon separated property with the following syntax.
</p>

<pre>&lt;initial time to wait: max read giop header time to wait: max read message time to wait: backoff factor&gt;</pre>

<p>
  If you are getting this error, then you can add this option to the jconsole command line, adjusting the 2nd value higher as needed. This example sets the timeout to 30 seconds:
</p>

<pre>jconsole -J-Dcom.sun.CORBA.transport.ORBTCPReadTimeouts=10:30000:500:10</pre>

<h4>
  Incorporating into LoadRunner
</h4>

<p>
  Once you have enabled the JMX monitors, you can then incorporate this data into your LoadRunner test scenarios using SiteScope. SiteScope is an agent-less monitoring tool that actually comes bundled with LoadRunner and is free (up to 500 monitoring "points") for non-production use.
</p>

<p>
  </span></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/07/17/monitoring-weblogic-9-using-jmx/">Monitoring WebLogic 9 using JMX</a>
</p>