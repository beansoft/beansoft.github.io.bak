---
id: 3838
title: OkHttp 2.x 的 Interceptor 无法读取Http请求时发出的header的问题及解决方案
date: 2016-08-30T11:29:28+00:00
author: 刘长炯
excerpt: 项目中使用了 okhttp:2.7.5, 上层是Retrofit. 因为App端最经常出现的问题就是发现某页面不可用, 那么就需要可视化展示请求结果. 所以我参考了这个文章: https://github.com/square/okhttp/wiki/Interceptors , 并参考了代码
layout: post
guid: http://www.beansoft.biz/?p=3838
permalink: '/2016/08/30/okhttp-2-x-%e7%9a%84-interceptor-%e6%97%a0%e6%b3%95%e8%af%bb%e5%8f%96http%e8%af%b7%e6%b1%82%e6%97%b6%e5%8f%91%e5%87%ba%e7%9a%84header%e7%9a%84%e9%97%ae%e9%a2%98%e5%8f%8a%e8%a7%a3%e5%86%b3%e6%96%b9/'
views:
  - "2542"
categories:
  - Android
---
项目中使用了 okhttp:2.7.5, 上层是Retrofit. 因为App端最经常出现的问题就是发现某页面不可用, 那么就需要可视化展示请求结果. 所以我参考了这个文章: <a rev="en_rl_minimal" href="https://github.com/square/okhttp/wiki/Interceptors">https://github.com/square/okhttp/wiki/Interceptors</a> , 并参考了代码

<a rev="en_rl_small" href="https://github.com/square/okhttp/blob/parent-2.7.5/okhttp-logging-interceptor/src/main/java/com/squareup/okhttp/logging/HttpLoggingInterceptor.java">https://github.com/square/okhttp/blob/parent-2.7.5/okhttp-logging-interceptor/src/main/java/com/squareup/okhttp/logging/HttpLoggingInterceptor.java</a>

进行了测试, 然而很惊讶的发现, request 中的Header总是为空, 具体代码:

<span style="color:#808000">@Override </span><span style="color:#000080;font-weight:bold">public </span>Response intercept(Chain chain) <span style="color:#000080;font-weight:bold">throws </span>IOException {
  
  Level level = <span style="color:#000080;font-weight:bold">this</span>.<span style="color:#660e7a;font-weight:bold">level</span>;
  
  Request request = chain.request();

// 此处省略若干行

    Headers headers = request.headers();
  
    <span style="color:#000080;font-weight:bold">for </span>(<span style="color:#000080;font-weight:bold">int </span>i = <span style="color:#0000ff"></span>, count = headers.size(); i < count; i++) {
  
      String name = headers.name(i);
  
      <span style="color:#808080;font-style:italic">// Skip headers from the request body as they are explicitly logged above.</span><span style="color:#808080;font-style:italic">     </span> <span style="color:#000080;font-weight:bold">if </span>(!<span style="color:#008000;font-weight:bold">"Content-Type"</span>.equalsIgnoreCase(name) && !<span style="color:#008000;font-weight:bold">"Content-Length"</span>.equalsIgnoreCase(name)) {
  
        <span style="color:#660e7a;font-weight:bold">logger</span>.log(name + <span style="color:#008000;font-weight:bold">": " </span>+ headers.value(i));
  
      }

<span style="font-size: 9pt"><span style="font-family: Menlo">    }</span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo"></span></span>

<span style="font-size: 9pt"><span style="font-family: Menlo">那么总是为空, 问题出在哪里呢?后来发现 OkHttp支持两种类型的拦截器:</span></span>

application 和 network interceptors.

区别如下, 但是并没有提到Http头的问题:

**Application interceptors**

  * Don&#8217;t need to worry about intermediate responses like redirects and retries.
  * Are always invoked once, even if the HTTP response is served from the cache.
  * Observe the application&#8217;s original intent. Unconcerned with OkHttp-injected headers like `If-None-Match`.
  * Permitted to short-circuit and not call `Chain.proceed()`.
  * Permitted to retry and make multiple calls to `Chain.proceed()`.

**Network Interceptors**

  * Able to operate on intermediate responses like redirects and retries.
  * Not invoked for cached responses that short-circuit the network.
  * Observe the data just as it will be transmitted over the network.
  * Access to the `Connection` that carries the request.

, 之前的代码是这样添加的应用拦截器:

<span style="color:#660e7a;font-weight:bold">okHttpClient</span>.interceptors().add(logging)

, 现在修改为:

<span style="color:#660e7a;font-weight:bold">okHttpClient</span>.networkInterceptors().add(logging);

问题解决.

<span style="font-size: 13px"><span><span style="font-family: Menlo"><b>但是一个新的问题又出现了:</b></span></span></span>

**<span style="font-family: Menlo"><span><span><span style="font-size: 12px"><span style="font-size: 13px">如果网络出现故障比如域名解析失败的时候, 只会走 Application interceptors, 而完全不走 Network Interceptors, 这对异常处理来说是个灾难!</span></span></span></span></span>**

**<span style="font-size: 13px"><span style="font-family: Menlo"><span></span></span></span>**

源码逻辑:

先走 应用拦截器, 没有异常时才会通过 Call 类的 

