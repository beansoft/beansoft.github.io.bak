---
id: 1238
title: 'Weblogic 8 debug flags[forward]'
date: 2010-09-23T09:02:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1238
permalink: /2010/09/23/weblogic-8-debug-flagsforward/
views:
  - "5311"
original_post_id:
  - "1238"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Debug
  - Flag
  - WebLogic8
---
</p> 

<p class="MsoNormal" style="line-height:16.8pt;text-align:left;margin:18pt 0 6pt;" align="left">
  <span lang="EN-US" style="font-size:8pt;text-transform:uppercase;color:#999999;font-family:&quot;letter-spacing:2.4pt;">TUESDAY, FEBRUARY 13, 2007 </p> 
  
  <p>
    </span>
  </p>
  
  <p class="MsoNormal" style="line-height:16.8pt;text-align:left;" align="left">
    <a name="1865764147749548852"></a><span lang="EN-US" style="font-size:13.5pt;color:#cc6600;font-family:&quot;"><a href="http://theworkaholic.blogspot.com/2007/02/weblogic-debug-flags.html"><span style="color:#cc6600;">Weblogic debug flags</span></a> </p> 
    
    <p>
      </span>
    </p>
    
    <p class="MsoNormal" style="line-height:16.8pt;text-align:left;" align="left">
      <span lang="EN-US"><a href="http://theworkaholic.blogspot.com/2007/02/weblogic-debug-flags.html">http://theworkaholic.blogspot.com/2007/02/weblogic-debug-flags.html</a></span><span lang="EN-US" style="font-size:13.5pt;color:#cc6600;font-family:&quot;"> </p> 
      
      <p>
        </span>
      </p>
      
      <p class="MsoNormal" style="line-height:19.2pt;text-align:left;" align="left">
        <span lang="EN-US" style="font-size:10pt;color:#333333;font-family:&quot;">Reproduced from </span><span lang="EN-US"><a href="http://dev2dev.bea.com/blog/hoos/archive/2007/01/weblogic_server.html"><span style="font-size:10pt;color:#5588aa;font-family:&quot;">Hussein Badakhchani&#8217;s Blog</span></a></span><span lang="EN-US" style="font-size:10pt;color:#333333;font-family:&quot;"> and comments </p> 
        
        <p>
          </span>
        </p>
        
        <p class="MsoNormal" style="line-height:19.2pt;text-align:left;" align="left">
          <span lang="EN-US" style="font-size:10pt;color:#333333;font-family:&quot;">weblogic debug flags(8.1) <br /><b>IIOP</b> <br />weblogic.iiop.ots <br />weblogic.iiop.transport <br />weblogic.iiop.marshal <br />weblogic.iiop.startup </p> 
          
          <p>
            <b>JDBC/Data Sources</b> <br />weblogic.JDBCConn <br />weblogic.JDBCSQL <br />weblogic.JDBCConnStackTrace
          </p>
          
          <p>
            <b>JMX/Deployment</b> <br />weblogic.commoAdmin <br />weblogic.commoProxy <br />weblogic.deployerRuntime <br />weblogic.MasterDeployer <br />weblogic.deployTask <br />weblogic.deployHelper <br />weblogic.MasterDeployer <br />weblogic.OamDelta <br />weblogic.OamVersion <br />weblogic.slaveDeployer.semaphore <br />weblogic.slaveDeployer <br />weblogic.ConfigMBean <br />weblogic.ConfigMBeanEncrypt <br />weblogic.ConfigMBeanSetAttribute <br />weblogic.management.DynamicMBeanImpl <br />weblogic.management.DynamicMBeanImpl.setget <br />weblogic.mbeanProxyCache <br />weblogic.mbeanDelete <br />weblogic.mbeanQuery <br />weblogic.MBeanInteropList <br />weblogic.mbeanProxy <br />weblogic.registerMBean <br />weblogic.getMBeanInfo <br />weblogic.getMBeanAttributes <br />weblogic.addDependenciesRecursively <br />weblogic.MBeanListener <br />weblogic.application <br />weblogic.deployer <br />weblogic.appPoller <br />weblogic.appManager <br />weblogic.BootstrapServlet <br />weblogic.fileDistributionServlet
          </p>
          
          <p>
            <b>Application Deployment</b> <br />weblogic.J2EEApplication <br />weblogic.application <br />weblogic.appPoller <br />weblogic.appManager
          </p>
          
          <p>
            <b>JTA</b> <br />weblogic.JTAGateway <br />weblogic.JTAGatewayStackTrace <br />weblogic.JTA2PC <br />weblogic.JTA2PCStackTrace <br />weblogic.JTAHealth <br />weblogic.JTAPropagate <br />weblogic.JTARecovery <br />weblogic.JTAXA <br />weblogic.JTAXAStackTrace <br />weblogic.JTAResourceHealth <br />weblogic.JTAMigration <br />weblogic.JTARecoveryStackTrace <br />weblogic.JTANaming <br />weblogic.JTATLOG <br />weblogic.JTALifecycle
          </p>
          
          <p>
            <b>EJB</b> <br />weblogic.ejb.cache.debug <br />weblogic.ejb.cache.verbose <br />ejb.enableCacheDump <br />weblogic.ejb20.cmp.rdbms.debug <br />weblogic.ejb20.cmp.rdbms.verbose <br />weblogic.ejb20.persistence.debug <br />weblogic.ejb20.persistence.verbose <br />weblogic.ejb20.compliance.debug <br />weblogic.ejb20.compliance.verbose <br />weblogic.ejb.deployment.debug <br />weblogic.ejb.deployment.verbose <br />weblogic.ejb20.dd.xml <br />weblogic.ejb.deployer.debug <br />weblogic.ejb.deployer.verbose <br />weblogic.ejb.verbose.deployment <br />weblogic.ejb20.ejbc.debug <br />weblogic.ejb20.ejbc.verbose <br />weblogic.ejb.runtime.debug <br />weblogic.ejb.runtime.verbose <br />weblogic.ejb20.jms.poll.debug <br />weblogic.ejb20.jms.poll.verbose <br />weblogic.ejb20.security.debug <br />weblogic.ejb20.security.verbose <br />weblogic.ejb.locks.debug <br />weblogic.ejb.locks.verbose <br />weblogic.ejb.bean.manager.debug <br />weblogic.ejb.bean.manager.verbose <br />weblogic.ejb.pool.InstancePool.debug <br />weblogic.ejb.pool.InstancePool.verbose <br />weblogic.ejb.swap.debug <br />weblogic.ejb.swap.verbose <br />weblogic.j2ee.dd.xml
          </p>
          
          <p>
            <b>General</b> <br />weblogic.debug <br />weblogic.kernel.debug <br />weblogic.debug.DebugConnection <br />weblogic.debug.DebugRouting <br />weblogic.debug.DebugMessaging <br />weblogic.debug.isLogRemoteExceptionsEnabled <br />weblogic.StdoutDebugEnabled
          </p>
          
          <p>
            <b>WLI</b> <br />wlc.debug.signature <br />wli.bpm.client.security.debug <br />wli.bpm.studio.timeprocessor.debug <br />wli.bpm.studio.debug <br />wli.bpm.server.common.timedevent.debug <br />wli.bpm.server.common.xmltemplate.debug <br />wli.bpm.server.eventprocessor.addrmsgdebug <br />wli.bpm.server.eventprocessor.debug <br />wli.bpm.server.jms.debug <br />wli.bpm.server.plugin.debug <br />wli.bpm.server.workflow.debug <br />wli.bpm.server.businesscalendar.debug <br />wli.bpm.server.busop.debug <br />wli.bpm.server.workflow.action.taskduedate.debug <br />wli.bpm.server.workflow.timedevent.debug <br />wli.bpm.server.xml.debug <br />wli.bpm.server.xslt.debug <br />wli.bpm.server.workflow.start.debug <br />wli.bpm.server.workflowprocessor.debug <br />wli.common.server.errorlistener.debug
          </p>
          
          <p>
            <b>Messaging Bridge</b> <br />-Dweblogic.debug.DebugMessagingBridgeStartup=true -Dweblogic.debug.DebugMessagingBridgeRuntime=true And two others for stdout and stderr : -Dweblogic.Stdout= -Dweblogic.Stderr=
          </p>
          
          <p>
            <b>SSL</b> <br />-Dweblogic.security.SSL.verbose=true -Dssl.debug=true
          </p>
          
          <p>
            <b>-9.x available via console plus</b> <br />webservices: -Dweblogic.wsee.verbose=*
          </p>
          
          <p>
            <b>6.x,7.x</b> <br />http://wldj.sys-con.com/read/42733.htm
          </p>
          
          <p>
            <b>RMI debug flags</b> <br />java<br /> .rmi.server.logCalls=true <br />sun.rmi.loader.logLevel=[BRIEF|VERBOSE] <br />sun.rmi.server.exceptionTrace <br />sun.rmi.server.logLevel=[BRIEF|VERBOSE]
          </p>
          
          <p>
            </span>
          </p>
          
          <p class="MsoNormal" style="line-height:16.8pt;text-align:left;" align="left">
            <span lang="EN-US" style="font-size:8pt;text-transform:uppercase;color:#999999;font-family:&quot;letter-spacing:1.2pt;">POSTED BY DEEPAK SHETTY AT </span><span lang="EN-US"><a title="permanent link" href="http://theworkaholic.blogspot.com/2007/02/weblogic-debug-flags.html"><span style="font-size:8pt;text-transform:uppercase;color:#5588aa;font-family:&quot;letter-spacing:1.2pt;">6:48 AM</span></a></span><span lang="EN-US" style="font-size:8pt;text-transform:uppercase;color:#999999;font-family:&quot;letter-spacing:1.2pt;">&#160; </p> 
            
            <p>
              </span>
            </p>
            
            <p class="MsoNormal">
              <span lang="EN-US"> </p> 
              
              <p>
                &#160;
              </p>
              
              <p>
                </span>
              </p>
              
              <p>
                转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/23/weblogic-8-debug-flagsforward/">Weblogic 8 debug flags[forward]</a>
              </p>