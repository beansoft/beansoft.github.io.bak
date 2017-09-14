---
id: 2187
title: 'IBM HeapAnalyzer下载[转]'
date: 2011-08-24T20:02:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2187
permalink: '/2011/08/24/ibm-heapanalyzer%e4%b8%8b%e8%bd%bd%e8%bd%ac/'
views:
  - "5929"
original_post_id:
  - "2187"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
---
来源: [http://www.alphaworks.ibm.com/tech/heapanalyzer](http://www.alphaworks.ibm.com/tech/heapanalyzer "http://www.alphaworks.ibm.com/tech/heapanalyzer")

下载地址: [http://www.alphaworks.ibm.com/tech/heapanalyzer/download](http://www.alphaworks.ibm.com/tech/heapanalyzer/download "http://www.alphaworks.ibm.com/tech/heapanalyzer/download")

HeapAnalyzer 

用来探测可能存在的Java堆泄漏的工具.

更新: 2011年4月19日   
版本4.1.4 增强了可疑的root泄漏检测.

&#160;

<div id="ibm-top">
  <div id="ibm-pcon">
    <div id="ibm-content">
      <div id="ibm-content-body">
        <div id="ibm-content-main">
          <div class="ibm-container ibm-graphic-tabs">
            <div class="ibm-container">
              <h2>
                What is HeapAnalyzer?
              </h2>
              
              <div class="ibm-container-body">
                </p> 
                
                <p>
                  HeapAnalyzer allows the finding of a possible Java™ heap leak area through its heuristic search engine and analysis of the Java heap dump in Java applications.
                </p>
                
                <p>
                  Java heap areas define objects, arrays, and classes. When the Garbage Collector allocates areas of storage in the heap, an object continues to be live while a reference to it exists somewhere in the active state of the JVM; therefore the object is reachable. When an object ceases to be referenced from the active state, it becomes garbage and can be reclaimed for reuse. When this reclamation occurs, the Garbage Collector must process a possible finalizer and also ensure that any internal JVM resources that are associated with the object are returned to the pool of such resources. Java heap dumps are snap shots of Java heaps at specific times.
                </p></p> 
                
                <h2>
                  How does it work?
                </h2></p> 
                
                <p>
                  HeapAnalyzer analyzes Java heap dumps by parsing the Java heap dump, creating directional graphs, transforming them into directional trees, and executing the heuristic search engine.
                </p>
                
                <p>
                  The following are examples of features:
                </p>
                
                <ul class="ibm-bullet-list ibm-no-links">
                  <li>
                    List of Java heap leak suspects
                  </li>
                  <li>
                    Recommendation of the size of kCluster
                  </li>
                  <li>
                    List of gaps among allocated objects/classes/arrays
                  </li>
                  <li>
                    Java objects/classes/arrays search engine
                  </li>
                  <li>
                    List of objects/classes/arrays by type name
                  </li>
                  <li>
                    List of objects/classes/arrays by object name
                  </li>
                  <li>
                    List of objects/classes/arrays by address
                  </li>
                  <li>
                    List of objects/classes/arrays by size
                  </li>
                  <li>
                    List of objects/classes/arrays by size of child
                  </li>
                  <li>
                    List of objects/classes/arrays by number of child
                  </li>
                  <li>
                    List of objects/classes/arrays by frequency
                  </li>
                  <li>
                    List of available heap spaces by size
                  </li>
                  <li>
                    Tree view of Java heap dump
                  </li>
                  <li>
                    Loading/saving processed Java heap dumps.
                  </li>
                </ul>
                
                <p>
                  For more information, please check out this Webcast replay:
                </p></p> 
                
                <ul class="ibm-bullet-list ibm-no-links">
                  <li>
                    <a href="http://www-1.ibm.com/support/docview.wss?uid=swg27006624" target="_new">Using HeapAnalyzer to diagnose Java heap issues</a>
                  </li>
                </ul>
                
                <p>
                  or these articles by Jinwoo Hwang in the Java Developer&#8217;s Journal:
                </p>
                
                <ul class="ibm-bullet-list ibm-no-links">
                  <li>
                    <a href="http://java.sys-con.com/node/995699" target="_new">"Anatomy of a Java Finalizer"</a>
                  </li>
                  <li>
                    <a href="http://java.sys-con.com/node/1229281" target="_new">"Unveiling the java.lang. OutOfMemoryError"</a>
                  </li>
                </ul></p>
              </div></p>
            </div>
            
            <div class="ibm-container">
              <h2>
                About the technology author(s)
              </h2>
              
              <div class="ibm-container-body">
                <div class="ibm-container-body">
                  <span class="ibm-inset-img-caption"><img height="90" alt="Jinwoo Hwang" hspace="10" src="http://www.alphaworks.ibm.com/g/g.nsf/img/developerpix/$file/tra-Hwang.jpg" width="64" align="left" vspace="5" border="0" /></span> </p> 
                  
                  <p>
                    Jinwoo Hwang is a software engineer, a team leader, and a technical leader within the WebSphere Application Server Technical Support team, which is based in Research Triangle Park, N.C. He joined IBM in 1995 and worked with IBM Global Learning Services, IBM Consulting Services, and development prior to his current position. Mr. Hwang is an IBM Certified Solution Developer as well as a SUN Certified Programmer for the Java 2 platform.
                  </p></p>
                </div></p>
              </div></p>
            </div></p>
          </div></p>
        </div></p>
      </div></p>
    </div></p>
  </div></p>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [IBM HeapAnalyzer下载[转]](http://www.beansoft.biz/2011/08/24/ibm-heapanalyzer%e4%b8%8b%e8%bd%bd%e8%bd%ac/)