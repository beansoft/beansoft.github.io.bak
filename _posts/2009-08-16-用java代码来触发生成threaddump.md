---
id: 227
title: 用Java代码来触发生成ThreadDump
date: 2009-08-16T15:54:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=227
permalink: '/2009/08/16/%e7%94%a8java%e4%bb%a3%e7%a0%81%e6%9d%a5%e8%a7%a6%e5%8f%91%e7%94%9f%e6%88%90threaddump/'
views:
  - "4254"
original_post_id:
  - "227"
categories:
  - Java SE
---
ThreadDump对于JVM诊断和调优是个好东西. 以前, 我们生成ThreadDump, 一般都需要另外连到服务器上的进程管理器才行, 不管是Ctrl+Break还是kill –3, 比较不方便. 有时候, 也许想远程直接生成并检查一下服务器的ThreadDump, 这个怎么办呢? 幸好我们有以下代码可以做到:

**util.threaddump.ThreadDumpBuilder.java**

> package util.threaddump; 
> 
> import java.util.Map; 
> 
> /**   
> * 使用 Java 远程代码生成 ThreadDump. 适用于 JDK 1.5+.   
> * 参考: {@link Thread#getStackTrace()}   
> * {@link Throwable#getStackTrace()}   
> * @see StackTraceElement   
> * @author beansoft@126.com   
> * 转载请注明出处: beansoft.blogjava.net   
> */   
> public class ThreadDumpBuilder {   
> &#160;&#160;&#160; /**   
> &#160;&#160;&#160;&#160; * 生成并返回 Thread Dump.   
> &#160;&#160;&#160;&#160; * 转载请注明出处: beansoft.blogjava.net   
> &#160;&#160;&#160;&#160; * @return   
> &#160;&#160;&#160;&#160; */   
> &#160;&#160;&#160; public String build() {   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; StringBuilder output = new StringBuilder(1000);   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; for (Map.Entry stackTrace : Thread.getAllStackTraces().entrySet()) {   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; appendThreadStackTrace(output, (Thread) stackTrace.getKey(),   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (StackTraceElement[]) stackTrace.getValue());   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; return output.toString();   
> &#160;&#160;&#160; } 
> 
> &#160;&#160;&#160; /**   
> &#160;&#160;&#160;&#160; * 处理并输出堆栈信息.   
> &#160;&#160;&#160;&#160; * @param output   
> &#160;&#160;&#160;&#160; *&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 输出内容   
> &#160;&#160;&#160;&#160; * @param thread   
> &#160;&#160;&#160;&#160; *&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 线程   
> &#160;&#160;&#160;&#160; * @param stack   
> &#160;&#160;&#160;&#160; *&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 线程堆栈   
> &#160;&#160;&#160;&#160; */   
> &#160;&#160;&#160; private void appendThreadStackTrace(StringBuilder output, Thread thread,   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; StackTraceElement[] stack) {   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; // 忽略当前线程的堆栈信息   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; if (thread.equals(Thread.currentThread())) {   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; return;   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; } 
> 
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; output.append(thread).append("n");   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; for (StackTraceElement element : stack) {   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; output.append("t").append(element).append("n");   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
> &#160;&#160;&#160; } 
> 
> }

然后在一个JSP里或者Servlet中任意调用即可:

<%=new ThreadDumpBuilder().build() %>

我用的 Oracle JRocket ReamTime 的JVM跑的空的Tomcat, 输出内容如下: 

> <pre>Thread[(GC Main Thread),5,system]
Thread[Main Thread,5,main]
	java.net.PlainSocketImpl.socketAccept(Native Method)
	java.net.PlainSocketImpl.accept(PlainSocketImpl.java:384)
	java.net.ServerSocket.implAccept(ServerSocket.java:453)
	java.net.ServerSocket.accept(ServerSocket.java:421)
	org.apache.catalina.core.StandardServer.await(StandardServer.java:389)
	org.apache.catalina.startup.Catalina.await(Catalina.java:630)
	org.apache.catalina.startup.Catalina.start(Catalina.java:590)
	sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	java.lang.reflect.Method.invoke(Method.java:597)
	org.apache.catalina.startup.Bootstrap.start(Bootstrap.java:288)
	org.apache.catalina.startup.Bootstrap.main(Bootstrap.java:413)
Thread[TP-Processor1,5,main]
	java.lang.Object.wait(Native Method)
	java.lang.Object.wait(Object.java:485)
	org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:658)
	java.lang.Thread.run(Thread.java:619)
