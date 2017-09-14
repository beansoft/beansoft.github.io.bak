---
id: 507
title: WebLogic Server 9 的 Web Service 编程之 JWS
date: 2010-08-05T22:56:54+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=507
permalink: '/2010/08/05/weblogic-server-9-%e7%9a%84-web-service-%e7%bc%96%e7%a8%8b%e4%b9%8b-jws-%e8%bd%ac%e8%87%aawlsfans/'
views:
  - "5925"
original_post_id:
  - "507"
image: /wp-content/uploads/2012/09/doc_nav_prev.gif
categories:
  - WebLogic
---
查看原始edoc: <http://www.beansoft.biz/weblogic/docs92/webserv/jws.html>

[英文对照](http://docs.oracle.com/cd/E13222_01/wls/docs92/webserv/jws.html)

<img alt="" src="http://www.beansoft.biz/global_resources/images/_.gif" width="1" height="1" />

[eDocs 首页](http://www.beansoft.biz/weblogic/docs92/index.html) >&#160; > [WebLogic Server 的 Web Service 编程](http://www.beansoft.biz/weblogic/docs92/webserv/index.html) > JWS 文件编程

### WebLogic Server 的 Web Service 编程

[<img border="0" alt="上一页" src="http://www.beansoft.biz/global_resources/images/doc_nav_prev.gif" />](http://www.beansoft.biz/weblogic/docs92/webserv/setenv.html) [<img border="0" alt="下一页" src="http://www.beansoft.biz/global_resources/images/doc_nav_next.gif" />](http://www.beansoft.biz/weblogic/docs92/webserv/advanced.html)  <img border="0" alt="" src="http://www.beansoft.biz/global_resources/images/doc_nav_dots.gif" />[<img border="0" alt="在新窗口中打开目录" src="http://www.beansoft.biz/global_resources/images/doc_nav_contents.gif" />](http://www.beansoft.biz/weblogic/docs92/webserv/) <del><a name="link_group_0"></a></del>

<a name="skipnav"><img border="0" alt="在此处开始内容" src="http://www.beansoft.biz/global_resources/images/_.gif" width="1" height="1" /></a>

### <del><a name="wp203459"></a></del>JWS 文件编程

<del><a name="wp198198"></a></del>下列部分提供有关实现 Web Service 的 JWS 文件编程的信息：

  * <del><a name="wp210936"></a></del>[JWS 文件和 JWS 批注的概述](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp209608)
  * <del><a name="wp221409"></a></del>[JWS 文件编程：Java 要求](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp220946)
  * <del><a name="wp210948"></a></del>[JWS 文件编程：典型步骤](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp212031)
  * <del><a name="wp216837"></a></del>[使用 JwsContext 访问有关 Web Service 的运行时信息](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp216814)
  * <del><a name="wp215810"></a></del>[是否要实现无状态会话 EJB？](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp215790)
  * <del><a name="wp210953"></a></del>[编写用户定义的 Java 数据类型](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp210057)
  * <del><a name="wp210963"></a></del>[引发异常](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp209620)
  * <del><a name="wp214590"></a></del>[从 JWS 文件调用另一 Web Service](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp214603)
  * <del><a name="wp224062"></a></del>[使用 JWS 批注和 API 编写其他杂项功能](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp223990)
  * <del><a name="wp210993"></a></del>[JWS 编程最佳实践](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp209992)

<hr noshade="noshade" />

#### <del><a name="wp209608"></a></del>JWS 文件和 JWS 批注的概述

<del><a name="wp210013"></a></del>编写 WebLogic Web Service 的一种方法是从头开始对标准 JSR-921 EJB 或 Java 类进行编码，然后手工生成其关联工件（部署描述符文件、WSDL 文件、用户定义数据类型的数据绑定工件等)。该过程难度较大且非常繁琐。BEA 建议利用新的 [JDK 5.0 metadata annotations](http://java.sun.com/developer/technicalArticles/releases/j2se15/) 功能，使用编程模型创建批注 Java 文件，再使用 Ant 任务将该文件编译为 Java 源代码，然后生成所有关联工件。

<del><a name="wp210015"></a></del>Java Web Service (JWS) 批注的文件是 Web Service 的核心。它包含确定 Web Service 行为方式的 Java 代码。JWS 文件是一个普通 Java 类文件，它使用 JDK 5.0 元数据批注指定 Web Service 的形状和特征。可在 JWS 文件中使用的 JWS 批注包括[Web Services Metadata for the Java Platform specification (JSR-181)](http://www.jcp.org/en/jsr/detail?id=181) 中定义的标准批注以及 WebLogic 特定的一组批注。

<del><a name="wp221119"></a></del>本主题是创建 Web Service 的迭代开发过程的一部分，如[从 Java 开始迭代开发 WebLogic Web Service：主要步骤](http://www.beansoft.biz/weblogic/docs92/webserv/setenv.html#wp209755)和[从 WSDL 文件开始迭代开发 WebLogic Web Service：主要步骤](http://www.beansoft.biz/weblogic/docs92/webserv/setenv.html#wp214341)中所述。本主题假设您已经创建 JWS 文件，现在希望向其中添加 JWS 批注。

<hr noshade="noshade" />

#### <del><a name="wp220946"></a></del>JWS 文件编程：Java 要求

<del><a name="wp220947"></a></del>在编写 JWS 文件时，必须遵守 [Web Services Metadata for the Java Platform JSR-181 specification](http://www.jcp.org/en/jsr/detail?id=181) 指定的一组要求。具体来说，实现 Web Service 的 Java 类：

  * <del><a name="wp220949"></a></del>必须是外部公共类，不得是最终类，也不得是抽象类。 
  * <del><a name="wp220950"></a></del>必须包含默认的公共构造方法。 
  * <del><a name="wp220951"></a></del>不得定义 `finalize()` 方法。 
  * <del><a name="wp220952"></a></del>必须至少包括一个类级别 `@WebService` JWS 批注，以指示 JWS 文件实现 Web Service。 
  * <del><a name="wp220953"></a></del>可以使用 `@WebService.endpointInterface` 批注引用服务端点接口。在这种情况下，假设服务端点接口存在，且不能在 JWS 文件中指定除 `@WebService.endpointInterface` 和 `@WebService.serviceName` 以外的 JWS 批注。 
  * <del><a name="wp221522"></a></del>如果 JWS 文件未实现服务端点接口，则除从 `java.lang.Object` 继承的方法外，所有公共方法都会公开为 Web Service 操作。通过使用 `@WebMethod` 批注明确指定将公开的公共方法，可以替代此行为。如果存在 `@WebMethod` 批注，则仅公开对其适用的方法。

<hr noshade="noshade" />

#### <del><a name="wp212031"></a></del>JWS 文件编程：典型步骤

<del><a name="wp221286"></a></del>下列部分描述如何在 JWS 文件中使用标准 ([JSR-181](http://www.jcp.org/en/jsr/detail?id=181)) 批注和 WebLogic 特定的批注来编写基本 Web Service 功能。批注用于 JWS 文件中的不同级别或不同目标。部分批注用在类级别，表明该批注应用于整个 JWS 文件。其他批注用于方法级别，但还有一部分批注用于参数级别。此部分讨论下列基本 JWS 批注：

  * <del><a name="wp221287"></a></del>`@WebService`（标准） 
  * <del><a name="wp221288"></a></del>`@SOAPBinding`（标准） 
  * <del><a name="wp221289"></a></del>`@WLHttpTransport`（WebLogic 特定） 
  * <del><a name="wp221290"></a></del>`@WebMethod`（标准） 
  * <del><a name="wp221291"></a></del>`@Oneway`（标准） 
  * <del><a name="wp221292"></a></del>`@WebParam`（标准） 
  * <del><a name="wp221293"></a></del>`@WebResult`（标准）

<del><a name="wp221294"></a></del>有关使用其他 JWS 批注编写 Web Service 可靠消息传递、对话、SOAP 消息处理程序等多个高级功能的信息，请参阅[高级 JWS 编程：实现异步功能](http://www.beansoft.biz/weblogic/docs92/webserv/advanced.html)。

<del><a name="wp221376"></a></del>有关标准批注和 WebLogic 特定 JWS 批注的参考文档，请参阅 [JWS 批注参考](http://www.beansoft.biz/weblogic/docs92/webserv/annotations.html)。

<del><a name="wp212035"></a></del>以下步骤说明 JWS 文件编程 时实现 Web Service 的常规基本步骤。有关代码示例，请参阅 [JWS 文件示例](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp212014)。

  1. <del><a name="wp212060"></a></del>导入将在 JWS 文件中使用的标准 JWS 批注。标准 JWS 批注位于 `javax.jws` 或 `javax.jws.soap` 包中。例如：<del><a name="wp212110"></a></del> 
    <pre>import javax.jws.WebMethod;<br />import javax.jws.WebService;<br />import javax.jws.soap.SOAPBinding;</pre>

  2. <del><a name="wp212095"></a></del>导入 JWS 文件中使用的 WebLogic 特定批注。WebLogic 特定批注位于 `weblogic.jws` 包中。例如：<del><a name="wp212149"></a></del> 
    <pre>import weblogic.jws.WLHttpTransport;</pre>

  3. <del><a name="wp212147"></a></del>在类级别添加所需的标准 `@WebService` JWS，以指定 Java 类公开 Web Service。 
    <del><a name="wp212300"></a></del>请参阅[指定 JWS 文件实现 Web Service](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp211661)。

  4. <del><a name="wp212225"></a></del>（可选）在类级别添加标准 `@SOAPBinding` JWS 批注，以指定 Web Service 与 SOAP 消息协议之间的映射。具体来说，使用此批注指定 Web Service 是 document-literal 还是 RPC 编码等。 
    <del><a name="wp214669"></a></del>虽然此 JWS 批注并非必需项，但 BEA 建议您在 JWS 文件中明确指定它，以明确客户端应用程序用于调用 Web Service 的 SOAP 绑定类型。
    
    <del><a name="wp223755"></a></del>请参阅[指定 Web Service 到 SOAP 消息协议的映射](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp212250)。

  5. <del><a name="wp223757"></a></del>（可选）在类级别添加 WebLogic 特定的 `@WLHttpTransport` JWS 批注，以指定调用 Web Service 的 URL 中使用的上下文路径和服务 URI。 
    <del><a name="wp214689"></a></del>虽然此 JWS 批注并非必需项，但 BEA 建议您在 JWS 文件中明确指定它，以明确客户端应用程序用于调用 Web Service的 URL。
    
    <del><a name="wp212322"></a></del>请参阅[指定 Web Service 的上下文路径和服务 URI](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp212252)。

  6. <del><a name="wp212295"></a></del>对于希望作为公共操作公开的 JWS 文件中的每种方法，可选择添加标准 `@WebMethod` 批注。（可选）使用标准 `@Oneway` 批注，以指定该操作仅使用输入参数，但不返回任何值。 
    <del><a name="wp212417"></a></del>请参阅[指定 JWS 方法公开为公共操作](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp211662)。

  7. <del><a name="wp212428"></a></del>（可选）通过添加标准 `@WebParam` 批注，自定义所公开操作的输入参数的名称。 
    <del><a name="wp212446"></a></del>请参阅[自定义操作参数和 WSDL 部件之间的映射](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp211663)。

  8. <del><a name="wp212467"></a></del>（可选）通过添加标准 `@WebResult` 批注，自定义所公开操作的返回值的名称和行为。 
    <del><a name="wp212475"></a></del>请参阅[自定义操作返回值与 WSDL 部件之间的映射](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp213914)。

  9. <del><a name="wp223760"></a></del>向方法中添加业务 Java 代码，使 WebService 能够执行您需要的行为。

##### <del><a name="wp212014"></a></del>JWS 文件示例

<del><a name="wp211027"></a></del>以下 JWS 文件示例说明如何实现简单 Web Service。

<del><a name="wp218708"></a></del>

<pre>package examples.webservices.simple;</pre>

<del><a name="wp218710"></a></del>

<pre>// 导入标准 JWS 批注接口</pre>

<del><a name="wp218712"></a></del>

<pre>import javax.jws.WebMethod;<br />import javax.jws.WebService;<br />import javax.jws.soap.SOAPBinding;</pre>

<del><a name="wp218716"></a></del>

<pre>// 导入 WebLogic 特定的 JWS 批注接口</pre>

<del><a name="wp218718"></a></del>

<pre>import weblogic.jws.WLHttpTransport;</pre>

<del><a name="wp218720"></a></del>

<pre>// 标准 JWS 批注，用于指定 Web Service 的<br />// porType 名称为“SimplePortType”，服务名为“SimpleService”，<br />// 在生成的 WSDL 中使用的 targetNamespace 为“http://example.org”</pre>

<del><a name="wp218724"></a></del>

<pre>@WebService(name="SimplePortType", serviceName="SimpleService",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp218727"></a></del>

<pre>// 标准 JWS 批注，用于指定服务到<br />// SOAP 消息协议的映射。尤其，它用于指定 SOAP 消息<br />// 为 document-literal-wrapped。</pre>

<del><a name="wp218731"></a></del>

<pre>@SOAPBinding(style=SOAPBinding.Style.DOCUMENT,<br />             use=SOAPBinding.Use.LITERAL,<br />             parameterStyle=SOAPBinding.ParameterStyle.WRAPPED)</pre>

<del><a name="wp218735"></a></del>

<pre>// WebLogic 特定的 JWS 批注，用于指定生成 Web Service<br />// 的 URI 所使用的上下文路径和服务 URI 为<br />// “simple/SimpleService”</pre>

<del><a name="wp218739"></a></del>

<pre>@WLHttpTransport(contextPath="simple", serviceUri="SimpleService",<br />                 portName="SimpleServicePort")</pre>

<del><a name="wp218742"></a></del>

<pre>/**<br /> * 此 JWS 文件形成了带有下列单个操作的简单 Java 类实现的 WebLogic<br /> * Web Service 的基础：sayHello<br /> *<br /> */</pre>

<del><a name="wp218749"></a></del>

<pre>public class SimpleImpl {</pre>

<del><a name="wp218751"></a></del>

<pre>// 标准 JWS 批注，用于指定方法应公开为<br />  // 公共操作。因为批注不包括<br />  // 成员值“operationName”，所以操作的公共名称将与<br /> // 方法名相同：sayHello。</pre>

<del><a name="wp219051"></a></del>

<pre>@WebMethod()<br />  public String sayHello(String message) {<br />    System.out.println("sayHello:" + message);<br />    return "Here is the message: '" + message + "'";<br />  }<br />}</pre>

##### <del><a name="wp211661"></a></del>指定 JWS 文件实现 Web Service

<del><a name="wp212632"></a></del>使用标准 `@WebService` 批注在类级别指定 JWS 文件实现 Web Service，如以下代码摘录所示：

<del><a name="wp215173"></a></del>

<pre>@WebService(name="SimplePortType", serviceName="SimpleService",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp212650"></a></del>在该示例中，Web Service 的名称是 `SimplePortType`，以后它将映射到 `jwsc` Ant 任务生成的 WSDL 文件中的 `wsdl:portType` 元素。服务名称是 `SimpleService`，它将映射到生成的 WSDL 文件中的 `wsdl:service` 元素。生成的 WSDL 中使用的目标名称空间是 `http://example.org`。

<del><a name="wp212839"></a></del>另外，可以指定 `@WebService` 批注的下列其他特性：

  * <del><a name="wp212860"></a></del>`endpointInterface` &#8211; 现有服务端点接口文件的完全限定名称。如果指定此特性，`jwsc` Ant 任务不会生成接口，但会假设已创建该接口且它位于 CLASSPATH 中。

<del><a name="wp212848"></a></del>`@WebService` 批注的所有特性都不是必需项。有关每个特性的默认值，请参阅 [Web Services Metadata for the Java Platform](http://www.jcp.org/en/jsr/detail?id=181)。

##### <del><a name="wp212250"></a></del>指定 Web Service 到 SOAP 消息协议的映射

<del><a name="wp212876"></a></del>假设您希望通过 SOAP 消息协议提供 Web Service；因此，JWS 文件中应当在类级别包含标准 `@SOAPBinding` 批注，以指定 Web Service 的 SOAP 绑定（RPC 编码或 document-literal-wrapped），如以下代码摘录所示：

<del><a name="wp215202"></a></del>

<pre>@SOAPBinding(style=SOAPBinding.Style.DOCUMENT,<br />             use=SOAPBinding.Use.LITERAL,<br />             parameterStyle=SOAPBinding.ParameterStyle.WRAPPED)</pre>

<del><a name="wp213147"></a></del>在该示例中，Web Service 使用 document-wrapped-style 编码和文字消息格式，如果未指定 `@SOAPBinding` 批注，则这类格式也是默认格式。

<del><a name="wp223828"></a></del>另外，可以使用 WebLogic 特定的 `@weblogic.jws.soap.SOAPBinding` 批注在方法级别指定 SOAP 绑定；其特性与标准 `@javax.jws.soap.SOAPBinding` 批注的特性相同。

<del><a name="wp213216"></a></del>使用 `parameterStyle` 批注（与 style=SOAPBinding.Style.DOCUMENT 特性结合使用）指定 Web Service 操作参数是代表全部 SOAP 消息正文，还是包装为与操作同名的顶级元素的元素。

<del><a name="wp213274"></a></del>下表列出 `@SOAPBinding`（标准或 WebLogic 特定）批注的三个特性的可能值和默认值。

<del><a name="wp213353"></a></del>表 5-1：@SOAPBinding 批注的特性

<del><a name="wp213324"></a></del>**特性**

<del><a name="wp213326"></a></del>**可能值**

<del><a name="wp213328"></a></del>**默认值**

<del><a name="wp213330"></a></del>style

<del><a name="wp213332"></a></del>`SOAPBinding.Style.RPC<br />
    <br />SOAPBinding.Style.DOCUMENT`

<del><a name="wp213334"></a></del>`SOAPBinding.Style.DOCUMENT`

<del><a name="wp213336"></a></del>use

<del><a name="wp213393"></a></del>`SOAPBinding.Use.LITERAL<br />
    <br />SOAPBinding.Use.ENCODED`

<del><a name="wp213413"></a></del>`SOAPBinding.Use.LITERAL`

<del><a name="wp213342"></a></del>parameterStyle

<del><a name="wp213397"></a></del>`SOAPBinding.ParameterStyle.BARE<br />
    <br />SOAPBinding.ParameterStyle.WRAPPED`

<del><a name="wp213417"></a></del>`SOAPBinding.ParameterStyle.WRAPPED`

##### <del><a name="wp212252"></a></del>指定 Web Service 的上下文路径和服务 URI

<del><a name="wp213444"></a></del>使用 WebLogic 特定的 `@WLHttpTransport` 批注指定通过 HTTP 传输调用 Web Service 的 URL 的上下文路径和服务 URI 部分，以及生成的 WSDL 中的端口名称，如以下代码摘录所示：

<del><a name="wp215219"></a></del>

<pre>@WLHttpTransport(contextPath="simple", serviceUri="SimpleService",<br />                 portName="SimpleServicePort")</pre>

<del><a name="wp213473"></a></del>在该示例中，`jwsc` Ant 任务生成的 WSDL 文件中的端口名称（具体来说，即 `<port>` 元素的 `name` 特性）是 `SimpleServicePort`。用于通过 HTTP 调用 Web Service 的 URL 包括上下文路径 `simple` 和服务 URI `SimpleService`，如下例中所示：

<del><a name="wp213535"></a></del>

<pre>http://<em>host</em>:<em>port</em>/simple/SimpleService</pre>

<del><a name="wp213539"></a></del>有关此批注和其他 WebLogic 特定批注的参考文档，请参阅 [JWS 批注参考](http://www.beansoft.biz/weblogic/docs92/webserv/annotations.html)。

##### <del><a name="wp211662"></a></del>指定 JWS 方法公开为公共操作

<del><a name="wp212882"></a></del>使用标准 `@WebMethod` 批注指定 JWS 文件的一个方法应公开为 Web Service 的公共操作，如以下代码摘录所示：

<del><a name="wp215279"></a></del>

<pre>public class SimpleImpl {</pre>

<del><a name="wp215283"></a></del>

<pre>@WebMethod(operationName="sayHelloOperation")<br />  public String sayHello(String message) {<br />    System.out.println("sayHello:" + message);<br />    return "Here is the message: '" + message + "'";<br />  }<br />...</pre>

<del><a name="wp212921"></a></del>在该示例中，`SimpleImpl` JWS 文件的 `sayHello()` 方法公开为 Web Service 的公共操作。不过，`operationName` 特性指定 WSDL 文件中操作的公共名称是 `sayHelloOperation`。如果不指定 `operationName` 特性，则操作的公共名称就是方法本身的名称。

<del><a name="wp212996"></a></del>另外，可以使用 `action` 特性指定操作的行为。在使用 SOAP 作为绑定时，`action` 特性的值确定 SOAP 消息中 `SOAPAction` 头的值。

<del><a name="wp213024"></a></del>可以使用标准 `@Oneway` 批注指定操作不向调用应用程序返回值，如下例所示：

<del><a name="wp213029"></a></del>

<pre>public class OneWayImpl {</pre>

<del><a name="wp213030"></a></del>

<pre>@WebMethod()<br />  @Oneway()</pre>

<del><a name="wp213031"></a></del>

<pre>public void ping() {<br />    System.out.println("ping operation");<br />  }</pre>

<del><a name="wp213032"></a></del>

<pre>...</pre>

<del><a name="wp213027"></a></del>如果将某个操作指定为单向，则需要实现方法以返回 `void`，不能使用 Holder 类作为参数，也不能引发任何 checked 异常。

<del><a name="wp212955"></a></del>`@WebMethod` 批注的所有特性都不是必需项。有关每个特性的默认值，以及有关 `@WebMethod` 和 `@Oneway` 批注的其他信息，请参阅 [Web Services Metadata for the Java Platform](http://www.jcp.org/en/jsr/detail?id=181)。

<del><a name="wp224002"></a></del>如果 JWS 文件中的所有公共方法都尚未使用 `@WebMethod` 批注进行批注，则在默认情况下，__所有公共方法都会公开为 Web Service 操作。

##### <del><a name="wp211663"></a></del>自定义操作参数和 WSDL 部件之间的映射

<del><a name="wp213911"></a></del>使用标准 `@WebParam` 批注自定义 Web Service 的操作输入参数与生成的 WSDL 文件中的元素之间的映射，并指定参数的行为，如以下代码摘录所示：

<del><a name="wp213964"></a></del>

<pre>public class SimpleImpl {</pre>

<del><a name="wp213972"></a></del>

<pre>@WebMethod()<br />  @WebResult(name="IntegerOutput",<br />             targetNamespace="http://example.org/docLiteralBare")<br />  public int echoInt(<br /><b>      @WebParam(name="IntegerInput",<br />                targetNamespace="http://example.org/docLiteralBare")<br /></b>      int input)</pre>

<del><a name="wp220355"></a></del>

<pre>{<br />      System.out.println("echoInt '" + input + "' to you too!");<br />      return input;<br />  }<br />...</pre>

<del><a name="wp214010"></a></del>在该示例中，生成的 WSDL 中 `echoInt` 操作的参数名称是 `IntegerInput`；如果 JWS 文件中不存在 `@WebParam` 批注，则生成的 WSDL 文件中参数的名称将与方法参数的名称相同：`input`。`targetNamespace` 特性指定参数的 XML 名称空间是`http://example.org/docLiteralBare`；仅在使用 document-style SOAP 绑定，即参数映射至 XML 元素时，该特性才起作用。

<del><a name="wp214053"></a></del>另外，可以指定 `@WebParam` 批注的下列其他特性：

  * <del><a name="wp214094"></a></del>`mode`&#8211; 参数流的方向（`WebParam.Mode.IN`、`WebParam.Mode.OUT` 或 `WebParam.Mode.INOUT`）。只能为符合 `Holder` 类型的 JAX-RPC 定义的参数类型指定 OUT 和 INOUT 模式。仅 RPC 样式操作或映射至头的参数支持 OUT 和 INOUT 模式。 
  * <del><a name="wp214103"></a></del>`header` &#8211; 布尔特性，设置为 `true` 时，则指定应当从 SOAP 头而不是从默认正文中检索出的参数的值。

<del><a name="wp214122"></a></del>`@WebParam` 批注的所有特性都不是必需项。有关每个特性的默认值，请参阅 [Web Services Metadata for the Java Platform](http://www.jcp.org/en/jsr/detail?id=181)。

##### <del><a name="wp213914"></a></del>自定义操作返回值与 WSDL 部件之间的映射

<del><a name="wp214133"></a></del>使用标准 `@WebResult` 批注自定义 Web Service 操作返回值与生成 WSDL 文件中的对应元素之间的映射，如以下代码摘录所示：

<del><a name="wp214134"></a></del>

<pre>public class Simple {</pre>

<del><a name="wp214135"></a></del>

<pre>@WebMethod()<br /><b>  @WebResult(name="IntegerOutput",<br />             targetNamespace="http://example.org/docLiteralBare")<br /></b>  public int echoInt(<br />      @WebParam(name="IntegerInput",<br />                targetNamespace="http://example.org/docLiteralBare")<br />      int input)</pre>

<del><a name="wp220357"></a></del>

<pre>{<br />      System.out.println("echoInt '" + input + "' to you too!");<br />      return input;<br />  }<br />...</pre>

<del><a name="wp214136"></a></del>在该示例中，生成的 WSDL 中的 `echoInt` 操作的返回值名称是 `IntegerOutput`；如果 JWS 文件中不存在 `@WebResult` 批注，则所生成 WSDL 文件中返回值的名称将是硬编码名称 `return`。`targetNamespace` 特性指定返回值的 XML 名称空间是`http://example.org/docLiteralBare`；仅在使用 document-style SOAP 绑定，即返回值映射至 XML 元素时，该特性才起作用。

<del><a name="wp214131"></a></del>`@WebResult` 批注的所有特性都不是必需项。有关每个特性的默认值，请参阅 [Web Services Metadata for the Java Platform](http://www.jcp.org/en/jsr/detail?id=181)。

<hr noshade="noshade" />

#### <del><a name="wp216814"></a></del>使用 JwsContext 访问有关 Web Service 的运行时信息

<del><a name="wp216821"></a></del>当客户端应用程序调用使用 JWS 文件实现的 WebLogic Web Service 时，WebLogic Server 会自动创建一个上下文__，Web Service 可以使用该上下文来访问有关该服务的运行时信息，有时还可以更改这些信息。此信息主要与对话相关，例如当前对话是否已完成、对话属性的当前值以及在运行时更改对话属性等。（有关对话和如何实现对话的信息，请参阅[创建对话 Web Service](http://www.beansoft.biz/weblogic/docs92/webserv/advanced.html#wp255666)。）可以通过该上下文访问的某些信息更为通用，如用于调用该 Web Service 的协议（HTTP/S 或 JMS）、SOAP 消息请求中的 SOAP 头等。

<del><a name="wp217861"></a></del>可以在 JWS 文件中使用批注和 WebLogic Web Service API 访问运行时上下文信息，如下列部分所述。

##### <del><a name="wp217434"></a></del>访问 Web Service 上下文的准则

<del><a name="wp216953"></a></del>下例说明使用上下文确定用于调用 Web Service 的协议的简单 JWS 文件；该示例之后的编程准则中将讨论用粗体显示的代码。

<del><a name="wp219073"></a></del>

<pre>package examples.webservices.jws_context;</pre>

<del><a name="wp219075"></a></del>

<pre>import javax.jws.WebMethod;<br />import javax.jws.WebService;</pre>

<del><a name="wp219078"></a></del>

<pre>import weblogic.jws.WLHttpTransport;<br /><code>import weblogic.jws.Context;</code></pre>

<del><a name="wp219081"></a></del>

    import weblogic.wsee.jws.JwsContext;<br />import weblogic.wsee.jws.Protocol;

<del><a name="wp219084"></a></del>

<pre>@WebService(name="JwsContextPortType", serviceName="JwsContextService",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp219087"></a></del>

<pre>@WLHttpTransport(contextPath="contexts", serviceUri="JwsContext",<br />                 portName="JwsContextPort")</pre>

<del><a name="wp219090"></a></del>

<pre>/**<br /> * 说明如何使用 @Context 批注的简单 Web Service。<br /> */</pre>

<del><a name="wp219094"></a></del>

<pre>public class JwsContextImpl {</pre>

<del><a name="wp219096"></a></del>

      @Context<br />  private JwsContext ctx;

<del><a name="wp219099"></a></del>

<pre>@WebMethod()<br />  public String getProtocol() {</pre>

<del><a name="wp219102"></a></del>

        Protocol protocol = ctx.getProtocol();

<del><a name="wp219104"></a></del>

<pre>System.out.println("protocol: " + protocol);<br />    return "This is the protocol: " + protocol;<br />  }<br />}</pre>

<del><a name="wp217274"></a></del>使用 JWS 文件中的下列准则访问 Web Service 的运行时上下文，如上例中用粗体显示的代码所示：

  * <del><a name="wp217275"></a></del>导入 `@weblogic.jws.Context` JWS 批注：<del><a name="wp217276"></a></del> 
    <pre>import weblogic.jws.Context;</pre>

  * <del><a name="wp217243"></a></del>导入 `weblogic.wsee.jws.JwsContext` API 以及可能使用的所有其他相关 API（该示例还使用 `weblogic.wsee.jws.Protocol` API）：<del><a name="wp217290"></a></del> 
    <pre>import weblogic.wsee.jws.JwsContext;<br />import weblogic.wsee.jws.Protocol;</pre>
    
    <del><a name="wp217291"></a></del>有关上下文相关 API 的参考文档，请参阅 [weblogic.wsee.*](http://e-docs.bea.com/wls/docs92/javadocs/index.html) Javadocs。

  * <del><a name="wp217236"></a></del>使用字段级 `@Context` JWS 批注对 `weblogic.wsee.jws.JwsContext` 数据类型的私有变量进行批注：<del><a name="wp217333"></a></del> 
    <pre>@Context<br /> private JwsContext ctx;</pre>
    
    <del><a name="wp216830"></a></del>第一次调用 Web Service 时，WebLogic Server 自动为已批注变量（在该例中为 `ctx`）分配 `JwsContext` 运行时实现，所以，以后无需在代码中明确初始化该变量即可以使用它。

  * <del><a name="wp220665"></a></del>使用 `JwsContext` 类的方法获取和在某些情况下更改有关 Web Service 的运行时信息。下例说明如何获取用于调用 Web Service 的协议：<del><a name="wp217410"></a></del> 
    <pre>Protocol protocol = ctx.getProtocol();</pre>
    
    <del><a name="wp216836"></a></del>有关可用方法的完整列表，请参阅 [JwsContext 的方法](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp217430)。

##### <del><a name="wp217430"></a></del>JwsContext 的方法

<del><a name="wp217441"></a></del>下表简单介绍 `JwsContext` 的方法，可以在 JWS 文件中使用这些方法，以访问有关 Web Service 的运行时信息。有关 `JwsContext` 以及 `Protocol` 和 `ServiceHandle` 等其他上下文相关 API 的详细参考信息，请参阅 [weblogic.wsee.*](http://e-docs.bea.com/wls/docs92/javadocs/index.html) Javadocs。

<del><a name="wp217454"></a></del>

<del><a name="wp217457"></a></del>表 5-2：JwsContext 的方法

<del><a name="wp217461"></a></del>方法

<del><a name="wp217542"></a></del>返回值

<del><a name="wp217463"></a></del>描述

<del><a name="wp217465"></a></del>isFinished()

<del><a name="wp217544"></a></del>boolean

<del><a name="wp217467"></a></del>返回一个布尔值，指定当前对话已结束还是仍在继续。

<del><a name="wp217890"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217469"></a></del>finishConversation()

<del><a name="wp217546"></a></del>void

<del><a name="wp217471"></a></del>完成当前对话。

<del><a name="wp218145"></a></del>此方法相当于调用已使用 `@Conversation (Conversation.Phase.FINISH)` JWS 批注进行批注的方法的客户端应用程序。

<del><a name="wp218086"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217473"></a></del>setMaxAge(java.util.Date)

<del><a name="wp217548"></a></del>void

<del><a name="wp218116"></a></del>将新的最大对话期限设置为绝对 `Date`。如果 date 参数为过去的日期，WebLogic Server 会立即结束该对话。

<del><a name="wp218148"></a></del>此方法相当于 `@Conversational` 批注的 `maxAge` 特性__，该特性指定默认的最大对话期限。使用此方法在运行时替代此默认值。

<del><a name="wp218127"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217477"></a></del>setMaxAge(String)

<del><a name="wp217550"></a></del>void

<del><a name="wp218188"></a></del>通过指定 `String` 持续时间，例如 `1 day`，来设置新的最大对话期限。

<del><a name="wp220678"></a></del>`String` 参数的有效值为数字和下列期限之一：

  * <del><a name="wp220679"></a></del>`seconds`
  * <del><a name="wp220680"></a></del>`minutes`
  * <del><a name="wp220681"></a></del>`hours`
  * <del><a name="wp220682"></a></del>`days`
  * <del><a name="wp220683"></a></del>`years`

<del><a name="wp220684"></a></del>例如，要指定最大期限为 10 分钟，请使用以下语法：

<del><a name="wp220685"></a></del>`ctx.setMaxAge("10 minutes")`

<del><a name="wp218203"></a></del>此方法相当于 `@Conversational` 批注的 `maxAge` 特性__，该特性指定默认的最大对话期限。使用此方法在运行时替代此默认值。

<del><a name="wp217479"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217481"></a></del>getMaxAge()

<del><a name="wp217552"></a></del>long

<del><a name="wp217483"></a></del>返回允许的最大对话期限，以秒为单位。

<del><a name="wp218209"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217485"></a></del>getCurrentAge()

<del><a name="wp217554"></a></del>long

<del><a name="wp217487"></a></del>返回对话的当前期限，以秒为单位。

<del><a name="wp218212"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217489"></a></del>resetIdleTime()

<del><a name="wp217556"></a></del>void

<del><a name="wp218256"></a></del>重置用于计量当前会话中上一次活动之后经过的秒数的计时器。

<del><a name="wp218298"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217493"></a></del>setMaxIdleTime(long)

<del><a name="wp217558"></a></del>void

<del><a name="wp218335"></a></del>设置在 WebLogic Server 因客户端不活动而结束对话之前，对话可保持空闲的秒数。

<del><a name="wp218341"></a></del>此方法相当于 `@Conversational` 批注的 `maxIdleTime` 特性__，该特性指定默认的对话空闲时间。使用此方法在运行时替代此默认值。

<del><a name="wp217495"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217497"></a></del>setMaxIdleTime(String)

<del><a name="wp217560"></a></del>void

<del><a name="wp218359"></a></del>设置在 WebLogic Server 因客户端不活动而结束对话之前，对话可保持空闲的秒数（指定为 `String`）。

<del><a name="wp220713"></a></del>`String` 参数的有效值为数字和下列期限之一：

  * <del><a name="wp220714"></a></del>`seconds`
  * <del><a name="wp220715"></a></del>`minutes`
  * <del><a name="wp220716"></a></del>`hours`
  * <del><a name="wp220717"></a></del>`days`
  * <del><a name="wp220718"></a></del>`years`

<del><a name="wp220719"></a></del>例如，要指定最大空闲时间为 10 分钟，请使用以下语法：

<del><a name="wp220720"></a></del>`ctx.setMaxIdleTime("10 minutes")`

<del><a name="wp218360"></a></del>此方法相当于 `@Conversational` 批注的 `maxIdleTime` 特性__，该特性指定默认的对话空闲时间。使用此方法在运行时替代此默认值。

<del><a name="wp217499"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217501"></a></del>getMaxIdleTime()

<del><a name="wp217562"></a></del>long

<del><a name="wp218386"></a></del>返回在 WebLogic Server 因客户端不活动而结束对话之前，允许对话保持空闲的秒数。

<del><a name="wp218404"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217688"></a></del>getCurrentIdleTime()

<del><a name="wp217690"></a></del>long

<del><a name="wp218410"></a></del>获取最后一个客户端请求后，或重置对话的最大空闲时间后的秒数。

<del><a name="wp218425"></a></del>仅在对话 Web Service 中，或者在已使用 `@Conversation` 或 `@Conversational` 批注进行批注的 Web Service 中使用此方法。

<del><a name="wp217682"></a></del>getCallerPrincipal()

<del><a name="wp217684"></a></del>java.security.Principal

<del><a name="wp218441"></a></del>返回与刚刚调用的操作关联的安全委托人，假设已执行基本身份验证。

<del><a name="wp217676"></a></del>isCallerInRole(String)

<del><a name="wp217678"></a></del>boolean

<del><a name="wp218472"></a></del>如果经身份验证的委托人具有指定的安全角色，则返回 `true`。

<del><a name="wp217670"></a></del>getService()

<del><a name="wp217672"></a></del>weblogic.wsee.jws.ServiceHandle

<del><a name="wp217674"></a></del>返回 `ServiceHandle` 的实例，即一个 WebLogic Web Service API，可查询该 API 以收集有关 Web Service 的其他信息，例如对话 ID（如果 Web Service 为对话）和 Web Service 的 URL 等。

<del><a name="wp217664"></a></del>getLogger(String)

<del><a name="wp217666"></a></del>weblogic.wsee.jws.util.Logger

<del><a name="wp218501"></a></del>获取 `Logger` 类的实例，可使用该实例将消息从 Web Service 发送到日志文件。

<del><a name="wp217658"></a></del>getInputHeaders()

<del><a name="wp217660"></a></del>org.w3c.dom.Element[]

<del><a name="wp217662"></a></del>返回与当前操作调用的 SOAP 请求消息关联的 SOAP 头数组。

<del><a name="wp217652"></a></del>setUnderstoodInputHeaders(boolean)

<del><a name="wp217654"></a></del>void

<del><a name="wp217656"></a></del>指明是否应了解输入头。

<del><a name="wp217646"></a></del>getUnderstoodInputHeaders()

<del><a name="wp217648"></a></del>boolean

<del><a name="wp217650"></a></del>返回最近通过调用 setUnderstoodInputHeader 设置的值。

<del><a name="wp217640"></a></del>setOutputHeaders(Element[])

<del><a name="wp217642"></a></del>void

<del><a name="wp217644"></a></del>指定应当与传出 SOAP 响应消息（发送回最初调用当前操作的客户端应用程序）关联的 SOAP 头数组。

<del><a name="wp217634"></a></del>getProtocol()

<del><a name="wp217636"></a></del>weblogic.wsee.jws.Protocol

<del><a name="wp217638"></a></del>返回用于调用当前操作的协议（如 HTTP/S 或 JMS）。

<hr noshade="noshade" />

#### <del><a name="wp215790"></a></del>是否要实现无状态会话 EJB？

<del><a name="wp215801"></a></del>`jwsc` Ant 任务始终选择常规 Java 对象，作为处理 JWS 文件时的 Web Service 底层实现。

<del><a name="wp222608"></a></del>不过，有时可能要将 Web Service 的底层实现作为无状态会话 EJB，从而利用 EJB 提供的所有特性，例如实例缓冲池、事务、安全、容器管理的持久性、容器管理的关系和数据缓存等。如果决定需要 Web Service 的 EJB 实现，请遵循以下部分中的编程准则。

##### <del><a name="wp216057"></a></del>在 JWS 文件中实现 EJB 时的编程准则

<del><a name="wp216276"></a></del>一般准则是始终在 JWS 文件中使用 EJBGen 批注，以自动生成而不是手工创建实现 EJB 时需要的 EJB Remote 类、Home 接口类和部署描述符文件。EJBGen 批注的工作方式与 JWS 批注相同：它们遵循 JDK 5.0 元数据语法，可显著简化编程任务。

<del><a name="wp216265"></a></del>有关 EJBGen 的详细信息，请参阅 [WebLogic Enterprise JavaBean 编程](http://www.beansoft.biz/weblogic/docs92/ejb/index.html) 中的 [EJBGen 参考](http://www.beansoft.biz/weblogic/docs92/ejb/EJBGen_reference.html) 部分。

<del><a name="wp216210"></a></del>在 JWS 文件中明确实现无状态会话 EJB 时，请遵循上述准则。有关示例，请参阅[实现 EJB 的 JWS 文件示例](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp216300)，相关部分用粗体显示：

  * <del><a name="wp216287"></a></del>导入标准 J2EE EJB 类：<del><a name="wp216541"></a></del> 
    <pre>import javax.ejb.SessionBean;<br />import javax.ejb.SessionContext;</pre>

  * <del><a name="wp216532"></a></del>导入 EJBGen 批注，所有批注都包含在 `weblogic.ejbgen` 包中。至少需要导入 `@Session` 批注；如果希望在 JWS 文件中使用其他 EJBGen 批注指定 EJB 的形状和行为，请参阅 [EJBGen](http://www.beansoft.biz/weblogic/docs92/ejb/EJBGen_reference.html) 参考指南。<del><a name="wp216706"></a></del> 
    <pre>import weblogic.ejbgen.Session;</pre>

  * <del><a name="wp216707"></a></del>至少应在类级别使用 `@Session` 批注指定 EJB 的名称：<del><a name="wp216708"></a></del> 
    <pre>@Session(ejbName="TransactionEJB")</pre>
    
    <del><a name="wp216721"></a></del>`@Session` 是唯一一个必须在 JWS 文件中使用的 EJBGen 批注。如果希望，可以使用其他 EJBGen 批注指定 EJB 的其他特性。

  * <del><a name="wp215831"></a></del>确保 JWS 类实现 `SessionBean`：<del><a name="wp216733"></a></del> 
    <pre>public class TransactionImpl implements SessionBean {...</pre>

  * <del><a name="wp216745"></a></del>另外，必须包含标准 EJB 方法 `ejbCreate()`和 `ejbActivate()` 等，即便除了希望更改 EJB 的默认行为的情况下以外，通常并不需要向这些方法中添加代码：<del><a name="wp216758"></a></del> 
    <pre>public void ejbCreate() {}<br />  public void ejbActivate() {}<br />  public void ejbRemove() {}<br />  public void ejbPassivate() {}<br />  public void setSessionContext(SessionContext sc) {}</pre>

<del><a name="wp216805"></a></del>如果在 JWS 文件中遵循上述全部准则，`jwsc` Ant 任务稍后会将 Web Service 编译为 EJB，并将其打包到企业应用程序的 EJB JAR 文件中。

##### <del><a name="wp216300"></a></del>实现 EJB 的 JWS 文件示例

<del><a name="wp216304"></a></del>下例给出一个实现无状态会话 EJB 的简单 JWS 文件。相关代码用粗体显示。

<del><a name="wp216313"></a></del>

<pre>package examples.webservices.transactional;</pre>

<del><a name="wp216315"></a></del>

    import javax.ejb.SessionBean;<br />import javax.ejb.SessionContext;

<del><a name="wp216318"></a></del>

<pre>import javax.jws.WebMethod;<br />import javax.jws.WebService;</pre>

<del><a name="wp216321"></a></del>

<pre>import weblogic.jws.WLHttpTransport;<br />import weblogic.jws.Transactional;</pre>

<del><a name="wp216324"></a></del>

    import weblogic.ejbgen.Session;

<del><a name="wp216326"></a></del>

    @Session(ejbName="TransactionEJB")

<del><a name="wp216328"></a></del>

<pre>@WebService(name="TransactionPortType", serviceName="TransactionService",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp216331"></a></del>

<pre>@WLHttpTransport(contextPath="transactions", serviceUri="TransactionService",<br />                 portName="TransactionPort")</pre>

<del><a name="wp216334"></a></del>

<pre>/**<br /> * 此 JWS 文件形成了带有下列单个操作的简单 EJB 实现的 WebLogic<br /> * Web Service 的基础：sayHello。此操作作为事务的一部分<br /> * 执行。<br />*<br /> */</pre>

<del><a name="wp216342"></a></del>

    public class TransactionImpl implements SessionBean {

<del><a name="wp216344"></a></del>

<pre>@WebMethod()<br />  @Transactional(value=true)</pre>

<del><a name="wp216347"></a></del>

<pre>public String sayHello(String message) {<br />    System.out.println("sayHello:" + message);<br />    return "Here is the message: '" + message + "'";<br />  }</pre>

<del><a name="wp216352"></a></del>

<pre>// 标准 EJB 方法。通常无需替换这些方法。</pre>

<del><a name="wp216354"></a></del>

      public void ejbCreate() {}<br />  public void ejbActivate() {}<br />  public void ejbRemove() {}<br />  public void ejbPassivate() {}<br />  public void setSessionContext(SessionContext sc) {}<br />}

<hr noshade="noshade" />

#### <del><a name="wp210057"></a></del><del><a name="complex_types"></a></del>编写用户定义的 Java 数据类型

<del><a name="wp210069"></a></del>公开为 Web Service 操作的 JWS 文件的方法无需使用内置数据类型（如字符串和整数类型）作为参数，也无需返回值，而是应当使用您自己创建的 Java 数据类型。用户定义数据类型的示例是 `TradeResult`，它包含两个字段：`String` 股票代码和代表交易股数的整数。

<del><a name="wp210073"></a></del>如果 JWS 文件使用用户定义的数据类型作为它的一个或多个方法的参数或返回值，则必须创建您自己的数据类型的 Java 代码，然后将该类导入 JWS 文件并相应地使用它。`jwsc` Ant 任务稍后会创建所有必需的数据绑定工件，例如，Java 用户定义数据类型的对应 XML Schema 表示、JAX-RPC 类型映射文件等。

<del><a name="wp210148"></a></del>在为用户定义数据类型编写 Java 类时，请遵循下列基本要求：

  * <del><a name="wp210091"></a></del>定义不使用参数的默认构造方法。 
  * <del><a name="wp210092"></a></del>对于要公开公布的每个成员变量，定义 `getXXX()` 和 `setXXX()` 方法。 
  * <del><a name="wp210093"></a></del>将公开的每个成员变量的数据类型设置为内置数据类型之一，或设置为包含内置数据类型的其他用户定义数据类型。

<del><a name="wp210094"></a></del>这些要求由 JAX-RPC 1.1 指定；有关更详细的信息和完整的要求列表，请参阅 [JAX-RPC specification](http://java.sun.com/xml/jaxrpc/index.jsp)。

<del><a name="wp210179"></a></del>`jwsc` Ant 任务可为大多数常用 XML 和 Java 数据类型生成数据绑定工件。有关支持的用户定义数据类型的列表，请参阅[支持的用户定义数据类型](http://www.beansoft.biz/weblogic/docs92/webserv/data_types.html#wp209611)。有关支持的内置数据类型的完整列表，请参阅[支持的内置数据类型](http://www.beansoft.biz/weblogic/docs92/webserv/data_types.html#wp209610)。

<del><a name="wp210166"></a></del>下例介绍称为 `BasicStruct` 的简单 Java 用户定义数据类型：

<del><a name="wp219343"></a></del>

<pre>package examples.webservices.complex;</pre>

<del><a name="wp219346"></a></del>

<pre>/**<br /> * 定义一个具有 integer、String<br /> * 和 String[] 属性的名为 BasicStruct 的简单 JavaBean<br /> */</pre>

<del><a name="wp219351"></a></del>

<pre>public class BasicStruct {</pre>

<del><a name="wp219353"></a></del>

<pre>// 属性</pre>

<del><a name="wp219355"></a></del>

<pre>private int intValue;<br />  private String stringValue;<br />  private String[] stringArray;</pre>

<del><a name="wp219359"></a></del>

<pre>// 获取器和设置器方法</pre>

<del><a name="wp219361"></a></del>

<pre>public int getIntValue() {<br />    return intValue;<br />  }</pre>

<del><a name="wp219365"></a></del>

<pre>public void setIntValue(int intValue) {<br />    this.intValue = intValue;<br />  }</pre>

<del><a name="wp219369"></a></del>

<pre>public String getStringValue() {<br />    return stringValue;<br />  }</pre>

<del><a name="wp219373"></a></del>

<pre>public void setStringValue(String stringValue) {<br />    this.stringValue = stringValue;<br />  }</pre>

<del><a name="wp219377"></a></del>

<pre>public String[] getStringArray() {<br />    return stringArray;<br />  }</pre>

<del><a name="wp219381"></a></del>

<pre>public void setStringArray(String[] stringArray) {<br />    this.stringArray = stringArray;<br />  }</pre>

<del><a name="wp219520"></a></del>

<pre>}</pre>

<del><a name="wp219522"></a></del>以下段落选自 JWS 文件，说明如何导入 `BasicStruct` 类和将该类其方法之一的参数和返回值；有关完整的 JWS 文件，请参阅[示例 ComplexImpl.java JWS 文件](http://www.beansoft.biz/weblogic/docs92/webserv/use_cases.html#wp219292)：

<del><a name="wp219531"></a></del>

<pre>package examples.webservices.complex;</pre>

<del><a name="wp219535"></a></del>

<pre>// 导入标准 JWS 批注接口</pre>

<del><a name="wp219537"></a></del>

<pre>import javax.jws.WebMethod;<br />import javax.jws.WebParam;<br />import javax.jws.WebResult;<br />import javax.jws.WebService;<br />import javax.jws.soap.SOAPBinding;</pre>

<del><a name="wp219543"></a></del>

<pre>// 导入 WebLogic 特定的 JWS 批注接口</pre>

<del><a name="wp219545"></a></del>

<pre>import weblogic.jws.WLHttpTransport;</pre>

<del><a name="wp219547"></a></del>

    // 导入 BasicStruct JavaBean

<del><a name="wp219549"></a></del>

    import examples.webservices.complex.BasicStruct;

<del><a name="wp219555"></a></del>

<pre>@WebService(serviceName="ComplexService", name="ComplexPortType",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp219625"></a></del>

<pre>...</pre>

<del><a name="wp219820"></a></del>

<pre>public class ComplexImpl {</pre>

<del><a name="wp219657"></a></del>

<pre>@WebMethod(operationName="echoComplexType")<br /><code>  public BasicStruct echoStruct(BasicStruct struct)</code></pre>

<del><a name="wp219662"></a></del>

<pre>{<br /><code>    return struct;&lt;br /></code>  }<br />}</pre>

<hr noshade="noshade" />

#### <del><a name="wp209620"></a></del>引发<a name="exceptions"></a>异常

<del><a name="wp210487"></a></del>在 JWS 文件的方法中编写错误处理 Java 代码时，可以引发您自己的用户定义异常，也可以引发 `javax.xml.rpc.soap.SOAPFaultException` 异常。如果引发 `SOAPFaultException` 异常，WebLogic Server 会将其映射到 SOAP 错误，并将其发送至调用该操作的客户端应用程序。

<del><a name="wp210488"></a></del>如果 JWS 文件引发 `SOAPFaultException` 以外的任何 Java 异常类型，WebLogic Server 会尝试尽可能将其映射至 SOAP 错误。不过，如果希望控制由哪一个客户端应用程序检索并向其发送最相关的异常信息，应明确引发 `SOAPFaultException` 异常或引发扩展该异常的异常。有关创建和引发您自己的用户定义异常的详细信息，请参阅 [JAX-RPC 1.1 specification](http://java.sun.com/xml/jaxrpc/index.jsp)。

<del><a name="wp210489"></a></del>以下代码摘录介绍 `SOAPFaultException` 类：

<del><a name="wp210490"></a></del>

<pre>public class SOAPFaultException extends java.lang.RuntimeException {<br />    public SOAPFaultException (QName faultcode,<br />                               String faultstring,<br />                               String faultactor,<br />                               javax.xml.soap.Detail detail ) {...}<br />    public Qname getFaultCode() {...}<br />    public String getFaultString() {...}<br />    public String getFaultActor() {...}<br />    public javax.xml.soap.Detail getDetail() {...}<br />}</pre>

<del><a name="wp220176"></a></del>使用 SOAP with Attachments API for Java 1.1 (SAAJ) `javax.xml.soap.SOAPFactory.createDetail()` 方法创建 `Detail` 对象，该对象是提供有关错误的详细应用程序特定信息的 `DetailEntry` 对象的容器。

<del><a name="wp222291"></a></del>可以使用您自己或 BEA 的 `SOAPFactory` 实现，可以在 JWS 文件中访问后者，方法是通过调用返回 `javax.xml.soap.SOAPFactory object` 的 `weblogic.wsee.util.WLSOAPFactory.createSOAPFactory()` 静态方法。然后，在运行时使用 `-Djavax.xml.soap.SOAPFactory` 标志指定 BEA 的 `SOAPFactory` 实现，如下所示：

<del><a name="wp222304"></a></del>

<pre>-Djavax.xml.soap.SOAPFactory=weblogic.xml.saaj.SOAPFactoryImpl</pre>

<del><a name="wp220172"></a></del>以下 JWS 文件显示通过实现 Web Service 操作的方法创建并引发 `SOAPFaultException`；各部分中用粗体突出显示异常代码：

<del><a name="wp219934"></a></del>

<pre>package examples.webservices.soap_exceptions;</pre>

<del><a name="wp219936"></a></del>

    import javax.xml.namespace.QName;<br />import javax.xml.soap.Detail;<br />import javax.xml.soap.SOAPException;<br />import javax.xml.soap.SOAPFactory;<br />import javax.xml.rpc.soap.SOAPFaultException;

<del><a name="wp219942"></a></del>

<pre>// 导入 @WebService 批注</pre>

<del><a name="wp219944"></a></del>

<pre>import javax.jws.WebService;</pre>

<del><a name="wp219946"></a></del>

<pre>// 导入 WLHttpTransport</pre>

<del><a name="wp219948"></a></del>

<pre>import weblogic.jws.WLHttpTransport;</pre>

<del><a name="wp219950"></a></del>

<pre>@WebService(serviceName="SoapExceptionsService",<br />            name="SoapExceptionsPortType",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp219954"></a></del>

<pre>@WLHttpTransport(contextPath="exceptions",<br />                 serviceUri="SoapExceptionsService",<br />                 portName="SoapExceptionsServicePort")<br />/**<br /> * 此 JWS 文件形成了带有下列单个操作的简单 Java 类实现的 WebLogic<br /> * Web Service 的基础：sayHelloWorld<br /> *<br /> * @作者版权所有 (c) 2005，BEA Systems。保留所有权利。<br />*/</pre>

<del><a name="wp219964"></a></del>

<pre>public class SoapExceptionsImpl {</pre>

<del><a name="wp219966"></a></del>

<pre>public SoapExceptionsImpl() {</pre>

<del><a name="wp219968"></a></del>

<pre>}</pre>

<del><a name="wp220079"></a></del>

<pre>public void tirarSOAPException() {</pre>

<del><a name="wp220114"></a></del>

        Detail detail = null;

<del><a name="wp219975"></a></del>

        try {

<del><a name="wp219977"></a></del>

          SOAPFactory soapFactory = SOAPFactory.newInstance();<br />      detail = soapFactory.createDetail();

<del><a name="wp220782"></a></del>

        } catch (SOAPException e) {<br />        // 执行某些操作<br />    }

<del><a name="wp219984"></a></del>

        QName faultCode = null;<br />    String faultString = "the fault string";<br />    String faultActor = "the fault actor";<br />    throw new SOAPFaultException(faultCode, faultString, faultActor, detail);<br />  }  
    }

<del><a name="wp222331"></a></del>以上示例使用 `SOAPFactory` 的默认实现。

<del><a name="wp222284"></a></del>

**警告：**

如果您创建和引发自己的异常（而不是使用 `SOAPFaultException`），而且您的异常类的两个或多个属性具有相同数据类型，那么还必须__为这些属性创建 setter 方法，即使 JAX-RPC 规范并不要求这样做也是如此。这是因为在 WebLogic Web Service 通过 SOAP 消息接收异常时，会将 XML 转换为 Java 异常类，如果不使用对应的 setter 方法，则无法确定 XML 元素与类属性之间的映射关系。

<hr noshade="noshade" />

#### <del><a name="wp214603"></a></del>从 JWS 文件调用另一 Web Service

<del><a name="wp215554"></a></del>在 JWS 文件中可以调用另一 Web Service，它既可以部署在 WebLogic Server 上，也可以部署在 .NET 等其他应用服务器上。执行该操作的步骤与[从独立 JAX-RPC Java 客户端调用 Web Service](http://www.beansoft.biz/weblogic/docs92/webserv/use_cases.html#wp219050)中介绍的对应步骤相似，只是不运行 `clientgen` Ant 任务生成客户端存根控件，而是包含构建调用 Web Service 以生成客户端存根控件的 `jwsc` Ant 任务的 `<clientgen>` 子元素。然后，与在独立客户端应用程序中一样，在 JWS 文件中使用标准 JAX-RPC API。

<del><a name="wp214604"></a></del>有关详细说明，请参阅[从其他 Web Service 中调用 Web Service](http://www.beansoft.biz/weblogic/docs92/webserv/client.html#wp213814)。

<hr noshade="noshade" />

#### <del><a name="wp223990"></a></del><del><a name="misc"></a></del>使用 JWS 批注和 API 编写其他杂项功能

<del><a name="wp223994"></a></del>下列部分介绍通过在 JWS 文件中指定特定 JWS 批注或使用 WebLogic Web Service API 可以编写的其他杂项功能：

  * <del><a name="wp224082"></a></del>[流 SOAP 附件](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp223999)
  * <del><a name="wp224090"></a></del>[使用 SOAP 1.2](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp224000)
  * <del><a name="wp224095"></a></del>[指定操作在事务内运行](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp224001)
  * <del><a name="wp224908"></a></del>[获取 HttpServletRequest/Response 对象](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html#wp224692)

##### <del><a name="wp223999"></a></del><del><a name="stream_attach"></a></del>流 SOAP 附件

<del><a name="wp224160"></a></del>通过使用 `@weblogic.jws.StreamAttachments` JWS 批注，可以指定 Web Service 在读取包含附件的入站 SOAP 消息时使用流 API，而不是执行服务将整条消息读取到内存中的默认行为。此功能可以提高 SOAP 消息特别大的 Web Service 的性能。

<del><a name="wp224481"></a></del>有关指定应使用流的附件的示例，请参阅 [weblogic.jws.StreamAttachments](http://www.beansoft.biz/weblogic/docs92/webserv/annotations.html#wp1079627)。

##### <del><a name="wp224000"></a></del>使用 SOAP 1.2

<del><a name="wp224188"></a></del>默认情况下，WebLogic Web Service 使用简单对象访问协议 (SOAP) 版本 1.1，作为在 Web Service 与其客户端之间传输数据和调用呼叫时的消息格式。要指定 Web Service 使用 SOAP 版本 1.2，请在 JWS 文件中使用类级别 `@`[`weblogic.jws.Binding`](http://www.beansoft.biz/weblogic/docs92/webserv/annotations.html#wp1081014)批注并将其单个特性设置为值 `Binding.Type.SOAP12`，如下例所示（相关代码用粗体显示）：

<del><a name="wp224207"></a></del>

<pre>package examples.webservices.soap12;</pre>

<del><a name="wp224209"></a></del>

<pre>import javax.jws.WebMethod;<br />import javax.jws.WebService;</pre>

<del><a name="wp224212"></a></del>

<pre>import weblogic.jws.WLHttpTransport;<br /><code>import weblogic.jws.Binding;</code></pre>

<del><a name="wp224215"></a></del>

<pre>@WebService(name="SOAP12PortType",<br />            serviceName="SOAP12Service",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp224219"></a></del>

<pre>@WLHttpTransport(contextPath="soap12",<br />                 serviceUri="SOAP12Service",<br />                 portName="SOAP12ServicePort")</pre>

<del><a name="wp224223"></a></del>

    @Binding(Binding.Type.SOAP12)

<del><a name="wp224225"></a></del>

<pre>/**<br /> * 此 JWS 文件形成了带有下列单个操作的简单 Java 类实现的 WebLogic<br /> * Web Service 的基础：sayHello。该类绑定了 SOAP 1.2。<br /> *<br />*<br /> */</pre>

<del><a name="wp224232"></a></del>

<pre>public class SOAP12Impl {</pre>

<del><a name="wp224234"></a></del>

<pre>@WebMethod()<br />  public String sayHello(String message) {<br />    System.out.println("sayHello:" + message);<br />    return "Here is the message: '" + message + "'";<br />  }<br />}</pre>

<del><a name="wp224283"></a></del>除设置该批注外，无需执行任何其他操作即可指定 Web Service 使用SOAP 1.2，包括更改调用 Web Service 的客户端应用程序；WebLogic Web Service 运行时会完成其他操作。

##### <del><a name="wp224001"></a></del>指定操作在事务内运行

<del><a name="wp224144"></a></del>默认情况下，当客户端应用程序调用 WebLogic Web Service 操作时，该操作调用会在事务上下文以外发生。如果希望操作在事务内运行，请在 JWS 文件中指定 `@`[`weblogic.jws.Transactional`](http://www.beansoft.biz/weblogic/docs92/webserv/annotations.html#wp1057803) 批注，然后将布尔特性 `value` 设置为 `true`，如下例所示（相关代码用粗体显示）：

<del><a name="wp224322"></a></del>

<pre>package examples.webservices.transactional;</pre>

<del><a name="wp224324"></a></del>

<pre>import javax.jws.WebMethod;<br />import javax.jws.WebService;</pre>

<del><a name="wp224327"></a></del>

<pre>import weblogic.jws.WLHttpTransport;<br /><code>import weblogic.jws.Transactional;</code></pre>

<del><a name="wp224330"></a></del>

<pre>@WebService(name="TransactionPojoPortType",<br />            serviceName="TransactionPojoService",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp224334"></a></del>

<pre>@WLHttpTransport(contextPath="transactionsPojo",<br />                 serviceUri="TransactionPojoService",<br />                 portName="TransactionPojoPort")</pre>

<del><a name="wp224338"></a></del>

<pre>/**<br /> * 此 JWS 文件形成了带有下列单个操作的简单 WebLogic<br /> * Web Service 的基础：sayHello。此操作作为事务的一部分<br /> * 执行。<br />*<br /> */</pre>

<del><a name="wp224346"></a></del>

<pre>public class TransactionPojoImpl {</pre>

<del><a name="wp224348"></a></del>

<pre>@WebMethod()<br />  <code>@Transactional(value=true)&lt;br /></code>  public String sayHello(String message) {<br />    System.out.println("sayHello:" + message);<br />    return "Here is the message: '" + message + "'";<br />  }<br />}</pre>

<del><a name="wp224405"></a></del>如果希望 Web Service 的所有__操作都在事务内运行，请在类级别指定 `@Transactional` 批注。如果仅希望在事务中运行操作的子集，请在方法级别指定批注。如果存在冲突，方法级别的值将替代类级别的值。

<del><a name="wp224409"></a></del>有关其他特性的信息，请参阅 [weblogic.jws.Transactional](http://www.beansoft.biz/weblogic/docs92/webserv/annotations.html#wp1057803)。

##### <del><a name="wp224692"></a></del>获取 HttpServletRequest/Response 对象

<del><a name="wp224696"></a></del>如果您的 Web Service 使用 HTTP 作为传输协议，则使用 `<a href="http://e-docs.bea.com/wls/docs92/javadocs/weblogic/wsee/connection/transport/servlet/package-summary.html">weblogic.wsee.connection.transport.servlet.HttpTransportUtils</a>` API 可以从 JAX-RPC `ServletEndpointContext` 对象获取 `javax.servlet.http.HttpServletRequest` 和`javax.servlet.http.HttpServletResponse` 对象，如以下示例所示（相应的代码以粗体表示，在示例后有相应的说明）：

<del><a name="wp224735"></a></del>

<pre>package examples.webservices.http_transport_utils;</pre>

<del><a name="wp224737"></a></del>

    import javax.xml.rpc.server.ServiceLifecycle;<br />import javax.xml.rpc.server.ServletEndpointContext;<br />import javax.xml.rpc.ServiceException;

<del><a name="wp224741"></a></del>

    import javax.servlet.http.HttpServletRequest;<br />import javax.servlet.http.HttpServletResponse;

<del><a name="wp224744"></a></del>

<pre>import javax.jws.WebMethod;<br />import javax.jws.WebService;</pre>

<del><a name="wp224747"></a></del>

<pre>import weblogic.jws.WLHttpTransport;</pre>

<del><a name="wp224749"></a></del>

    import weblogic.wsee.connection.transport.servlet.HttpTransportUtils;

<del><a name="wp224752"></a></del>

<pre>@WebService(name="HttpTransportUtilsPortType",<br />            serviceName="HttpTransportUtilsService",<br />            targetNamespace="http://example.org")</pre>

<del><a name="wp224756"></a></del>

<pre>@WLHttpTransport(contextPath="servlet", serviceUri="HttpTransportUtils",<br />                 portName="HttpTransportUtilsPort")</pre>

<del><a name="wp224763"></a></del>

    public class HttpTransportUtilsImpl implements ServiceLifecycle {

<del><a name="wp224765"></a></del>

      private ServletEndpointContext wsctx = null;

<del><a name="wp224767"></a></del>

      public void init(Object context) throws ServiceException {<br />    System.out.println("ServletEndpointContext inited...");<br />    wsctx = (ServletEndpointContext)context;<br />  }

<del><a name="wp224772"></a></del>

      public void destroy() {<br />    System.out.println("ServletEndpointContext destroyed...");<br />    wsctx = null;<br />  }

<del><a name="wp224798"></a></del>

<pre>@WebMethod()<br />  public String getServletRequestAndResponse() {</pre>

<del><a name="wp224801"></a></del>

        HttpServletRequest request =<br />       HttpTransportUtils.getHttpServletRequest(wsctx.getMessageContext());<br />    HttpServletResponse response =<br />       HttpTransportUtils.getHttpServletResponse(wsctx.getMessageContext());

<del><a name="wp224806"></a></del>

<pre>System.out.println("HttpTransportUtils API used successfully.");<br />    return "HttpTransportUtils API used successfully";</pre>

<del><a name="wp224808"></a></del>

<pre>}</pre>

<del><a name="wp224705"></a></del>

<pre>}</pre>

<del><a name="wp224819"></a></del>上述示例的重要部分如下：

  * <del><a name="wp224825"></a></del>导入所需的 JAX-RPC 和 Servlet 类：<del><a name="wp224918"></a></del> 
    <pre>import javax.xml.rpc.server.ServiceLifecycle;<br />import javax.xml.rpc.server.ServletEndpointContext;<br />import javax.xml.rpc.ServiceException;</pre>
    
    <del><a name="wp224921"></a></del>
    
    <pre>import javax.servlet.http.HttpServletRequest;<br />import javax.servlet.http.HttpServletResponse;</pre>

  * <del><a name="wp224931"></a></del>导入 WebLogic `HttpTransportUtils` 类：<del><a name="wp224935"></a></del> 
    <pre>import weblogic.wsee.connection.transport.servlet.HttpTransportUtils;</pre>

  * <del><a name="wp224950"></a></del>由于您将查询 JAX-RPC 消息上下文，因此您的 JWS 文件必须明确实现 `ServiceLifecycle`：<del><a name="wp224954"></a></del> 
    <pre>public class HttpTransportUtilsImpl implements ServiceLifecycle </pre>

  * <del><a name="wp224973"></a></del>创建 `ServletEndpointContext` 数据类型的变量：<del><a name="wp224977"></a></del> 
    <pre>private ServletEndpointContext wsctx = null;</pre>

  * <del><a name="wp224992"></a></del>由于 JWS 文件实现 `ServiceLifecycle`，因此您还必须实现 `init` 和 `destroy` 生命周期方法：<del><a name="wp225014"></a></del> 
    <pre>public void init(Object context) throws ServiceException {<br />    System.out.println("ServletEndpointContext inited...");<br />    wsctx = (ServletEndpointContext)context;<br />  }<br />  public void destroy() {<br />    System.out.println("ServletEndpointContext destroyed...");<br />    wsctx = null;<br />  }</pre>

  * <del><a name="wp225040"></a></del>最后，在实现 Web Service 操作的方法中，使用 `ServletEndpointContext` 对象获取 `HttpServletRequest` 和 `HttpServletResponse` 对象：<del><a name="wp225049"></a></del> 
    <pre>HttpServletRequest request =<br />  HttpTransportUtils.getHttpServletRequest(wsctx.getMessageContext());<br />HttpServletResponse response =<br />  HttpTransportUtils.getHttpServletResponse(wsctx.getMessageContext());</pre>

<hr noshade="noshade" />

#### <del><a name="wp209992"></a></del>JWS 编程最佳实践

<del><a name="wp214270"></a></del>以下列表提供了 JWS 文件编程时的部分最佳实践：

  * <del><a name="wp209996"></a></del>在创建 document-literal-bare Web Service 时，使用 `@WebParam` JWS 批注确保给定 Web Service 的所有操作的所有输入参数都具有唯一名称。 
    <del><a name="wp214271"></a></del>document-literal-bare Web Service 的性质决定了如果不明确使用 `@WebParam` 批注指定输入参数的名称，WebLogic Server 会创建一个名称，所以可能造成 Web Service 内的参数名称重复。

  * <del><a name="wp221630"></a></del>一般而言，document-literal-wrapped Web Service 是互操作性最强的 Web Service 类型。 
  * <del><a name="wp210004"></a></del>使用 `@WebResult` JWS 批注明确设置操作返回值的名称，而不是始终依赖于硬编码名称 `return`，如果没有在 JWS 文件中使用 `@WebResult` 批注，则该硬编码名称是返回值的默认名称。 
  * <del><a name="wp210006"></a></del>如果希望控制在调用 Web Service 时遇到错误的情况下传递回客户端应用程序的异常信息，请在 JWS 文件中使用 SOAPFaultExceptions。 
  * <del><a name="wp214269"></a></del>虽然并非必需操作，但 BEA 建议您始终在 JWS 文件中指定 WebLogic 特定 `@WLHttpTransport` 批注的 `portName` 特性。如果不指定此特性，`jwsc` Ant 任务将在生成 WSDL 文件时为您生成端口名称，但该名称可能不会非常便于用户记忆。因此，不会为在客户端应用程序中用于调用 Web Service 的 `getXXX()` 方法指定适当名称。为确保客户端应用程序在调用 Web Service 时使用最便于用户使用的方法，请使用 `portName` 特性指定 Web Service 端口的相对名称。

[<img title="返回顶部" border="0" alt="返回顶部" src="http://www.beansoft.biz/global_resources/images/backtop.gif" width="90" height="25" />](http://www.beansoft.biz/weblogic/docs92/webserv/jws.html) [<img border="0" alt="上一页" src="http://www.beansoft.biz/global_resources/images/prevtop.gif" />](http://www.beansoft.biz/weblogic/docs92/webserv/setenv.html) [<img border="0" alt="下一页" src="http://www.beansoft.biz/global_resources/images/nexttop.gif" />](http://www.beansoft.biz/weblogic/docs92/webserv/advanced.html)

[© 2008 BEA Systems](http://edocs.bea.com.cn/copyright.html)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic Server 9 的 Web Service 编程之 JWS](http://www.beansoft.biz/2010/08/05/weblogic-server-9-%e7%9a%84-web-service-%e7%bc%96%e7%a8%8b%e4%b9%8b-jws-%e8%bd%ac%e8%87%aawlsfans/)