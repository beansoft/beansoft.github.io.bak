---
id: 3377
title: '<!--:zh-->ThreadLogic简介<!--:--><!--:en-->Introducing ThreadLogic<!--:-->'
date: 2013-02-04T20:10:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3377
permalink: /2013/02/04/introducing-threadlogic/
views:
  - "4322"
categories:
  - WebLogic 监控
tags:
  - ThreadLogic
  - WebLogic
---
<!--:zh-->Eric Gross 和Sabha Parameswaran, 来自Oracle FMW 架构组 (The A-team), 开发了 

[ThreadLogic 工具](http://java.net/projects/threadlogic), 一款开源的 Thread Dump 分析工具, 提供给 Oracle 融合中间件社区及客户.  他们的官方博客地址是: [https://blogs.oracle.com/ATeamExalogic/entry/introducing_threadlogic](https://blogs.oracle.com/ATeamExalogic/entry/introducing_threadlogic "https://blogs.oracle.com/ATeamExalogic/entry/introducing_threadlogic") **ThreadLogic**和普通TDA工具的区别在于它添加了很多针对WebLogic的分析报告.

<div>
  Complete support for Hotpsot/IBM/Jrockit & WLST generated thread dumps and numerous additional improvements/advisories
</div>

**Motivation behind ThreadLogic**

The current set of TDA tools (Samurai/TDA) do not mine the thread dumps. Neither do they provide a more detailed view of what each thread is doing. Most of the existing tools tend to limit themselves to reporting the state (locked/waiting/running) or the lock information.  They don&#8217;t go into details of the type of activity within a thread, should it be treated as normal or deserving a closer look? Can a pattern or anti-pattern be applied against them? Any possible optimizations? Are there any hot spots? Any classification of threads based on their execution cycles?

We decided to create ThreadLogic to address these deficiencies. It is based on a fork of the [TDA](http://java.net/projects/tda/) open source tool with new capabilities to analyze and provide advice based on a set of extensible advisories and thread grouping while supporting all JVM thread dumps. Also, a thorough and in-depth analysis of WebLogic Server thread dumps is provided. Both the thread grouping and advisories are extensible where user can add new patterns to match and tag or group threads. Please check the attached document for more details of the tool.

The latest stable bits (version 0.9) and documentation can be downloaded from [here](http://java.net/projects/threadlogic/downloads).  For more details on the tool&#8217;s capabilities, please check the [documentation page.](http://java.net/projects/threadlogic/downloads/download/ThreadLogic-v0.9.pdf)

Our hope is that this tool would go a long way in improving and helping both internal teams (Support/Dev/Field) and external customers in terms of better analysis and faster issue resolutions.

Feedback welcome.

ThreadLogic 运行时截图:

<img style="display: inline; border-width: 0px;" title="image" src="http://www.beansoft.biz/wp-content/uploads/2013/02/image.png" alt="image" width="547" height="416" border="0" />

ThreadLogic的诊断报告:

Thread Group Name

**Rest of WLS**

Thread Group Health

**IGNORE** 

Total Number of threads

**15**

Number of threads blocked for locks

****

Number of busy (not waiting or blocked) threads

**5**

Number of Hot Patterns Found

**1**

33% of threads are running Healthy (not waiting or blocked).

33% of Threads in this thread group exhibit a pattern of executing same code paths tagged as Hot Patterns.

This implies multiple threads are executing the same code path and can be affected by locks, synchronization, resource constraints.

or resources limits as part of the same code path execution.

**Critical Advisories (WATCH, WARNING or FATAL levels) Found**

Thread Advisory Name

**Hot Spots**

Health Level

**WATCH** 

Keyword

**HotCallPattern**

Description

**Multiple Threads executing same code path**

Advice

**Ensure there are no blocking locks or bottlenecks, sufficient resources are available.**

Remote service being invoked is responsive and scaling well to handle increased load.

Use custom Work Manager and dispatch policy to avoid thread starvation or to use dedicated threads for execution<!--:-->

<!--:en-->Eric Gross and Sabha Parameswaran, from Oracle FMW Architects Team (The A-team) are happy to introduce 

[ThreadLogic](http://java.net/projects/threadlogic), an open source Thread Dump Analyzer, to Oracle Fusion Middleware community and customers.  Their blog is: [https://blogs.oracle.com/ATeamExalogic/entry/introducing_threadlogic](https://blogs.oracle.com/ATeamExalogic/entry/introducing_threadlogic "https://blogs.oracle.com/ATeamExalogic/entry/introducing_threadlogic")

<div>
  Complete support for Hotpsot/IBM/Jrockit & WLST generated thread dumps and numerous additional improvements/advisories
</div>

**Motivation behind ThreadLogic**

The current set of TDA tools (Samurai/TDA) do not mine the thread dumps. Neither do they provide a more detailed view of what each thread is doing. Most of the existing tools tend to limit themselves to reporting the state (locked/waiting/running) or the lock information.  They don&#8217;t go into details of the type of activity within a thread, should it be treated as normal or deserving a closer look? Can a pattern or anti-pattern be applied against them? Any possible optimizations? Are there any hot spots? Any classification of threads based on their execution cycles?

We decided to create ThreadLogic to address these deficiencies. It is based on a fork of the [TDA](http://java.net/projects/tda/) open source tool with new capabilities to analyze and provide advice based on a set of extensible advisories and thread grouping while supporting all JVM thread dumps. Also, a thorough and in-depth analysis of WebLogic Server thread dumps is provided. Both the thread grouping and advisories are extensible where user can add new patterns to match and tag or group threads. Please check the attached document for more details of the tool.

The latest stable bits (version 0.9) and documentation can be downloaded from [here](http://java.net/projects/threadlogic/downloads).  For more details on the tool&#8217;s capabilities, please check the [documentation page.](http://java.net/projects/threadlogic/downloads/download/ThreadLogic-v0.9.pdf)

&nbsp;

Our hope is that this tool would go a long way in improving and helping both internal teams (Support/Dev/Field) and external customers in terms of better analysis and faster issue resolutions.

Feedback welcome.

Here is the screenshot of ThreadLogic:

[<img style="background-image: none; padding-left: 0px; padding-right: 0px; display: inline; padding-top: 0px; border: 0px;" title="threadLogic" src="http://www.beansoft.biz/wp-content/uploads/2013/08/threadLogic_thumb.png" alt="threadLogic" width="1339" height="698" border="0" />](http://www.beansoft.biz/wp-content/uploads/2013/08/threadLogic.png)

And this is a report generated by ThreadLogic:

Thread Group Name

**Rest of WLS**

Thread Group Health

**IGNORE** 

Total Number of threads

**15**

Number of threads blocked for locks

****

Number of busy (not waiting or blocked) threads

**5**

Number of Hot Patterns Found

**1**

33% of threads are running Healthy (not waiting or blocked).

33% of Threads in this thread group exhibit a pattern of executing same code paths tagged as Hot Patterns.

This implies multiple threads are executing the same code path and can be affected by locks, synchronization, resource constraints.

or resources limits as part of the same code path execution.

**Critical Advisories (WATCH, WARNING or FATAL levels) Found**

Thread Advisory Name

**Hot Spots**

Health Level

**WATCH** 

Keyword

**HotCallPattern**

Description

**Multiple Threads executing same code path**

Advice

**Ensure there are no blocking locks or bottlenecks, sufficient resources are available.**

Remote service being invoked is responsive and scaling well to handle increased load.

Use custom Work Manager and dispatch policy to avoid thread starvation or to use dedicated threads for execution<!--:-->

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [<!--:zh-->ThreadLogic简介

<!--:-->

<!--:en-->Introducing ThreadLogic

<!--:-->](http://www.beansoft.biz/2013/02/04/introducing-threadlogic/)