Thread[TP-Processor3,5,main]
	java.lang.Object.wait(Native Method)
	java.lang.Object.wait(Object.java:485)
	org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:658)
	java.lang.Thread.run(Thread.java:619)
Thread[(VM Periodic Task),10,system]
Thread[ContainerBackgroundProcessor[StandardEngine[Catalina]],5,main]
	java.lang.Thread.sleep(Native Method)
	org.apache.catalina.core.ContainerBase$ContainerBackgroundProcessor.run(ContainerBase.java:1579)
	java.lang.Thread.run(Thread.java:619)
Thread[Finalizer,8,system]
	java.lang.Thread.run(Thread.java:619)
Thread[TP-Processor2,5,main]
	java.lang.Object.wait(Native Method)
	java.lang.Object.wait(Object.java:485)
	org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:658)
	java.lang.Thread.run(Thread.java:619)
Thread[Reference Handler,10,system]
	java.lang.ref.Reference.waitForActivatedQueue(Native Method)
	java.lang.ref.Reference.access$100(Reference.java:11)
	java.lang.ref.Reference$ReferenceHandler.run(Reference.java:79)
Thread[(Code Generation Thread 1),5,system]
Thread[TP-Processor4,5,main]
	java.net.PlainSocketImpl.socketAccept(Native Method)
	java.net.PlainSocketImpl.accept(PlainSocketImpl.java:384)
	java.net.ServerSocket.implAccept(ServerSocket.java:453)
	java.net.ServerSocket.accept(ServerSocket.java:421)
	org.apache.jk.common.ChannelSocket.accept(ChannelSocket.java:306)
	org.apache.jk.common.ChannelSocket.acceptConnections(ChannelSocket.java:660)
	org.apache.jk.common.ChannelSocket$SocketAcceptor.runIt(ChannelSocket.java:870)
	org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:686)
	java.lang.Thread.run(Thread.java:619)
Thread[http-8080-Acceptor-0,5,main]
	java.net.PlainSocketImpl.socketAccept(Native Method)
	java.net.PlainSocketImpl.accept(PlainSocketImpl.java:384)
	java.net.ServerSocket.implAccept(ServerSocket.java:453)
	java.net.ServerSocket.accept(ServerSocket.java:421)
	org.apache.tomcat.util.net.DefaultServerSocketFactory.acceptSocket(DefaultServerSocketFactory.java:61)
	org.apache.tomcat.util.net.JIoEndpoint$Acceptor.run(JIoEndpoint.java:310)
	java.lang.Thread.run(Thread.java:619)
Thread[(Signal Handler),5,system]
Thread[(Sensor Event Thread),5,system]
Thread[TP-Monitor,5,main]
	java.lang.Object.wait(Native Method)
	org.apache.tomcat.util.threads.ThreadPool$MonitorRunnable.run(ThreadPool.java:561)
	java.lang.Thread.run(Thread.java:619)
Thread[(Attach Listener),5,system]
Thread[(Code Optimization Thread 1),5,system]</pre>

<pre>对比用 Ctrl + Break 做出的GC, 显然因为有安全性的限制, 输出的日志信息比上面的方式详细的多, 因此这仍然是推荐做法:</pre>

===== FULL THREAD DUMP ===============
    
  
Sun Aug 16 15:37:48 2009

