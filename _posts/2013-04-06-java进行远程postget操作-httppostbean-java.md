---
id: 3388
title: '<!--:zh-->Java进行远程POST/GET操作 HttpPostBean.java<!--:--><!--:en-->Java do remote POST/GET operation HttpPostBean.java<!--:-->'
date: 2013-04-06T20:21:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3388
permalink: '/2013/04/06/java%e8%bf%9b%e8%a1%8c%e8%bf%9c%e7%a8%8bpostget%e6%93%8d%e4%bd%9c-httppostbean-java/'
views:
  - "4503"
categories:
  - Java SE
tags:
  - GET
  - Java
  - POST
---
<!--:zh-->后台支持tomcat,weblogic,resin等.

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/* </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @(#)HttpPostBean.java 1.01 2005-5-1</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Copyright 2005 ~ 2013 BeanSoft.biz.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* This class is free to modify or redistricute without any limitations.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">package</span> beansoft.net;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.io.ByteArrayOutputStream;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.io.DataOutputStream;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.io.InputStream;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.MalformedURLException;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.URL;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.URLConnection;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.URLEncoder;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.util.Enumeration;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.util.Hashtable;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

HttpPostBean performs a http post/get action and reads the response from the

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*  server.</pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* A sample code to use this Bean:</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">HttpPostBean httpPostBean = new HttpPostBean();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.setUrl("http://localhost/test.jsp");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.addParameter("name", "beansoft");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.addParameter("email", "beansoftstudio@msn.com");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.setEncoding("UTF-8");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">if(httpPostBean.doPost()) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.out.println(httpPostBean.getResponse());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Also you can use GET method to send these parameters:</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre>httpPostBean.setMethod("get");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* The corresponding JSP file content(note: this file does not handling encoding problems):</pre>

<pre></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.out.println("name=" + request.gerParameter("name") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.out.println("email=" + request.gerParameter("email") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">out.println("name=" + request.gerParameter("name") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">out.println("email=" + request.gerParameter("email") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">%&gt;</pre>

<pre></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @author BeanSoft</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @version 1.0</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> HttpPostBean {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The character encoding used to encode parameters. */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> String encoding = "<span style="color: #8b0000;">UTF-8</span>";</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The parameters to post */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> Hashtable parameters = <span style="color: #0000ff;">new</span> Hashtable();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The url to connect to */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> String url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The response from the server when doing a connection operation */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> <span style="color: #0000ff;">byte</span>[] response;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** HTTP form method, POST or GET, default to POST */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> String method = "<span style="color: #8b0000;">post</span>";</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Do the post action and read the response from the server.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return boolean , false if any error occurs.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">boolean</span> doPost() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (url == <span style="color: #0000ff;">null</span> || url.length() == 0)</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">try</span> {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">URL url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">URLConnection urlConn;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">DataOutputStream printout;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// URL of HTTP pages which handles the POST action.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">url = <span style="color: #0000ff;">new</span> URL(getUrl());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">boolean</span> isPost = "<span style="color: #8b0000;">post</span>".equalsIgnoreCase(getMethod());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// If there is always a ? in url, then do not append it to the address again</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">String urlGetMethod = getUrl().indexOf("<span style="color: #8b0000;">?</span>") == -1 ? getUrl() + "<span style="color: #8b0000;">?</span>" : getUrl();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">String content = "";<span style="color: #008000;">// Content to post</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">Enumeration enumeration = parameters.keys();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">boolean</span> first = <span style="color: #0000ff;">true</span>;<span style="color: #008000;">// Is this the first parameter?</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">while</span> (enumeration.hasMoreElements()) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">String key = enumeration.nextElement().toString();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (first == <span style="color: #0000ff;">false</span>) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">content += "<span style="color: #8b0000;">&</span>";</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// if (isPost) {</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// content += URLEncoder.encode(key, getEncoding())</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// + "="</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// + URLEncoder.encode(parameters.get(key).toString(),</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// getEncoding());</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// } else {</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// content += key + "=" + parameters.get(key);</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// }</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">content += URLEncoder.encode(key, getEncoding())</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">+ "<span style="color: #8b0000;">=</span>"</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">+ URLEncoder.encode(parameters.get(key).toString(),</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">getEncoding());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">first = <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (!isPost) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlGetMethod += content;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">url = <span style="color: #0000ff;">new</span> URL(urlGetMethod);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// URL connection channel.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn = url.openConnection();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Let the run-time system (RTS) know that we want input.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setDoInput(<span style="color: #0000ff;">true</span>);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Let the RTS know that we want to do output.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setDoOutput(<span style="color: #0000ff;">true</span>);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// No caching, we want the real thing.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setUseCaches(<span style="color: #0000ff;">false</span>);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (isPost) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Specify the content type.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setRequestProperty("<span style="color: #8b0000;">Content-Type</span>",</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">"<span style="color: #8b0000;">application/x-www-form-urlencoded</span>");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Send POST output.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout = <span style="color: #0000ff;">new</span> DataOutputStream(urlConn.getOutputStream());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout.writeBytes(content);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout.flush();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout.close();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Get response data.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(<span style="color: #0000ff;">null</span>); <span style="color: #008000;">// Clear response string</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">int</span> data = 0;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">ByteArrayOutputStream bout = <span style="color: #0000ff;">new</span> ByteArrayOutputStream();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">InputStream in = urlConn.getInputStream();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">while</span> ((data = in.read()) != -1) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">bout.write(data);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(bout.toByteArray());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">in.close();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">true</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">} <span style="color: #0000ff;">catch</span> (MalformedURLException me) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// System.err.println("MalformedURLException: " + me.getMessage());</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(("" + me).getBytes());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">} <span style="color: #0000ff;">catch</span> (Exception ex) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.err.println("<span style="color: #8b0000;">Exception: </span>" + ex.getMessage());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(("" + ex).getBytes());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// ex.printStackTrace();</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Add a form parameter.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param key -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            parameter name</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param value -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            parameter value</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> addParameter(String key, String value) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (value == <span style="color: #0000ff;">null</span> || value.length() == 0) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">removeParameter(key);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">} <span style="color: #0000ff;">else</span> {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">parameters.put(key, value);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Remove a form parameter from the request.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param key -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            parameter name</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> removeParameter(String key) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (key != <span style="color: #0000ff;">null</span>) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">parameters.remove(key);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Return the URL this bean will connect to.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return a URL in string format</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> String getUrl() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Set a URL this bean will connect to.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param url</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            a URL string without form parameters, eg:</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            http://www.abc.com/index.jsp , and</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            http://www.abc.com/index.jsp?name=value will cause some error</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            when u use HTTP GET method.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> setUrl(String url) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.url = url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Responsed data by server.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return byte[] - the data</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">byte</span>[] getResponse() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> response;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Set esponsed data by server</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param response -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            byte[], data array</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> <span style="color: #0000ff;">void</span> setResponse(<span style="color: #0000ff;">byte</span>[] response) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.response = response;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return returns the form method.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> String getMethod() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> method;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param method</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            The form method to set, valid values is {"get", "post"}, null</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            value means "post".</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> setMethod(String method) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.method = method;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Default encoding is UTF-8.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return returns encoding.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> String getEncoding() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> encoding;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Default encoding is UTF-8.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param encoding The encoding to set.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> setEncoding(String encoding) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.encoding = encoding;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<!--:-->

