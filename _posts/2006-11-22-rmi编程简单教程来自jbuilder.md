---
id: 145
title: RMI编程简单教程(来自JBuilder)
date: 2006-11-22T14:02:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=145
permalink: '/2006/11/22/rmi%e7%bc%96%e7%a8%8b%e7%ae%80%e5%8d%95%e6%95%99%e7%a8%8b%e6%9d%a5%e8%87%aajbuilder/'
views:
  - "4432"
original_post_id:
  - "145"
image: /wp-content/uploads/2012/09/linkblog.jpg
categories:
  - Java SE
---
<div class="pagelayout">
  <div class="centercolumn">
    <div class="singlepost">
      <h1>
        <font color="#0000ff">RMI编程简单教程</font><font size="+0">&#8211;BeanSoft 翻译[11 1,2001,Thu]</font>
      </h1>
      
      <h1>
        Project Notes <br /><font color="#0000ff"><strong>项目备注</strong></font>
      </h1>
      
      <hr />
      
      <font size="+0"><strong> </p> 
      
      <p>
        Project:
      </p>
      
      <p>
        </strong>RMI: A Simple RMI Application <br /></font><font color="#0000ff"><strong>项目:</strong>RMI:一个简单的RMI应用程序 <br /></font><strong>Author:</strong> JBuilder Team <br /><font color="#0000ff"><strong>作者:</strong>JBuilder工作组 <br /></font><strong>Company:</strong> borland.com <br /><font color="#0000ff"><strong>公司:</strong>borland.com <br /></font><strong>Description:</strong> <br />This sample will guide you through the steps to create a simple RMI application <br /><font color="#0000ff"><strong>描述:</strong>这个示例将会教你建立一个简单的RMI应用程序的步骤.</font>
      </p>
      
      <p>
        Steps to creation of an RMI application: <br /><font color="#0000ff">一个RMI应用程序的创建步骤</font>
      </p>
      
      <p>
        <em>The short version</em> <br /><font color="#0000ff">精简版</font>
      </p>
      
      <pre>1) Create an interface. (in this case, the interface is SimpleRMIInterface.java).
