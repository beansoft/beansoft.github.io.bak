---
id: 2954
title: 'WLS10:Please enable the DomainRuntimeMBean Server and the Edit MBean Server in this domain&#8217;s configuration'
date: 2012-06-22T22:46:41+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2954
permalink: /2012/06/22/wls10please-enable-the-domainruntimembean-server-and-the-edit-mbean-server-in-this-domains-configuration/
views:
  - "7697"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - WebLogic
  - 故障解决
---
<span style="WIDOWS: 2; TEXT-TRANSFORM: none; TEXT-INDENT: 0px; BORDER-COLLAPSE: separate; FONT: medium Tahoma; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: rgb(0,0,0); WORD-SPACING: 0px; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">weblogic10启动后，输入用户名 密码，提示： <br />已禁用所需的 MBean 服务器，这将阻止 WebLogic 管理控制台的正常操作。 <br />请在该域的配置中启用 DomainRuntimeMBean 服务器和 Edit MBean 服务器。 </p> 

<p>
  请问如何启用DomainRuntimeMBean 服务器和 Edit MBean 服务器？？？</span>
</p>

<div>
  <div>
    <span style="WIDOWS: 2; TEXT-TRANSFORM: none; TEXT-INDENT: 0px; BORDER-COLLAPSE: separate; FONT: medium Tahoma; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: rgb(0,0,0); WORD-SPACING: 0px; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">解决办法：删除config.xml中无效的<app-deployment>元素即可。此种错误的一般原因是config.xml中出现了无效的更改。</span>
  </div>
  
  <div>
    <span style="WIDOWS: 2; TEXT-TRANSFORM: none; TEXT-INDENT: 0px; BORDER-COLLAPSE: separate; FONT: medium Tahoma; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: rgb(0,0,0); WORD-SPACING: 0px; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px">其它可能解决方案请参考：</span>
  </div>
  
  <div>
    <div>
      <span style="WIDOWS: 2; TEXT-TRANSFORM: none; TEXT-INDENT: 0px; BORDER-COLLAPSE: separate; FONT: medium Tahoma; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: rgb(0,0,0); WORD-SPACING: 0px; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"><span style="WIDOWS: 2; TEXT-TRANSFORM: none; TEXT-INDENT: 0px; BORDER-COLLAPSE: separate; FONT: medium Tahoma; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: rgb(0,0,0); WORD-SPACING: 0px; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"><a href="http://weblogicfordummies.blogspot.com/2008/10/wls10please-enable-domainruntimembean.html">http://weblogicfordummies.blogspot.com/2008/10/wls10please-enable-domainruntimembean.html</a></span></span>
    </div>
    
    <div>
      <div>
        <span style="WIDOWS: 2; TEXT-TRANSFORM: none; TEXT-INDENT: 0px; BORDER-COLLAPSE: separate; FONT: medium Tahoma; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: rgb(0,0,0); WORD-SPACING: 0px; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"><span style="WIDOWS: 2; TEXT-TRANSFORM: none; TEXT-INDENT: 0px; BORDER-COLLAPSE: separate; FONT: medium Tahoma; WHITE-SPACE: normal; ORPHANS: 2; LETTER-SPACING: normal; COLOR: rgb(0,0,0); WORD-SPACING: 0px; -webkit-border-horizontal-spacing: 0px; -webkit-border-vertical-spacing: 0px; -webkit-text-decorations-in-effect: none; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px"><a href="https://forums.oracle.com/forums/thread.jspa?threadID=2186455&tstart=0">https://forums.oracle.com/forums/thread.jspa?threadID=2186455&tstart=0</a></span></span>
      </div></p>
    </div></p>
  </div></p>
</div>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2012/06/22/wls10please-enable-the-domainruntimembean-server-and-the-edit-mbean-server-in-this-domains-configuration/">WLS10:Please enable the DomainRuntimeMBean Server and the Edit MBean Server in this domain&#8217;s configuration</a>
</p>