BEA JRockit(R) R27.6.3-40\_o-112056-1.6.0\_11-20090318-2104-windows-ia32 

"Main Thread" id=1 idx=0x4 tid=1760 prio=5 alive, in native
    
  
&#160;&#160;&#160; at java/net/PlainSocketImpl.socketAccept(Ljava/net/SocketImpl;)V(Native Method)

&#160;&#160;&#160; at java/net/PlainSocketImpl.accept(PlainSocketImpl.java:384)

&#160;&#160;&#160; ^&#8211; Holding lock: java/net/SocksSocketImpl@0x017CA398[biased lock]

&#160;&#160;&#160; at java/net/ServerSocket.implAccept(ServerSocket.java:453)

&#160;&#160;&#160; at java/net/ServerSocket.accept(ServerSocket.java:421)

&#160;&#160;&#160; at org/apache/catalina/core/StandardServer.await(StandardServer.java:389)

&#160;&#160;&#160; at org/apache/catalina/startup/Catalina.await(Catalina.java:630)

&#160;&#160;&#160; at org/apache/catalina/startup/Catalina.start(Catalina.java:590)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; at jrockit/vm/Reflect.invokeMethod(Ljava/lang/Object;Ljava/lang/Object;[Ljava/lang/Object;)Ljava/lang/Object;(Native

Method)

&#160;&#160;&#160; at sun/reflect/NativeMethodAccessorImpl.invoke0(Ljava/lang/reflect/Method;Ljava/lang/Object;[Ljava/lang/Object;)Ljav

a/lang/Object;(Native Method)

&#160;&#160;&#160; at sun/reflect/NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)

&#160;&#160;&#160; at sun/reflect/DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)

&#160;&#160;&#160; at java/lang/reflect/Method.invoke(Method.java:597)

&#160;&#160;&#160; at org/apache/catalina/startup/Bootstrap.start(Bootstrap.java:288)

&#160;&#160;&#160; at org/apache/catalina/startup/Bootstrap.main(Bootstrap.java:413)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"(Signal Handler)" id=2 idx=0x8 tid=1368 prio=5 alive, in native, daemon 

"(GC Main Thread)" id=3 idx=0xc tid=1912 prio=5 alive, in native, native_waiting, daemon 

"(GC Worker Thread 1)" id=? idx=0x10 tid=2760 prio=5 alive, in native, daemon 

"(GC Worker Thread 2)" id=? idx=0x14 tid=1432 prio=5 alive, in native, daemon 

"(Code Generation Thread 1)" id=4 idx=0x18 tid=2104 prio=5 alive, in native, native_waiting, daemon 

"(Code Optimization Thread 1)" id=5 idx=0x1c tid=1136 prio=5 alive, in native, native_waiting, daemon 

"(VM Periodic Task)" id=6 idx=0x20 tid=2184 prio=10 alive, in native, daemon 

"(Attach Listener)" id=7 idx=0x24 tid=2464 prio=5 alive, in native, daemon 

"Finalizer" id=8 idx=0x28 tid=2668 prio=8 alive, in native, native_waiting, daemon
    
  
&#160;&#160;&#160; at jrockit/memory/Finalizer.waitForFinalizees([Ljava/lang/Object;)I(Native Method)

&#160;&#160;&#160; at jrockit/memory/Finalizer.access$500(Finalizer.java:12)

&#160;&#160;&#160; at jrockit/memory/Finalizer$4.run(Finalizer.java:159)

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"Reference Handler" id=9 idx=0x2c tid=772 prio=10 alive, in native, native_waiting, daemon
    
  
&#160;&#160;&#160; at java/lang/ref/Reference.waitForActivatedQueue()Ljava/lang/ref/Reference;(Native Method)

&#160;&#160;&#160; at java/lang/ref/Reference.access$100(Reference.java:11)