<!--:en-->Supports backend server such as tomcat,weblogic,resin etc.

<pre></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/* </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @(#)HttpPostBean.java 1.01 2005-5-1</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Copyright 2005 ~ 2013 BeanSoft.biz.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* This class is free to modify or redistricute without any limitations.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">package</span> beansoft.net;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.io.ByteArrayOutputStream;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.io.DataOutputStream;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.io.InputStream;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.MalformedURLException;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.URL;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.URLConnection;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.net.URLEncoder;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.util.Enumeration;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">import</span> java.util.Hashtable;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

HttpPostBean performs a http post/get action and reads the response from the

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*  server.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* A sample code to use this Bean:</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">HttpPostBean httpPostBean = new HttpPostBean();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.setUrl("http://localhost/test.jsp");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.addParameter("name", "beansoft");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.addParameter("email", "beansoftstudio@msn.com");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">httpPostBean.setEncoding("UTF-8");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">if(httpPostBean.doPost()) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.out.println(httpPostBean.getResponse());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Also you can use GET method to send these parameters:</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre>httpPostBean.setMethod("get");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* The corresponding JSP file content(note: this file does not handling encoding problems):</pre>

<pre></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.out.println("name=" + request.gerParameter("name") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.out.println("email=" + request.gerParameter("email") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">out.println("name=" + request.gerParameter("name") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">out.println("email=" + request.gerParameter("email") + "
");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">%&gt;</pre>

<pre></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @author BeanSoft</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @version 1.0</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span> HttpPostBean {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The character encoding used to encode parameters. */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> String encoding = "<span style="color: #8b0000;">UTF-8</span>";</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

