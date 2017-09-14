---
id: 3676
title: Apache Tomcat全系再曝严重安全漏洞
date: 2014-06-01T09:17:10+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3676
permalink: '/2014/06/01/apache-tomcat%e5%85%a8%e7%b3%bb%e5%86%8d%e6%9b%9d%e4%b8%a5%e9%87%8d%e5%ae%89%e5%85%a8%e6%bc%8f%e6%b4%9e/'
views:
  - "1703"
categories:
  - Apache开源产品
---
<p style="color: #404040;">
  整理自互联网.
</p>

<p style="color: #404040;">
  Apache Tomcat 全系产品再次爆出严重的安全漏洞，其中包括 2 个 DoS 漏洞和 3 个信息泄露漏洞。
</p>

<p style="color: #404040;">
  <img src="http://images.cnitblog.com/news/157064/201405/282056144314319.png" alt="" />
</p>

<p style="color: #404040;">
  　　<strong>1. &nbsp; CVE-2014-0095：DoS（拒绝服务）漏洞</strong>
</p>

<p style="color: #404040;">
  　　如果 AJP 请求中设置了一个长度为 0 的内容，会导致 AJP 请求挂起，这会消耗一个请求处理线程，可能导致拒绝服务攻击。
</p>

<p style="color: #404040;">
  　　受影响版本：Apache Tomcat 8.0.0-RC2~8.0.3
</p>

<p style="color: #404040;">
  　　<strong>2. &nbsp; CVE-2014-0075：DoS（拒绝服务）漏洞</strong>
</p>

<p style="color: #404040;">
  　　攻击者可以制作一个特殊大小的 chunked 请求，允许大量数据流传输到服务器，并可以绕过各种大小验证，从而导致 DoS 攻击。
</p>

<p style="color: #404040;">
  　　受影响版本：
</p>

<ul style="color: #404040;">
  <li>
    Apache Tomcat 8.0.0-RC1~8.0.3
  </li>
  <li>
    Apache Tomcat 7.0.0~7.0.52
  </li>
  <li>
    Apache Tomcat 6.0.0~6.0.39
  </li>
</ul>

<p style="color: #404040;">
  <strong>3. &nbsp; CVE-2014-0096：信息泄露漏洞</strong>
</p>

<p style="color: #404040;">
  　　默认的 servlet 可以让 Web 应用程序定义一个 XSLT，用于格式化目录列表。当在一个安全管理机制下运行时，这些进程没有受到和 Web 应用程序一样的约束条件，使得恶意 Web 应用通过使用外部 XML 来绕过安全限制。
</p>

<p style="color: #404040;">
  　　受影响版本：
</p>

<ul style="color: #404040;">
  <li>
    Apache Tomcat 8.0.0-RC1~8.0.3
  </li>
  <li>
    Apache Tomcat 7.0.0~7.0.52
  </li>
  <li>
    Apache Tomcat 6.0.0~6.0.39
  </li>
</ul>

<p style="color: #404040;">
  <strong>4. &nbsp; CVE-2014-0097：信息泄露漏洞</strong>
</p>

<p style="color: #404040;">
  　　用于解析请求内容长度头的代码没有检查溢出，这将导致请求泄露。
</p>

<p style="color: #404040;">
  　　受影响版本：
</p>

<ul style="color: #404040;">
  <li>
    Apache Tomcat 8.0.0-RC1~8.0.3
  </li>
  <li>
    Apache Tomcat 7.0.0~7.0.52
  </li>
  <li>
    Apache Tomcat 6.0.0~6.0.39
  </li>
</ul>

<p style="color: #404040;">
  <strong>5. &nbsp; CVE-2014-0119：信息泄露漏洞</strong>
</p>

<p style="color: #404040;">
  　　在特定情况下，恶意 Web 应用可能取代 Tomcat 中的 XML 解析器来处理默认 servlet 的 XSLT、JSP 文档、TLD（标签库描述符）和标签插件配置文件，注入的 XML 解析器可能会绕过针对 XML 外部实体的限制。
</p>

<p style="color: #404040;">
  　　受影响版本：
</p>

<ul style="color: #404040;">
  <li>
    Apache Tomcat 8.0.0-RC1~8.0.5
  </li>
  <li>
    Apache Tomcat 7.0.0~7.0.53
  </li>
  <li>
    Apache Tomcat 6.0.0~6.0.39
  </li>
</ul>

<p style="color: #404040;">
  <strong>解决方法：</strong>
</p>

<p style="color: #404040;">
  　　各分支产品升级至最新的版本。
</p>

<ul style="color: #404040;">
  <li>
    Tomcat 8.x 分支升级至 Tomcat 8.0.8 或更新版本
  </li>
  <li>
    Tomcat 7.x 分支升级至 Tomcat 7.0.54 或更新版本
  </li>
  <li>
    Tomcat 6.x 分支升级至 Tomcat 6.0.41 或更新版本
  </li>
</ul>

<p style="color: #404040;">
  <strong>　　下载地址</strong>：<a style="color: #005fa9;" href="http://tomcat.apache.org/" target="_blank">http://tomcat.apache.org/</a>
</p>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Apache Tomcat全系再曝严重安全漏洞](http://www.beansoft.biz/2014/06/01/apache-tomcat%e5%85%a8%e7%b3%bb%e5%86%8d%e6%9b%9d%e4%b8%a5%e9%87%8d%e5%ae%89%e5%85%a8%e6%bc%8f%e6%b4%9e/)