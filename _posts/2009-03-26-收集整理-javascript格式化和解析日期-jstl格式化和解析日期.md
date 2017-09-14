---
id: 1245
title: '收集整理: JavaScript格式化和解析日期, JSTL格式化和解析日期'
date: 2009-03-26T13:42:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1245
permalink: '/2009/03/26/%e6%94%b6%e9%9b%86%e6%95%b4%e7%90%86-javascript%e6%a0%bc%e5%bc%8f%e5%8c%96%e5%92%8c%e8%a7%a3%e6%9e%90%e6%97%a5%e6%9c%9f-jstl%e6%a0%bc%e5%bc%8f%e5%8c%96%e5%92%8c%e8%a7%a3%e6%9e%90%e6%97%a5%e6%9c%9f/'
views:
  - "3982"
original_post_id:
  - "1245"
categories:
  - JSP
---
2009-03-26 13:42 BeanSoft

JSP开发时, 在页面中格式化和解析日期始终是个头疼的事情. 可以用JSTL和JavaScript搞定.

1. JSTL格式化和解析日期

格式化日期： 

<fmt:formatDate value="${model.date}" pattern ="yyyy-MM-dd" > 

或者 

<fmt:formatDate value="<%=new java.util.Date() %>" pattern ="yyyy-MM-dd" /> 

取得request参数： 

<c:out value="param.参数名"/> 

jstl格式化日期标签收藏   
JSP Standard Tag Libraries   
Formatting and Internationalization   
Two form input parameters, &#8216;date&#8217; and &#8216;isoDate&#8217;, are URL-encoded in the link leading to this page. &#8216;isoDate&#8217; is formatted according to the ISO8601 standard.   
Formatting of numbers and dates is based on the browser&#8217;s locale setting. Formatting will change if you switch the default language setting from English to French or German, for example. (The browser needs to be restarted, too.) 

Library import and parameter capturing: 

<%@ taglib prefix="c" uri="<http://java.sun.com/jstl/core"> %>   
<%@ taglib prefix="fmt" uri="<http://java.sun.com/jstl/fmt"> %> 

<fmt:parseDate value="${param.date}" var="date" pattern="yyyy/MM/dd:HH:mm:ss>   
<fmt:parseDate value="${param.isoDate}" var="isoDate" pattern="yyyyMMdd&#8217;T&#8217;HHmmss"> 

The input parameters must match the patterns, or the JSP will thrown an exception. This page does no error handling. 

Input parameters:   
Date:&#160;&#160;&#160; 2004/04/01:13:30:00&#160;&#160; Java format: Thu Apr 01 13:30:00 CST 2004   
isoDate: 20040531T235959&#160;&#160;&#160;&#160;&#160;&#160; Java format: Mon May 31 23:59:59 CDT 2004 

Dates   
Tag Output   
Attribute: value; required. Tag has no body.   
<fmt:formatDate value="${date}" type="both"/> 

2004-4-1 13:30:00&#160;   
<fmt:formatDate value="${isoDate}" type="both"/> 

2004-5-31 23:59:59&#160;   
Attribute: type; optional. Indicates what to print: date, time, or both.   
<fmt:formatDate value="${date}" type="date"/> 

2004-4-1&#160;   
<fmt:formatDate value="${isoDate}" type="time"/> 

23:59:59&#160;   
Attribute: dateStyle; optional. Varies the date format.   
<fmt:formatDate value="${isoDate}" type="date" dateStyle="default"/> 

2004-5-31&#160;   
<fmt:formatDate value="${isoDate}" type="date" dateStyle="short"/> 

04-5-31&#160;   
<fmt:formatDate value="${isoDate}" type="date" dateStyle="medium"/> 

2004-5-31&#160;   
<fmt:formatDate value="${isoDate}" type="date" dateStyle="long"/> 

2004年5月31日&#160;   
<fmt:formatDate value="${isoDate}" type="date" dateStyle="full"/> 

2004年5月31日 星期一&#160;   
Attribute: timeStyle; optional. Varies the time format.   
<fmt:formatDate value="${isoDate}" type="time" timeStyle="default"/> 

23:59:59&#160;   
<fmt:formatDate value="${isoDate}" type="time" timeStyle="short"/> 

下午11:59&#160;   
<fmt:formatDate value="${isoDate}" type="time" timeStyle="medium"/> 

23:59:59&#160;   
<fmt:formatDate value="${isoDate}" type="time" timeStyle="long"/> 

下午11时59分59秒&#160;   
<fmt:formatDate value="${isoDate}" type="time" timeStyle="full"/> 

下午11时59分59秒 CDT&#160;   
Attribute: pattern; optional. Inidcates date/time custom patterns.   
<fmt:formatDate value="${date}" type="both" pattern="EEEE, MMMM d, yyyy HH:mm:ss Z"/> 

