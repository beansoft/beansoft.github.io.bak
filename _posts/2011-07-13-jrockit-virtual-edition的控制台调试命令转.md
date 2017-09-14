---
id: 2054
title: 'JRockit Virtual Edition的控制台调试命令[转]'
date: 2011-07-13T21:20:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2054
permalink: '/2011/07/13/jrockit-virtual-edition%e7%9a%84%e6%8e%a7%e5%88%b6%e5%8f%b0%e8%b0%83%e8%af%95%e5%91%bd%e4%bb%a4%e8%bd%ac/'
views:
  - "4132"
original_post_id:
  - "2054"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
---
From: <http://prsync.com/oracle/jrockit-virtual-edition-debug-key-24625/>

There are a few keys that can help the debugging of the JRVE env in console. you can type in each keys in JRVE console to see what&#8217;s happening under the hood.

key &#8216;0&#8217; : System information   
key &#8216;5&#8217; : Enable shutdown   
key &#8216;7&#8217; : Start JRockit Management Server (port 7091)   
key &#8216;8&#8217; : Statistics Counters   
key &#8216;9&#8217; : Full Thread Dump   
key &#8216;0&#8217; : Status of Debug-key

Below is the sample out from each keys.

Debug-key &#8216;1&#8217; pressed

============ JRockitVE System Information ============   
JRockitVE version : 11.1.1.3.0-67-131044   
Kernel version : 6.1.0.0-97-131024   
JVM version : R27.6.6-28\_o-125824-1.6.0\_17-20091214-2104-linux-ia32   
Hypervisor version : Xen 3.4.0   
Boot state : 0x007effff   
Uptime : 0 days 02:04:31   
CPU : uniprocessor @2327 Mhz   
CPU usage : 0% ctx/s: 285 preempt/s: 0 migrations/s: 0   
Physical pages : 82379/261121 (321/1020 MB)   
Network info : 10.179.97.64 (10.179.97.64/255.255.254.0)   
GateWay : 10.179.96.1   
MAC address : 00:16:3e:7e:dc:78   
Boot options :   
vfsCwd : /application/user\_projects/domains/wlsve\_domain   
mainArgs : java -javaagent:/jrockitve/services/sshd/sshd.jar -cp /jrockitve/jrockit/lib/tools.jar:/jrockitve/lib/common.jar:/application/patch\_wls1032/profiles/default/sys\_manifest\_classpath/weblogic\_patch.jar:/application/wlserver\_10.3/server/lib/weblogic.jar -Dweblogic.Name=WlsveAdmin -Dweblogic.Domain=wlsve\_domain -Dweblogic.management.username=weblogic -Dweblogic.management.password=welcome1 -Dweblogic.management.GenerateDefaultConfig=true weblogic.Server   
consLog : /jrockitve/log/jrockitve.log   
mounts : ext2 / dev0;   
posixLocale : en_US   
posixTimezone : Asia/Seoul   
posixEncoding : ISO-8859-1   
Local disk : Size: 1024M, Used: 728M, Free: 295M   
========================================================

Debug-key &#8216;5&#8217; pressed   
Shutdown enabled.

Debug-key &#8216;7&#8217; pressed   
[JRockit] Management server already started. Ignoring request.

Debug-key &#8216;8&#8217; pressed   
Starting stat recording   
Debug-key &#8216;8&#8217; pressed   
========= Statistics Counters for the last second =========   
dev.eth0_rx.cnt : 22 packets   
dev.eth0\_rx\_bytes.cnt : 2704 bytes   
dev.net_interrupts.cnt : 22 interrupts   
evt.timer_ticks.cnt : 123 ticks   
hyper.priv_entries.cnt : 144 entries   
schedule.context_switches.cnt : 271 switches   
schedule.idle\_cpu\_time.cnt : 997318849 nanoseconds   
schedule.idle\_cpu\_time_0.cnt : 997318849 nanoseconds   
schedule.total\_cpu\_time.cnt : 1000031757 nanoseconds   
time.system_time.cnt : 1000 ns   
time.timer_updates.cnt : 123 updates   
time.wallclock_time.cnt : 1000 ns   
=======================================

Debug-key &#8216;9&#8217; pressed

===== FULL THREAD DUMP ===============   
Fri Jun 4 08:22:12 2010   
BEA JRockit(R) R27.6.6-28\_o-125824-1.6.0\_17-20091214-2104-linux-ia32

"Main Thread" id=1 idx=0x4 tid=1 prio=5 alive, in native, waiting   
&#8212; Waiting for notification on: weblogic/t3/srvr/T3Srvr@0x646ede8[fat lock]   
at jrockit/vm/Threads.waitForNotifySignal(JLjava/lang/Object;)Z(Native Method)   
at java/lang/Object.wait(J)V(Native Method)   
at java/lang/Object.wait(Object.java:485)   
at weblogic/t3/srvr/T3Srvr.waitForDeath(T3Srvr.java:919)   
^&#8211; Lock released while waiting: weblogic/t3/srvr/T3Srvr@0x646ede8[fat lock]   
at weblogic/t3/srvr/T3Srvr.run(T3Srvr.java:479)   
at weblogic/Server.main(Server.java:67)   
at jrockit/vm/RNI.c2java(IIIII)V(Native Method)   
&#8212; end of trace

"(Signal Handler)" id=2 idx=0x8 tid=2 prio=5 alive, in native, daemon

Open lock chains   
================   
Chain 1:   
"ExecuteThread: &#8216;0&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;" id=23 idx=0x50 tid=20 waiting for java/lang/String@0x630c588 held by:   
"ExecuteThread: &#8216;1&#8217; for queue: &#8216;weblogic.socket.Muxer&#8217;" id=24 idx=0x54 tid=21 (active)

===== END OF THREAD DUMP ===============

Debug-key &#8216;0&#8217; pressed

Debug-keys enabled

Happy Cloud Walking 🙂

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JRockit Virtual Edition的控制台调试命令[转]](http://www.beansoft.biz/2011/07/13/jrockit-virtual-edition%e7%9a%84%e6%8e%a7%e5%88%b6%e5%8f%b0%e8%b0%83%e8%af%95%e5%91%bd%e4%bb%a4%e8%bd%ac/)