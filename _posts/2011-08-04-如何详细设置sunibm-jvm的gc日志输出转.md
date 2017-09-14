---
id: 2143
title: 如何详细设置SUN/IBM JVM的GC日志输出(转)
date: 2011-08-04T20:01:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2143
permalink: '/2011/08/04/%e5%a6%82%e4%bd%95%e8%af%a6%e7%bb%86%e8%ae%be%e7%bd%aesunibm-jvm%e7%9a%84gc%e6%97%a5%e5%bf%97%e8%be%93%e5%87%ba%e8%bd%ac/'
views:
  - "6643"
original_post_id:
  - "2143"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
tags:
  - GC
---
原文: <http://www.tagtraum.com/gcviewer-vmflags.html>

   <span class="Apple-style-span" style="word-spacing:0;font:medium simsun;text-transform:none;color:rgb(0,0,0);text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"></p> 

<h1 style="margin-top:16px;margin-bottom:0;font:bold 15px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
  VMFlags
</h1>

<p style="font:12px/16px &#039;margin:8px 16px;">
  When it comes to garbage collector and memory flags VMs from different vendors differ somewhat. Most flags aren&#8217;t even properly documented by the usage printout of the VM themselves. This page tries to shine some light on what garbage collection related flags there are and what they are good for. It covers several<span class="Apple-converted-space">&#160;</span><a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun">Sun</a><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#ibm">IBM</a><span class="Apple-converted-space">&#160;</span>JVMs
</p>

<h2 style="margin-top:16px;margin-bottom:0;font:bold 13px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
  <a style="color:rgb(12,85,252);text-decoration:none;" name="sun">Sun JVMs</a>
</h2>

<p style="font:12px/16px &#039;margin:8px 16px;">
  Disclaimer: Please note that the data presented in this document has been gathered from several publicly available sources. It is a conscious selection of available VM parameters and even though we tried to check most of the facts presented this document may contain errors.
</p>

<h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
  Choosing a VM
</h3>

<dl>
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.server">-server</a>
  </dt>
  
  <dd>
    Instructs the VM to use the server HotSpot VM. This also implies that default heap sizes and permanent generation sizes are different.<span class="Apple-converted-space">&#160;</span> <br />Under 1.5 this option is the default option, if the machine is a<span class="Apple-converted-space">&#160;</span><a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.serverclass">server-class machine</a>.<span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.3, 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.client">-client</a>
  </dt>
  
  <dd>
    Instructs the VM to use the client HotSpot VM. This also implies that default heap sizes and permanent generation sizes are different.<span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.3, 1.4, 1.5
  </dd>
</dl>

<h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
  Printing Information about GC
</h3>

<dl>
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.verbose">-verbose:gc</a>
  </dt>
  
  <dd>
    Prints out information about garbage collections to standard out. To print the same information to a file, use<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.loggc">-Xloggc:&lt;file&gt;&lt;/a></code><span class="Apple-converted-space">&#160;</span> <br />Example: <br /><code>[GC 325407K-&gt;83000K(776768K), 0.2300771 secs]          &lt;br />[GC 325816K-&gt;83372K(776768K), 0.2454258 secs]           &lt;br />[Full GC 267628K-&gt;83769K(776768K), 1.8479984 secs]</code><span class="Apple-converted-space">&#160;</span> <br />See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.loggc">-Xloggc&lt;/a></code><span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.3, 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.loggc">-Xloggc:<file></a>
  </dt>
  
  <dd>
    Prints information about garbage collections to the specified file.<span class="Apple-converted-space">&#160;</span> <br />In conjunction with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.PrintGCDetails">-XX:+PrintGCDetails&lt;/a></code><span class="Apple-converted-space">&#160;</span>this is the best setting for the free<span class="Apple-converted-space">&#160;</span><a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer.html">GCViewer</a>.<span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.PrintGCDetails">-XX:+PrintGCDetails</a>
  </dt>
  
  <dd>
    Instructs the VM to be more verbose when printing out garbage collecion data. Specifically it does not only tell you that there was a collection, but also what impact it had on the different generations.<span class="Apple-converted-space">&#160;</span> <br />This flag is very useful when tuning generation sizes.<span class="Apple-converted-space">&#160;</span> <br />In conjunction with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.loggc">-Xloggc&lt;/a></code><span class="Apple-converted-space">&#160;</span>this is the best setting for the free<span class="Apple-converted-space">&#160;</span><a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer.html">GCViewer</a>.<span class="Apple-converted-space">&#160;</span> <br />Example:<span class="Apple-converted-space">&#160;</span> <br /><code>2.459: [GC 2.459: [DefNew: 3967K-&gt;0K(4032K), 0.0141600 secs] 8559K-&gt;7454K(16320K), 0.0143588 secs]</code><span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.PrintGCApplicationStoppedTime">-XX:+PrintGCApplicationStoppedTime</a>
  </dt>
  
  <dd>
    Instructs the VM to print out the length of actual collection pauses.<span class="Apple-converted-space">&#160;</span> <br />This flag is useful when tuning concurrent collectors.<span class="Apple-converted-space">&#160;</span> <br />Example:<span class="Apple-converted-space">&#160;</span> <br /><code>Tota&lt;br />