&#160;&#160;&#160; at java/lang/ref/Reference$ReferenceHandler.run(Reference.java:79)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"(Sensor Event Thread)" id=10 idx=0x30 tid=280 prio=5 alive, in native, daemon 

"ContainerBackgroundProcessor[StandardEngine[Catalina]]" id=12 idx=0x34 tid=3616 prio=5 alive, in native, sleeping, nati
    
  
ve_waiting, daemon

&#160;&#160;&#160; at java/lang/Thread.sleep(J)V(Native Method)

&#160;&#160;&#160; at org/apache/catalina/core/ContainerBase$ContainerBackgroundProcessor.run(ContainerBase.java:1579)

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"http-8080-Acceptor-0" id=13 idx=0x38 tid=2780 prio=5 alive, in native, daemon
    
  
&#160;&#160;&#160; at java/net/PlainSocketImpl.socketAccept(Ljava/net/SocketImpl;)V(Native Method)

&#160;&#160;&#160; at java/net/PlainSocketImpl.accept(PlainSocketImpl.java:384)

&#160;&#160;&#160; ^&#8211; Holding lock: java/net/SocksSocketImpl@0x031F98D0[biased lock]

&#160;&#160;&#160; at java/net/ServerSocket.implAccept(ServerSocket.java:453)

&#160;&#160;&#160; at java/net/ServerSocket.accept(ServerSocket.java:421)

&#160;&#160;&#160; at org/apache/tomcat/util/net/DefaultServerSocketFactory.acceptSocket(DefaultServerSocketFactory.java:61)

&#160;&#160;&#160; at org/apache/tomcat/util/net/JIoEndpoint$Acceptor.run(JIoEndpoint.java:310)

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"TP-Processor1" id=14 idx=0x3c tid=3184 prio=5 alive, in native, waiting, daemon
    
  
&#160;&#160;&#160; &#8212; Waiting for notification on: org/apache/tomcat/util/threads/ThreadPool$ControlRunnable@0x0179EB28[fat lock]

&#160;&#160;&#160; at jrockit/vm/Threads.waitForNotifySignal(JLjava/lang/Object;)Z(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(J)V(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(Object.java:485)

&#160;&#160;&#160; at org/apache/tomcat/util/threads/ThreadPool$ControlRunnable.run(ThreadPool.java:658)

&#160;&#160;&#160; ^&#8211; Lock released while waiting: org/apache/tomcat/util/threads/ThreadPool$ControlRunnable@0x0179EB28[fat lock]

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"TP-Processor2" id=15 idx=0x40 tid=2336 prio=5 alive, in native, waiting, daemon
    
  
&#160;&#160;&#160; &#8212; Waiting for notification on: org/apache/tomcat/util/threads/ThreadPool$ControlRunnable@0x0179EF40[fat lock]

&#160;&#160;&#160; at jrockit/vm/Threads.waitForNotifySignal(JLjava/lang/Object;)Z(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(J)V(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(Object.java:485)

&#160;&#160;&#160; at org/apache/tomcat/util/threads/ThreadPool$ControlRunnable.run(ThreadPool.java:658)

&#160;&#160;&#160; ^&#8211; Lock released while waiting: org/apache/tomcat/util/threads/ThreadPool$ControlRunnable@0x0179EF40[fat lock]

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"TP-Processor3" id=16 idx=0x44 tid=2644 prio=5 alive, in native, waiting, daemon
    
  
&#160;&#160;&#160; &#8212; Waiting for notification on: org/apache/tomcat/util/threads/ThreadPool$ControlRunnable@0x0179F400[fat lock]

&#160;&#160;&#160; at jrockit/vm/Threads.waitForNotifySignal(JLjava/lang/Object;)Z(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(J)V(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(Object.java:485)

&#160;&#160;&#160; at org/apache/tomcat/util/threads/ThreadPool$ControlRunnable.run(ThreadPool.java:658)