星期四, 四月 1, 2004 13:30:00 -0600&#160;   
<fmt:formatDate value="${isoDate}" type="both" pattern="d MMM yy, h:m:s a zzzz/> 

&#160; 

2. JavaScript 格式化 

来源: [http://gwbasic.javaeye.com/blog/36904](http://gwbasic.javaeye.com/blog/36904 "http://gwbasic.javaeye.com/blog/36904") 

&#160; 

/*   
&#160; 将String类型解析为Date类型.   
&#160; parseDate(&#8216;2006-1-1&#8217;) return new Date(2006,0,1)   
&#160; parseDate(&#8216; 2006-1-1 &#8216;) return new Date(2006,0,1)   
&#160; parseDate(&#8216;2006-1-1 15:14:16&#8217;) return new Date(2006,0,1,15,14,16)   
&#160; parseDate(&#8216; 2006-1-1 15:14:16 &#8216;) return new Date(2006,0,1,15,14,16);   
&#160; parseDate(&#8216;2006-1-1 15:14:16.254&#8217;) return new Date(2006,0,1,15,14,16,254)   
&#160; parseDate(&#8216; 2006-1-1 15:14:16.254 &#8216;) return new Date(2006,0,1,15,14,16,254)   
&#160; parseDate(&#8216;不正确的格式&#8217;) retrun null   
*/   
function parseDate(str){   
&#160; if(typeof str == &#8216;string&#8217;){   
&#160;&#160;&#160; var results = str.match(/^ \*(d{4})-(d{1,2})-(d{1,2}) \*$/);   
&#160;&#160;&#160; if(results && results.length>3)   
&#160;&#160;&#160;&#160;&#160; return new Date(parseInt(results[1]),parseInt(results[2]) -1,parseInt(results[3]));   
&#160;&#160;&#160; results = str.match(/^ \*(d{4})-(d{1,2})-(d{1,2}) +(d{1,2}):(d{1,2}):(d{1,2}) \*$/);   
&#160;&#160;&#160; if(results && results.length>6)   
&#160;&#160;&#160;&#160;&#160; return new Date(parseInt(results[1]),parseInt(results[2]) -1,parseInt(results[3]),parseInt(results[4]),parseInt(results[5]),parseInt(results[6]));   
&#160;&#160;&#160; results = str.match(/^ \*(d{4})-(d{1,2})-(d{1,2}) +(d{1,2}):(d{1,2}):(d{1,2}).(d{1,9}) \*$/);   
&#160;&#160;&#160; if(results && results.length>7)   
&#160;&#160;&#160;&#160;&#160; return new Date(parseInt(results[1]),parseInt(results[2]) -1,parseInt(results[3]),parseInt(results[4]),parseInt(results[5]),parseInt(results[6]),parseInt(results[7]));   
&#160; }   
&#160; return null;   
} 

/*   
&#160; 将Date/String类型,解析为String类型.   
&#160; 传入String类型,则先解析为Date类型   
&#160; 不正确的Date,返回 &#8221;   
&#160; 如果时间部分为0,则忽略,只返回日期部分.   
*/   
function formatDate(v){   
&#160; if(typeof v == &#8216;string&#8217;) v = parseDate(v);   
&#160; if(v instanceof Date){   
&#160;&#160;&#160; var y = v.getFullYear();   
&#160;&#160;&#160; var m = v.getMonth() + 1;   
&#160;&#160;&#160; var d = v.getDate();   
&#160;&#160;&#160; var h = v.getHours();   
&#160;&#160;&#160; var i = v.getMinutes();   
&#160;&#160;&#160; var s = v.getSeconds();   
&#160;&#160;&#160; var ms = v.getMilliseconds();&#160;&#160;   
&#160;&#160;&#160; if(ms>0) return y + &#8216;-&#8216; + m + &#8216;-&#8216; + d + &#8216; &#8216; + h + &#8216;:&#8217; + i + &#8216;:&#8217; + s + &#8216;.&#8217; + ms;   
&#160;&#160;&#160; if(h>0 || i>0 || s>0) return y + &#8216;-&#8216; + m + &#8216;-&#8216; + d + &#8216; &#8216; + h + &#8216;:&#8217; + i + &#8216;:&#8217; + s;   
&#160;&#160;&#160; return y + &#8216;-&#8216; + m + &#8216;-&#8216; + d;   
&#160; }   
&#160; return &#8221;;   
}

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [收集整理: JavaScript格式化和解析日期, JSTL格式化和解析日期](http://www.beansoft.biz/2009/03/26/%e6%94%b6%e9%9b%86%e6%95%b4%e7%90%86-javascript%e6%a0%bc%e5%bc%8f%e5%8c%96%e5%92%8c%e8%a7%a3%e6%9e%90%e6%97%a5%e6%9c%9f-jstl%e6%a0%bc%e5%bc%8f%e5%8c%96%e5%92%8c%e8%a7%a3%e6%9e%90%e6%97%a5%e6%9c%9f/)