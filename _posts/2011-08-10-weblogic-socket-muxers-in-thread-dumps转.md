---
id: 2168
title: 'Weblogic &#8211; Socket Muxers in Thread Dumps[转]'
date: 2011-08-10T12:24:42+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2168
permalink: '/2011/08/10/weblogic-socket-muxers-in-thread-dumps%e8%bd%ac/'
views:
  - "11167"
original_post_id:
  - "2168"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: <http://jojovedder.blogspot.com/2009/05/weblogic-socket-muxers-are-not-stuck.html>

&#160;

**What are these weblogic.socket.Muxer threads seen in thread dumps ?**   
Note: for a basic primer on taking thread dumps and analyzing them, see [this earlier article](http://jojovedder.blogspot.com/2009/01/app-server-high-cpu-or-low-threads.html)   
Socket Reader Threads accept the incoming request from the Listen Thread Queue and put it on the Execute Thread Queue.   
In WL 8.1, there are 3 socket reader threads by default.   
In WL 9 and 10, WebLogic allocates 33% of server threads to act as socket readers by default. This need not be changed usually.   
One socket reader thread is usually in the poll function, while the others are available to process requests.   
The polling thread is highlighted [in the thread dump](http://www.blogger.com/posts.g?blogID=2805163882887351730&searchType=ALL&txtKeywords=&label=thread+dump) below.

<pre><br />
"ExecuteThread: '2' for queue: 'weblogic.socket.Muxer'" daemon prio=5 tid=0x016b2148 nid=0x42 waiting for monitor entry [5997f000..5997fc28]<br />
at weblogic.socket.PosixSocketMuxer.processSockets(PosixSocketMuxer.java:91)<br />
- waiting to lock &lt;0x94846b40&gt; (a java.lang.String)<br />
at weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:32)<br />
at weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:219)<br />
at weblogic.kernel.ExecuteThread.run(ExecuteThread.java:178)</pre>

<pre><br />
"ExecuteThread: '1' for queue: 'weblogic.socket.Muxer'" daemon prio=5 tid=0x00683c28 nid=0x41 waiting for monitor entry [59a7f000..59a7fc28]<br />
at weblogic.socket.PosixSocketMuxer.processSockets(PosixSocketMuxer.java:91)<br />
- waiting to lock &lt;0x94846b40&gt; (a java.lang.String)<br />
at weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:32)<br />
at weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:219)<br />
at weblogic.kernel.ExecuteThread.run(ExecuteThread.java:178)</pre>

<pre><br />
"ExecuteThread: '0' for queue: 'weblogic.socket.Muxer'" daemon prio=5 tid=0x0079e5b0 nid=0x40 runnable [59b7f000..59b7fc28]<br />
at weblogic.socket.PosixSocketMuxer.poll(Native Method)<br />
at weblogic.socket.PosixSocketMuxer.processSockets(PosixSocketMuxer.java:100)<br />
- locked &lt;0x94846b40&gt; (a java.lang.String)<br />
at weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:32)<br />
at weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:219)<br />
at weblogic.kernel.ExecuteThread.run(ExecuteThread.java:178)</pre>

In an earlier support case on Stuck Threads, we asked BEA:
    
  
Should we worry about the Weblogic.socket.Muxer threads which always show 2 threads waiting for lock and 3rd thread locking the same object?

The Muxer TD is attached. This shows same behaviour on all our Weblogic servers.

<pre><br />
Full thread dump Java HotSpot(TM) Server VM (1.4.2_05-b04 mixed mode):<br />
<br />
"ExecuteThread: '2' for queue: 'weblogic.socket.Muxer'" daemon prio=5 tid=0x0151<br />
c588 nid=0x1b4 waiting for monitor entry [ad57f000..ad57fc28]<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.socket.PosixSocketMuxer.processSockets(PosixSocketMuxer.java:91)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; - waiting to lock &lt;0xd9331760&gt; (a java.lang.String)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:32)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:219)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.kernel.ExecuteThread.run(ExecuteThread.java:178)</pre>

<pre><br />
<br />
"ExecuteThread: '1' for queue: 'weblogic.socket.Muxer'" daemon prio=5 tid=0x0161<br />
d608 nid=0x1b3 runnable [ad67f000..ad67fc28]<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.socket.PosixSocketMuxer.poll(Native Method)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.socket.PosixSocketMuxer.processSockets(PosixSocketMuxer.java:100)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; - locked &lt;0xd9331760&gt; (a java.lang.String)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:32)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:219)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.kernel.ExecuteThread.run(ExecuteThread.java:178)</pre>

