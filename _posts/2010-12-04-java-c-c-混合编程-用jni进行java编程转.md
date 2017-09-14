---
id: 1476
title: 'Java C C++ 混合编程-用JNI进行Java编程[转]'
date: 2010-12-04T17:06:36+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1476
permalink: '/2010/12/04/java-c-c-%e6%b7%b7%e5%90%88%e7%bc%96%e7%a8%8b-%e7%94%a8jni%e8%bf%9b%e8%a1%8cjava%e7%bc%96%e7%a8%8b%e8%bd%ac/'
views:
  - "4547"
original_post_id:
  - "1476"
categories:
  - Java SE
---
最新的Java混合本地语言的技术是JNA, 详情可Google.

IBM文章完整查看: <http://www.ibm.com/developerworks/cn/education/java/j-jni/index.html>

### 用 JNI 进行 Java 编程

[Scott Stricker](http://www.ibm.com/developerworks/cn/education/java/j-jni/authors.html#author1), 企业应用程序开发人员, IBM

**简介：**&#160; 本教程描述和演示了 Java 本机接口（Java Native Interface）的基本的和最常用的技术 ― 从 Java 程序调用 C 或 C++ 代码，以及从 C 或 C++ 程序调用 Java 代码 ― 以帮助您迅速而高效地开发自己的 JNI 解决方案。

[](http://www.ibm.com/developerworks/cn/education/java/j-jni/index.html#)

<span class="Apple-style-span" style="word-spacing:0;font:medium simsun;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="text-align:left;"> </p> 

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  <span class="atitle" style="font-weight:bold;font-size:1.5em;">关于本教程</span>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  <a name="N1011F"><span class="smalltitle" style="font-weight:bold;font-size:1.2em;">本教程是关于什么的？</span></a>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  Java 本机接口（Java Native Interface (JNI)）是一个本机编程接口，它是 Java 软件开发工具箱（Java Software Development Kit (SDK)）的一部分。JNI 允许 Java 代码使用以其它语言（譬如 C 和 C++）编写的代码和代码库。Invocation API（JNI 的一部分）可以用来将 Java 虚拟机（JVM）嵌入到本机应用程序中，从而允许程序员从本机代码内部调用 Java 代码。
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  本教程涉及 JNI 最常见的两个应用：从 Java 程序调用 C/C++，以及从 C/C++ 程序调用 Java 代码。我们将讨论 Java 本机接口的这两个基本部分以及可能出现的一些更高级的编程难题。
</p>

<div class="ibm-alternate-rule" style="clear:both;background-image:url('http://www.ibm.com/i/solid.gif');height:1px;background-color:rgb(255,255,255);">
</div>

<p class="ibm-ind-link ibm-back-to-top" style="clear:both;font-size:.76em;font-family:arial, nsimsun, sans-serif;height:15px;text-align:right;margin:0;padding:5px;">
  <a class="ibm-anchor-up-link" style="background-position:0 -1px;display:inline;font-weight:bold;background-image:url('http://www.ibm.com/i/v16/icons/u_bold.gif');color:rgb(76,110,148);text-decoration:none;margin:0;padding:0 0 0 18px;" href="http://www.ibm.com/developerworks/cn/education/java/j-jni/index.html#ibm-pcon">回页首</a>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  <a name="N1012A"><span class="smalltitle" style="font-weight:bold;font-size:1.2em;">我应该学习本教程吗？</span></a>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  本教程将带您去了解使用 Java 本机接口的所有步骤。 您将学习如何从 Java 应用程序内部调用本机 C/C++ 代码以及如何从本机 C/C++ 应用程序内部调用 Java 代码。
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  所有示例都是使用 Java、C 和 C++ 代码编写的，并可以移植到 Windows 和基于 UNIX 的平台上。要完全理解这些示例，您必须有一些 Java 语言编程经验。此外，您还需要一些 C 或 C++ 编程经验。严格来说，JNI 解决方案可以分成 Java 编程任务和 C/C++ 编程任务，由不同的程序员完成每项任务。然而，要完全理解 JNI 是如何在两种编程环境中工作的，您必须能够理解 Java 和 C/C++ 代码。
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  我们还将讲述一些高级主题，包括本机方法的异常处理和多线程。要充分理解本教程，您应该熟悉 Java 平台的安全性模型，并有一些多线程应用程序开发的经验。
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  这里将关于<a style="color:rgb(76,110,148);" href="http://www.ibm.com/developerworks/cn/education/java/j-jni/section4.html">高级主题</a><span class="Apple-converted-space">&#160;</span>的节从较基本的循序渐进 JNI 简介中划分出来。现在，初级 Java 程序员可以先学习本教程的前两部分，掌握之后再开始学习高级主题。
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  请参阅<a style="color:rgb(76,110,148);" href="http://www.ibm.com/developerworks/cn/education/java/j-jni/resources.html">参考资料</a>，那里有关于本文所提到的教程、文章和其它一些参考书目的清单。
</p>

<div class="ibm-alternate-rule" style="clear:both;background-image:url('http://www.ibm.com/i/solid.gif');height:1px;background-color:rgb(255,255,255);">
</div>

<p class="ibm-ind-link ibm-back-to-top" style="clear:both;font-size:.76em;font-family:arial, nsimsun, sans-serif;height:15px;text-align:right;margin:0;padding:5px;">
  <a class="ibm-anchor-up-link" style="background-position:0 -1px;display:inline;font-weight:bold;background-image:url('http://www.ibm.com/i/v16/icons/u_bold.gif');color:rgb(76,110,148);text-decoration:none;margin:0;padding:0 0 0 18px;" href="http://www.ibm.com/developerworks/cn/education/java/j-jni/index.html#ibm-pcon">回页首</a>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  <a name="N10146"><span class="smalltitle" style="font-weight:bold;font-size:1.2em;">工具与组件</span></a>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  要运行本教程中的示例，您需要下列工具与组件：
</p>

<ul style="padding-right:5px;margin-top:0;font-size:.76em;margin-bottom:0;padding-bottom:5px;padding-top:0;">
  <li style="padding-right:5px;margin-top:0;margin-bottom:0;padding-bottom:3px;padding-top:0;font-family:arial, nsimsun, sans-serif;">
    <strong>Java 编译器</strong>：随 SDK 一起提供的<span class="Apple-converted-space">&#160;</span><code style="font-size:small!important;font-family:monospace;">javac.exe</code>。
  </li>
  <li style="padding-right:5px;margin-top:0;margin-bottom:0;padding-bottom:3px;padding-top:0;font-family:arial, nsimsun, sans-serif;">
    <strong>Java 虚拟机（JVM）</strong>：随 SDK 一起提供的<span class="Apple-converted-space">&#160;</span><code style="font-size:small!important;font-family:monospace;">java.exe</code>。
  </li>
  <li style="padding-right:5px;margin-top:0;margin-bottom:0;padding-bottom:3px;padding-top:0;font-family:arial, nsimsun, sans-serif;">
    <strong>本机方法 C 文件生成器</strong>：随 SDK 一起提供的<span class="Apple-converted-space">&#160;</span><code style="font-size:small!important;font-family:monospace;">javah.exe</code>。
  </li>
  <li style="padding-right:5px;margin-top:0;margin-bottom:0;padding-bottom:3px;padding-top:0;font-family:arial, nsimsun, sans-serif;">
    定义 JNI 的<strong>库文件和本机头文件</strong>。jni.h C 头文件、jvm.lib 和 jvm.dll 或 jvm.so 文件，这些文件都是随 SDK 一起提供的。
  </li>
  <li style="padding-right:5px;margin-top:0;margin-bottom:0;padding-bottom:3px;padding-top:0;font-family:arial, nsimsun, sans-serif;">
    能够创建共享库的<span class="Apple-converted-space">&#160;</span><strong>C 和 C++ 编译器</strong>。最常见的两个 C 编译器是用于 Windows 的 Visual C++ 和用于基于 UNIX 系统的<span class="Apple-converted-space">&#160;</span><code style="font-size:small!important;font-family:monospace;">cc</code>。
  </li>
</ul>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  虽然您可以使用自己喜欢的任何开发环境，但我们将在本教程中使用示例是用随 SDK 一起提供的标准工具和组件编写的。请参阅<a style="color:rgb(76,110,148);" href="http://www.ibm.com/developerworks/cn/education/java/j-jni/resources.html">参考资料</a>来下载 SDK、完整的源文件以及对于完成本教程不可缺少的其它工具。本教程具体地解释了 Sun 的 JNI 实现，该实现被认为是 JNI 解决方案的标准。本教程中没有讨论其它 JNI 实现的详细信息。
</p>

<div class="ibm-alternate-rule" style="clear:both;background-image:url('http://www.ibm.com/i/solid.gif');height:1px;background-color:rgb(255,255,255);">
</div>

<p class="ibm-ind-link ibm-back-to-top" style="clear:both;font-size:.76em;font-family:arial, nsimsun, sans-serif;height:15px;text-align:right;margin:0;padding:5px;">
  <a class="ibm-anchor-up-link" style="background-position:0 -1px;display:inline;font-weight:bold;background-image:url('http://www.ibm.com/i/v16/icons/u_bold.gif');color:rgb(76,110,148);text-decoration:none;margin:0;padding:0 0 0 18px;" href="http://www.ibm.com/developerworks/cn/education/java/j-jni/index.html#ibm-pcon">回页首</a>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  <a name="N10196"><span class="smalltitle" style="font-weight:bold;font-size:1.2em;">其它注意事项</span></a>
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  在 Java 2 SDK 中，JVM 和运行时支持位于名为 jvm.dll（Windows）或 libjvm.so（UNIX）的共享库文件中。在 Java 1.1 JDK 中，JVM 和运行时支持位于名为 javai.dll（Windows）或 libjava.so（UNIX）的共享库文件中。版本 1.1 的共享库包含运行时以及类库的一些本机方法，但在版本 1.2 中已经不包含运行时，并且本机方法被放在 java.dll 和 libjava.so 中。对于以下 Java 代码，这一变化很重要：
</p>

<ul style="padding-right:5px;margin-top:0;font-size:.76em;margin-bottom:0;padding-bottom:5px;padding-top:0;">
  <li style="padding-right:5px;margin-top:0;margin-bottom:0;padding-bottom:3px;padding-top:0;font-family:arial, nsimsun, sans-serif;">
    代码是用非 JNI 本机方法编写的（因为使用了 JDK 1.0 中旧的本机方法接口）
  </li>
  <li style="padding-right:5px;margin-top:0;margin-bottom:0;padding-bottom:3px;padding-top:0;font-family:arial, nsimsun, sans-serif;">
    通过 JNI Invocation 接口使用了嵌入式 JVM
  </li>
</ul>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  在两种情况下，在您的本机库能与版本 1.2 一起使用之前，都必须重新链接它们。注：这个变化应该不影响 JNI 程序员实现本机方法 ― 只有通过 Invocation API调用 JVM 的 JNI 代码才会受到影响。
</p>

<p style="font-size:.76em;font-family:arial, nsimsun, sans-serif;margin:0;padding:.3em 5px .7em;">
  如果使用随 SDK/JDK 一起提供的 jni.h 文件，则头文件将使用 SDK/JDK 安装目录中的缺省 JVM（jvm.dll 或 libjvm.so）。支持 JNI 的 Java 平台的任何实现都会这么做，或允许您指定 JVM 共享库；然而，完成这方面操作的细节可能会因具体 Java 平台／JVM 实现而有所不同。实际上，许多 JVM 实现根本不支持 JNI。
</p>

<p>
  </span></span>
</p>

<p>
  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/12/04/java-c-c-%e6%b7%b7%e5%90%88%e7%bc%96%e7%a8%8b-%e7%94%a8jni%e8%bf%9b%e8%a1%8cjava%e7%bc%96%e7%a8%8b%e8%bd%ac/">Java C C++ 混合编程-用JNI进行Java编程[转]</a>
</p>