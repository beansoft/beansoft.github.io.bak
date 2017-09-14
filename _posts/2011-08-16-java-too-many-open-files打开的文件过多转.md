---
id: 2172
title: 'java Too many open files打开的文件过多[转]'
date: 2011-08-16T19:43:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2172
permalink: '/2011/08/16/java-too-many-open-files%e6%89%93%e5%bc%80%e7%9a%84%e6%96%87%e4%bb%b6%e8%bf%87%e5%a4%9a%e8%bd%ac/'
views:
  - "7338"
original_post_id:
  - "2172"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
---
来源: [http://www.tot.name/show/3/7/20070528072334.htm](http://www.tot.name/show/3/7/20070528072334.htm "http://www.tot.name/show/3/7/20070528072334.htm")

<table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
  <tr>
    <td style="VERTICAL-ALIGN: top">
      <span style="COLOR: #009900"><strong><span style="TEXT-DECORATION: underline">问题描述</span></strong></span> <br />以下两个堆栈跟踪指示同一个问题并报告相同的消息：<span>打开的文件过多</span>丅 </p> 
      
      <p>
        <span style="FONT-WEIGHT: bold">异常 1</span></td> </tr> </tbody> </table> 
        
        <table cellpadding="2" border="1" style="WIDTH: 615px" cellspacing="2">
          <tr>
            <td style="BACKGROUND-COLOR: rgb(204,204,204); VERTICAL-ALIGN: top">
              java.net.SocketException: Too many open files </p> 
              
              <div style="MARGIN-LEFT: 40px">
                at java.net.PlainSocketImpl.accept(Compiled Code) <br />at java.net.ServerSocket.implAccept(Compiled Code) <br />at java.net.ServerSocket.accept(Compiled Code) <br />at weblogic.t3.srvr.ListenThread.run(Compiled Code)
              </div>
            </td>
          </tr>
        </table>
        
        <p>
        </p>
        
        <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px; FONT-WEIGHT: bold" cellspacing="2">
          <tr>
            <td style="VERTICAL-ALIGN: top">
              异常 2
            </td>
          </tr>
        </table>
        
        <table cellpadding="2" border="1" style="WIDTH: 615px" cellspacing="2">
          <tr>
            <td style="BACKGROUND-COLOR: rgb(204,204,204); VERTICAL-ALIGN: top">
              java.io.IOException：打开的文件过多 </p> 
              
              <div style="MARGIN-LEFT: 40px">
                at java.lang.UNIXProcess.forkAndExec(Native Method) <br />at java.lang.UNIXProcess.(UNIXProcess.java:54) <br />at java.lang.UNIXProcess.forkAndExec(Native Method) <br />at java.lang.UNIXProcess.(UNIXProcess.java:54) <br />at java.lang.Runtime.execInternal(Native Method) <br />at java.lang.Runtime.exec(Runtime.java:551) <br />at java.lang.Runtime.exec(Runtime.java:477) <br />at java.lang.Runtime.exec(Runtime.java:443)
              </div>
              
              <div style="MARGIN-LEFT: 40px">
                &#8230;
              </div>
            </td>
          </tr>
        </table>
        
        <p>
        </p>
        
        <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
          <tr>
            <td style="VERTICAL-ALIGN: top">
              第一个异常在错误影响到基础 TCP 协议时抛出，而第二个异常则在错误影响到 I/O 操作时抛出。 <br />这两个异常都是由阻止服务器的类似问题所产生的，该问题可通过下面的研究方法来解决。
            </td>
          </tr>
        </table>
        
        <p>
        </p>
        
        <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
          <tr>
            <td style="VERTICAL-ALIGN: top">
              <span style="COLOR: #009900"><span style="TEXT-DECORATION: underline">故障排除</span></span> <br />请注意，并非下面所有任务都需要完成。有些问题仅通过执行几项任务就可以解决。 </p> 
              
              <p>
                <span style="COLOR: #009900"><span style="TEXT-DECORATION: underline"><strong><span style="FONT-FAMILY: times new roman; COLOR: rgb(0,0,0)"><span style="COLOR: #000000">快速链接：</span></span> <br /></strong></span></span>
              </p>
              
              <ul>
                <li>
                  <span style="TEXT-DECORATION: underline"><a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#Why_does_the_problem_occur"><span style="COLOR: #800080">为什么发生此问题？</span></a></span>
                </li>
                <li>
                  <span style="TEXT-DECORATION: underline"><a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#Monitoring_File_Descriptors"><span style="COLOR: #800080">监视文件描述符</span></a></span>
                </li>
                <li>
                  <span style="TEXT-DECORATION: underline"><a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#Checking_open_files"><span style="COLOR: #800080">检查打开的文件</span></a></span>
                </li>
                <li>
                  <span style="TEXT-DECORATION: underline"><a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#How_and_when_does_a_file_descriptor_get_released"><span style="COLOR: #800080">如何以及何时发布文件描述符？</span></a></span>
                </li>
                <li>
                  <span style="TEXT-DECORATION: underline"><a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#Known_WebLogic_Server_Issues"><span style="COLOR: #800080">已知的 WebLogic Server 问题</span></a></span>
                </li>
                <li>
                  <span style="TEXT-DECORATION: underline"><a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#File_Descriptors_and_Settings"><span style="COLOR: #800080">文件描述符和设置</span></a></span>
                </li>
              </ul>
            </td>
          </tr>
        </table>
        
        <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
          <tr>
            <td style="VERTICAL-ALIGN: top">
              <p>
                <span style="TEXT-DECORATION: underline"><strong>为什么发生此问题？</strong></span>
              </p>
              
              <p>
                这些异常指出操作系统 (OS) 资源问题和操作系统与 JVM 进程用完文件描述符的原因（请参阅 <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#What_is_a_File_Descriptor"><span style="COLOR: #800080">什么是文件描述符？</span></a> ）
              </p>
              
              <p>
                在几个并发用户连接到服务器之后通常会发生此问题。Java 打开许多文件，以便读取运行应用程序所必需的类。大量应用程序会使用许多文件描述符，这会导致缺乏新的文件描述符。同样，每个新的套接字都需要一个描述符。客户端和服务器通过 TCP 套接字进行通信。在与服务器建立连接时，每个浏览器的 http 请求都使用 TCP 套接字。
              </p>
              
              <p>
                一定要首先监视文件描述符并了解这些诊断方法如何告知您有关打开文件的状态和其它潜在问题。在针对操作系统逐步执行此故障排除部分之后，可能有必要增加文件描述符的数量（请参阅 <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#File_Descriptors_and_Settings"><span style="COLOR: #800080">文件描述符和设置</span></a> ）
              </p>
              
              <p>
                <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#TOP"><span style="COLOR: #800080">返回页首</span></a>
              </p>
              
              <p>
                <span style="COLOR: #009900"><span style="TEXT-DECORATION: underline"><strong><span style="COLOR: rgb(0,0,0)"><span style="COLOR: #000000">监视文件描述符</span></span></strong></span></span> <br /><span style="FONT-WEIGHT: bold"><br />解决方法指导原则</span> <br />下面是一般指导原则和考虑事项：
              </p>
              
              <ul>
                <li>
                  确定文件描述符的总数是否太少或者某些文件描述符是否未被正确释放。
                </li>
              </ul>
              
              <div style="MARGIN-LEFT: 40px">
                这可以通过以下方法来诊断：在不同的时期检查文件描述符的总数，确定此数量是有所减少还是一直增加。
              </div>
              
              <ul>
                <li>
                  如果此数量有所减少，则应当增加文件描述符的最大数量，以防止该问题再次发生（ <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#How_are_the_number_of_file_descriptors"><span style="COLOR: #800080">如何在不同平台上定义文件描述符的数量</span></a> ）。
                </li>
              </ul>
              
              <div style="MARGIN-LEFT: 40px">
                此变化可以和减少连接在断开之前保持 <span>TIME_WAIT</span> 状态的时间结合起来（ <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#How_and_when_does_a_file_descriptor_get_released"><span style="COLOR: #800080">如何以及何时发布文件描述符？</span></a> ）。在繁忙的服务器上，缺省值（240 秒）会延迟其它连接企图，从而将限制最大连接数量。
              </div>
              
              <ul>
                <li>
                  如果此数量一直增加，则应当确定某些描述符的处理时间是否过长（文件没有正确地关闭 &#8211; <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#How_and_when_does_a_file_descriptor_get_released"><span style="COLOR: #800080">如何以及何时发布文件描述符？</span></a> ）以及所创建的文件是否过多（例如，驱动程序库一直为每个新的 JDBC 连接加载文件）。
                </li>
              </ul>
              
              <ul>
                <li>
                  加载 jar 文件还可能减少所使用的文件描述符的数量。每个 jar 文件都使用一个描述符，即使每个单独加载的单一类都将使用一个描述符时也是如此。
                </li>
              </ul>
              
              <p>
                您可以使用下列指导原则来监视和诊断所有描述符如何由一个进程使用（这取决于您的操作系统）：
              </p>
              
              <p>
                <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#TOP"><span style="COLOR: #800080">返回页首</span></a>
              </p>
              
              <p>
                <span style="COLOR: #009900"><span style="TEXT-DECORATION: underline">检查打开的文件</span></span> <br style="COLOR: rgb(0,0,0)" /> <span style="COLOR: rgb(0,0,0); FONT-WEIGHT: bold"><br />Unix 平台</span> <br />在诸多工具中，<span>lsof</span> (<strong>L</strong>i<strong>S</strong>t <strong>O</strong>pen <strong>F</strong>iles) Unix 管理工具（适用于 Solaris、Tru64、HP-UX、Linux 和 AIX）显示有关打开文件和网络文件描述符的信息，包括它们的类型、大小和 i-节点。
              </p>
              
              <p>
                对于特定的进程，其语法如下所示：
              </p>
              
              <div style="MARGIN-LEFT: 40px">
                <span>lsof -p <进程的 pid></span>
              </div>
              
              <h4 style="FONT-STYLE: italic">
                示例 1
              </h4>
              
              <p>
                以下命令在 Solaris 2.7 启动 WLS 8.1SP1 后立即执行。它表明运行服务器的 Java 进程 (pid 390) 分配了 84 个文件描述符，此数量远小于文件描述符缺省的硬极限。
              </p>
              
              <div style="MARGIN-LEFT: 40px">
                <span>$ lsof -p 390 | wc -l</span> <br /><strong>84</strong>
              </div>
              
              <p>
                在异常出现之后可以执行此命令，以确保此 Java 进程达到了打开文件的最大数量。这将确认该进程缺乏文件描述符。
              </p>
              
              <p>
                然后，您可以运行 <span>$ lsof -p <pid></span> 并将输出结果重定向到某个文件以检查打开的每个文件。如果某个应当关闭的文件却出现在列表中，您可以探查此文件以前没有按照预期方式关闭的原因。
              </p>
              
              <p>
                下面是 <span>lsof</span> 的输出结果片断：</td> </tr> </tbody> </table> 
                
                <p>
                </p>
                
                <table cellpadding="2" width="615" border="1" cellspacing="2" bgcolor="#CCCCCC">
                  <tr>
                    <td>
                      <strong>COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME</strong> <br />java 29733 usera cwd VDIR 176,22 4096 4300274 /home/usera/810/user_projects/mydomain <br />java 29733 usera txt VREG 176,22 36396 6642305 /home/usera/810/jdk141_02/bin/java <br />java 29733 usera txt VREG 176,22 1251192 10818087 /home/usera/810/user_projects/mydomain/myserver/.wlnotdelete/extract/myserver_uddi_uddi/ <br />jarfiles/_wl_cls_gen.jar <br />java 29733 usera txt VREG 176,22 511935 10074851 /home/usera/810/user_projects/mydomain/myserver/.wlnotdelete/extract/myserver_uddi_uddi/ <br />jarfiles/WEB-INF/lib/jsse39153.jar <br />java 29733 usera txt VREG 176,22 2305960 6000676 /home/usera/810/user_projects/mydomain/myserver/.internal/uddi.war <br />java 29733 usera txt VREG 176,22 1227013 1385413 /home/usera/810/weblogic81/common/eval/pointbase/lib/pbserver44.jar <br />java 29733 usera txt VREG 176,22 653661 69379 /home/usera/810/weblogic81/server/lib/ant/ <br />optional.jar
                    </td>
                  </tr>
                </table>
                
                <p>
                </p>
                
                <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
                  <tr>
                    <td style="VERTICAL-ALIGN: top">
                      <span>lsof .h</span> 显示所有可能的语法和选项。此程序的最新版本可在以下网址中找到： <a href="http://ftp.cerias.purdue.edu/pub/tools/unix/sysutils/lsof/"><span style="COLOR: #0000ff">http://ftp.cerias.purdue.edu/pub/tools/unix/sysutils/lsof/</span></a> 。 </p> 
                      
                      <p>
                        文件描述符将用于每个套接字连接，<span>lsof</span> 还可以显示套接字的类型（TCP 或 UDP）以及监听地址和端口（位于名称列中）。
                      </p>
                      
                      <p>
                        <span style="FONT-STYLE: italic; FONT-WEIGHT: bold">示例 2</span></td> </tr> </tbody> </table> 
                        
                        <p>
                        </p>
                        
                        <table cellpadding="2" border="1" style="WIDTH: 615px" cellspacing="2">
                          <tr>
                            <td style="BACKGROUND-COLOR: rgb(204,204,204); VERTICAL-ALIGN: top">
                              COMMAND PID USER FD TYPE DEVICE SIZE/OFF NODE NAME <br />in.telnet 29705 root 2u inet 0x30002808fd8 0t76 TCP aaaaabbbb:telnet->abcdef.bea.com:3886 <br />(ESTABLISHED)
                            </td>
                          </tr>
                        </table>
                        
                        <p>
                        </p>
                        
                        <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
                          <tr>
                            <td style="VERTICAL-ALIGN: top">
                              在 HP 上，您还可以使用性能监视工具 <span>Glance</span>（可从 <a href="http://www.hp.com/"><span style="COLOR: #0000ff">http://www.hp.com/</span></a> 获得）来分析在运行 WebLogic Server 时所打开文件的总数。 </p> 
                              
                              <p>
                                如果您没有 <span>lsof</span>，则还可以在 <span style="FONT-FAMILY: courier new">/proc/<pid>/fd</span> 中查看某个进程的所有文件描述符，每个文件描述符都驻留在此目录中。
                              </p>
                              
                              <p>
                                <span style="FONT-WEIGHT: bold">Windows 平台</span>
                              </p>
                              
                              <p>
                                <span style="FONT-STYLE: italic; FONT-WEIGHT: bold">Handle</span> <br />在 WinNT 或 Windows 2000 上，命令行工具 <span style="FONT-FAMILY: courier new">handle</span> 报告有关引用所打开文件的句柄的信息，如下例所示。此工具可用于特定进程， <br />它可从以下网址获得： <a href="http://www.sysinternals.com/ntw2k/freeware/handle.shtml"><span style="COLOR: #0000ff">http://www.sysinternals.com/ntw2k/freeware/handle.shtml</span></a> 。</td> </tr> </tbody> </table> 
                                
                                <p>
                                </p>
                                
                                <table cellpadding="2" border="1" style="WIDTH: 615px" cellspacing="2">
                                  <tr>
                                    <td style="BACKGROUND-COLOR: rgb(204,204,204); VERTICAL-ALIGN: top">
                                      C:\tmp>ps -ef | grep java <br />usera 1656 1428 0 10:11:41 CONIN$ 0:46 c:\Releases\WLS8.2\JDK141~1\bin\java -client -Xms32m -Xmx200m -XX:MaxPermSize=128m -Xverify:none -Dweblogic.Name=myserver -Dweblogic.ProductionModeEnabled= -Djava.security.policy=&#8221;c:\Releases\WLS8.2\WEBLOG~1\server\lib\weblogic.policy&#8221; weblogic.Server
                                    </td>
                                  </tr>
                                </table>
                                
                                <p>
                                </p>
                                
                                <table cellpadding="2" border="1" style="WIDTH: 615px" cellspacing="2">
                                  <tr>
                                    <td style="BACKGROUND-COLOR: rgb(204,204,204); VERTICAL-ALIGN: top">
                                      C:\tmp>handle -p java </p> 
                                      
                                      <p>
                                        Handle v2.10 <br />Copyright (C) 1997-2003 Mark Russinovich <br />Sysinternals &#8211; www.sysinternals.com
                                      </p>
                                      
                                      <p>
                                        &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212; <br />java.exe pid: 1656 ABCDEF\usera <br />18: File C:\Releases\WLS8.2\user_projects\domains\mydomain <br />170: File C:\Releases\WLS8.2\jdk141_05\jre\lib\rt.jar <br />178: File C:\Releases\WLS8.2\jdk141_05\jre\lib\sunrsasign.jar <br />180: File C:\Releases\WLS8.2\jdk141_05\jre\lib\jsse.jar <br />188: File C:\Releases\WLS8.2\jdk141_05\jre\lib\jce.jar <br />190: File C:\Releases\WLS8.2\jdk141_05\jre\lib\charsets.jar <br />328: File C:\Releases\WLS8.2\jdk141_05\jre\lib\ext\dnsns.jar <br />330: File C:\Releases\WLS8.2\jdk141_05\jre\lib\ext\ldapsec.jar <br />338: File C:\Releases\WLS8.2\jdk141_05\jre\lib\ext\localedata.jar <br />340: File C:\Releases\WLS8.2\jdk141_05\jre\lib\ext\sunjce_provider.jar <br />348: File C:\Releases\WLS8.2\jdk141_05\lib\tools.jar <br />350: File C:\Releases\WLS8.2\weblogic81\server\lib\weblogic.jar <br />358: File C:\Releases\WLS8.2\weblogic81\server\lib\jconn2.jar <br />360: File C:\Releases\WLS8.2\weblogic81\server\lib\ojdbc14.jar <br />368: File C:\Releases\WLS8.2\weblogic81\server\lib\xmlx.jar <br />370: File C:\Releases\WLS8.2\weblogic81\server\lib\webservices.jar <br />378: File C:\Releases\WLS8.2\weblogic81\server\lib\wlcipher.jar <br />3e0: File C:\Releases\WLS8.2\weblogic81\server\lib\ant\ant.jar <br />3e8: File C:\Releases\WLS8.2\weblogic81\server\lib\EccpressoJcae.jar <br />3f0: File C:\Releases\WLS8.2\weblogic81\server\lib\EccpressoCore.jar <br />3f8: File C:\Releases\WLS8.2\weblogic81\server\lib\EccpressoAsn1.jar <br />400: File C:\Releases\WLS8.2\weblogic81\server\lib\jConnect.jar <br />408: File C:\Releases\WLS8.2\weblogic81\server\lib\ant\optional.jar <br />410: File C:\Releases\WLS8.2\weblogic81\server\lib\ant\jakarta-oro-2.0.7.jar <br />…. <br />C:\tmp>handle -p java | wc -l <br />65</td> </tr> </tbody> </table> 
                                        
                                        <p>
                                        </p>
                                        
                                        <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
                                          <tr>
                                            <td style="VERTICAL-ALIGN: top">
                                              这表明在 Windows 上运行 WLS 8.1SP2 时使用了 65 个文件句柄。 </p> 
                                              
                                              <p>
                                                <span style="FONT-STYLE: italic; FONT-WEIGHT: bold">Process Explorer</span> <br /><span style="FONT-FAMILY: courier new">Process Explorer</span> 是另一个 Windows 工具，它是用来监视文件句柄的更高级实用程序。它具有 GUI 界面并显示有关正在运行的每个进程的更多信息。您可以使用此程序来搜索特殊句柄。 它可从以下网址获得： <a href="http://www.sysinternals.com/ntw2k/freeware/procexp.shtml"><span style="COLOR: #0000ff">http://www.sysinternals.com/ntw2k/freeware/procexp.shtml</span></a> 。 下面是示例输出的屏幕快照：</td> </tr> </tbody> </table> 
                                                
                                                <p>
                                                </p>
                                                
                                                <div style="TEXT-ALIGN: left" />
                                                
                                                <p>
                                                </p>
                                                
                                                <table cellpadding="2" width="615" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
                                                  <tr>
                                                    <td style="VERTICAL-ALIGN: top">
                                                      <p>
                                                        这表明运行 WLS 的 Java 进程使用 884 个句柄，但只有少数（65 个）句柄引用打开的文件。
                                                      </p>
                                                      
                                                      <p>
                                                        通过使用上述任一工具，您可以确定应当关闭的文件是否仍处于打开状态。接着，您应当按照下面说明的方式检查如何关闭文件以及如何释放它的文件描述符。
                                                      </p>
                                                      
                                                      <p>
                                                        <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#TOP"><span style="COLOR: #800080">返回页首</span></a>
                                                      </p>
                                                      
                                                      <p>
                                                        <span style="COLOR: #009900"><strong><span style="TEXT-DECORATION: underline">如何以及何时发布文件描述符？</span></strong></span> <br />文件描述符是在文件关闭或进程终止时被淘汰的。如果 <em>close()</em> 系统调用没有返回失败代码，则为将来要分配文件描述符的 <em>open()</em> 调用提供相关的文件描述符。当与某个打开文件的描述相关联的所有文件描述符已经关闭时，该打开文件的描述会被释放。
                                                      </p>
                                                      
                                                      <p>
                                                        您不应当依赖垃圾回收和对象终止功能来释放非 Java 资源（如文件描述符）。这就是为什么应当使用 <em>close()</em> 调用以及在出现错误时处理其输出结果的原因。
                                                      </p>
                                                      
                                                      <p>
                                                        已关闭的套接字传输到 <span style="FONT-FAMILY: courier new">TIME_WAIT</span> 以确保所有的数据在连接期间被传输，最终确认 (ACK) 应当终止数据传输，此状态会延迟释放分配给该套接字的文件描述符。在 Unix 系统上，此 <span style="FONT-FAMILY: courier new">TIME_WAIT</span> 期间的持续时间在名为 <span>tcp_time_wait _interval</span> 的内核参数中定义。在 Windows NT、Windows 2000 和 Windows XP 上，此期间在注册表中名为 <span>HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters</span> 的系统项中定义为 <span style="FONT-FAMILY: courier new">TcpTimedWaitDelay</span>。
                                                      </p>
                                                      
                                                      <p>
                                                        下面的 URL 提供关于 Unix 内核参数的详细说明： <a href="http://www.unixadm.net/networking/tune.html"><span style="COLOR: #0000ff">http://www.unixadm.net/networking/tune.html <br /></span></a>
                                                      </p>
                                                      
                                                      <p>
                                                        <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#TOP"><span style="COLOR: #800080">返回页首</span></a>
                                                      </p>
                                                      
                                                      <p>
                                                        <span style="COLOR: #009900"><span style="TEXT-DECORATION: underline"><strong>已知的 WebLogic Server 问题</strong></span></span> <br style="COLOR: rgb(0,0,0)" /> <span style="COLOR: #009900"><span style="TEXT-DECORATION: underline"><strong><br /></strong></span></span>增加文件描述符的数量通常将能够解决这种问题，但是您还将需要确保 WebLogic Server 作为一种应用程序不使用过多的文件，还要确保打开的文件能够正确关闭，以便释放文件描述符。
                                                      </p>
                                                      
                                                      <p>
                                                        报告给 BEA 客户支持部门的所有问题都与缺少文件描述符或者描述符表溢出有关。此问题总是在操作系统通知 Java 进程不能分配新文件描述符时发生。在这种情况下，您需要增加 fd 的数量。
                                                      </p>
                                                      
                                                      <p>
                                                        <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#TOP"><span style="COLOR: #800080">返回页首</span></a>
                                                      </p>
                                                      
                                                      <p>
                                                        <strong style="COLOR: rgb(0,0,0)"><span style="TEXT-DECORATION: underline">文件描述符和设置</span></strong> <br /><span style="FONT-WEIGHT: bold"><br /><a id="What_is_a_File_Descriptor" name="What_is_a_File_Descriptor">什么是文件描述符？</a></span> <br />文件描述符是由无符号整数表示的句柄，进程使用它来标识打开的文件。文件描述符与包括相关信息（如文件的打开模式、文件的位置类型、文件的初始类型等）的文件对象相关联，这些信息被称作文件的<em>上下文</em>。
                                                      </p>
                                                      
                                                      <p>
                                                        <span style="FONT-WEIGHT: bold">如何创建文件描述符？</span> <br />进程获取文件描述符最常见的方法是通过本机子例程 <em>open</em> 或 <em>create</em> 获取或者通过从父进程继承。后一种方法允许子进程同样能够访问由父进程使用的文件。文件描述符对于每个进程一般是唯一的。当用 <em>fork</em> 子例程创建某个子进程时，该子进程会获得其父进程所有文件描述符的副本，这些文件描述符在执行 <em>fork</em> 时打开。在由 <em>fcntl、dup</em> 和 <em>dup2</em> 子例程复制或拷贝某个进程时，会发生同样的复制过程。
                                                      </p>
                                                      
                                                      <p>
                                                        第二个异常在 JVM 进程缺乏文件描述符时出现（尽管在执行 <em>forkAndExec()</em> 子例程时丆需要新的文件描述符来复制父进程的文件描述符）。对于每个进程，操作系统内核在 <em>u_block</em> 结构中维护文件描述符表，所有的文件描述符都在该表中建立索引。
                                                      </p>
                                                      
                                                      <p>
                                                        <a id="How_are_the_number_of_file_descriptors" name="How_are_the_number_of_file_descriptors"><strong><span style="COLOR: #003300">如何在不同平台上定义文件描述符的数量</span></strong></a> <br />文件描述符极限以及可分配给进程的最大大小由资源限制来定义。这些值应当按照在 WebLogic Server 文档中建议的、特定于操作系统的文件描述符值来设置：
                                                      </p>
                                                      
                                                      <p>
                                                        对于 WLS 8.1： <a href="http://e-docs.bea.com/wls/docs81/perform/HWTuning.html#1119561"><span style="COLOR: #0000ff">调整硬件、操作系统和网络性能</span></a> <br />对于 WLS 7.0： <a href="http://e-docs.bea.com/wls/docs70/perform/HWTuning.html#1104200"><span style="COLOR: #0000ff">调整硬件、操作系统和网络性能</span></a> <br />对于 WLS 6.1： <a href="http://e-docs.bea.com/wls/docs61/perform/HWTuning.html"><span style="COLOR: #0000ff">调整硬件、操作系统和网络性能</span></a>
                                                      </p>
                                                      
                                                      <p>
                                                        Unix 和 Linux 都有文件描述符。 不过，二者的主要区别在于如何设置文件描述符的硬极限值、缺省值和配置过程。
                                                      </p>
                                                      
                                                      <p>
                                                        <span style="FONT-WEIGHT: bold"><span style="FONT-STYLE: italic">Solaris</span></span> <br /><span>/usr/bin/ulimit</span> 实用程序定义允许单个进程使用的文件描述符的数量。它的最大值在 <span style="FONT-FAMILY: courier new">rlim_fd_max</span> 中定义，在缺省情况下，它设置为 65,536。只有 root 用户才能修改这些内核值。 <br /><span style="FONT-WEIGHT: bold"><br /><span style="FONT-STYLE: italic">Linux</span></span> <br />管理用户可以在 etc/security/limits.conf 配置文件中设置他们的文件描述符极限，如下例所示。
                                                      </p>
                                                      
                                                      <div style="MARGIN-LEFT: 40px">
                                                        <span style="FONT-FAMILY: courier new">soft nofile 1024</span> <br style="FONT-FAMILY: courier new" /> <span style="FONT-FAMILY: courier new">hard nofile 4096</span>
                                                      </div>
                                                      
                                                      <p>
                                                        系统级文件描述符极限还可以通过将以下三行添加到 <span>/etc/rc.d/rc.local</span> 启动脚本中来设置：
                                                      </p>
                                                      
                                                      <div style="MARGIN-LEFT: 40px">
                                                        <span># Increase system-wide file descriptor limit.</span> <br /><span>echo 4096 > /proc/sys/fs/file-max</span> <br /><span>echo 16384 > /proc/sys/fs/inode-max</span>
                                                      </div>
                                                      
                                                      <p>
                                                        <span style="FONT-WEIGHT: bold"><span style="FONT-STYLE: italic">Windows</span></span> <br />在 Windows 操作系统上，文件描述符被称作文件句柄。在 Windows 2000 服务器上，打开文件的句柄极限设置为 16,384。此数量可以在任务管理器的性能摘要中监视。
                                                      </p>
                                                      
                                                      <p>
                                                        <span style="FONT-STYLE: italic; FONT-WEIGHT: bold">HP-UX</span> <br /><span><span style="FONT-FAMILY: courier new">nfile</span></span> 定义打开文件的最大数量。此值通常由以下公式来确定：<em>((NPROC*2)+1000)</em>，其中 <em>NPROC</em> 通常为：<em>((MAXUSERS*5)+64)</em>。 如果 <span style="FONT-FAMILY: courier new">MAXUSERS</span> 等于 400，则经过计算得到此值为 5128。通常可以将此值设高一些。<span style="FONT-FAMILY: courier new">maxfiles</span> 是每个进程的软文件极限，<span>maxfiles_lim</span> 是每个进程的硬文件极限。
                                                      </p>
                                                      
                                                      <p>
                                                        <span style="FONT-STYLE: italic; FONT-WEIGHT: bold">AIX</span> <br />文件描述符极限在 <span style="FONT-FAMILY: courier new">/etc/security/limits</span> 文件中设置，它的缺省值是 2000。此极限可以通过 <span>ulimit</span> 命令或 setrlimit 子例程来更改。最大大小由 <span style="FONT-FAMILY: courier new">OPEN_MAX</span> <em>常数来定义。</em>
                                                      </p>
                                                      
                                                      <p>
                                                        <a href="http://www.bea.com.cn/support_pattern/Too_Many_Open_Files_Pattern.html#TOP"><span style="COLOR: #800080">返回页首</span></a>
                                                      </p>
                                                    </td>
                                                  </tr>
                                                </table>
                                                
                                                <table cellpadding="2" style="TEXT-ALIGN: left; WIDTH: 615px" cellspacing="2">
                                                  <tr>
                                                    <td style="VERTICAL-ALIGN: top">
                                                      <p>
                                                        <strong><span style="TEXT-DECORATION: underline">是否需要更多帮助？</span></strong>
                                                      </p>
                                                      
                                                      <p>
                                                        如果您已经理解这个模式，但仍需要其它帮助，您可以：
                                                      </p>
                                                      
                                                      <ol>
                                                        <li>
                                                          在 <a href="http://support.bea.com/"><span style="COLOR: #0000ff">http://support.bea.com</span></a> 上查询 AskBEA（例如，使用&#8221;<span style="FONT-SIZE: 12pt">too many open files</span>&#8220;），以查找其它已发布的解决方案。
                                                        </li>
                                                        <li>
                                                          在 <a href="http://support.bea.com/"><span style="COLOR: #0000ff">http://support.bea.com</span></a> 上，向 BEA 的某个新闻组中提出更详细具体的问题。
                                                        </li>
                                                      </ol>
                                                      
                                                      <p>
                                                        如果这还不能解决您的问题，并且您拥有有效的技术支持合同，您可以通过登录以下网站来打开支持案例： <a href="http://support.bea.com/"><span style="COLOR: #0000ff">http://support.bea.com</span></a> 。
                                                      </p>
                                                    </td>
                                                  </tr>
                                                </table>
                                                
                                                <p>
                                                </p>
                                                
                                                <table width="615" border="2">
                                                  <tr>
                                                    <td>
                                                      <p>
                                                        <strong>反馈</strong>
                                                      </p>
                                                      
                                                      <p>
                                                        请给我们提供您的意见，说明此支持诊断模式<strong>&#8220;打开的文件过多&#8221;</strong>一文是否有所帮助，您需要的<span style="COLOR: #000000">任何解释，以及对</span> <a href="mailto:support.ke@bea.com?subject=Patterns Feedback: Too Many Open Files&body="><span style="COLOR: #0000ff">支持诊断模式</span></a> 的新主题的任何要求。
                                                      </p>
                                                    </td>
                                                  </tr>
                                                </table>
                                                
                                                <p>
                                                </p>
                                                
                                                <table width="615" border="2">
                                                  <tr>
                                                    <td height="78">
                                                      <p>
                                                        <strong>免责声明：</strong>
                                                      </p>
                                                      
                                                      <p>
                                                        依据 BEA 与您签署的维护和支持协议条款，BEA Systems, Inc. 在本网站上提供技术技巧和修补程序供您使用。虽然您可以将这些信息和代码与您获得 BEA 授权的软件一起使用，但 BEA 并不对所提供的技术技巧和修补程序做任何形式的担保，无论是明确的还是隐含的。
                                                      </p>
                                                      
                                                      <p>
                                                        本文档中引用的任何商标是其各自所有者的财产。有关完整的商标信息，请参考您的产品手册。
                                                      </p>
                                                    </td>
                                                  </tr>
                                                </table>
                                                
                                                <p>
                                                  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/08/16/java-too-many-open-files%e6%89%93%e5%bc%80%e7%9a%84%e6%96%87%e4%bb%b6%e8%bf%87%e5%a4%9a%e8%bd%ac/">java Too many open files打开的文件过多[转]</a>
                                                </p>