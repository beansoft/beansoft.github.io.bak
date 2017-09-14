---
id: 3318
title: 此时不应有 \Java\jre6\lib\ext\QTJava.zip
date: 2012-10-08T17:27:28+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3318
permalink: '/2012/10/08/%e6%ad%a4%e6%97%b6%e4%b8%8d%e5%ba%94%e6%9c%89-javajre6libextqtjava-zip/'
views:
  - "10925"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - JVM
  - WebLogic
---
C:\bea1036\user\_projects\domains\mydomain\bin>C:\bea1036\user\_projects\domains\m   
ydomain\bin\startWebLogic_jprofiler.cmd   
此时不应有 \Java\jre6\lib\ext\QTJava.zip。

E:\Middleware\_Home\user\_projects\domains\first_domain\bin>setDomainEnv.cmd   
\Java\jre6\lib\ext\QTJava.zip was unexpected at this time.

C:\Users\BeanSoft>echo %CLASSPATH%   
.;C:\Program Files (x86)\Java\jre6\lib\ext\QTJava.zip

出错原因: QuickTime，将我的电脑>属性>高级>环境变量中CLASSPATH中的QTJava去掉。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [此时不应有 \Java\jre6\lib\ext\QTJava.zip](http://www.beansoft.biz/2012/10/08/%e6%ad%a4%e6%97%b6%e4%b8%8d%e5%ba%94%e6%9c%89-javajre6libextqtjava-zip/)