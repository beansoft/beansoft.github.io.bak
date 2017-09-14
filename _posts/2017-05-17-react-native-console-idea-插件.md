---
id: 3912
title: 'React Native Console &#8211; IDEA 插件'
date: 2017-05-17T15:11:27+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3912
permalink: '/2017/05/17/react-native-console-idea-%e6%8f%92%e4%bb%b6/'
views:
  - "1718"
categories:
  - Uncategorized
---
一键在IDEA终端中运行React Native开发命令.</p> 

<div>
</div>

<div>
  https://github.com/beansoftapp/react-native-console
</div>

<div>
</div>

<div>
  <h1>
    React Native Console
  </h1>
  
  <p>
    an IDEA/WebStorm/Android Studio Plugin for One-Click run React Native commands in embed terminal
  </p>
  
  <h4>
    <a id="user-content-installation" class="anchor" href="https://github.com/beansoftapp/react-native-console#installation" aria-hidden="true"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Installation
  </h4>
  
  <p>
    First, please setup your React Native dev env:<br /> <a href="https://facebook.github.io/react-native/docs/getting-started.html">https://facebook.github.io/react-native/docs/getting-started.html</a>
  </p>
  
  <p>
    Second, install jar file react-native-console.jar as a plugin to your IDE.<br /> The plugin home page is here: <a href="https://plugins.jetbrains.com/plugin/9564-react-native-console">https://plugins.jetbrains.com/plugin/9564-react-native-console</a>
  </p>
  
  <p>
    Or you can install it through your IDE, bring up Preferences > Plugins > Browse repositories&#8230; , search for &#8216;<strong>React Native Console</strong>&#8216;,<br /> then you can install this plugin there.
  </p>
  
  <p>
    Now just restart and enjoy!
  </p>
  
  <h2>
    <a id="user-content-features" class="anchor" href="https://github.com/beansoftapp/react-native-console#features" aria-hidden="true"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Features
  </h2>
  
  <p>
    OneClick run following commands:<br /> react-native run-android<br /> react-native link<br /> react-native run-ios<br /> npm run start<br /> npm install<br /> Open dev menu on Android device(adb shell input keyevent 82)<br /> forward android device request to dev machine(adb reverse tcp:8081 tcp:8081)<br /> open React Native debugger ui(Chrome browser required)
  </p>
  
  <p>
    react-native log-android<br /> react-native log-ios<br /> gradlew assembleRelease<br /> react-native bundle &#8211;platform android/ios &#8211;dev false
  </p>
  
  <p>
    Auto detect React Native package.json in current folder and parent folder(eg coding Java in Android Studio),<br /> thus the command will auto execute in that folder
  </p>
  
  <h4>
    <a id="user-content-note" class="anchor" href="https://github.com/beansoftapp/react-native-console#note" aria-hidden="true"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Note
  </h4>
  
  <p>
    Java 8 required to run the IDE.
  </p>
  
  <p>
    Only tested on Mac OSX with WebStorm/IDEA/Android Studio.
  </p>
  
  <h2>
    <a id="user-content-功能" class="anchor" href="https://github.com/beansoftapp/react-native-console#%E5%8A%9F%E8%83%BD" aria-hidden="true"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>功能
  </h2>
  
  <p>
    一键运行下列功能:<br /> react-native run-android<br /> react-native link<br /> react-native run-ios<br /> npm run start<br /> npm install<br /> 安卓设备上打开开发菜单(adb shell input keyevent 82)<br /> 安卓设备网络请求转发到开发机(adb reverse tcp:8081 tcp:8081)<br /> 打开 React Native debugger ui(需要Chrome浏览器)<br /> react-native log-android<br /> react-native log-ios<br /> gradlew assembleRelease<br /> react-native bundle &#8211;platform android/ios &#8211;dev false
  </p>
  
  <p>
    自动在当前目录和父级目录检测 React Native的package.json文件位置(比如在Android Studio中只开发Java代码时), 这样所有的npm相关的命令都会自动在正确的目录执行
  </p>
  
  <h4>
    <a id="user-content-screenshot" class="anchor" href="https://github.com/beansoftapp/react-native-console#screenshot" aria-hidden="true"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>ScreenShot
  </h4>
  
  <p>
    <a href="https://camo.githubusercontent.com/6f0aaf6f5a7f8be46cd369b9ee10a1101eba52fd/68747470733a2f2f706c7567696e732e6a6574627261696e732e636f6d2f66696c65732f393536342f73637265656e73686f745f31363833352e706e67" target="_blank"><img src="https://camo.githubusercontent.com/6f0aaf6f5a7f8be46cd369b9ee10a1101eba52fd/68747470733a2f2f706c7567696e732e6a6574627261696e732e636f6d2f66696c65732f393536342f73637265656e73686f745f31363833352e706e67" alt="ScreenShot" data-canonical-src="https://plugins.jetbrains.com/files/9564/screenshot_16835.png" style="max-width:100%;" align="middle" height="201" width="552" /></a>
  </p>
  
  <h4>
    <a id="user-content-demo-gif" class="anchor" href="https://github.com/beansoftapp/react-native-console#demo-gif" aria-hidden="true"><svg aria-hidden="true" class="octicon octicon-link" height="16" version="1.1" viewBox="0 0 16 16" width="16"><path fill-rule="evenodd" d="M4 9h1v1H4c-1.5 0-3-1.69-3-3.5S2.55 3 4 3h4c1.45 0 3 1.69 3 3.5 0 1.41-.91 2.72-2 3.25V8.59c.58-.45 1-1.27 1-2.09C10 5.22 8.98 4 8 4H4c-.98 0-2 1.22-2 2.5S3 9 4 9zm9-3h-1v1h1c1 0 2 1.22 2 2.5S13.98 12 13 12H9c-.98 0-2-1.22-2-2.5 0-.83.42-1.64 1-2.09V6.25c-1.09.53-2 1.84-2 3.25C6 11.31 7.55 13 9 13h4c1.45 0 3-1.69 3-3.5S14.5 6 13 6z"></path></svg></a>Demo Gif
  </h4>
  
  <p>
    <a href="https://raw.githubusercontent.com/beansoftapp/react-native-console/master/screenshot/rnconsole.gif" target="_blank"><img src="https://raw.githubusercontent.com/beansoftapp/react-native-console/master/screenshot/rnconsole.gif" alt="" style="max-width:100%;" /></a>
  </p>
</div>

<div>
</div>

</body></html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [React Native Console &#8211; IDEA 插件](http://www.beansoft.biz/2017/05/17/react-native-console-idea-%e6%8f%92%e4%bb%b6/)