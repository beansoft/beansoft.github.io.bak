---
id: 3581
title: Tomcat Native的Heartbleed漏洞
date: 2014-04-21T20:46:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3581
permalink: '/2014/04/21/tomcat-native%e7%9a%84heartbleed%e6%bc%8f%e6%b4%9e/'
views:
  - "2149"
categories:
  - Apache开源产品
tags:
  - Tomcat
---
[http://tomcat.apache.org/](http://tomcat.apache.org/ "http://tomcat.apache.org/") 参考官方网站内容, 下载11.30版本即可修正.

##### Tomcat Native 1.1.30 Released

The Apache Tomcat Project is proud to announce the release of version 1.1.30 of Tomcat Native. The notable changes since 1.1.29 include:

  * Windows binaries are linked with OpenSSL 1.0.1g. This provides a fix for [CVE-2014-0160](http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2014-0160) ([Heartbleed](https://wiki.apache.org/tomcat/Security/Heartbleed)) SSL vulnerability. 
  * Add support for ECDHE ciphers. ([55915](https://issues.apache.org/bugzilla/show_bug.cgi?id=55915))

[Download](http://tomcat.apache.org/download-native.cgi) | [ChangeLog for 1.1.30](http://tomcat.apache.org/native-doc/miscellaneous/changelog.html)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Tomcat Native的Heartbleed漏洞](http://www.beansoft.biz/2014/04/21/tomcat-native%e7%9a%84heartbleed%e6%bc%8f%e6%b4%9e/)