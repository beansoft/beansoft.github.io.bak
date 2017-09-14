---
id: 212
title: 'java.net.SocketException: Too many open files 问题的解决办法'
date: 2009-11-02T11:55:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=212
permalink: '/2009/11/02/java-net-socketexception-too-many-open-files-%e9%97%ae%e9%a2%98%e7%9a%84%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95-2/'
views:
  - "5193"
original_post_id:
  - "212"
categories:
  - Uncategorized
---
Oct 31, 2009 8:14:25 AM org.apache.tomcat.util.net.PoolTcpEndpoint acceptSocket   
WARNING: Reinitializing ServerSocket   
Oct 31, 2009 8:14:25 AM org.apache.tomcat.util.net.PoolTcpEndpoint acceptSocket   
SEVERE: Endpoint ServerSocket[addr=0.0.0.0/0.0.0.0,port=0,localport=8080] ignored exception: java.net.SocketException: Too many open files   
java.net.SocketException: Too many open files   
&#160;&#160;&#160; at java.net.PlainSocketImpl.socketAccept(Native Method)   
&#160;&#160;&#160; at java.net.PlainSocketImpl.accept(PlainSocketImpl.java:384)   
&#160;&#160;&#160; at java.net.ServerSocket.implAccept(ServerSocket.java:450)   
&#160;&#160;&#160; at java.net.ServerSocket.accept(ServerSocket.java:421)   
&#160;&#160;&#160; at org.apache.tomcat.util.net.DefaultServerSocketFactory.acceptSocket(DefaultServerSocketFactory.java:61)   
&#160;&#160;&#160; at org.apache.tomcat.util.net.PoolTcpEndpoint.acceptSocket(PoolTcpEndpoint.java:408)   
&#160;&#160;&#160; at org.apache.tomcat.util.net.LeaderFollowerWorkerThread.runIt(LeaderFollowerWorkerThread.java:71)   
&#160;&#160;&#160; at org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:689)   
&#160;&#160;&#160; at java.lang.Thread.run(Thread.java:595) 

这是Tomcat报的错误， Google一把，看到如下解释： 

[http://www.cnitblog.com/rd416/archive/2008/08/07/47724.aspx](http://www.cnitblog.com/rd416/archive/2008/08/07/47724.aspx "http://www.cnitblog.com/rd416/archive/2008/08/07/47724.aspx") 

linux 上tomcat 服务器抛出socket异常“文件打开太多”的问题   
java.net.SocketException: Too many open files   
at java.net.PlainSocketImpl.socketAccept(Native Method)   
at java.net.PlainSocketImpl.accept(PlainSocketImpl.java:384)   
at java.net.ServerSocket.implAccept(ServerSocket.java:450)   
at java.net.ServerSocket.accept(ServerSocket.java:421)   
at org.apache.tomcat.util.net.DefaultServerSocketFactory.acceptSocket(DefaultServerSocketFactory.java:60)   
at org.apache.tomcat.util.net.PoolTcpEndpoint.acceptSocket(PoolTcpEndpoint.java:407)   
at org.apache.tomcat.util.net.LeaderFollowerWorkerThread.runIt(LeaderFollowerWorkerThread.java:70)   
at org.apache.tomcat.util.threads.ThreadPool$ControlRunnable.run(ThreadPool.java:684)   
at java.lang.Thread.run(Thread.java:595) 

原本以为是tomcat的配置或是应用本身的问题，"谷歌"一把后才发现，该问题的根本原因是由于系统文件资源的限制导致的。 

具体可以参考[http://www.bea.com.cn/support\_pattern/Too\_Many\_Open\_Files_Pattern.html](http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html)   
的说明。具体的解决方式可以参考一下：   
1。ulimit -a 查看系统目前资源限制的设定。   
&#160;&#160; [root@test security]# umlimit -a   
-bash: umlimit: command not found   
[root@test security]# ulimit -a   
core file size&#160;&#160;&#160;&#160;&#160;&#160;&#160; (blocks, -c) 0   
data seg size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -d) unlimited   
file size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (blocks, -f) unlimited   
max locked memory&#160;&#160;&#160;&#160; (kbytes, -l) unlimited   
max memory size&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -m) unlimited   
open files&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (-n) 1024   
pipe size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (512 bytes, -p) 8   
stack size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -s) 8192   
cpu time&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (seconds, -t) unlimited   
max user processes&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (-u) 7168   
virtual memory&#160;&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -v) unlimited   
[root@test security]#   
通过以上命令，我们可以看到open files 的最大数为1024   
那么我们可以通过一下命令修改该参数的最大值   
2. ulimit -n 4096   
[root@test security]# ulimit -n 4096   
[root@test security]# ulimit -a   
core file size&#160;&#160;&#160;&#160;&#160;&#160;&#160; (blocks, -c) 0   
data seg size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -d) unlimited   
file size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (blocks, -f) unlimited   
max locked memory&#160;&#160;&#160;&#160; (kbytes, -l) unlimited   
max memory size&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -m) unlimited   
open files&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (-n) 4096   
pipe size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (512 bytes, -p) 8   
stack size&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -s) 8192   
cpu time&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (seconds, -t) unlimited   
max user processes&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; (-u) 7168   
virtual memory&#160;&#160;&#160;&#160;&#160;&#160;&#160; (kbytes, -v) unlimited 

这样我们就修改了系统在同一时间打开文件资源的最大数，基本解决以上问题。 

以上部分是查找网络上的解决方法。设置了之后段时间内有作用。 

后来仔细想来，问题还是要从根本上解决，于是把以前的代码由认真地看了一遍。终于找到了，罪魁祸首。 

在读取文件时，有一些使用的BufferedReader 没有关闭。导致文件一直处于打开状态。造成资源的严重浪费。 

修改之后的简单代码如下： 

public void test(){   
&#160;&#160;&#160; BufferedReader reader =null;   
try{   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; reader = 读取文件;   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; String line = "";   
while( ( ine=reader.readLine())!=null){   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 其他操作   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160; } catch (IOException e){   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println(e);   
&#160;&#160;&#160; } finally{&#160;   
if(reader !=null){   
try {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; reader.close();   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; } catch (IOException e) {   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; e.printStackTrace();   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
&#160;&#160;&#160; }   
} 

以上只是我的个人见解，希望对大家有所帮助。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [java.net.SocketException: Too many open files 问题的解决办法](http://www.beansoft.biz/2009/11/02/java-net-socketexception-too-many-open-files-%e9%97%ae%e9%a2%98%e7%9a%84%e8%a7%a3%e5%86%b3%e5%8a%9e%e6%b3%95-2/)