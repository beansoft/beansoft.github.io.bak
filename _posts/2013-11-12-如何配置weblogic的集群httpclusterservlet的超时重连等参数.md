---
id: 3466
title: 如何配置WebLogic的集群HttpClusterServlet的超时重连等参数
date: 2013-11-12T19:45:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3466
permalink: '/2013/11/12/%e5%a6%82%e4%bd%95%e9%85%8d%e7%bd%aeweblogic%e7%9a%84%e9%9b%86%e7%be%a4httpclusterservlet%e7%9a%84%e8%b6%85%e6%97%b6%e9%87%8d%e8%bf%9e%e7%ad%89%e5%8f%82%e6%95%b0/'
views:
  - "3821"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Cluster
  - WebLogic
---
[http://docs.oracle.com/cd/E17904_01/web.1111/e13709/setup.htm](http://docs.oracle.com/cd/E17904_01/web.1111/e13709/setup.htm "http://docs.oracle.com/cd/E17904_01/web.1111/e13709/setup.htm")

可配置的参数包括 ConnectTimeoutSecs ConnectRetrySecs 等. 另一篇文档参考: [http://docs.oracle.com/cd/E14571\_01/web.1111/e16435/plugin\_params.htm](http://docs.oracle.com/cd/E14571_01/web.1111/e16435/plugin_params.htm "http://docs.oracle.com/cd/E14571_01/web.1111/e16435/plugin_params.htm")

&#160;

<p class="titleintable">
  <font face="宋体"><font style="font-size: 12pt">Table 10-1 Proxy Servlet Deployment Parameter</font></font>
</p>

<table dir="ltr" class="HRuleFormal" title="Proxy Servlet Deployment Parameter" border="1" rules="rows" cellspacing="0" summary="This table shows key parameters for configuring the behavior of the proxy servlet in web.xml" cellpadding="3" width="100%" frame="hsides">
  <colgroup> <col width="20%" /> <col /></colgroup> <tr valign="top" align="left">
    <th id="r1c1-t12" valign="bottom" width="20%" align="left">
      <font face="宋体"><font style="font-size: 12pt">Parameter</font></font>
    </th>
    
    <th id="r1c2-t12" valign="bottom" align="left">
      <font face="宋体"><font style="font-size: 12pt">Usage</font></font>
    </th>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r2c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">WebLogicCluster 
</font></pre>
    </td>
    
    <td headers="r2c1-t12 r1c2-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt;
   &lt;param-name&gt;WebLogicCluster&lt;/param-name&gt;
   &lt;param-value&gt;WLS1.com:<span class="italic">port</span>|WLS2.com:<span class="italic">port</span>
&lt;/param-value&gt;
</font></pre>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Where </font></font><font style="font-size: 12pt"><code>WLS1.com</code><font face="宋体"> and </font><code>WLS2.com</code></font><font face="宋体"><font style="font-size: 12pt"> are the host names of servers in the cluster, and <span class="italic">port</span> is a port where the host is listening for HTTP requests.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">If you are using SSL between the plug-in and WebLogic Server, set the port number to the SSL listen port (see </font></font><font style="font-size: 12pt"><a href="http://docs.oracle.com/cd/E17904_01/apirefs.1111/e13952/taskhelp/channels/ConfigureListenPorts.html"><font color="#0066cc" face="宋体">"Configuring the Listen Port"</font></a><font face="宋体">) and set the </font><code>SecureProxy</code></font><font face="宋体"><font style="font-size: 12pt"> parameter to ON.</font></font>
      </p>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r3c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">SecureProxy 
</font></pre>
    </td>
    
    <td headers="r3c1-t12 r1c2-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt; 
    &lt;param-name&gt;SecureProxy&lt;/param-name&gt; 
   &lt;param-value&gt;<span class="italic">ParameterValue</span>&lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Valid values are ON and OFF.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">If you are using SSL between the plug-in and WebLogic Server, set the port number to the SSL listen port (see </font></font><font style="font-size: 12pt"><a href="http://docs.oracle.com/cd/E17904_01/apirefs.1111/e13952/taskhelp/channels/ConfigureListenPorts.html"><font color="#0066cc" face="宋体">"Configuring the Listen Port"</font></a><font face="宋体">) and set the </font><code>SecureProxy</code></font><font face="宋体"><font style="font-size: 12pt"> parameter to ON.</font></font>
      </p>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r4c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">DebugConfigInfo 
</font></pre>
    </td>
    
    <td headers="r4c1-t12 r1c2-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt; 
    &lt;param-name&gt;DebugConfigInfo&lt;/param-name&gt; 
   &lt;param-value&gt;<span class="italic">ParameterValue</span>&lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Valid values are ON and OFF.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">If set to ON, you can query the </font></font><font style="font-size: 12pt"><code>HttpClusterServlet</code><font face="宋体"> for debugging information by adding a request parameter of </font><code>?__WebLogicBridgeConfig</code><font face="宋体"> to any request. (Note: There are two underscore ( _ ) characters after the ?.) For security reasons, it is recommended that you set the </font><code>DebugConfigInfo</code></font><font face="宋体"><font style="font-size: 12pt"> parameter to OFF in a production environment.</font></font>
      </p>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r5c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">ConnectRetrySecs 
</font></pre>
    </td>
    
    <td headers="r5c1-t12 r1c2-t12" align="left">
      <p>
        <font face="宋体"><font style="font-size: 12pt">Interval in seconds that the servlet will sleep between attempts to connect to a server instance. Assign a value less than </font></font><font style="font-size: 12pt"><code>ConnectTimeoutSecs</code></font><font face="宋体"><font style="font-size: 12pt">.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">The number of connection attempts the servlet makes before returning an </font></font><font style="font-size: 12pt"><code>HTTP 503/Service Unavailable</code><font face="宋体"> response to the client is </font><code>ConnectTimeoutSecs</code><font face="宋体"> divided by </font><code>ConnectRetrySecs</code></font><font face="宋体"><font style="font-size: 12pt">.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Syntax:</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt;
   &lt;param-name&gt;ConnectRetrySecs&lt;/param-name&gt; 
   &lt;param-value&gt;<span class="italic">ParameterValue</span>&lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r6c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">ConnectTimeoutSecs 
</font></pre>
    </td>
    
    <td headers="r6c1-t12 r1c2-t12" align="left">
      <p>
        <font face="宋体"><font style="font-size: 12pt">Maximum time in seconds that the servlet will attempt to connect to a server instance. Assign a value greater than </font></font><font style="font-size: 12pt"><code>ConnectRetrySecs</code></font><font face="宋体"><font style="font-size: 12pt">.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">If </font></font><font style="font-size: 12pt"><code>ConnectTimeoutSecs</code><font face="宋体"> expires before a successful connection, an </font><code>HTTP 503/Service Unavailable</code></font><font face="宋体"><font style="font-size: 12pt"> response is sent to the client.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Syntax:</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt;
&lt;param-name&gt;ConnectTimeoutSecs&lt;/param-name&gt; 
   &lt;param-value&gt;<span class="italic">ParameterValue</span>&lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r7c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">PathTrim 
</font></pre>
    </td>
    
    <td headers="r7c1-t12 r1c2-t12" align="left">
      <p>
        <font face="宋体"><font style="font-size: 12pt">String trimmed by the plug-in from the beginning of the original URL, before the request is forwarded to the cluster.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Syntax:</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt;
&lt;param-name&gt;PathTrim&lt;/param-name&gt; 
   &lt;param-value&gt;<span class="italic">ParameterValue</span>&lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Example:</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">If the URL</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">http://myWeb.server.com/weblogic/foo
</font></pre>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">is passed to the plug-in for parsing and if </font></font><font style="font-size: 12pt"><code>PathTrim</code></font><font face="宋体"><font style="font-size: 12pt"> has been set to</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">/weblogic 
</font></pre>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">the URL forwarded to WebLogic Server is:</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">http://myWeb.server.com:7001/foo
</font></pre>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r8c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">TrimExt 
</font></pre>
    </td>
    
    <td headers="r8c1-t12 r1c2-t12" align="left">
      <p>
        <font face="宋体"><font style="font-size: 12pt">The file extension to be trimmed from the end of the URL.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Syntax:</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt;
&lt;param-name&gt;TrimExt&lt;/param-name&gt; 
   &lt;param-value&gt;<span class="italic">ParameterValue</span>&lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r9c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">clientCertProxy 
</font></pre>
    </td>
    
    <td headers="r9c1-t12 r1c2-t12" align="left">
      <p>
        <font face="宋体"><font style="font-size: 12pt">Specifies to trust client certificates in the </font></font><font style="font-size: 12pt"><code>WL-Proxy-Client-Cert</code></font><font face="宋体"><font style="font-size: 12pt"> header.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">Valid values are true and false. The default value is false.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">This setting is useful if user authentication is performed on the proxy server—setting </font></font><font style="font-size: 12pt"><code>clientCertProxy</code><font face="宋体"> to true causes the proxy server to pass on the certs to the cluster in a special header, </font><code>WL-Proxy-Client-Cert</code></font><font face="宋体"><font style="font-size: 12pt">.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">The </font></font><font style="font-size: 12pt"><code>WL-Proxy-Client-Cert</code></font><font face="宋体"><font style="font-size: 12pt"> header can be used by any client with direct access to WebLogic Server. WebLogic Server takes the certificate information from that header, trusting that is came from a secure source (the plug-in) and uses that information to authenticate the user.</font></font>
      </p>
      
      <p>
        <font face="宋体"><font style="font-size: 12pt">For this reason, if you set </font></font><font style="font-size: 12pt"><code>clientCertProxy</code><font face="宋体"> to true, use a connection filter to ensure that WebLogic Server accepts connections only from the machine on which the plug-in is running. See </font><a class="olink SCPRG377" href="http://docs.oracle.com/cd/E17904_01/web.1111/e13711/con_filtr.htm#SCPRG377"><font color="#0066cc" face="宋体">"Using Network Connection Filters"</font></a></font><font face="宋体"><font style="font-size: 12pt"> in <span class="italic">Programming Security for Oracle WebLogic Server</span>.</font></font>
      </p>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r10c1-t12" width="20%" headers="r1c1-t12" align="left">
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">PathPrepend 
</font></pre>
    </td>
    
    <td headers="r10c1-t12 r1c2-t12" align="left">
      <p>
        <font face="宋体"><font style="font-size: 12pt">String that the servlet prepends to the original URL, after </font></font><font style="font-size: 12pt"><code>PathTrim</code></font><font face="宋体"><font style="font-size: 12pt"> is trimmed, before forwarding the URL to the cluster.</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt;
&lt;param-name&gt;PathPrepend&lt;/param-name&gt; 
   &lt;param-value&gt;<span class="italic">ParameterValue</span>&lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
    </td>
  </tr>
  
  <tr valign="top" align="left">
    <td id="r11c1-t12" width="20%" headers="r1c1-t12" align="left">
      <p>
        <code>&lt;font style="font-size: 12pt">RoutingHandlerClassName&lt;/font></code>
      </p>
    </td>
    
    <td headers="r11c1-t12 r1c2-t12" align="left">
      <p>
        <font face="宋体"><font style="font-size: 12pt">Extends the proxy servlet to support Web service cluster routing. For more information, see </font></font><font style="font-size: 12pt"><a class="olink WSADV299" href="http://docs.oracle.com/cd/E17904_01/web.1111/e13734/cluster.htm#WSADV299"><font color="#0066cc" face="宋体">"Managing Web Services in a Cluster"</font></a></font><font face="宋体"><font style="font-size: 12pt"> in <span class="italic">Programming Advanced Features of JAX-WS Web Services for Oracle WebLogic Server</span>.</font></font>
      </p>
      
      <pre class="oac_no_warn" xml:space="preserve"><font style="font-size: 12pt">&lt;init-param&gt;
&lt;param-name&gt;RoutingHandlerClassName&lt;/param-name&gt; 
   &lt;param-value&gt;
      weblogic.wsee.jaxws.cluster.proxy.SOAPRoutingHandler
   &lt;/param-value&gt; 
&lt;/init-param&gt;
</font></pre>
    </td>
  </tr>
</table>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [如何配置WebLogic的集群HttpClusterServlet的超时重连等参数](http://www.beansoft.biz/2013/11/12/%e5%a6%82%e4%bd%95%e9%85%8d%e7%bd%aeweblogic%e7%9a%84%e9%9b%86%e7%be%a4httpclusterservlet%e7%9a%84%e8%b6%85%e6%97%b6%e9%87%8d%e8%bf%9e%e7%ad%89%e5%8f%82%e6%95%b0/)