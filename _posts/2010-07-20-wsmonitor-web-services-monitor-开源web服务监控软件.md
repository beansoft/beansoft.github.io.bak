---
id: 392
title: 'wsmonitor (Web Services Monitor) &#8211; 开源Web服务监控软件'
date: 2010-07-20T13:51:28+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=392
permalink: '/2010/07/20/wsmonitor-web-services-monitor-%e5%bc%80%e6%ba%90web%e6%9c%8d%e5%8a%a1%e7%9b%91%e6%8e%a7%e8%bd%af%e4%bb%b6/'
original_post_id:
  - "392"
views:
  - "5712"
categories:
  - SOA/WebService
tags:
  - Monitor
  - WebService
---
[https://wsmonitor.dev.java.net/](https://wsmonitor.dev.java.net/ "https://wsmonitor.dev.java.net/")

wsmonitor

Web services Message Monitoring Tool 

  * **Licenses:** Dual license consisting of the [CDDL v1.0 and GPL v2](https://glassfish.dev.java.net/public/CDDL+GPL.html). 
  * **Governance:** [Same as Project GlassFish](https://glassfish.dev.java.net/public/GovernancePolicy.html)

__

[![](https://wsmonitor.dev.java.net/images/visitor.gif)](https://wsmonitor.dev.java.net/meet/index.html)   
[](https://wsmonitor.dev.java.net/meet/index.html) 

Meet Wsmonitor

Find out what is Wsmonitor and get started.</p> 

[![](https://wsmonitor.dev.java.net/images/user.gif)](https://wsmonitor.dev.java.net/use/index.html)   
[](https://wsmonitor.dev.java.net/use/index.html) 

Use Wsmonitor

See how to get more out of Wsmonitor.</p> 

[![](https://wsmonitor.dev.java.net/images/developer.gif)](https://wsmonitor.dev.java.net/extend/index.html)   
[](https://wsmonitor.dev.java.net/extend/index.html) 

Extend Wsmonitor

Learn how to build Wsmonitor or extend Wsmonitor by writing plugins.

<font color="#669966"></font></p> 

Stable Release

  1. [Download](https://wsmonitor.dev.java.net/servlets/ProjectDocumentList?folderID=5758&expandFolder=5758&folderID=5758) the distribution (download the latest version). 
  2. [JDK 1.5.0](http://java.sun.com/javase/downloads/index.jsp) or later is required. Install by giving the following command:   
    `java -jar wsmonitor-installer-XX.jar`   
    where `XX` is the version number of the tool. This will present a dialog box asking you to accept the license. Once accepted, it will extract the tool in "wsmonitor" directory in your current directory. All scripts are in `wsmonitor/bin` directory and can be invoked from any directory. 
  3. Invoke the tool by giving the following command:   
    `wsmonitor/bin/wsmonitor.[bat | sh]`   
    This start the tool listening at `localhost:4040` and forwarding to `localhost:8080`. 
  4. To invoke with a config file specifying non-default port forwards, use the following command:   
    `wsmonitor/bin/wsmonitor.[bat | sh] config.xml`
  5. To invoke the tool in verbose, use the following command:   
    `wsmonitor/bin/wsmonitor.[bat | sh] -verbose`

&#160;

## Overview

wsmonitor (Web Services Monitor) is a light-weight SOAP and HTTP traffic monitor. This tool intercepts and logs the SOAP messages and HTTP headers between a sender and a receiver and displays them nicely formatted in a graphical user interface. 

  * **Licenses:** Dual license consisting of the [CDDL v1.0 and GPL v2](https://glassfish.dev.java.net/public/CDDL+GPL.html). 
  * **Governance:** [Same as Project GlassFish](https://glassfish.dev.java.net/public/GovernancePolicy.html)

## 

## How does it work ?

The tool uses [port-forwarding](http://en.wikipedia.org/wiki/Port_forwarding) to capture the traffic. In simple language, when the tool is started it listens on `listenPort` port on localhost and brings up a display window. A sender originally sending request to `http://targetHost:targetPort/somepath` now sends the request to `http://localhost:listenPort/somepath`. The wsmonitor then forwards the request received at `localhost:listenPort` to `targetHost:targetPort`., without any alteration of the message. In between, it captures all the inbound and outbound SOAP and HTTP traffic and displays in a nicely formatted way in the wsmonitor window. 

The wsmonitor listen port, target host and target port are specified in an XML-based configuration file. In the absence of this configuration file, a default value of "4040" for listen port, "localhost" for target host, "8080" for target port is assumed. A sample config file, along with it&#8217;s schema, is available in the `etc` directory. Each port forward opens up as a new tab on the wsmonitor display window.

The name "wsmonitor" is aligned with [wsimport](https://jax-ws.dev.java.net/jax-ws-20-fcs/docs/wsimport.html) and [wsgen](https://jax-ws.dev.java.net/jax-ws-20-fcs/docs/wsgen.html) tools available in [JAX-WS](http://jax-ws.dev.java.net/). Even though the name is aligned with JAX-WS tools, this tool can be used with any Web services stack.</p> 

## <a name="features"></a>Key Features

  * Easy to use
  * Light weight
  * Displays XML and Fast Infoset SOAP messages
  * Separate tabs for SOAP and HTTP traffic
  * Transport-level data capture

&#160;

&#160;

#### How can I use it ?

The wsmonitor workspace is undergoing [extreme makeover](https://wsmonitor.dev.java.net/use/makeover.html). You can try the [bleeding edge build](https://wsmonitor.dev.java.net/servlets/ProjectDocumentList?folderID=9496&expandFolder=9496&folderID=5758) or [stable release](https://wsmonitor.dev.java.net/servlets/ProjectDocumentList?folderID=5758&expandFolder=5758&folderID=5758).&#160; Bugs will only be fixed in the bleeding edge build. So before filing an issue, please try it with the bleeding edge build.   
Let&#8217;s get started! 

  1. Download and Start Wsmonitor from [Bleeding Edge](https://wsmonitor.dev.java.net/use/bleeding-edge.html) or [Stable Release](https://wsmonitor.dev.java.net/use/stable-release.html). 
  2. Develop a Web service using NetBeans and deploy on GlassFish as described in [screencast #ws7](http://blogs.sun.com/arungupta/entry/screncast_ws7_secure_and_reliable). 
  3. Override the endpoint address for the generated client by following [these instructions](https://metro.dev.java.net/guide/How_to_invoke_and_endpoint_by_overriding_endpoint_address_in_the_WSDL.html). The only difference in the new endpoint address is that the port number is 4040 instead of 8080.

That&#8217;s it, now every SOAP request message sent and response message received by this client is displayed in the wsmonitor console. The wsmonitor console dumps showing HTTP headers and request/response messages using SOAP and Fast Infoset are shown below. 

##### HTTP headers for a SOAP Message![HTTP headers for a SOAP Message captured with Wsmonitor](https://wsmonitor.dev.java.net/images/soap-http.jpg "HTTP headers for a SOAP Message captured with Wsmonitor")

##### SOAP Request and Response Message![SOAP Request and Response Message captured with Wsmonitor](https://wsmonitor.dev.java.net/images/soap-request.jpg "SOAP Request and Response Message captured with Wsmonitor")

##### 

##### HTTP Headers for a FastInfoset Message![HTTP Headers for a FastInfoset Message captured using Wsmonitor](https://wsmonitor.dev.java.net/images/fast-http.jpg "HTTP Headers for a FastInfoset Message captured using Wsmonitor")

##### 

##### FastInfoset Request and Response Message![FastInfoset Request and Response Message captured using Wsmonitor](https://wsmonitor.dev.java.net/images/fast-request.jpg "FastInfoset Request and Response Message captured using Wsmonitor")

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [wsmonitor (Web Services Monitor) &#8211; 开源Web服务监控软件](http://www.beansoft.biz/2010/07/20/wsmonitor-web-services-monitor-%e5%bc%80%e6%ba%90web%e6%9c%8d%e5%8a%a1%e7%9b%91%e6%8e%a7%e8%bd%af%e4%bb%b6/)