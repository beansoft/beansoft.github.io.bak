---
id: 1836
title: JavaScript身份证号码验证函数
date: 2009-02-07T10:21:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1836
permalink: '/2009/02/07/javascript%e8%ba%ab%e4%bb%bd%e8%af%81%e5%8f%b7%e7%a0%81%e9%aa%8c%e8%af%81%e5%87%bd%e6%95%b0/'
views:
  - "2538"
original_post_id:
  - "1836"
categories:
  - AJAX/JavaScript
---
网上也有一些JS的身份证号码验证函数, 不过有些没考虑到一个特殊情况: 最后一位是数字或者X. 下面给出我的一种写法供参考: 

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;">&lt;script&gt;
<span style="color:#008000;">//自定义的身份证验证函数</span><span style="color:#0000ff;">function</span> checkID(f) {
        <span style="color:#008000;">// 身份证验证 18 位数字</span><span style="color:#008000;">// 1. 18位</span><span style="color:#0000ff;">if</span>(f.ID.value.length != 18) {
        alert(<span style="color:#006080;">"请输入中国公民的18位身份证号码, 您当前输入了"</span> + f.ID.value.length + <span style="color:#006080;">"位号码"</span> );
        f.ID.focus();
        <span style="color:#0000ff;">return</span><span style="color:#0000ff;">false</span>;
    }
    <span style="color:#008000;">// 2. 确保前17位每一位都是数字</span><span style="color:#0000ff;">for</span>(i = 0; i &lt; f.ID.value.length - 1; i++) {
        <span style="color:#008000;">// 如何判断一个字母是数字</span><span style="color:#0000ff;">if</span>(isNaN( parseInt( f.ID.value.charAt(i) ) )) {
            alert(<span style="color:#006080;">"您输入的身份证号码前17位包含有字母, 不合要求"</span> );
            f.ID.focus();
            <span style="color:#0000ff;">return</span><span style="color:#0000ff;">false</span>;
        }
    }

    <span style="color:#008000;">// 3. 确保最后一位是数字或者X</span><span style="color:#0000ff;">var</span> lastIDNum = f.ID.value.charAt(17);
    <span style="color:#0000ff;">if</span>( isNaN(parseInt( f.ID.value.charAt(i) )) &&  lastIDNum.toLowerCase() != <span style="color:#006080;">'x'</span>) {
        alert(<span style="color:#006080;">"您输入的身份证号码最后一位不是数字也不是x, 不合要求"</span> );
        f.ID.focus();
        <span style="color:#0000ff;">return</span><span style="color:#0000ff;">false</span>;
    }

    <span style="color:#0000ff;">return</span><span style="color:#0000ff;">true</span>;
}
&lt;/script&gt;</pre>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [JavaScript身份证号码验证函数](http://www.beansoft.biz/2009/02/07/javascript%e8%ba%ab%e4%bb%bd%e8%af%81%e5%8f%b7%e7%a0%81%e9%aa%8c%e8%af%81%e5%87%bd%e6%95%b0/)