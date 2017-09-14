---
id: 2505
title: 如何抓取Thread Dump小结
date: 2011-11-28T21:39:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2505
permalink: '/2011/11/28/%e5%a6%82%e4%bd%95%e6%8a%93%e5%8f%96thread-dump%e5%b0%8f%e7%bb%93/'
views:
  - "12094"
original_post_id:
  - "2505"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - ThreadDump
  - WebLogic
---
<!--:zh-->

<p class="MsoNormal">
  <strong><span style="font-family: 宋体;">如何抓取</span><span lang="EN-US">Thread Dump</span></strong><strong><span style="font-family: 宋体;">小结</span> </strong>
</p>

&nbsp;

<p class="MsoNormal">
  <strong><span style="font-family: 宋体;">作者</span><span lang="EN-US">: 刘长炯 BeanSoft@126.com </span></strong><strong><span style="font-family: 宋体;">日期</span><span lang="EN-US">: 2011-11-28 </span></strong><strong><span style="font-family: 宋体;">本文环境</span><span lang="EN-US">: JDK 1.5/1.6, WebLogic 9.0 or later</span> </strong>
</p>

<p class="MsoNormal">
  <span style="font-family: 宋体;">当服务器挂起</span><span lang="EN-US">,</span><span style="font-family: 宋体;">崩溃或者性能底下时</span><span lang="EN-US">,</span><span style="font-family: 宋体;">就需要抓取服务器的线程堆栈</span><span lang="EN-US">(Thread Dump)</span><span style="font-family: 宋体;">用于后续的分析</span><span lang="EN-US">.</span>
</p>

<p class="MsoNormal">
  <span lang="EN-US">Thread dump</span><span style="font-family: 宋体;">提供了当前活动的线程的快照</span><span lang="EN-US">. </span><span style="font-family: 宋体;">它提供了</span><span lang="EN-US">JVM</span><span style="font-family: 宋体;">中所有</span><span lang="EN-US">Java</span><span style="font-family: 宋体;">线程的栈跟踪信息</span>
</p>

<p class="MsoNormal">
  <span style="font-family: 宋体;">有很多方式可用于获取</span><span lang="EN-US">Thread Dump, </span><span style="font-family: 宋体;">一些是操作系统特定的命令</span><span lang="EN-US">.</span>
</p>

