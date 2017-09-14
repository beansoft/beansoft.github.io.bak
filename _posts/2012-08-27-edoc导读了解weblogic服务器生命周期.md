---
id: 2982
title: edoc导读:了解WebLogic服务器生命周期
date: 2012-08-27T22:54:52+00:00
author: 刘长炯
layout: post
guid: http://weblogic.clawz.com/?p=2982
permalink: '/2012/08/27/edoc%e5%af%bc%e8%af%bb%e4%ba%86%e8%a7%a3weblogic%e6%9c%8d%e5%8a%a1%e5%99%a8%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f/'
views:
  - "3093"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Services
  - WebLogic
---
点击 [http://weblogic.clawz.com/weblogic/docs100/server\_start/server\_life.html](http://weblogic.clawz.com/weblogic/docs100/server_start/server_life.html "http://weblogic.clawz.com/weblogic/docs100/server_start/server_life.html") 阅读全文. 需要提示的是WebLogic是以顺序的方式启动所有内部服务的, 一旦中间某一环节出错, 则后续服务不会继续载入而是转入失败状态.

&#160;

以下为摘要:

&#160;

服务器生命周期命令的状态转换 

<del><a name="wp1052793"></a></del>

![服务器生命周期命令的状态转换](http://weblogic.clawz.com/weblogic/docs100/server_start/wwimages/lifecycle.gif)

<del><a name="wp1052797"></a></del>要理解每种状态以及状态之间的关系，请参阅[了解服务器生命周期中的服务器状态](http://weblogic.clawz.com/weblogic/docs100/server_start/server_life.html#wp1052817)。有关生命周期命令的信息，请参阅[使用服务器生命周期命令](http://weblogic.clawz.com/weblogic/docs100/server_start/server_life.html#wp1052935)。 

&#160;

服务器实例将以[表 6-1](http://weblogic.clawz.com/weblogic/docs100/server_start/server_life.html#wp402325) 中的列出顺序启动该表中列出的服务。</p> 

<div align="left">
  <table id="wp402325table1062864" class="table" cellspacing="0" cellpadding="3">
    <caption>表 6-1 <span style="font-style: normal; vertical-align: baseline; font-weight: bold; text-decoration: none">以 STARTING 状态启动的服务</span> </caption> <tr valign="top" align="center" bgcolor="#cccccc">
      <th scope="col">
        <div class="pCellHeading">
          <del><a name="wp1063520"></a></del>服务&#160;
        </div>
      </th>
      
      <th scope="col">
        <div class="pCellHeading">
          <del><a name="wp1063522"></a></del>功能
        </div>
      </th>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063524"></a></del><code class="cCode">weblogic.management.provider.internal.BeanInfoAccessService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063528"></a></del><code class="cCode">weblogic.management.PropertyService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063532"></a></del><code class="cCode">weblogic.management.internal.DomainDirectoryService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063536"></a></del><code class="cCode">weblogic.upgrade.domain.DomainUpgradeServerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063540"></a></del><code class="cCode">weblogic.management.upgrade.ConfigurationMigrationService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063544"></a></del><code class="cCode">weblogic.deploy.service.internal.DeploymentService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063548"></a></del><code class="cCode">weblogic.management.provider.internal.RuntimeAccessDeploymentReceiverService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063552"></a></del><code class="cCode">weblogic.management.provider.internal.RuntimeAccessService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063556"></a></del><code class="cCode">weblogic.diagnostics.lifecycle.DiagnosticInstrumentationService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063560"></a></del><code class="cCode">weblogic.t3.srvr.LicenseService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063564"></a></del><code class="cCode">weblogic.t3.srvr.BootService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063566"></a></del>包括诸如内核、执行队列和服务器运行时等基本服务。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063568"></a></del><code class="cCode">weblogic.management.provider.internal.DomainAccessService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063570"></a></del>仅管理服务器服务的根。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063572"></a></del><code class="cCode">weblogic.diagnostics.lifecycle.DiagnosticFoundationService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063574"></a></del>用于日志记录和调试的容器服务。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063576"></a></del><code class="cCode">weblogic.nodemanager.NMService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063578"></a></del>节点管理器服务，负责通过服务器输出流将服务器状态更改报告至节点管理器。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063580"></a></del><code class="cCode">weblogic.timers.internal.TimerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063584"></a></del><code class="cCode">weblogic.rjvm.RJVMService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063586"></a></del>在关闭期间，关闭所有 RJVM（管理服务器连接除外）。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063588"></a></del><code class="cCode">weblogic.protocol.ProtocolService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063592"></a></del><code class="cCode">weblogic.t3.srvr.DomainLibService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063594"></a></del>注册已配置的协议，使它们可用于出站流量配置和入站配置。受管服务器要求在开始启动顺序时就提供此服务，以便它们向管理服务器提供正确的寻址信息。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063596"></a></del><code class="cCode">weblogic.server.channels.Channel               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063598"></a></del>此服务依赖于一致配置和所注册的协议。启动顺序进行至此，所有协议应均已注册。
        </div>
        
        <div class="pCellBody">
          <del><a name="wp1063599"></a></del>此服务启动后，诸如 <code class="cCode">ServerChannelManager.findDefaultLocalServer Channel()</code> 等寻址信息可用。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063601"></a></del><code class="cCode">weblogic.server.channels.AdminPort               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063605"></a></del><code class="cCode">weblogic.t3.srvr.ListenerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063609"></a></del><code class="cCode">weblogic.transaction.internal.               &lt;br />PrimordialTransactionService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063611"></a></del>转换助手已经初始化，能够提供各种实用工具：获取事务管理器并将事务与线程关联起来，获取 <code class="cCode">UserTransaction</code> 对象以及执行其他任务。
        </div>
        
        <p class="pTableNote">
          <del><a name="wp1063612"></a></del>
        </p>
        
        <table>
          <tr>
            <td valign="top">
              <strong>注意：</strong>
            </td>
            
            <td>
              启动顺序进行至此，事务服务自身并未启用。
            </td>
          </tr>
        </table>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063614"></a></del><code class="cCode">weblogic.rmi.internal.RMIServerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063616"></a></del>仅用于初始化的 RMI 引导服务。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063618"></a></del><code class="cCode">weblogic.jndi.internal.NamingService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063622"></a></del><code class="cCode">weblogic.iiop.IIOPClientService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063624"></a></del>安装 VM 范围内的委托。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063626"></a></del><code class="cCode">weblogic.management.Primordial               &lt;br />ManagementService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063630"></a></del><code class="cCode">weblogic.ldap.EmbeddedLDAP</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063634"></a></del><code class="cCode">weblogic.security.SecurityService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063638"></a></del><code class="cCode">weblogic.jndi.internal.RemoteNaming               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063642"></a></del><code class="cCode">weblogic.security.acl.internal.Remote               &lt;br />SecurityService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063646"></a></del><code class="cCode">weblogic.rmi.cluster.RemoteBinder               &lt;br />FactoryService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063650"></a></del><code class="cCode">weblogic.cluster.ClusterService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063654"></a></del><code class="cCode">weblogic.iiop.IIOPService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063658"></a></del><code class="cCode">weblogic.protocol.ProtocolHandler               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063662"></a></del><code class="cCode">weblogic.management.internal.AdminService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063666"></a></del><code class="cCode">weblogic.xml.registry.XMLService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063670"></a></del><code class="cCode">weblogic.messaging.interception.               &lt;br />MessageInterceptionService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063674"></a></del><code class="cCode">weblogic.cluster.migration.rmiservice.MigratableRMIService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063678"></a></del><code class="cCode">weblogic.messaging.interception.               &lt;br />configuration.Configurator</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063682"></a></del><code class="cCode">weblogic.drs.internal.DataReplication               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063686"></a></del><code class="cCode">weblogic.management.provider.internal.EditAccessService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063688"></a></del>启动管理编辑服务。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063690"></a></del><code class="cCode">weblogic.health.HealthMonitorService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063694"></a></del><code class="cCode">weblogic.cluster.migration.Migration               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063698"></a></del><code class="cCode">weblogic.t3.srvr.T3Initialization               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063700"></a></del>初始化不赞成使用的 T3 服务器服务，例如 <code class="cCode">BootServicesImpl</code>。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063702"></a></del><code class="cCode">weblogic.server.channels.Channel               &lt;br />RuntimeService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063704"></a></del>启动顺序进行至此，诸如 <code class="cCode">ServerRuntime.getListenAddress()</code> 等寻址信息和动态更新都可用。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063706"></a></del><code class="cCode">weblogic.store.admin.DefaultStore               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063710"></a></del><code class="cCode">weblogic.transaction.internal.               &lt;br />TransactionService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063714"></a></del><code class="cCode">weblogic.jdbc.common.internal.               &lt;br />JDBCService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063718"></a></del><code class="cCode">weblogic.connector.common.               &lt;br />ConnectorService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063722"></a></del><code class="cCode">weblogic.store.admin.Store               &lt;br />DeploymentService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063726"></a></del><code class="cCode">weblogic.jms.JMSServiceServerLifeCycleImpl</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063730"></a></del><code class="cCode">weblogic.jms.BridgeService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063734"></a></del><code class="cCode">weblogic.application.Application               &lt;br />ShutdownService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063736"></a></del>检查正常关闭期间的待定应用程序工作。同时关闭应用程序。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063738"></a></del><code class="cCode">weblogic.messaging.saf.internal.               &lt;br />SAFServerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063742"></a></del><code class="cCode">weblogic.ejb20.deployer.EJB20Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063746"></a></del><code class="cCode">weblogic.io.common.internal.File               &lt;br />Service</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063750"></a></del><code class="cCode">weblogic.time.server.TimerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063752"></a></del>在关闭期间取消应用程序触发器。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063754"></a></del><code class="cCode">weblogic.rmi.internal.HeartbeatHelperService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063756"></a></del>支持仅协议客户端内的心跳。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063758"></a></del><code class="cCode">weblogic.servlet.internal.WebService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063762"></a></del><code class="cCode">weblogic.webservice.conversation.               &lt;br />internal.ConversationServiceImpl</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063766"></a></del><code class="cCode">weblogic.wtc.gwt.WTCServerLife               &lt;br />CycleImpl</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063770"></a></del><code class="cCode">com.beasys.CORBA.pool.weblogic.               &lt;br />WLECService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063774"></a></del><code class="cCode">weblogic.management.service.Managed               &lt;br />ServerNotificationService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063778"></a></del><code class="cCode">weblogic.webservice.WSServerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063782"></a></del><code class="cCode">weblogic.management.mbeanservers.               &lt;br />runtime.internal.RuntimeServerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063784"></a></del>运行时 JMX 服务。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063868"></a></del><code class="cCode">weblogic.management.mbeanservers.               &lt;br />edit.internal.EditServerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063872"></a></del><code class="cCode">weblogic.management.mbeanservers.compatability.internal.               &lt;br />CompatabilityMBeanServerService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063876"></a></del><code class="cCode">weblogic.management.snmp.SNMPService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063880"></a></del><code class="cCode">weblogic.management.deploy.               &lt;br />classdeployment.ClassDeploymentService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063882"></a></del>添加启动和关闭类的处理。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063884"></a></del><code class="cCode">weblogic.server.ServerLifeCycleService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063886"></a></del>处理服务器生命周期运行时 Mbean 的创建以允许控制域。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063888"></a></del><code class="cCode">weblogic.server.channels.EnableAdmin               &lt;br />ListenersService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063890"></a></del>在服务器进入 <code class="cCode">ADMIN</code> 状态之前启用管理端口。
        </div>
      </td>
    </tr>
    
    <tr valign="top" align="left">
      <td class="table" scope="row">
        <div class="pCellBody">
          <del><a name="wp1063892"></a></del><code class="cCode">domainweblogic.diagnostics.lifecycle.               &lt;br />DiagnosticSystemService</code>
        </div>
      </td>
      
      <td class="table" scope="row">
        &#160;
      </td>
    </tr>
  </table>
</div>

<p class="pGraphic">
  <h3 class="pHeading2">
    <del><a name="wp1062829"></a></del>STA<a name="StandbyState"></a>NDBY 状态
  </h3>
  
  <p>
    转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2012/08/27/edoc%e5%af%bc%e8%af%bb%e4%ba%86%e8%a7%a3weblogic%e6%9c%8d%e5%8a%a1%e5%99%a8%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f/">edoc导读:了解WebLogic服务器生命周期</a>
  </p>