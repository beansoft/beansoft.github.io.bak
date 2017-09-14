---
id: 3917
title: Android Gradle编译任务动态修改AndroidManifest的内容
date: 2017-04-14T14:45:18+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3917
permalink: '/2017/04/14/android-gradle%e7%bc%96%e8%af%91%e4%bb%bb%e5%8a%a1%e5%8a%a8%e6%80%81%e4%bf%ae%e6%94%b9androidmanifest%e7%9a%84%e5%86%85%e5%ae%b9/'
views:
  - "1060"
categories:
  - Uncategorized
---
</p> 

<pre style="background-color: rgb(255, 255, 255); font-family: Menlo; font-size: 9pt;">因为新的Gradle有Instant Run功能, 一些旧的代码不能正确运行, 此功能可用于动态替换一些占位符的内容.</pre>

<pre style="background-color: rgb(255, 255, 255); font-family: Menlo; font-size: 9pt;">参考: http://stackoverflow.com/questions/36874191/editing-androidmanifest-xml-in-gradle-task-processmanifest-dolast-has-no-effect</pre>

<pre style="background-color: rgb(255, 255, 255);"><font face="Menlo"><span style="font-size: 9pt;">android.applicationVariants.all { variant -&gt;<br />    variant.outputs.each { output -&gt;<br />        output.processManifest.doLast {<br />            </span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 0, 67); font-weight: bold;">if</span><font face="Menlo"><span style="font-size: 9pt;">(!rootProject.ext.enableThinker) {<br />                [output.processManifest.manifestOutputFile,<br />                 output.processManifest.instantRunManifestOutputFile<br />                ].forEach({ File manifestOutFile -&gt;<br />                    </span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 0, 67); font-weight: bold;">if </span><font face="Menlo"><span style="font-size: 9pt;">(manifestOutFile.exists()) {<br />                        </span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 0, 67); font-weight: bold;">def </span><font face="Menlo"><span style="font-size: 9pt;">newFileContents = manifestOutFile.getText(</span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">'UTF-8'</span><font face="Menlo"><span style="font-size: 9pt;">).replace(<br />                                </span></font><font color="#008000" face="Menlo"><span style="font-size: 12px;"><b>“</b></span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 0, 128); font-weight: bold;">\"</span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">xxxxApplication</span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 0, 128); font-weight: bold;">\"</span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">"</span><font face="Menlo"><span style="font-size: 9pt;">, </span></font><font color="#008000" face="Menlo"><span style="font-size: 12px;"><b>“</b></span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 0, 128); font-weight: bold;">\"</span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">xxxxApplicationDev</span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 0, 128); font-weight: bold;">\"</span><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">"</span><font face="Menlo"><span style="font-size: 9pt;">)<br />                        manifestOutFile.write(newFileContents, </span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">'UTF-8'</span><font face="Menlo"><span style="font-size: 9pt;">)<br />                        println </span></font><span style="font-family: Menlo; font-size: 9pt; color: rgb(0, 128, 0); font-weight: bold;">"*************** 更新AndroidManifest ********" </span><font face="Menlo"><span style="font-size: 9pt;">+ manifestOutFile<br />                    }<br />                })<br />            }<br />        }<br /><br />    }<br />}</span></font></pre>

</body></html>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Android Gradle编译任务动态修改AndroidManifest的内容](http://www.beansoft.biz/2017/04/14/android-gradle%e7%bc%96%e8%af%91%e4%bb%bb%e5%8a%a1%e5%8a%a8%e6%80%81%e4%bf%ae%e6%94%b9androidmanifest%e7%9a%84%e5%86%85%e5%ae%b9/)