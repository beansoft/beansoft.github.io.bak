---
id: 1503
title: '配置基于Coherence 的WebLogic Server会话管理[转]'
date: 2010-12-22T17:45:22+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1503
permalink: '/2010/12/22/%e9%85%8d%e7%bd%ae%e5%9f%ba%e4%ba%8ecoherence-%e7%9a%84weblogic-server%e4%bc%9a%e8%af%9d%e7%ae%a1%e7%90%86%e8%bd%ac/'
views:
  - "8387"
original_post_id:
  - "1503"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
作者: [Yekki](http://www.oraclefmw.com/author/admin/) 来源: <http://www.oraclefmw.com/2010/02/28/%E9%85%8D%E7%BD%AE%E5%9F%BA%E4%BA%8Ecoherence-web%E7%9A%84weblogic-server%E4%BC%9A%E8%AF%9D%E7%AE%A1%E7%90%86/>

&#160;

<span class="Apple-style-span" style="word-spacing:0;font:medium simsun;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:16px;color:rgb(51,51,51);line-height:24px;font-family:georgia, &#039;"> </p> 

<h2 style="clear:both;font-weight:normal;vertical-align:baseline;color:rgb(0,0,0);line-height:1.5em;background-color:transparent;border-width:0;margin:0 0 20px;padding:0;">
  介质版本与补丁
</h2>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  WebLogic Server版本：10.3.2
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  Coherence版本：3.5.2/463
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  注：以上版本不需要打补丁，另外，WebLogic Server 10.3.1也不需要打补丁，其它版本需要打以下补丁：
</p>

<table style="border-right:rgb(231,231,231) 1px solid;border-top:rgb(231,231,231) 1px solid;vertical-align:baseline;border-left:rgb(231,231,231) 1px solid;width:639px;border-bottom:rgb(231,231,231) 1px solid;border-collapse:collapse;background-color:transparent;text-align:left;margin:0 -1px 24px 0;padding:0;" cellspacing="0" cellpadding="2" width="579" border="0">
  <tr style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="133">
      &#160;
    </td>
    
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="133">
      <strong>WebLogic Server 9.2 MP1</strong>
    </td>
    
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="311">
      <strong>WebLogic Server 10.3</strong>
    </td>
  </tr>
  
  <tr style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="133">
      <strong>WebLogic Smart Update</strong>
    </td>
    
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="133">
      <strong>Patch ID: AJQB</strong>
    </td>
    
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="311">
      <strong>Patch ID: 6W2W<br /> </strong>
    </td>
  </tr>
  
  <tr style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="133">
      <strong>Minimum Coherence Release Level/MetaLink Patch ID</strong>
    </td>
    
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="133">
      3.4.2 Patch2 – Patch ID: 8429415
    </td>
    
    <td style="border-top:rgb(231,231,231) 1px solid;border-left-width:0;border-bottom-width:0;vertical-align:baseline;background-color:transparent;border-right-width:0;margin:0;padding:6px 24px;" valign="top" width="311">
      3.4.2 Patch6 – Patch ID: 11399293
    </td>
  </tr>
</table>

<h2 style="clear:both;font-weight:normal;vertical-align:baseline;color:rgb(0,0,0);line-height:1.5em;background-color:transparent;border-width:0;margin:0 0 20px;padding:0;">
  WebLogic Server 配置过程
</h2>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  %COHERENCE_HOME%：Coherence安装目录
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  %DOMAIN_HOME%：用户创建的WebLogic Domain目录
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  1. 创建WebLogic Domain
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  <em>过程略</em>
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  2. 复制%COHERENCE_HOME%libcoherence.jar到%DOMAIN_HOME%lib目录下
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  3. 启动WebLogic Domain
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  4. 部署共享库，此库位于%COHERENCE_HOME%libcoherence-web-spi.war
</p>

<h2 style="clear:both;font-weight:normal;vertical-align:baseline;color:rgb(0,0,0);line-height:1.5em;background-color:transparent;border-width:0;margin:0 0 20px;padding:0;">
  Coherence配置
</h2>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  1. 复制%COHERENCE_HOME%bincache-server.cmd并更名为web-cache-server.cmd
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  2. 修改web-cache-server.cmd，改为以下内容：
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  java -server -Xms512m -Xmx512m -cp %coherence_home%/lib/coherence.jar;%coherence_home%/lib/coherence-web-spi.war -Dtangosol.coherence.management.remote=true -Dtangosol.coherence.cacheconfig=WEB-INF/classes/session-cache-config.xml -Dtangosol.coherence.session.localstorage=true com.tangosol.net.DefaultCacheServer
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  3. 启动web-cache-server.cmd
</p>

<h2 style="clear:both;font-weight:normal;vertical-align:baseline;color:rgb(0,0,0);line-height:1.5em;background-color:transparent;border-width:0;margin:0 0 20px;padding:0;">
  测试
</h2>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  1. 根据上面所讲配置过程分别配置两个WebLogic Domain: domain_a, domain_b
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  2. 用oepe创建应用CoherenceWeb，实现三个功能：
</p>

<ul style="vertical-align:baseline;list-style-type:square;background-color:transparent;border-width:0;margin:0 0 24px 1.5em;padding:0;">
  <li style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    a. 列出Http Session值
  </li>
  <li style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    b. 更改Http Session值
  </li>
  <li style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    c. 清空Http Session
  </li>
</ul>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  详细实现参看“参考代码”
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  3. 修改CoherenceWeb的weblogic.xml文件
</p>

<div class="dp-highlighter" style="font-size:12px;vertical-align:baseline;width:633px;font-family:consolas, &#039;background-color:rgb(231,229,220);border-width:0;margin:18px 0;padding:1px 0 0;">
  <div class="bar" style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0 0 0 45px;">
    <div class="tools" style="border-top-width:0;border-bottom-width:0;font:9px verdana, geneva, arial, helvetica, sans-serif;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;color:silver;background-color:rgb(248,248,248);border-right-width:0;margin:0;padding:3px 8px 10px 10px;">
      <a style="font-size:9px;vertical-align:baseline;color:rgb(160,160,160);background-color:transparent;text-decoration:none;border-width:0;margin:0 10px 0 0;padding:0;" href="http://www.oraclefmw.com/2010/02/28/%E9%85%8D%E7%BD%AE%E5%9F%BA%E4%BA%8Ecoherence-web%E7%9A%84weblogic-server%E4%BC%9A%E8%AF%9D%E7%AE%A1%E7%90%86/#">view plain</a><a style="font-size:9px;vertical-align:baseline;color:rgb(160,160,160);background-color:transparent;text-decoration:none;border-width:0;margin:0 10px 0 0;padding:0;" href="http://www.oraclefmw.com/2010/02/28/%E9%85%8D%E7%BD%AE%E5%9F%BA%E4%BA%8Ecoherence-web%E7%9A%84weblogic-server%E4%BC%9A%E8%AF%9D%E7%AE%A1%E7%90%86/#">copy to clipboard</a><a style="font-size:9px;vertical-align:baseline;color:rgb(160,160,160);background-color:transparent;text-decoration:none;border-width:0;margin:0 10px 0 0;padding:0;" href="http://www.oraclefmw.com/2010/02/28/%E9%85%8D%E7%BD%AE%E5%9F%BA%E4%BA%8Ecoherence-web%E7%9A%84weblogic-server%E4%BC%9A%E8%AF%9D%E7%AE%A1%E7%90%86/#">print</a><a style="font-size:9px;vertical-align:baseline;color:rgb(160,160,160);background-color:transparent;text-decoration:none;border-width:0;margin:0 10px 0 0;padding:0;" href="http://www.oraclefmw.com/2010/02/28/%E9%85%8D%E7%BD%AE%E5%9F%BA%E4%BA%8Ecoherence-web%E7%9A%84weblogic-server%E4%BC%9A%E8%AF%9D%E7%AE%A1%E7%90%86/#">?</a>
    </div></p>
  </div>
  
  <ol class="dp-xml" style="vertical-align:baseline;color:rgb(92,92,92);background-color:rgb(255,255,255);border-width:0;margin:0 0 24px 45px;padding:0;">
    <li class="alt" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(255,255,255);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;"><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><?</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">xml</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;</span><span class="attribute" style="vertical-align:baseline;color:red;background-color:transparent;border-width:0;margin:0;padding:0;">version</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">=</span><span class="attribute-value" style="vertical-align:baseline;color:blue;background-color:transparent;border-width:0;margin:0;padding:0;">"1.0"</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;</span><span class="attribute" style="vertical-align:baseline;color:red;background-color:transparent;border-width:0;margin:0;padding:0;">encoding</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">=</span><span class="attribute-value" style="vertical-align:baseline;color:blue;background-color:transparent;border-width:0;margin:0;padding:0;">"UTF-8"</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">?></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(248,248,248);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;"><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:weblogic-web-app</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;</span><span class="attribute" style="vertical-align:baseline;color:red;background-color:transparent;border-width:0;margin:0;padding:0;">xsi:schemalocation</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">=</span><span class="attribute-value" style="vertical-align:baseline;color:blue;background-color:transparent;border-width:0;margin:0;padding:0;">"http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd http://xmlns.oracle.com/weblogic/weblogic-web-app http://xmlns.oracle.com/weblogic/weblogic-web-app/1.0/weblogic-web-app.xsd"</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;</span><span class="attribute" style="vertical-align:baseline;color:red;background-color:transparent;border-width:0;margin:0;padding:0;">xmlns:xsi</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">=</span><span class="attribute-value" style="vertical-align:baseline;color:blue;background-color:transparent;border-width:0;margin:0;padding:0;">"http://www.w3.org/2001/XMLSchema-instance"</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;</span><span class="attribute" style="vertical-align:baseline;color:red;background-color:transparent;border-width:0;margin:0;padding:0;">xmlns:wls</span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">=</span><span class="attribute-value" style="vertical-align:baseline;color:blue;background-color:transparent;border-width:0;margin:0;padding:0;">"http://xmlns.oracle.com/weblogic/weblogic-web-app"</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="alt" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(255,255,255);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;&#160;&#160; <span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:weblogic-version</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">10.3.2</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"></</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:weblogic-version</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(248,248,248);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;&#160;&#160; <span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:context-root</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">CoherenceWeb</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"></</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:context-root</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="alt" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(255,255,255);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;&#160;&#160; <span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:library-ref</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(248,248,248);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;&#160;&#160;&#160;&#160;&#160;&#160; <span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:library-name</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">coherence-web-spi</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"></</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:library-name</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="alt" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(255,255,255);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;&#160;&#160;&#160;&#160;&#160;&#160; <span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:specification-version</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">1.0.0.0</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"></</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:specification-version</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(248,248,248);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;&#160;&#160;&#160;&#160;&#160;&#160; <span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"><</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:exact-match</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">true</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"></</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:exact-match</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="alt" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(255,255,255);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160;&#160;&#160; <span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"></</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:library-ref</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
    <li class="" style="border-top-width:0;border-bottom-width:0;vertical-align:baseline;border-left:rgb(108,226,108) 3px solid;line-height:14px;background-color:rgb(248,248,248);border-right-width:0;margin:0;padding:0 0 0 10px;">
      <span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;"><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;"></</span><span class="tag-name" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">wls:weblogic-web-app</span><span class="tag" style="font-weight:bold;vertical-align:baseline;color:rgb(0,102,153);background-color:transparent;border-width:0;margin:0;padding:0;">></span><span style="vertical-align:baseline;color:black;background-color:transparent;border-width:0;margin:0;padding:0;">&#160; </span></span>
    </li>
  </ol>
</div>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  4. 将应用CoherenceWeb部署到domain_a与domain_b
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  5. 演示步骤
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  a. 从domain_a上更改session的值
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  b. 查看domain_b上的session的值是否更改
</p>

<p style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0 0 24px;padding:0;">
  参考代码下载 ：<a style="vertical-align:baseline;color:rgb(0,102,204);background-color:transparent;border-width:0;margin:0;padding:0;" href="http://www.oraclefmw.com/download/CoherenceWeb.war">CoherenceWeb.war</a>
</p>

<h2 style="clear:both;font-weight:normal;vertical-align:baseline;color:rgb(0,0,0);line-height:1.5em;background-color:transparent;border-width:0;margin:0 0 20px;padding:0;">
  参考资料
</h2>

<ul style="vertical-align:baseline;list-style-type:square;background-color:transparent;border-width:0;margin:0 0 24px 1.5em;padding:0;">
  <li style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    <a style="vertical-align:baseline;color:rgb(0,102,204);background-color:transparent;border-width:0;margin:0;padding:0;" href="http://www.oracle.com/technology/obe/fusion_middleware/coherence/obe34coherence_wls/coherenceweb_wls_install/coherenceweb_wls_install.htm#t3s1"><em>Using Oracle Coherence*Web 3.4.2 with Oracle WebLogic Server 10gR3</em></a>
  </li>
  <li style="vertical-align:baseline;background-color:transparent;border-width:0;margin:0;padding:0;">
    <a style="vertical-align:baseline;color:rgb(0,102,204);background-color:transparent;border-width:0;margin:0;padding:0;" href="http://www.oracle.com/technology/obe/fusion_middleware/coherence/obe34coherence_wls/coherenceweb_wls_appconfig/coherenceweb_wls_appconfig.htm"><em>Oracle Coherence*Web 3.4.2 with Oracle WebLogic Server 10gR3</em></a>
  </li>
</ul>

<p>
  </span></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/12/22/%e9%85%8d%e7%bd%ae%e5%9f%ba%e4%ba%8ecoherence-%e7%9a%84weblogic-server%e4%bc%9a%e8%af%9d%e7%ae%a1%e7%90%86%e8%bd%ac/">配置基于Coherence 的WebLogic Server会话管理[转]</a>
</p>