---
id: 1474
title: Flex解析单个JSon对象示例代码(需要corelib)
date: 2010-12-04T16:12:48+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1474
permalink: '/2010/12/04/flex%e8%a7%a3%e6%9e%90%e5%8d%95%e4%b8%aajson%e5%af%b9%e8%b1%a1%e7%a4%ba%e4%be%8b%e4%bb%a3%e7%a0%81%e9%9c%80%e8%a6%81corelib/'
views:
  - "4599"
original_post_id:
  - "1474"
categories:
  - Flash/Flex
---
<span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><?xml version="1.0" encoding="utf-8"?></span> <span lang="EN-US" style="font-size:10pt;font-family:&quot;"></span> </p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;"><mx:Application</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> xmlns:mx="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">http://www.adobe.com/2006/mxml</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" layout="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">absolute</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" xmlns:ns1="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">com.amcharts.*</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">"</span><span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;">></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <p class="MsoNormal" style="text-align:left;" align="left">
    <span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;"></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"></span>
  </p>
</p>

<span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160; </span></span><span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;"><mx:Button</span> <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">x="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">102</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" y="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">276</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" label="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">JSON Encode</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" click="jsonEncode()"</span><span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;">/></span>    <span lang="EN-US" style="font-size:10pt;font-family:&quot;"></p> 

<p>
  </span>
</p>

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160; </span></span><span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;"><mx:Button</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> x="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">210</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" y="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">276</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" label="</span><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">JSON Dncode</span><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">" click="jsonDecode()"</span><span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;">/></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160; </span></span><span lang="EN-US" style="font-size:10pt;color:#006633;font-family:&quot;"><mx:Script></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span><![CDATA[</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">import</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> com.adobe.serialization.json.JSON;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">import</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> mx.controls.*;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#<br /> 160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">private</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> </span><b><span lang="EN-US" style="font-size:10pt;color:#6699cc;font-family:&quot;">var</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> jsonStr:String ;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"></span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">private</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> </span><b><span lang="EN-US" style="font-size:10pt;color:#339966;font-family:&quot;">function</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> jsonEncode():</span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">void</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> {</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#6699cc;font-family:&quot;">var</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> stuInfo:Object = </span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">new</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> Object;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>stuInfo.faculty = </span><b><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">"fa"</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>stuInfo.major = </span><b><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">"major"</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#6699cc;font-family:&quot;">var</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> stuStr:String = JSON.encode(stuInfo);</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>jsonStr = stuStr;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span>Alert.show(stuStr, </span><b><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">"DEBUG"</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">);</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span>}</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"></span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">private</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> </span><b><span lang="EN-US" style="font-size:10pt;color:#339966;font-family:&quot;">function</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> jsonDecode():</span><b><span lang="EN-US" style="font-size:10pt;color:#0033ff;font-family:&quot;">void</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> {</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span></span><b><span lang="EN-US" style="font-size:10pt;color:#6699cc;font-family:&quot;">var</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> jsonObject:Object = JSON.decode(jsonStr);<span>&#160; </span></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"></span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span><span></span></span><b><span lang="EN-US" style="font-size:10pt;color:#6699cc;font-family:&quot;">var</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"> operation:String = jsonObject.major;</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160;&#160; </span><span></span>Alert.show(operation, </span><b><span lang="EN-US" style="font-size:10pt;color:#990000;font-family:&quot;">"DEBUG"</span></b><span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;">);</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span>}</span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160;&#160;&#160;&#160; </span>]]></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:black;font-family:&quot;"><span>&#160;&#160;&#160; </span></span><span lang="EN-US" style="font-size:10pt;color:#006633;font-family:&quot;"></mx:Script></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal" style="text-align:left;" align="left">
  <span lang="EN-US" style="font-size:10pt;color:blue;font-family:&quot;"></mx:Application></span><span lang="EN-US" style="font-size:10pt;font-family:&quot;"> </span>
</p></p> 

<p class="MsoNormal">
  <span lang="EN-US"></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/12/04/flex%e8%a7%a3%e6%9e%90%e5%8d%95%e4%b8%aajson%e5%af%b9%e8%b1%a1%e7%a4%ba%e4%be%8b%e4%bb%a3%e7%a0%81%e9%9c%80%e8%a6%81corelib/">Flex解析单个JSon对象示例代码(需要corelib)</a>
</p>