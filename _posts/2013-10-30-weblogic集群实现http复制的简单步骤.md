---
id: 1431
title: WebLogic集群实现HTTP复制的简单步骤
date: 2013-10-30T20:01:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1431
permalink: '/2013/10/30/weblogic%e9%9b%86%e7%be%a4%e5%ae%9e%e7%8e%b0http%e5%a4%8d%e5%88%b6%e7%9a%84%e7%ae%80%e5%8d%95%e6%ad%a5%e9%aa%a4/'
views:
  - "23318"
original_post_id:
  - "1431"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Cluster
  - WebLogic
  - 会话
---
首先, 需要正确配置Web集群, 可参考文档:

##### [WebLogic Server 11g 集群配置单服务器版(Windows) 原创PDF](http://www.beansoft.biz/?p=67)&#160;

##### [WebLogic Server 9.2 集群配置单服务器版和多服务器版(PDF)](http://www.beansoft.biz/?p=413)

[Weblogic 11 集群和节点管理器配置快速入门视频(单服务器版)](http://www.beansoft.biz/?p=410)

然后, 要修改Web应用的weblogic.xml, 加入session复制的内容:

> <?xml version="1.0" encoding="UTF-8"?>
> 
> <weblogic-web-app xmlns="http://www.bea.com/ns/weblogic/90">   
> &#160; <session-descriptor>   
> &#160;&#160;&#160; <persistent-store-type>replicated</persistent-store-type>   
> &#160; </session-descriptor>   
> </weblogic-web-app>

注: 此处配置的是存放在内存中的会话复制.

最后, 切记session中的对象必须都是可序列化的.

参考文档: [http://download.oracle.com/docs/cd/E12840\_01/wls/docs103/webapp/weblogic\_xml.html#wp1071982](http://download.oracle.com/docs/cd/E12840_01/wls/docs103/webapp/weblogic_xml.html#wp1071982 "http://download.oracle.com/docs/cd/E12840_01/wls/docs103/webapp/weblogic_xml.html#wp1071982")

或: [http://edocs.weblogicfans.net/wls/docs92/webapp/weblogic_xml.html](http://edocs.weblogicfans.net/wls/docs92/webapp/weblogic_xml.html "http://edocs.weblogicfans.net/wls/docs92/webapp/weblogic_xml.html")

`persistent-store-type默认值:``memory`

将持久性存储方法设置为以下某个选项：

  * <del><a name="wp1061720"></a></del>`memory` &#8211; 禁用持久性会话存储。 
  * <del><a name="wp1061721"></a></del>`replicated` &#8211; 与 `memory` 相同，但会话数据将在群集服务器之间复制。 
  * <del><a name="wp1061722"></a></del>replicated\_if\_clustered – 如果 Web 应用程序部署于群集服务器上，则会复制生效的 `persistent-store-type`。否则，`memory` 为默认值。 
  * <del><a name="wp1061723"></a></del>sync-replication-across-cluster – 复制将在群集内同步发生。 
  * <del><a name="wp1061724"></a></del>async-replication-across-cluster – 复制将在群集内异步发生。 
  * <del><a name="wp1061725"></a></del>`file` &#8211; 使用基于文件的持久性（另请参阅 [persistent-store-dir](http://edocs.weblogicfans.net/wls/docs92/webapp/weblogic_xml.html#wp1061967)）。 
  * <del><a name="wp1061726"></a></del>`jdbc` &#8211; 使用数据库存储持久性会话。（另请参阅 [persistent-store-pool](http://edocs.weblogicfans.net/wls/docs92/webapp/weblogic_xml.html#wp1062057)。） 
  * <del><a name="wp1061727"></a></del>cookie – 所有会话数据都存储于用户浏览器的 cookie 中。 

&#160;

其它参考资料:weblogic 集群 HTTP 会话复制失败的解决方案

转载自: [http://hi.baidu.com/shenxiaolei_it/blog/item/1b7ce9c2f7c4cd30e5dd3bbc.html](http://hi.baidu.com/shenxiaolei_it/blog/item/1b7ce9c2f7c4cd30e5dd3bbc.html "http://hi.baidu.com/shenxiaolei_it/blog/item/1b7ce9c2f7c4cd30e5dd3bbc.html")

<center>
  </p> 
  
  <div style="width: 996px" id="main" align="left">
    <div class="stage">
      <div class="stagepad">
        <div style="width: 100%">
          <div style="overflow-x: hidden" id="m_blog" class="modbox">
            <div class="tit">
              weblogic 集群 HTTP 会话复制失败
            </div>
            
            <div class="date">
              2008年05月07日 星期三 10:38
            </div>
            
            <table style="width: 100%; table-layout: fixed">
              <tr>
                <td>
                  <div id="blog_text" class="cnt">
                    <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2" width="615">
                      <tr>
                        <td style="vertical-align: top">
                          <font style="color: rgb(0,0,0)" color="#009900"><strong><u>问题描述</u></strong></font> <br />Http 会话状态没有从 Primary 服务器复制到 Secondary 服务器。下面是一些故障症状： </p> 
                          
                          <ul>
                            <li>
                              使用 http 会话的应用程序没有按设计运行，并且会话数据有所丢失
                            </li>
                            <li>
                              即使在会话仍未超时的情况下，系统也可能提示您重新登录到应用程序中
                            </li>
                            <li>
                              您在服务器的日志文件中看到与 Http 会话失败相关的错误和警告
                            </li>
                            <li>
                              没有正确地将请求 Failover 到另一个服务器
                            </li>
                          </ul>
                        </td>
                      </tr>
                    </table>
                    
                    <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2" width="615">
                      <tr>
                        <td style="vertical-align: top" width="615">
                          <font style="color: rgb(0,0,0)" color="#009900"><strong><u>故障排除</u></strong></font> <br />请注意，并非下面所有任务都需要完成。有些问题仅通过执行几项任务就可以解决。 </p> 
                          
                          <p>
                            <font color="#009900"><span style="color: rgb(0,0,0); font-weight: bold">快速链接</span></font>
                          </p>
                          
                          <ul>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Why_does_the_problem_occur">为什么发生此问题？</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#What_are_the_types_of_Http_Session_Replication?">Http 会话复制有什么类型？</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#How_do_I_diagnose_the_issue_as_session_replication_failure?">当会话复制失败时如何诊断此问题？</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Enable_the_Debug_Flags_to_track_Session_Replication_Failures:">启用调试标志跟踪会话复制失败</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Checklist_for_each_Session_Persistence_type_used">所使用的每个会话持久性类型的检查清单</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Validate_the_Weblogic_entries">验证 Weblogic.xml 条目</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Session_Data_Must_Be_Serializable">会话数据必须可序列化</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Check_for_Network/Multicast_issues">检查网络/组播问题</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Validate_Cluster_Configuration">验证群集配置</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Application_Code_Diagnostics">应用程序代码诊断</a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Cookies_Vs_URL-Rewriting">Cookie 与 URL Rewriting </a></u></font>
                            </li>
                            <li>
                              <font color="#009900"><u><a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Performance_Issues">性能问题</a></u></font>
                            </li>
                          </ul>
                          
                          <p>
                            <font style="color: rgb(0,0,0); font-weight: bold" color="#009900"><span style="text-decoration: underline"><a name="Why_does_the_problem_occur">为什么发生此问题？</a></span></font> <br />会话复制失败通常是因为组播/网络问题引起的。有时候，配置问题也会导致失败（请查看“验证 <span>Weblogic.xml</span> 条目”一节）。此外，请确保输入到会话中的数据必须是可序列化的，否则复制可能会失败。使用下列检查清单检查配置或可能导致会话复制失败的其它潜在问题。
                          </p>
                          
                          <p>
                            <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                          </p>
                          
                          <p>
                            <span style="font-weight: bold; text-decoration: underline"><a name="What_are_the_types_of_Http_Session_Replication?">Http 会话复制有什么类型？</a></span> <br />有五种不同的会话持久性实现方式：
                          </p>
                          
                          <ol>
                            <li>
                              内存（单个服务器，不复制）
                            </li>
                          </ol>
                          
                          <blockquote>
                            <p>
                              当您使用基于内存的存储方式时，所有会话信息都存储在内存中，并且当您停止和重新启动 WebLogic Server 时，这些信息将会丢失。
                            </p>
                          </blockquote>
                          
                          <ol>
                            <li value="value">
                              文件系统持久性
                            </li>
                          </ol>
                          
                          <blockquote>
                            <p>
                              会话信息存储在指定的 <a href="http://e-docs.bea.com/wls/docs81/webapp/weblogic_xml.html#1038256">PersistentStoreDir</a> 中的一个文件中。
                            </p>
                          </blockquote>
                          
                          <ol>
                            <li value="value">
                              JDBC 持久性
                            </li>
                          </ol>
                          
                          <blockquote>
                            <p>
                              会话信息存储在数据库表中。
                            </p>
                          </blockquote>
                          
                          <ol>
                            <li value="value">
                              基于 cookie 的会话持久性
                            </li>
                          </ol>
                          
                          <blockquote>
                            <p>
                              会话信息存储在 cookie 中。
                            </p>
                          </blockquote>
                          
                          <ol>
                            <li value="value">
                              内存中复制（在群集内）
                            </li>
                          </ol>
                          
                          <blockquote>
                            <p>
                              会话数据从一个服务器实例复制到内存中的另一个实例。
                            </p>
                          </blockquote>
                          
                          <p>
                            <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                          </p>
                          
                          <p>
                            <span style="font-weight: bold; text-decoration: underline"><a name="How_do_I_diagnose_the_issue_as_session_replication_failure?">当会话复制失败时如何诊断此问题？</a> <br /></span>考虑一个群集中有两个服务器（MyServer-1，MyServer-2）的情况。当您启用调试标志后，如果从某个客户端发送了一个请求，您将会立即看到下面的消息（请参阅<a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#Enable_the_Debug_Flags_to_track_Session_Replication_Failures:">启用调试标志跟踪会话复制失败</a>）
                          </p>
                          
                          <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2">
                            <tr>
                              <td style="vertical-align: top">
                                在 MyServer-1 上：
                              </td>
                            </tr>
                          </table>
                          
                          <table style="width: 615px" border="1" cellspacing="2" cellpadding="2">
                            <tr>
                              <td style="background-color: rgb(204,204,204); vertical-align: top">
                                <font font="courier new"><Oct 9, 2003 12:38:21 PM PDT> <Debug> <Cluster> <000000> <Creating primary 5165892837402719733> </p> 
                                
                                <p>
                                  <Oct 9, 2003 12:38:21 PM PDT> <Debug> <Cluster> <000000> <Created secondary for 5165892837402719733 on -7957889153726652135S: 210.23.23.1: [9001,9001, -1, -1,9001, -1, -1]: mydomain: MyServer-2></font></td> </tr> </tbody> </table> 
                                  
                                  <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2">
                                    <tr>
                                      <td style="vertical-align: top" height="80">
                                        <p>
                                          上面的记录消息意味着 Primary 服务器是 MyServer-1，并且在 Myserver-2 上创建了一个 Secondary 服务器，而且您将看到在 MyServer-2 中记录了类似下面的确认消息。
                                        </p>
                                        
                                        <p>
                                          在 MyServer-2 上：
                                        </p>
                                      </td>
                                    </tr>
                                  </table>
                                  
                                  <table style="width: 615px" border="1" cellspacing="2" cellpadding="2">
                                    <tr>
                                      <td style="background-color: rgb(204,204,204); vertical-align: top">
                                        <font font="courier new">ExecuteThread: &#8216;1&#8217; for queue: &#8216;Replication&#8217;> <kernel identity> <> <000000> <Creating secondary 5165892837402719733> </p> 
                                        
                                        <p>
                                          ####<Oct 9, 2003 12:38:21 PM PDT> <Debug> <Cluster> <machine1-c840> <MyServer-2> <ExecuteThread: &#8216;1&#8217; for queue: &#8216;Replication&#8217;> <kernel identity> <> <000000> <Updated local secondary of 5165892837402719733> </font></td> </tr> </tbody> </table> 
                                          
                                          <p>
                                            如果您检查 JsessionId，其形式如下：
                                          </p>
                                          
                                          <p>
                                            &#160;&#160; JSESSIONID=1E9Xwn7nLYfOsc1obgRZIwW5s72an7HPPvSD7iaWHMXzpHga5cQj!-1587343083!-1587348922
                                          </p>
                                          
                                          <p>
                                            JSESSIONID 是缺省的 cookie 名称，可以在 weblogic.xml 中将其更改为任何内容。
                                          </p>
                                          
                                          <p>
                                            JSESSIONID 的格式为：
                                          </p>
                                          
                                          <p>
                                            &#160;&#160; SessionId!PrimaryServer JVM Hash!SecondaryServer JVMHash
                                          </p>
                                          
                                          <p>
                                            Every time data is changed (either set/get or removed) in the session you&#8217;ll see the logging message.
                                          </p>
                                          
                                          <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2">
                                            <tr>
                                              <td style="vertical-align: top">
                                                在 MyServer-1 上：
                                              </td>
                                            </tr>
                                          </table>
                                          
                                          <table style="width: 615px" border="1" cellspacing="2" cellpadding="2">
                                            <tr>
                                              <td style="background-color: rgb(204,204,204); vertical-align: top">
                                                <font font="courier new"><Oct 9, 2003 12:38:21 PM PDT> <Debug> <Cluster> <000000> <Updated remote secondary for 5165892837402719733></font>
                                              </td>
                                            </tr>
                                          </table>
                                          
                                          <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2">
                                            <tr>
                                              <td style="vertical-align: top">
                                                在 MyServer-2 上：
                                              </td>
                                            </tr>
                                          </table>
                                          
                                          <table style="width: 615px" border="1" cellspacing="2" cellpadding="2">
                                            <tr>
                                              <td style="background-color: rgb(204,204,204); vertical-align: top">
                                                <font font="courier new">####<Oct 9, 2003 12:38:21 PM PDT> <Debug> <Cluster> <machine1-c840> <MyServer-2> <ExecuteThread: &#8216;1&#8217; for queue: &#8216;Replication&#8217;> <kernel identity> <> <000000> <Updated local secondary of 5165892837402719733></font>
                                              </td>
                                            </tr>
                                          </table>
                                          
                                          <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2">
                                            <tr>
                                              <td style="vertical-align: top">
                                                <p>
                                                  如果因为任何原因而导致会话复制失败，您将在 MyServer-1 日志中看到下面的消息。
                                                </p>
                                              </td>
                                            </tr>
                                          </table>
                                          
                                          <table style="width: 615px" border="1" cellspacing="2" cellpadding="2">
                                            <tr>
                                              <td style="background-color: rgb(204,204,204); vertical-align: top">
                                                <font font="courier new"><Nov 6, 2003 12:59:12 PM EST> <Debug> <Cluster> <000000> <Unable to create secondary for -5165892837402719733> </p> 
                                                
                                                <p>
                                                  <Nov 6, 2003 12:59:12 PM EST> <Debug> <Cluster> <000000> <Error creating secondary 5165892837402719733 on -7957889153726652135S: 210.23.23.1:[9001,9001,-1,-1,9001,-1,-1]:mydomain:MyServer-2></font></td> </tr> </tbody> </table> 
                                                  
                                                  <p>
                                                    上面的消息意味着会话复制已失败。
                                                  </p>
                                                  
                                                  <p>
                                                    JSESSIONID 也会显示为如下形式：
                                                  </p>
                                                  
                                                  <p>
                                                    &#160;&#160; JSESSIONID=1E9Xwn7nLYfOsc1obgRZIwW5s72an7HPPvSD7iaWHMXzpHga5cQj!-1587343083!NONE
                                                  </p>
                                                  
                                                  <p>
                                                    Secondary 服务器散列信息将变为 NONE。
                                                  </p>
                                                  
                                                  <p>
                                                    <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                  </p>
                                                  
                                                  <p>
                                                    <span style="font-weight: bold; text-decoration: underline"><a name="Enable_the_Debug_Flags_to_track_Session_Replication_Failures:">启用调试标志跟踪会话复制失败：</a></span> <br />您可以启用 DebugCluster、DebugClusterAnnouncements、DebugFailOver、DebugReplication、DebugReplicationDetails 标志。&#160;
                                                  </p>
                                                  
                                                  <p>
                                                    若要启用：
                                                  </p>
                                                  
                                                  <ol>
                                                    <li>
                                                      可以使用 weblogic.Admin 命令行实用程序来动态地启用或关闭调试选项。 <br />例如，若要在 ServerDebug Mbean 的所有管理实例（即管理服务器或托管服务器）上启用 DebugCluster： <p>
                                                        java weblogic.Admin -url t3://localhost:6151 -username system -password weblogic SET -type ServerDebug -property DebugCluster true </li> </ol> 
                                                        
                                                        <ol>
                                                          <li>
                                                            另外，对于要调试的每个服务器，可以编辑 <ServerDebug/> 节中的 config.xml 和 Mbean 要素，将值设置为“true”表示启用，或设置为“false”表示禁用。然后必须重新启动管理服务器。托管服务器将重新连接到管理服务器，然后调试标志将动态生效。示例： <p>
                                                              <ServerDebug DebugCluster="true" Name="myserver"/> </li> </ol> 
                                                              
                                                              <ol>
                                                                <li>
                                                                  在设置了所有标志后，在 config.xml 的末尾处，ServerDebug 标记将类似于如下形式： <p>
                                                                    <ServerDebug ClassFinder="true" DebugCluster="true" DebugClusterAnnouncements="true" DebugFailOver="true" DebugReplication="true" DebugReplicationDetails="true" Name="MyServer1"/>
                                                                  </p>
                                                                  
                                                                  <p>
                                                                    确保服务器的 stdOutSeverity 级别为 INFO，且 StdoutDebugEnabled 被设置为“true”。调试信息将被记录到服务器日志以及标准输出中。
                                                                  </p>
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                              </p>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold; text-decoration: underline"><a name="#Checklist_for_each_Session_Persistence_type_used">所使用的每个会话持久性类型的检查清单：</a></span>
                                                              </p>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold">内存（单个服务器，不复制）&#160; </span><span style="font-style: italic; color: rgb(255,0,0)"></span><span style="font-weight: bold"> <br /></span>
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  当您使用基于内存的存储方式时，所有会话信息都存储在内存中，并且当您停止和重新启动 WebLogic Server 时，这些信息将会丢失。
                                                                </li>
                                                                <li value="value">
                                                                  确保您在运行 WebLogic Server 时已分配足够的堆大小；否则，您的服务器可能在大量负载情况下用尽内存。
                                                                </li>
                                                                <li value="value">
                                                                  不是群集配置的推荐类型（因为数据保存在堆中，且不可用于任何其它服务器）。
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold">文件系统持久性</span>
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  确认已在 weblogic.xml 中正确指定了 WebLogic Server 存储会话的目录。您还必须自行创建此目录，并确保已分配访问此目录的适当权限。
                                                                </li>
                                                                <li value="value">
                                                                  确保拥有足够的磁盘空间。
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold">JDBC 持久性</span>
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  确保连接到数据库的连接池拥有对所用数据库表的读/写权限。
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold">基于 Cookie 的持久性</span>
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  确保在 http 会话中没有存储 java.lang.String 以外的任何内容。
                                                                </li>
                                                                <li value="value">
                                                                  不要刷新您的应用程序代码中的 Http 响应对象。
                                                                </li>
                                                                <li value="value">
                                                                  确保响应的信息长度超过所设置的缓冲区大小（缺省值为 8192 字节）。
                                                                </li>
                                                                <li value="value">
                                                                  确保在浏览器中启用了 cookie。
                                                                </li>
                                                                <li value="value">
                                                                  确保在使用基于 cookie 的会话持久性时，没有在字符串中使用逗号 (,)。
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold">内存中复制</span>
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  确保仅通过代理服务器或硬件负载平衡器来访问 Weblogic Server。
                                                                </li>
                                                                <li value="value">
                                                                  硬件负载平衡器应支持兼容的被动或主动 cookie 持久性机制以及 SSL 持久性。
                                                                </li>
                                                                <li value="value">
                                                                  群集中的推荐类型。
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                              </p>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold; text-decoration: underline"><a name="#Validate_the_Weblogic_entries">验证 Weblogic.xml 条目：</a></span> <br />确保 weblogic.xml 含有需要为每个“会话复制”类型设置的所有参数。 例如，当使用内存中复制时，样本 weblogic.xml 将类似于如下形式：
                                                              </p>
                                                              
                                                              <p>
                                                                &#160;&#160;&#160;&#160;&#160;&#160;&#160; <session-descriptor> <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; <session-param> <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; <param-name> <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; PersistentStoreType <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </param-name> <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; <param-value> <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; replicated <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </param-value> <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; </session-param> <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; </session-descriptor>
                                                              </p>
                                                              
                                                              <p>
                                                                <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                              </p>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold; text-decoration: underline"><a name="Session_Data_Must_Be_Serializable"></a>会话数据必须可序列化</span> <br />为了支持 HTTP 会话状态的内存中复制，所有 servlet 和 JSP 会话数据都必须是可序列化的，否则会话复制将会失败。当启用了调试标志时，Weblogic Server 将在下面输出警告消息，指示会话仍未被复制。您必须使该对象变为可序列化的对象，这样才能复制它。其它对象的会话复制将会正常进行。
                                                              </p>
                                                              
                                                              <p>
                                                                <strong>调试消息：</strong>
                                                              </p>
                                                              
                                                              <table style="width: 615px" border="1" cellspacing="2" cellpadding="2">
                                                                <tr>
                                                                  <td style="background-color: rgb(204,204,204); vertical-align: top">
                                                                    <font font="courier new"><Oct 8, 2003 2:10:45 PM PDT> <Error> <Cluster> <000126> <All session objects should be serializable to replicate. Please check the objects in your session. Failed to replicate non-serializable object> </font>
                                                                  </td>
                                                                </tr>
                                                              </table>
                                                              
                                                              <p>
                                                                <em>解决办法：</em>找到从中抛出错误的页面，并确保输入会话中的所有数据是可序列化的。
                                                              </p>
                                                              
                                                              <p>
                                                                <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                              </p>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold; text-decoration: underline"><a name="Check_for_Network/Multicast_issues"></a>检查网络/组播问题：</span> <br />确保网络是完好的，且没有组播问题。您可以执行组播测试来确保组播 IP 工作正常。
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  <p>
                                                                    运行 utils.MulticastTest 实用程序 <br />语法形式类似于：
                                                                  </p>
                                                                  
                                                                  <p>
                                                                    java utils.MulticastTest -n name -a address [-p portnumber] [-t timeout] [-s send]
                                                                  </p>
                                                                </li>
                                                              </ol>
                                                              
                                                              <ol>
                                                                <li value="value">
                                                                  您也可以参阅 <a href="http://e-docs.bea.com/wls/docs81/admin_ref/utils.html#1199798">http://e-docs.bea.com/wls/docs81/admin_ref/utils.html#1199798</a>
                                                                </li>
                                                              </ol>
                                                              
                                                              <p>
                                                                <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                              </p>
                                                              
                                                              <p>
                                                                <span style="font-weight: bold; text-decoration: underline"><a name="Validate_Cluster_Configuration">验证群集配置：</a></span> <br />从群集列表中选择 Primary 服务器和 Secondary 服务器。在一个由两个服务器组成的群集中，如果该群集没有包含所有服务器，则不能选择 Secondary 服务器，从而导致会话数据不能被复制。
                                                              </p>
                                                              
                                                              <p>
                                                                若要验证，可执行下列命令：
                                                              </p>
                                                              
                                                              <ol>
                                                                <li>
                                                                  确保 weblogic.jar 在类路径中。
                                                                </li>
                                                              </ol>
                                                              
                                                              <ol>
                                                                <li value="value">
                                                                  若要获得群集中的所有服务器： <p>
                                                                    java weblogic.Admin -username weblogic -password weblogic -url http://oneofthemanagedserverurlinthecluster:6151/ GET -type ClusterRuntime .pretty </li> </ol> 
                                                                    
                                                                    <p>
                                                                      这样将列出群集中的所有服务器。可以将 URL 改变为群集中的每个服务器，以确保他们拥有相同的条目。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: bold; text-decoration: underline"><a name="Application_Code_Diagnostics">应用程序代码诊断：</a></span> <br />确保仅在应用程序代码中使用 HttpSession 中的 setAttribute/removeAttribute 方法来更新 Http 会话。如果您使用其它设置方法来更改会话内的对象，WebLogic Server 将不复制这些更改。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      请不要使用 http 会话的 putValue 和removeValue 方法，因为它们不受支持，并且当您在应用程序中使用这些方法时，可能会出现会话数据复制问题。相反，请仅使用 HttpSession 的setAttribute/removeAttribute 方法。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: bold; text-decoration: underline"><a name="Cookies_Vs_URL-Rewriting">Cookie 与 URL Rewriting ：</a></span> <br />在某些情况下，浏览器或无线设备可能不接受 cookie，这样会使利用 cookie 的会话跟踪不能进行。当 WebLogic Server 检测到浏览器不接受 cookie 时，URL Rewriting 是对这种情况的一个可自动替换的解决方法。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      通过设置 WebLogic-specific 部署描述符 weblogic.xml 中、<session-param> 元素下的 URLRewritingEnabled 属性，在 WebLogic Server 中启用 URL Rewriting。此属性的缺省值为 true。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: bold; text-decoration: underline"><a name="#Performance_Issues">性能问题：</a></span>
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: bold">考虑序列化系统开销</span> <br />序列化会话数据会给复制会话状态带来一些系统开销。系统开销随序列化对象大小的增大而增加。如果您想在会话中创建很大的对象，请测试您的 servlet 的性能，以确保性能是可接受的。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: bold">控制对会话数据的帧访问</span> <br />如果您正在设计使用多帧的 Web 应用程序，请记住给定帧集中的帧无法执行任何请求同步。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      例如，尽管在逻辑上客户端应当仅创建单个会话，但帧集中的多个帧可以代表客户端应用程序创建多个会话。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      为了避免意外的应用程序行为，您应认真规划如何利用帧访问会话数据。可以应用下列其中一个一般规则来避免常见问题：
                                                                    </p>
                                                                    
                                                                    <ul>
                                                                      <li>
                                                                        在一个给定帧集中，确保只有一个帧创建和修改会话数据。
                                                                      </li>
                                                                      <li>
                                                                        始终在应用程序使用的第一个帧集内的某个帧中创建会话（例如，在所访问的第一个 HTML 页面中创建会话）。
                                                                      </li>
                                                                      <li>
                                                                        在创建会话后，仅在除第一个帧集外的其它帧集中访问会话数据。
                                                                      </li>
                                                                    </ul>
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: bold">在会话中存储更大量的数据</span> <br />JDBC 持久性和文件持久性的速度将不会更快，因为会话数据必须存储在外部资源中并从中检索，并且也会因为 JDBC 访问每个会话的更新信息而存在性能开销。如果您想在会话中存储大型对象，则应考虑 JDBC 或文件持久性。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <span style="font-weight: bold">在会话中存储小量的数据</span> <br />当您不需要在会话中存储大量数据时，基于 cookie 的会话持久性是最有用的。基于 cookie 的会话持久性可以使 WebLogic Server 安装的管理更加容易，因为不需要群集 Failover 逻辑。
                                                                    </p>
                                                                    
                                                                    <p>
                                                                      <a href="http://www.bea.com.cn/support_pattern/HTTP_Session_Replication_Failures_Pattern.html#TOP">返回页首</a>
                                                                    </p>
                                                                    
                                                                    <table style="text-align: left; width: 615px" class="FCK__ShowTableBorders" cellspacing="2" cellpadding="2">
                                                                      <tr>
                                                                        <td style="vertical-align: top">
                                                                          <p>
                                                                            <strong><u>是否需要更多帮助？</u></strong>
                                                                          </p>
                                                                          
                                                                          <p>
                                                                            如果您已经理解这个模式，但仍需要其它帮助，您可以：
                                                                          </p>
                                                                          
                                                                          <ol>
                                                                            <li>
                                                                              在 <a href="http://support.bea.com/">http://support.bea.com</a> 上查询 AskBEA（例如使用“HTTP session replication failure”），以查找其它已发布的解决方案。
                                                                            </li>
                                                                            <li>
                                                                              在 <a href="http://support.bea.com/">http://support.bea.com</a> 上，向 BEA 的某个新闻组中提出更详细具体的问题。
                                                                            </li>
                                                                          </ol>
                                                                          
                                                                          <p>
                                                                            如果这还不能解决您的问题，并且您拥有有效的技术支持合同，您可以通过登录以下网站来打开支持案例：<a href="http://support.bea.com/">http://support.bea.com</a>。
                                                                          </p>
                                                                        </td>
                                                                      </tr>
                                                                    </table>
                                                                    
                                                                    <table border="1" width="615">
                                                                      <tr>
                                                                        <td>
                                                                          <p>
                                                                            <strong>反馈</strong>
                                                                          </p>
                                                                          
                                                                          <p>
                                                                            请给我们提供您的意见，说明此支持诊断模式<strong>“HTTP 会话复制失败”</strong>一文是否有所帮助，您需要的任何解释，以及对<a href="mailto:support.ke@bea.com?subject=Patterns Feedback: HTTP Session Replication Failures&body=">支持诊断模式</a>的新主题的任何要求。
                                                                          </p>
                                                                        </td>
                                                                      </tr>
                                                                    </table>
                                                                    
                                                                    <table border="1" width="615">
                                                                      <tr>
                                                                        <td>
                                                                          <p>
                                                                            <strong>免责声明</strong>
                                                                          </p>
                                                                          
                                                                          <p>
                                                                            依据 BEA 与您签署的维护和支持协议条款，BEA Systems, Inc. 在本网站上提供技术技巧和修补程序供您使用。虽然您可以将这些信息和代码与您获得 BEA 授权的软件一起使用，但 BEA 并不对所提供的技术技巧和修补程序做任何形式的担保，无论是明确的还是隐含的。
                                                                          </p>
                                                                          
                                                                          <p>
                                                                            本文档中引用的任何商标是其各自所有者的财产。有关完整的商标信息，请参考您的产品手册。
                                                                          </p>
                                                                        </td>
                                                                      </tr>
                                                                    </table></td> </tr> </tbody> </table></div> </td> </tr> </tbody> </table></div>
                                                                  </p></div> </p></div> </p></div> </p></div> 
                                                                  
                                                                  <p>
                                                                    </center>
                                                                  </p>
                                                                  
                                                                  <p>
                                                                    转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2013/10/30/weblogic%e9%9b%86%e7%be%a4%e5%ae%9e%e7%8e%b0http%e5%a4%8d%e5%88%b6%e7%9a%84%e7%ae%80%e5%8d%95%e6%ad%a5%e9%aa%a4/">WebLogic集群实现HTTP复制的简单步骤</a>
                                                                  </p>