<pre><br />
<br />
"ExecuteThread: '0' for queue: 'weblogic.socket.Muxer'" daemon prio=5 tid=0x01bb<br />
6730 nid=0x1b2 waiting for monitor entry [ad77f000..ad77fc28]<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.socket.PosixSocketMuxer.processSockets(PosixSocketMuxer.java:91)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; - waiting to lock &lt;0xd9331760&gt; (a java.lang.String)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:32)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:219)<br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; at weblogic.kernel.ExecuteThread.run(ExecuteThread.java:178)</pre>

The reply from BEA Support was that the above pattern of weblogic.socket.Muxer threads are not a cause of stuck threads.
    
  
**Why do they mostly show as being Stuck in Samurai TD analyzer ?** 

<img title="clip_image001[3]" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="46" alt="clip_image001[3]" src="http://www.beansoft.biz/wp-content/uploads/2011/08/clip_image0013.jpg" width="320" border="0" />

As the image shows, [when you analyze thread dumps using Samurai](http://yusuke.homeip.net/samurai/), the muxer threads are shown as being Stuck since they&#8217;re all locked on the same object. This is probably treated as a deadlock condition.

<pre><br />
"ExecuteThread: '2' for queue: 'weblogic.socket.Muxer'"<br />
- waiting to lock &lt;0xd9b61098&gt; (a java.lang.String)</pre>

"ExecuteThread: &#8216;1&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;"
    
  
&#8211; waiting to lock <0xd9b61098> (a java.lang.String)

"ExecuteThread: &#8216;0&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;"
    
  
&#8211; locked <0xd9b61098> (a java.lang.String)

But you will see the same in any Thread dump even on a development instance with no requests.
    
  
The locks mentioned do show up as red in Samurai &#8211; but they aren&#8217;t deadlocks just regular locks.

A thread gains an exclusive lock on an object to perform some action, then frees it allowing the next thread to gain access.

Additionally, if you look at the thread dumps over time, you&#8217;ll see that these specific locks are not always present &#8211; they are moving between the threads which is indicative of their transitory nature.

**I want to know more details on Muxers**

The socket Muxer manages the server’s existing socket connections.

It first determines which sockets have incoming requests waiting to be processed. It then reads enough data to determine the protocol and dispatches the socket to an appropriate runtime layer based on the protocol.

In the runtime layer, the socket muxer threads determine which execute thread queue to be used and delegates the request accordingly.

From the documentation on http://edocs.bea.com/wls/docs100/perform/WLSTuning.html#wp1152246 ,

Weblogic has two versions of the socket muxer, one is the Java version and the other uses a native library which makes better use of operating system calls. The Enable Native IO checkbox on the server’s configuration settings tells the server which version to use. This is ON by default for most platforms.

Native muxers provide superior scalability because they implement a non-blocking thread model. When a native muxer is used, the server creates a fixed number of threads dedicated to reading incoming requests. Oracle recommends using the default setting of true for the Enable Native IO parameter which allows the server to automatically select the appropriate muxer to use.

You must ensure that to use Native I/O, the native library must be present in the server’s shared library path . This is set up with the default scripts.

When the server does not find the native library, it throws an error

java.lang.UnsatisfiedLinkError: no muxer in java.library.path

and then loads the Java version of the muxer.

Confirm the LD library path is okay and pointing to the Solaris LD path. Check the startup log when starting a managed server. What is the value of java.library.path?

This is where the JVM actually get&#8217;s the library from.

http://m-button.blogspot.com/2008/08/how-does-weblogic-handle-socket-muxers.html has a good example of how to identify Native vs Java muxer in a thread dump.

The Thread Dump I’ve used in my examples above uses the Native muxer (weblogic.socket.PosixSocketMuxer) on Solaris.

Solaris has another Native muxer called the weblogic.socket.DevPollSocketMuxer

An example TD using this muxer is shown below.

<pre><br />
"ExecuteThread: '4' for queue: 'weblogic.socket.Muxer'" waiting for lock java.lang.String@4edf4f BLOCKED<br />
weblogic.socket.DevPollSocketMuxer.processSockets(DevPollSocketMuxer.java:95)<br />
weblogic.socket.SocketReaderRequest.run(SocketReaderRequest.java:29)<br />
weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:42)<br />
weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:145)<br />
weblogic.kernel.ExecuteThread.run(ExecuteThread.java:117)</pre>

