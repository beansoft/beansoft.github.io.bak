---
id: 3899
title: React Native 集成到现有Android App中的常见错误及注意事项
date: 2017-03-08T13:45:24+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3899
permalink: '/2017/03/08/reactive-native-%e9%9b%86%e6%88%90%e5%88%b0%e7%8e%b0%e6%9c%89android-app%e4%b8%ad%e7%9a%84%e5%b8%b8%e8%a7%81%e9%94%99%e8%af%af%e5%8f%8a%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9/'
views:
  - "3557"
categories:
  - Uncategorized
---
</p> 

<div>
  <div>
    说明: 本文仅适用于河狸家Android App的集成过程, 部分细节可能会和您的项目有出入. 您本地的新的安装包一般来说会比0.41.0新. 因为React Native更新很快, 建议开发中绑定一个版本.
  </div>
  
  <div>
  </div>
  
  <ol start="1">
    <li>
      首先一定要按照官方向导创建一个HelloWorld并运行成功, 建议做, 确保环境没问题 &nbsp;<a href="https://facebook.github.io/react-native/docs/getting-started.html">https://facebook.github.io/react-native/docs/getting-started.html</a>
    </li>
    <li>
      参考官方文档:&nbsp;<a href="https://facebook.github.io/react-native/docs/integration-with-existing-apps.html">https://facebook.github.io/react-native/docs/integration-with-existing-apps.html</a>
    </li>
    <li>
      app的<font style="font-family: Menlo; font-size: 12px;">dependencies</font>中一定要按照粗体这样写(减少全局配置文件带来的可能干扰):
    </li>
  </ol>
  
  <p>
    a. 要填写本地node_modules的url作为依赖<br />b. 要填写固定版本的RN依赖, 例如默认是+, 很容易自动取到低版本(<font style="font-weight: bold; font-family: Menlo; font-size: 12px; color: rgb(0, 128, 0);">com.facebook.react:react-native:0.41.0), 会导致一些不必要的异常.&nbsp;</font></div> 
    
    <div>
      <font style="font-weight: bold; font-family: Menlo; font-size: 12px; color: rgb(0, 128, 0);"><br /></font>
    </div>
    
    <div>
      <font style="font-weight: bold; font-family: Menlo; font-size: 12px; color: rgb(0, 128, 0);"></p> 
      
      <div>
        <font color="#ff2600">先讲一个官方文档中的大坑:</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">In your project&#8217;s <code>build.gradle</code> file add an entry for the local React Native maven directory:<br /> </font>
      </div>
      
      <div>
      </div>
      
      <div>
        <font style="font-size: 14px;">allprojects {</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;repositories {</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#8230;</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;maven {</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;// All of React Native (JS, Android binaries) is installed from npm</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;url &#8220;$rootDir/../node_modules/react-native/android&#8221;</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;}</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">&nbsp;&nbsp;&nbsp;&nbsp;&#8230;</font>
      </div>
      
      <div>
        <font style="font-size: 14px;">}<br /></font>
      </div>
      
      <div>
        <font style="font-size: 14px;"><br /></font>
      </div>
      
      <div>
        <font style="font-size: 14px;">实践证明这样并不能成功找到对应版本的RN库(也许是因为各种build.gradle中的路径产生了冲突), 结果证实只能加到单个项目的build.gradle的</font><font style="font-size: 14px;">dependencies这块一般是不会出问题的.</font>
      </div>
      
      <p>
        </font></div> 
        
        <div>
          <font face="Menlo" color="#008000" size="2"><b><br /></b></font>
        </div>
        
        <div>
          <font face="Menlo" size="2"><b></p> 
          
          <pre style="font-family: Menlo; font-size: 9pt;">compileSdkVersion <span style="color: rgb(0, 0, 255);">23</span> // 22不行, 会报manifest等错误</pre>
          
          <p>
            </b></font><span style="font-family: Menlo; font-size: 9pt;">dependencies {</span><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp; compile fileTree(</span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">include</span><span style="font-family: Menlo; font-size: 9pt;">: </span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">&#8216;*.jar&#8217;</span><span style="font-family: Menlo; font-size: 9pt;">, </span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">dir</span><span style="font-family: Menlo; font-size: 9pt;">: </span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">&#8216;libs&#8217;</span><span style="font-family: Menlo; font-size: 9pt;">)</span><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp; repositories {</span><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; mavenCentral()</span><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; jcenter()</span><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; maven { url </span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">&#8220;<a href="https://jitpack.io/">https://jitpack.io</a>&#8221; </span><span style="font-family: Menlo; font-size: 9pt;">}</span><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; flatDir { dirs </span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">&#8216;libs&#8217; </span><span style="font-family: Menlo; font-size: 9pt;">}</span><br style="font-family: Menlo; font-size: 9pt;" /><b style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <font color="#ff2600">maven {</font>&nbsp; <span style="color:#808080;font-style:italic;">// All of React Native (JS, Android binaries) is installed from npm<br /></span><font color="#ff2600"><span style="font-style: italic;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span>url &#8220;$rootDir/node_modules/react-native/android&#8221;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }</font></b><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp; }</span><br style="font-family: Menlo; font-size: 9pt;" /><span style="font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp; compile </span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">&#8220;com.facebook.react:react-native:0.41.0&#8221; </span><span style="font-family: Menlo; font-size: 9pt; color: rgb(128, 128, 128); font-style: italic;">// From node_modules.</span></div> 
            
            <div>
              <span style="font-family: Menlo; font-size: 9pt; color: rgb(128, 128, 128); font-style: italic;"><font style="font-weight: bold; color: rgb(0, 128, 0);">检测标准:</font></span>
            </div>
            
            <div>
              <div>
              </div>
              
              <div>
                <font style="font-weight: bold; font-family: Menlo; font-size: 12px; color: rgb(0, 128, 0);"></p> 
                
                <pre style="color: rgb(0, 0, 0); font-family: Menlo; font-size: 9pt;"><span style="color: rgb(0, 0, 128);">protected void </span>onPause() {<br />&nbsp;&nbsp;&nbsp; <span style="color: rgb(0, 0, 128);">super</span>.onPause();<br /><br />&nbsp;&nbsp;&nbsp; <span style="color: rgb(0, 0, 128);">if </span>(<span style="color: rgb(102, 14, 122);">mReactInstanceManager </span>!= <span style="color: rgb(0, 0, 128);">null</span>) {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color: rgb(102, 14, 122);">mReactInstanceManager</span>.onHostPause(<span style="color: rgb(0, 0, 128);">this</span>);<br />&nbsp;&nbsp;&nbsp; }<br />}
</pre>
                
                <p>
                  </font></div> </div> 
                  
                  <div>
                    <font face="Menlo" color="#008000" size="2"><b>上面的代码不会编译报错.</b></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(128, 128, 128); font-style: italic;"><br /></span>
                  </div>
                  
                  <div>
                    <pre style="font-family: Menlo; font-size: 9pt;"><ol start="4">
  <li>
    <span style="font-size: 9pt;">项目一般的本地第三方Lib有x86, </span><font style="font-weight: bold; color: rgb(0, 128, 0);">armeabi等目录, 但是RN默认的lib库只有x86和armeabi-v7a, 所以要用到第一步中的APK所生成的so文件, 或者从本地的AAR解压缩: <span style="font-weight: normal; font-size: 11px; font-variant-ligatures: no-common-ligatures;">node_modules/react-native/android/com/facebook/react/react-native/0.41.0/react-native-0.41.0.aar, 将armeabi-v7a中的so库复制到<font style="font-weight: bold; font-size: 12px;">armeabi中, 然后删除ndk中对armeabi-v7a的打包支持</font></span></font><br />
  </li>
</ol></pre>
                    
                    <pre><font face="Menlo" size="2">android {<br /><br />&nbsp;&nbsp;&nbsp; compileSdkVersion </font><span style="color: rgb(0, 0, 255); font-family: Menlo; font-size: 9pt;">23<br /></span><span style="color: rgb(0, 0, 255); font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp; </span><font face="Menlo" size="2">buildToolsVersion </font><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;">'25.0.2'<br /></span><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;"><br /></span><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;">&nbsp;&nbsp;&nbsp; </span><font face="Menlo" size="2">defaultConfig {</font></pre>
                    
                    <pre><font face="Menlo" size="2">...</font></pre>
                    
                    <pre><span style="color: rgb(0, 0, 255); font-family: Menlo; font-size: 9pt;"><br /></span><span style="color: rgb(0, 0, 255); font-family: Menlo; font-size: 9pt;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">/**<br /></span><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; * not like proguard, multiDexKeepProguard is not a list, so we can't just<br /></span><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; * add for you in our task. you can copy tinker keep rules at<br /></span><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; * build/intermediates/tinker_intermediates/tinker_multidexkeep.pro<br /></span><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; */<br /></span><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><font face="Menlo" size="2">multiDexKeepProguard file(</font><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;">"keep_in_main_dex.txt"</span><font face="Menlo" size="2">)<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ndk {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </font><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">//jpush 选择要添加的对应cpu类型的.so库。&nbsp; 还可以添加 'x86', 'x86_64', 'mips64','armeabi-v7a', 'armeabi-v8a',<br /></span><span style="color: rgb(128, 128, 128); font-family: Menlo; font-size: 9pt; font-style: italic;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><font face="Menlo" size="2">abiFilters </font><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;">'armeabi'</span><font face="Menlo" size="2">, </font><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;">'x86'</span><font face="Menlo" size="2">, </font><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;">'mips'<br /></span><span style="color: rgb(0, 128, 0); font-family: Menlo; font-size: 9pt; font-weight: bold;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><font face="Menlo" size="2">}
</font></pre>
                    
                    <p>
                      </div> 
                      
                      <div>
                        <ol start="5">
                          <li>
                            常见运行错误与解决
                          </li>
                        </ol>
                        
                        <p>
                          1).&nbsp;com.facebook.react.devsupport.JSException: Could not get BatchedBridge, make sure your bundle is packaged correctly
                        </p>
                        
                        <div>
                          这个是因为没有打包jsbundle到app中. 解决方案需要新建assets目录(如果没有), 然后把JS打包进去, 用于发版时用.
                        </div>
                        
                        <div>
                          react-native bundle &#8211;platform android &#8211;entry-file index.android.js &#8211;bundle-output android/app/src/main/assets/index.android.bundle &#8211;dev false
                        </div>
                        
                        <div>
                        </div>
                        
                        <div>
                          2).&nbsp;TypeError: undefined is not a function (evaluating ‘remoteModules.forEach&#8217;)
                        </div>
                        
                        <div>
                          <img src="http://www.beansoft.biz/wp-content/uploads/2017/03/D3829785-7B4E-4A12-9BFF-E85EF073323D-2963-00000930B63D6418_file.png" style="" />
                        </div>
                      </div>
                      
                      <div>
                        原因:&nbsp;<code>node_modules 中的文件不完整, 解决方案: 从运行正常的项目出复制一份 或 重新初始化(注意保持网络环境良好), 参考:&nbsp;&lt;a href="http://stackoverflow.com/questions/39924469/typeerror-undefined-is-not-a-function-evaluating-remotemodules-foreach">&lt;font style="font-size: 13px;">http://stackoverflow.com/questions/39924469/typeerror-undefined-is-not-a-function-evaluating-remotemodules-foreach&lt;/font>&lt;/a></code>
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        3).&nbsp;Could not connect to development server.
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Try the following to fix the issue:
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• Ensure that the packager server is running
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• Ensure that your device/emulator is connected to your machine and has USB debugging enabled &#8211; run &#8216;adb devices&#8217; to see a list of connected devices
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• Ensure Airplane Mode is disabled
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• If you&#8217;re on a physical device connected to the same machine, run &#8216;adb reverse tcp:8081 tcp:8081&#8217; to forward requests from your device
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• If your device is on the same Wi-Fi network, set &#8216;Debug server host & port for device&#8217; in &#8216;Dev settings&#8217; to your machine&#8217;s IP address and the port of the local dev server &#8211; e.g. 10.0.1.1:8081
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;URL: <a href="http://localhost:8081/index.android.bundle?platform=android&dev=true&hot=false&minify=false">http://localhost:8081/index.android.bundle?platform=android&dev=true&hot=false&minify=false</a>
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        最快解决方案:&nbsp;adb reverse tcp:8081 tcp:8081
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        稍慢的方案或者要连别人的电脑调试: 摇晃设备, 打开 Dev Settings, 然后再点 Debugging 下面的
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        Debug server host & port for device, 输入开发机的局域网IP+端口8080, 例如:&nbsp;10.0.1.1:8081
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        4). 如何启用实时刷新代码预览?
                      </div>
                      
                      <div>
                        &nbsp; &nbsp;&nbsp;摇晃设备, 打开 Dev Settings, 然后点击 Enable Hot Reload. 然后首次加载会稍微有点慢, 后面就可以实时预览了.
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        5): 什么是jest?
                      </div>
                      
                      <div>
                        <a href="http://facebook.github.io/jest/">http://facebook.github.io/jest/</a>&nbsp;一套号称0配置的JS测试框架
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        6): 错误&nbsp;Seems you&#8217;re trying to access &#8216;ReactNative.createClass&#8217; from the &#8216;react-native&#8217; package. Perhaps you meant to access &#8216;React.createClass&#8217; from the &#8216;react&#8217; package instead?
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For example, instead of:
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;import React, { Component, View } from &#8216;react-native&#8217;;
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;You should now do:
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;import React, { Component } from &#8216;react&#8217;;
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;import { View } from &#8216;react-native&#8217;;
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Check the release notes on how to upgrade your code &#8211; <a href="https://github.com/facebook/react-native/releases/tag/v0.25.1">https://github.com/facebook/react-native/releases/tag/v0.25.1</a>
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        原因: 用了旧的Reac Native语法, 需要改写:
                      </div>
                      
                      <div>
                      </div>
                      
                      <div>
                        <span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">&#8216;use strict&#8217;</span><span style="font-family: Menlo; font-size: 9pt; background-color: rgb(255, 255, 255);">;</span>
                      </div>
                      
                      <div>
                        <pre style="font-family: Menlo; font-size: 9pt;"><br /><span style="color:#000080;font-weight:bold;">var </span><span style="color:#458383;">React </span>= <span style="font-style:italic;">require</span>(<span style="color:#008000;font-weight:bold;">'react-native'</span>);<br /><span style="color:#000080;font-weight:bold;">var </span>{<br />&nbsp;&nbsp;&nbsp; <span style="color:#7a7a43;">AppRegistry</span>,<br />&nbsp;&nbsp;&nbsp; <span style="color:#7a7a43;">StyleSheet</span>,<br />&nbsp;&nbsp;&nbsp; <span style="color:#7a7a43;">Text</span>,<br />&nbsp;&nbsp;&nbsp; <span style="color:#7a7a43;">View</span>,<br />} = <span style="color:#458383;">React</span>;<br /><br /><span style="color:#000080;font-weight:bold;">var </span><span style="color:#458383;">DoubanMovie </span>= <span style="color:#458383;">React</span>.<span style="color:#660e7a;font-weight:bold;">createClass</span>({<br />&nbsp;&nbsp;&nbsp; <span style="color:#7a7a43;">render</span>: <span style="color:#000080;font-weight:bold;">function</span>() {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#000080;font-weight:bold;">return </span>(<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">View </span><span style="color:#0000ff;background-color:#efefef;font-weight:bold;">style</span><span style="color:#008000;background-color:#efefef;font-weight:bold;">=</span>{<span style="color:#458383;">styles</span>.<span style="color:#660e7a;font-weight:bold;">container</span>}<span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">Text </span><span style="color:#0000ff;background-color:#efefef;font-weight:bold;">style</span><span style="color:#008000;background-color:#efefef;font-weight:bold;">=</span>{<span style="color:#458383;">styles</span>.<span style="color:#660e7a;font-weight:bold;">welcome</span>}<span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 嗨，我是 Douban 1.0 版本 ！<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;/</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">Text</span><span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;/</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">View</span><span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; );<br />&nbsp;&nbsp;&nbsp; }<br />});<br /><br /><span style="color:#000080;font-weight:bold;">var </span><span style="color:#458383;">styles </span>= <span style="color:#7a7a43;">StyleSheet</span>.<span style="color:#7a7a43;">create</span>({<br />&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">container</span>: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">flex</span>: <span style="color:#0000ff;">1</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">justifyContent</span>: <span style="color:#008000;font-weight:bold;">'center'</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">alignItems</span>: <span style="color:#008000;font-weight:bold;">'center'</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">backgroundColor</span>: <span style="color:#008000;font-weight:bold;">'#F5FCFF'</span>,<br />&nbsp;&nbsp;&nbsp; },<br />&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">welcome</span>: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">fontSize</span>: <span style="color:#0000ff;">20</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">textAlign</span>: <span style="color:#008000;font-weight:bold;">'center'</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">margin</span>: <span style="color:#0000ff;">10</span>,<br />&nbsp;&nbsp;&nbsp; }<br />});<br /><br /><span style="color:#7a7a43;">AppRegistry</span>.<span style="color:#7a7a43;">registerComponent</span>(<span style="color:#008000;font-weight:bold;">'DoubanMovie'</span>, () =&gt; <span style="color:#458383;">DoubanMovie</span>);</pre>
                      </div>
                      
                      <div>
                        改为:&nbsp;
                      </div>
                      
                      <div>
                        <pre style="background-color: rgb(255, 255, 255); font-family: Menlo; font-size: 9pt;"><span style="color:#000080;font-weight:bold;">import </span>React, {Component} <span style="color:#000080;font-weight:bold;">from </span><span style="color:#008000;font-weight:bold;">'react'</span>;<br /><span style="color:#000080;font-weight:bold;">import </span>{<br />&nbsp;&nbsp;&nbsp; AppRegistry,<br />&nbsp;&nbsp;&nbsp; StyleSheet,<br />&nbsp;&nbsp;&nbsp; Text,<br />&nbsp;&nbsp;&nbsp; View,<br />&nbsp;&nbsp;&nbsp; Button<br />} <span style="color:#000080;font-weight:bold;">from </span><span style="color:#008000;font-weight:bold;">'react-native'</span>;<br /><br /><br /><span style="color:#000080;font-weight:bold;">export default class </span>DoubanMovie <span style="color:#000080;font-weight:bold;">extends </span>Component {<br />&nbsp;&nbsp;&nbsp; <span style="color:#7a7a43;">render</span>() {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#000080;font-weight:bold;">return </span>(<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">View </span><span style="color:#0000ff;background-color:#efefef;font-weight:bold;">style</span><span style="color:#008000;background-color:#efefef;font-weight:bold;">=</span>{<span style="color:#458383;">styles</span>.<span style="color:#660e7a;font-weight:bold;">container</span>}<span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">Text </span><span style="color:#0000ff;background-color:#efefef;font-weight:bold;">style</span><span style="color:#008000;background-color:#efefef;font-weight:bold;">=</span>{<span style="color:#458383;">styles</span>.<span style="color:#660e7a;font-weight:bold;">welcome</span>}<span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 嗨，我是 Douban 1.0 版本 ！<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;/</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">Text</span><span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="background-color:#efefef;">&lt;/</span><span style="color:#000080;background-color:#efefef;font-weight:bold;">View</span><span style="background-color:#efefef;">&gt;</span><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; );<br />&nbsp;&nbsp;&nbsp; }<br />}<br /><br /><span style="color:#000080;font-weight:bold;">const </span><span style="color:#458383;">styles </span>= StyleSheet.<span style="color:#7a7a43;">create</span>({<br />&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">container</span>: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">flex</span>: <span style="color:#0000ff;">1</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">backgroundColor</span>: <span style="color:#008000;font-weight:bold;">'#FFFFFF'</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">flexDirection</span>: <span style="color:#008000;font-weight:bold;">'column'<br /></span><span style="color:#008000;font-weight:bold;">&nbsp;&nbsp;&nbsp; </span>},<br /><br />&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">welcome</span>: {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">fontSize</span>: <span style="color:#0000ff;">20</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">textAlign</span>: <span style="color:#008000;font-weight:bold;">'center'</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">margin</span>: <span style="color:#0000ff;">10</span>,<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <span style="color:#660e7a;font-weight:bold;">backgroundColor</span>: <span style="color:#008000;font-weight:bold;">'#008800'</span>,<br />&nbsp;&nbsp;&nbsp; }<br />});<br /><br />AppRegistry.<span style="color:#7a7a43;">registerComponent</span>(<span style="color:#008000;font-weight:bold;">'DoubanMovie'</span>, () =&gt; DoubanMovie);
</pre>
                        
                        <p>
                          </div> 
                          
                          <div>
                          </div>
                          
                          <div>
                            7):&nbsp;Hot loading isn&#8217;t working because it cannot connect to the development server.
                          </div>
                          
                          <div>
                          </div>
                          
                          <div>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Try the following to fix the issue:
                          </div>
                          
                          <div>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#8211; Ensure that the packager server is running and available on the same network
                          </div>
                          
                          <div>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#8211; Ensure that your device/emulator is connected to your machine and has USB debugging enabled &#8211; run &#8216;adb devices&#8217; to see a list of connected devices
                          </div>
                          
                          <div>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#8211; If you&#8217;re on a physical device connected to the same machine, run &#8216;adb reverse tcp:8081 tcp:8081&#8217; to forward requests from your device
                          </div>
                          
                          <div>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#8211; If your device is on the same Wi-Fi network, set &#8216;Debug server host & port for device&#8217; in &#8216;Dev settings&#8217; to your machine&#8217;s IP address and the port of the local dev server &#8211; e.g. 10.0.1.1:8081
                          </div>
                          
                          <div>
                          </div>
                          
                          <div>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;URL: localhost:8081
                          </div>
                          
                          <div>
                          </div>
                          
                          <div>
                            &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Error: Expected &#8216;Connection&#8217; header value &#8216;Upgrade&#8217; but was &#8216;null&#8217;
                          </div>
                          
                          <div>
                            原因: 安卓机上跑了代理程序, 同时又运行了&nbsp;adb reverse tcp:8081 tcp:8081 导致实际上Mac上的代理服务器不能很好的处理WebSocket请求.
                          </div>
                          
                          <div>
                          </div>
                          
                          <p>
                            </body></html>
                          </p>
                          
                          <p>
                            转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2017/03/08/reactive-native-%e9%9b%86%e6%88%90%e5%88%b0%e7%8e%b0%e6%9c%89android-app%e4%b8%ad%e7%9a%84%e5%b8%b8%e8%a7%81%e9%94%99%e8%af%af%e5%8f%8a%e6%b3%a8%e6%84%8f%e4%ba%8b%e9%a1%b9/">React Native 集成到现有Android App中的常见错误及注意事项</a>
                          </p>