l time for which application threads were stopped: 0.0468229 seconds</code><span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.PrintGCApplicationConcurrentTime">-XX:+PrintGCApplicationConcurrentTime</a>
  </dt>
  
  <dd>
    Instructs the VM to print out the amount of time the applications runs between collection pauses. <br />This flag is useful when tuning concurrent collectors.<span class="Apple-converted-space">&#160;</span> <br />Example:<span class="Apple-converted-space">&#160;</span> <br /><code>Application time: 0.5291524 seconds</code><span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.PrintGCTimeStamps">-XX:+PrintGCTimeStamps</a>
  </dt>
  
  <dd>
    Ensures that timestamps relative to the start of the application are printed in the GC log.<span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.PrintTenuringDistribution">-XX:+PrintTenuringDistribution</a>
  </dt>
  
  <dd>
    Prints details about the tenuring distribution to standard out. It can be used to show this threshold and the ages of objects in the new generation. It is also useful for observing the lifetime distribution of an application.<span class="Apple-converted-space">&#160;</span> <br />Example:<span class="Apple-converted-space">&#160;</span> <br /><code>5.350: [GC Desired survivor size 32768 bytes, new threshold 1 (max 31)          &lt;br />- age 1: 57984 bytes, 57984 total           &lt;br />- age 2: 7552 bytes, 65536 total           &lt;br />756K-&gt;455K(1984K), 0.0097436 secs]</code><span class="Apple-converted-space">&#160;</span> <br />Supported by: 1.3, 1.4, 1.5
  </dd>
</dl>

<h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
  Sizing Heap and Generations
</h3>

