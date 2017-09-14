---
id: 3864
title: TextWatcher如何避免在afterTextChanged中调用setText后导致死循环
date: 2016-10-26T08:44:36+00:00
author: 刘长炯
excerpt: 'EditText在addTextChangedListener添加的TextWatcher中如果在afterTextChanged方法中又重新调用了setText, 那么会重复触发对此方法的递归死循环调用, 产生ANR, 官方文档有说明:'
layout: post
guid: http://www.beansoft.biz/?p=3864
permalink: '/2016/10/26/textwatcher%e5%a6%82%e4%bd%95%e9%81%bf%e5%85%8d%e5%9c%a8aftertextchanged%e4%b8%ad%e8%b0%83%e7%94%a8settext%e5%90%8e%e5%af%bc%e8%87%b4%e6%ad%bb%e5%be%aa%e7%8e%af/'
views:
  - "4069"
categories:
  - Android
---
EditText在<span style="font-size: 9pt"><span style="font-family: Menlo">addTextChangedListener添加的</span></span><span style="font-size: 9pt"><span style="font-family: Menlo">TextWatcher中如果在afterTextChanged方法中又重新调用了setText, 那么会重复触发对此方法的递归死循环调用, 产生ANR, 官方文档有说明:</span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo"></span></span>

<span style="color:#808080;font-style:italic">/**</span><span style="color:#808080;font-style:italic"> * This method is called to notify you that, somewhere within</span><span style="color:#808080;font-style:italic"> * </span><span style="color:#808080;background-color:#e2ffe2;font-style:italic"><code></span><span style="color:#808080;font-style:italic">s</span><span style="color:#808080;background-color:#e2ffe2;font-style:italic"></code></span><span style="color:#808080;font-style:italic">, the text has been changed.</span><span style="color:#808080;font-style:italic"> * It is legitimate to make further changes to </span><span style="color:#808080;background-color:#e2ffe2;font-style:italic"><code></span><span style="color:#808080;font-style:italic">s</span><span style="color:#808080;background-color:#e2ffe2;font-style:italic"></code></span><span style="color:#808080;font-style:italic"> from</span><span style="color:#808080;font-style:italic"> * this callback, but be careful not to get yourself into an infinite</span><span style="color:#808080;font-style:italic"> * loop, because any changes you make will cause this method to be</span><span style="color:#808080;font-style:italic"> * called again <span><b>recursively</b></span>.</span><span style="color:#808080;font-style:italic"> * (You are not told where the change took place because other</span><span style="color:#808080;font-style:italic"> * afterTextChanged() methods may already have made other changes</span><span style="color:#808080;font-style:italic"> * and invalidated the offsets.  But if you need to know here,</span><span style="color:#808080;font-style:italic"> * you can use {</span><span style="color:#808080;font-weight:bold;font-style:italic">@link </span><span style="color:#808080;font-style:italic">Spannable#setSpan} in {</span><span style="color:#808080;font-weight:bold;font-style:italic">@link </span><span style="color:#808080;font-style:italic">#onTextChanged}</span><span style="color:#808080;font-style:italic"> * to mark your place and then look up from here where the span</span><span style="color:#808080;font-style:italic"> * ended up.</span><span style="color:#808080;font-style:italic"> */</span><span style="color:#000080;font-weight:bold">public void </span>afterTextChanged(Editable s);

<span style="font-size: 9pt"><span style="font-family: Menlo"></span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo">那么简单的解决办法之前就是调用setText之前暂时去掉此监听器, 然后再恢复添加自身即可.</span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo"><span style="color:#660e7a;font-weight:bold">xxxEdit</span>.addTextChangedListener(<span style="color:#000080;font-weight:bold">new </span>TextWatcher() {</span></span>

    <span style="color:#808000">@Override</span><span style="color:#808000">   </span> <span style="color:#000080;font-weight:bold">public void </span>beforeTextChanged(CharSequence s, <span style="color:#000080;font-weight:bold">int </span>start, <span style="color:#000080;font-weight:bold">int </span>count, <span style="color:#000080;font-weight:bold">int </span>after) {
  
    }
  
    <span style="color:#808000">@Override</span><span style="color:#808000">   </span> <span style="color:#000080;font-weight:bold">public void </span>onTextChanged(CharSequence s, <span style="color:#000080;font-weight:bold">int </span>start, <span style="color:#000080;font-weight:bold">int </span>before, <span style="color:#000080;font-weight:bold">int </span>count) {
  
    }
  
    <span style="color:#808000">@Override</span>

<span style="font-size: 9pt"><span style="font-family: Menlo"><span style="color:#808000">   </span> <span style="color:#000080;font-weight:bold">public void </span>afterTextChanged(Editable s) {</span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo">     </span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo"><span style="color:#660e7a;font-weight:bold">     xxxEdit</span></span></span><span style="font-size: 9pt"><span style="font-family: Menlo">.removeTextChangedListener(<span style="color:#000080;font-weight:bold">this</span>);</span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo"><span style="color:#660e7a;font-weight:bold">     xxxEdit</span></span></span>.setText(<span><b>"</b></span>**新取值"**);

<span style="font-size: 9pt"><span style="font-family: Menlo"><span style="color:#660e7a;font-weight:bold">     xxxEdit</span></span></span><span style="font-size: 9pt"><span style="font-family: Menlo">.addTextChangedListener(<span style="color:#000080;font-weight:bold">this</span>);</span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo">    }</span></span>

});

<span style="font-size: 9pt"><span style="font-family: Menlo"></span></span>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [TextWatcher如何避免在afterTextChanged中调用setText后导致死循环](http://www.beansoft.biz/2016/10/26/textwatcher%e5%a6%82%e4%bd%95%e9%81%bf%e5%85%8d%e5%9c%a8aftertextchanged%e4%b8%ad%e8%b0%83%e7%94%a8settext%e5%90%8e%e5%af%bc%e8%87%b4%e6%ad%bb%e5%be%aa%e7%8e%af/)