&#160;&#160;&#160; ^&#8211; Lock released while waiting: org/apache/tomcat/util/threads/ThreadPool$ControlRunnable@0x0179F400[fat lock]

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"TP-Processor4" id=17 idx=0x48 tid=1384 prio=5 alive, in native, daemon
    
  
&#160;&#160;&#160; at java/net/PlainSocketImpl.socketAccept(Ljava/net/SocketImpl;)V(Native Method)

&#160;&#160;&#160; at java/net/PlainSocketImpl.accept(PlainSocketImpl.java:384)

&#160;&#160;&#160; ^&#8211; Holding lock: java/net/SocksSocketImpl@0x0176E128[biased lock]

&#160;&#160;&#160; at java/net/ServerSocket.implAccept(ServerSocket.java:453)

&#160;&#160;&#160; at java/net/ServerSocket.accept(ServerSocket.java:421)

&#160;&#160;&#160; at org/apache/jk/common/ChannelSocket.accept(ChannelSocket.java:306)

&#160;&#160;&#160; at org/apache/jk/common/ChannelSocket.acceptConnections(ChannelSocket.java:660)

&#160;&#160;&#160; at org/apache/jk/common/ChannelSocket$SocketAcceptor.runIt(ChannelSocket.java:870)

&#160;&#160;&#160; at org/apache/tomcat/util/threads/ThreadPool$ControlRunnable.run(ThreadPool.java:686)

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"TP-Monitor" id=18 idx=0x4c tid=2788 prio=5 alive, in native, waiting, daemon
    
  
&#160;&#160;&#160; &#8212; Waiting for notification on: org/apache/tomcat/util/threads/ThreadPool$MonitorRunnable@0x0179FBB0[fat lock]

&#160;&#160;&#160; at jrockit/vm/Threads.waitForNotifySignal(JLjava/lang/Object;)Z(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(J)V(Native Method)

&#160;&#160;&#160; at org/apache/tomcat/util/threads/ThreadPool$MonitorRunnable.run(ThreadPool.java:561)

&#160;&#160;&#160; ^&#8211; Lock released while waiting: org/apache/tomcat/util/threads/ThreadPool$MonitorRunnable@0x0179FBB0[fat lock]

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

"http-8080-1" id=20 idx=0x50 tid=2192 prio=5 alive, in native, waiting, daemon
    
  
&#160;&#160;&#160; &#8212; Waiting for notification on: org/apache/tomcat/util/net/JIoEndpoint$Worker@0x016649A8[fat lock]

&#160;&#160;&#160; at jrockit/vm/Threads.waitForNotifySignal(JLjava/lang/Object;)Z(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(J)V(Native Method)

&#160;&#160;&#160; at java/lang/Object.wait(Object.java:485)

&#160;&#160;&#160; at org/apache/tomcat/util/net/JIoEndpoint$Worker.await(JIoEndpoint.java:416)

&#160;&#160;&#160; ^&#8211; Lock released while waiting: org/apache/tomcat/util/net/JIoEndpoint$Worker@0x016649A8[fat lock]

&#160;&#160;&#160; at org/apache/tomcat/util/net/JIoEndpoint$Worker.run(JIoEndpoint.java:442)

&#160;&#160;&#160; at java/lang/Thread.run(Thread.java:619)

&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)

&#160;&#160;&#160; &#8212; end of trace 

===== END OF THREAD DUMP ===============

<pre>参考资料:</pre>

<pre>1. <a href="http://www.atlassian.com/software/confluence">Atlassian Confluence</a> 3.0 管理控制台</pre>

<pre>2. JDK的DEMO</pre>

<pre>jdk1.5.0demomanagementFullThreadDump</pre>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [用Java代码来触发生成ThreadDump](http://www.beansoft.biz/2009/08/16/%e7%94%a8java%e4%bb%a3%e7%a0%81%e6%9d%a5%e8%a7%a6%e5%8f%91%e7%94%9f%e6%88%90threaddump/)