&nbsp;

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The parameters to post */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> Hashtable parameters = <span style="color: #0000ff;">new</span> Hashtable();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The url to connect to */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> String url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** The response from the server when doing a connection operation */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> <span style="color: #0000ff;">byte</span>[] response;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** HTTP form method, POST or GET, default to POST */</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> String method = "<span style="color: #8b0000;">post</span>";</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Do the post action and read the response from the server.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return boolean , false if any error occurs.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">boolean</span> doPost() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (url == <span style="color: #0000ff;">null</span> || url.length() == 0)</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">try</span> {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">URL url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">URLConnection urlConn;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">DataOutputStream printout;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// URL of HTTP pages which handles the POST action.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">url = <span style="color: #0000ff;">new</span> URL(getUrl());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">boolean</span> isPost = "<span style="color: #8b0000;">post</span>".equalsIgnoreCase(getMethod());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// If there is always a ? in url, then do not append it to the address again</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">String urlGetMethod = getUrl().indexOf("<span style="color: #8b0000;">?</span>") == -1 ? getUrl() + "<span style="color: #8b0000;">?</span>" : getUrl();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">String content = "";<span style="color: #008000;">// Content to post</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">Enumeration enumeration = parameters.keys();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">boolean</span> first = <span style="color: #0000ff;">true</span>;<span style="color: #008000;">// Is this the first parameter?</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">while</span> (enumeration.hasMoreElements()) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">String key = enumeration.nextElement().toString();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (first == <span style="color: #0000ff;">false</span>) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">content += "<span style="color: #8b0000;">&</span>";</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// if (isPost) {</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// content += URLEncoder.encode(key, getEncoding())</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// + "="</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// + URLEncoder.encode(parameters.get(key).toString(),</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// getEncoding());</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// } else {</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// content += key + "=" + parameters.get(key);</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// }</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">content += URLEncoder.encode(key, getEncoding())</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">+ "<span style="color: #8b0000;">=</span>"</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">+ URLEncoder.encode(parameters.get(key).toString(),</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">getEncoding());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">first = <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (!isPost) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlGetMethod += content;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">url = <span style="color: #0000ff;">new</span> URL(urlGetMethod);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// URL connection channel.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn = url.openConnection();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Let the run-time system (RTS) know that we want input.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setDoInput(<span style="color: #0000ff;">true</span>);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Let the RTS know that we want to do output.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setDoOutput(<span style="color: #0000ff;">true</span>);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// No caching, we want the real thing.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setUseCaches(<span style="color: #0000ff;">false</span>);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (isPost) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Specify the content type.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">urlConn.setRequestProperty("<span style="color: #8b0000;">Content-Type</span>",</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">"<span style="color: #8b0000;">application/x-www-form-urlencoded</span>");</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Send POST output.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout = <span style="color: #0000ff;">new</span> DataOutputStream(urlConn.getOutputStream());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout.writeBytes(content);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout.flush();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">printout.close();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// Get response data.</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(<span style="color: #0000ff;">null</span>); <span style="color: #008000;">// Clear response string</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">int</span> data = 0;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">ByteArrayOutputStream bout = <span style="color: #0000ff;">new</span> ByteArrayOutputStream();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">InputStream in = urlConn.getInputStream();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">while</span> ((data = in.read()) != -1) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">bout.write(data);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(bout.toByteArray());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">in.close();</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">true</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">} <span style="color: #0000ff;">catch</span> (MalformedURLException me) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// System.err.println("MalformedURLException: " + me.getMessage());</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(("" + me).getBytes());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">} <span style="color: #0000ff;">catch</span> (Exception ex) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">System.err.println("<span style="color: #8b0000;">Exception: </span>" + ex.getMessage());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">setResponse(("" + ex).getBytes());</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">// ex.printStackTrace();</span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> <span style="color: #0000ff;">false</span>;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Add a form parameter.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param key -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            parameter name</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param value -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            parameter value</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> addParameter(String key, String value) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (value == <span style="color: #0000ff;">null</span> || value.length() == 0) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">removeParameter(key);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">} <span style="color: #0000ff;">else</span> {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">parameters.put(key, value);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Remove a form parameter from the request.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param key -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            parameter name</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> removeParameter(String key) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">if</span> (key != <span style="color: #0000ff;">null</span>) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">parameters.remove(key);</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Return the URL this bean will connect to.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return a URL in string format</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> String getUrl() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Set a URL this bean will connect to.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param url</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            a URL string without form parameters, eg:</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            http://www.abc.com/index.jsp , and</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            http://www.abc.com/index.jsp?name=value will cause some error</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            when u use HTTP GET method.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> setUrl(String url) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.url = url;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Responsed data by server.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return byte[] - the data</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">byte</span>[] getResponse() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> response;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Set esponsed data by server</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param response -</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            byte[], data array</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">private</span> <span style="color: #0000ff;">void</span> setResponse(<span style="color: #0000ff;">byte</span>[] response) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.response = response;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return returns the form method.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> String getMethod() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> method;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param method</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            The form method to set, valid values is {"get", "post"}, null</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*            value means "post".</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> setMethod(String method) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.method = method;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Default encoding is UTF-8.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @return returns encoding.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> String getEncoding() {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">return</span> encoding;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #008000;">/** </span></pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* Default encoding is UTF-8.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">* @param encoding The encoding to set.</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">*/</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">void</span> setEncoding(String encoding) {</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;"><span style="color: #0000ff;">this</span>.encoding = encoding;</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<pre style="background-color: #ffffff; margin: 0em; width: 100%; font-family: consolas,'Courier New',courier,monospace; font-size: 12px;">}</pre>

<!--:-->

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [<!--:zh-->Java进行远程POST/GET操作 HttpPostBean.java

<!--:-->

<!--:en-->Java do remote POST/GET operation HttpPostBean.java

<!--:-->](http://www.beansoft.biz/2013/04/06/java%e8%bf%9b%e8%a1%8c%e8%bf%9c%e7%a8%8bpostget%e6%93%8d%e4%bd%9c-httppostbean-java/)