<font color="#0000ff">1) 创建一个接口.(在这个例子中,接口是SimpleRMIInterface.java).
</font>2) Create a class that implements the interface. (in this case, SimpleRMIImpl.java).
<font color="#0000ff">2) 创建一个实现这个接口的类.(在这里,是SimpleRMIImpl.java).
</font>3) Create a server that creates an instance of this class.
<font color="#0000ff">3) 创建一个建立了一个这个类的示例的服务器.
</font>4) Create a client that connects to the server object using Naming.lookup().
<font color="#0000ff">4) 创建一个使用Naming.lookup()连接到服务器对象的客户.
</font>5) Set the compile options on the RMI implementation file.
<font color="#0000ff">5) 设置RMI实现文件的编译选项.
</font>6) Compile these classes.
<font color="#0000ff">6) 编译这些类.
</font>7) Start the RMI registry.
<font color="#0000ff">7) 打开RMI注册.
</font>8) Start the server class.
<font color="#0000ff">8) 运行服务器类.
</font>9) Run the client program.
<font color="#0000ff">9) 运行客户程序.
</font></pre>
      
      <p>
        <em></p> 
        
        <p>
          The long version<br /> <br /><font color="#0000ff">详细版</font>
        </p>
        
        <p>
          </em>
        </p>
        
        <ol>
          <li>
            Create an interface.<br /> <br /><font color="#0000ff">建立一个接口.<br /> <br /></font>The interface created for this example is <a href="http://blog.blogchina.com/mcp/SimpleRMIInterface.java">SimpleRMIInterface.java</a>. It contains only one method; the method takes no arguments and returns an object of type java.util.Date. Note two things about this interface: 1) it extends the java.rmi.Remote interface (all interfaces used in RMI must do this). 2) the method throws a java.rmi.RemoteException (every method in a remote object&#8217;s interface must specify this exception in its "throws" clause; this exception is a superclass of all RMI exceptions that can be thrown. See the JDK 1.1 final docs (in the java.rmi section) for a complete list of exceptions that can be thrown.</p> <p>
              <font color="#0000ff">这个例子创建的接口是<a href="http://blog.blogchina.com/mcp/SimpleRMIInterface.java">SimpleRMIInterface.java</a>.它仅仅含有一个方法;这个方法不需要参数并且返回一个java.util.Date类型的对象.注意这个接口中的两件事: 1)它继承自java.rmi.Remote接口(所有使用RMI的接口必须这样做). 2)这个方法抛出一个java.rim.RemoteException(一个远程对象接口中的每个方法都必须在它的"throws"子句中列入这个异常;这个异常是所有能够抛出的RMI异常的超类.参看JDK最终文档(在java.rmi部分)获得可以抛出的异常的完整列表.</p> 
              
              <p>
                </font></li> 
                
                <li>
                  Create a class that implements the interface.<br /> <br /><font color="#0000ff">建立一个实现上面接口的类.<br /> <br /></font>In this example, the implementation is found in <a href="http://blog.blogchina.com/mcp/SimpleRMIImpl.java">SimpleRMIImpl.java</a>. This class must extend java.rmi.UnicastRemoteObject and must implement the interface you created in step 1. In my example, the only method that needs to be implemented is getDate(), which returns the current date and time on the system. Note 2 things about the constructor: 1) the call to super(). 2) the call to Naming.rebind(name, this). This call informs the RMI registry that this object is available with the name given in "String name". Other than that, this object simply implements all the methods declared in the interface.</p> <p>
                    <font color="#0000ff">在本例中,可以在<a href="http://blog.blogchina.com/mcp/SimpleRMIImpl.java">SimpleRMIImpl.java</a>中找到这个实现.这个类必须继承自java.rmi.UnicastRemoteObject,并且必须实现你在步骤1中创建的接口.在我得例子中,唯一需要实现的方法是getDate(),它返回系统上当前的日期和时间.注意接口中的构造方法: 1)对super()的调用. 2)对Naming.rebind(name, this)的调用.这个调用通知RMI注册器这个以"字符串名字"为名字的对象可以使用了.除此之外,这个对象只不过实现了接口中定义的所有方法.</p> 
                    
                    <p>
                      </font></li> 
                      
                      <li>
                        Create a server that creates an instance of the "impl" class.<br /> <br /><font color="#0000ff">创建一个创建了一个"impl"类实例的服务器.<br /> <br /></font>In this example, the server class is <a href="http://blog.blogchina.com/mcp/SimpleRMIServer.java">SimpleRMIServer.java</a>. In this case, the server is pretty simple. It does 2 things: 1) Installs a new RMISecurityManager (Note that RMI uses a different security manager from the security manager used for applets). 2) Creates an instance of the SimpleRMIImpl class, and gives it the name "SimpleRMIImpl instance". The SimpleRMIImpl object takes care of registering the object with the RMI registry. After this code is run, the object will be available to remote clients as "rmi://<your server here>/SimpleRMIImpl instance". (and in fact, this is how the client connects to it in step 4).</p> <p>
                          <font color="#0000ff">在这个例子中,服务器类是<a href="http://blog.blogchina.com/mcp/SimpleRMIServer.java">SimpleRMIServer.java</a>.在这种情况下,服务器相当简单.它做了2件事: 1)安装一个新的RMISecurityManage(注意RMI使用了一个和applet所使用的安全管理器不同的管理器). 2)创建SimpleRMIImpl类的实例,给它一个名字"SimpleRMIImpl instance".SimpleRMIImpl对象使用RMI注册器实现注册.代码运行之后,这个对象以"rmi://<your server here>/SimpleRMIImpl instance"的形式对远程客户可用.(实际上,这就是步骤4中客户如何连接到此对象)</p> 
                          
                          <p>
                            </font></li> 
                            
                            <li>
                              Create a client that connects to the server object using Naming.lookup().<br /> <br /><font color="#0000ff">创建一个使用Naming.lookup()连接到服务器对象的客户.<br /> <br /></font>In this example, the client class is <a href="http://blog.blogchina.com/mcp/SimpleRMIClient.java">SimpleRMIClient.java</a>. The client first installs a new RMI Security Manager (see previous step), then uses the static method Naming.lookup() to get a reference to the remote object. Note that the client is using the <em>interface</em> to hold the reference and make method calls. You should make sure you&#8217;ve created your interface before you try to build the client, or you&#8217;ll get "class not found" errors when you try to compile your client.</p> <p>
                                <font color="#0000ff">在这个例子中,客户类是<a href="http://blog.blogchina.com/mcp/SimpleRMIClient.java">SimpleRMIClient.java</a>.客户首先安装一个新的RMI安全管理器(参见上一步),然后使用静态方法Naming.lookup()来得到远程对象的一个引用.注意,客户使用<em>接口</em>来获得引用和进行方法调用.确保在尝试建造客户类之前你已经创建了接口,否则你将在试图编译你的客户类时得到"无法找到类"的错误.</p> 
                                
                                <p>
                                  </font></li> 
                                  
                                  <li>
                                    Set the compile options on the RMI implementation file.<br /> <br /><font color="#0000ff">设置RMI实现文件的编译选项.<br /> <br /></font>In the IDE, Right-click the SimpleRMIImpl.java file in the navigator pane and choose "Java source properties." In the properties dialog, check "Generate RMI stub / skeleton." and click OK.</p> <p>
                                      <font color="#0000ff">在集成开发环境中,在浏览面板中右击文件SimpleRMIImpl.java,选择"Java source properties"(Java源代码属性).在属性对话框中,选中"Generate RMI stub / skeleton."(创建RMI存根 / 框架)并且点击OK按钮.</font> </li> 
                                      
                                      <li>
                                        Compile these classes.<br /> <br /><font color="#0000ff">编译这些类.<br /> <br /></font>
                                      </li>
                                      <li>
                                        <p align="left">
                                          <strong>JDK 1.2 specific:</strong> make sure that the JRE Security policy is <a href="http://blog.blogchina.com/mcp/#rmi_and_jdk12">setup for RMI</a>.
                                        </p>
                                        
                                        <p>
                                          <font color="#0000ff"><strong>JDK 1.2细节:</strong>确保JRE的安全策略已经<a href="http://blog.blogchina.com/mcp/#rmi_and_jdk12">为RMI设置</a>好.</font>
                                        </p>
                                      </li>
                                      
                                      <li>
                                        Start the RMI registry.<br /> <br /><font color="#0000ff">运行RMI注册器.<br /> <br /></font>OK. You&#8217;re done with development at this point; you&#8217;ve built all the code you need to run this example. Now you&#8217;re setting up the environment so that you can run it. rmiregistry is a program that comes with the JDK 1.1 final; you can find it in the "bin" directory of your JDK installation. From within JBuilder, choose Tools | RMIRegistry. The next time you look at the tools menu, you will notice there is a check next to this menu option. This is your clue that the registry is running. Selecting it again will close the RMIRegistry.</p> <p>
                                          <font color="#0000ff">好了.在这一点你已经开发完毕;你已经建立了运行这个例子所需的所有代码.现在你正在安装环境从而你能运行它.rmiregistry是一个来自于JDK 1.1最终版的程序;你可以在你的JDK安装的"bin"目录下找到它.在JBuilder内,选中 Tools | RMIRegistry.当你第二次打开工具菜单时,你将注意到在这个菜单选项附近有一个复选框.这是你的注册器正在运行的线索.再次选中它将会关闭RMIRegistry.<br /> <br /></font>
                                        </p>
                                        
                                        <p>
                                          Alternatively, you can start the RMIRegistry from the command line under Windows 95 or NT. To do this, type
                                        </p>
                                        
                                        <ul>
                                          <li>
                                            setvars (jbuilder install directory)
                                          </li>
                                          <li>
                                            start rmiregistry
                                          </li>
                                        </ul>
                                        
                                        <p>
                                          <font color="#0000ff">作为一种选择,你可以在Windows 95或者NT下从命令行运行RMIRegistry.要想做到这样,键入</font>
                                        </p>
                                        
                                        <ul>
                                          <li>
                                            <font color="#0000ff">setvars (jbuilder安装目录下) </font>
                                          </li>
                                          <li>
                                            <font color="#0000ff">start rmiregistry </font>
                                          </li>
                                        </ul>
                                        
                                        <p>
                                          which will cause the RMI registry to be started in its own DOS window. The RMI registry must be started before you can start your server.<br /> <br /><font color="#0000ff">这将会使RMI注册器在它自己的DOS窗口下运行.RMI注册器必须在你运行你自己的服务器之前运行.</font>
                                        </p>
                                      </li>
                                      
                                      <li>
                                        Start your RMI server program.<br /> <br /><font color="#0000ff">运行你自己的RMI服务器程序.<br /> <br /></font>Run the SimpleRMIServer from the project. This starts the server running. As we discussed earlier, the server then creates an instance of SimpleRMIImpl and makes it known to the RMI server as "SimpleRMIImpl instance".</p> <p>
                                          从项目中运行SimpleRMIServer.这将使服务器运行.正如我们早些时候讨论的,这个服务器于是建立一个SimpleRMIImpl的示例并且使它<font color="#0000ff">被RMI服务器命名为"SimpleRMIImpl instance".<br /> <br /></font></li> 
                                          
                                          <li>
                                            Run your client program.<br /> <br /><font color="#0000ff">运行你的客户程序.<br /> <br /></font>Run SimpleRMIClient. The program will ask the RMI registry for a reference to "SimpleRMIImpl instance". After it has this reference, the client can invoke any methods declared in the SimpleRMIInterface interface as if the object were a local object.</p> <p>
                                              <font color="#0000ff">运行SimpleRMIClient.这个程序将会向RMI注册器询问一个"SimpleRMIImpl instance"的引用.在它获得这个引用之后,客户就能调用SimpleRMIInterface中定义的任意方法,就像这个对象是一个本地对象一样.<br /> <br /></font></li> </ol> 
                                              
                                              <p>
                                                After the RMI application has been created, you probably want to deploy the client apart from the server. To accomplish this you can use the Deployment Wizard to setup separate directories for the client files and for the server files.<br /> <br /><font color="#0000ff">在RMI应用程序被创建之后,你可能想把客户程序从服务器发布出去.为了实现这个目的,你可以使用Deployment Wizard(发布向导)来为客户文件和服务器文件建立分开的目录.</font>
                                              </p>
                                              
                                              <ol>
                                                <li>
                                                  Create a directory for the client &#8211; create a directory in any location of your liking and let us name it RMIClient<br /> <br /><font color="#0000ff">为客户建立一个目录 &#8211; 在你喜欢的任意位置创建一个目录,让我们把它命名为RMIClient</font>
                                                </li>
                                                <li>
                                                  Create a directory for the server &#8211; let us name it RMIServer<br /> <br /><font color="#0000ff">为服务器建立一个目录 &#8211; 让我们把它命名为RMIServer&#160;&#160;&#160;&#160; </font>
                                                </li>
                                                <li>
                                                  Setup the client deployment: bring up the Deployment Wizard, under the Wizards menu, and set the Delivery Options to &#8216;No Archive&#8217;. Select SimpleRMIClient.java, SimpleRMIInterface.java, and SimpleRMIImpl_Stub.java from the file list. Set the Archive Output Path to the client directory. If SimpleRMIImpl_Stub.java is not show on the Deployment Wizard file list, then you can also copy it manually from the comborlandsamplesrmisimple directory under the output root directory into the comborlandsamplesrmisimple under your client directory, RMIClient.<br /> <br /><font color="#0000ff">设置客户发布:启动Deployment Wizard(发布向导),在Wizards(向导)菜单下,并且设置Delivery Options(传送选项)为&#8217;No Archive'(不存档).从文件列表中选择SimpleRMIClient.java,SimpleRMIInterface.java和SimpleRMIImppl_Stub.java.设置Archive Output Path(存档输出路径)为客户目录.如果SimpleRMIImpl_Stub.java在发布向导的文件列表中没有出现,那么你也可以人工的将它从位于输出根目录下的comborlandsamplesrmisimple子目录下复制到你的客户目录RMIClient下的comborlandsamplesrmisimple子目录.</font>
                                                </li>
                                                <li>
                                                  Setup for the server deployment: repeat the previous step but select these files: SimpleRMIServer.java, SimpleRMIInterface.java, SimpleRMIImpl.java, SimpleRMIImpl_Skel.java, and SimpleRMIImpl_Stub.java. Put those files into your server directory, which we have named RMIServer. If SimpleRMIImpl_Stub.java and SimpleRMIImpl_Skel.java are not show on the Deployment Wizard file list, then you can also copy it manually from the comborlandsamplesrmisimple directory under the output root directory into the comborlandsamplesrmisimple directory under your server directory, RMIServer.<br /> <br /><font color="#0000ff">设置服务器发布:重复上一步骤但是选择这些文件: SimpleRMIServer.java, SimpleRMIInterface.java, SimpleRMIImpl.java, SimpleRMIImpl_Skel.java, 以及 SimpleRMIImpl_Stub.java.将这些文件放到你的服务器目录,即我们已经命名为RMIServer的目录.如果SimpleRMIImpl_Stub.java和SimpleRMIImpl_Skel.java在发布向导的文件列表中没有出现,那么你也可以人工的将它从位于输出根目录下的comborlandsamplesrmisimple子目录下复制到你的服务器目录RMIServer下的comborlandsamplesrmisimple子目录.</font>
                                                </li>
                                              </ol>
                                              
                                              <p>
                                                Now, once you have separate setup for the client and the server, the client can be run from a different computer than the server. If you take a look at SimpleRMIClient.java you will notice that the client application takes a single argument which should be a computer name, with the default of the name of the local computer, if it is not supplied. The direction below shows how to have the server running on the current machine and have client running from a different machine that are attached together through a TCP/IP network.<br /> <br /><font color="#0000ff">现在,一旦你设置分离了服务器和客户,与服务器相比较,客户可以在一个不同的计算机上运行.如果你看一下SimpleRMIClient.java,你将注意到客户程序仅仅使用一个是计算机名字的参数,如果没有提供这个参数,它的默认值是本地计算机的名字.下面的说明显示了如何在当前计算机上运行服务器程序,同时在另一台通过TCP/IP<a style="background-color:transparent;color:#0000ff;cursor:hand;text-decoration:underline;" class="iAs" target="_blank">网络</a>和本机连接起来的计算机上运行客户程序.</font>
                                              </p>
                                              
                                              <ol>
                                                <li>
                                                  Copy the client directory to a different machine that has either JBuilder or JDK 1.1 (or above) installed properly to run java application.<br /> <br /><font color="#0000ff">复制客户目录到一台已经正确的安装了JBuilder或者JDK1.1(或以上)能够运行java应用程序的不同的机器.</font>
                                                </li>
                                                <li>
                                                  Start the rmiregistry, as described above, on the current machine<br /> <br /><font color="#0000ff">启动rmiregistry,像在上面描述过的那样在当前计算机上</font>
                                                </li>
                                                <li>
                                                  Start the server application: bring up the DOS Window and change directory to your server directory, RMIServer. Run [jbuilder_install_dir]setvars [jbuilder_install_dir]. This should setup the environment variables to run java. Run java com.borland.samples.rmi.simple.SimpleRMIServer.java<br /> <br /><font color="#0000ff">启动服务器程序:打开DOS窗口,改变目录到你的服务器目录,RMIServer.运行[jbuilder安装目录]setvars [jbuilder安装目录].这将设置运行Java的环境变量.运行java com.borland.samples.rmi.simple.SimpleRMIServer.java</font>
                                                </li>
                                                <li>
                                                  Start the client on the client machine. Go to the client machine, bring up a DOS Window, change directory to the client directory, and type java com.borland.samples.rmi.simple.SimpleRMIClient [server_hostname].<br /> <br /><font color="#0000ff">在客户程序上启动客户.来到客户机,打开DOS窗口,改变目录到客户目录,然后键入java com.borland.samples.rmi.simple.SimpleRMIClient [服务器主机名].</font>
                                                </li>
                                              </ol>
                                              
                                              <p>
                                                <a name="rmi_and_jdk12"><font size="+0"><strong></p> 
                                                
                                                <p>
                                                  Addendum: RMI and JDK 1.2 Security<font size="+0"><br /> <br /></font><font color="#0000ff"><strong>附录:RMI和JDK1.2安全</strong></font>
                                                </p>
                                                
                                                <p>
                                                  </strong></font><br /> </a><font size="+0"><br /> <br /></font><font color="#0000ff"><strong>附录:RMI和JDK1.2安全</strong> </font>
                                                </p>
                                                
                                                <p>
                                                  The JDK 1.2 security model is more sophisticated than the model used for JDK 1.1. JDK 1.2 contains enhancements for finer-grained security and requires code to be granted specific permissions to be allowed to perform certain operations.<br /> <br /><font color="#0000ff">JDK 1.2的安全模型比JDK 1.1使用的模型更加严格.JDK 1.2包含了增强的指纹安全,需要代码被同意授于特定的许可来进行某些操作.</font>
                                                </p>
                                                
                                                <p>
                                                  RMI uses sockets to communicate between the processes, however if the RMI application uses the RMISecurityManager, then you need to modify the security policy so that the application is allowed to accept and connect to the other RMI application through the sockets.<br /> <br /><font color="#0000ff">RMI使用套接字来进行进程间的<a style="background-color:transparent;color:#0000ff;cursor:hand;text-decoration:underline;" class="iAs" target="_blank">通信</a>,然而如果RMI应用程序使用RMISecurityManager,那么你需要更改安全策略,从而使应用程序被允许通过套接字接受和连接到其它的RMI应用程序.</font>
                                                </p>
                                                
                                                <p>
                                                  The easiest way to setup the security mechanism to enable RMI is to modify the java.policy file under the javajrelibsecurity directory in your JBuilder installation directory. Open it with a text editor and modify the line that says:<br /> <br /><font color="#0000ff">最简单的使安全机制使RMI可用的设置方法是更改在JBuiler安装目录下的javajrelibsecurity目录下的文件java.policy.用一个文本编辑器打开它并且更改如下行:</font>
                                                </p>
                                                
                                                <blockquote>
                                                  <p>
                                                    permission java.net.SocketPermission "localhost:1024-", "listen";
                                                  </p>
                                                </blockquote>
                                                
                                                <p>
                                                  to<br /> <br /><font color="#0000ff">为</font>
                                                </p>
                                                
                                                <blockquote>
                                                  <p>
                                                    permission java.net.SocketPermission "localhost:1024-", "listen, accept, connect";
                                                  </p>
                                                </blockquote>
                                                
                                                <p>
                                                  This should allow you to run the server application and the client application on a local machine.<br /> <br /><font color="#0000ff">这将允许你在本地计算机上运行服务器应用程序和客户应用程序.</font>
                                                </p>
                                                
                                                <p>
                                                  Please note that java.policy file controls the overall Java security policy. Alternatively you can create a file named &#8216;.java.policy&#8217; that resides in the user&#8217;s home directory. On Windows platform, the user&#8217;s home directory typically translates to the Windows installation directory, while on Unix the user&#8217;s home directory refers to the actual user&#8217;s home directory.<br /> <br /><font color="#0000ff">请注意文件java.policy控制了全部的Java安全策略.另一种选择是你可以建立一个名字为".java.policy"的文件放在用户的家目录下.在Windows平台上,用户的家目录代表性的翻译为Windows安装目录,然而在Unix上,用户的家目录是指目前用户的家目录.</font>
                                                </p>
                                                
                                                <p>
                                                  For a more thorough explanation on JDK 1.2 Security, please take a look at this excellent <a href="http://www.javasoft.com/docs/books/tutorial/security1.2/">tutorial at JavaSoft&#8217;s site</a>.
                                                </p>
                                                
                                                <p>
                                                  <font color="#0000ff">要想得到JDK 1.2的安全的更彻底的解释,请去看看极好的<a href="http://www.javasoft.com/docs/books/tutorial/security1.2/">JavaSoft站点的教程</a>.</font>
                                                </p>
                                                
                                                <hr />
                                                
                                                <p>
                                                  补充说明:<br /> <br />此目录下的程序没有包名,并且RMI的端口也被更改为5000,详情请参看源代码.
                                                </p>
                                                
                                                <p>
                                                  建立一个没有名字,只有扩展名的文件可以使用Windows的edit.com,这里用来建立.java.policy.或者使用位于JDK安装目录下的policytool.exe来保存文件为此名称,或者是除了notepad.exe以外的其它文本编辑器,甚至你可以使用一个Java程序来建立,最简单的就是使用COPY CON FILE的DOS命令.
                                                </p>
                                                
                                                <p>
                                                  如果你只想在此处使用安全策略,那么可以建立一个为.policy为扩展名的文件,例如java.policy.在文件中写入如下内容[此处允许所有主机]:
                                                </p>
                                                
                                                <p>
                                                  grant
                                                </p>
                                                
                                                <p>
                                                  {
                                                </p>
                                                
                                                <p>
                                                  permission java.net.SocketPermission "*:1024-", "listen, accept, connect";
                                                </p>
                                                
                                                <p>
                                                  };
                                                </p>
                                                
                                                <p>
                                                  然后使用这个策略文件的命令是:
                                                </p>
                                                
                                                <p>
                                                  运行客户程序:
                                                </p>
                                                
                                                <p>
                                                  java -Djava.security.policy=java.policy SimpleRMIClient
                                                </p>
                                                
                                                <p>
                                                  运行服务器程序:
                                                </p>
                                                
                                                <p>
                                                  java -Djava.security.policy=java.policy SimpleRMIServer
                                                </p>
                                                
                                                <p>
                                                  使RMI运行在5000端口的命令:rmiregistry 5000
                                                </p>
                                                
                                                <p>
                                                  使用rmic.exe可以得到存根文件,此处的用法是:rmic SimpleRMIImpl
                                                </p>
                                                
                                                <p>
                                                  如果生成JDK1.2的存根类,这样:rmi -V1.2 SimpleRMIImpl
                                                </p>
                                                
                                                <p>
                                                  RMI的命名规则:
                                                </p></p> 
                                                
                                                <table border="1" width="100%">
                                                  <tr>
                                                    <td width="50%">
                                                      无后缀&#160;&#160;&#160; [例如A]
                                                    </td>
                                                    
                                                    <td width="50%">
                                                      远程接口
                                                    </td>
                                                  </tr>
                                                  
                                                  <tr>
                                                    <td width="50%">
                                                      Impl后缀&#160; [例如AImpl]
                                                    </td>
                                                    
                                                    <td width="50%">
                                                      实现接口的服务器类
                                                    </td>
                                                  </tr>
                                                  
                                                  <tr>
                                                    <td width="50%">
                                                      Server后缀[例如AServer]
                                                    </td>
                                                    
                                                    <td width="50%">
                                                      创建服务器对象的服务器程序
                                                    </td>
                                                  </tr>
                                                  
                                                  <tr>
                                                    <td width="50%">
                                                      Client后缀[例如AClient]
                                                    </td>
                                                    
                                                    <td width="50%">
                                                      调用远程方法的客户程序
                                                    </td>
                                                  </tr>
                                                  
                                                  <tr>
                                                    <td width="50%">
                                                      _Stub后缀 [例如A_Stub]
                                                    </td>
                                                    
                                                    <td width="50%">
                                                      rmic程序自动生成的代码存根类
                                                    </td>
                                                  </tr>
                                                  
                                                  <tr>
                                                    <td width="50%">
                                                      _Skel后缀 [例如A_Skel]
                                                    </td>
                                                    
                                                    <td width="50%">
                                                      rmic程序自动生成的框架类[适用于JDK1.1]
                                                    </td>
                                                  </tr>
                                                </table>
                                                
                                                <p>
                                                  相关的评论:<br />
                                                </p>
                                                
                                                <table border="0" cellspacing="0" cellpadding="0" width="700">
                                                  <tr align="left">
                                                    <td colspan="4">
                                                      <h4>
                                                        <a name="comment$(remark.remarkID)">评论人：匿名网友</a> <span>&#160; 2004-12-07 13:50:48 <a><img border="0" src="http://blog.bokee.com/img/linkblog.jpg" /></a> </span>
                                                      </h4>
                                                    </td>
                                                  </tr>
                                                  
                                                  <tr align="left">
                                                    <td valign="top" colspan="4">
                                                      <p class="comment">
                                                        首先 我要感谢&#160; 整蛊之王&#160; 提醒了我，我还在网上寻找这方面的列程，看了你的东西之后，就去JBuilder的Sample目录下去看了看，找到了你所说的例子。
                                                      </p>
                                                      
                                                      <p>
                                                        然后按照你翻译的就去做了，竟然失败。查看原因：说找不到&#160; SimpleRMIImpl.java&#160; 这些文件，我就觉得奇怪了，明明就在目录下怎么会找不到那？我又仔细察看了保错信息，发现他说是在 C:&#8230;&#8230;.下找不到这个文件，但是我的JBuilder是装在D:&#8230;..目录里。于是我就用&#160; UltraEdit（注意）&#160;&#160; 打开这个工程的工程文件 SimpleRMI.jpx ，果然在其中发现了什么&#160; C:&#8230;&#8230;.然后修改成为我JBuilder所安装的路径，然后再去打开这个工程就抱错，说是文档不正确，然后我才想到&#160; UltraEdit&#160; 打开一个文件 时回把它Format 成 Dos 格式，于是我就用其他工具它开那个文件再修改才成功。
                                                      </p>
                                                      
                                                      <p>
                                                        这上面有两点注意：一个是JBuilder的安装目录，一个是打开那个工程文件的编辑器。
                                                      </p>
                                                      
                                                      <p>
                                                        我写出这些，希望大家不要犯和我一样的错误
                                                      </p>
                                                      
                                                      <p>
                                                        BeanSoft:
                                                      </p>
                                                    </td>
                                                  </tr>
                                                </table>
                                                
                                                <p>
                                                  正确的程序的运行方法是: 首先运行 runRMIRegistry.bat, 这个启动 RMI 注册程序, 然后运行 runServer.bat, 这个启动用户编写的 RMI 服务器, 最后, 运行 runClient.bat, 就可以看到返回当前日期了.
                                                </p>
                                                
                                                <p>
                                                  至于 JB8 的发布向导的问题, 我可以告诉大家一下, 好像自从 JB7 以后的版本中, 这个功能已经合并到了 Archive Builder 中, 访问的菜单是 File->New->Build->Archive Builder.
                                                </p>
                                                
                                                <p>
                                                  选项都选择默认的, 应该就可以打包了.
                                                </p>
                                                
                                                <p>
                                                  </div>
                                                </p></div> </p></div> 
                                                
                                                <p>
                                                  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2006/11/22/rmi%e7%bc%96%e7%a8%8b%e7%ae%80%e5%8d%95%e6%95%99%e7%a8%8b%e6%9d%a5%e8%87%aajbuilder/">RMI编程简单教程(来自JBuilder)</a>
                                                </p>