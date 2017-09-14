---
id: 52
title: 'Struts 2 配置拦截所有异常并显示为&#8221;系统模块正在升级中&#8221;'
date: 2009-12-08T14:27:00+00:00
author: 刘长炯
layout: post
guid: http://www.blogjava.net/beansoft/archive/2009/12/08/305158.html
permalink: '/2009/12/08/struts-2-%e9%85%8d%e7%bd%ae%e6%8b%a6%e6%88%aa%e6%89%80%e6%9c%89%e5%bc%82%e5%b8%b8%e5%b9%b6%e6%98%be%e7%a4%ba%e4%b8%baquot%e7%b3%bb%e7%bb%9f%e6%a8%a1%e5%9d%97%e6%ad%a3%e5%9c%a8%e5%8d%87%e7%ba%a7/'
views:
  - "2894"
original_post_id:
  - "52"
categories:
  - Struts
---
如此配置后 即使出现数据库异常 也能捕获并给予友好提示

首先在struts.xml中定义全局的结果和异常映射包, 定义为一个默认的 package
  
<!&#8211; 默认的异常捕捉机制 &#8211;>
  
<package name=&#8221;default&#8221; extends=&#8221;struts-default&#8221;>
  
<global-results>
  
<result name=&#8221;Exception&#8221;>/Exception.jsp</result>
  
</global-results>
  
<global-exception-mappings>
  
<exception-mapping exception=&#8221;java.lang.Exception&#8221; result=&#8221;Exception&#8221;/>
  
</global-exception-mappings>
  
</package>
  
接着修改我们自己的package继承自 default:
  
<!&#8211; 用户模块, 子路径名 /user &#8211; /user/list.do &#8211;>
  
<package name=&#8221;user&#8221; namespace=&#8221;/user&#8221; extends=&#8221;default&#8221;>
  
&#8230;

最后在 Exception.jsp 中写入下面的文字:
  
<%@ page language=&#8221;java&#8221; import=&#8221;java.util.*&#8221; pageEncoding=&#8221;UTF-8&#8243;%>
  
对不起, 系统模块正在升级维护中, 如有疑问, 请联系客服: XXXXXX

<!-- 默认的异常捕捉机制 -->

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Struts 2 配置拦截所有异常并显示为&#8221;系统模块正在升级中&#8221;](http://www.beansoft.biz/2009/12/08/struts-2-%e9%85%8d%e7%bd%ae%e6%8b%a6%e6%88%aa%e6%89%80%e6%9c%89%e5%bc%82%e5%b8%b8%e5%b9%b6%e6%98%be%e7%a4%ba%e4%b8%baquot%e7%b3%bb%e7%bb%9f%e6%a8%a1%e5%9d%97%e6%ad%a3%e5%9c%a8%e5%8d%87%e7%ba%a7/)