---
id: 2747
title: 使用RESTful客户端监控WebLogic 12c
date: 2012-03-28T20:54:56+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2747
permalink: '/2012/03/28/%e4%bd%bf%e7%94%a8restful%e5%ae%a2%e6%88%b7%e7%ab%af%e7%9b%91%e6%8e%a7weblogic-12c/'
views:
  - "5997"
categories:
  - WebLogic 监控
tags:
  - 12c
  - WebLogic
---
### 使用RESTful客户端监控WebLogic 12c

日期：2012-03-28 作者：刘长炯 出处：WebLogic中文博客

#### 前言

众所周知最近几年随着Web 2.0的发展，基于Rest风格的Web服务已经得到了越来越多的支持和认可，例如Amazon AWS也正式提供传统的Web Service之外的Rest服务，Java EE 5也集成进了JSR 311的Rest服务规范。作为云计算时代诞生的WebLogic 12c，也正式在传统的JMX监控方案之外，提供了轻量级的基于Restful传输方案的监控选项，这可以让客户使用脚本语言如JavaScript，Ruby，Perl，PHP，或者使用Flex/Flash等开发监控客户端，或使用移动开发平台搭建12c监控客户端，当然也可以使用Jersey方便的开发相应的客户端。有很多的浏览器插件都支持直接测试Restful Web Service,如Advanced REST client Application，REST Console等。

#### 基础知识

„ 什么是REST?

– Representational State Transfer，表征状态转移

– REST 从资源（由URI确定）的角度来观察整个网络，客户端的应用通过URI来获取资源的表征。用户访问不同的URI时，客户端应用不断地在转变着其状态，即REST。

„ REST的要求

– 客户端和服务器结构

– 连接协议具有无状态性

– 能够利用Cache机制增进性能

– 层次化的系统

– 随需代码 &#8211; Javascript （可选）

„ RESTful Web 服务（也称为 RESTful Web API）是一个使用HTTP并遵循REST原则的Web服务。定义了三种资源：

– URI，比如：http://example.com/resources/。

– Web服务接受与返回的互联网媒体类型，比如：JSON，XML ，YAML 等。

– Web服务在该资源上所支持的一系列请求方法（比如：POST，GET，PUT或DELETE）。

„ 目前Java EE 5中将REST作为规范的一部分实现（JAX-RS），具有官方开源实现Jersey

HTTP 请求方法在RESTful Web 服务中的典型应用： 

<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="top" width="245">
      <p>
        <b>资源</b>
      </p>
    </td>
    
    <td valign="top" width="191">
      <p>
        <b>GET</b>
      </p>
    </td>
    
    <td valign="top" width="159">
      <p>
        <b>PUT</b>
      </p>
    </td>
    
    <td valign="top" width="167">
      <p>
        <b>POST</b>
      </p>
    </td>
    
    <td valign="top" width="127">
      <p>
        <b>DELETE</b>
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="245">
      <p>
        <b>一组资源的URI</b><b>，比如http://svc.com/resources/</b>
      </p>
    </td>
    
    <td valign="top" width="191">
      <p>
        列出 URI，以及该资源组中每个资源的详细信息（后者可选）。
      </p>
    </td>
    
    <td valign="top" width="159">
      <p>
        使用给定的一组资源替换当前整组资源。
      </p>
    </td>
    
    <td valign="top" width="167">
      <p>
        在本组资源中创建/追加一个新的资源。 该操作往往返回新资源的URL。
      </p>
    </td>
    
    <td valign="top" width="127">
      <p>
        删除 整组资源。
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="245">
      <p>
        <b>单个资源的URI</b><b>，比如http://svc.com/resources/142</b>
      </p>
    </td>
    
    <td valign="top" width="191">
      <p>
        获取 指定的资源的详细信息，格式可以自选一个合适的网络媒体类型（比如：XML、JSON等）
      </p>
    </td>
    
    <td valign="top" width="159">
      <p>
        替换/创建 指定的资源。并将其追加到相应的资源组中。
      </p>
    </td>
    
    <td valign="top" width="167">
      <p>
        把指定的资源当做一个资源组，并在其下创建/追加一个新的元素，使其隶属于当前资源。
      </p>
    </td>
    
    <td valign="top" width="127">
      <p>
        删除 指定的元素。
      </p>
    </td>
  </tr>
</table>

下面则列出了一段访问Restful服务的Java客户端代码：

private static WebResource createWebResource(String uriString) {

ClientConfig config = new DefaultClientConfig();

Client client = Client.create(config);

String url = "http://localhost:7001";

URI uri = UriBuilder.fromUri(url + uriString).build();

WebResource service = client.resource(uri);

out.println("run once for JaxRSAdvancedTest &#8211;> " + service);

return service;

}

public void readRestService() {

WebResource service = createWebResource("/management/tenant-monitoring/servers");

String servers = service.path("form").accept(MediaType.TEXT_PLAIN)

.get(String.class, f);

}