<dl>
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.mx">-Xmx<value></a>
  </dt>
  
  <dd>
    Overall maximum heap size. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span> <br />Example:-Xmx256m sets the maximum heap size to 256mbSupported by: 1.3, 1.4, 1.5
  </dd>
  
  <dt>
    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.ms">-Xms<value></a>
  </dt>
  
  <dd>
    Minimum heap size. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span></p> 
    
    <p>
      Example:-Xms256m sets the minimum heap size to 256mbSupported by: 1.3, 1.4, 1.5</dd> 
      
      <dt>
        <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.mn">-Xmn<value></a>
      </dt>
      
      <dd>
        Sets the size of the young generation. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.</p> 
        
        <p>
          Example:-Xmn64m sets the young generation size to 64mbSupported by: 1.4, 1.5</dd> 
          
          <dt>
            <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.MinHeapFreeRatio">-XX:MinHeapFreeRatio=<minimumInPercent></a>
          </dt>
          
          <dd>
            Sets the minimal percentage of free heap memory that has to be available after a collection. This parameter can be used to influence when the VM is going to request more memory.<br /> <br />Example:-XX:MinHeapFreeRatio=70See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.MaxHeapFreeRatio">-XX:MaxHeapFreeRatio&lt;/a></code><span class="Apple-converted-space">&#160;</span></p> 
            
            <p>
              Supported by: 1.3, 1.4, 1.5</dd> 
              
              <dt>
                <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.MaxHeapFreeRatio">-XX:MaxHeapFreeRatio=<maximumInPercent></a>
              </dt>
              
              <dd>
                Sets the maximal percentage of free heap memory that must at most be available after a collection. This parameter can be used to influence when the VM is going to lower its footprint. In other words it can shrink the heap and therefore memory consumption.<br /> <br />Example:-XX:MaxHeapFreeRatio=20See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.MinHeapFreeRatio">-XX:MinHeapFreeRatio&lt;/a></code><span class="Apple-converted-space">&#160;</span></p> 
                
                <p>
                  Supported by: 1.3, 1.4, 1.5</dd> 
                  
                  <dt>
                    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.NewRatio">-XX:NewRatio=<ratio></a>
                  </dt>
                  
                  <dd>
                    Sets the ratio between young and old generation.<span class="Apple-converted-space">&#160;</span></p> 
                    
                    <p>
                      Example:-XX:NewRatio=3 means that the ratio between the young and old<br /> generation is 1:3; in other words, the combined size of<br /> eden and the survivor spaces will be one fourth of the<br /> heap.See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.NewSize">-XX:NewSize&lt;/a></code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.MaxNewSize">-XX:MaxNewSize&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                    </p>
                    
                    <p>
                      Supported by: 1.3, 1.4, 1.5</dd> 
                      
                      <dt>
                        <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.NewSize">-XX:NewSize=<value></a>
                      </dt>
                      
                      <dd>
                        Sets minimum size of the young generation.<span class="Apple-converted-space">&#160;</span></p> 
                        
                        <p>
                          Example:-XX:NewSize=64m sets the minimum size of the young<br /> generation to 64mbSee<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.NewRatio">-XX:NewRatio&lt;/a></code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.MaxNewSize">-XX:MaxNewSize&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                        </p>
                        
                        <p>
                          Supported by: 1.3, 1.4, 1.5</dd> 
                          
                          <dt>
                            <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.MaxNewSize">-XX:MaxNewSize=<value></a>
                          </dt>
                          
                          <dd>
                            Sets maximum size of the young generation.<span class="Apple-converted-space">&#160;</span></p> 
                            
                            <p>
                              Example:-XX:NewSize=64m sets the maximum size of the young<br /> generation to 64mbSee<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.NewRatio">-XX:NewRatio&lt;/a></code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.NewSize">-XX:NewSize&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                            </p>
                            
                            <p>
                              Supported by: 1.3, 1.4, 1.5</dd> 
                              
                              <dt>
                                <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.SurvivorRatio">-XX:SurvivorRatio=<ratio></a>
                              </dt>
                              
                              <dd>
                                Sets size of the survivor spaces in relation to eden.<span class="Apple-converted-space">&#160;</span></p> 
                                
                                <p>
                                  Example:-XX:SurvivorRatio=6 sets the ratio between each survivor space<br /> and eden to be 1:6; in other words, each survivor space<br /> will be one eighth of the young generation (not one seventh,<br /> because there are two survivor spaces).Supported by: 1.3, 1.4, 1.5</dd> 
                                  
                                  <dt>
                                    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.PermSize">-XX:PermSize=<value></a>
                                  </dt>
                                  
                                  <dd>
                                    Sets the initial size of the permanent generation (where classes etc. are stored). This can be useful for application servers using many EJBs and JSPs.<span class="Apple-converted-space">&#160;</span></p> 
                                    
                                    <p>
                                      Example:-XX:PermSize=64mSee<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.MaxPermSize">-XX:MaxPermSize&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                                    </p>
                                    
                                    <p>
                                      Supported by: 1.3, 1.4, 1.5</dd> 
                                      
                                      <dt>
                                        <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.MaxPermSize">-XX:MaxPermSize=<value></a>
                                      </dt>
                                      
                                      <dd>
                                        Sets the maximum size of the permanent generation (where classes etc. are stored). This can be useful for application servers using many EJBs and JSPs.<span class="Apple-converted-space">&#160;</span></p> 
                                        
                                        <p>
                                          Example:-XX:MaxPermSize=64mSee<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.PermSize">-XX:PermSize&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                                        </p>
                                        
                                        <p>
                                          Supported by: 1.3, 1.4, 1.5</dd> </dl> 
                                          
                                          <h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                            Choosing and Configuring a Collector
                                          </h3>
                                          
                                          <dl>
                                            <dt>
                                              <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.UseParallelGC">-XX:+UseParallelGC</a>
                                            </dt>
                                            
                                            <dd>
                                              Use parallel garbage collection. This collector is also referred to as the<span class="Apple-converted-space">&#160;</span><em>throughput</em><span class="Apple-converted-space">&#160;</span>collector. It uses a parallel version of the young generation collector. The old (tenured) generation is still cleaned with the default collector.<span class="Apple-converted-space">&#160;</span></p> 
                                              
                                              <p>
                                                Under 1.5 this option is the default option, if the machine is a<span class="Apple-converted-space">&#160;</span><a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.serverclass">server-class machine</a>.<span class="Apple-converted-space">&#160;</span>
                                              </p>
                                              
                                              <p>
                                                This option can not be used in conjunction with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseConcMarkSweepGC">-XX:+UseConcMarkSweepGC&lt;/a></code>.<span class="Apple-converted-space">&#160;</span>
                                              </p>
                                              
                                              <p>
                                                Supported by: 1.4.1, 1.5</dd> 
                                                
                                                <dt>
                                                  <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.UseParallelOldGC">-XX:+UseParallelOldGC</a>
                                                </dt>
                                                
                                                <dd>
                                                  Use the parallel old generation collector. Certain phases of an old generation collection can be performed in parallel, speeding up an old generation collection.<span class="Apple-converted-space">&#160;</span></p> 
                                                  
                                                  <p>
                                                    This option automatically enables<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParallelGC">-XX:+UseParallelGC&lt;/a></code>.<span class="Apple-converted-space">&#160;</span>
                                                  </p>
                                                  
                                                  <p>
                                                    Supported by: 1.5.0.6</dd> 
                                                    
                                                    <dt>
                                                      <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.ParallelGCThreads">-XX:ParallelGCThreads=<number></a>
                                                    </dt>
                                                    
                                                    <dd>
                                                      Specifies the number of threads used in parallel garbage collection when<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParallelGC">-XX:+UseParallelGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>is set. By default a system with N CPUs uses N garbage collection threads.<span class="Apple-converted-space">&#160;</span></p> 
                                                      
                                                      <p>
                                                        Example:-XX:ParallelGCThreads=4Supported by: 1.4.1, 1.5</dd> 
                                                        
                                                        <dt>
                                                          <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.MaxGCPauseMillis">-XX:MaxGCPauseMillis=<ms></a>
                                                        </dt>
                                                        
                                                        <dd>
                                                          Instructs the VM to try to keep garbage collection pauses shorter than the specified value in ms.<span class="Apple-converted-space">&#160;</span></p> 
                                                          
                                                          <p>
                                                            This option applies in conjunction with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParallelGC">-XX:+UseParallelGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>and has higher priority than<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.GCTimeRatio">-XX:GCTimeRatio&lt;/a></code>.<span class="Apple-converted-space">&#160;</span>
                                                          </p>
                                                          
                                                          <p>
                                                            Example:-XX:MaxGCPauseMillis=10Supported by: 1.5</dd> 
                                                            
                                                            <dt>
                                                              <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.GCTimeRatio">-XX:GCTimeRatio=<ratio></a>
                                                            </dt>
                                                            
                                                            <dd>
                                                              Sets a throughput goal for the VM. The ratio of garbage collection time to application time is<code>1/(1+&lt;ratio&gt;)</code>.<span class="Apple-converted-space">&#160;</span></p> 
                                                              
                                                              <p>
                                                                This option applies in conjunction with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParallelGC">-XX:+UseParallelGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>and has lower priority than<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.MaxGCPauseMillis">-XX:MaxGCPauseMillis&lt;/a></code>.<span class="Apple-converted-space">&#160;</span>
                                                              </p>
                                                              
                                                              <p>
                                                                Example:-XX:GCTimeRatio=19 sets a goal of 5% of the total time for<br /> garbage collection.Supported by: 1.5</dd> 
                                                                
                                                                <dt>
                                                                  <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.UseAdaptiveSizePolicy">-XX:+UseAdaptiveSizePolicy</a>
                                                                </dt>
                                                                
                                                                <dd>
                                                                  Instructs the VM to keep track of some statistics and resize both the young and the old (tenured) generation based on the collected data.<span class="Apple-converted-space">&#160;</span></p> 
                                                                  
                                                                  <p>
                                                                    This feature is on by default when the option<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParallelGC">-XX:+UseParallelGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>is used.<span class="Apple-converted-space">&#160;</span>
                                                                  </p>
                                                                  
                                                                  <p>
                                                                    Supported by: 1.4.1, 1.5</dd> 
                                                                    
                                                                    <dt>
                                                                      <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.AggressiveHeap">-XX:+AggressiveHeap</a>
                                                                    </dt>
                                                                    
                                                                    <dd>
                                                                      Instructs the JVM to push memory use to the limit. It inspects the machine resources (size of memory and number of processors) and attempts to set various parameters to be optimal for long-running, memory allocation-intensive jobs. This option is recommended for dedicated server machines.<span class="Apple-converted-space">&#160;</span></p> 
                                                                      
                                                                      <p>
                                                                        The physical memory on the machines must be at least 256MB before AggressiveHeap can be used.<span class="Apple-converted-space">&#160;</span>
                                                                      </p>
                                                                      
                                                                      <p>
                                                                        Beginning with JVM 1.3.1_02 some GC activity is done in parallel.<span class="Apple-converted-space">&#160;</span>
                                                                      </p>
                                                                      
                                                                      <p>
                                                                        Beginning with JVM 1.4 this option implies<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParallelGC">-XX:+UseParallelGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseAdaptiveSizePolicy">-XX:+UseAdaptiveSizePolicy&lt;/a></code>.<span class="Apple-converted-space">&#160;</span>
                                                                      </p>
                                                                      
                                                                      <p>
                                                                        Supported by: 1.3, 1.4, 1.5</dd> 
                                                                        
                                                                        <dt>
                                                                          <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.UseConcMarkSweepGC">-XX:+UseConcMarkSweepGC</a>
                                                                        </dt>
                                                                        
                                                                        <dd>
                                                                          Use concurrent garbage collection. This collector is also referred to as the<span class="Apple-converted-space">&#160;</span><em>concurrent</em><span class="Apple-converted-space">&#160;</span>low pause collector. It collects garbage in the old (tenured) generation concurrently to executing the application.<span class="Apple-converted-space">&#160;</span></p> 
                                                                          
                                                                          <p>
                                                                            Note that this option can not be used in conjunction with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParallelGC">-XX:+UseParallelGC&lt;/a></code>. Instead you may combine it with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParNewGC">-XX:+UseParNewGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                                                                          </p>
                                                                          
                                                                          <p>
                                                                            Supported by: 1.4.1, 1.5</dd> 
                                                                            
                                                                            <dt>
                                                                              <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.CMSParallelRemarkEnabled">-XX:+CMSParallelRemarkEnabled</a>
                                                                            </dt>
                                                                            
                                                                            <dd>
                                                                              If the<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseParNewGC">-XX:+UseParNewGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>option is in use the remark pauses may be decreased with the<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.CMSParallelRemarkEnabled">-XX:+CMSParallelRemarkEnabled&lt;/a>&lt;span class="Apple-converted-space">&#160;&lt;/span></code>option.<span class="Apple-converted-space">&#160;</span></p> 
                                                                              
                                                                              <p>
                                                                                Supported by: 1.4.1, 1.5</dd> 
                                                                                
                                                                                <dt>
                                                                                  <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.UseParNewGC">-XX:+UseParNewGC</a>
                                                                                </dt>
                                                                                
                                                                                <dd>
                                                                                  Instructs the VM to use a parallel collector for the young generation. This option should be used in conjunction with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseConcMarkSweepGC">-XX:+UseConcMarkSweepGC&lt;/a></code>.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                  
                                                                                  <p>
                                                                                    Supported by: 1.4.1, 1.5</dd> 
                                                                                    
                                                                                    <dt>
                                                                                      <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.UseTrainGC">-XX:+UseTrainGC</a>
                                                                                    </dt>
                                                                                    
                                                                                    <dd>
                                                                                      Activates the train garbage collector. Note that development for this collector has been stopped since 1.4.2.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                      
                                                                                      <p>
                                                                                        See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.incgc">-Xincgc&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                                                                                      </p>
                                                                                      
                                                                                      <p>
                                                                                        Supported by: 1.3, 1.4, 1.5</dd> 
                                                                                        
                                                                                        <dt>
                                                                                          <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.incgc">-Xincgc</a>
                                                                                        </dt>
                                                                                        
                                                                                        <dd>
                                                                                          Activates the incremental (also called train) garbage collector.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                          
                                                                                          <p>
                                                                                            See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.UseTrainGC">-XX:+UseTrainGC&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                                                                                          </p>
                                                                                          
                                                                                          <p>
                                                                                            Supported by: 1.3, 1.4, 1.5</dd> </dl> 
                                                                                            
                                                                                            <h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                                                                              Miscellaneous Settings
                                                                                            </h3>
                                                                                            
                                                                                            <dl>
                                                                                              <dt>
                                                                                                <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.ss">-Xss<value></a>
                                                                                              </dt>
                                                                                              
                                                                                              <dd>
                                                                                                Sets the size of the stack. In a server system with many threads lowering the stack size may be advantageous to reduce footprint. If the stack is too small, you will start seeing<code>StackOverflowError</code>s.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                
                                                                                                <p>
                                                                                                  You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span>
                                                                                                </p>
                                                                                                
                                                                                                <p>
                                                                                                  Example:-Xss128k sets the stack size to 128kbSupported by: 1.3, 1.4, 1.5</dd> 
                                                                                                  
                                                                                                  <dt>
                                                                                                    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.DisableExplicitGC">-XX:+DisableExplicitGC</a>
                                                                                                  </dt>
                                                                                                  
                                                                                                  <dd>
                                                                                                    Disables calls to<span class="Apple-converted-space">&#160;</span><code>java.lang.System.gc()</code>.
                                                                                                  </dd>
                                                                                                  
                                                                                                  <dt>
                                                                                                    <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.SoftRefLRUPolicyMSPerMB">-XX:SoftRefLRUPolicyMSPerMB=<ms per mb></a>
                                                                                                  </dt>
                                                                                                  
                                                                                                  <dd>
                                                                                                    Sets the rate at which the VM clears soft references. The rate is expressed in ms per free mb of heap. For the server VM free heap means<span class="Apple-converted-space">&#160;</span><em>potentially</em><span class="Apple-converted-space">&#160;</span>free heap using the maximum heap size as set with<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.mx">-Xmx&lt;/a></code><span class="Apple-converted-space">&#160;</span>in the calculation. For the client VM the free heap is calculated using the actual current heap size.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                    
                                                                                                    <p>
                                                                                                      Example:-XX:SoftRefLRUPolicyMSPerMB=1000 instructs the VM to allow<br /> softly reachable objects to remain alive for 1s per free mbSupported by: 1.3.1, 1.4, 1.5</dd> </dl> 
                                                                                                      
                                                                                                      <h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                                                                                        <a style="color:rgb(12,85,252);text-decoration:none;" name="sun.serverclass">Server-Class Machine</a>
                                                                                                      </h3>
                                                                                                      
                                                                                                      <p style="font:12px/16px &#039;margin:8px 16px;">
                                                                                                        Java 5.0 (1.5) defines a class of machines referred to as server-class machines. These are machines that have 2 or more physical processors and 2 or more gb of physical memory. On server-class machines the Sun JVM starts with altered default settings. These are:
                                                                                                      </p>
                                                                                                      
                                                                                                      <p style="font:12px/16px &#039;margin:8px 16px;">
                                                                                                        <code>-server -XX:+UseParallelGC</code>
                                                                                                      </p>
                                                                                                      
                                                                                                      <p style="font:12px/16px &#039;margin:8px 16px;">
                                                                                                        Additionally the initial heap size (<code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.ms">-Xms&lt;/a></code>) is set to 1/64 of the physical memory, up to 1gb. The maximum heap size (<code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#sun.mx">-Xmx&lt;/a></code>) is set to 1/4 of the physical memory, up to 1gb.
                                                                                                      </p>
                                                                                                      
                                                                                                      <p style="font:12px/16px &#039;margin:8px 16px;">
                                                                                                        Note that on server-class 32bit-Windows systems the VM will nevertheless start with the classic client settings, as most 32bit-Windows Java applications are not server applications.
                                                                                                      </p>
                                                                                                      
                                                                                                      <h2 style="margin-top:16px;margin-bottom:0;font:bold 13px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                                                                                        <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm">IBM JVMs</a>
                                                                                                      </h2>
                                                                                                      
                                                                                                      <p style="font:12px/16px &#039;margin:8px 16px;">
                                                                                                        Disclaimer: Please note that the data presented in this document has been gathered from several publicly available sources. It is a conscious selection of available VM parameters and even though we tried to check most of the facts presented this document may contain errors. Also note that the semantics of some of these parameters are different when used with IBM&#8217;s resettable JVM for the z/OS platform.
                                                                                                      </p>
                                                                                                      
                                                                                                      <h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                                                                                        Printing Information about GC
                                                                                                      </h3>
                                                                                                      
                                                                                                      <dl>
                                                                                                        <dt>
                                                                                                          <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.verbose">-verbose:gc</a>
                                                                                                        </dt>
                                                                                                        
                                                                                                        <dd>
                                                                                                          Prints out information about garbage collections to standard out.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                          
                                                                                                          <p>
                                                                                                            See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#ibm.verbosegclog">-Xverbosegclog&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                                                                                                          </p>
                                                                                                          
                                                                                                          <p>
                                                                                                            Supported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                            
                                                                                                            <dt>
                                                                                                              <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.verbosegclog">-Xverbosegclog:<path to file><filename[,X,Y]></a>
                                                                                                            </dt>
                                                                                                            
                                                                                                            <dd>
                                                                                                              Prints out information about garbage collections to a file. If the integers<span class="Apple-converted-space">&#160;</span><code>X</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>Y</code><span class="Apple-converted-space">&#160;</span>are specified, the output is redirected to<span class="Apple-converted-space">&#160;</span><code>X</code><span class="Apple-converted-space">&#160;</span>files each containing output from<span class="Apple-converted-space">&#160;</span><code>Y</code><span class="Apple-converted-space">&#160;</span>GC cycles.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                              
                                                                                                              <p>
                                                                                                                See<span class="Apple-converted-space">&#160;</span><code>&lt;a style="color:rgb(12,85,252);text-decoration:none;" href="http://www.tagtraum.com/gcviewer-vmflags.html#ibm.verbose">-verbose:gc&lt;/a></code><span class="Apple-converted-space">&#160;</span>
                                                                                                              </p>
                                                                                                              
                                                                                                              <p>
                                                                                                                Supported by: 1.4.1, 1.4.2</dd> </dl> 
                                                                                                                
                                                                                                                <h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                                                                                                  Sizing Heap and Generations
                                                                                                                </h3>
                                                                                                                
                                                                                                                <dl>
                                                                                                                  <dt>
                                                                                                                    <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.mx">-Xmx<value></a>
                                                                                                                  </dt>
                                                                                                                  
                                                                                                                  <dd>
                                                                                                                    Overall maximum heap size. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                    
                                                                                                                    <p>
                                                                                                                      Example:-Xmx256m sets the maximum heap size to 256mbSupported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                      
                                                                                                                      <dt>
                                                                                                                        <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.ms">-Xms<value></a>
                                                                                                                      </dt>
                                                                                                                      
                                                                                                                      <dd>
                                                                                                                        Overall minimum heap size. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                        
                                                                                                                        <p>
                                                                                                                          Example:-Xmx256m sets the minimum heap size to 256mbSupported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                          
                                                                                                                          <dt>
                                                                                                                            <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.initsh">-Xinitsh<value></a>
                                                                                                                          </dt>
                                                                                                                          
                                                                                                                          <dd>
                                                                                                                            Sets the initial size of the system heap. Classes in this heap exist for the lifetime of the JVM. The system heap is never subjected to garbage collection. The maximum size of the system heap is unbounded. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                            
                                                                                                                            <p>
                                                                                                                              Example:-Xinitsh256m sets the minimum system heap size to 256mbSupported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                              
                                                                                                                              <dt>
                                                                                                                                <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.maxf">-Xmaxf<value></a>
                                                                                                                              </dt>
                                                                                                                              
                                                                                                                              <dd>
                                                                                                                                This is a floating point number between 0 and 1, which specifies the maximum percentage of free space in the heap. The default is 0.6, or 60%. When this value is set to 0, heap contraction is a constant activity. With a value of 1, the heap never contracts. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                
                                                                                                                                <p>
                                                                                                                                  Example:-Xmaxf0.6 specifies that the heap will be contracted if more<br /> then 60% of the heap are unused.Supported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                                  
                                                                                                                                  <dt>
                                                                                                                                    <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.minf">-Xminf<value></a>
                                                                                                                                  </dt>
                                                                                                                                  
                                                                                                                                  <dd>
                                                                                                                                    This is a floating point number between 0 and 1, which specifies the minimum percentage of free space in the heap. The default is 0.3, or 30%. The heap grows if the free space is below the specified amount. You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                    
                                                                                                                                    <p>
                                                                                                                                      Example:-Xminf0.3 specifies that the heap will be grown if less<br /> then 30% of the heap are unused.Supported by: 1.3.1, 1.4.1, 1.4.2</dd> </dl> 
                                                                                                                                      
                                                                                                                                      <h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                                                                                                                        Choosing and Configuring a Collector
                                                                                                                                      </h3>
                                                                                                                                      
                                                                                                                                      <dl>
                                                                                                                                        <dt>
                                                                                                                                          <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.gcpolicy">-Xgcpolicy:<optthruput|optavgpause|subpool></a>
                                                                                                                                        </dt>
                                                                                                                                        
                                                                                                                                        <dd>
                                                                                                                                          Note that the<span class="Apple-converted-space">&#160;</span><code>subpool</code><span class="Apple-converted-space">&#160;</span>option was introduced in Version 1.4.1 Service Refresh 1 for AIX only.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                          
                                                                                                                                          <p>
                                                                                                                                            Setting gcpolicy to<span class="Apple-converted-space">&#160;</span><code>optthruput</code><span class="Apple-converted-space">&#160;</span>disables concurrent mark. If you do not have pause time problems (as seen by erratic application response times or by analysis of the verbose GC output), you should get the best throughput with this option.<span class="Apple-converted-space">&#160;</span><code>optthruput</code><span class="Apple-converted-space">&#160;</span>is the default setting.<span class="Apple-converted-space">&#160;</span>
                                                                                                                                          </p>
                                                                                                                                          
                                                                                                                                          <p>
                                                                                                                                            Setting gcpolicy to<span class="Apple-converted-space">&#160;</span><code>optavgpause</code><span class="Apple-converted-space">&#160;</span>enables concurrent mark with its default values. If you are having problems with erratic application response times that are caused by normal garbage collections, you can remove those problems at the cost of some throughput when running with the<code>optavgpause</code><span class="Apple-converted-space">&#160;</span>option.<span class="Apple-converted-space">&#160;</span>
                                                                                                                                          </p>
                                                                                                                                          
                                                                                                                                          <p>
                                                                                                                                            Setting gcpolicy to<span class="Apple-converted-space">&#160;</span><code>subpool</code><span class="Apple-converted-space">&#160;</span>enables improved object allocation that aims to achieve better performance in allocating objects on the heap. This setting might provide additional throughput optimization because it can improve the efficiency of object allocation and reduce lock contention on large SMP systems. Concurrent mark is disabled when this policy is enabled.<span class="Apple-converted-space">&#160;</span>
                                                                                                                                          </p>
                                                                                                                                          
                                                                                                                                          <p>
                                                                                                                                            Supported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                                            
                                                                                                                                            <dt>
                                                                                                                                              <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.gcthreads">-Xgcthreads<n></a>
                                                                                                                                            </dt>
                                                                                                                                            
                                                                                                                                            <dd>
                                                                                                                                              Sets the total number of threads that are used for garbage collection. On a system with n processors, the default setting is n.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                              
                                                                                                                                              <p>
                                                                                                                                                Supported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                                                
                                                                                                                                                <dt>
                                                                                                                                                  <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.compactgc">-Xcompactgc</a>
                                                                                                                                                </dt>
                                                                                                                                                
                                                                                                                                                <dd>
                                                                                                                                                  Compacts the heap<span class="Apple-converted-space">&#160;</span><em>every</em><span class="Apple-converted-space">&#160;</span>garbage collection cycle. The default is false (that is, the heap is not compacted). This is not recommended.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                  
                                                                                                                                                  <p>
                                                                                                                                                    Supported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                                                    
                                                                                                                                                    <dt>
                                                                                                                                                      <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.nocompactgc">-Xnocompactgc</a>
                                                                                                                                                    </dt>
                                                                                                                                                    
                                                                                                                                                    <dd>
                                                                                                                                                      <em>Never</em><span class="Apple-converted-space">&#160;</span>compact the heap. Default is false.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                      
                                                                                                                                                      <p>
                                                                                                                                                        Supported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                                                        
                                                                                                                                                        <dt>
                                                                                                                                                          <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.noclassgc">-Xnoclassgc</a>
                                                                                                                                                        </dt>
                                                                                                                                                        
                                                                                                                                                        <dd>
                                                                                                                                                          Disables class garbage collection.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                          
                                                                                                                                                          <p>
                                                                                                                                                            Supported by: 1.3.1, 1.4.1, 1.4.2</dd> </dl> 
                                                                                                                                                            
                                                                                                                                                            <h3 style="margin-top:16px;margin-bottom:0;font:bold 12px/16px &#039;margin-left:16px;color:rgb(12,85,252);">
                                                                                                                                                              Miscellaneous Settings
                                                                                                                                                            </h3>
                                                                                                                                                            
                                                                                                                                                            <dl>
                                                                                                                                                              <dt>
                                                                                                                                                                <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.ss">-Xss<value></a>
                                                                                                                                                              </dt>
                                                                                                                                                              
                                                                                                                                                              <dd>
                                                                                                                                                                Sets maximum native stack size for any thread.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                                
                                                                                                                                                                <p>
                                                                                                                                                                  You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span>
                                                                                                                                                                </p>
                                                                                                                                                                
                                                                                                                                                                <p>
                                                                                                                                                                  Example:-Xss128k sets the stack size to 128kbSupported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                                                                  
                                                                                                                                                                  <dt>
                                                                                                                                                                    <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.oss">-Xoss<value></a>
                                                                                                                                                                  </dt>
                                                                                                                                                                  
                                                                                                                                                                  <dd>
                                                                                                                                                                    Sets maximum Java stack size for any thread.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                                    
                                                                                                                                                                    <p>
                                                                                                                                                                      You may use<span class="Apple-converted-space">&#160;</span><code>k</code>,<span class="Apple-converted-space">&#160;</span><code>m</code><span class="Apple-converted-space">&#160;</span>and<span class="Apple-converted-space">&#160;</span><code>g</code><span class="Apple-converted-space">&#160;</span>for kilobyte, megabyte and gigabyte.<span class="Apple-converted-space">&#160;</span>
                                                                                                                                                                    </p>
                                                                                                                                                                    
                                                                                                                                                                    <p>
                                                                                                                                                                      Example:-Xoss128k sets the stack size to 128kbSupported by: 1.3.1, 1.4.1, 1.4.2</dd> 
                                                                                                                                                                      
                                                                                                                                                                      <dt>
                                                                                                                                                                        <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.compactexplicitgc">-Xcompactexplicitgc</a>
                                                                                                                                                                      </dt>
                                                                                                                                                                      
                                                                                                                                                                      <dd>
                                                                                                                                                                        Runs full compaction each time<span class="Apple-converted-space">&#160;</span><code>java.lang.System.gc()</code><span class="Apple-converted-space">&#160;</span>is called. Its default behavior with a<code>java.lang.System.gc()</code><span class="Apple-converted-space">&#160;</span>call is to perform a compaction only if an allocation failure triggered a garbage collection since the last<span class="Apple-converted-space">&#160;</span><code>java.lang.System.gc()</code><span class="Apple-converted-space">&#160;</span>call.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                                        
                                                                                                                                                                        <p>
                                                                                                                                                                          Supported by: 1.4.1, 1.4.2</dd> 
                                                                                                                                                                          
                                                                                                                                                                          <dt>
                                                                                                                                                                            <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.nocompactexplicitgc">-Xnocompactexplicitgc</a>
                                                                                                                                                                          </dt>
                                                                                                                                                                          
                                                                                                                                                                          <dd>
                                                                                                                                                                            Never runs compaction when<span class="Apple-converted-space">&#160;</span><code>java.lang.System.gc()</code><span class="Apple-converted-space">&#160;</span>is called. Its default behavior with a<code>java.lang.System.gc()</code><span class="Apple-converted-space">&#160;</span>call is to perform a compaction only if an allocation failure triggered a garbage collection since the last<span class="Apple-converted-space">&#160;</span><code>java.lang.System.gc()</code><span class="Apple-converted-space">&#160;</span>call.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                                            
                                                                                                                                                                            <p>
                                                                                                                                                                              Supported by: 1.4.1, 1.4.2</dd> 
                                                                                                                                                                              
                                                                                                                                                                              <dt>
                                                                                                                                                                                <a style="color:rgb(12,85,252);text-decoration:none;" name="ibm.disableexplicitgc">-Xdisableexplicitgc</a>
                                                                                                                                                                              </dt>
                                                                                                                                                                              
                                                                                                                                                                              <dd>
                                                                                                                                                                                Converts Java application calls to<span class="Apple-converted-space">&#160;</span><code>java.lang.System.gc()</code><span class="Apple-converted-space">&#160;</span>into no-ops.<span class="Apple-converted-space">&#160;</span></p> 
                                                                                                                                                                                
                                                                                                                                                                                <p>
                                                                                                                                                                                  Supported by: 1.4.1, 1.4.2</dd> </dl> 
                                                                                                                                                                                  
                                                                                                                                                                                  <p>
                                                                                                                                                                                    </span>
                                                                                                                                                                                  </p>
                                                                                                                                                                                  
                                                                                                                                                                                  <p>
                                                                                                                                                                                    转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/08/04/%e5%a6%82%e4%bd%95%e8%af%a6%e7%bb%86%e8%ae%be%e7%bd%aesunibm-jvm%e7%9a%84gc%e6%97%a5%e5%bf%97%e8%be%93%e5%87%ba%e8%bd%ac/">如何详细设置SUN/IBM JVM的GC日志输出(转)</a>
                                                                                                                                                                                  </p>