---
id: 3278
title: 关注SPECjEnterprise2010中JVM和WebLogic参数设置
date: 2012-09-28T21:57:41+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3278
permalink: '/2012/09/28/%e5%85%b3%e6%b3%a8specjenterprise2010%e4%b8%adjvm%e5%92%8cweblogic%e5%8f%82%e6%95%b0%e8%ae%be%e7%bd%ae/'
views:
  - "5605"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
  - WebLogic
tags:
  - GC
  - JVM
  - WebLogic
---
报告全文参考：<http://www.spec.org/jEnterprise2010/results/res2011q1/jEnterprise2010-20110223-00019.html>

&nbsp;

下面是一些Linux 64位下参数配置：

<pre>-showversion -Xlargepages:exitOnFailure=true -Xms6400m -Xmx6400m -Xns3360m -XXaggressive -Xgc:genpar
-XXgcthreads=8 -Xlargepages -Xverbose:opt,gcpause,compaction -Dweblogic.MuxerClass=weblogic.socket.NIOSocketMuxer
-Dweblogic.SocketReaders=3 -Dweblogic.management.discover=false -Dweblogic.diagnostics.debug.DebugLogger.DISABLED=true
-Djaxws.transport.streaming=true -Doracle.jdbc.defaultRowPrefetch=200
-Djavax.xml.parsers.DocumentBuilderFactory=weblogic.xml.jaxp.RegistryDocumentBuilderFactory
-Dsun.net.inetaddr.ttl=0 -Dnetworkaddress.cache.ttl=0</pre>

<pre>&nbsp;</pre>

<pre>超大内存：</pre>

<pre>-Xmx21g -Xms21g -Xmn7g -Xss272k -XX:PermSize=95m -XX:MaxPermSize=512M -XX:+UseLargePages -XX:+AggressiveOpts
-XX:+DisableExplicitGC -verbosegc -Xloggc:emugc.log -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -XX:+PrintCommandLineFlags
-showversion -Dsun.net.inetaddr.ttl=0 -Dnetworkaddress.cache.ttl=0 -Dweblogic.SocketReaders=1
-Dweblogic.management.discover=false -Dweblogic.diagnostics.debug.DebugLogger.DISABLED=true
-Djavax.xml.parsers.DocumentBuilderFactory=com.sun.org.apache.xerces.internal.jaxp.DocumentBuilderFactoryImpl -Dhttp.keepAlive=false</pre>

<pre>&nbsp;</pre>

<pre>硬件配置:</pre>

<pre>&nbsp;</pre>

<table style="widows: 2; text-transform: none; text-indent: 0px; letter-spacing: normal; font-family: ; orphans: 2; word-spacing: 0px; -webkit-text-size-adjust: auto; -webkit-text-stroke-width: 0px" border="1" cellspacing="2" cellpadding="2" width="100%">
  <tr>
    <th>
      <font face="宋体"><font style="font-size: 12pt">JEE AppServer HW (SUT hardware)</font></font>
    </th>
  </tr>
  
  <tr>
    <td>
      <table style="word-spacing: normal" border="0" cellspacing="0" width="100%">
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Hardware Vendor:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">Cisco</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">OS Vendor:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">Oracle Corporation</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Model Name:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">Cisco UCS B440 M1 Blade Server</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">OS Name:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">Oracle Linux 5 Update 5 x86_64</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Processor:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">Eight Core Intel(R) Xeon(R) X7560</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Filesystem:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">ext3</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">MHz:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">2262</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Disks:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">4x 73GB 6Gb/s SAS 15K RPM Cisco UCS M71KR-Q QLogic Converged</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt"># of CPUs:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">32 cores, 4 chips, 8 cores/chip, 2 threads/core (Hyper-Threading)</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Network Interface:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">Network Adapter with 2 x 10 Gigabit Ethernet and 2 x 4Gbps Fiber Channel</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Memory (MB):</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">131072</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Other Hardware:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">See notes</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">DIMM[0] Count:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">32</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">DIMM[0] Size:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">4096</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">L1 Cache:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">32KB(I)+32KB(D) on chip per core</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt"># of Systems:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">2</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">L2 Cache:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">256 KB on chip per core</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">H/W Available:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">May-2010</font></font>
          </td>
        </tr>
        
        <tr valign="bottom" align="left">
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">Other Cache:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">24MB(I+D) L3 on chip per chip</font></font>
          </td>
          
          <th width="20%">
            <font face="宋体"><font style="font-size: 12pt">OS Available:</font></font>
          </th>
          
          <td width="30%">
            <font face="宋体"><font style="font-size: 12pt">Apr-2010</font></font>
          </td>
        </tr>
      </table>
    </td>
  </tr>
  
  <tr>
    <td>
      <table style="word-spacing: normal" border="1" cellspacing="0" width="100%">
        <tr>
          <th width="100%">
            <font face="宋体"><font style="font-size: 12pt">Notes / Tuning Information</font></font>
          </th>
        </tr>
        
        <tr>
          <td width="100%">
            <pre><font style="font-size: 12pt">Added to /etc/sysctl.conf:
fs.file-max = 524288
kernel.sem = 250 32000 100 128
kernel.shmall = 10737418240
kernel.shmmax = 4398046511104
net.core.netdev_max_backlog = 400000
net.core.optmem_max = 30000000
net.core.rmem_default = 30000000
net.core.rmem_max = 30000000
net.core.somaxconn = 40000
net.core.wmem_default = 30000000
net.core.wmem_max = 30000000
net.ipv4.ip_local_port_range = 1024 65000
net.ipv4.tcp_fin_timeout = 10
net.ipv4.tcp_max_syn_backlog = 30000
net.ipv4.tcp_max_tw_buckets = 2000000
net.ipv4.tcp_mem = 30000000 30000000 30000000
net.ipv4.tcp_rmem = 30000000 30000000 30000000
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_wmem = 30000000 30000000 30000000
vm.zone_reclaim_mode=1

For each of the NICs:
set arp_announce = 2
set arp_ignore = 1
set txqueuelen 60000
enable tso and gso
bind interrupt to a core corresponding to the server instance

Server instances were started using numactl in RT priority of 89, binding 1 instance per chip.
Stop iptables.
Stop irqbalance.
Configure 50000 hugepages.

System was configured with 4 drives in RAID1/0
for jms and server logs.</font></pre>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [关注SPECjEnterprise2010中JVM和WebLogic参数设置](http://www.beansoft.biz/2012/09/28/%e5%85%b3%e6%b3%a8specjenterprise2010%e4%b8%adjvm%e5%92%8cweblogic%e5%8f%82%e6%95%b0%e8%ae%be%e7%bd%ae/)