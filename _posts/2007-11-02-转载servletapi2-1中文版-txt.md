---
id: 1130
title: '[转载]servletAPI2.1中文版.txt'
date: 2007-11-02T14:23:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1130
permalink: '/2007/11/02/%e8%bd%ac%e8%bd%bdservletapi2-1%e4%b8%ad%e6%96%87%e7%89%88-txt/'
views:
  - "3524"
original_post_id:
  - "1130"
categories:
  - Java EE
  - 图书视频
---
2007-11-02 10:14

<http://www.blogjava.net/Files/beansoft/servletAPI2.1中文版.txt.zip>

译者前言：   
近来在整理有关Servlet资料时发现，在网上竟然找不到一份中文的Java Servlet API的说明文档，而在有一本有关JSP的书后面附的Java Servlet API说明竟然不全，而这份文档的2.1a版在1998年的11月份就已定稿。所以我决定翻译一份中文的文档（其中一些与技术关系不大的部分已被略去），有兴趣的读者可以从http://java.sun.com/products/servlet/2.1/servletspec-2.1.zip下载原文阅读。

Java Servlet API说明文档（2.1a版）   
1998年11月

绪言   
这是一份关于2.1版Java Servlet API的说明文档，作为对这本文档的补充，你可以到http://java.sun.com/products/servlet/index.html下面下载Javadoc格式的文档。

谁需要读这份文档   
这份文档描述了Java Servlet API的最新版本2.1版。所以，这本书对于Servlet的开发者及servlet引擎的开发者同样适用。

Java Servlet API的组成   
Java Servlet API由两个软件包组成：一个是对应HTTP的软件包，另一个是不对应HTTP的通用的软件包。这两个软件包的同时存在使得Java Servlet API能够适应将来的其他请求-响应的协议。   
这份文档以及刚才提及的Javadoc格式的文档都描述了这两个软件包，Javadoc格式的文档还描述了你应该如何使用这两个软件包中的所有方法。

