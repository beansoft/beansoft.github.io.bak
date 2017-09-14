---
id: 2225
title: WLST快速创建单机Domain
date: 2011-08-30T21:17:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2225
permalink: '/2011/08/30/wlst%e5%88%9b%e5%bb%ba%e5%8d%95%e6%9c%badomain/'
views:
  - "3397"
original_post_id:
  - "2225"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - WLST
---
readTemplate(&#8216;C:/bea/wlserver_10.3/common/templates/domains/wls.jar&#8217;) 

cd(&#8216;Servers/AdminServer&#8217;)   
set(&#8216;ListenAddress&#8217;,&#8221;)   
set(&#8216;ListenPort&#8217;, 7001) 

cd(&#8216;/&#8217;)   
cd(&#8216;Security/base_domain/User/weblogic&#8217;)   
cmo.setPassword(&#8216;weblogic&#8217;) 

setOption(&#8216;CreateStartMenu&#8217;, &#8216;true&#8217;)   
setOption(&#8216;ServerStartMode&#8217;, &#8216;dev&#8217;)   
setOption(&#8216;JavaHome&#8217;,&#8217;C:/bea/jrockit\_160\_05&#8242;)   
setOption(&#8216;OverwriteDomain&#8217;, &#8216;true&#8217;) 

writeDomain(&#8216;C:/bea/user_projects/domains/mydomain)   
closeTemplate()

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLST快速创建单机Domain](http://www.beansoft.biz/2011/08/30/wlst%e5%88%9b%e5%bb%ba%e5%8d%95%e6%9c%badomain/)