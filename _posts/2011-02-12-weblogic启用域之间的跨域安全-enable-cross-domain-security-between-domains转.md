---
id: 1717
title: 'WebLogic启用域之间的跨域安全 Enable Cross Domain Security between domains[转]'
date: 2011-02-12T19:50:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1717
permalink: '/2011/02/12/weblogic%e5%90%af%e7%94%a8%e5%9f%9f%e4%b9%8b%e9%97%b4%e7%9a%84%e8%b7%a8%e5%9f%9f%e5%ae%89%e5%85%a8-enable-cross-domain-security-between-domains%e8%bd%ac/'
views:
  - "7232"
original_post_id:
  - "1717"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
本文转自WebLogic的控制台帮助文档, 任何Console打开后的帮助文档均有此内容.

本文的英文版本: <http://download.oracle.com/docs/cd/E17904_01/apirefs.1111/e13952/taskhelp/security/EnableTrustBetweenDomains.html>

&#160;

   <span class="Apple-style-span" style="word-spacing:0;font:medium 微软雅黑;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"></p> 

<div class="prereq">
  <p class="sectiontitle">
    <b>开始前</b>
  </p>
  
  <p>
    阅读<a href="http://download.oracle.com/docs/cd/E17904_01/web.1111/e13707/domain.htm#SECMG405">启用 WebLogic Server 域之间的跨域安全</a>
  </p></p>
</div>

<div>
  </p> 
  
  <p>
    <a id="WLACH03075__security_7x1180570" name="WLACH03075__security_7x1180570"></a>“跨域安全”可在两个 WebLogic Server 域对之间建立信任，方法是：使用身份证明映射器配置这些 WebLogic Server 域之间的通信。
  </p></p>
</div>

<ol>
  <li>
    如果尚未执行此操作，请在管理控制台的更改中心中单击<b>锁定并编辑</b><span class="Apple-converted-space">&#160;</span>(请参阅<a href="/consolehelp/console-help.portal?_nfpb=true&_pageLabel=page&helpId=console.UseTheChangeCenter">使用更改中心</a>)。
  </li>
  <li>
    <span><a id="WLACH03075__security_7x1180580" name="WLACH03075__security_7x1180580"></a>在左侧窗格中，单击域的名称。</span>
  </li>
  <li>
    <span><a id="WLACH03075__security_7x1182978" name="WLACH03075__security_7x1182978"></a>选择<b>安全</b><span class="Apple-converted-space">&#160;</span>><span class="Apple-converted-space">&#160;</span><b>一般信息</b>。</span>
  </li>
  <li>
    <span><a id="WLACH03075__security_7x1180582" name="WLACH03075__security_7x1180582"></a>选择<b>已启用跨域安全</b>。</span>
  </li>
  <li>
    <span><a id="WLACH03075__security_7x1180585" name="WLACH03075__security_7x1180585"></a>单击<b>保存</b>。</span>
  </li>
  <li>
    <span>在域的安全领域中创建跨域安全用户，并将此用户分配给<span class="Apple-converted-space">&#160;</span><code>CrossDomainConnectors</code><span class="Apple-converted-space">&#160;</span>组。请参阅<a href="/consolehelp/console-help.portal?_nfpb=true&_pageLabel=page&helpId=security.DefineUsers">创建用户</a>和<a href="/consolehelp/console-help.portal?_nfpb=true&_pageLabel=page&helpId=security.AddUsersToGroup">将用户添加到组中</a>。</span>
  </li>
  <li>
    <span>为跨域安全用户配置跨域安全身份证明映射。请参阅<a href="/consolehelp/console-help.portal?_nfpb=true&_pageLabel=page&helpId=security.CreateCrossDomainCredentialMapping">创建跨域安全身份证明映射</a>。</span>
  </li>
  <li>
    要激活这些更改，请在管理控制台的更改中心中单击<b>激活更改</b>。 <br />并非所有更改都立即生效。某些更改必须重新启动后才能生效 (请参阅<a href="/consolehelp/console-help.portal?_nfpb=true&_pageLabel=page&helpId=console.UseTheChangeCenter">使用更改中心</a>)。
  </li>
</ol>

<div class="postreq">
  <p class="sectiontitle">
    <b>完成后</b>
  </p>
  
  <p>
    在要启用跨域安全的每个域中执行相同的过程。
  </p></p>
</div>

<p>
  </span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/02/12/weblogic%e5%90%af%e7%94%a8%e5%9f%9f%e4%b9%8b%e9%97%b4%e7%9a%84%e8%b7%a8%e5%9f%9f%e5%ae%89%e5%85%a8-enable-cross-domain-security-between-domains%e8%bd%ac/">WebLogic启用域之间的跨域安全 Enable Cross Domain Security between domains[转]</a>
</p>