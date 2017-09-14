---
id: 1170
title: weblogic如何强制先加载web-inf/lib下的jar
date: 2010-09-13T19:39:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1170
permalink: '/2010/09/13/weblogic%e5%a6%82%e4%bd%95%e5%bc%ba%e5%88%b6%e5%85%88%e5%8a%a0%e8%bd%bdweb-inflib%e4%b8%8b%e7%9a%84jar/'
views:
  - "8592"
original_post_id:
  - "1170"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
此问题很常见且棘手, 解决方式如下:

**方法1:**

修改WEB-INF/weblogic.xml (如果没有此文件需要先创建), 并加入下列代码: **<prefer-web-inf-classes>true</prefer-web-inf-classes>**

一段完整示例代码如下(WebLogic 8):

<div id="codeSnippetWrapper">
  <div id="codeSnippet" style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: #f4f4f4; text-align: left; border-style: none; padding: 0;">
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: white; text-align: left; border-style: none; margin: 0; padding: 0;"><span style="color: #0000ff;">&lt;?</span><span style="color: #800000;">xml</span> <span style="color: #ff0000;">version</span><span style="color: #0000ff;">="1.0"</span> <span style="color: #ff0000;">encoding</span><span style="color: #0000ff;">="UTF-8"</span>?<span style="color: #0000ff;">&gt;</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: #f4f4f4; text-align: left; border-style: none; margin: 0; padding: 0;"></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: white; text-align: left; border-style: none; margin: 0; padding: 0;"><span style="color: #0000ff;">&lt;!</span><span style="color: #800000;">DOCTYPE</span> <span style="color: #ff0000;">weblogic-web-app</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: #f4f4f4; text-align: left; border-style: none; margin: 0; padding: 0;">  <span style="color: #ff0000;">PUBLIC</span> <span style="color: #0000ff;">"-//BEA Systems, Inc.//DTD Web Application 8.1//EN"</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: white; text-align: left; border-style: none; margin: 0; padding: 0;">  <span style="color: #0000ff;">"http://www.bea.com/servers/wls810/dtd/weblogic810-web-jar.dtd"</span><span style="color: #0000ff;">&gt;</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: #f4f4f4; text-align: left; border-style: none; margin: 0; padding: 0;"></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: white; text-align: left; border-style: none; margin: 0; padding: 0;"><span style="color: #0000ff;">&lt;</span><span style="color: #800000;">weblogic-web-app</span><span style="color: #0000ff;">&gt;</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: #f4f4f4; text-align: left; border-style: none; margin: 0; padding: 0;"></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: white; text-align: left; border-style: none; margin: 0; padding: 0;">  <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">container-descriptor</span><span style="color: #0000ff;">&gt;</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: #f4f4f4; text-align: left; border-style: none; margin: 0; padding: 0;">    <span style="color: #0000ff;">&lt;</span><span style="color: #800000;">prefer-web-inf-classes</span><span style="color: #0000ff;">&gt;</span>true<span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">prefer-web-inf-classes</span><span style="color: #0000ff;">&gt;</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: white; text-align: left; border-style: none; margin: 0; padding: 0;">  <span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">container-descriptor</span><span style="color: #0000ff;">&gt;</span></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: #f4f4f4; text-align: left; border-style: none; margin: 0; padding: 0;"></pre>
    
    <p>
      &nbsp;
    </p>
    
    <pre style="font-size: 8pt; overflow: visible; width: 100%; color: black; direction: ltr; line-height: 12pt; font-family: 'Courier New', courier, monospace; background-color: white; text-align: left; border-style: none; margin: 0; padding: 0;"><span style="color: #0000ff;">&lt;/</span><span style="color: #800000;">weblogic-web-app</span><span style="color: #0000ff;">&gt;</span></pre>
    
    <p>
      &nbsp;
    </p>
  </div>
</div>

**方法2:**

修改 startWebLogic.cmd/.sh 将这些类库置于CLASSPATH的最前端.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [weblogic如何强制先加载web-inf/lib下的jar](http://www.beansoft.biz/2010/09/13/weblogic%e5%a6%82%e4%bd%95%e5%bc%ba%e5%88%b6%e5%85%88%e5%8a%a0%e8%bd%bdweb-inflib%e4%b8%8b%e7%9a%84jar/)