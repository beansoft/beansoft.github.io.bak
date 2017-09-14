---
id: 569
title: Google Android Dalvik VM 源码涉嫌抄袭 Oracle OpenJDK JVM 源码?
date: 2010-08-16T18:51:14+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=569
permalink: '/2010/08/16/google-android-dalvik-vm-%e6%b6%89%e5%ab%8c%e6%ba%90%e7%a0%81%e6%8a%84%e8%a2%ad-oracle-openjdk-jvm-%e6%ba%90%e7%a0%81/'
views:
  - "5405"
original_post_id:
  - "569"
categories:
  - Android
tags:
  - Android
  - OpenJDK
  - 抄袭
---
本文只为提供更多信息之目的. 本文中提到的Google, Android, Delvik, Oracle, OpenJDK, JVM, Java 等均属于各自公司的商标或者专利产品.

本文转载请注明作者为 <wlsmon@qq.com>, 来自于 <http://www.beansoft.biz/> .

&#160;

首先, 虚拟机都是C/C++开发的.

Dalvik 的源码可以在这里下: [http://android.git.kernel.org/?p=platform/dalvik.git;a=summary](http://android.git.kernel.org/?p=platform/dalvik.git;a=summary "http://android.git.kernel.org/?p=platform/dalvik.git;a=summary") 然后点下面链接中的最后一个 snapshot 即可下载:

_2010-07-01_ _Bruce Beare_ [Don&#8217;t prelink dalvik for x86 64/15564/2 master](http://android.git.kernel.org/?p=platform/dalvik.git;a=commit;h=034125abd217d874a546010aef430a3969b9587a)&#160;[commit](http://android.git.kernel.org/?p=platform/dalvik.git;a=commit;h=034125abd217d874a546010aef430a3969b9587a) | [commitdiff](http://android.git.kernel.org/?p=platform/dalvik.git;a=commitdiff;h=034125abd217d874a546010aef430a3969b9587a) | [tree](http://android.git.kernel.org/?p=platform/dalvik.git;a=tree;h=034125abd217d874a546010aef430a3969b9587a;hb=034125abd217d874a546010aef430a3969b9587a) | [**snapshot**](http://android.git.kernel.org/?p=platform/dalvik.git;a=snapshot;h=034125abd217d874a546010aef430a3969b9587a;sf=tgz)

Open JDK 6 的源码可以这里下: [http://download.java.net/openjdk/jdk6/](http://download.java.net/openjdk/jdk6/ "http://download.java.net/openjdk/jdk6/") 点击下面链接下载:

OpenJDK 6 source

  * OpenJDK 6 source bundle   
    [openjdk-6-src-b20-21\_jun\_2010.tar.gz](http://download.java.net/openjdk/jdk6/promoted/b20/openjdk-6-src-b20-21_jun_2010.tar.gz), 42.99 MB ([Checksums](http://download.java.net/openjdk/jdk6/promoted/b20/openjdk-6-src-b20-21_jun_2010.md5))

&#160;

下载完毕分别解压缩, 然后可以发现都有一个**jni.h**的文件, 打开来进行比较的结果, 令人惊讶, 大部分代码都几乎是一样的, 只是顶部的版权信息变了&#8230; 呵呵, 难怪会起纠纷. 其源代码的前100行分别如下所示:

<table border="0" cellspacing="0" cellpadding="2" width="100%">
  <tr>
    <td valign="top" width="50%">
      <strong>OpenJDK</strong>
    </td>
    
    <td valign="top" width="50%">
      <strong>Dalvik</strong>
    </td>
  </tr>
  
  <tr>
    <td valign="top" width="50%">
      <div id="codeSnippetWrapper">
        <div style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;padding:0;" id="codeSnippet">
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum1">   1:</span> <span style="color:#008000;">/*</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum2">   2:</span> <span style="color:#008000;"> * @(#)jni.h    1.62 06/02/02</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum3">   3:</span> <span style="color:#008000;"> *</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum4">   4:</span> <span style="color:#008000;"> * Copyright 2006 Sun Microsystems, Inc.  All rights reserved.</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum5">   5:</span> <span style="color:#008000;"> * SUN PROPRIETARY/CONFIDENTIAL.  Use is subject to license terms.</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum6">   6:</span> <span style="color:#008000;"> */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum7">   7:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum8">   8:</span> <span style="color:#008000;">/*</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum9">   9:</span> <span style="color:#008000;"> * We used part of Netscape's Java Runtime Interface (JRI) as the starting</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum10">  10:</span> <span style="color:#008000;"> * point of our design and implementation.</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum11">  11:</span> <span style="color:#008000;"> */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum12">  12:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum13">  13:</span> <span style="color:#008000;">/******************************************************************************</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum14">  14:</span> <span style="color:#008000;"> * Java Runtime Interface</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum15">  15:</span> <span style="color:#008000;"> * Copyright (c) 1996 Netscape Communications Corporation. All rights reserved.</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum16">  16:</span> <span style="color:#008000;"> *****************************************************************************/</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum17">  17:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum18">  18:</span> #ifndef _JAVASOFT_JNI_H_</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum19">  19:</span> #define _JAVASOFT_JNI_H_</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum20">  20:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum21">  21:</span> #include &lt;stdio.h&gt;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum22">  22:</span> #include &lt;stdarg.h&gt;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum23">  23:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum24">  24:</span> <span style="color:#008000;">/* jni_md.h contains the machine-dependent typedefs for jbyte, jint</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum25">  25:</span> <span style="color:#008000;">   and jlong */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum26">  26:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum27">  27:</span> #include <span style="color:#006080;">"jni_md.h"</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum28">  28:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum29">  29:</span> #ifdef __cplusplus</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum30">  30:</span> extern <span style="color:#006080;">"C"</span> {</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum31">  31:</span> #endif</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum32">  32:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum33">  33:</span> <span style="color:#008000;">/*</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum34">  34:</span> <span style="color:#008000;"> * JNI Types</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum35">  35:</span> <span style="color:#008000;"> */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum36">  36:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum37">  37:</span> #ifndef JNI_TYPES_ALREADY_DEFINED_IN_JNI_MD_H</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum38">  38:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum39">  39:</span> typedef unsigned <span style="color:#0000ff;">char</span>    jboolean;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum40">  40:</span> typedef unsigned <span style="color:#0000ff;">short</span>    jchar;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum41">  41:</span> typedef <span style="color:#0000ff;">short</span>        jshort;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum42">  42:</span> typedef <span style="color:#0000ff;">float</span>        jfloat;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum43">  43:</span> typedef <span style="color:#0000ff;">double</span>        jdouble;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum44">  44:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum45">  45:</span> typedef jint            jsize;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum46">  46:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum47">  47:</span> #ifdef __cplusplus</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum48">  48:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum49">  49:</span> <span style="color:#0000ff;">class</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum50">  50:</span> <span style="color:#0000ff;">class</span> _jclass : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum51">  51:</span> <span style="color:#0000ff;">class</span> _jthrowable : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum52">  52:</span> <span style="color:#0000ff;">class</span> _jstring : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum53">  53:</span> <span style="color:#0000ff;">class</span> _jarray : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum54">  54:</span> <span style="color:#0000ff;">class</span> _jbooleanArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum55">  55:</span> <span style="color:#0000ff;">class</span> _jbyteArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum56">  56:</span> <span style="color:#0000ff;">class</span> _jcharArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum57">  57:</span> <span style="color:#0000ff;">class</span> _jshortArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum58">  58:</span> <span style="color:#0000ff;">class</span> _jintArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum59">  59:</span> <span style="color:#0000ff;">class</span> _jlongArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum60">  60:</span> <span style="color:#0000ff;">class</span> _jfloatArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum61">  61:</span> <span style="color:#0000ff;">class</span> _jdoubleArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum62">  62:</span> <span style="color:#0000ff;">class</span> _jobjectArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum63">  63:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum64">  64:</span> typedef _jobject *jobject;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum65">  65:</span> typedef _jclass *jclass;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum66">  66:</span> typedef _jthrowable *jthrowable;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum67">  67:</span> typedef _jstring *jstring;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum68">  68:</span> typedef _jarray *jarray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum69">  69:</span> typedef _jbooleanArray *jbooleanArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum70">  70:</span> typedef _jbyteArray *jbyteArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum71">  71:</span> typedef _jcharArray *jcharArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum72">  72:</span> typedef _jshortArray *jshortArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum73">  73:</span> typedef _jintArray *jintArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum74">  74:</span> typedef _jlongArray *jlongArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum75">  75:</span> typedef _jfloatArray *jfloatArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum76">  76:</span> typedef _jdoubleArray *jdoubleArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum77">  77:</span> typedef _jobjectArray *jobjectArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum78">  78:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum79">  79:</span> #<span style="color:#0000ff;">else</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum80">  80:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum81">  81:</span> struct _jobject;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum82">  82:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum83">  83:</span> typedef struct _jobject *jobject;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum84">  84:</span> typedef jobject jclass;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum85">  85:</span> typedef jobject jthrowable;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum86">  86:</span> typedef jobject jstring;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum87">  87:</span> typedef jobject jarray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum88">  88:</span> typedef jarray jbooleanArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum89">  89:</span> typedef jarray jbyteArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum90">  90:</span> typedef jarray jcharArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum91">  91:</span> typedef jarray jshortArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum92">  92:</span> typedef jarray jintArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum93">  93:</span> typedef jarray jlongArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum94">  94:</span> typedef jarray jfloatArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum95">  95:</span> typedef jarray jdoubleArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum96">  96:</span> typedef jarray jobjectArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum97">  97:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum98">  98:</span> #endif</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum99">  99:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum100"> 100:</span> typedef jobject jweak;</pre>
          
          <p>
            <!--CRLF-->
          </p></p>
        </div></p>
      </div>
    </td>
    
    <td valign="top" width="50%">
      <div id="codeSnippetWrapper">
        <div style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;padding:0;" id="codeSnippet">
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum1">   1:</span> <span style="color:#008000;">/*</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum2">   2:</span> <span style="color:#008000;"> * Copyright 2006 The Android Open Source Project</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum3">   3:</span> <span style="color:#008000;"> *</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum4">   4:</span> <span style="color:#008000;"> * JNI specification, as defined by Sun:</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum5">   5:</span> <span style="color:#008000;"> * http://java.sun.com/javase/6/docs/technotes/guides/jni/spec/jniTOC.html</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum6">   6:</span> <span style="color:#008000;"> *</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum7">   7:</span> <span style="color:#008000;"> * Everything here is expected to be VM-neutral.</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum8">   8:</span> <span style="color:#008000;"> */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum9">   9:</span> #ifndef _JNI_H</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum10">  10:</span> #define _JNI_H</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum11">  11:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum12">  12:</span> #include &lt;stdarg.h&gt;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum13">  13:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum14">  14:</span> <span style="color:#008000;">/*</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum15">  15:</span> <span style="color:#008000;"> * Primitive types that match up with Java equivalents.</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum16">  16:</span> <span style="color:#008000;"> */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum17">  17:</span> #ifdef HAVE_INTTYPES_H</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum18">  18:</span> # include &lt;inttypes.h&gt;      <span style="color:#008000;">/* C99 */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum19">  19:</span> typedef uint8_t         jboolean;       <span style="color:#008000;">/* unsigned 8 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum20">  20:</span> typedef int8_t          jbyte;          <span style="color:#008000;">/* signed 8 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum21">  21:</span> typedef uint16_t        jchar;          <span style="color:#008000;">/* unsigned 16 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum22">  22:</span> typedef int16_t         jshort;         <span style="color:#008000;">/* signed 16 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum23">  23:</span> typedef int32_t         jint;           <span style="color:#008000;">/* signed 32 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum24">  24:</span> typedef int64_t         jlong;          <span style="color:#008000;">/* signed 64 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum25">  25:</span> typedef <span style="color:#0000ff;">float</span>           jfloat;         <span style="color:#008000;">/* 32-bit IEEE 754 */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum26">  26:</span> typedef <span style="color:#0000ff;">double</span>          jdouble;        <span style="color:#008000;">/* 64-bit IEEE 754 */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum27">  27:</span> #<span style="color:#0000ff;">else</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum28">  28:</span> typedef unsigned <span style="color:#0000ff;">char</span>   jboolean;       <span style="color:#008000;">/* unsigned 8 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum29">  29:</span> typedef signed <span style="color:#0000ff;">char</span>     jbyte;          <span style="color:#008000;">/* signed 8 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum30">  30:</span> typedef unsigned <span style="color:#0000ff;">short</span>  jchar;          <span style="color:#008000;">/* unsigned 16 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum31">  31:</span> typedef <span style="color:#0000ff;">short</span>           jshort;         <span style="color:#008000;">/* signed 16 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum32">  32:</span> typedef <span style="color:#0000ff;">int</span>             jint;           <span style="color:#008000;">/* signed 32 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum33">  33:</span> typedef <span style="color:#0000ff;">long</span> <span style="color:#0000ff;">long</span>       jlong;          <span style="color:#008000;">/* signed 64 bits */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum34">  34:</span> typedef <span style="color:#0000ff;">float</span>           jfloat;         <span style="color:#008000;">/* 32-bit IEEE 754 */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum35">  35:</span> typedef <span style="color:#0000ff;">double</span>          jdouble;        <span style="color:#008000;">/* 64-bit IEEE 754 */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum36">  36:</span> #endif</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum37">  37:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum38">  38:</span> <span style="color:#008000;">/* "cardinal indices and sizes" */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum39">  39:</span> typedef jint            jsize;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum40">  40:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum41">  41:</span> #ifdef __cplusplus</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum42">  42:</span> <span style="color:#008000;">/*</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum43">  43:</span> <span style="color:#008000;"> * Reference types, in C++</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum44">  44:</span> <span style="color:#008000;"> */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum45">  45:</span> <span style="color:#0000ff;">class</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum46">  46:</span> <span style="color:#0000ff;">class</span> _jclass : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum47">  47:</span> <span style="color:#0000ff;">class</span> _jstring : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum48">  48:</span> <span style="color:#0000ff;">class</span> _jarray : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum49">  49:</span> <span style="color:#0000ff;">class</span> _jobjectArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum50">  50:</span> <span style="color:#0000ff;">class</span> _jbooleanArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum51">  51:</span> <span style="color:#0000ff;">class</span> _jbyteArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum52">  52:</span> <span style="color:#0000ff;">class</span> _jcharArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum53">  53:</span> <span style="color:#0000ff;">class</span> _jshortArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum54">  54:</span> <span style="color:#0000ff;">class</span> _jintArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum55">  55:</span> <span style="color:#0000ff;">class</span> _jlongArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum56">  56:</span> <span style="color:#0000ff;">class</span> _jfloatArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum57">  57:</span> <span style="color:#0000ff;">class</span> _jdoubleArray : <span style="color:#0000ff;">public</span> _jarray {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum58">  58:</span> <span style="color:#0000ff;">class</span> _jthrowable : <span style="color:#0000ff;">public</span> _jobject {};</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum59">  59:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum60">  60:</span> typedef _jobject*       jobject;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum61">  61:</span> typedef _jclass*        jclass;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum62">  62:</span> typedef _jstring*       jstring;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum63">  63:</span> typedef _jarray*        jarray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum64">  64:</span> typedef _jobjectArray*  jobjectArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum65">  65:</span> typedef _jbooleanArray* jbooleanArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum66">  66:</span> typedef _jbyteArray*    jbyteArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum67">  67:</span> typedef _jcharArray*    jcharArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum68">  68:</span> typedef _jshortArray*   jshortArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum69">  69:</span> typedef _jintArray*     jintArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum70">  70:</span> typedef _jlongArray*    jlongArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum71">  71:</span> typedef _jfloatArray*   jfloatArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum72">  72:</span> typedef _jdoubleArray*  jdoubleArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum73">  73:</span> typedef _jthrowable*    jthrowable;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum74">  74:</span> typedef _jobject*       jweak;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum75">  75:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum76">  76:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum77">  77:</span> #<span style="color:#0000ff;">else</span> <span style="color:#008000;">/* not __cplusplus */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum78">  78:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum79">  79:</span> <span style="color:#008000;">/*</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum80">  80:</span> <span style="color:#008000;"> * Reference types, in C.</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum81">  81:</span> <span style="color:#008000;"> */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum82">  82:</span> typedef <span style="color:#0000ff;">void</span>*           jobject;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum83">  83:</span> typedef jobject         jclass;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum84">  84:</span> typedef jobject         jstring;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum85">  85:</span> typedef jobject         jarray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum86">  86:</span> typedef jarray          jobjectArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum87">  87:</span> typedef jarray          jbooleanArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum88">  88:</span> typedef jarray          jbyteArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum89">  89:</span> typedef jarray          jcharArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum90">  90:</span> typedef jarray          jshortArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum91">  91:</span> typedef jarray          jintArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum92">  92:</span> typedef jarray          jlongArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum93">  93:</span> typedef jarray          jfloatArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum94">  94:</span> typedef jarray          jdoubleArray;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum95">  95:</span> typedef jobject         jthrowable;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum96">  96:</span> typedef jobject         jweak;</pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum97">  97:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum98">  98:</span> #endif <span style="color:#008000;">/* not __cplusplus */</span></pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum99">  99:</span>&#160; </pre>
          
          <p>
            <!--CRLF-->
          </p>
          
          <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:&#039;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#606060;" id="lnum100"> 100:</span> struct _jfieldID;                       <span style="color:#008000;">/* opaque structure */</span></pre>
          
          <p>
            <!--CRLF-->
          </p></p>
        </div></p>
      </div>
    </td>
  </tr>
</table>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Google Android Dalvik VM 源码涉嫌抄袭 Oracle OpenJDK JVM 源码?](http://www.beansoft.biz/2010/08/16/google-android-dalvik-vm-%e6%b6%89%e5%ab%8c%e6%ba%90%e7%a0%81%e6%8a%84%e8%a2%ad-oracle-openjdk-jvm-%e6%ba%90%e7%a0%81/)