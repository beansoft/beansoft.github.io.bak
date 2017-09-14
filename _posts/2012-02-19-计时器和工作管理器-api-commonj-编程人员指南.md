---
id: 2673
title: 计时器和工作管理器 API (CommonJ) 编程人员指南
date: 2012-02-19T19:23:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2673
permalink: '/2012/02/19/%e8%ae%a1%e6%97%b6%e5%99%a8%e5%92%8c%e5%b7%a5%e4%bd%9c%e7%ae%a1%e7%90%86%e5%99%a8-api-commonj-%e7%bc%96%e7%a8%8b%e4%ba%ba%e5%91%98%e6%8c%87%e5%8d%97/'
views:
  - "4167"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
<p style="background: white; margin-left: 12pt">
  <span style="color: #0076cc"><span style="font-size: 14pt"><strong><span style="font-family: 宋体">计时器和工作管理器</span><span style="font-family: verdana"> API (CommonJ) </span><span style="font-family: 宋体">编程人员指南</span><span style="font-family: verdana"> </p> 
  
  <table style="background: white; border-collapse: collapse" border="0">
    <colgroup> <col style="width: 578px" /></colgroup> <tr>
      <td style="padding-right: 1px; padding-left: 1px; padding-bottom: 1px; padding-top: 1px" valign="middle">
        &#160;<a name="link_group_0"></a>
      </td>
    </tr>
  </table>
  
  <p>
    </span></strong></span></span>
  </p>
  
  <p>
    <span style="font-size: 10pt; color: black"><span style="font-family: 宋体; background-color: white">本文整理自</span><span style="font-family: verdana; background-color: white"> WebLogic 10.0</span><span style="font-family: 宋体; background-color: white">中文文档。</span><span style="font-family: verdana; background-color: white"> </span></span>
  </p>
  
  <p>
    <span style="color: black"><span style="font-size: 10pt"><span style="font-family: 宋体; background-color: white">更多</span><span style="font-family: verdana; background-color: white">CommonJ</span><span style="font-family: 宋体; background-color: white">规范的信息参考：<a href="http://www.ibm.com/developerworks/library/specification/j-commonj-sdowmt/index.html"></a></span><span style="color: blue; text-decoration: underline">http://www.ibm.com/developerworks/library/specification/j-commonj-sdowmt/index.html</span><span style="font-size: 12pt; font-family: 宋体"> </span></span></span>
  </p>
  
  <p style="background: white; margin-left: 12pt">
    <span style="font-size: 30pt; color: black"><span style="font-family: 宋体"></span><a name="wp1043185">计时器和工作管理器</a><span style="font-family: arial"> API </span></span>
  </p>
  
  <p style="background: white; margin-left: 12pt">
    <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057936">此文档概述计时器和工作管理器</a><span style="font-family: verdana"> API</span><span style="font-family: 宋体">，并说明其在应用程序中的实现方法。</span><span style="font-family: verdana"> </span></span>
  </p>
  
  <ul style="margin-left: 36pt">
    <li>
      <div style="background: white">
      </div>
      
      <p>
        <a href="#wp1057962"><span style="font-size: 10pt; text-decoration: underline"><span style="font-family: 宋体">计时器和工作管理器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">的描述</span></span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span></li> </ul>
      </p>
      
      <ul style="margin-left: 36pt">
        <li>
          <div style="background: white">
            <a href="#wp1057981"><span style="font-size: 10pt; color: #0076cc; text-decoration: underline"><span style="font-family: 宋体">计时器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">概述</span></span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span>
          </div>
        </li>
        
        <li>
          <div style="background: white">
            <a href="#wp1058023"><span style="font-size: 10pt; color: #0076cc; text-decoration: underline"><span style="font-family: 宋体">使用计时器</span><span style="font-family: verdana"> API</span></span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span>
          </div>
        </li>
        
        <li>
          <div style="background: white">
            <a href="#wp1058049"><span style="font-size: 10pt; color: #0076cc; font-family: 宋体; text-decoration: underline">使用作业调度程序</span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span>
          </div>
        </li>
        
        <li>
          <div style="background: white">
            <a href="#wp1058124"><span style="font-size: 10pt; color: #0076cc; text-decoration: underline"><span style="font-family: 宋体">工作管理器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">的描述</span></span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span>
          </div>
        </li>
        
        <li>
          <div style="background: white">
            <a href="#wp1058139"><span style="font-size: 10pt; color: #0076cc; font-family: 宋体; text-decoration: underline">工作管理器示例</span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span>
          </div>
        </li>
      </ul>
      
      <p style="background: white">
        &#160;&#160;
      </p>
      
      <p>
        <img alt="" src="http://www.blogjava.net/images/blogjava_net/beansoft/021912_1923_API1.png" /><span style="font-size: 12pt; font-family: 宋体"> </span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 30pt; color: black"><span style="font-family: 宋体"><a name="wp1057962">计时器和工作管理器</a><span style="font-family: arial"> API </span><span style="font-family: 宋体">的描述</span><span style="font-family: arial"> </span></span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057963">计时器和工作管理器</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">是按照</span><span style="font-family: verdana"> BEA Systems </span><span style="font-family: 宋体">和</span><span style="font-family: verdana"> IBM </span><span style="font-family: 宋体">共同创建的规范进行定义的。通过此</span><span style="font-family: verdana"> API</span><span style="font-family: 宋体">，可以并发编写在</span><span style="font-family: verdana"> Java EE </span><span style="font-family: 宋体">应用程序中的</span><span style="font-family: verdana"> EJB </span><span style="font-family: 宋体">和</span><span style="font-family: verdana"> Servlet </span><span style="font-family: 宋体">程序。此</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">经常被称为</span><span style="font-family: verdana"> CommonJ</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: verdana"></span><a name="wp1057964">CommonJ API </a><span style="font-family: 宋体">包含下列组件：</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <ul style="margin-left: 36pt">
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057965">计时器</a><span style="font-family: verdana"> API </span></span>
          </div>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057966">通过计时器</a><span style="font-family: verdana"> API</span><span style="font-family: 宋体">，应用程序可以为在某一应用程序中定义的特定监听器调度和接收计时器通知回调。通过计时器，您可以在特定时间或间隔调度和执行工作。请参阅</span><a href="#wp1057981"><span style="color: #0076cc; text-decoration: underline">计时器</span></a></span><span style="font-family: verdana; text-decoration: underline"> API </span><span style="color: #0076cc"><span style="font-family: 宋体"><span style="text-decoration: underline">概述</span><span style="color: black">。</span></span><span style="font-family: verdana"> </span></span>
          </p>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"><a name="wp1057970">此</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">通过导入</span><span style="font-family: verdana"> commonj.timer </span><span style="font-family: 宋体">包来实现。</span><span style="font-family: verdana"> </span></span></span>
          </p>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057971">工作管理器</a><span style="font-family: verdana"> API </span></span>
          </div>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057972">通过工作管理器</a><span style="font-family: verdana"> API</span><span style="font-family: 宋体">，应用程序可以确定</span><span style="font-family: verdana"> EJB </span><span style="font-family: 宋体">或</span><span style="font-family: verdana"> Servlet </span><span style="font-family: 宋体">中工作的优先级。应用程序可采用编程方式，在一个容器中执行多个工作项。请参阅</span><a href="#wp1058124"><span style="color: #0076cc; text-decoration: underline">工作管理器</span></a></span><span style="font-family: verdana; text-decoration: underline"> API </span><span style="color: #0076cc"><span style="font-family: 宋体"><span style="text-decoration: underline">的描述</span><span style="color: black">。</span></span><span style="font-family: verdana"> </span></span>
          </p>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"><a name="wp1057976">此</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">通过导入</span><span style="font-family: verdana"> commonj.work </span><span style="font-family: 宋体">包来实现。</span><span style="font-family: verdana"> </span></span></span>
          </p>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057977">除</a><span style="font-family: verdana"> CommonJ </span><span style="font-family: 宋体">工作管理器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">外，</span><span style="font-family: verdana">WebLogic Server </span><span style="font-family: 宋体">还包含服务器级别的工作管理器，这些工作管理器可提供优先级和线程管理。这些可以通过全局方式进行配置，也可以针对应用程序的特定模块进行配置。</span><span style="font-family: verdana"> </span></span>
          </p></p>
        </li>
      </ul>
      
      <p style="background: white">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057978">虽然</a><span style="font-family: verdana"> commonj.timer </span><span style="font-family: 宋体">和</span><span style="font-family: verdana"> commonj.work </span><span style="font-family: 宋体">属于同一个</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">的一部分，但它们的功能却各不相同。您可以根据应用程序的特定需要实现其中的一种。</span><span style="font-family: verdana">CommonJ </span><span style="font-family: 宋体">计时器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">适用于按特定间隔调度工作的情形；例如，您知道某一项作业应在特定时间运行的情形。而</span><span style="font-family: verdana"> CommonJ </span><span style="font-family: 宋体">工作</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">适用于根据优先级处理工作的情形。例如，您不能准确预测一项特定作业的发生时间，而是希望这项作业被赋予更高或更低的优先级。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057979">下列部分将详细描述</a><span style="font-family: verdana"> CommonJ API</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        &#160;&#160;
      </p>
      
      <p>
        <img alt="" src="http://www.blogjava.net/images/blogjava_net/beansoft/021912_1923_API2.png" /><span style="font-size: 12pt; font-family: 宋体"> </span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 30pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057981">计时器</a><span style="font-family: arial"> API </span><span style="font-family: 宋体">概述</span><span style="font-family: arial"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057982">计时器</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">包含以下三个接口：</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <ul style="margin-left: 36pt">
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057983">计时器管理器</a><span style="font-family: verdana"> </span></span>
          </div>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057984">计时器监听器</a><span style="font-family: verdana"> </span></span>
          </div>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1059163">计时器对象</a><span style="font-family: verdana"> </span></span>
          </div>
        </li>
      </ul>
      
      <p style="background: white">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057990">计时器管理器提供在受管环境中创建和使用计时器的框架。计时器监听器接收计时器通知。</a><span style="font-family: verdana">TimerManager.schedule() </span><span style="font-family: 宋体">方法用于调度</span><span style="font-family: verdana"> TimerListener</span><span style="font-family: 宋体">，使其在特定时间或间隔运行。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1057997">有关如何实现计时器的详细描述，请参阅</a><a href="#wp1058023"><span style="color: #0076cc; text-decoration: underline">使用计时器</span></a></span><span style="font-family: verdana; text-decoration: underline"> API</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span>
      </p></p> 
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 23pt; color: black"><span style="font-family: arial"><a name="wp1057998">TimerManager </a><span style="font-family: 宋体">接口</span><span style="font-family: arial"> </span></span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: verdana"></span><a name="wp1060214">TimerManager </a><span style="font-family: 宋体">接口在应用程序中提供常规调度框架。受管的环境可以支持多个</span><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">实例。这就是说，一个应用程序可以包含多个</span><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">实例。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 18pt; color: black"><span style="font-family: 宋体"></span><a name="wp1060215">创建和配置计时器管理器</a><span style="font-family: arial"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1060216">可通过部署描述符在部署期间配置</a><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。</span><span style="font-family: verdana">TimerManager </span><span style="font-family: 宋体">定义还可以包含其他实现特定的配置信息。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1060239">一旦在部署描述符中定义了</a><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">，您就可以在本地</span><span style="font-family: verdana"> Java </span><span style="font-family: 宋体">环境中使用</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找访问它的实例。每次调用</span><span style="font-family: verdana"> JNDI lookup() </span><span style="font-family: 宋体">访问</span><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">时，都将返回</span><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">的一个新逻辑实例。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: verdana"></span><a name="wp1058005">TimerManager </a><span style="font-family: 宋体">接口是线程安全的。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058006">有关使用</a><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">的详细信息，请参阅</span><span style="font-family: verdana">"WebLogic JNDI </span><span style="font-family: 宋体">编程</span><span style="font-family: verdana">"</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 18pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058014">挂起</a><span style="font-family: arial"> TimerManager </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058015">可使用</a><span style="font-family: verdana"> suspend() </span><span style="font-family: 宋体">和</span><span style="font-family: verdana"> resume() </span><span style="font-family: 宋体">方法，挂起和恢复</span><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。当挂起</span><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">时，所有待定的计时器将延迟到</span><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">恢复时为止。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 18pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058016">停止</a><span style="font-family: arial"> TimerManager </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058017">可使用</a><span style="font-family: verdana"> stop() </span><span style="font-family: 宋体">方法停止</span><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。在调用</span><span style="font-family: verdana"> stop() </span><span style="font-family: 宋体">方法后，所有活动的计时器都将停止，而且</span><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">实例将停止监视所有</span><span style="font-family: verdana"> TimerListener </span><span style="font-family: 宋体">实例。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 23pt; color: black"><span style="font-family: arial"></span><a name="wp1058018">TimerListener </a><span style="font-family: 宋体">接口</span><span style="font-family: arial"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="color: black"><span style="font-size: 10pt"><span style="font-family: 宋体"></span><a name="wp1058019">使用</a><span style="font-family: verdana">&#160;</span></span><span style="font-size: 12pt; font-family: courier new">commonj.timers</span><span style="font-size: 10pt"><span style="font-family: verdana">&#160;</span><span style="font-family: 宋体">包的所有应用程序都需要实现</span><span style="font-family: verdana"> TimerListener </span><span style="font-family: 宋体">接口。</span><span style="font-family: verdana"> </span></span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 23pt; color: black"><span style="font-family: arial"></span><a name="wp1058020">Timer </a><span style="font-family: 宋体">接口</span><span style="font-family: arial"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058021">当通过</a><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">调度计时器时，将返回</span><span style="font-family: verdana"> Timer </span><span style="font-family: 宋体">接口的实例。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        &#160;&#160;
      </p>
      
      <p>
        <img alt="" src="http://www.blogjava.net/images/blogjava_net/beansoft/021912_1923_API3.png" /><span style="font-size: 12pt; font-family: 宋体"> </span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 30pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058023">使用计时器</a><span style="font-family: arial"> API </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058024">此部分将简述在应用程序中使用计时器</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">时的必需步骤。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058025">在部署应用程序前，确保已创建了包含计时器管理器资源引用的部署描述符。</a><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058029">这样可以通过</a><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">访问</span><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。有关</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找的详细信息，请参阅</span><span style="font-family: verdana">"WebLogic JNDI </span><span style="font-family: 宋体">编程</span><span style="font-family: verdana">"</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058030">下面描述计时器</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">的实现过程：</span><span style="font-family: verdana"> </span></span>
      </p>
      
      <ol style="margin-left: 36pt">
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058031">导入</a><span style="font-family: verdana"> commonj.timers.* </span><span style="font-family: 宋体">包。</span><span style="font-family: verdana"> </span></span>
          </div>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058032">创建一个</a><span style="font-family: verdana"> InitialContext</span><span style="font-family: 宋体">，以便在</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">中查找</span><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
          </div>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058033">IntialContext inctxt = new InitialContext(); </a>
          </p>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058034">有关</a><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找的详细信息，请参阅</span><span style="font-family: verdana">"WebLogic JNDI </span><span style="font-family: 宋体">编程</span><span style="font-family: verdana">"</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
          </p>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058035">基于</a><span style="font-family: verdana"> TimerManager </span><span style="font-family: 宋体">的</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找，新建一个</span><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
          </div>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058036">TimerManager mgr = (TimerManager)ctx.lookup(`java:comp/env/timer/MyTimer&#8217;); </a>
          </p>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058037">在此语句中，将</a><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找结果强制转换成</span><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
          </p>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058038">实现</a><span style="font-family: verdana"> TimerListener </span><span style="font-family: 宋体">来接收计时器通知。</span><span style="font-family: verdana"> </span></span>
          </div>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058039">TimerListener listener = new StockQuoteTimerListener(`abc&#8217;, `example&#8217;); </a>
          </p>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058040">调用</a><span style="font-family: verdana"> TimerManager.schedule() </span></span>
          </div>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058041">mgr.schedule(listener, 0, 1000*60) </a>
          </p>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: verdana"></span><a name="wp1058042">schedule() </a><span style="font-family: 宋体">方法返回计时器对象。</span><span style="font-family: verdana"> </span></span>
          </p>
        </li>
        
        <li>
          <div style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058043">实现</a><span style="font-family: verdana"> timerExpired() </span><span style="font-family: 宋体">方法</span><span style="font-family: verdana"> </span></span>
          </div>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black"><span style="font-family: courier new"></span><a name="wp1058044">public void timerExpired(Timer timer) { <br />&#160;&#160;&#160;&#160; //</a><span style="font-family: 宋体">此方法执行</span><span style="font-family: courier new"> <br />&#160;&#160;&#160;&#160; //</span><span style="font-family: 宋体">业务逻辑</span><span style="font-family: courier new"> </span></span>
          </p>
          
          <p style="background: white">
            <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058045">} </a>
          </p>
        </li>
      </ol>
      
      <p style="background: white">
        <span style="font-size: 23pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058046">计时器管理器示例</a><span style="font-family: arial"> </span></span>
      </p>
      
      <p style="background: white; margin-left: 12pt">
        <span style="font-size: 10pt; color: black"><span style="font-family: courier new"></span><a name="wp1059634">package examples.servlets; <br />import java.io.IOException; <br />import java.io.PrintWriter; </p> 
        
        <p>
          import javax.servlet.http.HttpServlet; <br />import javax.servlet.http.HttpServletRequest; <br />import javax.servlet.http.HttpServletResponse; <br />import javax.naming.InitialContext; <br />import javax.naming.NamingException;
        </p>
        
        <p>
          import commonj.timers.*;
        </p>
        
        <p>
          /** <br />* TimerServlet </a><span style="font-family: 宋体">演示了</span><span style="font-family: courier new"> commonj </span><span style="font-family: 宋体">计时器的简单使用</span><span style="font-family: courier new"> <br />*/ <br />public class TimerServlet extends HttpServlet { </p> 
          
          <p>
            /** <br />&#160; * </span><span style="font-family: 宋体">非常简单地实现服务方法</span><span style="font-family: courier new"> <br />&#160; * </span><span style="font-family: 宋体">该实现安排了</span><span style="font-family: courier new"> commonj </span><span style="font-family: 宋体">计时器。</span><span style="font-family: courier new"> <br />&#160; */ <br />&#160; public void service(HttpServletRequest req, HttpServletResponse res) <br />&#160;&#160;&#160; throws IOException <br />&#160; { <br />&#160;&#160;&#160; res.setContentType("text/html"); <br />&#160;&#160;&#160; PrintWriter out = res.getWriter(); <br />&#160;&#160;&#160; try { <br />&#160;&#160;&#160;&#160;&#160; InitialContext ic = new InitialContext(); <br />&#160;&#160;&#160;&#160;&#160; TimerManager tm = (TimerManager)ic.lookup <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160; ("java:comp/env/tm/default"); <br />&#160;&#160;&#160;&#160;&#160; // </span><span style="font-family: 宋体">立即开始每</span><span style="font-family: courier new"> 10 </span><span style="font-family: 宋体">秒执行一次计时器</span><span style="font-family: courier new"> <br />&#160;&#160;&#160;&#160;&#160; tm.schedule (new MyTimerListener(), 0, 10*1000); <br />&#160;&#160;&#160;&#160;&#160; out.println("<h4>Timer scheduled!</h4>"); <br />&#160;&#160;&#160; } catch (NamingException ne) { <br />&#160;&#160;&#160;&#160;&#160; ne.printStackTrace(); <br />&#160;&#160;&#160;&#160;&#160; out.println("<h4>Timer schedule failed!</h4>"); <br />&#160;&#160;&#160; } <br />&#160; } </p> 
            
            <p>
              &#160; private static class MyTimerListener implements TimerListener { <br />&#160;&#160;&#160; public void timerExpired(Timer timer) { <br />&#160;&#160;&#160;&#160;&#160; System.out.println("timer expired called on " + timer); <br />&#160;&#160;&#160;&#160;&#160; // </span><span style="font-family: 宋体">此处一些有用的工作</span><span style="font-family: courier new">&#8230; <br />&#160;&#160;&#160;&#160;&#160; // </span><span style="font-family: 宋体">只取消计时器</span><span style="font-family: courier new"> <br />&#160;&#160;&#160;&#160;&#160; System.out.println("cancelling timer &#8230;"); <br />&#160;&#160;&#160;&#160;&#160; timer.cancel(); <br />&#160;&#160;&#160; } <br />&#160; } <br />} </span></span>
            </p>
            
            <p style="background: white; margin-left: 12pt">
              &#160;&#160;
            </p>
            
            <p>
              <img alt="" src="http://www.blogjava.net/images/blogjava_net/beansoft/021912_1923_API4.png" /><span style="font-size: 12pt; font-family: 宋体"> </span>
            </p>
            
            <p style="background: white; margin-left: 12pt">
              <span style="font-size: 30pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058049">使用作业调度程序</a><span style="font-family: arial"> </span></span>
            </p>
            
            <p style="background: white; margin-left: 12pt">
              <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058050">此部分描述作业调度程序功能的用法。通过作业调度程序，您可以在群集环境中实现</a><span style="font-family: verdana"> commonj.timer API</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
            </p>
            
            <p style="background: white; margin-left: 12pt">
              <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1059083">作业调度程序实际上就是可以在群集中使用的</a><span style="font-family: verdana"> commonj.timer API </span><span style="font-family: 宋体">包的实现。在此上下文，作业被定义为要提交给作业调度程序进行执行的</span><span style="font-family: verdana"> commonj.timers.TimerListener </span><span style="font-family: 宋体">实例。</span><span style="font-family: verdana"> </span></span>
            </p>
            
            <p style="background: white; margin-left: 12pt">
              <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1059081">本部分包含下列主题：</a><span style="font-family: verdana"> </span></span>
            </p>
            
            <ul style="margin-left: 36pt">
              <li>
                <div style="background: white">
                </div>
                
                <p>
                  <a href="#wp1058069"><span style="font-size: 10pt; color: #0076cc; font-family: 宋体; text-decoration: underline">计时器的生命周期</span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span></li> </ul> 
                  
                  <li>
                    <div style="background: white">
                      <a href="#wp1058097"><span style="font-size: 10pt; color: #0076cc; font-family: 宋体; text-decoration: underline">实现和配置作业调度程序</span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span>
                    </div>
                  </li>
                  
                  <li>
                    <div style="background: white">
                      <a href="#wp1058112"><span style="font-size: 10pt; color: #0076cc; font-family: 宋体; text-decoration: underline">不支持的方法和接口</span></a><span style="font-size: 10pt; color: black; font-family: verdana"> </span>
                    </div></p> 
                    
                    <p style="background: white">
                      <span style="font-size: 23pt; color: black"><span style="font-family: 宋体"><a name="wp1058069">计时器的生命周期</a><span style="font-family: arial"> </span></span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058070">在应用程序中实现</a><span style="font-family: verdana"> commonj.timer API </span><span style="font-family: 宋体">时，可以为计时器配置两种可能的生命周期。</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <ul style="margin-left: 36pt">
                      <li>
                        <div style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058071">本地计时器</a><span style="font-family: verdana"> </span></span>
                        </div>
                        
                        <p style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058072">本地计时器在单个服务器</a><span style="font-family: verdana"> JVM </span><span style="font-family: 宋体">中调度，并且这些计时器在它们整个生命期中都是在此</span><span style="font-family: verdana"> JVM </span><span style="font-family: 宋体">中进行处理。只要</span><span style="font-family: verdana"> JVM </span><span style="font-family: 宋体">运行，计时器就将一直运行；而当</span><span style="font-family: verdana"> JVM </span><span style="font-family: 宋体">退出时，计时器将出现故障。在服务器启动后，应用程序负责重新调度计时器。</span><span style="font-family: verdana"> </span></span>
                        </p>
                        
                        <p style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058078">此为</a><span style="font-family: verdana"> commonj.timers </span><span style="font-family: 宋体">的基本实现，其描述见</span><a href="#wp1057981"><span style="color: #0076cc; text-decoration: underline">计时器</span></a></span><span style="font-family: verdana; text-decoration: underline"> API </span><span style="color: #0076cc"><span style="font-family: 宋体"><span style="text-decoration: underline">概述</span><span style="color: black">。</span></span><span style="font-family: verdana"> </span></span>
                        </p>
                      </li>
                    </ul>
                  </li>
                  
                  <li>
                    <div style="background: white">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"><a name="wp1058080">群集范围的计时器</a><span style="font-family: verdana"> </span></span></span> </p> 
                      
                      <p style="background: white">
                        <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058081">群集范围的计时器了解包含群集中每一服务器的其他</a><span style="font-family: verdana"> JVM</span><span style="font-family: 宋体">，因此能执行负载平衡和故障转移。群集范围计时器的生命周期不与创建它的服务器绑定在一起，但是在群集的整个生命周期继续发挥作用。只要还有一个群集成员处于活动状态，计时器就会继续发挥作用。此功能称为作业调度程序。</span><span style="font-family: verdana"> </span></span>
                      </p></p>
                    </div>
                    
                    <p style="background: white">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1059065">每一计时器有其自己的优缺点。本地计时器能以短得多的作业处理时间间隔处理作业。由于群集有持久性要求，因此作业调度程序不能如此精确地处理作业。另一方面，作业调度程序更适合于在即使创建任务的初始服务器出现故障的情况下也必须执行的任务。</a><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 23pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058097">实现和配置作业调度程序</a><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058098">此部分将简述在应用程序中实现作业调度程序的基本过程以及配置</a><span style="font-family: verdana"> WebLogic Server </span><span style="font-family: 宋体">环境以利用作业调度程序的基本过程。</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 18pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058100">数据库配置</a><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058101">为了维持持久性，并使计时器支持群集，作业调度程序需要数据库连接。作业调度程序功能与服务器迁移支持相同的数据库供应商和版本。</a><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1059049">为方便起见，可与会话持久性、服务器迁移等使用相同的数据库。</a><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058102">在数据库中，必须基于以下模式创建一个称为</a><span style="font-family: verdana"> WEBLOGIC_TIMERS </span><span style="font-family: 宋体">的表：</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1060424">CREATE TABLE WEBLOGIC_TIMERS ( <br />&#160; TIMER_ID VARCHAR2(100) NOT NULL, <br />&#160; LISTENER BLOB NOT NULL, <br />&#160; START_TIME NUMBER NOT NULL, <br />&#160; INTERVAL NUMBER NOT NULL, <br />&#160; TIMER_MANAGER_NAME VARCHAR2(100) NOT NULL, <br />&#160; DOMAIN_NAME VARCHAR2(100) NOT NULL, <br />&#160; CLUSTER_NAME VARCHAR2(100) NOT NULL, <br />&#160; CONSTRAINT SYS_C00323062 PRIMARY KEY(TIMER_ID, CLUSTER_NAME, DOMAIN_NAME) <br />) </a>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 18pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058104">数据源配置</a><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058105">在创建了采用所需模式的表之后，必须定义一个可在群集配置内引用的数据源。只有为</a><span style="font-family: verdana"> Cluster MBean </span><span style="font-family: 宋体">的</span><span style="font-family: verdana"> DataSourceForJobScheduler </span><span style="font-family: 宋体">特性定义了有效数据源后，才能使用作业调度程序功能。您可以在</span><span style="font-family: verdana"> WebLogic Server </span><span style="font-family: 宋体">管理控制台对此进行配置。</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058106">以下的代码摘自</a><span style="font-family: verdana"> config.xml</span><span style="font-family: 宋体">，用于说明对此进行定义的方法：</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058107"><domain> <br />&#8230; <br /><cluster> <br />&#160; <name>Cluster-0</name> <br />&#160; <multicast-address>239.192.0.0</multicast-address> <br />&#160; <multicast-port>7466</multicast-port> <br />&#160; <data-source-for-job-scheduler>JDBC Data&#160;&#160;&#160;&#160; Source-0</data-source-for-job-scheduler> <br /></cluster> <br />&#8230; <br /><jdbc-system-resource> <br />&#160; <name>JDBC Data Source-0</name> <br />&#160; <target>myserver,server-0</target> <br />&#160; <descriptor-file-name>jdbc/JDBC_Data_Source-0-3407-jdbc.xml</descriptor-&#160;&#160;&#160; file-name> <br /></jdbc-system-resource> <br /></domain> </a>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 18pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058108">作业调度程序中的</a><span style="font-family: arial"> JNDI </span><span style="font-family: 宋体">访问</span><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058109">与常规</a><span style="font-family: verdana"> commonj.timer API </span><span style="font-family: 宋体">相比，在群集计时器中执行</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找的过程有所不同。下面的代码段说明如何将</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找强制转换成</span><span style="font-family: verdana"> TimerManager</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: courier new"></span><a name="wp1058110">InitialContext ic = new InitialContext(); <br />commonj.timers.TimerManager jobScheduler =(common.timers.TimerManager)ic.lookup <br />&#160;&#160; ("weblogic.JobScheduler"); <br />commonj.timers.TimerListener timerListener = new MySerializableTimerListener(); <br />jobScheduler.schedule(timerListener, 0, 30*1000); <br />// </a><span style="font-family: 宋体">每</span><span style="font-family: courier new"> 30 </span><span style="font-family: 宋体">秒执行一次此作业</span><span style="font-family: courier new"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 23pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058112">不支持的方法和接口</a><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058113">作业调度程序环境并非支持</a><span style="font-family: verdana"> commonj.timer API </span><span style="font-family: 宋体">的所有方法和接口。不支持下列方法和接口：</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <ul style="margin-left: 36pt">
                      <li>
                        <div style="background: white">
                          <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058114">CancelTimerListener</a><span style="font-size: 10pt"><span style="font-family: verdana">&#160;</span><span style="font-family: 宋体">接口</span><span style="font-family: verdana"> </span></span></span>
                        </div>
                      </li>
                      
                      <li>
                        <div style="background: white">
                          <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058115">StopTimerListener</a><span style="font-size: 10pt"><span style="font-family: verdana">&#160;</span><span style="font-family: 宋体">接口</span><span style="font-family: verdana"> </span></span></span>
                        </div>
                      </li>
                      
                      <li>
                        <div style="background: white">
                          <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058116">TimerManager</a><span style="font-size: 10pt"><span style="font-family: verdana">&#160;</span><span style="font-family: 宋体">接口的下列方法：</span><span style="font-family: verdana"> </span></span></span>
                        </div>
                        
                        <ul>
                          <li>
                            <div style="background: white">
                              <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058117">suspend()</a><span style="font-size: 10pt; font-family: verdana"> </span></span>
                            </div>
                          </li>
                          
                          <li>
                            <div style="background: white">
                              <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058118">resume()</a><span style="font-size: 10pt; font-family: verdana"> </span></span>
                            </div>
                          </li>
                          
                          <li>
                            <div style="background: white">
                              <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058119">scheduleAtFixedRate()</a><span style="font-size: 10pt; font-family: verdana"> </span></span>
                            </div>
                          </li>
                          
                          <li>
                            <div style="background: white">
                              <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058120">stop()</a><span style="font-size: 10pt; font-family: verdana"> </span></span>
                            </div>
                          </li>
                          
                          <li>
                            <div style="background: white">
                              <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058121">waitForStop()</a><span style="font-size: 10pt; font-family: verdana"> </span></span>
                            </div>
                          </li>
                          
                          <li>
                            <div style="background: white">
                              <span style="color: black"><span style="font-size: 12pt; font-family: courier new"></span><a name="wp1058122">waitForSuspend()</a><span style="font-size: 10pt; font-family: verdana"> </span></span>
                            </div>
                          </li>
                        </ul>
                      </li>
                    </ul>
                    
                    <p style="background: white">
                      &#160;&#160;
                    </p>
                    
                    <p>
                      <img alt="" src="http://www.blogjava.net/images/blogjava_net/beansoft/021912_1923_API5.png" /><span style="font-size: 12pt; font-family: 宋体"> </span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 30pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058124">工作管理器</a><span style="font-family: arial"> API </span><span style="font-family: 宋体">的描述</span><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="color: black"><span style="font-size: 10pt"><span style="font-family: 宋体"></span><a name="wp1058125">工作管理器</a><span style="font-family: verdana"> (</span></span><span style="font-size: 12pt; font-family: courier new">commonj.work</span><span style="font-size: 10pt"><span style="font-family: verdana">) API </span><span style="font-family: 宋体">提供的接口允许应用程序在一个容器中并发地执行多个工作项。</span><span style="font-family: verdana"> </span></span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058126">实际上，此</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">就是</span><span style="font-family: verdana"> java.lang.Thread API </span><span style="font-family: 宋体">的容器管理替代方法。</span><span style="font-family: verdana">java.lang.Thread API </span><span style="font-family: 宋体">不适用于受管</span><span style="font-family: verdana"> Java EE </span><span style="font-family: 宋体">环境中承载的应用程序。在这样的环境中，工作管理器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">替代方法的效果更好，因为它允许容器全面查看和控制所有执行线程。</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <div>
                      <table style="background: white; border-collapse: collapse" border="0">
                        <colgroup> <col style="width: 72px" /> <col style="width: 510px" /></colgroup> <tr>
                          <td style="padding-right: 1px; padding-left: 1px; padding-bottom: 1px; padding-top: 1px">
                            <p style="margin-left: 12pt">
                              <span style="font-size: 10pt; color: black; font-family: 宋体"><strong><a name="wp1058127">注意：</a></strong></span>
                            </p>
                          </td>
                          
                          <td style="padding-right: 1px; padding-left: 1px; padding-bottom: 1px; padding-top: 1px" valign="middle">
                            <p style="margin-left: 12pt">
                              <span style="font-size: 10pt; color: black"><span style="font-family: 宋体">工作管理器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">不提供故障转移和持久性机制。如果受管服务器环境出现故障或关闭，则当前所有工作都将丢失。</span></span>
                            </p>
                          </td>
                        </tr>
                      </table>
                    </div>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 23pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058128">工作管理器接口</a><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058689">此部分概述工作管理器</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">中定义的接口。有关使用这些接口的详细信息，请参阅</span><span style="font-family: verdana">&#160;</span><a href="http://e-docs.bea.com/wls/docs100/javadocs/commonj/work/package-summary.html"><span style="color: #0076cc; text-decoration: underline">commonj.work package</span></a>&#160;</span><span style="font-family: 宋体">的</span><span style="font-family: verdana"> javadoc</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span>
                    </p></p> 
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"><a name="wp1058686">工作管理器</a><span style="font-family: verdana"> API </span><span style="font-family: 宋体">包含下列接口：</span><span style="font-family: verdana"> </span></span></span>
                    </p>
                    
                    <ul style="margin-left: 36pt">
                      <li>
                        <div style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: verdana"><strong></strong><a name="wp1058266">WorkManager</a> &#8211; </span><span style="font-family: 宋体">此接口提供一组用于调度要执行工作的调度方法。</span><span style="font-family: verdana"> </span></span>
                        </div>
                        
                        <p style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058367">系统管理员可在服务器级别定义</a><span style="font-family: verdana"> WorkManager</span><span style="font-family: 宋体">。</span><span style="font-family: verdana">WorkManager </span><span style="font-family: 宋体">实例通过执行</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">查找来获取。受管的环境可以支持多个</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">实例。请参阅</span><span style="font-family: verdana">"WebLogic JNDI </span><span style="font-family: 宋体">编程</span><span style="font-family: verdana">"</span><span style="font-family: 宋体">。您在部署期间将</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">配置为</span><span style="font-family: verdana"> resource-ref</span><span style="font-family: 宋体">。请参阅</span><a href="#wp1058134"><span style="color: #0076cc; text-decoration: underline">工作管理器部署</span></a>。</span><span style="font-family: verdana"> </span>
                        </p>
                        
                        <p style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"><a name="wp1058539">每个</a><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">实例在应用程序级别返回一个</span><span style="font-family: verdana"> WorkItem</span><span style="font-family: 宋体">。有关在应用程序中实现</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">的详细信息，请参阅</span><a href="http://e-docs.bea.com/wls/docs100/javadocs/commonj/work/WorkManager.html"></a><span style="color: #0076cc"><span style="font-family: verdana">&#160;<span style="text-decoration: underline">WorkManager</span><span style="color: black"> javadocs</span></span><span style="font-family: 宋体">。</span><span style="color: black; font-family: verdana"> </span></span></span></span>
                        </p>
                      </li>
                      
                      <li>
                        <div style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: verdana"><strong></strong><a name="wp1058540">Work</a> &#8211; </span><span style="font-family: 宋体">通过此接口，您可以异步运行应用程序代码。通过创建实现此接口的类，您可以创建可通过调度在特定的时间或定义的间隔运行的代码块。换句话说，此为在工作管理器</span><span style="font-family: verdana"> API </span><span style="font-family: 宋体">中处理的</span><span style="font-family: verdana">"</span><span style="font-family: 宋体">工作</span><span style="font-family: verdana">"</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
                        </div>
                      </li>
                      
                      <li>
                        <div style="background: white">
                          <span style="color: black"><span style="font-size: 10pt"><span style="font-family: verdana"><strong></strong><a name="wp1058271">WorkItem</a> &#8211; </span><span style="font-family: 宋体">在将</span><span style="font-family: verdana">&#160;</span></span><span style="font-size: 12pt; font-family: courier new">Work</span><span style="font-size: 10pt"><span style="font-family: verdana">&#160;</span><span style="font-family: 宋体">实例提交给</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">后，</span><span style="font-family: verdana">WorkManager </span><span style="font-family: 宋体">将返回一个</span><span style="font-family: verdana"> WorkItem</span><span style="font-family: 宋体">。此</span><span style="font-family: verdana"> WorkItem </span><span style="font-family: 宋体">用于确定整个</span><span style="font-family: verdana"> Work </span><span style="font-family: 宋体">实例的状态。</span><span style="font-family: verdana"> </span></span></span>
                        </div>
                      </li>
                      
                      <li>
                        <div style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: verdana"><strong></strong><a name="wp1058653">WorkListener</a> &#8211; WorkListener </span><span style="font-family: 宋体">接口是一个回调接口，它在</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">与</span><span style="font-family: verdana"> Work </span><span style="font-family: 宋体">实例中定义的调度工作之间建立通信。</span><span style="font-family: verdana"> </span></span>
                        </div>
                        
                        <p style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058661">可以使用</a><span style="font-family: verdana"> WorkListener </span><span style="font-family: 宋体">确定</span><span style="font-family: verdana"> Work </span><span style="font-family: 宋体">项的当前状态。有关详细信息，请参阅</span><a href="http://e-docs.bea.com/wls/docs100/javadocs/commonj/work/WorkListener.html"></a><span style="color: #0076cc"><span style="font-family: verdana">&#160;<span style="text-decoration: underline">WorkListener</span><span style="color: black"> javadocs</span></span><span style="font-family: 宋体">。</span><span style="color: black; font-family: verdana"> </span></span></span>
                        </p>
                      </li>
                    </ul>
                    
                    <div style="margin-left: 36pt">
                      <table style="border-collapse: collapse" border="0">
                        <colgroup> <col style="width: 72px" /> <col style="width: 462px" /></colgroup> <tr>
                          <td style="padding-right: 1px; padding-left: 1px; padding-bottom: 1px; padding-top: 1px">
                            <p>
                              <span style="font-size: 10pt; color: black; font-family: 宋体"><strong><a name="wp1058993">注意：</a></strong></span>
                            </p>
                          </td>
                          
                          <td style="padding-right: 1px; padding-left: 1px; padding-bottom: 1px; padding-top: 1px" valign="middle">
                            <p style="margin-left: 12pt">
                              <span style="font-size: 10pt; color: black"><span style="font-family: verdana">WorkListener </span><span style="font-family: 宋体">实例总与通过</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">调度</span><span style="font-family: verdana"> Work </span><span style="font-family: 宋体">的初始线程在同一个</span><span style="font-family: verdana"> JVM </span><span style="font-family: 宋体">中执行。</span></span>
                            </p>
                          </td>
                        </tr>
                      </table>
                    </div>
                    
                    <ul style="margin-left: 36pt">
                      <li>
                        <div style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: verdana"><strong></strong><a name="wp1058656">WorkEvent</a> &#8211; </span><span style="font-family: 宋体">在</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">处理</span><span style="font-family: verdana"> Work </span><span style="font-family: 宋体">时，会将</span><span style="font-family: verdana"> WorkEvent </span><span style="font-family: 宋体">发送给</span><span style="font-family: verdana"> WorkListener</span><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span>
                        </div>
                      </li>
                      
                      <li>
                        <div style="background: white">
                          <span style="font-size: 10pt; color: black"><span style="font-family: verdana"><strong></strong><a name="wp1058633">RemoteWorkItem</a> &#8211; RemoteWorkItem </span><span style="font-family: 宋体">接口是</span><span style="font-family: verdana"> WorkItem </span><span style="font-family: 宋体">接口的扩展，可用于在远程执行工作。通过此接口，可序列化工作可以在群集中的任何成员上执行。</span><span style="font-family: verdana"> </span></span>
                        </div>
                      </li>
                    </ul>
                    
                    <p style="background: white">
                      <span style="font-size: 23pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058134">工作管理器部署</a><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="color: black"><span style="font-size: 10pt"><span style="font-family: 宋体"></span><a name="wp1058135">在适当部署描述符中通过</a><span style="font-family: verdana"> resource-ref </span><span style="font-family: 宋体">在服务器级别定义工作管理器。在其他描述符中可以是</span><span style="font-family: verdana">&#160;</span></span><span style="font-size: 12pt; font-family: courier new">web.xml</span><span style="font-size: 10pt"><span style="font-family: 宋体">或</span><span style="font-family: verdana">&#160;</span></span><span style="font-size: 12pt; font-family: courier new">ejb-jar.xml</span><span style="font-size: 10pt"><span style="font-family: 宋体">。</span><span style="font-family: verdana"> </span></span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058738">下面的部署描述符片段说明如何配置</a><span style="font-family: verdana"> WorkManager</span><span style="font-family: 宋体">：</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black; font-family: courier new"> <br /></span><a name="wp1058743"> <br /><resource-ref> <br />&#160;&#160; <res-ref-name>wm/MyWorkManager</res-ref-name> <br />&#160;&#160; <res-type>commonj.work.WorkManager</res-type> <br />&#160;&#160; <res-auth>Container</res-auth> <br />&#160;&#160; <res-sharing-scope>Shareable</res-sharing-scope> <br /></resource-ref> <br />&#8230; </a>
                    </p>
                    
                    <div>
                      <table style="background: white; border-collapse: collapse" border="0">
                        <colgroup> <col style="width: 74px" /> <col style="width: 508px" /></colgroup> <tr>
                          <td style="padding-right: 1px; padding-left: 1px; padding-bottom: 1px; padding-top: 1px">
                            <p style="margin-left: 12pt">
                              <span style="font-size: 10pt; color: black; font-family: 宋体"><strong><a name="wp1058824">注意：</a></strong></span>
                            </p>
                          </td>
                          
                          <td style="padding-right: 1px; padding-left: 1px; padding-bottom: 1px; padding-top: 1px" valign="middle">
                            <p style="margin-left: 12pt">
                              <span style="color: black"><span style="font-size: 10pt"><span style="font-family: 宋体">建议您为</span><span style="font-family: verdana"> WorkManager </span><span style="font-family: 宋体">对象的</span><span style="font-family: verdana"> JNDI </span><span style="font-family: 宋体">名称空间使用前缀</span><span style="font-family: verdana">&#160;</span></span><span style="font-size: 12pt; font-family: courier new">java:comp/env/wm</span><span style="font-size: 10pt; font-family: 宋体">。</span></span>
                            </p>
                          </td>
                        </tr>
                      </table>
                    </div>
                    
                    <p style="background: white; margin-left: 12pt">
                      &#160;&#160;
                    </p>
                    
                    <p>
                      <img alt="" src="http://www.blogjava.net/images/blogjava_net/beansoft/021912_1923_API6.png" /><span style="font-size: 12pt; font-family: 宋体"> </span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 30pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058139">工作管理器示例</a><span style="font-family: arial"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black"><span style="font-family: 宋体"></span><a name="wp1058142">此部分的工作代码示例在</a><span style="font-family: verdana"> HTTP Servlet </span><span style="font-family: 宋体">中使用</span><span style="font-family: verdana"> CommonJ </span><span style="font-family: 宋体">工作管理器。</span><span style="font-family: verdana"> </span></span>
                    </p>
                    
                    <p style="background: white; margin-left: 12pt">
                      <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058143">import java.io.IOException; <br />import java.io.PrintWriter; <br />import javax.servlet.http.HttpServlet; <br />import javax.servlet.http.HttpServletRequest; <br />import javax.servlet.http.HttpServletResponse; <br />import javax.naming.InitialContext; <br />import javax.naming.NamingException; </p> 
                      
                      <p>
                        import weblogic.work.ExecuteThread; <br />import commonj.work.WorkManager; <br />import commonj.work.Work; <br />import commonj.work.WorkException;
                      </p>
                      
                      <p>
                        public class HelloWorldServlet extends HttpServlet { </a>
                      </p>
                      
                      <p style="background: white; margin-left: 12pt">
                        <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058144">&#160;&#160; public void service(HttpServletRequest req, HttpServletResponse res) <br />&#160;&#160;&#160;&#160;&#160; throws IOException <br />&#160;&#160; { <br />&#160;&#160;&#160;&#160;&#160; res.setContentType("text/html"); <br />&#160;&#160;&#160;&#160;&#160; PrintWriter out = res.getWriter(); </p> 
                        
                        <p>
                          &#160;&#160;&#160;&#160;&#160; try { <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; InitialContext ic = new InitialContext(); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("## [servlet] executing in: " + <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; ((ExecuteThread)Thread.currentThread()).getWorkManager() <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; .getName()); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; WorkManager wm = (WorkManager)ic.lookup <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; ("java:comp/env/foo-servlet"); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("## got Java EE work manager !!!!"); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; wm.schedule(new Work(){ <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; public void run() { <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; ExecuteThread th = (ExecuteThread) Thread.currentThread(); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println("## [servlet] self-tuning workmanager: " + <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; th.getWorkManager().getName()); <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; } <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; public void release() {} </a>
                        </p>
                        
                        <p style="background: white; margin-left: 12pt">
                          <span style="font-size: 10pt; color: black"><span style="font-family: courier new"></span><a name="wp1058145">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; public boolean isDaemon() {return false;} <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; }); <br />} <br />catch (NamingException ne) { <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; ne.printStackTrace();} </p> 
                          
                          <p>
                            catch (WorkException e) { <br />&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; e.printStackTrace(); <br />}
                          </p>
                          
                          <p>
                            out.println("<h4>Hello World!</h4>"); <br />// </a><span style="font-family: 宋体">不要关闭输出流</span><span style="font-family: courier new"> &#8211; </span><span style="font-family: 宋体">而是启用</span><span style="font-family: courier new"> servlet </span><span style="font-family: 宋体">引擎关闭输出流</span><span style="font-family: courier new"> <br />// </span><span style="font-family: 宋体">以实现更佳性能。</span><span style="font-family: courier new"> <br />System.out.println("finished execution");} </span></span>
                          </p>
                          
                          <p style="background: white; margin-left: 12pt">
                            <span style="font-size: 10pt; color: black; font-family: courier new"></span><a name="wp1058146">} </a>
                          </p></p> </li> 
                          
                          <p>
                            转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2012/02/19/%e8%ae%a1%e6%97%b6%e5%99%a8%e5%92%8c%e5%b7%a5%e4%bd%9c%e7%ae%a1%e7%90%86%e5%99%a8-api-commonj-%e7%bc%96%e7%a8%8b%e4%ba%ba%e5%91%98%e6%8c%87%e5%8d%97/">计时器和工作管理器 API (CommonJ) 编程人员指南</a>
                          </p>