---
id: 2306
title: WebLogic Web 应用映射到根目录
date: 2011-11-09T20:20:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2306
permalink: '/2011/11/09/weblogic-web-%e5%ba%94%e7%94%a8%e6%98%a0%e5%b0%84%e5%88%b0%e6%a0%b9%e7%9b%ae%e5%bd%95/'
views:
  - "4254"
original_post_id:
  - "2306"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
修改WEB-INF/weblogic.xml

<div id="codeSnippetWrapper">
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;direction:ltr;line-height:12pt;font-family:&#039;background-color:#f4f4f4;text-align:left;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">&lt;!</span><span style="color:#800000;">DOCTYPE</span> <span style="color:#ff0000;">weblogic-web-app</span> <span style="color:#ff0000;">PUBLIC</span> <span style="color:#0000ff;">"-//BEA<br />Systems, Inc.//DTD Web Application 8.1//EN"</span><br /><span style="color:#0000ff;">"http://www.bea.com/servers/wls810/dtd/weblogic810-web-jar.dtd"</span><span style="color:#0000ff;">&gt;</span><br /><br /><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">weblogic-web-app</span><span style="color:#0000ff;">&gt;</span><br />    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">context-root</span><span style="color:#0000ff;">&gt;</span>/<span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">context-root</span><span style="color:#0000ff;">&gt;</span><br /><span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">weblogic-web-app</span><span style="color:#0000ff;">&gt;</span></pre>
  
  <p>
    </div> 
    
    <p>
      转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/11/09/weblogic-web-%e5%ba%94%e7%94%a8%e6%98%a0%e5%b0%84%e5%88%b0%e6%a0%b9%e7%9b%ae%e5%bd%95/">WebLogic Web 应用映射到根目录</a>
    </p>