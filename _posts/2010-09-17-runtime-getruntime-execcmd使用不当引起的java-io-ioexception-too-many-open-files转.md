---
id: 1201
title: 'Runtime.getRuntime().exec(cmd)使用不当引起的java.io.IOException: Too many open files[转]'
date: 2010-09-17T18:45:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1201
permalink: '/2010/09/17/runtime-getruntime-execcmd%e4%bd%bf%e7%94%a8%e4%b8%8d%e5%bd%93%e5%bc%95%e8%b5%b7%e7%9a%84java-io-ioexception-too-many-open-files%e8%bd%ac/'
views:
  - "5517"
original_post_id:
  - "1201"
image: /wp-content/uploads/2012/09/None1.gif
categories:
  - Linux/Unix
---
本文出处: <http://www.blogjava.net/jnbzwm/archive/2010/09/14/332009.html>

<span class="Apple-style-span" style="word-spacing:0;font:medium 微软雅黑;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:14px;line-height:21px;font-family:arial;"> </p> 

<h2 style="font-size:14px;margin:0 0 4px;">
  <a id="viewpost1_TitleUrl" style="color:rgb(34,51,85);text-decoration:none;" href="http://www.blogjava.net/jnbzwm/archive/2010/09/14/332009.html">Runtime.getRuntime().exec(cmd)使用不当引起的java.io.IOException: Too many open files</a>
</h2>

<div class="postbody">
  <p style="margin:0 0 14px;">
    今天生产环境的一个Java应用程序的日志里，出现了很不和谐的记录： <br />java.io.IOException: Too many open files
  </p>
  
  <p style="margin:0 0 14px;">
    在网上查了一些关于此异常的解决方案，基本上都是说要扩大linux系统的文件句柄数限制。 <br />但如果程序对于Socket、Stream等使用后没能及时关闭的话，扩大这个文件句柄数限制是治标不治本的。
  </p>
  
  <p>
    我先是在测试环境扩大了linux的文件句柄数限制，随后提高测试压力，过一段时间后发现还是会报这个异常。 <br />（中间也用lsof命令查看占用的文件句柄数，不断的增加啊，心寒啊。） <br />现象是 用 lsof -p *** 来查看，形如<span class="Apple-converted-space">&#160;</span> <br /><span style="color:red;">java&#160;&#160;&#160; 22055 webapp&#160;&#160; 21w&#160; FIFO&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 0,6&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 29300342 pipe <br />java&#160;&#160;&#160; 22055 webapp&#160;&#160; 22r&#160; FIFO&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 0,6&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; 29256305 pipe</span> <br />在不断增加。
  </p>
  
  <p>
    所以我果断对代码进行了排查。文件的IO操作、对数据库的操作，看了都没有什么问题， <br />最后排查到由Java程序去调用Shell脚本的代码，
  </p>
  
  <p>
    代码写的还是很简单的，看上去很清晰，但是有明显的问题：
  </p>
  
  <div style="border-right:rgb(204,204,204) 1px solid;border-top:rgb(204,204,204) 1px solid;font-size:13px;border-left:rgb(204,204,204) 1px solid;width:1067px;border-bottom:rgb(204,204,204) 1px solid;background-color:rgb(238,238,238);padding:4px 5px 4px 4px;">
    <img style="border-width:0;" alt="" src="http://www.blogjava.net/Images/OutliningIndicators/None.gif" align="top" /><span style="color:rgb(0,0,0);">Process proc </span><span style="color:rgb(0,0,0);">=</span><span style="color:rgb(0,0,0);"> Runtime.getRuntime().exec(cmd); <br /><img style="border-width:0;" alt="" src="http://www.blogjava.net/Images/OutliningIndicators/None.gif" align="top" /></span><span style="color:rgb(0,128,0);">//</span><span style="color:rgb(0,128,0);">略<img style="border-width:0;" alt="" src="http://www.blogjava.net/Images/dot.gif" />对proc.getErrorStream()、proc.getInputStream()流的操作。</span><span style="color:rgb(0,128,0);"> <br /><img style="border-width:0;" alt="" src="http://www.blogjava.net/Images/OutliningIndicators/None.gif" align="top" /></span><span style="color:rgb(0,0,0);">proc.waitFor(); <br /><img style="border-width:0;" alt="" src="http://www.blogjava.net/Images/OutliningIndicators/None.gif" align="top" /></span><span style="color:rgb(0,0,255);">return</span><span style="color:rgb(0,0,0);"> proc.exitValue();</span>
  </div>
  
  <p style="margin:0 0 14px;">
    这里的问题是 对流没有在finally处做关闭处理。这个问题比较明显。 <br />还有一个问题就是Process的使用问题，
  </p>
  
  <p>
    如果对Process的不熟悉的话，可能会以为return proc.exitValue();之后就万事大吉了。 <br />（exitValue()确实很像是已经退出了并得到返回值的意思，估计是这个方法的名字迷惑了我们的开发人员。） <br />实际不然，看Jdk的帮助文档可以发现，要通过destroy()来实现对子进程的销毁并释放占用的File Descriptor。
  </p>
  
  <p style="margin:0 0 14px;">
    这个问题，短时间的测试是不会有问题的，但在投入生产后，随着程序的长期运行，开发中的疏忽就会暴露了。 <br />所以在对使用的方法拿不准的情况下，还是要多做调查，谨慎使用啊。
  </p>
  
  <p>
    <span style="color:red;">希望能让在排查类似问题的朋友注意，如果你排查的代码中也存在Runtime.getRuntime().exec(cmd)这样的调用，那么请确保那段代码没有问题。</span>
  </p></p>
</div>

<p>
  </span></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/17/runtime-getruntime-execcmd%e4%bd%bf%e7%94%a8%e4%b8%8d%e5%bd%93%e5%bc%95%e8%b5%b7%e7%9a%84java-io-ioexception-too-many-open-files%e8%bd%ac/">Runtime.getRuntime().exec(cmd)使用不当引起的java.io.IOException: Too many open files[转]</a>
</p>