有关规范   
你也许对下面的这些Internet规范感兴趣，这些规范将直接影响到Servlet API的发展和执行。你可以从http://info.internet.isi.edu/7c/in-notes/rfc/.cache 找到下面提到的所有这些RFC规范。   
RFC 1738 统一资源定位器(URL)   
RFC 1808 相关统一资源定位器   
RFC 1945 超文本传输协议&#8211;HTTP/1.0   
RFC 2045 多用途Internet邮件扩展(多用途网际邮件扩充协议(MIME))第一部分:Internet信息体格式   
RFC 2046 多用途Internet邮件扩展(多用途网际邮件扩充协议(MIME))第二部分:媒体类型   
RFC 2047 多用途网际邮件扩充协议(MIME)(多用途Internet邮件扩展)第三部分:信息标题扩展用于非ASCII文本   
RFC 2048 多用途Internet邮件扩展(多用途网际邮件扩充协议(MIME))第四部分: 注册步骤   
RFC 2049 多用途Internet邮件扩展(多用途网际邮件扩充协议(MIME))第五部分:一致性标准和例子   
RFC 2068 超文本传输协议 &#8212; HTTP/1.1   
RFC 2069 一个扩展HTTP:摘要访问鉴定   
RFC 2109 HTTP状态管理机制   
RFC 2145 HTTP 版本号的使用和解释   
RFC 2324 超文本Coffee Pot控制协议 (HTCPCP/1.0)   
万维网协会（[http://www.w3.org）管理着这些协议的规范和执行。](http://www.w3.xn--org)-tv5f62wojc020c4e7amhf96bk6wfmxj3qbgf75ig6s./)

有关Java Servlets   
JavaTM servlets是一个不受平台约束的Java小程序，它可以被用来通过多种方法扩充一个Web服务器的功能。你可以把Servlet理解成Server上的applets，它被编译成字节码，这样它就可以被动态地载入并用效地扩展主机的处理能力。   
Servlet与applets不同的地方是，它不运行在Web浏览器或其他图形化的用户界面上。Servlet通过servlet引擎运行在Web服务器中，以执行请求和响应，请求、响应的典型范例是HTTP协议。   
一个客户端程序，可以是一个Web浏览器，或者是非其他的可以连接上Internet的程序，它会访问Web服务器并发出请求。这个请求被运行在Web服务器上的Servlet引擎处理，并返回响应到Servlet。Servlet通过HTTP将这个响应转发到客户端。   
在功能上，Servlet与CGI、NSAPI有点类似，但是，与他们不同的是：Servlet具有平台无关性。

Java Servlet概论   
Servlet与其他普通的server扩展机制有以下进步：   
因为它采用了不同的进程处理模式，所以它比CGI更快。   
它使用了许多Web服务器都支持的标准的API。   
它继承了Java的所有优势，包括易升级以及平台无关性。   
它可以调用Java所提供的大量的API的功能模块。   
这份文档说明了Java Servlet API的类和接口的方法。有关更多的信息，请参看下面的API说明。

Servlet的生命周期   
一个Java servlet具有一个生命周期，这个生命周期定义了一个Servlet如何被载入并被初始化，如何接收请求并作出对请求的响应，如何被从服务中清除。Servlet的生命周期被javax.servlet.Servlet这个接口所定义。   
所有的Java Servlet都会直接地或间接地执行javax.servlet.Servlet接口，这样它才能在一个Servlet引擎中运行。Servlet引擎是Web 服务器按照Java Servlet API定制的扩展。Servlet引擎提供网络服务，能够理解MIME请求，并提供一个运行Servlet的容器。   
javax.servlet.Servlet接口定义了在Servlet的生命周期中特定时间以及特定顺序被调用的方法。

Servlet的解析和载入   
Servlet引擎解析并载入一个Servlet，这个过程可以发生在引擎启动时，需要一个Servlet去响应请求时，以及在此之间的任何时候。   
Servlet引擎利用Java类载入工具载入一个Servlet，Servlet引擎可以从一个本地的文件系统、一个远程的文件系统以及网络载入Servlet。

Servlet的初始化   
Servlet引擎载入Servlet后，Servlet引擎必须对Servlet进行初始化，在这一过程中，你可以读取一些固定存储的数据、初始化JDBC的连接以及建立与其他资源的连接。   
在初始化过程中，javax.servlet.Servlet接口的init()方法提供了Servlet的初始化信息。这样，Servlet可以对自己进行配置。   
init()方法获得了一个Servlet配置对象（ServletConfig）。这个对象在Servlet引擎中执行，并允许Servlet通过它获处相关参数。这个对象使得Servlet能够访问ServletContext对象。

Servlet处理请求   
Servlet被初始化之后，它已经可以处理来自客户端的请求，每一个来自客户端的请求都被描述成一个ServletRequest对象，Servlet的响应被描述成一个ServletResponse对象。   
当客户端发出请求时，Servlet引擎传递给Servlet一个ServletRequest对象和一个ServletResponse对象，这两个对象作为参数传递到service()方法中。   
Servlet也可以执行ServletRequest接口和ServletResponse接口。ServletRequest接口使得Servlet有权使用客户端发出的请求。Servlet可以通过ServletInputStream对象读取请求信息。   
ServletResponse接口允许Servlet建立响应头和状态代码。通过执行这个接口，Servlet有权使用ServletOutputStream类来向客户端返回数据。

多线程和映射   
在多线程的环境下，Servlet必须能处理许多同时发生的请求。例外的情况是这个Servlet执行了SingleThreadModel接口，如果是那样的话，Servlet只能同时处理一个请求。   
Servlet依照Servlet引擎的映射来响应客户端的请求。一个映射对包括一个Servlet实例以及一个Servlet返回数据的URL，例如：HelloServlet with /hello/index.html。   
然而，一个映射可能是由一个URL和许多Servlet实例组成，例如：一个分布式的Servlet引擎可能运行在不止一个的服务器中，这样的话，每一个服务器中都可能有一个Servlet实例，以平衡进程的载入。作为一个Servlet的开发者，你不能假定一个Servlet只有一个实例。

Servlet的卸载   
Servlet引擎并不必需保证一个Servlet在任何时候或在服务开启的任何时候都被载入。Servlet引擎可以自由的在任何时候使用或清除一个Servlet。因此，我们不能依赖一个类或实例来存储重要的信息。   
当Servlet引擎决定卸载一个Servlet时（例如，如果这个引擎被关闭或者需要让资源），这个引擎必须允许Servlet释放正在使用的资源并存储有关资料。为了完成以上工作，引擎会调用Servlet的destroy()方法。   
在卸载一个Servlet之前，Servlet引擎必须等待所有的service()方法完成或超时结束（Servlet引擎会对超时作出定义）。当一个Servlet被卸载时，引擎将不能给Servlet发送任何请求。引擎必须释放Servlet并完成无用存储单元的收集

Servlet映射技术   
作为一个Servlet引擎的开发者，你必须对于如何映射客户端的请求到Servlet有大量的适应性。这份说明文档不规定映射如何发生。但是，你必须能够自由地运用下面的所有技术：

映射一个Servlet到一个URL   
例如，你可以指定一个特殊的Servlet它仅被来自/feedback/index.html的请求调用。

映射一个Servlet到以一个指定的目录名开始的所有URL   
例如，你可以映射一个Servlet到/catalog，这样来自/catalog/、 /catalog/garden和/catalog/housewares/index.html的请求都会被映射到这个Servlet。但是来自/catalogtwo 或/catalog.html的请求没被映射。

映射一个Servlet到所有以一个特定的字段结尾的所有URL   
例如，你可以映射一个来自于所有以in.thtml结尾的请求到一个特定的Servlet。

映射一个Servlet到一个特殊的URL /servlet/servlet_name。   
例如，如果你建立了一个名叫listattributes的Servlet，你可以通过使用/servlet/listattributes来访问这个Servlet。

通过类名调用Servlet   
例如，如果Servlet引擎接收了来自/servlet/com.foo.servlet.MailServlet的请求，Servlet引擎会载入这个com.foo.servlet.MailServlet类，建立实例，并通过这个Servlet来处理请求。

Servlet环境   
ServletContext接口定义了一个Servlet环境对象，这个对象定义了一个在Servlet引擎上的Servlet的视图。通过使用这个对象，Servlet可以记录事件、得到资源并得到来自Servlet引擎的类（例如RequestDispatcher对象）。一个Servlet只能运行在一个Servlet环境中，但是不同的Servlet可以在Servlet引擎上有不同的视图。   
如果Servlet引擎支持虚拟主机，每个虚拟主机有一个Servlet环境。一个Servlet环境不能在虚拟主机之间共享。   
Servlet引擎能够允许一个Servlet环境有它自己的活动范围。   
例如，一个Servlet环境是属于bank应用的，它将被映射到/bank目录下。在这种情况下，一个对getContext方法的调用会返回/bank的Servlet环境。

HTTP会话   
HTTP是一个没有状态的协议。要建立一个有效的Web服务应用，你必须能够识别一个连续的来自远端的客户机的唯一的请求。随着时间的过去，发展了许多会话跟踪的技术，但是使用起来都比较麻烦。   
Java Servlet API提供了一个简单的接口，通过这个接口，Servlet引擎可以有效地跟踪用户的会话。

建立Session   
因为HTTP是一个请求-响应协议，一个会话在客户机加入之前会被认为是一个新的会话。加入的意思是返回会话跟踪信息到服务器中，指出会话已被建立。在客户端加入之前，我们不能判断下一个客户端请求是目前会话的一部分。   
在下面的情况下，Session会被认为是新的Session。   
客户端的Session在此之前还不知道   
客户端选择不加入Session，例如，如果客户端拒绝接收来自服务器的cookie   
作为一个Servlet的开发者，你必须决定你的Web应用是否处理客户机不加入或不能加入Session。服务器会在Web服务器或Servlet规定的时间内维持一个Session对象。当Session终止时，服务器会释放Session对象以及所有绑定在Session上的对象。   
绑定对象到Session中   
如果有助于你处理应用的数据需求，你也许需要绑定对象到Session中，你可以通过一个唯一的名字绑定任何的对象到Session中，这时，你需要使用HttpSession对象。任何绑定到Session上的对象都可以被处理同一会话的Servlet调用。   
有些对象可能需要你知道什么时候会被放置到Session中或从Session中移开。你可以通过使用HttpSessionBindingListener接口获得这些信息。当你的应用存储数据到Session中，或从Session中清除数据，Servlet都会通过HttpSessionBindingListener检杳什么类被绑定或被取消绑定。这个接口的方法会通报被绑定或被取消绑定的对象。   
API对象的说明   
这一部分包含了对Java Servlet API的全部类和接口的详细说明。这个说明与Javadoc API差不多，但是这份文档提供了更多的信息。   
API包含了两个软件包，十二个接口和九个类。   
软件包：javax.servlet   
所包含的接口：RequestDispatcher；Servlet；ServletConfig；ServletContext；ServletRequest；ServletResponse；SingleThreadModel。   
所包含的类：GenericServlet；ServletInputStream；ServletOutputStream；ServletException；UnavailableException。

一、RequestDispatcher接口：   
定义：   
public interface RequestDispatcher;   
定义一个对象，从客户端接收请求，然后将它发给服务器的可用资源（例如Servlet、CGI、HTML文件、JSP文件）。Servlet引擎创建request dispatcher对象，用于封装由一个特定的URL定义的服务器资源。   
这个接口是专用于封装Servlet的，但是一个Servlet引擎可以创建request dispatcher对象用于封装任何类型的资源。   
request dispatcher对象是由Servlet引擎建立的，而不是由Servlet开发者建立的。   
方法   
1、forward   
public void forward(ServletRequest request, ServletReponse response)   
throws ServletException, IOException;   
被用来从这个Servlet向其它服务器资源传递请求。当一个Servlet对响应作了初步的处理，并要求其它的对象对此作出响应时，可以使用这个方法。   
当request对象被传递到目标对象时，请求的URL路径和其他路径参数会被调整为反映目标对象的目标URL路径。   
如果已经通过响应返回了一个ServletOutputStream对象或PrintWriter对象，这个方法将不能使用，否则，这个方法会抛出一个IllegalStateException。   
2、include   
public void include(ServletRequest request, ServletResponse response)   
throws ServletException, IOException   
用来包括发送给其他服务器资源的响应的内容。本质上来说，这个方法反映了服务器端的内容。   
请求对象传到目标对象后会反映调用请求的请求URL路径和路径信息。这个响应对象只能调用这个Servlet的ServletOutputStream对象和PrintWriter对象。   
一个调用include的Servlet不能设置头域，如果这个Servlet调用了必须设置头域的方法（例如cookie），这个方法将不能保证正常使用。作为一个Servlet开发者，你必须妥善地解决那些可能直接存储头域的方法。例如，即使你使用会话跟踪，为了保证session的正常工作，你必须在一个调用include的Servlet之外开始你的session

二、Servlet接口。   
定义   
public interface Servlet   
这个接口定义了一个Servlet：一个在Web服务器上继承了这个功能的Java类。   
方法   
1、init   
public void init(ServletConfig config) throws ServletException;   
Servlet引擎会在Servlet实例化之后，置入服务之前精确地调用init方法。在调用service方法之前，init方法必须成功退出。   
如果init方法抛出一个ServletException，你不能将这个Servlet置入服务中，如果init方法在超时范围内没完成，我们也可以假定这个Servlet是不具备功能的，也不能置入服务中。   
2、service   
public void service(ServletRequest request, ServletResponse response)   
throws ServletException, IOException;   
Servlet引擎调用这个方法以允许Servlet响应请求。这个方法在Servlet未成功初始化之前无法调用。在Servlet被初始化之前，Servlet引擎能够封锁未决的请求。   
在一个Servlet对象被卸载后，直到一个新的Servelt被初始化，Servlet引擎不能调用这个方法   
3、destroy   
public void destroy();   
当一个Servlet被从服务中去除时，Servlet引擎调用这个方法。在这个对象的service方法所有线程未全部退出或者没被引擎认为发生超时操作时，destroy方法不能被调用。   
4、getServletConfig   
public ServletConfig getServletConfig();   
返回一个ServletConfig对象，作为一个Servlet的开发者，你应该通过init方法存储ServletConfig对象以便这个方法能返回这个对象。为了你的便利，GenericServlet在执行这个接口时，已经这样做了。   
5、getServletInfo   
public String getServletInfo();   
允许Servlet向主机的Servlet运行者提供有关它本身的信息。返回的字符串应该是纯文本格式而不应有任何标志（例如HTML，XML等）。

三、ServletConfig接口   
定义   
public interface ServletConfig   
这个接口定义了一个对象，通过这个对象，Servlet引擎配置一个Servlet并且允许Servlet获得一个有关它的ServletContext接口的说明。每一个ServletConfig对象对应着一个唯一的Servlet。   
方法   
1、getInitParameter   
public String getInitParameter(String name);   
这个方法返回一个包含Servlet指定的初始化参数的String。如果这个参数不存在，返加空值。   
2、getInitParameterNames   
public Enumeration getInitParameterNames();   
这个方法返回一个列表String对象，该对象包括Servlet的所有初始化参数名。如果Servlet没有初始化参数，getInitParameterNames返回一个空的列表。   
3、getServletContext   
public ServletContext getServletContext();   
返回这个Servlet的ServletContext对象。

四、ServletContext接口   
定义   
public interface ServletContext   
定义了一个Servlet的环境对象，通过这个对象，Servlet引擎向Servlet提供环境信息。   
一个Servlet的环境对象必须至少与它所驻留的主机是一一对应的。在一个处理多个虚拟主机的Servlet引擎中（例如，使用了HTTP1.1的主机头域），每一个虚拟主机必须被视为一个单独的环境。此外，Servlet引擎还可以创建对应于一组Servlet的环境对象。   
方法   
1、getAttribute   
public Object getAttribute(String name);   
返回Servlet环境对象中指定的属性对象。如果该属性对象不存在，返回空值。这个方法允许访问有关这个Servlet引擎的在该接口的其他方法中尚未提供的附加信息。   
2、getAttributeNames   
public Enumeration getAttributeNames();   
返回一个Servlet环境对象中可用的属性名的列表。   
3、getContext   
public ServletContext getContext(String uripath);   
返回一个Servlet环境对象，这个对象包括了特定URI路径的Servlets和资源，如果该路径不存在，则返回一个空值。URI路径格式是/dir/dir/filename.ext。   
为了安全，如果通过这个方法访问一个受限制的Servlet的环境对象，会返回一个空值。   
4、getMajorVersion   
public int getMajorVersion();   
返回Servlet引擎支持的Servlet API的主版本号。例如对于2.1版，这个方法会返回一个整数2。   
5、getMinorVersion   
public int getMinorVersion();   
返回Servlet引擎支持的Servlet API的次版本号。例如对于2.1版，这个方法会返回一个整数2。   
6、getMimeType   
public String getMimeType(String file);   
返回指定文件的MIME类型，如果这种MIME类型未知，则返回一个空值。MIME类型是由Servlet引擎的配置决定的。   
7、getRealPath   
public String getRealPath(String path);   
一个符合URL路径格式的指定的虚拟路径的格式是：/dir/dir/filename.ext。用这个方法，可以返回与一个符合该格式的虚拟路径相对应的真实路径的String。这个真实路径的格式应该适合于运行这个Servlet引擎的计算机（包括其相应的路径解析器）。   
不管是什么原因，如果这一从虚拟路径转换成实际路径的过程不能执行，该方法将会返回一个空值。   
8、getResource   
public URL getResource(String uripath);   
返回一个URL对象，该对象反映位于给定的URL地址（格式：/dir/dir/filename.ext）的Servlet环境对象已知的资源。无论URLStreamHandlers对于访问给定的环境是不是必须的，Servlet引擎都必须执行。如果给定的路径的Servlet环境没有已知的资源，该方法会返回一个空值。   
这个方法和java.lang.Class的getResource方法不完全相同。java.lang.Class的getResource方法通过装载类来寻找资源。而这个方法允许服务器产生环境变量给任何资源的任何Servlet，而不必依赖于装载类、特定区域等等。   
9、getResourceAsStream   
public InputStream getResourceAsStream(String uripath);   
返回一个InputStream对象，该对象引用指定的URL的Servlet环境对象的内容。如果没找到Servlet环境变量，就会返回空值，URL路径应该具有这种格式：/dir/dir/filename.ext。   
这个方法是一个通过getResource方法获得URL对象的方便的途径。请注意，当你使用这个方法时，meta-information（例如内容长度、内容类型）会丢失。   
10、getRequestDispatcher   
public RequestDispatcher getRequestDispatcher(String uripath);   
如果这个指定的路径下能够找到活动的资源(例如一个Servlet，JSP页面，CGI等等)就返回一个特定URL的RequestDispatcher对象，否则，就返回一个空值，Servlet引擎负责用一个request dispatcher对象封装目标路径。这个request dispatcher对象可以用来完全请求的传送。   
11、getServerInfo   
public String getServerInfo();   
返回一个String对象，该对象至少包括Servlet引擎的名字和版本号。   
12、log   
public void log(String msg);   
public void log(String msg, Throwable t);   
public void log(Exception exception, String msg); // 这种用法将被取消   
写指定的信息到一个Servlet环境对象的log文件中。被写入的log文件由Servlet引擎指定，但是通常这是一个事件log。当这个方法被一个异常调用时，log中将包括堆栈跟踪。   
13、setAttribute   
public void setAttribute(String name, Object o);   
给予Servlet环境对象中你所指定的对象一个名称。   
14、removeAttribute   
public void removeAttribute(String name);   
从指定的Servlet环境对象中删除一个属性。   
注：以下几个方法将被取消   
15、getServlet   
public Servlet getServlet(String name) throws ServletException;   
最初用来返回一个指定名称的Servlet，如果没找到就返回一个空值。如果这个Servlet能够返回，这就意味着它已经被初始化，而且已经可以接受service请求。这是一个危险的方法。当调用这个方法时，可能并不知道Servlet的状态，这就可能导致有关服务器状态的问题。而允许一个Servlet访问其他Servlet的这个方法也同样的危险。   
现在这个方法返回一个空值，为了保持和以前版本的兼容性，现在这个方法还没有被取消。在以后的API版本中，该方法将被取消。   
16、getServletNames   
public Enumeration getServletNames();   
最初用来返回一个String对象的列表，该列表表示了在这个Servlet环境下所有已知的Servlet对象名。这个列表总是包含这个Servlet自身。   
基于与上一个方法同样的理由，这也是一个危险的方法。   
现在这个方法返回一个空的列表。为了保持和以前版本的兼容性，现在这个方法还没有被取消。在以后的API版本中，该方法将被取消。   
17、getServlets   
public Enumeration getServlets();   
最初用来返回在这个Servelet环境下所有已知的Servlet对象的列表。这个列表总是包含这个Servlet自身。   
基于与getServlet方法同样的理由，这也是一个危险的方法。   
现在这个方法返回一个空的列表。为了保持和以前版本的兼容性，现在这个方法还没有被取消。在以后的API版本中，该方法将被取消。

五、ServletRequest接口   
定义   
public interface ServletRequest   
定义一个Servlet引擎产生的对象，通过这个对象，Servlet可以获得客户端请求的数据。这个对象通过读取请求体的数据提供包括参数的名称、值和属性以及输入流的所有数据。   
方法   
1、getAttribute   
public Object getAttribute(String name);   
返回请求中指定属性的值，如果这个属性不存在，就返回一个空值。这个方法允许访问一些不提供给这个接口中其他方法的请求信息以及其他Servlet放置在这个请求对象内的数据。   
2、getAttributeNames   
public Enumeration getAttributeNames();   
返回包含在这个请求中的所有属性名的列表。   
3、getCharacterEncoding   
public String getCharacterEncoding();   
返回请求中输入内容的字符编码类型，如果没有定义字符编码类型就返回空值。   
4、getContentLength   
public int getContentLength();   
请求内容的长度，如果长度未知就返回-1。   
5、getContentType   
public String getContentType();   
返回请求数据体的MIME类型，如果类型未知返回空值。   
6、getInputStream   
public ServletInputStream getInputStream() throws IOException;   
返回一个输入流用来从请求体读取二进制数据。如果在此之前已经通过getReader方法获得了要读取的结果，这个方法会抛出一个IllegalStateException。   
7、getParameter   
public String getParameter(String name);   
以一个String返回指定的参数的值，如果这个参数不存在返回空值。例如，在一个HTTP Servlet中，这个方法会返回一个指定的查询语句产生的参数的值或一个被提交的表单中的参数值。如果一个参数名对应着几个参数值，这个方法只能返回通过getParameterValues方法返回的数组中的第一个值。因此，如果这个参数有（或者可能有）多个值，你只能使用getParameterValues方法。   
8、getParameterNames   
public Enumeration getParameterNames();   
返回所有参数名的String对象列表，如果没有输入参数，该方法返回一个空值。   
9、getParameterValues   
public String[] getParameterValues(String name);   
通过一个String对象的数组返回指定参数的值，如果这个参数不存在，该方法返回一个空值。   
10、getProtocol   
public String getProtocol();   
返回这个请求所用的协议，其形式是协议/主版本号.次版本号。例如对于一个HTTP1.0的请求，该方法返回HTTP/1.0。   
11、getReader   
public BufferedReader getReader() throws IOException;   
这个方法返回一个buffered reader用来读取请求体的实体，其编码方式依照请求数据的编码方式。如果这个请求的输入流已经被getInputStream调用获得，这个方法会抛出一个IllegalStateException。   
12、getRemoteAddr   
public String getRemoteAddr();   
返回发送请求者的IP地址。   
13、getRemoteHost   
public String getRemoteHost();   
返回发送请求者的主机名称。如果引擎不能或者选择不解析主机名（为了改善性能），这个方法会直接返回IP地址。   
14、getScheme   
public String getScheme();   
返回请求所使用的URL的模式。例如，对于一个HTTP请求，这个模式就是http。   
15、getServerName   
public String getServerName();   
返回接收请求的服务器的主机名。   
16、getServerPort   
public int getServerPort();   
返回接收请求的端口号。   
17、setAttribute   
public void setAttribute(String name, Object object);   
这个方法在请求中添加一个属性，这个属性可以被其他可以访问这个请求对象的对象（例如一个嵌套的Servlet）使用。   
注：以下方法将被取消   
getRealPath   
public String getRealPath(String path);   
返回与虚拟路径相对应的真实路径，如果因为某种原因，这一过程不能进行，该方法将返回一个空值。   
这个方法和ServletContext接口中的getRealPath方法重复。在2.1版中，ServletContext接口将阐明一个Servlet所能用的所有的路径的映射。该方法执行的结果将会与ServletContext中getRealPath方法的结果完全一样。

六、ServletResponse接口   
定义   
public interface ServletResponse   
定义一个Servlet引擎产生的对象，通过这个对象，Servlet对客户端的请求作出响应。这个响应应该是一个MIME实体，可能是一个HTML页、图象数据或其他MIME的格式。   
方法   
1、getCharacterEncoding   
public String getCharacterEncoding();   
返回MIME实体的字符编码。这个字符编码可以是指定的类型，也可以是与请求头域所反映的客户端所能接受的字符编码最匹配的类型。在HTTP协议中，这个信息被通过Accept-Charset传送到Servlet引擎。   
有关字符编码和MIME的更多信息请参看RFC 2047。   
2、getOutputStream   
public ServletOutputStream getOutputStream() throws IOException;   
返回一个记录二进制的响应数据的输出流。   
如果这个响应对象已经调用getWriter，将会抛出IllegalStateException。   
3、getWriter   
public PrintWriter getWriter throws IOException;   
这个方法返回一个PringWriter对象用来记录格式化的响应实体。如果要反映使用的字符编码，必须修改响应的MIME类型。在调用这个方法之前，必须设定响应的content类型。   
如果没有提供这样的编码类型，会抛出一个UnsupportedEncodingException，如果这个响应对象已调用getOutputStream，会抛出一个getOutputStream。   
4、setContentLength   
public void setContentLength(int length);   
设置响应的内容的长度，这个方法会覆盖以前对内容长度的设定。   
为了保证成功地设定响应头的内容长度，在响应被提交到输出流之前必须调用这个方法。   
5、setContentType   
public void setContentType(String type);   
这个方法用来设定响应的content类型。这个类型以后可能会在另外的一些情况下被隐式地修改，这里所说的另外的情况可能当服务器发现有必要的情况下对MIME的字符设置。   
为了保证成功地设定响应头的content类型，在响应被提交到输出流之前必须调用这个方法。

七、SingleThreadModel接口   
定义   
public interface SingleThreadModel;   
这是一个空接口，它指定了系统如何处理对同一个Servlet的调用。如果一个Servlet被这个接口指定，那么在这个Servlet中的service方法中将不会有两个线程被同时执行。   
Servlet可以通过维持一个各自独立的Servlet实例池，或者通过只让Servlet的service中只有一个线程的方法来实现这个保证。

八、GenericServlet类   
public abstract class GenericServlet implements Servlet,   
ServletConfig, Serializable;   
这个类的存在使得编写Servlet更加方便。它提供了一个简单的方案，这个方案用来执行有关Servlet生命周期的方法以及在初始化时对ServletConfig对象和ServletContext对象进行说明。   
方法   
1、destroy   
public void destroy();   
在这里destroy方法不做任何其他的工作。   
2、getInitParameter   
public String getInitParameter(String name);   
这是一个简便的途径，它将会调用ServletConfig对象的同名的方法。   
3、getInitParameterNames   
public Enumeration getInitParameterNames();   
这是一个简便的途径，它将会调用ServletConfig对象的同名的方法。   
4、getServletConfig   
public ServletConfig getServletConfig();   
返回一个通过这个类的init方法产生的ServletConfig对象的说明。   
5、getServletContext   
public ServletContext getServletContext();   
这是一个简便的途径，它将会调用ServletConfig对象的同名的方法。   
6、getServletInfo   
public String getServletInfo();   
返回一个反映Servlet版本的String。   
7、init   
public void init() throws ServletException;   
public void init(ServletConfig config) throws ServletException;   
init(ServletConfig config)方法是一个对这个Servlet的生命周期进行初始化的简便的途径。   
init()方法是用来让你对GenericServlet类进行扩充的，使用这个方法时，你不需要存储config对象，也不需要调用super.init(config)。   
init(ServletConfig config)方法会存储config对象然后调用init()。如果你重载了这个方法，你必须调用super.init(config)，这样GenericServlet类的其他方法才能正常工作。   
8、log   
public void log(String msg);   
public void log(String msg, Throwable cause);   
通过Servlet content对象将Servlet的类名和给定的信息写入log文件中。   
9、service   
public abstract void service(ServletRequest request, ServletResponse   
response) throws ServletException, IOException;   
这是一个抽象的方法，当你扩展这个类时，为了执行网络请求，你必须执行它。

九、ServletInputStream类   
定义   
public abstract class ServletInputStream extends InputStream   
这个类定义了一个用来读取客户端的请求信息的输入流。这是一个Servlet引擎提供的抽象类。一个Servlet通过使用ServletRequest接口获得了对一个ServletInputStream对象的说明。   
这个类的子类必须提供一个从InputStream接口读取有关信息的方法。   
方法   
1、readLine   
public int readLine(byte[] b, int off, int len) throws IOException;   
从输入流的指定的偏移量开始将指定长度的字节读入到指定的数组中。如果该行所有请求的内容都已被读取，这个读取的过程将结束。如果是遇到了新的一行，新的一行的首个字符也将被读入到数组中。

十、ServletOutputStream类   
定义   
public abstract class ServletOutputStream extends OutputStream   
这是一个由Servlet引擎使用的抽象类。Servlet通过使用ServletResponse接口的使用获得了对一个这种类型的对象的说明。利用这个输出流可以将数据返回到客户端。   
这个类的子类必须提供一个向OutputStream接口写入有关信息的方法。   
在这个接口中，当一个刷新或关闭的方法被调用时。所有数据缓冲区的信息将会被发送到客户端，也就是说响应被提交了。请注意，关闭这种类型的对象时不一定要关闭隐含的socket流。   
方法   
1、print   
public void print(String s) throws IOException;   
public void print(boolean b) throws IOException;   
public void print(char c) throws IOException;   
public void print(int i) throws IOException;   
public void print(long l) throws IOException;   
public void print(float f) throws IOException;   
public void print(double d) throws IOException;   
输出变量到输出流中   
2、println   
public void println() throws IOException;   
public void println(String s) throws IOException;   
public void println(boolean b) throws IOException;   
public void println(char c) throws IOException;   
public void println(int i) throws IOException;   
public void println(long l) throws IOException;   
public void println(float f) throws IOException;   
public void println(double d) throws IOException;   
输出变量到输出流中，并增加一个回车换行符

十一、ServletException类   
定义   
public class ServletException extends Exception   
当Servlet遇到问题时抛出的一个异常。   
构造函数   
public ServletException();   
public ServletException(String message);   
public ServletException(String message, Throwable cause);   
public ServletException(Throwable cause);   
构造一个新的ServletException，如果这个构造函数包括一个Throwable参数，这个Throwable对象将被作为可能抛出这个异常的原因。   
方法   
1、getRootCause   
public Throwable getRootCause();   
如果配置了抛出这个异常的原因，这个方法将返回这个原因，否则返回一个空值。

十二、UnavailableException类   
定义   
public class UnavailableException extends ServletException   
不论一个Servlet是永久地还是临时地无效，都会抛出这个异常。Servlet会记录这个异常以及Servlet引擎所要采取的相应措施。   
临时的无效是指Servlet在某一时间由于一个临时的问题而不能处理请求。例如，在另一个不同的应用层的服务（可能是数据库）无法使用。这个问题可能会自行纠正或者需要采取其他的纠正措施。   
永久的无效是指除非管理员采取措施，这个Servlet将不能处理客户端的请求。例如，这个Servlet配置信息丢失或Servlet的状态被破坏。   
Servlet引擎可以安全地处理包括永久无效在内的这两种异常，但是对临时无效的正常处理可以使得Servlet引擎更健壮。特别的，这时对Servlet的请求只是被阻止（或者是被延期）一段时间，这显然要比在service自己重新启动前完全拒绝请求更为科学。   
构造函数   
public UnavailableException(Servlet servlet, String message);   
public UnavailableException(int seconds, Servlet servlet,   
String message);   
构造一个包含指定的描述信息的新的异常。如果这个构造函数有一个关于秒数的参数，这将给出Servlet发生临时无效后，能够重新处理请求的估计时间。如果不包含这个参数，这意味着这个Servlet永久无效。   
方法   
1、getServlet   
public Servlet getServlet();   
返回报告无效的Servlet。这被Servlet引擎用来识别受到影响的Servlet。   
2、getUnavailableSeconds   
public int getUnavailableSeconds();   
返回Servlet预期的无效时间，如果这个Servlet是永久无效，返回-1。   
3、isPermanent   
public boolean isPermanent();   
如果这个Servlet永久无效，返回布尔值true，指示必须采取一些管理行动以使得这个Servlet可用   
软件包：javax.servlet.http   
所包含的接口：HttpServletRequest；HttpServletResponse；HttpSession；HttpSessionBindingListener；HttpSessionContext。   
所包含的类：Cookie；HttpServlet；HttpSessionBindingEvent；HttpUtils。

一、HttpServletRequest接口   
定义\   
public interface HttpServletRequest extends ServletRequest;   
用来处理一个对Servlet的HTTP格式的请求信息。   
方法   
1、getAuthType   
public String getAuthType();   
返回这个请求的身份验证模式。   
2、getCookies   
public Cookie[] getCookies();   
返回一个数组，该数组包含这个请求中当前的所有cookie。如果这个请求中没有cookie，返回一个空数组。   
3、getDateHeader   
public long getDateHeader(String name);   
返回指定的请求头域的值，这个值被转换成一个反映自1970-1-1日（GMT）以来的精确到毫秒的长整数。   
如果头域不能转换，抛出一个IllegalArgumentException。如果这个请求头域不存在，这个方法返回-1。   
4、getHeader   
public String getHeader(String name);   
返回一个请求头域的值。（译者注：与上一个方法不同的是，该方法返回一个字符串）   
如果这个请求头域不存在，这个方法返回-1。   
5、getHeaderNames   
public Enumeration getHeaderNames();   
该方法返回一个String对象的列表，该列表反映请求的所有头域名。   
有的引擎可能不允许通过这种方法访问头域，在这种情况下，这个方法返回一个空的列表。   
6、getIntHeader   
public int getIntHeader(String name);   
返回指定的请求头域的值，这个值被转换成一个整数。   
如果头域不能转换，抛出一个IllegalArgumentException。如果这个请求头域不存在，这个方法返回-1。   
7、getMethod   
public String getMethod();   
返回这个请求使用的HTTP方法（例如：GET、POST、PUT）   
8、getPathInfo   
public String getPathInfo();   
这个方法返回在这个请求的URL的Servlet路径之后的请求URL的额外的路径信息。如果这个请求URL包括一个查询字符串，在返回值内将不包括这个查询字符串。这个路径在返回之前必须经过URL解码。如果在这个请求的URL的Servlet路径之后没有路径信息。这个方法返回空值。   
9、getPathTranslated   
public String getPathTranslated();   
这个方法获得这个请求的URL的Servlet路径之后的额外的路径信息，并将它转换成一个真实的路径。在进行转换前，这个请求的URL必须经过URL解码。如果在这个URL的Servlet路径之后没有附加路径信息。这个方法返回空值。   
10、getQueryString   
public String getQueryString();   
返回这个请求URL所包含的查询字符串。一个查询字串符在一个URL中由一个&#8221;？&#8221;引出。如果没有查询字符串，这个方法返回空值。   
11、getRemoteUser   
public String getRemoteUser   
返回作了请求的用户名，这个信息用来作HTTP用户论证。   
如果在请求中没有用户名信息，这个方法返回空值。   
12、getRequestedSessionId   
public String getRequestedSessionId();   
返回这个请求相应的session id。如果由于某种原因客户端提供的session id是无效的，这个session id将与在当前session中的session id不同，与此同时，将建立一个新的session。   
如果这个请求没与一个session关联，这个方法返回空值。   
13、getRequestURI   
public String getRequestURI();   
从HTTP请求的第一行返回请求的URL中定义被请求的资源的部分。如果有一个查询字符串存在，这个查询字符串将不包括在返回值当中。例如，一个请求通过/catalog/books?id=1这样的URL路径访问，这个方法将返回/catalog/books。这个方法的返回值包括了Servlet路径和路径信息。   
如果这个URL路径中的的一部分经过了URL编码，这个方法的返回值在返回之前必须经过解码。   
14、getServletPath   
public String getServletPath();   
这个方法返回请求URL反映调用Servlet的部分。例如，一个Servlet被映射到/catalog/summer这个URL路径，而一个请求使用了/catalog/summer/casual这样的路径。所谓的反映调用Servlet的部分就是指/catalog/summer。   
如果这个Servlet不是通过路径匹配来调用。这个方法将返回一个空值。   
15、getSession   
public HttpSession getSession();   
public HttpSession getSession(boolean create);   
返回与这个请求关联的当前的有效的session。如果调用这个方法时没带参数，那么在没有session与这个请求关联的情况下，将会新建一个session。如果调用这个方法时带入了一个布尔型的参数，只有当这个参数为真时，session才会被建立。   
为了确保session能够被完全维持。Servlet开发者必须在响应被提交之前调用该方法。   
如果带入的参数为假，而且没有session与这个请求关联。这个方法会返回空值。   
16、isRequestedSessionIdValid   
public boolean isRequestedSessionIdValid();   
这个方法检查与此请求关联的session当前是不是有效。如果当前请求中使用的session无效，它将不能通过getSession方法返回。   
17、isRequestedSessionIdFromCookie   
public boolean isRequestedSessionIdFromCookie();   
如果这个请求的session id是通过客户端的一个cookie提供的，该方法返回真，否则返回假。   
18、isRequestedSessionIdFromURL   
public boolean isRequestedSessionIdFromURL();   
如果这个请求的session id是通过客户端的URL的一部分提供的，该方法返回真，否则返回假。请注意此方法与isRequestedSessionIdFromUrl在URL的拼写上不同。   
以下方法将被取消\

19、isRequestedSessionIdFromUrl   
public boolean isRequestedSessionIdFromUrl();   
该方法被isRequestedSessionIdFromURL代替。

二、HttpServletResponse接口   
定义\

public interface HttpServletResponse extends ServletResponse   
描述一个返回到客户端的HTTP回应。这个接口允许Servlet程序员利用HTTP协议规定的头信息。   
成员变量   
public static final int SC_CONTINUE = 100;   
public static final int SC\_SWITCHING\_PROTOCOLS = 101;   
public static final int SC_OK = 200;   
public static final int SC_CREATED = 201;   
public static final int SC_ACCEPTED = 202;   
public static final int SC\_NON\_AUTHORITATIVE_INFORMATION = 203;   
public static final int SC\_NO\_CONTENT = 204;   
public static final int SC\_RESET\_CONTENT = 205;   
public static final int SC\_PARTIAL\_CONTENT = 206;   
public static final int SC\_MULTIPLE\_CHOICES = 300;   
public static final int SC\_MOVED\_PERMANENTLY = 301;   
public static final int SC\_MOVED\_TEMPORARILY = 302;   
public static final int SC\_SEE\_OTHER = 303;   
public static final int SC\_NOT\_MODIFIED = 304;   
public static final int SC\_USE\_PROXY = 305;   
public static final int SC\_BAD\_REQUEST = 400;   
public static final int SC_UNAUTHORIZED = 401;   
public static final int SC\_PAYMENT\_REQUIRED = 402;   
public static final int SC_FORBIDDEN = 403;   
public static final int SC\_NOT\_FOUND = 404;   
public static final int SC\_METHOD\_NOT_ALLOWED = 405;   
public static final int SC\_NOT\_ACCEPTABLE = 406;   
public static final int SC\_PROXY\_AUTHENTICATION_REQUIRED = 407;   
public static final int SC\_REQUEST\_TIMEOUT = 408;   
public static final int SC_CONFLICT = 409;   
public static final int SC_GONE = 410;   
public static final int SC\_LENGTH\_REQUIRED = 411;   
public static final int SC\_PRECONDITION\_FAILED = 412;   
public static final int SC\_REQUEST\_ENTITY\_TOO\_LARGE = 413;   
public static final int SC\_REQUEST\_URI\_TOO\_LONG = 414;   
public static final int SC\_UNSUPPORTED\_MEDIA_TYPE = 415;   
public static final int SC\_INTERNAL\_SERVER_ERROR = 500;   
public static final int SC\_NOT\_IMPLEMENTED = 501;   
public static final int SC\_BAD\_GATEWAY = 502;   
public static final int SC\_SERVICE\_UNAVAILABLE = 503;   
public static final int SC\_GATEWAY\_TIMEOUT = 504;   
public static final int SC\_HTTP\_VERSION\_NOT\_SUPPORTED = 505;   
以上HTTP产状态码是由HTTP/1.1定义的。   
方法   
1、addCookie   
public void addCookie(Cookie cookie);   
在响应中增加一个指定的cookie。可多次调用该方法以定义多个cookie。为了设置适当的头域，该方法应该在响应被提交之前调用。   
2、containsHeader   
public boolean containsHeader(String name);   
检查是否设置了指定的响应头。   
3、encodeRedirectURL   
public String encodeRedirectURL(String url);   
对sendRedirect方法使用的指定URL进行编码。如果不需要编码，就直接返回这个URL。之所以提供这个附加的编码方法，是因为在redirect的情况下，决定是否对URL进行编码的规则和一般情况有所不同。所给的URL必须是一个绝对URL。相对URL不能被接收，会抛出一个IllegalArgumentException。   
所有提供给sendRedirect方法的URL都应通过这个方法运行，这样才能确保会话跟踪能够在所有浏览器中正常运行。   
4、encodeURL   
public String encodeURL(String url);   
对包含session ID的URL进行编码。如果不需要编码，就直接返回这个URL。Servlet引擎必须提供URL编码方法，因为在有些情况下，我们将不得不重写URL，例如，在响应对应的请求中包含一个有效的session，但是这个session不能被非URL的（例如cookie）的手段来维持。   
所有提供给Servlet的URL都应通过这个方法运行，这样才能确保会话跟踪能够在所有浏览器中正常运行。   
5、sendError   
public void sendError(int statusCode) throws IOException;   
public void sendError(int statusCode, String message) throws   
IOException;   
用给定的状态码发给客户端一个错误响应。如果提供了一个message参数，这将作为响应体的一部分被发出，否则，服务器会返回错误代码所对应的标准信息。   
调用这个方法后，响应立即被提交。在调用这个方法后，Servlet不会再有更多的输出。   
6、sendRedirect   
public void sendRedirect(String location) throws IOException;   
使用给定的路径，给客户端发出一个临时转向的响应（SC\_MOVED\_TEMPORARILY）。给定的路径必须是绝对URL。相对URL将不能被接收，会抛出一个IllegalArgumentException。   
这个方法必须在响应被提交之前调用。调用这个方法后，响应立即被提交。在调用这个方法后，Servlet不会再有更多的输出。   
7、setDateHeader   
public void setDateHeader(String name, long date);   
用一个给定的名称和日期值设置响应头，这里的日期值应该是反映自1970-1-1日（GMT）以来的精确到毫秒的长整数。如果响应头已经被设置，新的值将覆盖当前的值。   
8、setHeader   
public void setHeader(String name, String value);   
用一个给定的名称和域设置响应头。如果响应头已经被设置，新的值将覆盖当前的值。   
9、setIntHeader   
public void setIntHeader(String name, int value);   
用一个给定的名称和整形值设置响应头。如果响应头已经被设置，新的值将覆盖当前的值。   
10、setStatus   
public void setStatus(int statusCode);   
这个方法设置了响应的状态码，如果状态码已经被设置，新的值将覆盖当前的值。   
以下的几个方法将被取消\   
11、encodeRedirectUrl   
public String encodeRedirectUrl(String url);   
该方法被encodeRedirectURL取代。   
12、encodeUrl   
public String encodeUrl(String url);   
该方法被encodeURL取代。   
13、setStatus   
public void setStatus(int statusCode, String message);   
这个方法设置了响应的状态码，如果状态码已经被设置，新的值将覆盖当前的值。如果提供了一个message，它也将会被作为响应体的一部分被发送。

三、HttpSession接口   
定义\   
public interface HttpSession   
这个接口被Servlet引擎用来实现在HTTP客户端和HTTP会话两者的关联。这种关联可能在多外连接和请求中持续一段给定的时间。session用来在无状态的HTTP协议下越过多个请求页面来维持状态和识别用户。   
一个session可以通过cookie或重写URL来维持。   
方法   
1、getCreationTime   
public long getCreationTime();   
返回建立session的时间，这个时间表示为自1970-1-1日（GMT）以来的毫秒数。   
2、getId   
public String getId();   
返回分配给这个session的标识符。一个HTTP session的标识符是一个由服务器来建立和维持的唯一的字符串。   
3、getLastAccessedTime   
public long getLastAccessedTime();   
返回客户端最后一次发出与这个session有关的请求的时间，如果这个session是新建立的，返回-1。这个时间表示为自1970-1-1日（GMT）以来的毫秒数。   
4、getMaxInactiveInterval   
public int getMaxInactiveInterval();   
返加一个秒数，这个秒数表示客户端在不发出请求时，session被Servlet引擎维持的最长时间。在这个时间之后，Servlet引擎可能被Servlet引擎终止。如果这个session不会被终止，这个方法返回-1。   
当session无效后再调用这个方法会抛出一个IllegalStateException。   
5、getValue   
public Object getValue(String name);   
返回一个以给定的名字绑定到session上的对象。如果不存在这样的绑定，返回空值。   
当session无效后再调用这个方法会抛出一个IllegalStateException。   
6、getValueNames   
public String[] getValueNames();   
以一个数组返回绑定到session上的所有数据的名称。   
当session无效后再调用这个方法会抛出一个IllegalStateException。   
7、invalidate   
public void invalidate();   
这个方法会终止这个session。所有绑定在这个session上的数据都会被清除。并通过HttpSessionBindingListener接口的valueUnbound方法发出通告。   
8、isNew   
public boolean isNew();   
返回一个布尔值以判断这个session是不是新的。如果一个session已经被服务器建立但是还没有收到相应的客户端的请求，这个session将被认为是新的。这意味着，这个客户端还没有加入会话或没有被会话公认。在他发出下一个请求时还不能返回适当的session认证信息。   
当session无效后再调用这个方法会抛出一个IllegalStateException。   
9、putValue   
public void putValue(String name, Object value);   
以给定的名字，绑定给定的对象到session中。已存在的同名的绑定会被重置。这时会调用HttpSessionBindingListener接口的valueBound方法。   
当session无效后再调用这个方法会抛出一个IllegalStateException。   
10、removeValue   
public void removeValue(String name);   
取消给定名字的对象在session上的绑定。如果未找到给定名字的绑定的对象，这个方法什么出不做。 这时会调用HttpSessionBindingListener接口的valueUnbound方法。   
当session无效后再调用这个方法会抛出一个IllegalStateException。   
11、setMaxInactiveInterval   
public int setMaxInactiveInterval(int interval);   
设置一个秒数，这个秒数表示客户端在不发出请求时，session被Servlet引擎维持的最长时间。   
以下这个方法将被取消\   
12、getSessionContext   
public HttpSessionContext getSessionContext();   
返回session在其中得以保持的环境变量。这个方法和其他所有HttpSessionContext的方法一样被取消了。

四、HttpSessionBindingListener接口   
定义\   
public interface HttpSessionBindingListener   
这个对象被加入到HTTP的session中，执行这个接口会通告有没有什么对象被绑定到这个HTTP session中或被从这个HTTP session中取消绑定。   
方法   
1、valueBound   
public void valueBound(HttpSessionBindingEvent event);   
当一个对象被绑定到session中，调用此方法。HttpSession.putValue方法被调用时，Servlet引擎应该调用此方法。   
2、valueUnbound   
public void valueUnbound(HttpSessionBindingEvent event);   
当一个对象被从session中取消绑定，调用此方法。HttpSession.removeValue方法被调用时，Servlet引擎应该调用此方法。

五、HttpSessionContext接口   
定义\   
此接口将被取消\   
public interface HttpSessionContext   
这个对象是与一组HTTP session关联的单一的实体。   
这个接口由于安全的原因被取消，它出现在目前的版本中仅仅是为了兼容性的原因。这个接口的方法将模拟以前的版本的定义返回相应的值。   
方法   
1、getSession   
public HttpSession getSession(String sessionId);   
当初用来返回与这个session id相关的session。现在返回空值。   
2、getIds   
public Enumeration getIds();   
当初用来返回这个环境下所有session id的列表。现在返回空的列表。

六、Cookie类\   
定义\   
public class Cookie implements Cloneable   
这个类描述了一个cookie，有关cookie的定义你可以参照Netscape Communications Corporation的说明，也可以参照RFC 2109。   
构造函数   
public Cookie(String name, String value);   
用一个name-value对定义一个cookie。这个name必须能被HTTP/1.1所接受。   
以字符$开头的name被RFC 2109保留。   
给定的name如果不能被HTTP/1.1所接受，该方法抛出一个IllegalArgumentException。   
方法   
1、getComment   
public String getComment();   
返回描述这个cookie目的的说明，如果未定义这个说明，返回空值。   
2、getDomain   
public String getDomain();   
返回这个cookie可以出现的区域，如果未定义区域，返回空值。   
3、getMaxAge   
public int getMaxAge();   
这个方法返回这个cookie指定的最长存活时期。如果未定义这个最长存活时期，该方法返回-1。   
4、getName   
public String getName();   
该方法返回cookie名。   
5、getPath   
public String getPath();   
返回这个cookie有效的所有URL路径的前缀，如果未定义，返回空值。   
6、getSecure   
public boolean getSecure();   
如果这个cookie只通过安全通道传输返回真，否则返回假。   
7、getValue   
public String getValue();   
该方法返回cookie的值。   
8、getVersion   
public int getVersion();   
返回cookie的版本。版本1由RFC 2109解释。版本0由Netscape Communications Corporation的说明解释。新构造的cookie默认使用版本0。   
9、setComment   
public void setComment(String purpose);   
如果一个用户将这个cookie提交给另一个用户，必须通过这个说明描述这个cookie的目的。版本0不支持这个属性。   
10、setDomain   
public void setDomain(String pattern);   
这个方法设置cookie的有效域的属性。这个属性指定了cookie可以出现的区域。一个有效域以一个点开头（.foo.com），这意味着在指定的域名解析系统的区域中（可能是www.foo.com但不是a.b.foo.com）的主机可以看到这个cookie。默认情况是，cookie只能返回保存它的主机。   
11、setMaxAge   
public void setMaxAge(int expiry);   
这个方法设定这个cookie的最长存活时期。在该存活时期之后，cookie会被终目。负数表示这个cookie不会生效，0将从客户端删除这个cookie。   
12、setPath   
public void setPath(String uri);   
这个方法设置cookie的路径属性。客户端只能向以这个给定的路径String开头的路径返回cookie。   
13、setSecure   
public void setSecure(boolean flag);   
指出这个cookie只能通过安全通道（例如HTTPS）发送。只有当产生这个cookie的服务器使用安全协议发送这个cookie值时才能这样设置。   
14、setValue   
public void setValue(String newValue);   
设置这个cookie的值，对于二进制数据采用BASE64编码。   
版本0不能使用空格、{}、()、=、，、&#8221;&#8221;、/、?、@、：以及；。   
15、setVersion   
public void setVersion(int v);   
设置cookie的版本号

七、HttpServlet类\   
定义\   
public class HttpServlet extends GenericServlet implements   
Serializable   
这是一个抽象类，用来简化HTTP Servlet写作的过程。它是GenericServlet类的扩充，提供了一个处理HTTP协议的框架。   
在这个类中的service方法支持例如GET、POST这样的标准的HTTP方法。这一支持过程是通过分配他们到适当的方法（例如doGet、doPost）来实现的。   
方法   
1、doDelete   
protected void doDelete(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
被这个类的service方法调用，用来处理一个HTTP DELETE操作。这个操作允许客户端请求从服务器上删除URL。这一操作可能有负面影响，对此用户就负起责任。   
这一方法的默认执行结果是返回一个HTTP BAD_REQUEST错误。当你要处理DELETE请求时，你必须重载这一方法。   
2、doGet   
protected void doGet(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
被这个类的service方法调用，用来处理一个HTTP GET操作。这个操作允许客户端简单地从一个HTTP服务器&#8221;获得&#8221;资源。对这个方法的重载将自动地支持HEAD方法。   
GET操作应该是安全而且没有负面影响的。这个操作也应该可以安全地重复。   
这一方法的默认执行结果是返回一个HTTP BAD_REQUEST错误。   
3、doHead   
protected void doHead(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
被这个类的service方法调用，用来处理一个HTTP HEAD操作。默认的情况是，这个操作会按照一个无条件的GET方法来执行，该操作不向客户端返回任何数据，而仅仅是返回包含内容长度的头信息。   
与GET操作一样，这个操作应该是安全而且没有负面影响的。这个操作也应该可以安全地重复。   
这个方法的默认执行结果是自动处理HTTP HEAD操作，这个方法不需要被一个子类执行。   
4、doOptions   
protected void doOptions(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
被这个类的service方法调用，用来处理一个HTTP OPTION操作。这个操作自动地决定支持哪一种HTTP方法。例如，一个Servlet写了一个HttpServlet的子类并重载了doGet方法，doOption会返回下面的头：   
Allow: GET,HEAD,TRACE,OPTIONS   
你一般不需要重载这个方法。   
5、doPost   
protected void doPost(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
被这个类的service方法调用，用来处理一个HTTP POST操作。这个操作包含请求体的数据，Servlet应该按照他行事。   
这个操作可能有负面影响。例如更新存储的数据或在线购物。   
这一方法的默认执行结果是返回一个HTTP BAD_REQUEST错误。当你要处理POST操作时，你必须在HttpServlet的子类中重载这一方法。   
6、doPut   
protected void doPut(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
被这个类的service方法调用，用来处理一个HTTP PUT操作。这个操作类似于通过FTP发送文件。   
这个操作可能有负面影响。例如更新存储的数据或在线购物。   
这一方法的默认执行结果是返回一个HTTP BAD_REQUEST错误。当你要处理PUT操作时，你必须在HttpServlet的子类中重载这一方法。   
7、doTrace   
protected void doTrace(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
被这个类的service方法调用，用来处理一个HTTP TRACE操作。这个操作的默认执行结果是产生一个响应，这个响应包含一个反映trace请求中发送的所有头域的信息。   
当你开发Servlet时，在多数情况下你需要重载这个方法。   
8、getLastModified   
protected long getLastModified(HttpServletRequest request);   
返回这个请求实体的最后修改时间。为了支持GET操作，你必须重载这一方法，以精确地反映最后修改的时间。这将有助于浏览器和代理服务器减少装载服务器和网络资源，从而更加有效地工作。返回的数值是自1970-1-1日（GMT）以来的毫秒数。   
默认的执行结果是返回一个负数，这标志着最后修改时间未知，它也不能被一个有条件的GET操作使用。   
9、service   
protected void service(HttpServletRequest request,   
HttpServletResponse response) throws ServletException,   
IOException;   
public void service(ServletRequest request, ServletResponse response)   
throws ServletException, IOException;   
这是一个Servlet的HTTP-specific方案，它分配请求到这个类的支持这个请求的其他方法。   
当你开发Servlet时，在多数情况下你不必重载这个方法。

八、HttpSessionBindingEvent类\   
定义\   
public class HttpSessionBindingEvent extends EventObject   
这个事件是在监听到HttpSession发生绑定和取消绑定的情况时连通HttpSessionBindingListener的。这可能是一个session被终止或被认定无效的结果。   
事件源是HttpSession.putValue或HttpSession.removeValue。   
构造函数   
public HttpSessionBindingEvent(HttpSession session, String name);   
通过引起这个事件的Session和发生绑定或取消绑定的对象名构造一个新的HttpSessionBindingEvent。   
方法   
1、getName   
public String getName();   
返回发生绑定和取消绑定的对象的名字。   
2、getSession   
public HttpSession getSession();   
返回发生绑定和取消绑定的session的名字。

九、HttpUtils类\   
定义\   
public class HttpUtils   
收集HTTP Servlet使用的静态的有效的方法。   
方法   
1、getRequestURL   
public static StringBuffer getRequestURL(HttpServletRequest   
request);   
在服务器上重建客户端用来建立请求的URL。这个方法反映了不同的协议（例如http和https）和端口，但不包含查询字符串。   
这个方法返回一个StringBuffer而不是一个String，这样URL可以被Servlet开发者有效地修改。   
2、parsePostData   
public static Hashtable parsePostData(int len,   
ServletInputstream in);   
解析一个包含MIME类型application/x-www-form-urlencoded的数据的流，并创建一个具有关键值-数据对的hash table。这里的关键值是字符串，数据是该字符串所对应的值的列表。一个关键值可以在POST的数据中出现一次或多次。这个关键值每出现一次，它的相应的值就被加入到hash table中的字符串所对应的值的列表中。   
从POST数据读出的数据将经过URL解码，+将被转换为空格以十六进制传送的数据（例如%xx）将被转换成字符。   
当POST数据无效时，该方法抛出一个IllegalArgumentException。   
3、parseQueryString   
public static Hashtable parseQueryString(String s);   
解析一个查询字符串，并创建一个具有关键值-数据对的hash table。这里的数据是该字符串所对应的值的列表。一个关键值可以出现一次或多次。这个关键值每出现一次，它的相应的值就被加入到hash table中的字符串所对应的值的列表中。   
从查询字符串读出的数据将经过URL解码，+将被转换为空格以十六进制传送的数据（例如%xx）将被转换成字符。   
当查询字符串无效时，该方法抛出一个IllegalArgumentException。   
术语表   
bytecode   
字节码：由Java编译器和Java解释程序生成的机器代码。   
cookie   
由Web服务器建立的数据，该数据存储在用户的计算机上，提供了一个Web站点跟踪用户的参数并存储在用户自己硬盘上的方法。   
HTTP   
超文本传输协议。一个请求响应协议用来连接WWW服务器向客户端浏览器传输HTML页面。   
输入流对象   
一个对象，由ServletInputStream类定义，被Servlet用来从客户端读取请求。   
映射   
由Servlet实例和Servlet返回数据的URL组成的一对，例如，HelloServlet和/hello/index.html。   
输出流对象   
一个对象，由ServletOutputStream class类定义，被Servlet用来向客户端返回数据。   
request dispatcher object   
由RequestDispatcher接口定义的一个对象，用来从客户端接收请求，并将其发送到Web服务器上可用的其他资源（例如Servlet、CGI、HTML文件或JSP文件）。   
sandboxed servlet   
在一个安全性约束下运行的Servlet。   
servlet   
一个小的，具有平台无关性的，没有图形用户界面的Java程序。它可以在许多方面扩充Web服务的功能。   
servlet configuration object   
ServletConfig接口定义的一个对象，用来配置一个Servlet。   
servlet context object   
ServletContext接口定义的一个对象。给予Servlet有关Servlet引擎的信息。   
servlet引擎   
由Web服务器提供商制作的一个环境，可以允许Servlet在具体的Web服务器上运行。   
servlet请求对象   
由ServletRequest接口定义的一个对象，允许Servlet获得用关客户端请求的数据。   
servlet response object   
由ServletResponse接口定义的一个对象，允许Servlet作出响应。   
servlet runner   
Java Servlet Developer&#8217;s Kit (JSDK)中的sun.servlet.http.HttpServer过程，它使得Servlet得以运行。   
会话跟踪   
在一个Web应用程序中，识别一个从同一个客户端发出的连续的唯一的请求的能力。   
SSL   
加密套接字协议层。一个安全协议，用来在Iternet上的客户端浏览器和服务器交换密钥和加密数据。   
URI   
统一资源标识。定义一个Internet地址，它是一个URL的超集。   
URL   
统一资源路径。这个地址定义了到达一个WWW上的文件的路线，通常由协议前缀、域名、目录名和文件名组成

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [[转载]servletAPI2.1中文版.txt](http://www.beansoft.biz/2007/11/02/%e8%bd%ac%e8%bd%bdservletapi2-1%e4%b8%ad%e6%96%87%e7%89%88-txt/)