<pre><br />
<br />
"ExecuteThread: '3' for queue: 'weblogic.socket.Muxer'" RUNNABLE native<br />
weblogic.socket.DevPollSocketMuxer.doPoll(Native Method)<br />
weblogic.socket.DevPollSocketMuxer.processSockets(DevPollSocketMuxer.java:96)<br />
weblogic.socket.SocketReaderRequest.run(SocketReaderRequest.java:29)<br />
weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:42)<br />
weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:145)</pre>

<pre><br />
<br />
weblogic.kernel.ExecuteThread.run(ExecuteThread.java:117)<br />
"ExecuteThread: '2' for queue: 'weblogic.socket.Muxer'" waiting for lock java.lang.String@4edf4f BLOCKED<br />
weblogic.socket.DevPollSocketMuxer.processSockets(DevPollSocketMuxer.java:95)<br />
weblogic.socket.SocketReaderRequest.run(SocketReaderRequest.java:29)<br />
weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:42)<br />
weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:145)<br />
weblogic.kernel.ExecuteThread.run(ExecuteThread.java:117)</pre>

<pre><br />
<br />
"ExecuteThread: '1' for queue: 'weblogic.socket.Muxer'" waiting for lock java.lang.String@4edf4f BLOCKED<br />
weblogic.socket.DevPollSocketMuxer.processSockets(DevPollSocketMuxer.java:95)<br />
weblogic.socket.SocketReaderRequest.run(SocketReaderRequest.java:29)<br />
weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:42)<br />
weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:145)<br />
weblogic.kernel.ExecuteThread.run(ExecuteThread.java:117)</pre>

<pre><br />
<br />
"ExecuteThread: '0' for queue: 'weblogic.socket.Muxer'" waiting for lock java.lang.String@4edf4f BLOCKED<br />
weblogic.socket.DevPollSocketMuxer.processSockets(DevPollSocketMuxer.java:95)<br />
weblogic.socket.SocketReaderRequest.run(SocketReaderRequest.java:29)<br />
weblogic.socket.SocketReaderRequest.execute(SocketReaderRequest.java:42)<br />
weblogic.kernel.ExecuteThread.execute(ExecuteThread.java:145)<br />
weblogic.kernel.ExecuteThread.run(ExecuteThread.java:117)</pre>

<pre>&#160;</pre>

To change the number of Muxers from the default, follow the instructions given at http://e-docs.bea.com/wls/docs92/ConsoleHelp/taskhelp/tuning/TuningSocketReaders.html
    
  
See <http://jojovedder.blogspot.com/2009/07/more-on-weblogic-muxers.html>for an update on Muxers

Additionally on Oracle JRockit JVMs &#8211; there are some information in the thread dumps which point out the same problem in a different manner.

After the normal stack dumps, BEA JRockit performs a deadlock detection. This is done by finding "lock chains" in the Java application. If a lock chain is found to be circular, the application is considered caught in a deadlock.

A detailed explanation of the 3 types of lock chains in JRockit [is given here](http://download.oracle.com/docs/cd/E13150_01/jrockit_jvm/jrockit/geninfo/diagnos/thread_basics.html)

What is relevant for us is the example of Muxers which are shown as:

Blocked lock chains

===================

Chain 2:

"ExecuteThread: &#8216;2&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;" id=129 idx=0x218 tid=4079 waiting for java/lang/String@0x37804000 held by:

"ExecuteThread: &#8216;0&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;" id=127 idx=0x210 tid=4077 in chain 1

Open lock chains

================

Chain 1:

"ExecuteThread: &#8216;1&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;" id=128 idx=0x214 tid=4078 waiting for java/lang/String@0x37804000 held by:

"ExecuteThread: &#8216;0&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;" id=127 idx=0x210 tid=4077 (active)

As per the explanation, the Open lock chain depicts Thread 1 waiting for Thread 0. This is not a deadlock, only a straight dependency.

Since Thread 0 is already part of the Open lock chain, the fact that Thread 2 is also waiting on the same Thread 0 is treated as a "Blocked lock chain".

In this case this is not a problem.

**Update 15th Feb 2011**

I&#8217;m glad this blog entry on weblogic muxers has made it [onto the Oracle forums](http://forums.oracle.com/forums/thread.jspa?messageID=9318157&tstart=0) with a mention from [James Bayer](http://blogs.oracle.com/jamesbayer/). 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Weblogic &#8211; Socket Muxers in Thread Dumps[转]](http://www.beansoft.biz/2011/08/10/weblogic-socket-muxers-in-thread-dumps%e8%bd%ac/)