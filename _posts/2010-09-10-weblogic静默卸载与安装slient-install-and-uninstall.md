---
id: 1055
title: 'WebLogic静默卸载与安装[Slient Install and Uninstall]'
date: 2010-09-10T19:08:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1055
permalink: '/2010/09/10/weblogic%e9%9d%99%e9%bb%98%e5%8d%b8%e8%bd%bd%e4%b8%8e%e5%ae%89%e8%a3%85slient-install-and-uninstall/'
views:
  - "15058"
original_post_id:
  - "1055"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
Uninstall 卸载:

set WL\_HOME=C:\bea\wlserver\_10.3   
cd %WL_HOME%\uninstall   
uninstall.cmd -mode=silent

Install 安装:

C:\BEA\wls1033\_win32.exe -mode=silent -silent\_xml=C:\BEA\silent.xml

**silent.xml:**

<div id="codeSnippetWrapper">
  <div style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: #f4f4f4; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px" id="codeSnippet">
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: white; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
<span style="COLOR: #0000ff">&lt;?</span><span style="COLOR: #800000">xml</span> <span style="COLOR: #ff0000">version</span><span style="COLOR: #0000ff">="1.0"</span> <span style="COLOR: #ff0000">encoding</span><span style="COLOR: #0000ff">="UTF-8"</span>?<span style="COLOR: #0000ff">&gt;</span>
</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: #f4f4f4; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
 
</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: white; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
<span style="COLOR: #008000">&lt;!-- Silent installer option: -mode=silent -silent_xml=/home/me/silent.xml --&gt;</span>
</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: #f4f4f4; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
<span style="COLOR: #0000ff">&lt;</span><span style="COLOR: #800000">domain-template-descriptor</span><span style="COLOR: #0000ff">&gt;</span> 
</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: white; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
<span style="COLOR: #0000ff">&lt;</span><span style="COLOR: #800000">input-fields</span><span style="COLOR: #0000ff">&gt;</span> 
</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: #f4f4f4; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
   <span style="COLOR: #0000ff">&lt;</span><span style="COLOR: #800000">data-value</span> <span style="COLOR: #ff0000">name</span><span style="COLOR: #0000ff">="BEAHOME"</span> <span style="COLOR: #ff0000">value</span><span style="COLOR: #0000ff">="C:\bea"</span> <span style="COLOR: #0000ff">/&gt;</span> 
</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: white; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
<span style="COLOR: #0000ff">&lt;/</span><span style="COLOR: #800000">input-fields</span><span style="COLOR: #0000ff">&gt;</span> 
</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="BORDER-BOTTOM-STYLE: none; TEXT-ALIGN: left; PADDING-BOTTOM: 0px; LINE-HEIGHT: 12pt; BORDER-RIGHT-STYLE: none; BACKGROUND-COLOR: #f4f4f4; MARGIN: 0em; PADDING-LEFT: 0px; WIDTH: 100%; PADDING-RIGHT: 0px; FONT-FAMILY: 'Courier New', courier, monospace; DIRECTION: ltr; BORDER-TOP-STYLE: none; COLOR: black; FONT-SIZE: 8pt; BORDER-LEFT-STYLE: none; OVERFLOW: visible; PADDING-TOP: 0px">
<span style="COLOR: #0000ff">&lt;/</span><span style="COLOR: #800000">domain-template-descriptor</span><span style="COLOR: #0000ff">&gt;</span>
</pre>
    
    <p>
      <!--CRLF--></div>
    </p>
  </div>
  
  <p>
    Ref:
  </p>
  
  <p>
    Silent Install
  </p>
  
  <p>
    <a href="http://download.oracle.com/docs/cd/E14571_01/doc.1111/e14142/silent.htm#i1083883" title="http://download.oracle.com/docs/cd/E14571_01/doc.1111/e14142/silent.htm#i1083883">http://download.oracle.com/docs/cd/E14571_01/doc.1111/e14142/silent.htm#i1083883</a>
  </p>
  
  <p>
    Silent Uninstall
  </p>
  
  <p>
    <a href="http://download.oracle.com/docs/cd/E14571_01/doc.1111/e14142/uninstal.htm#WLSIG145">http://download.oracle.com/docs/cd/E14571_01/doc.1111/e14142/uninstal.htm#WLSIG145</a>
  </p>
  
  <p>
    转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/10/weblogic%e9%9d%99%e9%bb%98%e5%8d%b8%e8%bd%bd%e4%b8%8e%e5%ae%89%e8%a3%85slient-install-and-uninstall/">WebLogic静默卸载与安装[Slient Install and Uninstall]</a>
  </p>