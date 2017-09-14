---
id: 667
title: IBM Thread and Monitor Dump Analyzer for Java Download
date: 2010-09-03T12:30:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=667
permalink: /2010/09/03/ibm-thread-and-monitor-dump-analyzer-for-java-download/
views:
  - "9454"
original_post_id:
  - "667"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
---
IBM Thread and Monitor Dump Analyzer for Java is a _tool that allows identification of hangs, deadlocks, resource contention, and bottlenecks in Java threads._

Offcial download address: <http://www.alphaworks.ibm.com/tech/jca>, required an IBM site account.

Mirror: <http://cid-519b3f7aa2172030.office.live.com/self.aspx/Public/WebLogic/jca401.zip>

Date Posted: April 5, 2006

Update: June 16, 2010   
Version 4.0.1 provides thread dump detection enhancement.

#### What is IBM Thread and Monitor Dump Analyzer for Java?

During the run time of a Java™ process, some Java Virtual Machiness (JVMs) may not respond predictably and oftentimes seem to hang up for a long time or until JVM shutdown occurs. It is not easy to determine the root cause of these sorts of problems.

By triggering a _javacore_ when a Java process does not respond, it is possible to collect diagnostic information related to the JVM and a Java application captured at a particular point during execution. For example, the information can be about the operating system, the application environment, threads, native stack, locks, and memory. The exact contents are dependent on the platform on which the application is running.

On some platforms, and in some cases, javacore is known as "javadump." The code that creates javacore is part of the JVM. One can control it by using environment variables and run-time switches. By default, a javacore occurs when the JVM terminates unexpectedly. A javacore can also be triggered by sending specific signals to the JVM. Although javacore or javadump is present in Sun Solaris JVMs, much of the content of the javacore is added by IBM and, therefore, is present only in IBM JVMs.

IBM Thread and Monitor Dump Analyzer for Java analyzes javacore and diagnoses monitor locks and thread activities in order to identify the root cause of hangs, deadlocks, and resource contention or monitor bottlenecks.

#### How does it work?

This technology analyzes each thread information and provides diagnostic information, such as current thread information, the signal that caused the javacore, Java heap information (maximum Java heap size, initial Java heap size, garbage collector counter, allocation failure counter, free Java heap size, and allocated Java heap size), number of runnable threads, total number of threads, number of monitors locked, and deadlock information.

In addition, IBM Thread and Monitor Dump Analyzer for Java provides the recommended size of the Java heap cluster (applicable only to IBM SDK 1.4.2 and 1.3.1 SR7 or above) based on the heuristic analysis engine.

IBM Thread and Monitor Dump Analyzer for Java compares each javacore and provides process ID information for threads, time stamp of the first javacore, time stamp of the last javacore, number of garbage collections per minute, number of allocation failures per minute, time between the first javacore and the last javacore, number of hang suspects, and list of hang suspects.

This technology also compares all monitor information in javacore and detects deadlock and resource contention or monitor bottlenecks, if there are any.

Please see this [Webcast replay: Analysis of hangs, deadlocks, and resource contention or monitor bottlenecks using IBM Thread and Monitor Dump Analyzer for Java](http://www-1.ibm.com/support/docview.wss?uid=swg27011855).

Read Jinwoo Hwang&#8217;s article ["How to Diagnose Java Resource Starvation: Using the IBM Thread & Monitor Dump Analyzer for Java technology."](http://java.sys-con.com/node/921279)

Read Jinwoo Hwang&#8217;s article ["Anatomy of a Java Finalizer"](http://java.sys-con.com/node/995699) in the Java Developer&#8217;s Journal.

![](http://1qwoyq.bay.livefilestore.com/y1pEINd9dnf2U6Oy5Y5atOLWxdO04QDckOX60xFZDJRynnB8m4Ir_LHDI5f1ZdDoymmPXB_VMFCuY2DLhoa05V0E320dMwWwqxA/jca01.jpg?psid=1)

![](http://1qwoyq.bay.livefilestore.com/y1pSVWjeFmYLJ6_wdAjc3b6FVnqi--R5XUeLsY-VNMmKq_TnMZpxEthNvW9Goe7Pix5x8cRiwpR6HotiUn3xzf2ew/jca02.jpg?psid=1)

![](http://1qwoyq.bay.livefilestore.com/y1pSVWjeFmYLJ6ceaFhsyXFFmw53Jl_qRSuURXpDAqWzLB6CF80fuwQcy0y0K0z9A3_4ZI9-0SpBxJPlhJwg-id3g/jca03.jpg?psid=1)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [IBM Thread and Monitor Dump Analyzer for Java Download](http://www.beansoft.biz/2010/09/03/ibm-thread-and-monitor-dump-analyzer-for-java-download/)