---
id: 401
title: 用微软 IE 8 调试 JavaScript
date: 2010-07-21T14:10:43+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=401
permalink: '/2010/07/21/%e7%94%a8%e5%be%ae%e8%bd%af-ie-8-%e8%b0%83%e8%af%95-javascript/'
views:
  - "3802"
original_post_id:
  - "401"
image: /wp-content/uploads/2012/09/image_thumb72.png
categories:
  - AJAX/JavaScript
tags:
  - Debugger
  - JavaScript
---
&#160; 对开发人员来说，相比较起 Firefox 来，IE最大的缺点，就是连个JavaScript调试器都不好使（勉强也算有了）。还好，微软已经推出了IE8 的下载，地址在

[http://www.microsoft.com/windows/internet-explorer/default.aspx](http://www.microsoft.com/windows/internet-explorer/default.aspx "http://www.microsoft.com/windows/internet-explorer/default.aspx")

[<img title="image" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="429" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/07/image_thumb7.png" width="640" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/image15.png) 

它的新特性包括：

1. CSS 2.1支持。微软决定在这个领域完全遵守W3C标准，放弃一定的向后兼容性。   
2. CSS Certification。IE8将全面通过CSS标准的测试和认证。   
3. 性能。IE8的性能有巨大提升，甚至略好于Firefox 3 Beta。   
4. HTML 5支持。IE8全面支持HTML5标准，实现诸如Ajax页面的回退，本地页面缓存等关键功能。   
能够在网络不通时将整个页面缓存（避免原来填入内容提交后报错，却无法返回）   
5. 开发支持。IE8将内置调试器，不但可以方便地调试Javascript代码，而且可以在调试状态下通过点击查找与该页面元素相应的HTML/CSS/Javascript代码段，大大提升开发效率。 

其它功能等等&#8230;. 

可以看到微软终于向 W3C 标准靠齐了，也许以后大家写网页就不用费劲的特意调试不同的浏览器下的效果了。 

而第5条的内置调试器大概是最大的福音了，要知道以前的版本都必须单独下载IE调试器，而且用法古怪，调试完毕后退出调试器还会把主窗口也给关了。 

先看看IE 8的界面： 

[<img style="border-width:0;" height="189" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/07/image_thumb8.png" width="710" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/image16.png) 

它还提供了模拟IE7界面的功能按钮：Emulate IE 7。点击工具栏上的 Developer Tools 即可启动开发人员工具窗口，如下图所示： 

[<img style="border-width:0;" height="468" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/07/image_thumb9.png" width="607" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/image17.png) 

。之后就可以打开页面进行调试了。调试的方法之一是在左侧源码窗行号上单击设置断点，然后执行到被设置断点的代码。另一种方式呢，则是使用JavaScript中的一个关键字：debugger。例如下面我们做了个能够自动触发调试器的页面： 

> <script>   
> function test() {   
> &#160; var a=1;   
> &#160; var b=2; 
> 
> &#160; debugger;   
> &#160; alert(a+b);   
> }   
> </script> 
> 
> <input type=button onclick="test();" value="启动调试器">

然后用IE8打开此页面，点击页面中出现的**启动调试器**按钮，再看调试器窗口： 

[<img style="border-width:0;" height="334" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/07/image_thumb10.png" width="607" border="0" />](http://www.beansoft.biz/wp-content/uploads/2010/07/image18.png) 

。我想过多的话已经不需要再说了，使用Step Into,Step Over, Step Out等可以控制单步执行，一行行的调试代码，观察变量取值，添加监视（Watch)等，的确是比以前方便多了。 

要结束调试，点击**Stop Debugging** 按钮即可，原来的进程还在，再也不会出现以前的调试器一停止，整个IE进程都退出的尴尬局面了。 

&#160; 

整体感觉，推荐试试！下载包14.4MB(XP版本，需要SP2）。

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [用微软 IE 8 调试 JavaScript](http://www.beansoft.biz/2010/07/21/%e7%94%a8%e5%be%ae%e8%bd%af-ie-8-%e8%b0%83%e8%af%95-javascript/)