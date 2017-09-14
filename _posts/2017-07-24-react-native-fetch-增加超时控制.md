---
id: 3927
title: React Native fetch 增加超时控制
date: 2017-07-24T13:14:40+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3927
permalink: '/2017/07/24/react-native-fetch-%e5%a2%9e%e5%8a%a0%e8%b6%85%e6%97%b6%e6%8e%a7%e5%88%b6/'
views:
  - "218"
categories:
  - Uncategorized
---
</p> 

RN的fetch方法默认是没有超时控制的, 但我们可以参考下列代码实现超时控制:



<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;"><span style="color:#000080;font-weight:bold;">let </span><span style="color:#458383;">oldFetchfn </span>= <span style="color:#660e7a;font-weight:bold;font-style:italic;">fetch</span>; <span style="color:#808080;font-style:italic;">//拦截原始的fetch方法<br /></span><span style="color:#808080;font-style:italic;"><br /></span><span style="color:#000080;font-weight:bold;">const </span><span style="color:#458383;">timeout </span>= <span style="color:#0000ff;">5000</span>;<span style="color:#808080;font-style:italic;">// 5秒请求超时<br /></span><span style="color:#000080;font-weight:bold;">function</span><span style="color: rgb(122, 122, 67); font-size: 10.5pt;"> _fetch</span><span style="font-size: 10.5pt;">(input, opts) {</span><span style="font-size: 10.5pt; color: rgb(128, 128, 128); font-style: italic;">//定义新的fetch方法，封装原有的fetch方法, 支持超时</span></pre>

<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;"><span style="color:#808080;font-style:italic;">    </span><span style="color:#000080;font-weight:bold;">let </span><span style="color:#458383;">fetchPromise </span>= <span style="color:#458383;">oldFetchfn</span>(input, opts);<br /><br />    <span style="color:#000080;font-weight:bold;">if</span>(opts.<span style="color:#660e7a;font-weight:bold;">timeout </span>=== <span style="color:#660e7a;font-weight:bold;">undefined</span>) {<br />        opts.<span style="color:#660e7a;font-weight:bold;">timeout </span>= <span style="color:#458383;">timeout</span>;<br />    }<br /><br />    <span style="color:#000080;font-weight:bold;">let </span><span style="color:#458383;">timeoutPromise </span>= <span style="color:#000080;font-weight:bold;">new </span>Promise(<span style="color:#000080;font-weight:bold;">function</span>(resolve, reject){<br />        <span style="color:#7a7a43;">setTimeout</span>(()=&gt;{<br />            <span style="color:#660e7a;font-weight:bold;">console</span>.<span style="color:#7a7a43;">log</span>(<span style="color:#008000;font-weight:bold;">"HTTPBase._fetch() 请求超时!"</span>);<br />            reject({<span style="color:#008000;font-weight:bold;">'code'</span>:  <span style="color:#008000;font-weight:bold;">'408'</span>, <span style="color:#008000;font-weight:bold;">'msg'</span>:  <span style="color:#008000;font-weight:bold;">'网络请求超时'</span>});<br />        }, opts.<span style="color:#660e7a;font-weight:bold;">timeout</span>)<br />    });<br /><br />    <span style="color:#000080;font-weight:bold;">return </span>Promise.<span style="color:#7a7a43;">race</span>([<span style="color:#458383;">fetchPromise</span>, <span style="color:#458383;">timeoutPromise</span>]);<br />};</pre>

<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;"><br /></pre>

<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;">参考资料: </pre>

<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;">http://www.cnblogs.com/wonyun/p/fetch_polyfill_timeout_jsonp_cookie_progress.html</pre>

<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;">https://github.com/whatwg/fetch/issues/20</pre>

<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;"><br /></pre>

<pre style="background-color: rgb(255, 255, 255); font-family: 'Microsoft YaHei'; font-size: 10.5pt;"><br /></pre></p> </p> 

</body></html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [React Native fetch 增加超时控制](http://www.beansoft.biz/2017/07/24/react-native-fetch-%e5%a2%9e%e5%8a%a0%e8%b6%85%e6%97%b6%e6%8e%a7%e5%88%b6/)