<p class="MsoNormal">
  <p class="MsoNormal">
    <strong><span style="font-family: 宋体;">操作系统命令获取</span><span lang="EN-US">ThreadDump:</span> </strong>
  </p>
  
  <p>
    &nbsp;
  </p>
  
  <p class="MsoNormal">
    <p class="MsoNormal">
      <span lang="EN-US">Windows:</span>
    </p>
    
    <p class="MsoNormal">
      <span lang="EN-US">1.<span>      </span></span><span style="font-family: 宋体;">转向服务器的标准输出窗口并按下</span><span lang="EN-US">Control + Break</span><span style="font-family: 宋体;">组合键</span><span lang="EN-US">, </span><span style="font-family: 宋体;">之后需要将线程堆栈复制到文件中</span>
    </p>
    
    <p class="MsoNormal">
      <span lang="EN-US">UNIX/ Linux</span>
    </p>
    
    <p class="MsoNormal">
      <span style="font-family: 宋体;">首先查找到服务器的进程号</span><span lang="EN-US">(process id), </span><span style="font-family: 宋体;">然后获取堆栈</span><span lang="EN-US">.</span>
    </p>
    
    <p class="MsoNormal">
      <span lang="EN-US">1.<span>      </span>ps –ef<span>  </span>| grep java</span>
    </p>
    
    <p class="MsoNormal">
      <span lang="EN-US">2.<span>      </span>kill -3 </span>
    </p>
    
    <p class="MsoNormal">
      <span lang="EN-US"><span> </span></span><span style="font-family: 宋体;">注意一定要谨慎</span><span lang="EN-US">, </span><span style="font-family: 宋体;">一步不慎就可能让服务器进程被杀死</span><span lang="EN-US">! </span>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal">
      <strong><span lang="EN-US">JVM </span></strong><strong><span style="font-family: 宋体;">自带的工具获取线程堆栈</span><span lang="EN-US">:</span> </strong>
    </p>
    
    <p>
      &nbsp;
    </p>
    
    <p class="MsoNormal">
      <span lang="EN-US">JDK</span><span style="font-family: 宋体;">自带命令行工具获取</span><span lang="EN-US">PID</span><span style="font-family: 宋体;">并做</span><span lang="EN-US">ThreadDump:</span>
    </p>
    
    <p class="MsoListParagraph" style="margin-left: 21pt; text-indent: -21pt;">
      <span lang="EN-US"><span>1.<span style="font: 7pt;">         </span></span></span><span lang="EN-US">jps</span>
    </p>
    
    <p class="MsoListParagraph" style="margin-left: 21pt; text-indent: -21pt;">
      <span lang="EN-US"><span>2.<span style="font: 7pt;">         </span></span></span><span lang="EN-US">jstack </span>
    </p>
    
    <p class="MsoNormal">
      <span style="font-family: 宋体;">使用</span><span lang="EN-US">JVisualVM:</span>
    </p>
    
    <p class="MsoNormal">
      <span lang="EN-US">Threads </span><span style="font-family: 宋体;">标签页</span><span style="font-family: wingdings;" lang="EN-US"><span>à</span></span><span lang="EN-US">ThreadDump</span><span style="font-family: 宋体;">按钮</span><span lang="EN-US">.</span>
    </p>
    
    <p class="MsoNormal">
      <p class="MsoNormal">
        <strong><span lang="EN-US">WebLogic </span></strong><strong><span style="font-family: 宋体;">自带的获取</span><span lang="EN-US"> thread dump</span></strong><strong><span style="font-family: 宋体;">的工具</span><span lang="EN-US">:</span> </strong>
      </p>
      
      <p>
        &nbsp;
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">1. webLogic.Admin </span><span style="font-family: 宋体;">工具</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">a. </span><span style="font-family: 宋体;">打开命令提示符</span><span lang="EN-US">, </span><span style="font-family: 宋体;">通过运行</span><span lang="EN-US">/bin/setDomain.env</span><span style="font-family: 宋体;">设置相关类路径</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">b. </span><span style="font-family: 宋体;">执行下面的命令</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">java weblogic.Admin -url t3://localhost:7001 -username weblogic -password weblogic1 THREAD_DUMP</span>
      </p>
      
      <p class="MsoNormal">
        <span style="font-family: 宋体;">注意</span><span lang="EN-US">: Thread Dump </span><span style="font-family: 宋体;">会打印到标准输出</span><span lang="EN-US">, </span><span style="font-family: 宋体;">如</span><span lang="EN-US">nohup</span><span style="font-family: 宋体;">日志或者进程窗口</span><span lang="EN-US">.</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">2. </span><span style="font-family: 宋体;">使用</span><span lang="EN-US"> Admin Console</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">a. </span><span style="font-family: 宋体;">登录</span><span lang="EN-US"> Admin Console , </span><span style="font-family: 宋体;">点击对应的服务器</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">b. </span><span style="font-family: 宋体;">点击</span><span lang="EN-US">Server </span><span style="font-family: wingdings;" lang="EN-US"><span>à</span></span><span lang="EN-US"> Monitoring </span><span style="font-family: wingdings;" lang="EN-US"><span>à</span></span><span lang="EN-US">Threads</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">c. </span><span style="font-family: 宋体;">点击</span><span lang="EN-US">: Dump Thread Stack </span><span style="font-family: 宋体;">按钮</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">3. </span><span style="font-family: 宋体;">使用</span><span lang="EN-US">WLST (WebLogic Scripting Tool)</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">connect(‘weblogic’,&#8217;weblogic1’,’t3://localhost:7001’)</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">cd(‘Servers’)</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">cd(‘AdminServer’)</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">threadDump()</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">disconnect()</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span lang="EN-US">exit()</span>
      </p>
      
      <p class="MsoNormal" style="margin-left: 10.5pt;">
        <span style="font-family: 宋体;">注意</span><span lang="EN-US">: </span><span style="font-family: 宋体;">线程堆栈将会保存在运行</span><span lang="EN-US">wlst</span><span style="font-family: 宋体;">的当前目录下</span><span lang="EN-US">.</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US"><span> </span></span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">4. </span><span style="font-family: 宋体;">使用</span><span lang="EN-US">utils.ThreadDumper</span>
      </p>
      
      <p class="MsoNormal">
        <span style="font-family: 宋体;">用法</span><span lang="EN-US">:</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">C:\bea\wlserver_10.3\server\lib>java -cp weblogic.jar utils.ThreadDumper</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">Broadcast Thread dumps disabled: must specify weblogic.debug.dumpThreadAddr and</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">weblogic.debug.dumpThreadPort</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">Exception in thread &#8220;main&#8221; java.lang.IllegalArgumentException: Port out of range</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US">:-1</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US"><span>        </span>at java.net.DatagramPacket.setPort(Unknown Source)</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US"><span>        </span>at java.net.DatagramPacket.(Unknown Source)</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US"><span>        </span>at java.net.DatagramPacket.(Unknown Source)</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US"><span>        </span>at utils.ThreadDumper.sendDumpMsg(ThreadDumper.java:124)</span>
      </p>
      
      <p class="MsoNormal">
        <span lang="EN-US"><span>        </span>at utils.ThreadDumper.main(ThreadDumper.java:145)</span>
      </p>
      
      <p class="MsoNormal">
        <p class="MsoNormal">
          <span lang="EN-US">5. </span><span style="font-family: 宋体;">如果服务器是作为</span><span lang="EN-US">Windows</span><span style="font-family: 宋体;">服务的方式运行</span><span lang="EN-US">, </span><span style="font-family: 宋体;">请运行下列命令</span><span lang="EN-US">:</span>
        </p>
        
        <p class="MsoNormal">
          <span lang="EN-US">%WL_HOME%\bin\beasvc -dump -svcname:service-name</span>
        </p>
        
        <p class="MsoNormal">
          <p class="MsoNormal">
            <span style="font-family: 宋体;">其它一些获取</span><span lang="EN-US">Thread Dump</span><span style="font-family: 宋体;">的工具有</span><span lang="EN-US">jrcmd, jrmc(JRockit VM</span><span style="font-family: 宋体;">自带</span><span lang="EN-US">) ,Samurai, JProfiler</span><span style="font-family: 宋体;">等</span><span lang="EN-US">, </span><span style="font-family: 宋体;">还可通过</span><span lang="EN-US">JMX</span><span style="font-family: 宋体;">编程的方式获取</span><span lang="EN-US">, </span><span style="font-family: 宋体;">如</span><span lang="EN-US">JDK</span><span style="font-family: 宋体;">自带示例代码</span><span lang="EN-US">:</span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US">$JAVA_HOME\demo\management\FullThreadDump</span>
          </p>
          
          <p class="MsoNormal">
            <p class="MsoNormal">
              <p>
                <!--:-->
                
                <!--:en-->
              </p>
              
              <p class="MsoNormal">
                <b><span style="font-family:宋体;">如何抓取</span><span lang="EN-US">Thread Dump</span></b><b><span style="font-family:宋体;">小结</span><span lang="EN-US"></span> </p> 
                
                <p>
                  </b>
                </p>
                
                <p class="MsoNormal">
                  <b><span lang="EN-US"></span> </p> 
                  
                  <p>
                    </b>
                  </p>
                  
                  <p class="MsoNormal">
                    <b><span style="font-family:宋体;">作者</span><span lang="EN-US">: 刘长炯 BeanSoft@126.com </span></b><b><span style="font-family:宋体;">日期</span><span lang="EN-US">: 2011-11-28 </span></b><b><span style="font-family:宋体;">本文环境</span><span lang="EN-US">: JDK 1.5/1.6, WebLogic 9.0 or later</span> </p> 
                    
                    <p>
                      </b>
                    </p>
                    
                    <p class="MsoNormal">
                      <b><span lang="EN-US"></span> </p> 
                      
                      <p>
                        </b>
                      </p>
                      
                      <p class="MsoNormal">
                        <span style="font-family:宋体;">当服务器挂起</span><span lang="EN-US">,</span><span style="font-family:宋体;">崩溃或者性能底下时</span><span lang="EN-US">,</span><span style="font-family:宋体;">就需要抓取服务器的线程堆栈</span><span lang="EN-US">(Thread Dump)</span><span style="font-family:宋体;">用于后续的分析</span><span lang="EN-US">.</span>
                      </p></p> 
                      
                      <p class="MsoNormal">
                        <span lang="EN-US">Thread dump</span><span style="font-family:宋体;">提供了当前活动的线程的快照</span><span lang="EN-US">. </span><span style="font-family:宋体;">它提供了</span><span lang="EN-US">JVM</span><span style="font-family:宋体;">中所有</span><span lang="EN-US">Java</span><span style="font-family:宋体;">线程的栈跟踪信息</span><span lang="EN-US"></span>
                      </p></p> 
                      
                      <p class="MsoNormal">
                        <span style="font-family:宋体;">有很多方式可用于获取</span><span lang="EN-US">Thread Dump, </span><span style="font-family:宋体;">一些是操作系统特定的命令</span><span lang="EN-US">.</span>
                      </p></p> 
                      
                      <p class="MsoNormal">
                        <span lang="EN-US"></span>
                      </p></p> 
                      
                      <p class="MsoNormal">
                        <b><span style="font-family:宋体;">操作系统命令获取</span><span lang="EN-US">ThreadDump:</span> </p> 
                        
                        <p>
                          </b>
                        </p>
                        
                        <p class="MsoNormal">
                          <span lang="EN-US"></span>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <span lang="EN-US">Windows:</span>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <span lang="EN-US">1.<span>      </span></span><span style="font-family:宋体;">转向服务器的标准输出窗口并按下</span><span lang="EN-US">Control + Break</span><span style="font-family:宋体;">组合键</span><span lang="EN-US">, </span><span style="font-family:宋体;">之后需要将线程堆栈复制到文件中</span><span lang="EN-US"></span>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <span lang="EN-US">UNIX/ Linux</span>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <span style="font-family:宋体;">首先查找到服务器的进程号</span><span lang="EN-US">(process id), </span><span style="font-family:宋体;">然后获取堆栈</span><span lang="EN-US">.</span>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <span lang="EN-US">1.<span>      </span>ps –ef<span>  </span>| grep java</span>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <span lang="EN-US">2.<span>      </span>kill -3 <pid></span>
                        </p></p> 
                        
                        <p class="MsoNormal">
                          <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">注意一定要谨慎</span><span lang="EN-US">, </span><span style="font-family:宋体;">一步不慎就可能让服务器进程被杀死</span><span lang="EN-US">! </p> 
                          
                          <p>
                            </span>
                          </p></p> 
                          
                          <p class="MsoNormal">
                            <b><span lang="EN-US">JVM </span></b><b><span style="font-family:宋体;">自带的工具获取线程堆栈</span><span lang="EN-US">:</span> </p> 
                            
                            <p>
                              </b>
                            </p>
                            
                            <p class="MsoNormal">
                              <span lang="EN-US">JDK</span><span style="font-family:宋体;">自带命令行工具获取</span><span lang="EN-US">PID</span><span style="font-family:宋体;">并做</span><span lang="EN-US">ThreadDump:</span>
                            </p></p> 
                            
                            <p class="MsoListParagraph" style="margin-left:21pt;text-indent:-21pt;">
                              <span lang="EN-US"><span>1.<span style="font:7pt "">         </span></span></span><span lang="EN-US">jps</span>
                            </p></p> 
                            
                            <p class="MsoListParagraph" style="margin-left:21pt;text-indent:-21pt;">
                              <span lang="EN-US"><span>2.<span style="font:7pt "">         </span></span></span><span lang="EN-US">jstack <pid></span>
                            </p></p> 
                            
                            <p class="MsoNormal">
                              <span style="font-family:宋体;">使用</span><span lang="EN-US">JVisualVM:</span>
                            </p></p> 
                            
                            <p class="MsoNormal">
                              <span lang="EN-US">Threads </span><span style="font-family:宋体;">标签页</span><span lang="EN-US" style="font-family:wingdings;"><span>à</span></span><span lang="EN-US">ThreadDump</span><span style="font-family:宋体;">按钮</span><span lang="EN-US">.</span>
                            </p></p> 
                            
                            <p class="MsoNormal">
                              <span lang="EN-US"></span>
                            </p></p> 
                            
                            <p class="MsoNormal">
                              <b><span lang="EN-US">WebLogic </span></b><b><span style="font-family:宋体;">自带的获取</span><span lang="EN-US"> thread dump</span></b><b><span style="font-family:宋体;">的工具</span><span lang="EN-US">:</span> </p> 
                              
                              <p>
                                </b>
                              </p>
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">1. webLogic.Admin </span><span style="font-family:宋体;">工具</span><span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">a. </span><span style="font-family:宋体;">打开命令提示符</span><span lang="EN-US">, </span><span style="font-family:宋体;">通过运行</span><span lang="EN-US"><DOMAIN_HOME>/bin/setDomain.env</span><span style="font-family:宋体;">设置相关类路径</span><span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">b. </span><span style="font-family:宋体;">执行下面的命令</span><span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">java weblogic.Admin -url t3://localhost:7001 -username weblogic -password weblogic1 THREAD_DUMP</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span style="font-family:宋体;">注意</span><span lang="EN-US">: Thread Dump </span><span style="font-family:宋体;">会打印到标准输出</span><span lang="EN-US">, </span><span style="font-family:宋体;">如</span><span lang="EN-US">nohup</span><span style="font-family:宋体;">日志或者进程窗口</span><span lang="EN-US">.</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">2. </span><span style="font-family:宋体;">使用</span><span lang="EN-US"> Admin Console</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">a. </span><span style="font-family:宋体;">登录</span><span lang="EN-US"> Admin Console , </span><span style="font-family:宋体;">点击对应的服务器</span><span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">b. </span><span style="font-family:宋体;">点击</span><span lang="EN-US">Server </span><span lang="EN-US" style="font-family:wingdings;"><span>à</span></span><span lang="EN-US"> Monitoring </span><span lang="EN-US" style="font-family:wingdings;"><span>à</span></span><span lang="EN-US">Threads</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">c. </span><span style="font-family:宋体;">点击</span><span lang="EN-US">: Dump Thread Stack </span><span style="font-family:宋体;">按钮</span><span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">3. </span><span style="font-family:宋体;">使用</span><span lang="EN-US">WLST (WebLogic Scripting Tool)</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">connect(‘weblogic’,&#8217;weblogic1’,’t3://localhost:7001’)</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">cd(‘Servers’)</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">cd(‘AdminServer’)</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">threadDump()</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">disconnect()</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span lang="EN-US">exit()</span>
                              </p></p> 
                              
                              <p class="MsoNormal" style="margin-left:10.5pt;">
                                <span style="font-family:宋体;">注意</span><span lang="EN-US">: </span><span style="font-family:宋体;">线程堆栈将会保存在运行</span><span lang="EN-US">wlst</span><span style="font-family:宋体;">的当前目录下</span><span lang="EN-US">.</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"><span> </span></span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">4. </span><span style="font-family:宋体;">使用</span><span lang="EN-US">utils.ThreadDumper</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span style="font-family:宋体;">用法</span><span lang="EN-US">:</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">C:beawlserver_10.3serverlib>java -cp weblogic.jar utils.ThreadDumper</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">Broadcast Thread dumps disabled: must specify weblogic.debug.dumpThreadAddr and</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">weblogic.debug.dumpThreadPort</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">Exception in thread &#8220;main&#8221; java.lang.IllegalArgumentException: Port out of range</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">:-1</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"><span>        </span>at java.net.DatagramPacket.setPort(Unknown Source)</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"><span>        </span>at java.net.DatagramPacket.<init>(Unknown Source)</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"><span>        </span>at java.net.DatagramPacket.<init>(Unknown Source)</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"><span>        </span>at utils.ThreadDumper.sendDumpMsg(ThreadDumper.java:124)</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"><span>        </span>at utils.ThreadDumper.main(ThreadDumper.java:145)</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">5. </span><span style="font-family:宋体;">如果服务器是作为</span><span lang="EN-US">Windows</span><span style="font-family:宋体;">服务的方式运行</span><span lang="EN-US">, </span><span style="font-family:宋体;">请运行下列命令</span><span lang="EN-US">:</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">WL_HOMEbinbeasvc -dump -svcname:service-name</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span style="font-family:宋体;">其它一些获取</span><span lang="EN-US">Thread Dump</span><span style="font-family:宋体;">的工具有</span><span lang="EN-US">jrcmd, jrmc(JRockit VM</span><span style="font-family:宋体;">自带</span><span lang="EN-US">) ,Samurai, JProfiler</span><span style="font-family:宋体;">等</span><span lang="EN-US">, </span><span style="font-family:宋体;">还可通过</span><span lang="EN-US">JMX</span><span style="font-family:宋体;">编程的方式获取</span><span lang="EN-US">, </span><span style="font-family:宋体;">如</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">自带示例代码</span><span lang="EN-US">:</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US">$JAVA_HOMEdemomanagementFullThreadDump</span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"></span>
                              </p></p> 
                              
                              <p class="MsoNormal">
                                <span lang="EN-US"></span>
                              </p>
                              
                              <p>
                                <!--:-->
                              </p>
                              
                              <p>
                                转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/11/28/%e5%a6%82%e4%bd%95%e6%8a%93%e5%8f%96thread-dump%e5%b0%8f%e7%bb%93/">如何抓取Thread Dump小结</a>
                              </p>