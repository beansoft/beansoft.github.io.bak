---
id: 1303
title: 'Spring IntrospectorCleanupListener 解决内存泄露问题[整理]'
date: 2010-10-10T20:45:58+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1303
permalink: '/2010/10/10/spring-introspectorcleanuplistener-%e8%a7%a3%e5%86%b3%e5%86%85%e5%ad%98%e6%b3%84%e9%9c%b2%e9%97%ae%e9%a2%98%e6%95%b4%e7%90%86/'
views:
  - "7412"
original_post_id:
  - "1303"
categories:
  - Spring
---
长期运行, Spring 会产生内存泄露, 可尝试如下方法解决:

In **web.xml**, add following line:

<div id="codeSnippetWrapper">
  <div style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;padding:0;" id="codeSnippet">
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">&lt;</span><span style="color:#800000;">listener</span><span style="color:#0000ff;">&gt;</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    <span style="color:#0000ff;">&lt;</span><span style="color:#800000;">listener-class</span><span style="color:#0000ff;">&gt;</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        org.springframework.web.util.IntrospectorCleanupListener</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    <span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">listener-class</span><span style="color:#0000ff;">&gt;</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">&lt;/</span><span style="color:#800000;">listener</span><span style="color:#0000ff;">&gt;</span></pre>
    
    <p>
      <!--CRLF--></div> </div> 
      
      <p>
        转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/10/10/spring-introspectorcleanuplistener-%e8%a7%a3%e5%86%b3%e5%86%85%e5%ad%98%e6%b3%84%e9%9c%b2%e9%97%ae%e9%a2%98%e6%95%b4%e7%90%86/">Spring IntrospectorCleanupListener 解决内存泄露问题[整理]</a>
      </p>