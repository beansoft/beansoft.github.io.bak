---
id: 2171
title: 'WebLogic如何处理socket muxers ?[转]'
date: 2011-08-12T20:39:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2171
permalink: '/2011/08/12/weblogic%e5%a6%82%e4%bd%95%e5%a4%84%e7%90%86socket-muxers-%e8%bd%ac/'
views:
  - "14439"
original_post_id:
  - "2171"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Muxer
  - WebLogic
---
来源: <http://m-button.blogspot.com/2008/08/how-does-weblogic-handle-socket-muxers.html>

&#160;

   <span class="Apple-style-span" style="word-spacing:0;font:14px/18px arial, tahoma, helvetica, freesans, sans-serif;text-transform:none;color:rgb(204,204,204);text-indent:0;white-space:normal;letter-spacing:normal;background-color:rgb(28,28,28);orphans:2;widows:2;"></p> 

<h3 class="post-title entry-title" style="font:18px georgia, utopia, &#039;position:relative;margin:0;">
  How does WebLogic handle socket muxers ?
</h3>

<div class="post-header" style="color:rgb(153,153,153);line-height:1.6;margin:0 0 1.5em;">
  <div class="post-header-line-1">
  </div></p>
</div>

<div class="post-body entry-content" id="post-body-8829001742119452144" style="font-size:15px;width:1048px;line-height:1.4;position:relative;">
  <h2 style="font:18px georgia, utopia, &#039;text-transform:none;color:rgb(255,255,255);position:relative;margin:.5em 0;">
    Muxer ? What&#8217;s that ?
  </h2>
  
  <p>
    <u>Taken from the documentation</u><span class="Apple-converted-space">&#160;</span>(<a title="http://edocs.bea.com/wls/docs100/perform/WLSTuning.html#wp1152246" style="color:rgb(255,153,0);text-decoration:none;" href="http://edocs.bea.com/wls/docs100/perform/WLSTuning.html#wp1152246">http://edocs.bea.com/wls/docs100/perform/WLSTuning.html#wp1152246</a>) :
  </p>
  
  <p>
    WebLogic Server uses software modules called muxers to read incoming requests on the server and incoming responses on the client.
  </p>
  
  <p>
    These muxers are of two primary types: the Java muxer or native muxer. A Java muxer has the following characteristics:
  </p>
  
  <ul style="line-height:1.4;list-style-type:disc;margin:.5em 0;padding:0 2.5em;">
  </ul>
  
  <ul style="line-height:1.4;list-style-type:disc;margin:.5em 0;padding:0 2.5em;">
  </ul>
  
  <blockquote>
    <p>
      <a name="wp1152787"></a>* Uses pure Java to read data from sockets.
    </p>
  </blockquote>
  
  <blockquote>
    <p>
      <a name="wp1152797"></a>* It is also the only muxer available for RMI clients.
    </p>
  </blockquote>
  
  <blockquote>
    <p>
      <a name="wp1152791"></a>* Blocks on reads until there is data to be read from a socket.
    </p>
    
    <p>
      (This behavior does not scale well when there are a large number of sockets and/or when data arrives infrequently at sockets.
    </p>
    
    <p>
      This is typically not an issue for clients, but it can create a huge bottleneck for a server. )
    </p>
  </blockquote>
  
  <ul style="line-height:1.4;list-style-type:disc;margin:.5em 0;padding:0 2.5em;">
  </ul>
  
  <p>
    <a name="wp1153211"></a>Native muxers use platform-specific native binaries to read data from sockets. The majority of all platforms provide some mechanism to poll a socket for data.
  </p>
  
  <p>
    &#160;
  </p>
  
  <p>
    For example, Unix systems use the poll system and the Windows architecture uses completion ports.
  </p>
  
  <p>
    Native provide superior scalability because they implement a non-blocking thread model.
  </p>
  
  <p>
    When a native muxer is used, the server creates a fixed number of threads dedicated to reading incoming requests.
  </p>
  
  <p>
    &#160;
  </p>
  
  <p>
    BEA recommends using the default setting of selected for the<span class="Apple-converted-space">&#160;</span><code>Enable Native IO</code><span class="Apple-converted-space">&#160;</span>parameter which allows the server automatically selects the appropriate muxer for the server to use.
  </p>
  
  <p>
    <a name="wp1151372"></a>If the<span class="Apple-converted-space">&#160;</span><code>Enable Native IO</code><span class="Apple-converted-space">&#160;</span>parameter is not selected, the server instance exclusively uses the Java muxer.
  </p>
  
  <p>
    This maybe acceptable if there are a small number of clients and the rate at which requests arrive at the server is fairly high.
  </p>
  
  <p>
    Under these conditions, the Java muxer performs as well as a native muxer and eliminate Java Native Interface (JNI) overhead. Unlike native muxers,
  </p>
  
  <p>
    the number of threads used to read requests is not fixed and is tunable for Java muxers by configuring the<span class="Apple-converted-space">&#160;</span><code>Percent Socket Readers</code><span class="Apple-converted-space">&#160;</span>parameter setting in the Administration Console.
  </p>
  
  <p>
    &#160;
  </p>
  
  <p>
    See<span class="Apple-converted-space">&#160;</span><a style="color:rgb(255,153,0);text-decoration:none;" href="http://edocs.bea.com/wls/docs100/perform/WLSTuning.html#wp1152595">Changing the Number of Available Socket Readers</a>.
  </p>
  
  <p>
    Ideally, you should configure this parameter so the number of threads roughly equals the number of remote concurrently connected clients up to 50% of the total thread pool size.
  </p>
  
  <p>
    Each thread waits for a fixed amount of time for data to become available at a socket.
  </p>
  
  <p>
    If no data arrives, the thread moves to the next socket.
  </p></p> 
  
  <p>
    Then, for those reasons, it is obviously better to use native muxers.
  </p>
  
  <p>
    &#160;
  </p>
  
  <h2 style="font:18px georgia, utopia, &#039;text-transform:none;color:rgb(255,255,255);position:relative;margin:.5em 0;">
    How do you know that your muxers are native and not java ?
  </h2>
  
  <p>
    Well, you&#8217;ve got two ways to know that.
  </p>
  
  <h3 style="position:relative;margin:0;">
    Log File
  </h3>
  
  <p>
    First one, when you start your server, if the log level is high enough, you should see a line like this one :
  </p>
  
  <blockquote>
    <p>
      <Info> <Socket> <BEA-000446> <Native IO Enabled.>
    </p>
  </blockquote>
  
  <p>
    If you don&#8217;t have the opportunity to check for that line in the logs, it is possible to see that information, thanks to thread dumps.<span class="Apple-converted-space">&#160;</span> <br />To perform a thread dump, you&#8217;ve got to send a precise signal to the JVM (<a title="http://en.wikipedia.org/wiki/SIGQUIT" style="color:rgb(255,153,0);text-decoration:none;" href="http://en.wikipedia.org/wiki/SIGQUIT">http://en.wikipedia.org/wiki/SIGQUIT</a>).
  </p>
  
  <h3 style="position:relative;margin:0;">
    Thread dump
  </h3>
  
  <h4 style="position:relative;margin:0;">
    <u>Perform a thread dump</u>
  </h4>
  
  <p>
    If you&#8217;re in a Windows environment and your server has been launched with a startup script, switch to the command line window and press CTRL + Break.
  </p>
  
  <p>
    That will display the thread dump in the console.
  </p>
  
  <p>
    If you&#8217;re in a Windows environment, but in a service mode, use the beasvc tool to perform the dump. (beasvc -dump)
  </p>
  
  <p>
    If Unix is your playground, then you should use the following command "kill -3 PID" (PID is the process id of your JVM)
  </p>
  
  <p>
    Another way is to use WLST to perform the dump (quite useful in a AIX environment, trust me !). Take a look at one of my previous post to know more about it.
  </p>
  
  <p>
    Once you have your thread dump, you&#8217;ll have to analyze it.
  </p>
  
  <h4 style="position:relative;margin:0;">
    <u>Analyze a thread dump</u>
  </h4>
  
  <p>
    In the dump, look for a section in which you can find<span class="Apple-converted-space">&#160;</span><strong><u><em>queue: &#8216;weblogic.socket.Muxer&#8217;"</em></u></strong>
  </p>
  
  <p>
    Like that :
  </p>
  
  <blockquote>
    <p>
      "ExecuteThread: &#8216;2&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;" id=25 idx=0x5c tid=2492 prio=5 alive, in native, daemon<span class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; at weblogic/socket/<font color="#0000ff">NTSocketMuxer</font>.getIoCompletionResult(Lweblogic/socket/NTSocketMuxer$IoCompletionData;)Z(Native Method)<s class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; at weblogic/socket/NTSocketMuxer.processSockets(NTSocketMuxer.java:81)<span class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; at weblogic/socket/SocketReaderRequest.run(SocketReaderRequest.java:29)<span class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; at weblogic/socket/SocketReaderRequest.execute(SocketReaderRequest.java:42)<span class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; at weblogic/kernel/ExecuteThread.execute(ExecuteThread.java:145)<span class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; at weblogic/kernel/ExecuteThread.run(ExecuteThread.java:117)<span class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; at jrockit/vm/RNI.c2java(IIIII)V(Native Method)<span class="Apple-converted-space">&#160;</span> <br />&#160;&#160;&#160; &#8212; end of trace
    </p>
  </blockquote>
  
  <p>
    Here you can see (in blue) that the muxer used is the NTSoketMuxer. As long as it is NOT the class<span class="Apple-converted-space">&#160;</span><strong>weblogic.socket.SocketMuxer</strong>,<strong>&#160;</strong>you&#8217;re using a native muxer.
  </p>
  
  <p>
    Else it&#8217;s a java muxer.
  </p>
  
  <p>
    &#160;
  </p>
  
  <h2 style="font:18px georgia, utopia, &#039;text-transform:none;color:rgb(255,255,255);position:relative;margin:.5em 0;">
    List of muxers
  </h2>
  
  <h3 style="position:relative;margin:0;">
    <u>Java Muxer</u>
  </h3>
  
  <p>
    As said above, a java muxer is embodied by the class<span class="Apple-converted-space">&#160;</span><strong>weblogic.socket.SocketMuxer</strong>
  </p>
  
  <h3 style="position:relative;margin:0;">
    <u>Native muxers</u>
  </h3>
  
  <p>
    Windows :<span class="Apple-converted-space">&#160;</span><strong>weblogic.socket.NTSocketMuxer</strong>
  </p>
  
  <p>
    UNIX<span class="Apple-converted-space">&#160;</span><strong>weblogic.socket.PosixSocketMuxer</strong><span class="Apple-converted-space">&#160;</span>&<span class="Apple-converted-space">&#160;</span><strong>weblogic.socket.DevPollSocketMuxer</strong>
  </p>
  
  <p>
    <em><u>Note :</u></em><span class="Apple-converted-space">&#160;</span>On UNIX environments (such as Solaris and HP-UX), WebLogic Server uses DevPollSocketMuxer by default,
  </p>
  
  <p>
    which prints out unnecessary SocketExceptions errors to the server log.
  </p>
  
  <p>
    As a workaround, you can enable PosixSocketMuxer via the WebLogic Scripting Tool as follows:
  </p>
  
  <blockquote>
    <p>
      edit()
    </p>
    
    <p>
      cd (&#8216;Servers/<em>&#8216;MyServerName</em>&#8216;)
    </p>
    
    <p>
      startEdit()
    </p>
    
    <p>
      set(&#8216;MuxerClass&#8217;,&#8217;weblogic.socket.PosixSocketMuxer&#8217;)
    </p>
    
    <p>
      activate()
    </p>
    
    <p>
      &#160;
    </p>
  </blockquote>
</div>

<p>
  </span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/08/12/weblogic%e5%a6%82%e4%bd%95%e5%a4%84%e7%90%86socket-muxers-%e8%bd%ac/">WebLogic如何处理socket muxers ?[转]</a>
</p>