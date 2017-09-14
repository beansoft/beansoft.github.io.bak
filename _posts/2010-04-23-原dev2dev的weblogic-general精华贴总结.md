---
id: 115
title: 原dev2dev的WebLogic General精华贴总结
date: 2010-04-23T22:09:49+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=115
permalink: '/2010/04/23/%e5%8e%9fdev2dev%e7%9a%84weblogic-general%e7%b2%be%e5%8d%8e%e8%b4%b4%e6%80%bb%e7%bb%93/'
views:
  - "48580"
original_post_id:
  - "115"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
WebLogic General精华贴总结 

总结人:周小超(dev2dev ID:supine) 

##### 

##### 1. 怎样获得jsp页面的物理路径

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=17881&tstart=75> 

在一个web服务器上，虚拟路径将物理上分离的各文件组合在一起，放在同一个站点路径上，在应用服务器上，每个应用定位于其自己的虚拟路径上，实际上相互之间有着完美地分离。   
getRealPath()方法   
JSP servlet API提供了getRealPath(path)方法，返回给定虚拟路径的真实路径，如果转换错误，则返回null。   
getRealPath语法定义：   
public java.lang.String getRealPath(java.lang.String path)   
返回一个字符串，包含一个给定虚拟路径的真实路径。例如，虚拟路径 "/index.html"   
不管在服务器文件系统上具有怎样的真实路径，使用"/index.html"总可以找到它。返回的真实路径使用了相近于servlet容器(srvlet container)所在计算机或操作系统的格式，包含了适当的路径分隔符。如果servlet容器无法转换则这个方法将返回null。   
参数：   
path -一个描述了虚拟路径的字符串   
返回值：   
描述真实路径的字符串或者null   
遗憾的是，getRealPath常常返回不同的东西，这取决于服务器或jsp文件调用此方法的路径位置。   
一个example站点   
假设我们的站点组织如下：   
根路径包含了我们的站点的根： [**http://address/**](http://address/)   
a_virtual目录包含了我们站点提供的虚拟路径的文件，例如：   
[**http://addess/virtual_dir/**](http://addess/virtual_dir/)   
我们查找file1.txt和file2.txt的真实路径，它们一个在站点根路径下，一个在虚拟路径下。   
getRealPath("/file1.txt") 应该返回“C:sitesite_rootfile1.txt"，   
getRealPath("/virtual\_dir/file2.txt")应该返回"C:sitea\_virtualfile2.txt"   
getRealPath("/file3.txt")应该返回null，因为这个文件不存在。   
但getRealPath()并不总是返回同样的结果，这还取决与你使用的js引擎。 

##### <a name="88542"></a>2. 在weblogic8.0中如何让weblogic起动成功以后，执行一个类的方法，是自动执行的

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=15889&tstart=125> 

可以配置startup后执行的类.   
参考:[**http://e-docs.bea.com/wls/docs81/ConsoleHelp/startup_shutdown.html**](http://e-docs.bea.com/wls/docs81/ConsoleHelp/startup_shutdown.html) 

或者是自动启动servlet 

##### <a name="86559"></a>3. 特殊servlet映射方法的问题

http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=15554&tstart=125 

Q:看weblogic8.1文档中有关于内置的ClasspathServlet映射的问题，文档中说这个servlet是默认打开的，并且将所有有关classes/模式的访问映射到系统类路径和WEB-INF/classes下，我的web应用名称是myweb.war里面有一个类org.aaa编译好后放在WEB-INF/classes下面，部署应用，用以下url访问该类   
[**http://MyIP:Port/myweb/classes/org/aaa.class**](http://myipPort) 总是提示404file not found   
请问这是怎么回事？我看了我的config.xml文件server标签中的ClasspathServletDisabled="false"属性已经设置了，请问各位大虾，这个系统类路径的映射servlet应该怎样配置才对，访问类时的浏览器中的url应该如何构建？ 

A:&#160;&#160; <servlet>   
&#160;&#160;&#160; <servlet-name>ClasspathServlet</servlet-name>   
&#160;&#160;&#160; <servlet-class>weblogic.servlet.ClasspathServlet</servlet-class>   
&#160; </servlet>   
&#160; <servlet-mapping>   
&#160;&#160;&#160; <servlet-name>ClasspathServlet</servlet-name>   
&#160;&#160;&#160; <url-pattern>/classes/*</url-pattern>   
&#160; </servlet-mapping> 

##### <a name="72297"></a>4. weblogic的管理员密码忘记了？

文章内容：   
1. 备份当前domain的config.xml、fileRealm.properties和SerializedSystemIni.dat   
2. 新建一个叫fileRealm.properties.src的文件，其内容为：user.system=weblogic ，其中weblogic就是您想要的明文的密码   
3. 打开dos窗口/控制台，cd到当前domain的目录，调用setEnv脚本设置相关的环境变量，然后执行：   
java weblogic.security.acl.internal.FileRealm fileRealm.properties SerializedSystemIni.dat   
4. 将原来的fileRealm.properties中acl、group相关的条目拷回到新生成的fileRealm.properties里边   
5. 将config.xml里边加密过的密码（以{3DES}开头）改成明文的。   
6. 启动weblogic 

##### 5. 一些weblogic的视频讲座资料！

[**http://www.bea.com.cn/services/custsupp/csnewsevents/csnews/support\_news\_news_05.jsp**](http://www.bea.com.cn/services/custsupp/csnewsevents/csnews/support_news_news_05.jsp) 

##### 6. weblogic7.0上开发webservice的问题

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=10574&tstart=200> 

在用weblogic7.0开发webservice应用时，遇到了几个问题，具体情况是：   
&#160; Q:1)我在webservice的方法中返回值为ArrayList，且ArrayList中若包含一些自定义类型，如javabean时，部署完成后，从确省的访问页执行此方法，出现下列错误信息：   
&#160; javax.xml.soap.SOAPException: failed to deserialize xml:weblogic.xml.schema.binding.DeserializationException: mapping lookup failure. type=[&#8216;http://www.w3.org/2001/XMLSchema&#8217;]:anyType schema context=TypedSchemaContext{javaType=javax.xml.soap.SOAPElement}   
注：但是若单独返回这个javabean没有问题   
&#160; 2）另外，如果返回的数据对象中包含中文数据的话，也会出现错误，具体信息如下：javax.xml.rpc.soap.SOAPFaultException: Error reading the response from: [**http://192.0.2.211:7001/basic_javaclass/HelloWorld.**](http://192.0.2.211:7001/basic_javaclass/HelloWorld.) Please ensure that this is a valid SOAP response 

A: 1.你的ArrayList中需要用   
/**   
* @common:operation   
* @jws:return-xml include-java-types="CustomBean"   
*/   
引用一下.这样weblogic在遇到你的bean时,知道如何解析成xml. 

##### <a name="45288"></a>7. 怎样才能把weblogic成功的配置成服务？

注意installService.cmd文件中的这句话:echo Usage: installService.cmd \[WLS\_USER\] \[WLS\_PW\]   
在命令行下执行完后,会提示你beasvc web_webso installed.   
说明已经安装成功.   
然后在services.msc就可以看到你的beasvc DOMAIN\_NAME&SERVER\_NAME 的名称了,点击运行,会自动运行你定义的domain.(没有显示). 稍等一会,等你的beasvc.exe进程稳定后,weblogic server启动完毕,你就可以通过控制台去管理了.   
如果只是在资源管理器中双击installService.cmd,那么屏幕将一闪而过,其实,是提示你installService的用法是installService.cmd \[WLS\_USER\] \[WLS\_PW\]的. 🙂   
所以,要想安装service成功,两中方法:1.config向导 2.cmd下运行installService.cmd   
顺便提及一下卸载,可以直接在资源管理器中双击uninstallService.cmd,该命令没有参数 🙂 

<a></a>

##### 8. 读书笔记 关于ClassLoader

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=9471&tstart=325> 

了解ClassLoader   
1， 什么是 ClassLoader?   
&#160;&#160;&#160; Java 程序并不是一个可执行文件，是需要的时候，才把装载到 JVM中。ClassLoader 做的工作就是 JVM 中将类装入内存。 而且，Java ClassLoader 就是用 Java 语言编写的。这意味着您可以创建自己的 ClassLoader   
&#160;&#160;&#160; ClassLoader 的基本目标是对类的请求提供服务。当 JVM 需要使用类时，它根据名称向 ClassLoader 请求这个类，然后 ClassLoader 试图返回一个表示这个类的 Class 对象。 通过覆盖对应于这个过程不同阶段的方法，可以创建定制的 ClassLoader。   
2， 一些重要的方法   
A)&#160; 方法 loadClass   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; ClassLoader.loadClass() 是 ClassLoader 的入口点。该方法的定义如下：   
&#160;&#160;&#160;&#160;&#160;&#160;&#160; Class loadClass( String name, boolean resolve );   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; name&#160; JVM 需要的类的名称，如 Foo 或 java.lang.Object。   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; resolve 参数告诉方法是否需要解析类。在准备执行类之前，应考虑类解析。并不总是需要解析。如果 JVM 只需要知道该类是否存在或找出该类的超类，那么就不需要解析。   
&#160;&#160;&#160; B)&#160; 方法 defineClass   
&#160;&#160;&#160;&#160;&#160;&#160; defineClass 方法是 ClassLoader 的主要诀窍。该方法接受由原始字节组成的数组并把它转换成 Class 对象。原始数组包含如从文件系统或网络装入的数据。defineClass 管理 JVM 的许多复杂、神秘和倚赖于实现的方面 &#8212; 它把字节码分析成运行时数据结构、校验有效性等等。不必担心，您无需亲自编写它。事实上，即使您想要这么做也不能覆盖它，因为它已被标记成final的。   
&#160;&#160;&#160; C)&#160; 方法 findSystemClass   
&#160;&#160;&#160;&#160;&#160;&#160; findSystemClass 方法从本地文件系统装入文件。它在本地文件系统中寻找类文件，如果存在，就使用 defineClass 将原始字节转换成 Class 对象，以将该文件转换成类。当运行 Java 应用程序时，这是 JVM 正常装入类的缺省机制。（Java 2 中 ClassLoader 的变动提供了关于 Java 版本 1.2 这个过程变动的详细信息。） 对于定制的 ClassLoader，只有在尝试其它方法装入类之后，再使用 findSystemClass。原因很简单：ClassLoader 是负责执行装入类的特殊步骤，不是负责所有类。例如，即使 ClassLoader 从远程的 Web 站点装入了某些类，仍然需要在本地机器上装入大量的基本 Java 库。而这些类不是我们所关心的，所以要 JVM 以缺省方式装入它们：从本地文件系统。这就是 findSystemClass 的用途。   
&#160;&#160;&#160;&#160; D) 方法 resolveClass   
正如前面所提到的，可以不完全地（不带解析）装入类，也可以完全地（带解析）装入类。当编写我们自己的 loadClass 时，可以调用 resolveClass，这取决于 loadClass 的 resolve 参数的值。   
&#160;&#160; E) 方法 findLoadedClass   
&#160;&#160;&#160;&#160;&#160; findLoadedClass 充当一个缓存：当请求 loadClass 装入类时，它调用该方法来查看 ClassLoader 是否已装入这个类，这样可以避免重新装入已存在类所造成的麻烦。应首先调用该方法。   
3， 怎么组装这些方法   
&#160; 1） 调用 findLoadedClass 来查看是否存在已装入的类。   
&#160; 2） 如果没有，那么采用那种特殊的神奇方式来获取原始字节。   
&#160; 3） 如果已有原始字节，调用 defineClass 将它们转换成 Class 对象。   
&#160; 4） 如果没有原始字节，然后调用 findSystemClass 查看是否从本地文件系统获取类。   
&#160; 5） 如果 resolve 参数是 true，那么调用 resolveClass 解析 Class 对象。   
&#160; 6） 如果还没有类，返回 ClassNotFoundException。   
4，Java 2 中 ClassLoader 的变动   
1）loadClass 的缺省实现   
定制编写的 loadClass 方法一般尝试几种方式来装入所请求的类，如果您编写许多类，会发现一次次地在相同的、很复杂的方法上编写变量。 在 Java 1.2 中 loadClass 的实现嵌入了大多数查找类的一般方法，并使您通过覆盖 findClass 方法来定制它，在适当的时候 findClass 会调用 loadClass。 这种方式的好处是您可能不一定要覆盖 loadClass；只要覆盖 findClass 就行了，这减少了工作量。   
2）新方法：findClass   
&#160;&#160;&#160;&#160; loadClass 的缺省实现调用这个新方法。findClass 的用途包含您的 ClassLoader 的所有特殊代码，而无需要复制其它代码（例如，当专门的方法失败时，调用系统 ClassLoader）。   
3） 新方法：getSystemClassLoader   
如果覆盖 findClass 或 loadClass，getSystemClassLoader 使您能以实际 ClassLoader 对象来访问系统 ClassLoader（而不是固定的从 findSystemClass 调用它）。   
4） 新方法：getParent&#160;   
为了将类请求委托给父代 ClassLoader，这个新方法允许 ClassLoader 获取它的父代 ClassLoader。当使用特殊方法，定制的 ClassLoader 不能找到类时，可以使用这种方法。   
父代 ClassLoader 被定义成创建该 ClassLoader 所包含代码的对象的 ClassLoader。 

##### 9. weblogic中如何建立自己的虚拟目录

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=9715&tstart=325> 

可以针对web app设置虚拟目录，在weblogic。xml中加入下面的配置。   
例如：   
<virtual-directory-mapping>   
&#160;&#160;&#160;&#160; <local-path>c:/webcrmdata/import</local-path>   
&#160;&#160;&#160;&#160; <url-pattern>/import/</url-pattern>   
&#160; </virtual-directory-mapping> 

##### 10. 如何修改weblogic7的console的登陆密码

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=7482&tstart=350> 

以 system及security登录进去后，   
依次展开yourdomain &#8211;> security &#8211;> realms &#8211;> myrealm,   
点击users &#8211;> 点击右边的system即可看到修改口令选项。 

##### 11. weblogic server 中的安全区有两种类型：RDBMS安全区和文件安全区，哪个高手知道如何配置RDBMS安全区

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=5932&tstart=425> 

[**http://dev2dev.bea.com/codelibrary/code/sec_rdbms.jsp**](http://dev2dev.bea.com/codelibrary/code/sec_rdbms.jsp)   
What It Does   
This is working example that builds a new security authenticator, populates a database with sample data, modifies the domain to add the new authenticator, change the ControlFlags for the DefaultAuthenticator and new Authenticator, and then copies a sample Web application to use to show how FORM based security works with the new Authenticator.   
How It Works   
Once you install and run the code, the following occurs:   
A new authenticator named DbSampleAuthenticator is created   
The ControlFlag for the DefaultAuthenticator changes from Required to Sufficient   
The ControlFlag for
   
the DbSampleAuthenticator changes from Required to Sufficient   
The realm property to DbSampleAuthenticator is added 

##### 12. WebLogic Server中的ClassPath设置问题

http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=6367&tstart=425 

Q: 请教:本人想在wls中配置sql server的连接池,但报该driver在classpath中找不到,我的jdbc driver for ms sql server是配置在本机的classpath中的,但我想wls肯定是使用了自己的classpath,所以我想请问一下怎么在wls的classpath中加上自己的类路径?   
先谢了. 

A:打开你的startweblogic.bat文件，找到classpath项，在后面加上你的jar就行了。 

##### 13. class file has wrong version是怎么回事？

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=5804&tstart=450> 

Q:我用的WEBLOGIC7.0SP1，部署webapp后运行，出现下面的错误：   
Compilation of &#8216;D:WorkSpaceccrmj2srcjsp\_servlet\_purveiw\_jsp\__workgroupmain.java&#8217; failed:   
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;   
D:WorkSpaceccrmj2srcjsp\_servlet\_purveiw\_jsp\__workgroupmain.java:19: cannot access com.torch.crm.purview.model.WorkGroupVO   
probably occurred due to an error in /Purveiw_jsp/workGroupMain.jsp line 14:   
<%@ page import="com.torch.crm.purview.model.WorkGroupVO" %>   
&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211;   
Full compiler error(s):   
D:WorkSpaceccrmj2srcjsp\_servlet\_purveiw\_jsp\__workgroupmain.java:19: cannot access com.torch.crm.purview.model.WorkGroupVO   
bad class file: C:beauser\_projectsmydomain.myserver.wlnotdelete\_appsdir\_webapp\_war\_webapp\_1896635jarfilescls64915.jar(com/torch/crm/purview/model/WorkGroupVO.class)   
class file has wrong version 48.0, should be 47.0   
Please remove or make sure it appears in the correct subdirectory of the classpath.   
import com.torch.crm.purview.model.WorkGroupVO; //[ /Purveiw_jsp/workGroupMain.jsp; Line: 14]   
&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; ^   
1 error   
此外，我想问一下，在StartWLS.cmd文件中的set JAVA_HOME有什么用？它默认的是1.3，但是我机子里用的是1.4，我把这个变量改成1.4后，weblogic就不能用了（出现错误）。为什么1。4就不能用了呢？ 

A: 出現這個問題，很可能就是修改了weblogic的JDK版本。1.4编译的程序在1.3下运行就会出现这种错误. 

##### <a name="21147"></a>14. Linux下找到Weblogic监听的Port

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=4791&tstart=475> 

不管多少个weblogic运行，他们总要监听端口的。用下边这个命令，就可以搜出所有的WLS监听的断口。：）。希望有用。   
当然，通过这个也可以确定wls正常启动了。^_^。   
建议把这个作成一个shell，放入path中，就没有那么麻烦了：）。   
最好用root权限执行，一行命令下来：   
for x in \`ps -af|grep &#8216;bea&#8217;|gawk &#8216;{print $2}&#8217;\`; do netstat -apn |grep $x|grep tcp;done   
希望对大家有用。大家一起来支持Linux！   
shell文件：   
#!/bin/bash   
for x in \`ps -af|grep &#8216;bea&#8217;|gawk &#8216;{print $2}&#8217;\`; do netstat -apn |grep $x|grep tcp;done 

##### <a name="20710"></a>15. 关于用weblogic发布程序后，页面中word及excel等文档下载连接的问题

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=4671&tstart=475> 

Q:用weblogic 6.1发布一个web应用程序，提供word上传及下载，但是当   
点击下载的链接时，不像我们正常在网站点击一个文件链接，会弹出一个   
提示框，询问“保存到本地磁盘还是在当前位置打开”；而是会自动在浏览器里   
打开这个文档，而且Ie自动打开这个文档时，默认的按html去解释，导致整个文档在IE   
中都是   
乱码。而我用tomcat发布，就会弹出提示框。请问是不是weblogic要进行什么配置以后   
才会   
弹出提示框。如果是，请问如何配置？   
另外，我在web.xml中加入如下代码（以word文档为例）：   
<mime-mapping>   
&#160;&#160;&#160; <extension>doc</extension>   
&#160;&#160;&#160; <mime-type>application/msword</mime-type>   
&#160; </mime-mapping>   
或者如下代码：   
<mime-mapping>   
&#160;&#160;&#160; <extension>doc</extension>   
&#160;&#160;&#160; <mime-type>application/octet-stream</mime-type>   
&#160; </mime-mapping>   
没有任何效果。 

A:   
在WEB.XML文件里加入   
<mime-mapping>   
<extension>doc</extension>   
<mime-type>application/self-define</mime-type>   
</mime-mapping>   
就可以出现提示下载框了.   
“application/self-define“不需要修改,因为注册表里没有对应的application/self-define内容. 

##### 16. 如何在Weblogic中用编徎的方法增加一个用户

<http://dev2dev.bea.com.cn/bbs/thread.jspa?forumID=126&threadID=82&tstart=525> 

下面是个添加用户的例子   
具体的你可以看看我也有个帖子就在本页   
import java.util.*;   
import javax.management.*;   
import weblogic.management.*;   
import weblogic.security.providers.authentication.*;   
import weblogic.management.security.authentication.AuthenticationProviderMBean;   
import weblogic.management.security.authentication.*;   
public class test2   
{   
public static void main(String[] args )   
{   
MBeanHome adminHome;   
String url = "t3://127.0.0.1:7001" ;   
adminHome = (MBeanHome)Helper.getAdminMBeanHome("username","password",url);   
AuthenticationProviderMBean[] providers = adminHome.getActiveDomain().getSecurityConfiguration().findDefaultRealm().getAuthenticationProviders();   
for (int i=0; providers != null && i <providers.length; i++)   
{   
if (providers _instanceof UserEditorMBean)   
{   
UserEditorMBean editor = (UserEditorMBean)providers;   
try   
{   
editor.createUser("username","password","description");   
}   
catch (Exception e)   
{   
e.printStackTrace();   
}   
}   
}   
}   
}   
}_ 

__

jsp原码：   
<%@page import="java.util.\*,javax.management.\*,weblogic.management.\*,weblogic.security.providers.authentication.\*,weblogic.management.security.authentication.AuthenticationProviderMBean,weblogic.management.security.authentication.*"%>   
<%   
MBeanHome adminHome;   
String url = "t3://172.30.94.60:7001" ;   
adminHome = (MBeanHome)Helper.getAdminMBeanHome("username","password",url);   
AuthenticationProviderMBean[] providers = adminHome.getActiveDomain().getSecurityConfiguration().findDefaultRealm().getAuthenticationProviders();   
for (int i=0; providers != null && i <providers.lengt
  
h; i++)   
{   
if (providers _instanceof UserPasswordEditorMBean)   
{   
UserPasswordEditorMBean editor = (UserPasswordEditorMBean)providers;   
try   
{   
editor.changeUserPassword("username","password","password2");   
System.out.println("modify password success.");   
}   
catch (Exception e)   
{   
e.printStackTrace();   
System.out.println("modify password ERROR:"+e.getMessage());   
}   
}   
}   
%>_

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [原dev2dev的WebLogic General精华贴总结](http://www.beansoft.biz/2010/04/23/%e5%8e%9fdev2dev%e7%9a%84weblogic-general%e7%b2%be%e5%8d%8e%e8%b4%b4%e6%80%bb%e7%bb%93/)