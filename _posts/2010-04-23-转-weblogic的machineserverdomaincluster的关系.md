---
id: 118
title: '转: Weblogic的Machine,Server,Domain,Cluster的关系'
date: 2010-04-23T22:10:45+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=118
permalink: '/2010/04/23/%e8%bd%ac-weblogic%e7%9a%84machineserverdomaincluster%e7%9a%84%e5%85%b3%e7%b3%bb/'
views:
  - "4690"
original_post_id:
  - "118"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
Weblogic的Machine,Server,Domain,Cluster的关系 

<table border="0" cellpadding="0">
  <tr>
    <td>
      <p>
        主要关系如图所示:
      </p>
      
      <p>
        <a href="http://www.beansoft.biz/wp-content/uploads/2010/04/clip_image0011.gif"><img style="display:inline;border-width:0;" title="clip_image001[1]" border="0" alt="clip_image001[1]" src="http://www.beansoft.biz/wp-content/uploads/2010/04/clip_image0011_thumb.gif" width="244" height="141" /></a>
      </p>
      
      <p>
        机器 （Machines）
      </p>
      
      <p>
        可以对应到服务器所在的物理硬件
      </p>
      
      <p>
        可以是Unix或non-Unix类型
      </p>
      
      <p>
        可以用来远程管理和监控
      </p>
      
      <p>
        用于加强fail over管理
      </p>
      
      <p>
        A machine is a computer that holds Weblogic Server(s).
      </p>
      
      <p>
        A machine:
      </p>
      
      <ul>
        <li>
          Runs a supported operating system platform
        </li>
        <li>
          Can host multiple Weblogic Server instances
        </li>
      </ul>
      
      <p>
        MyDomain {Machine1, Machine2}
      </p>
      
      <p>
        <b>服务器 （Servers）</b>
      </p>
      
      <p>
        服务器是执行在单一Java虚拟机（JVM）中weblogic.Server类的实例。
      </p>
      
      <p>
        最多和一个WLS机器关联
      </p>
      
      <p>
        占用一定数量的RAM
      </p>
      
      <p>
        是多线程的
      </p>
      
      <p>
        A server is an instance of weblogic.Server executing in a JVM. A server:
      </p>
      
      <ul>
        <li>
          Runs on a designated WLS machine;
        </li>
        <li>
          Has a dedicated amount of RAM;
        </li>
        <li>
          Is multi-threaded
        </li>
      </ul>
      
      <p>
        MyDomain { Machine {Server1, Server2} }
      </p>
      
      <p>
        <b>域 （Domains）</b>
      </p>
      
      <p>
        域是管理的单元或边界
      </p>
      
      <p>
        作为一个单元来管理的，并相互关联的一组Weblogic 服务器资源被称为域
      </p>
      
      <p>
        <b>为什么用域？</b>
      </p>
      
      <p>
        域管理的特征
      </p>
      
      <ul>
        <li>
          对应用来说是透明的
        </li>
        <li>
          可以出于技术或业务的理由来配置、管理
        </li>
      </ul>
      
      <p>
        WLS域可以用来分离：
      </p>
      
      <ul>
        <li>
          开发/测试/上线的应用
        </li>
        <li>
          管理和操作的任务
        </li>
        <li>
          组织或业务分配
        </li>
      </ul>
      
      <p>
        <b>集群 （Clustering）</b>
      </p>
      
      <p>
        WebLogic集群技术指通过一组服务器共同工作，在多台机器间复制应用表示层和应用逻辑层的能力，实现关键业务系统的负载分布，消除个别故障点。 集群用来实现负载均衡和容错
      </p>
      
      <p>
        A cluster is a logical group of WLS servers.
      </p>
      
      <p>
        WebLogic clusters provide automatic:
      </p>
      
      <ul>
        <li>
          Load-balancing
        </li>
        <li>
          Falut tolerance
        </li>
      </ul>
      
      <p>
        A cluster is transparent to a client.
      </p>
    </td>
  </tr>
</table>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [转: Weblogic的Machine,Server,Domain,Cluster的关系](http://www.beansoft.biz/2010/04/23/%e8%bd%ac-weblogic%e7%9a%84machineserverdomaincluster%e7%9a%84%e5%85%b3%e7%b3%bb/)