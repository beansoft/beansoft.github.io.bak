---
id: 2288
title: DomainHealth 1.0.0 发布
date: 2011-10-07T17:25:05+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2288
permalink: '/2011/10/07/domainhealth-1-0-0-%e5%8f%91%e5%b8%83/'
views:
  - "9993"
original_post_id:
  - "2288"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - DomainHealth
---
DomainHealth是一款开源免费的监控WebLogic服务器的Web应用, 发布日期为2011-10-05.

<http://sourceforge.net/projects/domainhealth/>

[http://sourceforge.net/apps/mediawiki/domainhealth](http://sourceforge.net/apps/mediawiki/domainhealth "http://sourceforge.net/apps/mediawiki/domainhealth")

&#160;

&#160;

=== DomainHealth 1.0.0 ===&#160; 

DATE:   
05 October 2011 

SUMMARY:   
Mainly a bug fix and minor enhancement release to provide a stable full features 1.0 version &#8211; also added optional support for showing host machine statistics (CPU, Memory, and Network usage) by using the WLHostMachineStats application, if deployed to the WebLogic domain, see: <https://sourceforge.net/projects/wlhostmchnstats/)>.   
DomainHealth is an open source "zero-config" monitoring tool for WebLogic. It collects important server metrics over time, archives these into CSV files and provides a simple web interface for viewing graphs of current and historical statistics. 

PROJECT HOME / DOWNLOAD:   
<http://sourceforge.net/projects/domainhealth/>

HELP DOCUMENTATION:   
<http://sourceforge.net/apps/mediawiki/domainhealth>

HOW-TO DEPLOY:   
1. Navigate to the project home page&#8217;s and download the following JEE web-application: domainhealth-100.war   
2. Deploy domainhealth-100.war to WebLogic, targeted to the Admin Server server of the domain only   
3. Using a Web Browser, navigate to: <http://adminhost:port/domainhealth>&#160; Eg.: <http://localhost:7001/domainhealth>   
&#160;&#160;&#160; (statistics may take a few minutes to appear &#8211; keep pressing the Latest Time (right arrow) Button) 

DEPLOYMENT CAUTION:   
If you are REPLACING a previous version of DomainHealth (DH), first undeploy the old DH version, then delete (or archive off) the old &#8216;statistics&#8217; directory containing the previously collected CSV files (usually located at <domainhonme>/logs/statistics), then deploy the new DH version. This is required because the latest DH version is not backwards compatible with the CSV format used in older DH versions. 

WEBLOGIC VERSIONS:   
Supports all WebLogic version from 9.0 to 10.3.x&#160; (including Exalogic, in addition to generic hardware platforms) 

NOTES:   
See the help documentation link above, especially if your WebLogic administrator is not called &#8216;weblogic&#8217;, if you need to force use of JMX Polling for data capture (i.e.. not use WLDF on WLS 10.3+) and/or if you need to change the path of the output directory for generated CSV files. 

&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;   
DomainHealth &#8211; version 1.0.0 &#8211; CHANGES 

&#160; * ENH#2782810 &#8211; Capture and display CPU, memory, network OS stats   
&#160; * ENH#3411845&#160;&#160;&#160; &#8211; CodeImprovement &#8211; Simplify background threading code   
&#160; * ENH#2989273 &#8211; CodeImprovement &#8211; Provide Tag Lib for URL param generation 

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [DomainHealth 1.0.0 发布](http://www.beansoft.biz/2011/10/07/domainhealth-1-0-0-%e5%8f%91%e5%b8%83/)