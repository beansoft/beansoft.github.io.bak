---
id: 1743
title: 'JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)'
date: 2011-02-15T18:24:39+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1743
permalink: '/2011/02/15/jsp-%e4%b8%ad-ajax-%e7%9a%84%e8%a1%a8%e5%8d%95%e6%8f%90%e4%ba%a4%e4%b8%ad%e6%96%87%e9%97%ae%e9%a2%98%e7%9a%84%e7%ae%80%e5%8d%95%e8%a7%a3%e5%86%b3%e6%96%b9%e6%a1%88-gbk-%e7%89%88%e6%9c%ac%e5%8e%9f/'
views:
  - "13902"
original_post_id:
  - "1743"
categories:
  - AJAX/JavaScript
tags:
  - AJAX/JavaScript
  - 乱码
---
本文原来发表在 [http://www.blogjava.net/beansoft/archive/2006/12/31/91144.html](http://www.blogjava.net/beansoft/archive/2006/12/31/91144.html "http://www.blogjava.net/beansoft/archive/2006/12/31/91144.html"), 因为整理Blog, 文章正式搬家到这里.

阅读本文的正确排版格式: [http://www.beansoft.biz/wp-content/uploads/2011/02/JSP\_AJAX\_ENC_GBK.swf](http://www.beansoft.biz/wp-content/uploads/2011/02/JSP_AJAX_ENC_GBK.swf)

<div class="posttitle">
  <a class="singleposttitle" href="">JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</a>
</div>

作者: <beansoft@126.com> 2007.01.03

下载本文源码: [ajaxform_gbk.zip](http://www.blogjava.net/Files/beansoft/ajaxform_gbk.zip) 6KB 

转载请注明原创作者, 尊重他人劳动成果. 

更新:   
**2007-01-03   
** 修复了 AJAXFormer 中第二个参数 resultDiv 处理不当的问题;   
增加了从服务器端返回脚本并加以执行的功能;   
增加了表单提交后网络出错的错误显示功能.   
这些新功能都已经放在示例页面中了.

测试通过: Resin 3.0.18, Tomcat 5.0.30, 5.5.20; 浏览器: IE 6/Firefox 2.0. 

上一篇文章 [JSP 中 AJAX 的表单提交中文问题的简单解决方案](/beansoft/archive/2006/12/25/89835.html) 主要是针对 UTF-8 版本的进行处理的, 鉴于中国大陆地区大部分还是用 GBK 编码写 JSP, 因此本文就针对 GBK 的实践结果进行介绍.

有朋友提到 [当AJAX遭遇GBK的尴尬](/errorfun/archive/2006/12/30/91000.html) 里说当 AJAX 使用 GBK 编码后, 表单提交将出现乱码. 如前文所述, 只要全部采用 UTF-8 编码, 是没有任何问题的. 那么都用 GBK 呢?

首先要讲的是我们的文章还是一样的原则: 尽可能少的改动原来的代码来解决中文乱码问题. 所以本文的示例没有用过滤器等方法.

那么使用 GBK 编码到底有没有乱码问题呢?

第一个关键点就是 AJAX 的表单提交代码必须正确的按照 HTTP 规范实现, 即要保持原来的 GET/POST 方式不变, 也要保持里面的内容和浏览器提交的内容一摸一样. 以下内容摘自我编写的内部培训教材:

&#8212;&#8212;&#8212;&#8212;&#8212;&#8211; 引用开始 &#8212;&#8212;&#8212;&#8212;&#8212;&#8211;

首先必须要介绍一下 HTTP 协议和 GET, POST 的工作方式.

当用户在Web浏览器地址栏中输入一个带有http://前缀的URL并按下Enter后,或者在Web页面中某个以http://开头的超链接上单击鼠标,HTTP事务处理的第一个阶段&#8211;建立连接阶段就开始了.HTTP的默认端口是80.   
随着连接的建立,HTTP就进入了客户向服务器发送请求的阶段.客户向服务器发送的请求是一个有特定格式的ASCII消息,其语法规则为:

<table>
  <tr>
    <td>
      6KB
    </td>
  </tr>
  
  <tr>
    <td width="100%">
      < Method > < URL > < HTTP Version > <n> <br />{ <Header>:<Value> <n>}* <br /><n> <br />{ Entity Body }
    </td>
  </tr>
</table>

请求消息的顶端是请求行,用于指定方法,URL和HTTP协议的版本,请求行的最后是回车换行.方法有GET,POST,HEAD,PUT,DELETE等.   
在请求行之后是若干个报头(Header)行.每个报头行都是由一个报头和一个取值构成的二元对,报头和取值之间以":"分隔;报头行的最后是回车换行. 常见的报头有Accept(指定MIME媒体类型),Accept\_Charset(响应消息的编码方式),Accept\_Encoding(响应消息的字符集),User_Agent(用户的浏览器信息)等.   
在请求消息的报头行之后是一个回车换行,表明请求消息的报头部分结束.在这个n之后是请求消息的消息实体(Entity Body).   
Web服务器在收到客户请求并作出处理之后,要向客户发送应答消息.与请求消息一样,应答消息的语法规则为:

<table style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
  <tr>
    <td width="100%">
      < HTTP Version> <Status Code> [<Message>]<n> <br />{ <Header>:<Value> <n> } * <br /><n> <br />{ Entity Body }
    </td>
  </tr>
</table>

应答消息的第一行为状态行,其中包括了HTTP版本号,状态码和对状态码进行简短解释的消息;状态行的最后是回车换行.状态码由3位数字组成,有5类: 

  * 1XX 保留 
  * 2XX 表示成功 
  * 3XX 表示URL已经被移走 
  * 4XX 表示客户错误 
  * 5XX 表示服务器错误 

例如:415,表示不支持改媒体类型;503,表示服务器不能访问.最常见的是200,表示成功.常见的报头有:Last\_Modified(最后修改时间),Content\_Type(消息内容的MIME类型),Content_Length(内容长度)等.   
在报头行之后也是一个回车换行,用以表示应答消息的报头部分的结束,以及应答消息实体的开始.   
下面是一个应答消息的例子:

<table style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
  <tr>
    <td width="100%">
      HTTP/1.0 200 OK <br />Date: Moday,07-Apr-97 21:13:02 GMT <br />Server:NCSA/1.1 <br />MIME_Version:1.0 <br />Content_Type:text/html <br />Last_Modified:Thu Dec 5 09:28:01 1996 <br />Coentent_Length:3107 </p> 
      
      <p>
        <HTML><HEAD><TITLE>&#8230;</HTML></td> </tr> </tbody> </table> 
        
        <p>
          那么 GET 和 POST 有什么区别? 区别就是一个在 URL 请求里面附带了表单参数和值, 一个是在 HTTP 请求的消息实体中. 用下面的例子可以很容易的看到同样的数据通过GET和POST来发送的区别, 发送的数据是 username=张三 :
        </p>
        
        <p>
          GET 方式, 浏览器键入 http://localhost?username=张三
        </p>
        
        <table style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
          <tr>
            <td width="100%">
              GET /?username=%E5%BC%A0%E4%B8%89 HTTP/1.1 <br />Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-powerpoint, application/vnd.ms-excel, application/msword, */* <br />Accept-Language: zh-cn <br />Accept-Encoding: gzip, deflate <br />User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.4322) <br />Host: localhost <br />Connection: Keep-Alive
            </td>
          </tr>
        </table>
        
        <p>
          POST 方式:
        </p>
        
        <table style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
          <tr>
            <td width="100%">
              POST / HTTP/1.1 <br />Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-powerpoint, application/vnd.ms-excel, application/msword, */* <br />Accept-Language: zh-cn <br />Content-Type: application/x-www-form-urlencoded <br />Accept-Encoding: gzip, deflate <br />User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0; .NET CLR 1.1.4322) <br />Host: localhost <br />Content-Length: 28 <br />Connection: Keep-Alive </p> 
              
              <p>
                username=%E5%BC%A0%E4%B8%89</td> </tr> </tbody> </table> 
                
                <p>
                  比较一下上面的两段文字, 您会发现 GET 方式把表单内容放在前面的请求头中, 而 POST 则把这些内容放在请求的主体中了, 同时 POST 中把请求的 Content-Type 头设置为 application/x-www-form-urlencoded. 而发送的正文都是一样的, 可以这样来构造一个表单提交正文:
                </p>
                
                <p>
                  <em>encodeURIComponent(arg1)=encodeURIComponent(value1)&encod<br /> eURIComponent(arg2)=encodeURIComponent(value2)&&#8230;..</em>
                </p>
                
                <p>
                  注: <strong>encodeURIComponent</strong> 返回一个包含了 <em>charstring</em> 内容的新的 <strong>String</strong> 对象（Unicode 格式）， 所有空格、标点、重音符号以及其他非 ASCII 字符都用 <strong>%</strong><em>xx</em> 编码代替，其中 <em>xx</em> 等于表示该字符的十六进制数。 例如，空格返回的是 "%20" 。 字符的值大于 255 的用 <strong>%u</strong><em>xxxx</em> 格式存储。参见 JavaScript 的 encodeURIComponent() 方法.
                </p>
                
                <p>
                  下面就讨论一下如何在 JavaScript 中执行一个 GET 或者 POST 请求. 如果您用过 Java, 那么您可能熟悉下列的用 java.net.URLConnection 类进行 POST 操作的代码(参考 <span style="font-size:.9em;font-family:verdana,arial,helvetica;"><a href="http://www.javaworld.com/javatips/jw-javatip34.html">Java Tip 34: POSTing via Java</a> ): <br /></span>
                </p>
                
                <table id="table1" style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
                  <tr>
                    <td>
                      <code>&lt;span style="font-size:.75em;color:rgb(0,0,0);font-family:courier new;">URL url;              &lt;br />URLConnection urlConn;               &lt;br />DataOutputStream printout;               &lt;br />&lt;span style="color:rgb(0,128,0);">// URL of CGI-Bin or jsp, asp script.                &lt;br />&lt;/span>url = &lt;strong>new&lt;/strong> URL (&lt;span style="color:rgb(0,0,128);">"somepage"&lt;/span>);               &lt;br />&lt;span style="color:rgb(0,128,0);">// URL connection channel.                &lt;br />&lt;/span>urlConn = url.openConnection();               &lt;br />&lt;span style="color:rgb(0,128,0);">// ......                &lt;br />// No caching, we want the real thing.                 &lt;br />&lt;/span>urlConn.setUseCaches (&lt;strong>false&lt;/strong>);               &lt;br />&lt;span style="color:rgb(0,128,0);">// Specify the content type.                &lt;br />&lt;/span>urlConn.setRequestProperty(&lt;span style="color:rgb(0,0,128);">"Content-Type"&lt;/span>, &lt;span style="color:rgb(0,0,128);">"application/x-www-form-urlencoded"&lt;/span>);               &lt;br />&lt;span style="color:rgb(0,128,0);">// Send POST output.                &lt;br />&lt;/span>printout = &lt;strong>new&lt;/strong> DataOutputStream (urlConn.getOutputStream ());               &lt;br />String content = &lt;span style="color:rgb(0,0,128);">"name="&lt;/span> + URLEncoder.encode (&lt;span style="color:rgb(0,0,128);">"Buford Early"&lt;/span>) + &lt;span style="color:rgb(0,0,128);">"&email="&lt;/span> + URLEncoder.encode (&lt;span style="color:rgb(0,0,128);">"buford@known-space.com"&lt;/span>);               &lt;br />printout.writeBytes (content);               &lt;br />printout.flush ();               &lt;br />printout.close ();&lt;/span></code>
                    </td>
                  </tr>
                </table>
                
                <p>
                  <code>以上的代码向 somepage 发送了一次 POST 请求, 数据为 name = Buford Early, email = buford@known-space.com.      &lt;br />用</code><span style="font-size:.9em;font-family:verdana,arial,helvetica;"><code>JavaScript 来执行 POST/GET 请求是同样的原理, 下面的代码展示了分别用 XMLHttpRequest 对象向 somepage 用 GET 和 POST 两种方式发送和上例相同的数据的具体过程:        &lt;br />GET 方式</code></span>
                </p>
                
                <table id="table2" style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
                  <tr>
                    <td>
                      <code>&lt;span style="font-size:.75em;color:rgb(0,0,0);font-family:courier new;">&lt;strong>var&lt;/strong> postContent =               &lt;br />&lt;span style="color:rgb(0,0,128);">"name="&lt;/span> + encodeURIComponent(&lt;span style="color:rgb(0,0,128);">"Buford Early"&lt;/span>) + &lt;span style="color:rgb(0,0,128);">"&email="&lt;/span> + encodeURIComponent(&lt;span style="color:rgb(0,0,128);">"buford@known-space.com"&lt;/span>);               &lt;br />xmlhttp.open(&lt;span style="color:rgb(0,0,128);">"GET"&lt;/span>, &lt;span style="color:rgb(0,0,128);">"somepage"&lt;/span> + &lt;span style="color:rgb(0,0,128);">"?"&lt;/span> + postContent, &lt;strong>true&lt;/strong>);               &lt;br />xmlhttp.send(&lt;strong>null&lt;/strong>);&lt;/span></code>
                    </td>
                  </tr>
                </table>
                
                <p>
                  <span style="font-size:.75em;">POST 方式</span>
                </p>
                
                <table id="table3" style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
                  <tr>
                    <td>
                      <code>&lt;span style="font-size:.75em;color:rgb(0,0,0);font-family:courier new;">&lt;strong>var&lt;/strong> postContent =               &lt;br />&lt;span style="color:rgb(0,0,128);">"name="&lt;/span> + encodeURIComponent(&lt;span style="color:rgb(0,0,128);">"Buford Early"&lt;/span>) + &lt;span style="color:rgb(0,0,128);">"&email="&lt;/span> + encodeURIComponent(&lt;span style="color:rgb(0,0,128);">"buford@known-space.com"&lt;/span>);               &lt;br />xmlhttp.open(&lt;span style="color:rgb(0,0,128);">"POST"&lt;/span>, &lt;span style="color:rgb(0,0,128);">"somepage"&lt;/span>, &lt;strong>true&lt;/strong>);               &lt;br />xmlhttp.setRequestHeader(&lt;span style="color:rgb(0,0,128);">"Content-Type"&lt;/span>, &lt;span style="color:rgb(0,0,128);">"application/x-www-form-urlencoded"&lt;/span>);               &lt;br />xmlhttp.send(postContent);&lt;/span></code>
                    </td>
                  </tr>
                </table>
                
                <p>
                  至此希望你已经能够理解如何用 JavaScript 中的 XMLHttpRequest 对象来执行 GET/POST 操作, 剩下的工作就是您如何来构造这些提交的参数了, 最后我给出一个将现有的 form 提交代码修改为异步的 AJAX 提交的代码(注意目前作者还不知道如何让 file 上传表单域也能异步上传文件). 首先请看两个 JavaScript 函数:
                </p>
                
                <table id="table4" style="border-collapse:collapse;" cellpadding="0" width="100%" bgcolor="#ebe9ed" border="1">
                  <tr>
                    <td>
                      <pre><code>&lt;span style="font-size:.75em;font-family:courier new;">&lt;span style="color:rgb(0,128,0);">// form - the form to submit&lt;br />// resultDivId - the division of which to display result text in, in null, then&lt;br />// create an element and add it to the end of the body&lt;br />&lt;/span>&lt;strong>function &lt;/strong>ajaxSubmitForm(form, resultDivId) {&lt;br />&lt;strong>var &lt;/strong>elements = form.elements;&lt;span style="color:rgb(0,128,0);">// Enumeration the form elements&lt;br />&lt;/span>&lt;strong>var &lt;/strong>element;&lt;br />&lt;strong>var &lt;/strong>i;&lt;br />&lt;br />&lt;strong>var &lt;/strong>postContent = &lt;span style="color:rgb(0,0,128);">""&lt;/span>;&lt;span style="color:rgb(0,128,0);">// Form contents need to submit&lt;br />&lt;br />&lt;/span>&lt;strong>for&lt;/strong>(i=&lt;span style="color:rgb(255,102,0);">0&lt;/span>;i&lt;elements.length;++i) {&lt;br />&lt;strong>var &lt;/strong>element=elements[i];&lt;br />&lt;br />&lt;strong>if&lt;/strong>(element.type==&lt;span style="color:rgb(0,0,128);">"text" &lt;/span>|| element.type==&lt;span style="color:rgb(0,0,128);">"textarea" &lt;/span>|| element.type==&lt;span style="color:rgb(0,0,128);">"hidden"&lt;/span>) {&lt;br />postContent += encodeURIComponent(element.name) + &lt;span style="color:rgb(0,0,128);">"=" &lt;/span>+ encodeURIComponent(element.value) + &lt;span style="color:rgb(0,0,128);">"&"&lt;/span>;&lt;br />}&lt;br />&lt;strong>else if&lt;/strong>(element.type==&lt;span style="color:rgb(0,0,128);">"select-one"&lt;/span>||element.type==&lt;span style="color:rgb(0,0,128);">"select-multiple"&lt;/span>) {&lt;br />&lt;strong>var &lt;/strong>options=element.options,j,item;&lt;br />&lt;strong>for&lt;/strong>(j=&lt;span style="color:rgb(255,102,0);">0&lt;/span>;j&lt;options.length;++j){&lt;br />item=options[j];&lt;br />&lt;strong>if&lt;/strong>(item.selected) {&lt;br />postContent += encodeURIComponent(element.name) + &lt;span style="color:rgb(0,0,128);">"=" &lt;/span>+ encodeURIComponent(item.value) + &lt;span style="color:rgb(0,0,128);">"&"&lt;/span>;&lt;br />}&lt;br />}&lt;br />} &lt;strong>else if&lt;/strong>(element.type==&lt;span style="color:rgb(0,0,128);">"checkbox"&lt;/span>||element.type==&lt;span style="color:rgb(0,0,128);">"r
adio"&lt;/span>) {&lt;br />&lt;strong>if&lt;/strong>(element.checked) {&lt;br />postContent += encodeURIComponent(element.name) + &lt;span style="color:rgb(0,0,128);">"=" &lt;/span>+ encodeURIComponent(element.value) + &lt;span style="color:rgb(0,0,128);">"&"&lt;/span>;&lt;br />}&lt;br />} &lt;strong>else if&lt;/strong>(element.type==&lt;span style="color:rgb(0,0,128);">"file"&lt;/span>) {&lt;br />&lt;strong>if&lt;/strong>(element.value != &lt;span style="color:rgb(0,0,128);">""&lt;/span>) {&lt;br />postContent += encodeURIComponent(element.name) + &lt;span style="color:rgb(0,0,128);">"=" &lt;/span>+ encodeURIComponent(element.value) + &lt;span style="color:rgb(0,0,128);">"&"&lt;/span>;&lt;br />}&lt;br />} &lt;strong>else &lt;/strong>{&lt;br />postContent += encodeURIComponent(element.name) + &lt;span style="color:rgb(0,0,128);">"=" &lt;/span>+ encodeURIComponent(element.value) + &lt;span style="color:rgb(0,0,128);">"&"&lt;/span>;&lt;br />}&lt;br />}&lt;br />&lt;br />alert(postContent);&lt;br />&lt;br />ajaxSubmit(form.action, form.method, postContent);&lt;br />}&lt;br />&lt;br />&lt;span style="color:rgb(0,128,0);">// url - the url to do submit&lt;br />// method - "get" or "post"&lt;br />// postContent - the string with values to be submited&lt;br />// resultDivId - the division of which to display result text in, in null, then&lt;br />// create an element and add it to the end of the body&lt;br />&lt;/span>&lt;strong>function &lt;/strong>ajaxSubmit(url, method, postContent, resultDivId)&lt;br />{&lt;br />&lt;strong>var &lt;/strong>loadingDiv = document.getElementById(&lt;span style="color:rgb(0,0,128);">'loading'&lt;/span>);&lt;br />&lt;span style="color:rgb(0,128,0);">// call in new thread to allow ui to update&lt;br />&lt;/span>window.setTimeout(&lt;strong>function &lt;/strong>() {&lt;br />loadingDiv.innerText = &lt;span style="color:rgb(0,0,128);">"Loading...."&lt;/span>;&lt;br />loadingDiv.style.display = &lt;span style="color:rgb(0,0,128);">""&lt;/span>;&lt;br />}, &lt;span style="color:rgb(255,102,0);">1&lt;/span>);&lt;br />&lt;br />&lt;span style="color:rgb(0,128,0);">// code for Mozilla, etc.&lt;br />&lt;/span>&lt;strong>if &lt;/strong>(window.XMLHttpRequest)&lt;br />{&lt;br />xmlhttp=&lt;strong>new &lt;/strong>XMLHttpRequest();&lt;br />}&lt;br />&lt;span style="color:rgb(0,128,0);">// code for IE&lt;br />&lt;/span>&lt;strong>else if &lt;/strong>(window.ActiveXObject)&lt;br />{&lt;br />xmlhttp=&lt;strong>new &lt;/strong>ActiveXObject(&lt;span style="color:rgb(0,0,128);">"Microsoft.XMLHTTP"&lt;/span>);&lt;br />}&lt;br />&lt;br />&lt;strong>if&lt;/strong>(xmlhttp) {&lt;br />xmlhttp.onreadystatechange = &lt;strong>function&lt;/strong>() {&lt;br />&lt;span style="color:rgb(0,128,0);">// if xmlhttp shows "loaded"&lt;br />&lt;/span>&lt;strong>if &lt;/strong>(xmlhttp.readyState==&lt;span style="color:rgb(255,102,0);">4&lt;/span>)&lt;br />{&lt;br />&lt;strong>if&lt;/strong>(resultDivId) {&lt;br />document.getElementByID(resultDivId).innerHTML = xmlhttp.responseText;&lt;br />} &lt;strong>else &lt;/strong>{&lt;br />&lt;strong>var &lt;/strong>result = document.createElement(&lt;span style="color:rgb(0,0,128);">"DIV"&lt;/span>);&lt;br />result.style.border=&lt;span style="color:rgb(0,0,128);">"1px solid #363636"&lt;/span>;&lt;br />result.innerHTML = xmlhttp.responseText;&lt;br />document.body.appendChild(result);&lt;br />}&lt;br />&lt;br />loadingDiv.innerHTML =&lt;br />&lt;span style="color:rgb(0,0,128);">"Submit finnished!"&lt;/span>;&lt;br />}&lt;br />&lt;br />};&lt;br />&lt;br />&lt;strong>if&lt;/strong>(method.toLowerCase() == &lt;span style="color:rgb(0,0,128);">"get"&lt;/span>) {&lt;br />xmlhttp.open(&lt;span style="color:rgb(0,0,128);">"GET"&lt;/span>, url + &lt;span style="color:rgb(0,0,128);">"?" &lt;/span>+ postContent, &lt;strong>true&lt;/strong>);&lt;br />xmlhttp.send(&lt;strong>null&lt;/strong>);&lt;br />} &lt;strong>else if&lt;/strong>(method.toLowerCase() == &lt;span style="color:rgb(0,0,128);">"post"&lt;/span>) {&lt;br />xmlhttp.open(&lt;span style="color:rgb(0,0,128);">"POST"&lt;/span>, url, &lt;strong>true&lt;/strong>);&lt;br />xmlhttp.setRequestHeader(&lt;span style="color:rgb(0,0,128);">"Content-Type"&lt;/span>, &lt;span style="color:rgb(0,0,128);">"application/x-www-form-urlencoded"&lt;/span>);&lt;br />xmlhttp.send(postContent);&lt;br />}&lt;br />} &lt;strong>else &lt;/strong>{&lt;br />loadingDiv.innerHTML =&lt;br />&lt;span style="color:rgb(0,0,128);">"Can't create XMLHttpRequest object, please check your web browser."&lt;/span>;&lt;br />}&lt;br />&lt;br />}&lt;/span></code></pre>
                    </td>
                  </tr>
                </table>
                
                <p>
                  函数 <code>&lt;span style="font-size:.75em;font-family:courier new;">ajaxSubmitForm 将表单要提交的内容进行封装, 然后调用 ajaxSubmit 函数来执行真正的异步提交, 表单提交后所返回的结果则显示在给定的 DIV 容器中或者没有指定参数时用 DOM 对象动态生成一个 DIV 容器来显示结果并添加到页面末尾. 这样, 对原来的表单只需要改动一个地方就可以将原来的表单提交改为异步模式, 即在 form 标签里加入: &lt;span style="background-color:rgb(235,233,237);">onSubmit="ajaxSubmitForm(this);return false;"&lt;/span> 即可, return false 确保表单不会被浏览器同步提交.&lt;/span></code>
                </p>
                
                <p>
                </p>
                
                <p>
                  &#8212;&#8212;&#8212;&#8212;&#8212;&#8211; 引用结束 &#8212;&#8212;&#8212;&#8212;&#8212;&#8211;
                </p>
                
                <p>
                  OK, 希望至此为止您已经理解了如何用 AJAX 来正确的执行 GET/POST. 如果这个问题您解决了, 可是说后台的乱码问题就和你直接通过表单提交几乎没有区别了. 这个方法的具体封装已经在附件的 ajax_common.js 中了.
                </p>
                
                <p>
                  至此也该贴出来我们的 GBK 编码的客户端页面的内容了:
                </p>
                
                <p>
                </p>
                
                <div style="border-right:rgb(204,204,204) 1px solid;border-top:rgb(204,204,204) 1px solid;font-size:13px;border-left:rgb(204,204,204) 1px solid;width:98%;border-bottom:rgb(204,204,204) 1px solid;background-color:rgb(238,238,238);padding:4px 5px 4px 4px;">
                  <p>
                    <html>
                  </p>
                  
                  <p>
                    <head><br /> <br /><meta http-equiv="Content-Type" content="text/html; charset=gbk">
                  </p>
                  
                  <p>
                    <title>AJAX Form Submit Test</title>
                  </p>
                  
                  <p>
                    <script src=&#8217;ajax_common.js&#8217;></script>
                  </p>
                  
                  <p>
                    </head>
                  </p>
                  
                  <p>
                    <body><br /> <br />本页面的编码是中文.<br/>
                  </p>
                  
                  <p>
                    <meta http-equiv="Content-Type" content="text/html; charset=gbk"><br/>
                  </p>
                  
                  <p>
                    <b>测试过的服务器:</b><br/>
                  </p>
                  
                  <p>
                    Resin 3.0.18<br/>
                  </p>
                  
                  <p>
                    Tomcat 5.5.20<br/>
                  </p>
                  
                  <p>
                    Tomcat 5.0.30<br/>
                  </p>
                  
                  <p>
                    <h3>AJAX Form Submit Test</h3>
                  </p>
                  
                  <p>
                    Fill the form and then click submit<br>
                  </p>
                  
                  <p>
                    提交方式: POST<br>
                  </p>
                  
                  <p>
                    <form method="POST" id="form1" name="form1"
                  </p>
                  
                  <p>
                    action="form_action.jsp"
                  </p>
                  
                  <p>
                    onSubmit="former.ajaxSubmitForm();return false;">
                  </p>
                  
                  <p>
                    <p><input type="hidden" name="hidden1" value="hiddenValue">
                  </p>
                  
                  <p>
                    text:<input type="text" name="textf&1" size="20" value="text文本&1">
                  </p>
                  
                  <p>
                    checkbox:<input type="checkbox" name="checkbox1" value="ON" checked>
                  </p>
                  
                  <p>
                    radio:<input type="radio" value="V1" checked name="radio1">
                  </p>
                  
                  <p>
                    select:<select size="1" name="select1">
                  </p>
                  
                  <p>
                    <option selected value="option1">D1</option>
                  </p>
                  
                  <p>
                    </select>
                  </p>
                  
                  <p>
                    <br>
                  </p>
                  
                  <p>
                    <br>
                  </p>
                  
                  <p>
                    <input type="submit" name="B1" value="submit">
                  </p>
                  
                  <p>
                    <input type="reset" name="B2" value="reset">
                  </p>
                  
                  <p>
                    </p>
                  </p>
                  
                  <p>
                    </form>
                  </p>
                  
                  <p>
                    提交方式: GET<br><br /> <br /><form method="GET" id="form2" name="form2"
                  </p>
                  
                  <p>
                    action="form_action.jsp"
                  </p>
                  
                  <p>
                    onSubmit="former2.ajaxSubmitForm();return false;">
                  </p>
                  
                  <p>
                    <p><input type="hidden" name="hidden1" value="hiddenValue">
                  </p>
                  
                  <p>
                    text:<input type="text" name="text文本&2" size="20" value="text文本&2">
                  </p>
                  
                  <p>
                    checkbox:<input type="checkbox" name="checkbox1" value="ON" checked>
                  </p>
                  
                  <p>
                    radio:<input type="radio" value="V1" checked name="radio1">
                  </p>
                  
                  <p>
                    select:<select size="1" name="select1">
                  </p>
                  
                  <p>
                    <option selected value="option1">D1</option>
                  </p>
                  
                  <p>
                    </select>
                  </p>
                  
                  <p>
                    <br>
                  </p>
                  
                  <p>
                    <br>
                  </p>
                  
                  <p>
                    <input type="submit" name="B1" value="submit">
                  </p>
                  
                  <p>
                    <input type="reset" name="B2" value="reset">
                  </p>
                  
                  <p>
                    </p>
                  </p>
                  
                  <p>
                    </form>
                  </p>
                  
                  <p>
                    <div id="loading" style="display:none; position:absolute;<br /> <br />border:1px solid orange; height:20px; width:600; left: 93px; top: 112px;
                  </p>
                  
                  <p>
                    background-color: #FFFFCC; cursor:pointer;" title="Click to hide" onClick="this.style.display=&#8217;none&#8217;;"></div>
                  </p>
                  
                  <p>
                    <div id="resultDiv" style="border:1px solid orange; background-color: #FFFFCC; cursor:pointer;" title="Click to hide" onClick="this.style.display=&#8217;none&#8217;;"><br /> <br />Form 1 的提交结果将会显示在这里.
                  </p>
                  
                  <p>
                    </div>
                  </p>
                  
                  <p>
                    <br /><script type="text/javascript">
                  </p>
                  
                  <p>
                    var former = new AjaxFormer($(&#8216;form1&#8217;), &#8216;resultDiv&#8217;);
                  </p>
                  
                  <p>
                    var former2 = new AjaxFormer($(&#8216;form2&#8217;));
                  </p>
                  
                  <p>
                    </script>
                  </p>
                  
                  <p>
                    </body>
                  </p>
                  
                  <p>
                    </html>
                  </p>
                </div>
                
                <p>
                  可以看到我们的确使用的是 GBK 编码, 浏览器打开的时候自动选择的编码也是简体中文.
                </p>
                
                <p>
                </p>
                
                <p>
                  那么第二个关键点就是服务器端的表单数据读取了.这个问题跟具体的服务器有很大关系. 对于 Resin 服务器来说, 问题很少, 基本上不论是 POST 和 GET, 出乱码的概率都比较小. 但是 Tomcat 就不敢恭维了, 这大概也是开源产品和商业产品的区别, 缺乏前后一致性和兼容性, 因为开源的不需要提供技术支持. Tomcat 的 GET/POST 的编码处理方式不同的版本都不一样, 就像 Eclipse/Netbeans 新版本从来不需要兼容老版本的插件 API 一样, Hibernate/Struts/Spring 也是一样, 所以学 Java 的很累. 当然, 这就是免费/开源的代价. 跑题了. 因此我们的服务器端代码大部分都是对 Tomcat 的乱码问题的解决(POST的没有问题, 主要是 GET 方法的).<br />
                </p>
                
                <div style="border-right:rgb(204,204,204) 1px solid;border-top:rgb(204,204,204) 1px solid;font-size:13px;border-left:rgb(204,204,204) 1px solid;width:98%;border-bottom:rgb(204,204,204) 1px solid;background-color:rgb(238,238,238);padding:4px 5px 4px 4px;">
                  <p>
                    <span style="color:rgb(0,0,255);"><%@ page contentType="text/html; charset=gbk" pageEncoding="gbk"%><br /> <br /><html></p> 
                    
                    <p>
                      <%
                    </p>
                    
                    <p>
                      //Send some headers to keep the user&#8217;s browser from caching the response.
                    </p>
                    
                    <p>
                      response.addHeader("Expires", "Mon, 26 Jul 1997 05:00:00 GMT" );
                    </p>
                    
                    <p>
                      response.addHeader("Last-Modified", new java.util.Date().toGMTString());
                    </p>
                    
                    <p>
                      response.addHeader("Cache-Control", "no-cache, must-revalidate" );
                    </p>
                    
                    <p>
                      response.addHeader("Pragma", "no-cache" );
                    </p>
                    
                    <p>
                      // This will emulate a network delay, for 2 sec.
                    </p>
                    
                    <p>
                      //Thread.currentThread().sleep(2000);</span>
                    </p>
                    
                    <p>
                      <span style="color:rgb(0,0,255);">request.setCharacterEncoding("utf-8");<br /> <br />%></span>
                    </p>
                    
                    <p>
                      <span style="color:rgb(0,0,255);"><%!</span>
                    </p>
                    
                    <p>
                      <span style="color:rgb(0,0,255);">/**<br /> <br />* 转换字符串的内码.</p> 
                      
                      <p>
                        *
                      </p>
                      
                      <p>
                        * @param input
                      </p>
                      
                      <p>
                        * 输入的字符串
                      </p>
                      
                      <p>
                        * @param sourceEncoding
                      </p>
                      
                      <p>
                        * 源字符集名称
                      </p>
                      
                      <p>
                        * @param targetEncoding
                      </p>
                      
                      <p>
                        * 目标字符集名称
                      </p>
                      
                      <p>
                        * @return 转换结果, 如果有错误发生, 则返回原来的值
                      </p>
                      
                      <p>
                        */
                      </p>
                      
                      <p>
                        public static String changeEncoding(String input, String sourceEncoding,
                      </p>
                      
                      <p>
                        String targetEncoding) {
                      </p>
                      
                      <p>
                        if (input == null || input.equals("")) {
                      </p>
                      
                      <p>
                        return input;
                      </p>
                      
                      <p>
                        }</span>
                      </p>
                      
                      <p>
                        <span style="color:rgb(0,0,255);">try {<br /> <br />byte[] bytes = input.getBytes(sourceEncoding);</p> 
                        
                        <p>
                          return new String(bytes, targetEncoding);
                        </p>
                        
                        <p>
                          } catch (Exception ex) {
                        </p>
                        
                        <p>
                          }
                        </p>
                        
                        <p>
                          return input;
                        </p>
                        
                        <p>
                          }</span>
                        </p>
                        
                        <p>
                          <span style="color:rgb(0,0,255);">/**<br /> <br />* 一个类似于 JavaScript 的 escape 函数的功能, 确保乱码可以正确传输.</p> 
                          
                          <p>
                            */
                          </p>
                          
                          <p>
                            public static String escape(String src) {
                          </p>
                          
                          <p>
                            int i;
                          </p>
                          
                          <p>
                            char j;
                          </p>
                          
                          <p>
                            StringBuffer tmp = new StringBuffer();
                          </p>
                          
                          <p>
                            tmp.ensureCapacity(src.length() * 6);
                          </p>
                          
                          <p>
                            for (i = 0; i < src.length(); i++) {
                          </p>
                          
                          <p>
                            j = src.charAt(i);
                          </p>
                          
                          <p>
                            if (Character.isDigit(j) || Character.isLowerCase(j)
                          </p>
                          
                          <p>
                            || Character.isUpperCase(j))
                          </p>
                          
                          <p>
                            tmp.append(j);
                          </p>
                          
                          <p>
                            else if (j < 256) {
                          </p>
                          
                          <p>
                            tmp.append("%");
                          </p>
                          
                          <p>
                            if (j < 16)
                          </p>
                          
                          <p>
                            tmp.append("0");
                          </p>
                          
                          <p>
                            tmp.append(Integer.toString(j, 16));
                          </p>
                          
                          <p>
                            } else {
                          </p>
                          
                          <p>
                            tmp.append("%u");
                          </p>
                          
                          <p>
                            tmp.append(Integer.toString(j, 16));
                          </p>
                          
                          <p>
                            }
                          </p>
                          
                          <p>
                            }
                          </p>
                          
                          <p>
                            return tmp.toString();
                          </p>
                          
                          <p>
                            }
                          </p>
                          
                          <p>
                            %></span>
                          </p>
                          
                          <p>
                            <span style="color:rgb(0,0,255);"><head><br /> <br /><title>Test form action page</title></p> 
                            
                            <p>
                              </head>
                            </p>
                            
                            <p>
                              <body>
                            </p>
                            
                            <p>
                              这是 GBK 编码版本的后台表单提交页面.<br/></span>
                            </p>
                            
                            <p>
                              <span style="color:rgb(0,0,255);"><%<br /> <br />boolean isTomcat = application.getServerInfo().toLowerCase().indexOf("tomcat") != -1;</p> 
                              
                              <p>
                                %></span>
                              </p>
                              
                              <p>
                                <span style="color:rgb(0,0,255);">Form submit method:<%=request.getMethod()%><br/><br /> <br />The form content u send is:<br/></p> 
                                
                                <p>
                                  <%
                                </p>
                                
                                <p>
                                  java.util.Enumeration e = request.getParameterNames();</span>
                                </p>
                                
                                <p>
                                  <span style="color:rgb(0,0,255);">while (e.hasMoreElements()) {<br /> <br />String name = (String)e.nextElement();</p> 
                                  
                                  <p>
                                    String value = request.getParameter(name);</span>
                                  </p>
                                  
                                  <p>
                                    <span style="color:rgb(0,0,255);">if(isTomcat && request.getMethod().equalsIgnoreCase("GET")) {<br /> <br />name = changeEncoding(name, "ISO8859-1", "UTF-8");</p> 
                                    
                                    <p>
                                      value = changeEncoding(value, "ISO8859-1", "UTF-8");
                                    </p>
                                    
                                    <p>
                                      }
                                    </p>
                                    
                                    <p>
                                      out.println("<b>" + name + "</b> = " + value + "<br/>");
                                    </p>
                                    
                                    <p>
                                      }</span>
                                    </p>
                                    
                                    <p>
                                      <span style="color:rgb(0,0,255);">// 给前台返回一个可以执行的脚本<br /> <br />//response.addHeader("response_script", changeEncoding("alert(&#8216;提交完成&#8217;);", "ISO8859-1", "UTF-8"));</p> 
                                      
                                      <p>
                                        response.addHeader("response_script", escape("alert(&#8216;提交完成&#8217;);"));
                                      </p>
                                      
                                      <p>
                                        %></span>
                                      </p>
                                      
                                      <p>
                                        <span style="color:rgb(0,0,255);"></body><br /> <br /></html></span>
                                      </p></div> 
                                      
                                      <p>
                                        <span style="color:rgb(0,0,255);background-color:rgb(245,245,245);">boolean</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">isTomcat</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">=</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">application.getServerInfo().toLowerCase().indexOf(</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">"</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">tomcat</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">"</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">) !</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">=</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">&#8211;</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">1</span><span style="color:rgb(0,0,0);background-color:rgb(245,245,245);">; 这一句主要针对 Tomcat 进行处理, 如果是 GET 方法的话, 就需要将表单参数从 ISO8859-1 转换到 UTF-8 (注意不是 GBK, 貌似 Tomcat 很喜欢 UTF-8?). 其它的地方和原来的 UTF-8 版本的没有区别. 当然如果您的站点应该用过滤器来更方便的解决这个问题.</span>
                                      </p>
                                      
                                      <p>
                                      </p>
                                      
                                      <p>
                                        小结:
                                      </p>
                                      
                                      <p>
                                        1. 使用一致的字符集很重要, 要么全是 GBK, 要么全是 UTF-8, 如果有条件, 就全部用 UTF-8, 那样工作量是最小的;
                                      </p>
                                      
                                      <p>
                                        2. 用 AJAX 提交的时候一定要按照 HTTP 的规范来, 做到和浏览器尽量兼容, 尤其是 POST 的时候不要再往 URL 地址里加参数了, 你那样是违规! 后果就是有的服务器会不搭理你传递的这些参数! 还是如我所讲, 参数提交之前要用 encodeURIComponent() 来转化, 这也是为了符合浏览器的习惯做法.
                                      </p>
                                      
                                      <p>
                                        3. 后台如果读取参数有乱码, 就尽量多在 ISO8859-1, GBK, UTF-8 中间多转换几次试试, 可以试试偶写的那个 changeEncoding() 方法, 把几个转换后的表单值都列出来, 一定有一个是正确的, 总是可以解决问题的. 这个本来不应该是偶们的任务, 但是写服务器的人是老美, 尤其是 Tomcat 作者, 只熟悉 ISO8859-1.
                                      </p>
                                      
                                      <p>
                                        4. 鉴于 TOMCAT 读取 POST 参数的时候很少出问题, 因此建议AJAX提交表单的时候多用 POST 方法, 尽量不用 GET.
                                      </p>
                                      
                                      <p>
                                        运行截屏:
                                      </p>
                                      
                                      <p>
                                        <img alt="http://www.blogjava.net/images/blogjava_net/beansoft/18680/o_AJAX%20Form%20Submit%20GBK.png" src="/images/blogjava_net/beansoft/18680/o_AJAX%20Form%20Submit%20GBK.png" />
                                      </p>
                                      
                                      <p>
                                        其它的一些资料可以参考Blogjava上的一篇原创文章: <a href="/errorfun/archive/2006/12/09/86584.html">[原创]struts,ajax乱码解决方案</a>
                                      </p>
                                      
                                      <p>
                                      </p>
                                      
                                      <p>
                                        欢迎发表建议和更好的观点. 谢谢! 重申本文无意代替您的 AJAX 框架, 不过在你抓狂的时候可以考虑看看他们表单提交的代码, 改改它!
                                      </p>
                                      
                                      <p>
                                        本人翻译的 XMLHttpRequest 对象介绍:
                                      </p>
                                      
                                      <h2>
                                        The XMLHttpRequest Object Reference XMLHttpRequest 对象参考
                                      </h2>
                                      
                                      <h3>
                                        Methods 方法
                                      </h3>
                                      
                                      <table style="border-collapse:collapse;" cellpadding="0" width="100%" border="1">
                                        <tr valign="top">
                                          <th align="left" width="45%">
                                            Method 方法
                                          </th>
                                          
                                          <th align="left" width="55%">
                                            Description 描述
                                          </th>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            abort()
                                          </td>
                                          
                                          <td>
                                            Cancels the current request<br /> <br />取消当前请求
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            getAllResponseHeaders()
                                          </td>
                                          
                                          <td>
                                            Returns the complete set of http headers as a string<br /> <br />将完整的 HTTP 头部做为一个字符串返回
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            getResponseHeader("headername")
                                          </td>
                                          
                                          <td>
                                            Returns the value of the specified http header<br /> <br />返回给定的 HTTP 头的值
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            open("method","URL",async,"uname","pswd")
                                          </td>
                                          
                                          <td>
                                            Specifies the method, URL, and other optional attributes of a request</p> 
                                            
                                            <p>
                                              The method parameter can have a value of "GET", "POST", or "PUT" (use "GET" when requesting data and use "POST" when sending data (especially if the length of the data is greater than 512 bytes.
                                            </p>
                                            
                                            <p>
                                              The URL parameter may be either a relative or complete URL.
                                            </p>
                                            
                                            <p>
                                              The async parameter specifies whether the request should be handled asynchronously or not. true means that script processing carries on after the send() method, without waiting for a response. false means that the script waits for a response before continuing script processing<br /> <br />指定表单提交方法, URL, 以及请求的可选属性
                                            </p>
                                            
                                            <p>
                                              method 参数可以是"GET", "POST" 或者 "PUT" 这些值中之一(使用"GET"来请求数据, 特别的, 当发送的数据长度大于512字节时使用 "POST").
                                            </p>
                                            
                                            <p>
                                              URL 参数可以为相对的和完整的 URL.
                                            </p>
                                            
                                            <p>
                                              async 参数指定请求是否为异步方式处理. true 意味着调用 send() 方法后脚本继续向下执行, 不需要等待响应. false 意味着脚本将等待响应之后才能继续执行
                                            </p>
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            send(content)
                                          </td>
                                          
                                          <td>
                                            Sends the request<br /> <br />发送请求
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            setRequestHeader("label","value")
                                          </td>
                                          
                                          <td>
                                            Adds a label/value pair to the http header to be sent<br /> <br />在要发送的 HTTP 头中添加 标签/取值
                                          </td>
                                        </tr>
                                      </table>
                                      
                                      <h3>
                                        Properties 属性
                                      </h3>
                                      
                                      <table style="border-collapse:collapse;" cellpadding="0" width="100%" border="1">
                                        <tr valign="top">
                                          <th align="left" width="30%">
                                            Property 属性
                                          </th>
                                          
                                          <th align="left" width="70%">
                                            Description 描述
                                          </th>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            onreadystatechange
                                          </td>
                                          
                                          <td>
                                            An event handler for an event that fires at every state change<br /> <br />每次状态改变时除非的事件处理器
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            readyState
                                          </td>
                                          
                                          <td>
                                            Returns the state of the object:</p> 
                                            
                                            <p>
                                              0 = uninitialized<br /> <br />1 = loading
                                            </p>
                                            
                                            <p>
                                              2 = loaded
                                            </p>
                                            
                                            <p>
                                              3 = interactive
                                            </p>
                                            
                                            <p>
                                              4 = complete
                                            </p>
                                            
                                            <p>
                                              返回对象的状态
                                            </p>
                                            
                                            <p>
                                              0 = 未初始化
                                            </p>
                                            
                                            <p>
                                              1 = 载入中
                                            </p>
                                            
                                            <p>
                                              2 = 已载入
                                            </p>
                                            
                                            <p>
                                              3 = 交互
                                            </p>
                                            
                                            <p>
                                              4 = 完成
                                            </p>
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            responseText
                                          </td>
                                          
                                          <td>
                                            Returns the response as a string<br /> <br />将响应做为字符串返回
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            responseXML
                                          </td>
                                          
                                          <td>
                                            Returns the response as XML. This property returns an XML document object, which can be examined and parsed using W3C DOM node tree methods and properties<br /> <br />将响应做为XML返回. 这个属性返回一个 XML 文档对象, 可以用 W3C 的 DOM 节点树方法和属性进行检索分析
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            status
                                          </td>
                                          
                                          <td>
                                            Returns the status as a number (e.g. 404 for "Not Found" or 200 for "OK")<br /> <br />将状态做为数字返回(例如 404 为"Not Found" 或者 200 为 "OK")
                                          </td>
                                        </tr>
                                        
                                        <tr valign="top">
                                          <td>
                                            statusText
                                          </td>
                                          
                                          <td>
                                            Returns the status as a string (e.g. "Not Found" or "OK")<br /> <br />将状态做为字符串返回(例如 "Not Found" 或者 "OK")
                                          </td>
                                        </tr>
                                      </table>
                                      
                                      <p>
                                      </p>
                                      
                                      <p>
                                        posted on 2006-12-31 14:37:00 <b>BeanSoft</b> 评论总数 (6)
                                      </p>
                                      
                                      <hr size="1" />
                                      
                                      <b>评论</b></p> 
                                      
                                      <p>
                                        <b>re: JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</b>
                                      </p>
                                      
                                      <p>
                                        <b><a href="http://www.beansoft.biz/">BeanSoft</a></b>
                                      </p>
                                      
                                      <p>
                                        posted @ 2007-02-12 14:04:00
                                      </p>
                                      
                                      <p>
                                        脚本组件太漂亮了 是指 YUI Ext, 详情请 google.
                                      </p>
                                      
                                      <p>
                                        <b>re: JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</b>
                                      </p>
                                      
                                      <p>
                                        <b><a href="null">按时的</a></b>
                                      </p>
                                      
                                      <p>
                                        posted @ 2007-01-28 22:25:00
                                      </p>
                                      
                                      <p>
                                        小告诉所得税地方
                                      </p>
                                      
                                      <p>
                                        <b>re: JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</b>
                                      </p>
                                      
                                      <p>
                                        <b><a href="http://www.blogjava.net/errorfun/">errorfun</a></b>
                                      </p>
                                      
                                      <p>
                                        posted @ 2006-12-31 17:26:00
                                      </p>
                                      
                                      <p>
                                        试了一下你的方法，果然可行。
                                      </p>
                                      
                                      <p>
                                        试验后不得不汗一个，在GBK编码下，无论如何都不能用SEND方法发送参数，而要把参数加到URL中然后OPEN，不管是GET或POST都这样，真晕了。
                                      </p>
                                      
                                      <p>
                                        使用encodeURIComponent 后的参数必须为UTF-8，如果不用的话就是XMLHTTP设置在CONTENT-TYPE中的CHARSET的编码，获取后可以用
                                      </p>
                                      
                                      <p>
                                        new String( value.getBytes("iso-8859-1"), "utf-8")
                                      </p>
                                      
                                      <p>
                                        和
                                      </p>
                                      
                                      <p>
                                        new String( value.getBytes("iso-8859-1"), your_contenttype_charset)
                                      </p>
                                      
                                      <p>
                                        问题总算解决，感觉XMLHTTP贼恶心的。
                                      </p>
                                      
                                      <p>
                                        <b>re: JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</b>
                                      </p>
                                      
                                      <p>
                                        <b><a href="http://www.blogjava.net/beansoft/">BeanSoft</a></b>
                                      </p>
                                      
                                      <p>
                                        posted @ 2006-12-31 16:18:00
                                      </p>
                                      
                                      <p>
                                        这也谈不上误会, 如果 N 个支持 JSP 规范的服务器都这样搞, 那开发人员岂不是累死了. 像 Resin, Weblogic 等这些商业软件就做的比较好, 根据来源编码自动切换后台的编码方式.
                                      </p>
                                      
                                      <p>
                                        <b>re: JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</b>
                                      </p>
                                      
                                      <p>
                                        <b><a href="http://www.blogjava.net/errorfun/">errorfun</a></b>
                                      </p>
                                      
                                      <p>
                                        posted @ 2006-12-31 16:12:00
                                      </p>
                                      
                                      <p>
                                        汗。。。。看来自己对AJAX的GET和POST还没有看透。
                                      </p>
                                      
                                      <p>
                                        不过，大家好像对TOMCAT的误会挺大的，TOMCAT的作者不是只熟悉ISO-8859-1编码的，它默认是ISO，但是可以通过更改配置文件的方式设置它的默认编码，具体方法为：进入%Tomcat_home%confserver.xml，找到Define a non-SSL Coyote HTTP/1.1 Connector on the port specified这个注释，它下面的一个Connector配置节，在上面的属性添加一个URIEncoding="GBK"，就可以了，具体内容如下：
                                      </p>
                                      
                                      <p>
                                        <Connector port="8080" maxThreads="150" minSpareThreads="25" maxSpareThreads="75" enableLookups="false" redirectPort="8443" acceptCount="100" debug="0" connectionTimeout="20000" disableUploadTimeout="true" URIEncoding="GBK" />
                                      </p>
                                      
                                      <p>
                                        <b>re: JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</b>
                                      </p>
                                      
                                      <p>
                                        <b><a href="null">Jeff Liu</a></b>
                                      </p>
                                      
                                      <p>
                                        posted @ 2007-01-03 15:07:00
                                      </p>
                                      
                                      <p>
                                        BeanSoft，你给我的脚本组件太漂亮了，非常感谢：）
                                      </p>
                                      
                                      <p>
                                        转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/02/15/jsp-%e4%b8%ad-ajax-%e7%9a%84%e8%a1%a8%e5%8d%95%e6%8f%90%e4%ba%a4%e4%b8%ad%e6%96%87%e9%97%ae%e9%a2%98%e7%9a%84%e7%ae%80%e5%8d%95%e8%a7%a3%e5%86%b3%e6%96%b9%e6%a1%88-gbk-%e7%89%88%e6%9c%ac%e5%8e%9f/">JSP 中 AJAX 的表单提交中文问题的简单解决方案 &#8211; GBK 版本(原创)</a>
                                      </p>