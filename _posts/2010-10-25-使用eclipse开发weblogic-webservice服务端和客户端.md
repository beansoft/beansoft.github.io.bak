---
id: 1343
title: 使用Eclipse开发WebLogic WebService服务端和客户端
date: 2010-10-25T18:33:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1343
permalink: '/2010/10/25/%e4%bd%bf%e7%94%a8eclipse%e5%bc%80%e5%8f%91weblogic-webservice%e6%9c%8d%e5%8a%a1%e7%ab%af%e5%92%8c%e5%ae%a2%e6%88%b7%e7%ab%af/'
views:
  - "22247"
original_post_id:
  - "1343"
image: /wp-content/uploads/2012/09/image4.png
categories:
  - SOA/WebService
  - WebLogic
---
本文内容是 [http://download.oracle.com/docs/cd/E14571\_01/web.1111/e13758/use\_cases.htm](http://download.oracle.com/docs/cd/E14571_01/web.1111/e13758/use_cases.htm) 的Eclipse版本, 环境 Windows XP, WebLogic 10.3, JDK 1.6.

**作者: 刘长炯 日期: 2010-10-25**

# **[开发前的准备工作]**

1. 创建一个Domain, 记得要选中对Web Service的支持, 更多详细信息可参考: <http://download.oracle.com/docs/cd/E14571_01/web.1111/e13758/setenv.htm#CACBAAGE>.

选择 **「开始」菜单\程序\Oracle WebLogic\WebLogic Server 11gR1\Tools\Configuration Wizard** , 启动 Fussion Middleware Configuration Wizard.

第一页欢迎页, 选择 Cre**ate a new WebLogic domain**;

第二页, 选择 **Generate a domain configured automatically to support the following products:**

复选下列这项:

**WebLogic Advanced Web Services for JAX-WS Extension**

然后一路选择Next, 这里为了简化只包含了一个AdminServer, 用户名和密码分别为 weblogic/weblogic1.

创建Domain完毕后, 启动此WebLogic, 并进入控制台 <http://localhost:7001/console>.

2. 启动Eclipse(使用纯Eclipse即可, 例如[Eclipse IDE for Java Developers](http://eclipse.org/downloads/packages/eclipse-ide-java-developers/heliossr1)).

选择菜单项 **Window -> Preferences**, 展开节点Ant > Runtime, 然后在 Classpath 标签页的 Global Entries 下添加如下几个jar包(点击右侧按钮 Add External JARs&#8230;进行安装):

$JAVA_HOME\lib\tools.jar

$BEA\_HOME\wlserver\_10.3\server\lib\weblogic.jar

$BEA\_HOME\wlserver\_10.3\server\lib\wseeclient.jar,

如下图所示:

&#160; <img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image4.png" width="773" height="236" />

&#160;

至此开发环境已经准备完毕.

&#160;

# **[开发服务端]**

下面来开发完成一个最简单的Web Service.

使用Eclipse新建一个Java项目, 名称为**wls_hellows**, 此项目的JDK必须选择**JDK 1.6**, 否则项目可能会出现问题, 例如<font color="#ff0000"><strong>无法编译</strong></font>.

在src目录下新建包**examples.webservices.hello_world**.

在此包下新建类文件HelloWorldImpl, 代码如下所示:

<div id="codeSnippetWrapper">
  <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">package</span> examples.webservices.hello_world;<br /><br /><span style="color: #008000">// Import the @WebService annotation</span><br /><span style="color: #0000ff">import</span> javax.jws.WebService;<br /><br />@WebService(name = <span style="color: #006080">"HelloWorldPortType"</span>, serviceName = <span style="color: #006080">"HelloWorldService"</span>)<br /><span style="color: #008000">/**</span><br /><span style="color: #008000"> * This JWS file forms the basis of simple Java-class implemented WebLogic</span><br /><span style="color: #008000"> * Web Service with a single operation: sayHelloWorld</span><br /><span style="color: #008000"> * http://download.oracle.com/docs/cd/E14571_01/web.1111/e13758/use_cases.htm</span><br /><span style="color: #008000"> */</span><br /><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> HelloWorldImpl {<br />    <span style="color: #008000">// By default, all public methods are exposed as Web Services operation</span><br />    <span style="color: #0000ff">public</span> String sayHelloWorld(String message) {<br />        <span style="color: #0000ff">try</span> {<br />            System.out.println(<span style="color: #006080">"sayHelloWorld:"</span> + message);<br />        } <span style="color: #0000ff">catch</span> (Exception ex) {<br />            ex.printStackTrace();<br />        }<br /><br />        <span style="color: #0000ff">return</span> <span style="color: #006080">"Here is the message: '"</span> + message + <span style="color: #006080">"'"</span>;<br />    }<br />}</pre>
  
  <p>
    </div> 
    
    <div id="codeSnippetWrapper">
    </div>
    
    <p>
      然后在项目根目录下创建文件<strong>build.xml</strong>, 内容如下所示
    </p>
  </p>
  
  <div id="codeSnippetWrapper">
    <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><span style="color: #0000ff">&lt;</span><span style="color: #800000">project</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="webservices-hello_world"</span> <span style="color: #ff0000">default</span><span style="color: #0000ff">="all"</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #008000">&lt;!-- set global properties for this build --&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="wls.username"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="weblogic"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="wls.password"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="weblogic1"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="wls.hostname"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="localhost"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="wls.port"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="7001"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="wls.server.name"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="AdminServer"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="ear.deployed.name"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="helloWorldEar"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="example-output"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="output"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="ear-dir"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="${example-output}/helloWorldEar"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">property</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="clientclass-dir"</span> <span style="color: #ff0000">value</span><span style="color: #0000ff">="${example-output}/clientclasses"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">path</span> <span style="color: #ff0000">id</span><span style="color: #0000ff">="client.class.path"</span><span style="color: #0000ff">&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">pathelement</span> <span style="color: #ff0000">path</span><span style="color: #0000ff">="${clientclass-dir}"</span> <span style="color: #0000ff">/&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">pathelement</span> <span style="color: #ff0000">path</span><span style="color: #0000ff">="${java.class.path}"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">path</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">taskdef</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="jwsc"</span> <span style="color: #ff0000">classname</span><span style="color: #0000ff">="weblogic.wsee.tools.anttasks.JwscTask"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">taskdef</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="clientgen"</span> <span style="color: #ff0000">classname</span><span style="color: #0000ff">="weblogic.wsee.tools.anttasks.ClientGenTask"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">taskdef</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="wldeploy"</span> <span style="color: #ff0000">classname</span><span style="color: #0000ff">="weblogic.ant.taskdefs.management.WLDeploy"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">target</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="all"</span> <span style="color: #ff0000">depends</span><span style="color: #0000ff">="clean,build-service,deploy,client"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">target</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="clean"</span> <span style="color: #ff0000">depends</span><span style="color: #0000ff">="undeploy"</span><span style="color: #0000ff">&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">delete</span> <span style="color: #ff0000">dir</span><span style="color: #0000ff">="${example-output}"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">target</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">target</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="build-service"</span><span style="color: #0000ff">&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">jwsc</span> <span style="color: #ff0000">srcdir</span><span style="color: #0000ff">="src"</span> <span style="color: #ff0000">destdir</span><span style="color: #0000ff">="${ear-dir}"</span><span style="color: #0000ff">&gt;</span><br />            <span style="color: #0000ff">&lt;</span><span style="color: #800000">jws</span> <span style="color: #ff0000">file</span><span style="color: #0000ff">="examples/webservices/hello_world/HelloWorldImpl.java"</span> <span style="color: #ff0000">type</span><span style="color: #0000ff">="JAXWS"</span> <span style="color: #0000ff">/&gt;</span><br />        <span style="color: #0000ff">&lt;/</span><span style="color: #800000">jwsc</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">target</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">target</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="deploy"</span><span style="color: #0000ff">&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">wldeploy</span> <span style="color: #ff0000">action</span><span style="color: #0000ff">="deploy"</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="${ear.deployed.name}"</span> <span style="color: #ff0000">source</span><span style="color: #0000ff">="${ear-dir}"</span> <span style="color: #ff0000">user</span><span style="color: #0000ff">="${wls.username}"</span> <span style="color: #ff0000">password</span><span style="color: #0000ff">="${wls.password}"</span> <span style="color: #ff0000">verbose</span><span style="color: #0000ff">="true"</span> <span style="color: #ff0000">adminurl</span><span style="color: #0000ff">="t3://${wls.hostname}:${wls.port}"</span> <span style="color: #ff0000">targets</span><span style="color: #0000ff">="${wls.server.name}"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">target</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">target</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="undeploy"</span><span style="color: #0000ff">&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">wldeploy</span> <span style="color: #ff0000">action</span><span style="color: #0000ff">="undeploy"</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="${ear.deployed.name}"</span> <span style="color: #ff0000">failonerror</span><span style="color: #0000ff">="false"</span> <span style="color: #ff0000">user</span><span style="color: #0000ff">="${wls.username}"</span> <span style="color: #ff0000">password</span><span style="color: #0000ff">="${wls.password}"</span> <span style="color: #ff0000">verbose</span><span style="color: #0000ff">="true"</span> <span style="color: #ff0000">adminurl</span><span style="color: #0000ff">="t3://${wls.hostname}:${wls.port}"</span> <span style="color: #ff0000">targets</span><span style="color: #0000ff">="${wls.server.name}"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">target</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">target</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="client"</span><span style="color: #0000ff">&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">clientgen</span> <span style="color: #ff0000">wsdl</span><span style="color: #0000ff">="http://${wls.hostname}:${wls.port}/HelloWorldImpl/HelloWorldService?WSDL"</span> <span style="color: #ff0000">destDir</span><span style="color: #0000ff">="${clientclass-dir}"</span> <span style="color: #ff0000">packageName</span><span style="color: #0000ff">="examples.webservices.hello_world.client"</span> <span style="color: #ff0000">type</span><span style="color: #0000ff">="JAXWS"</span> <span style="color: #0000ff">/&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">javac</span> <span style="color: #ff0000">srcdir</span><span style="color: #0000ff">="${clientclass-dir}"</span> <span style="color: #ff0000">destdir</span><span style="color: #0000ff">="${clientclass-dir}"</span> <span style="color: #ff0000">includes</span><span style="color: #0000ff">="**/*.java"</span> <span style="color: #0000ff">/&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">javac</span> <span style="color: #ff0000">srcdir</span><span style="color: #0000ff">="src"</span> <span style="color: #ff0000">destdir</span><span style="color: #0000ff">="${clientclass-dir}"</span> <span style="color: #ff0000">includes</span><span style="color: #0000ff">="examples/webservices/hello_world/client/**/*.java"</span> <span style="color: #0000ff">/&gt;</span><br />    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">target</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;</span><span style="color: #800000">target</span> <span style="color: #ff0000">name</span><span style="color: #0000ff">="run"</span><span style="color: #0000ff">&gt;</span><br />        <span style="color: #0000ff">&lt;</span><span style="color: #800000">java</span> <span style="color: #ff0000">classname</span><span style="color: #0000ff">="examples.webservices.hello_world.client.Main"</span> <span style="color: #ff0000">fork</span><span style="color: #0000ff">="true"</span> <span style="color: #ff0000">failonerror</span><span style="color: #0000ff">="true"</span><span style="color: #0000ff">&gt;</span><br />            <span style="color: #0000ff">&lt;</span><span style="color: #800000">classpath</span> <span style="color: #ff0000">refid</span><span style="color: #0000ff">="client.class.path"</span> <span style="color: #0000ff">/&gt;</span><br />            <span style="color: #0000ff">&lt;</span><span style="color: #800000">arg</span> <span style="color: #ff0000">line</span><span style="color: #0000ff">="http://${wls.hostname}:${wls.port}/HelloWorldImpl/HelloWorldService"</span> <span style="color: #0000ff">/&gt;</span><br />        <span style="color: #0000ff">&lt;/</span><span style="color: #800000">java</span><span style="color: #0000ff">&gt;</span><br />    <span style="color: #0000ff">&lt;/</span><span style="color: #800000">target</span><span style="color: #0000ff">&gt;</span><br /><span style="color: #0000ff">&lt;/</span><span style="color: #800000">project</span><span style="color: #0000ff">&gt;</span><br /></pre>
    
    <p>
      </div> 
      
      <p>
        . 打开此文件, 在<strong>Outline</strong>视图中的<strong>all</strong>节点上(Ant的Target)右键点击<strong>Run As > Ant Build</strong>, 即可启动并完成下列几个操作:
      </p>
      
      <p>
        <img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image5.png" width="485" height="358" />
      </p>
      
      <p>
        clean 移除部署, 删除生成的临时文件
      </p>
      
      <p>
        build-service 编译服务
      </p>
      
      <p>
        deploy 部署生成的Web Service到WebLogic服务器
      </p>
      
      <p>
        client 生成并编译客户端文件
      </p>
      
      <p>
        , 正确运行后的一个输出如下所示:
      </p>
      
      <p>
        &#160;
      </p>
      
      <table border="1" cellspacing="0" cellpadding="2" width="400">
        <tr>
          <td valign="top" width="400">
            <p>
              Buildfile: E:\workspace\wls_hellows\build.xml<br /> <br />undeploy:
            </p>
            
            <p>
              [wldeploy] weblogic.Deployer -verbose -noexit -name helloWorldEar -targets AdminServer -adminurl t3://localhost:7001 -user weblogic -password ******** -undeploy
            </p>
            
            <p>
              [wldeploy] weblogic.Deployer invoked with options:&#160; -verbose -noexit -name helloWorldEar -targets AdminServer -adminurl t3://localhost:7001 -user weblogic -undeploy
            </p>
            
            <p>
              [wldeploy] <Oct 25, 2010 5:49:19 AM VET> <Info> <J2EE Deployment SPI> <BEA-260121> <Initiating undeploy operation for application, helloWorldEar [archive: null], to AdminServer .>
            </p>
            
            <p>
              [wldeploy] [Deployer:149001]No application named &#8216;helloWorldEar&#8217; exists for operation undeploy
            </p>
            
            <p>
              clean:
            </p>
            
            <p>
              build-service:
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] JWS: processing module /examples/webservices/hello_world/HelloWorldImpl
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] Parsing source files
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] Parsing source files
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] 1 JWS files being processed for module /examples/webservices/hello_world/HelloWorldImpl
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] JWS: E:\workspace\wls_hellows\src\examples\webservices\hello_world\HelloWorldImpl.java Validated.
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] Processing 1 JAX-WS web services&#8230;
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] warning: Annotation types without processors: [javax.xml.bind.annotation.XmlRootElement, javax.xml.bind.annotation.XmlAccessorType, javax.xml.bind.annotation.XmlType, javax.xml.bind.annotation.XmlElement]
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] 1 warning
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] Compiling 3 source files to C:\DOCUME~1\jackyl\LOCALS~1\Temp\_gwf3vm
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] Building jar: E:\workspace\wls_hellows\output\helloWorldEar\examples\webservices\hello_world\HelloWorldImpl.war
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] Created JWS deployment outputFile: E:\workspace\wls_hellows\output\helloWorldEar\examples\webservices\hello_world\HelloWorldImpl.war
            </p>
            
            <p>
              &#160;&#160;&#160;&#160; [jwsc] [EarFile] Application File : E:\workspace\wls_hellows\output\helloWorldEar\META-INF\application.xml
            </p>
            
            <p>
              [AntUtil.deleteDir] Deleting directory C:\DOCUME~1\jackyl\LOCALS~1\Temp\_gwf3vm
            </p>
            
            <p>
              deploy:
            </p>
            
            <p>
              [wldeploy] weblogic.Deployer -verbose -noexit -name helloWorldEar -source E:\workspace\wls_hellows\output\helloWorldEar -targets AdminServer -adminurl t3://localhost:7001 -user weblogic -password ******** -deploy
            </p>
            
            <p>
              [wldeploy] weblogic.Deployer invoked with options:&#160; -verbose -noexit -name helloWorldEar -source E:\workspace\wls_hellows\output\helloWorldEar -targets AdminServer -adminurl t3://localhost:7001 -user weblogic -deploy
            </p>
            
            <p>
              [wldeploy] <Oct 25, 2010 5:49:24 AM VET> <Info> <J2EE Deployment SPI> <BEA-260121> <Initiating deploy operation for application, helloWorldEar [archive: E:\workspace\wls_hellows\output\helloWorldEar], to AdminServer .>
            </p>
            
            <p>
              [wldeploy] Task 6 initiated: [Deployer:149026]deploy application helloWorldEar on AdminServer.
            </p>
            
            <p>
              [wldeploy] Task 6 completed: [Deployer:149026]deploy application helloWorldEar on AdminServer.
            </p>
            
            <p>
              [wldeploy] Target state: deploy completed on Server AdminServer
            </p>
            
            <p>
              [wldeploy]
            </p>
            
            <p>
              [wldeploy] Target Assignments:
            </p>
            
            <p>
              [wldeploy] + helloWorldEar&#160; AdminServer
            </p>
            
            <p>
              client:
            </p>
            
            <p>
              [clientgen]
            </p>
            
            <p>
              [clientgen] *********** jax-ws clientgen attribute settings ***************
            </p>
            
            <p>
              [clientgen]
            </p>
            
            <p>
              [clientgen] wsdlURI: <a href="http://localhost:7001/HelloWorldImpl/HelloWorldService?WSDL">http://localhost:7001/HelloWorldImpl/HelloWorldService?WSDL</a>
            </p>
            
            <p>
              [clientgen] packageName : examples.webservices.hello_world.client
            </p>
            
            <p>
              [clientgen] destDir : E:\workspace\wls_hellows\output\clientclasses
            </p>
            
            <p>
              [clientgen]
            </p>
            
            <p>
              [clientgen] *********** jax-ws clientgen attribute settings end ***************
            </p>
            
            <p>
              [clientgen] Consider using <depends>/<produces> so that wsimport won&#8217;t do unnecessary compilation
            </p>
            
            <p>
              [clientgen] parsing WSDL&#8230;
            </p>
            
            <p>
              [clientgen] generating code&#8230;
            </p>
            
            <p>
              [clientgen] compiling code&#8230;
            </p>
            
            <p>
              all:
            </p>
            
            <p>
              BUILD SUCCESSFUL
            </p>
            
            <p>
              Total time: 7 seconds
            </p>
          </td>
        </tr>
      </table>
      
      <p>
        . 至此, 整个Web Service的服务端已经开发部署完毕, 并可在WebLogic Console的Deployments下看到此应用.
      </p>
      
      <p>
        &#160;
      </p>
      
      <h1>
        <strong>[开发客户端]</strong>
      </h1>
      
      <p>
        接着开发一个Java客户端来调用此Web Service.
      </p>
      
      <p>
        刷新项目目录, 可以看到如下所示的目录结构:
      </p>
      
      <p>
        <img style="border-right-width: 0px; display: inline; border-top-width: 0px; border-bottom-width: 0px; border-left-width: 0px" title="image" border="0" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2010/10/image6.png" width="386" height="572" />
      </p>
      
      <p>
        可以看到已经自动生成了服务端代码(位于<strong>output/helloWorldEar</strong>下)和客户端骨架代码(基于JAX-WS), 让我们在<strong> output/clientclasses/examples/webservices/hello_world/clien</strong>t 目录下新建一个Java文件 <strong>Main.java</strong>:
      </p>
      
      <div id="codeSnippetWrapper">
        <pre style="border-bottom-style: none; text-align: left; padding-bottom: 0px; line-height: 12pt; border-right-style: none; background-color: #f4f4f4; margin: 0em; padding-left: 0px; width: 100%; padding-right: 0px; font-family: &#39;Courier New&#39;, courier, monospace; direction: ltr; border-top-style: none; color: black; font-size: 8pt; border-left-style: none; overflow: visible; padding-top: 0px" id="codeSnippet"><br /><span style="color: #0000ff">package</span> examples.webservices.hello_world.client; <br /><span style="color: #0000ff">import</span> javax.xml.namespace.QName; <br /><span style="color: #0000ff">public</span> <span style="color: #0000ff">class</span> Main { <br /> <span style="color: #0000ff">public</span> <span style="color: #0000ff">static</span> <span style="color: #0000ff">void</span> main(String[] <br />args) { <br /> <span style="color: #008000">// Take argument from </span><br />command-line <br /> HelloWorldService <br />service = <span style="color: #0000ff">new</span> HelloWorldService(); <br /><br /> HelloWorldPortType port = <br />service.getHelloWorldPortTypePort(); <br /><br /> String result = <br />port.sayHelloWorld(<span style="color: #006080">"Call webService from Java client test"</span>); <br /><br /> System.out.println(<span style="color: #006080">"result = "</span> + <br />result); <br /> } <br />}</pre>
        
        <p>
          </div> 
          
          <div id="codeSnippetWrapper">
          </div>
          
          <p>
            接着转向build.xml, 运行一次名为client的Ant target, 即可将此文件编译完毕. 最后运行名为run的Ant target, 则可以看到调用Web Service的完整输出如下:
          </p>
          
          <p>
            &#160;
          </p>
          
          <p>
            Buildfile: E:\workspace\wls_hellows\build.xml<br /> <br />run:
          </p>
          
          <p>
            &#160;&#160;&#160;&#160; [java] result = Here is the message: &#8216;Call webService from Java client test&#8217;
          </p>
          
          <p>
            BUILD SUCCESSFUL
          </p>
          
          <p>
            Total time: 2 seconds
          </p>
        </p>
        
        <p>
          . Not bad, 至此第一个简单的Web Service服务端和客户端已经开发完毕了.
        </p>
        
        <h1>
          [参考资料]
        </h1>
        
        <p>
          <a href="http://download.oracle.com/docs/cd/E14571_01/web.1111/e13758/use_cases.htm">http://download.oracle.com/docs/cd/E14571_01/web.1111/e13758/use_cases.htm</a>
        </p>
        
        <p>
          转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/10/25/%e4%bd%bf%e7%94%a8eclipse%e5%bc%80%e5%8f%91weblogic-webservice%e6%9c%8d%e5%8a%a1%e7%ab%af%e5%92%8c%e5%ae%a2%e6%88%b7%e7%ab%af/">使用Eclipse开发WebLogic WebService服务端和客户端</a>
        </p>