#### 可监控的资源类型

WebLogic Server 的下列资源可以使用RESTful 管理服务进行监控:

  * Server – 域中的所有Server实例或者指定的单个Server实例.
  * 集群 –域中的所有集群或者指定的单个集群, 包括集群中的所有Server成员.
  * 应用 –域中的所有应用或者指定的单个应用.
  * 数据源 –域中的所有数据源或者指定的单个数据源.

#### 如何启用Restful监控服务

默认情况下，RESTful 监控服务处于禁用状态。启用步骤如下：<a name="WLACH01107__servers1170039"></a>

1. 在Administration Console的 Change Center, 点击 **Lock & Edit** (相关文档： [使用Change Center](http://download.oracle.com/docs/cd/E24329_01/apirefs.1211/e24401/taskhelp/console/UseTheChangeCenter.html)).

2. 在Console的左侧面板中,Domain Structure下方选择域名称.

<a name="WLACH01107__servers1166348"></a>3. 选择 **Configuration > General**, 然后在页面底部点击 **Advanced**.

4. 选中复选框 **Enable RESTful Management Services**.

<a name="WLACH01107__servers1152668"></a>5. 点击 **Save**.

6. 在Administration Console 的Change Center 中, 点击 **Activate Changes**.

**然后重启管理服务器生效！**

#### 返回的数据展示类型

WebLogic Server RESTful 管理服务支持下面的数据展示类型：

  * JSON
  * XML
  * HTML

客户端可通过指定HTTP头中的Accept信息来获得给定的类型，例如：Accept application/json，Accept application/xml；如果不带任何头信息，则返回HTML。

##### 单个资源的展示格式

###### JSON 格式

下例为单个服务器实例的JSON输出示意：

<pre>{</pre>

<pre>&#160; "body": {</pre>

<pre>&#160;&#160;&#160; "item": {</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // attributes for the item, e.g.</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // "name": "adminserver"</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // "state": "RUNNING",</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // …</pre>

<pre>&#160;&#160;&#160; } </pre>

<pre>&#160; },</pre>

<pre>&#160; "messages": [</pre>

<pre>&#160;&#160;&#160; // an array of messages</pre>

<pre>&#160; ]</pre>

<pre>}</pre>

相关的属性值类型有:

· 字符串, 用双引号分隔 ""

· boolean, true 或 false

· 数字

· null

· 数组, 使用 "[" 和 "]"分隔

· 对象, 使用 "{" 和 "}"分隔

###### <a name="RESTS159"></a><a name="sthref7"></a>XML 格式

单Server XML格式输出示意:

<pre>&lt;?xml version="1.0" encoding="utf-8"?&gt;</pre>

<pre>&lt;data&gt;</pre>

<pre>&lt;object&gt;</pre>

<pre>&#160; &lt;property name="body"&gt;</pre>

<pre>&#160;&#160; &lt;object&gt;</pre>

<pre>&#160;&#160;&#160; &lt;property name="item"&gt;</pre>

<pre>&#160;&#160;&#160;&#160; &lt;object&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160; &lt;!--</pre>

<pre>&#160;&#160;&#160;&#160;&#160; &lt;property name="Name"&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160; &lt;value type="string"&gt;adminserver&lt;/value&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160; &lt;/property&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160; // other properties</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160; --&gt;</pre>

<pre>&#160;&#160;&#160;&#160; &lt;/object&gt; </pre>

<pre>&#160;&#160;&#160; &lt;/property&gt;</pre>

<pre>&#160;&#160; &lt;/object&gt;</pre>

<pre>&#160; &lt;/property&gt;</pre>

<pre>&#160; &lt;property name="messages"&gt;</pre>

<pre>&#160;&#160; &lt;array&gt;</pre>

<pre>&#160;&#160;&#160; &lt;!-- message objects --&gt;</pre>

<pre>&#160;&#160; &lt;/array&gt;</pre>

<pre>&#160;&#160; &lt;/property&gt;</pre>

<pre>&lt;/object&gt;</pre>

<pre>&lt;/data&gt;</pre>

###### <a name="RESTS160"></a><a name="sthref8"></a>HTML 格式

HTML格式以列表的方式显示属性和取值，建议只用于测试和调试。下图为一个示例输出:

<a name="RESTS161"></a><a name="sthref9"></a><img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="clip_image001" border="0" alt="clip_image001" src="http://www.beansoft.biz/wp-content/uploads/2012/03/clip_image001.jpg" width="678" height="378" />

##### 集合资源的展示格式

###### <a name="RESTS163"></a><a name="sthref11"></a>JSON 格式

<pre>{</pre>

<pre>"body": {</pre>

<pre>&#160; "items": [</pre>

<pre>&#160;&#160;&#160; {</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // attributes for item 1</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // "name": "adminserver"</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // "state": "RUNNING",</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // …</pre>

<pre>&#160;&#160;&#160;&#160; },</pre>

<pre>&#160;&#160;&#160; {</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // attributes for item 2</pre>

<pre>&#160;&#160;&#160;&#160; },</pre>

<pre>&#160;&#160;&#160;&#160; …</pre>

<pre>&#160;&#160;&#160; {</pre>

<pre>&#160;&#160;&#160;&#160;&#160; // attributes for item n</pre>

<pre>&#160;&#160;&#160;&#160; }</pre>

<pre>&#160;&#160;&#160; ],</pre>

<pre>&#160;&#160; "messages": [</pre>

<pre>&#160;&#160;&#160; ]</pre>

<pre>}</pre>

###### <a name="RESTS164"></a><a name="sthref12"></a>XML 格式

<pre>&lt;?xml version="1.0" encoding="utf-8"?&gt;</pre>

<pre>&lt;data&gt;</pre>

<pre>&#160; &lt;object&gt;</pre>

<pre>&#160;&#160;&#160; &lt;property name="body"&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160; &lt;object&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;property name="items"&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;array&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;!--</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;object&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;property name="name"&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;value type="string"&gt;adminserver&lt;/value&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;/property&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; // other properties</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;/object&gt;</pre>

<pre></pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; // other items</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; --&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;/array&gt; </pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;/property&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160; &lt;/object&gt;</pre>

<pre>&#160;&#160;&#160; &lt;/property&gt;</pre>

<pre>&#160;&#160;&#160; &lt;property name="messages"&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160; &lt;array&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;!--</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;object&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;property name="severity"&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;value type="string"&gt;WARNING&lt;/value&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;/property&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;property name="message"&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;value type="string"&gt;Server ms1 is not running.&lt;/value&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; &lt;/property&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160; &lt;/object&gt;</pre>

<pre></pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160; // other messages</pre>

<pre>&#160;&#160;&#160;&#160;&#160;&#160; --&gt;</pre>

<pre>&#160;&#160;&#160;&#160;&#160; &lt;/array&gt;</pre>

<pre>&#160;&#160;&#160; &lt;/property&gt;&#160;&#160;&#160;&#160;&#160; </pre>

<pre>&#160; &lt;/object&gt;</pre>

<pre>&lt;/data&gt;</pre>

###### <a name="RESTS165"></a><a name="sthref13"></a>HTML 格式

<img style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="clip_image002" border="0" alt="clip_image002" src="http://www.beansoft.biz/wp-content/uploads/2012/03/clip_image002.jpg" width="503" height="295" />

#### 监控资源列表

##### `域中的所有服务器```

`访问地址：` `http(s)://`_host:port_`/management/tenant-monitoring/servers`

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td valign="bottom">
      <p>
        <b>属性</b>
      </p>
    </td>
    
    <td valign="bottom">
      <p>
        <b>类型</b>
      </p>
    </td>
    
    <td valign="bottom">
      <p>
        <b>有效值</b>
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        name
      </p>
    </td>
    
    <td valign="top">
      <p>
        string
      </p>
    </td>
    
    <td valign="top">
      <p>
        Name of the server.
      </p>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        state
      </p>
    </td>
    
    <td valign="top">
      <p>
        string
      </p>
    </td>
    
    <td valign="top">
      <p>
        Server status. Possible states are:
      </p>
      
      <ul>
        <li>
          RUNNING
        </li>
        <li>
          STARTING
        </li>
        <li>
          STANDBY
        </li>
        <li>
          ADMIN
        </li>
        <li>
          RESUMING
        </li>
        <li>
          SHUTDOWN
        </li>
      </ul>
    </td>
  </tr>
  
  <tr>
    <td valign="top">
      <p>
        health
      </p>
    </td>
    
    <td valign="top">
      <p>
        string
      </p>
    </td>
    
    <td valign="top">
      <p>
        Server health state. Possible health states are:
      </p>
      
      <ul>
        <li>
          HEALTH_OK
        </li>
        <li>
          HEALTH_WARN
        </li>
        <li>
          HEALTH_CRITICAL
        </li>
        <li>
          HEALTH_FAILED
        </li>
        <li>
          HEALTH_OVERLOADED
        </li>
        <li>
          UNKNOWN
        </li>
      </ul>
    </td>
  </tr>
</table>

示例JSON格式输出:

{

"body": {

"items": [

{

"name": "adminserver",

"state": "RUNNING",

"health": " HEALTH_OK "

},

{

"name": "ms1",

"state": "SHUTDOWN",

"health": ""

}

],

},

"messages": [

] 

}

更多监控点信息请访问官方edoc: 

<http://docs.oracle.com/cd/E24329_01/web.1211/e26722/toc.htm>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [使用RESTful客户端监控WebLogic 12c](http://www.beansoft.biz/2012/03/28/%e4%bd%bf%e7%94%a8restful%e5%ae%a2%e6%88%b7%e7%ab%af%e7%9b%91%e6%8e%a7weblogic-12c/)