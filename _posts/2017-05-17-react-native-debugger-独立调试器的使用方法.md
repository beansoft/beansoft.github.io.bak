---
id: 3921
title: React Native Debugger 独立调试器的使用方法
date: 2017-05-17T18:40:16+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3921
permalink: '/2017/05/17/react-native-debugger-%e7%8b%ac%e7%ab%8b%e8%b0%83%e8%af%95%e5%99%a8%e7%9a%84%e4%bd%bf%e7%94%a8%e6%96%b9%e6%b3%95/'
views:
  - "1035"
categories:
  - Uncategorized
---
</p> 

<div>
  <a href="https://github.com/jhen0409/react-native-debugger">https://github.com/jhen0409/react-native-debugger</a>&nbsp;先从官网下载.
</div>

<div>
  This is a standalone app for debugging React Native apps, it&#8217;s based on the official <a href="https://facebook.github.io/react-native/docs/debugging.html#chrome-developer-tools">Remote Debugger</a>, and includes React Inspector / Redux DevTools.
</div>

<div>
</div>

<div>
  <span style="font-weight: bold;">Installation</span>
</div>

<div>
</div>

<div>
  The prebuilt binaries can be found on the <a href="https://github.com/jhen0409/react-native-debugger/releases">releases</a> page.
</div>

<div>
</div>

<div>
  如何使用呢? 相当的简单, 参考文档:
</div>

<div>
  <a href="https://github.com/jhen0409/react-native-debugger/blob/master/docs/getting-started.md">https://github.com/jhen0409/react-native-debugger/blob/master/docs/getting-started.md</a>
</div>

<div>
</div>

  * Chrome浏览器中所有的&nbsp;[http://localhost](http://localhost/):<port>/debugger-ui 页面都得关了.
  * 先打开并运行 RNDebugger应用处于等待状态
  * 在模拟器或者真机上打开开发者菜单, 启用 &nbsp;Debug JS Remotely  
    Android:&nbsp;<span style="font-weight: bold;">Command</span>⌘ +<span style="font-weight: bold;">M</span>iOS:<span style="font-weight: bold;">&nbsp;</span><span style="font-weight: bold;">Command</span><span style="font-weight: bold;">⌘ +&nbsp;</span><span style="font-weight: bold;">D</span>
  * 然后不要忘了点击App底部的Inspect按钮来检查界面元素<img id="en-media:image/png:8e0c87f9933e434861957bc8a8e050fd:none:none" src="http://www.beansoft.biz/wp-content/uploads/2017/05/2B4174E3-239F-4844-8316-141F55A25C35-3851-000007588ED8C772_file.png" style="" />  
    <img id="en-media:image/png:96cfcdcaa5fcc41d53f08dfd41c97b47" src="evernotecid://4BC453C7-C6D4-416C-BD62-C05C7E1DB0D7/ENNote/p5995?hash=96cfcdcaa5fcc41d53f08dfd41c97b47" />

<div>
  最终效果:
</div>

<div>
  <img src="http://www.beansoft.biz/wp-content/uploads/2017/05/B8727A82-04AE-4BBE-ABB1-DFD80B3FA55D-3851-0000077003544D44_file.png" style="" />
</div>

<div>
</div>

<div>
</div>

<div>
</div>

<en-clipboard></en-clipboard></body></html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [React Native Debugger 独立调试器的使用方法](http://www.beansoft.biz/2017/05/17/react-native-debugger-%e7%8b%ac%e7%ab%8b%e8%b0%83%e8%af%95%e5%99%a8%e7%9a%84%e4%bd%bf%e7%94%a8%e6%96%b9%e6%b3%95/)