Response getResponse(Request request, <span style="color:#000080;font-weight:bold">boolean </span>forWebSocket) <span style="color:#000080;font-weight:bold">throws </span>IOException 方法

走入 HttpEngine, 这时候才会执行到NetworkInterceptors.

Header的真正加入是在这个方法里面开始进行的.

在HttpEngine中又加入了剩下的一些头包括Cookie等:

<span style="color:#808080;font-style:italic">/**</span><span style="color:#808080;font-style:italic"> * Populates request with defaults and cookies.</span><span style="color:#808080;font-style:italic"> *</span><span style="color:#808080;font-style:italic"> * </span><span style="color:#808080;background-color:#e2ffe2;font-style:italic"><p></span><span style="color:#808080;font-style:italic">This client doesn&#8217;t specify a default {</span><span style="color:#808080;font-weight:bold;font-style:italic">@code </span><span style="color:#808080;font-style:italic">Accept} header because it</span><span style="color:#808080;font-style:italic"> * doesn&#8217;t know what content types the application is interested in.</span><span style="color:#808080;font-style:italic"> */</span><span style="color:#000080;font-weight:bold">private </span>Request networkRequest(Request request) <span style="color:#000080;font-weight:bold">throws </span>IOException {
  
  Request.Builder result = request.newBuilder();
  
  <span style="color:#000080;font-weight:bold">if </span>(request.header(<span style="color:#008000;font-weight:bold">"Host"</span>) == <span style="color:#000080;font-weight:bold">null</span>) {
  
    result.header(<span style="color:#008000;font-weight:bold">"Host"</span>, Util.<span style="font-style:italic">hostHeader</span>(request.httpUrl()));
  
  }
  
  <span style="color:#000080;font-weight:bold">if </span>(request.header(<span style="color:#008000;font-weight:bold">"Connection"</span>) == <span style="color:#000080;font-weight:bold">null</span>) {
  
    result.header(<span style="color:#008000;font-weight:bold">"Connection"</span>, <span style="color:#008000;font-weight:bold">"Keep-Alive"</span>);
  
  }
  
  <span style="color:#000080;font-weight:bold">if </span>(request.header(<span style="color:#008000;font-weight:bold">"Accept-Encoding"</span>) == <span style="color:#000080;font-weight:bold">null</span>) {
  
    <span style="color:#660e7a;font-weight:bold">transparentGzip </span>= <span style="color:#000080;font-weight:bold">true</span>;
  
    result.header(<span style="color:#008000;font-weight:bold">"Accept-Encoding"</span>, <span style="color:#008000;font-weight:bold">"gzip"</span>);

<span style="font-size: 9pt"><span style="font-family: Menlo">  }</span></span>

  CookieHandler cookieHandler = <span style="color:#660e7a;font-weight:bold">client</span>.getCookieHandler();
  
  <span style="color:#000080;font-weight:bold">if </span>(cookieHandler != <span style="color:#000080;font-weight:bold">null</span>) {
  
    <span style="color:#808080;font-style:italic">// Capture the request headers added so far so that they can be offered to the CookieHandler.</span><span style="color:#808080;font-style:italic">    // This is mostly to stay close to the RI; it is unlikely any of the headers above would</span><span style="color:#808080;font-style:italic">    // affect cookie choice besides "Host".</span><span style="color:#808080;font-style:italic">   </span> Map<String, List<String>> headers = OkHeaders.<span style="font-style:italic">toMultimap</span>(result.build().headers(), <span style="color:#000080;font-weight:bold">null</span>);
  
    Map<String, List<String>> cookies = cookieHandler.get(request.uri(), headers);
  
    <span style="color:#808080;font-style:italic">// Add any new cookies to the request.</span><span style="color:#808080;font-style:italic">   </span> OkHeaders.<span style="font-style:italic">addCookies</span>(result, cookies);
  
  }
  
  <span style="color:#000080;font-weight:bold">if </span>(request.header(<span style="color:#008000;font-weight:bold">"User-Agent"</span>) == <span style="color:#000080;font-weight:bold">null</span>) {
  
    result.header(<span style="color:#008000;font-weight:bold">"User-Agent"</span>, Version.<span style="font-style:italic">userAgent</span>());
  
  }
  
  <span style="color:#000080;background-color:#e4e4ff;font-weight:bold">return </span><span style="background-color:#e4e4ff">result.build();</span>
  
}

参考资料:

<a rev="en_rl_small" href="https://www.learn2crack.com/2016/06/retrofit-okhttp-logging-interceptor.html">https://www.learn2crack.com/2016/06/retrofit-okhttp-logging-interceptor.html</a>

compile <span style="color:#008000;font-weight:bold">&#8216;com.squareup.okhttp:logging-interceptor:2.7.5&#8217;</span>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [OkHttp 2.x 的 Interceptor 无法读取Http请求时发出的header的问题及解决方案](http://www.beansoft.biz/2016/08/30/okhttp-2-x-%e7%9a%84-interceptor-%e6%97%a0%e6%b3%95%e8%af%bb%e5%8f%96http%e8%af%b7%e6%b1%82%e6%97%b6%e5%8f%91%e5%87%ba%e7%9a%84header%e7%9a%84%e9%97%ae%e9%a2%98%e5%8f%8a%e8%a7%a3%e5%86%b3%e6%96%b9/)