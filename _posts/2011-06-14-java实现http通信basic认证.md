---
id: 2029
title: Java实现HTTP通信Basic认证
date: 2011-06-14T12:03:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2029
permalink: '/2011/06/14/java%e5%ae%9e%e7%8e%b0http%e9%80%9a%e4%bf%a1basic%e8%ae%a4%e8%af%81/'
views:
  - "5950"
original_post_id:
  - "2029"
categories:
  - Java SE
---
<pre>&nbsp;&nbsp;&nbsp; public class MyAuth extends java.net.Authenticator {</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; private String user = "";</pre>

<pre>&nbsp;</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; private String pass = "";</pre>

<pre>&nbsp;</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public MyAuth(String username, String password) {</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; user = username;</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; pass = password;</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }</pre>

<pre>&nbsp;</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; protected java.net.PasswordAuthentication getPasswordAuthentication() {</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return new java.net.PasswordAuthentication(user, pass.toCharArray());</pre>

<pre>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }</pre>

<pre>&nbsp;&nbsp;&nbsp; }</pre>

<pre>&nbsp;</pre>

<pre>java.net.Authenticator.setDefault(new MyAuth("username", "password"));</pre>

<pre>然后操作HTTP或者Socket即可.</pre>

<pre>&nbsp;</pre>

<pre>遇到的问题: 无法更新新的用户名和密码组合? 看来还是直接操控401协议会更好一些.</pre>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Java实现HTTP通信Basic认证](http://www.beansoft.biz/2011/06/14/java%e5%ae%9e%e7%8e%b0http%e9%80%9a%e4%bf%a1basic%e8%ae%a4%e8%af%81/)