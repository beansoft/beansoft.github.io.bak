---
id: 599
title: JavaScript 解析 Cookie 的代码
date: 2007-10-26T10:51:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=599
permalink: '/2007/10/26/javascript-%e8%a7%a3%e6%9e%90-cookie-%e7%9a%84%e4%bb%a3%e7%a0%81/'
views:
  - "2687"
original_post_id:
  - "599"
categories:
  - AJAX/JavaScript
---
<div>
  <pre style="line-height:12pt;background-color:#f4f4f4;width:100%;font-family:consolas, &#039;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#008000;">/*</span>
<span style="color:#008000;"> * WebFXCookie class</span>
<span style="color:#008000;"> */</span>
<span style="color:#0000ff;">function</span> WebFXCookie() {
    <span style="color:#0000ff;">if</span> (document.cookie.length) { <span style="color:#0000ff;">this</span>.cookies = <span style="color:#006080;">' '</span> + document.cookie; }
}

WebFXCookie.prototype.setCookie = <span style="color:#0000ff;">function</span> (key, value) {
    document.cookie = key + <span style="color:#006080;">"="</span> + escape(value);
}

WebFXCookie.prototype.getCookie = <span style="color:#0000ff;">function</span> (key) {
    <span style="color:#0000ff;">if</span> (<span style="color:#0000ff;">this</span>.cookies) {
        <span style="color:#0000ff;">var</span> start = <span style="color:#0000ff;">this</span>.cookies.indexOf(<span style="color:#006080;">' '</span> + key + <span style="color:#006080;">'='</span>);
        <span style="color:#0000ff;">if</span> (start == -1) { <span style="color:#0000ff;">return</span> <span style="color:#0000ff;">null</span>; }
        <span style="color:#0000ff;">var</span> end = <span style="color:#0000ff;">this</span>.cookies.indexOf(<span style="color:#006080;">";"</span>, start);
        <span style="color:#0000ff;">if</span> (end == -1) { end = <span style="color:#0000ff;">this</span>.cookies.length; }
        end -= start;
        <span style="color:#0000ff;">var</span> cookie = <span style="color:#0000ff;">this</span>.cookies.substr(start,end);
        <span style="color:#0000ff;">return</span> unescape(cookie.substr(cookie.indexOf(<span style="color:#006080;">'='</span>) + 1, cookie.length - cookie.indexOf(<span style="color:#006080;">'='</span>) + 1));
    }
    <span style="color:#0000ff;">else</span> { <span style="color:#0000ff;">return</span> <span style="color:#0000ff;">null</span>; }
}



<span style="color:#0000ff;">function</span> getCookieVal (offset)
{
    <span style="color:#0000ff;">var</span> endstr=document.cookie.indexOf (<span style="color:#006080;">";"</span>,offset);<span style="color:#0000ff;">if</span> (endstr==-1)
    endstr=document.cookie.length;<span style="color:#0000ff;">return</span> unescape(document.cookie.substring(offset, endstr));
}


<span style="color:#0000ff;">function</span> GetCookie (name)
{
    <span style="color:#0000ff;">var</span> arg=name+<span style="color:#006080;">"="</span>;<span style="color:#0000ff;">var</span> alen=arg.length;<span style="color:#0000ff;">var</span> clen=document.cookie.length;<span style="color:#0000ff;">var</span> i = 0;<span style="color:#0000ff;">while</span> (i&lt;clen)
    {
        <span style="color:#0000ff;">var</span>
        j=i+alen;<span style="color:#0000ff;">if</span> (document.cookie.substring(i,j)==arg) <span style="color:#0000ff;">return</span> getCookieVal (j);i = document.cookie.indexOf(<span style="color:#006080;">" "</span>,i)+1;<span style="color:#0000ff;">if</span> (i==0)
        <span style="color:#0000ff;">break</span>;
    }
    <span style="color:#0000ff;">return</span> <span style="color:#0000ff;">null</span>;
}
<span style="color:#0000ff;">function</span> DeleteCookie (name)
{
    <span style="color:#0000ff;">var</span> exp=<span style="color:#0000ff;">new</span> Date(); exp.setTime (exp.getTime()-1); <span style="color:#0000ff;">var</span> cval=GetCookie (name);
    document.cookie=name+<span style="color:#006080;">"="</span>+cval+<span style="color:#006080;">"; expires="</span>+exp.toGMTString();
}</pre>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JavaScript 解析 Cookie 的代码](http://www.beansoft.biz/2007/10/26/javascript-%e8%a7%a3%e6%9e%90-cookie-%e7%9a%84%e4%bb%a3%e7%a0%81/)