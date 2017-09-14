---
id: 577
title: 久违或遗忘的WebLogic Java工具
date: 2010-08-16T22:11:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=577
permalink: '/2010/08/16/%e4%b9%85%e8%bf%9d%e6%88%96%e9%81%97%e5%bf%98%e7%9a%84weblogic-java%e5%b7%a5%e5%85%b7/'
views:
  - "3334"
original_post_id:
  - "577"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来自: 久违或遗忘的WebLogic Java工具 <http://www.weblogicfans.net/viewthread.php?tid=2875&highlight=>

使用WebLogic Java工具

WebLogic提供了几个Java应用程序用以简化安装与配置任务、提供服务以及提供方便的快捷方式。本章描述了WebLogic所提供的这些工具。本章给出了所有工具的命令行语法，有些还提供了示例。本章描述了以下工具：

1. AppletArchiver

2. Conversion

3. der2pem

4. dbping

5. deploy

6. getProperty

7. logToZip

8. MulticastTest

9. myip

10. pem2der

11. Schema

12. showLicenses

13. system

14. t3dbping

15. verboseToZip

16. version

17. writeLicense

在使用这些工具之前必须先正确地设置CLASSPATH 。详细信息，请参见“设置类路径选项”。

**AppletArchiver**

AppletArchiver工具在一个单独的框架中运行applet，并记录所有下被 applet下载的类与applet使用的资源，然后将它们打包在一个.jar文件或.cab文件中（cabarc工具可以从Microsoft得到）

语法

$ java utils.applet.archiver.AppletArchiver URL filename

参数 定义

URL Applet的URL

filename 打包后的.jar/.cab文件名

**Conversion**

如果你使用过以前版本的WebLogic，那么必须要转换weblogic.properties文件。在管理控制台在线帮助的“Conversion”部分中介绍了如何使用转换脚本来转换文件。

**Der2pem**

Der2pem工具用来把DER格式的X509证书转换为PRM格式。转换所得到的.pem格式的文件与原.der文件位于同一个目录中。

格式：

$ java utils.der2pem derFile \[headerFile\]\[footerFile\]

参数 描述

derFile 要进行转换的文件名。该文件的扩展名必须为.der扩展，并且.der文件中必须有一个有效的证书。

headerFile 放在PEM文件中的文件头。缺省的文件头为“&#8212;&#8212;BEGIN CERTIFICATE&#8212;&#8212;-” 。

如果要进行转换的DER文件是一个私钥文件，那么应该创建一个头文件，该头文件包含以下内容之一：

如果是未加密的私钥文件，那么为“&#8212;&#8211;BEGIN RSA PRIVATE KEY&#8212;&#8211;”

如果是加密的私钥文件，那么为“&#8212;&#8211;BEGIN ENCRYPTED PRIVATE KEY”

注意：文件头所在行的结尾应该另起一行。

footerFile 放在PEM文件中的头。缺省的文件头为“&#8212;&#8211;END CERTIFICATE&#8212;&#8211;”。

如果所转换的DER文件是一个私钥文件，那么应该使用一个脚注文件。所创建的脚注文件应该包含以下内容之一

如果是一个未加密的私钥，那么为“&#8212;&#8211;END RSA PRIVATE KEY&#8212;&#8211;”

如果是加密的私钥文件，那么应该为“&#8212;&#8211;END ENCRYPTED PRIVATE KEY&#8212;&#8211;”。

注意：在文件头所在行的结尾处应该另起一行。

例子

$ java utils.der2pem graceland_org.der

Decoding

dbping

dbping命令行工具用来测试DBMS与客户端之间使用两层WebLogic jDriver的连接。

语法

$ java utils.dbping DBMS user password DB

参数 定义

DBMS 该参数为MSSQLSERVER4, ORACLE, 或INFORMIX4

user 登录用的有效用户名。可以用isql或sqlplus中所使用的用户名

password 用户的口令。可以用isql或sqlplus所使用的口令。

DB 数据库的文件名，可以用isql或sqlplus所使用的值。

**Deploy**

Deploy工具从一个包文件中得到J2EE应用，并把该应用部署到正在运行着的WebLogic服务器中。更多的信息可以参见“组装并配置Web应用”以及编程指南中的“开发WebLogic 服务器应用”中的内容。

参数

$ java weblogic.deploy \[options\] \[action\] password {application name} {source}

Actions(从下表中选一个)

Action 描述

List 列出指定WebLogic服务器中的所有应用

deploy 将一个J2EE应用.jar,.war或.ear文件部署到指定的服务器中

undeploy 删除指定服务器上的一个应用

update 在指定服务器上重新部署一个应用

delete 按给出的应用名删除一个应用

其它参数

参数 描述

口令 指定WebLogic服务器的系统口令

应用名 指定应用的名字。应用的名字可以在分发时指定，也可以使用分发或控制台工具指定。

源 指出应用包文件（.jar,.war或.ear）的exact位置，或者是应用目录所在的路径。

选项

选项 定义

-help 打印出deploy工具的所有选项

-version 打印出deploy工具的版本

-port port 指定WebLogic服务器用来部署J2EE应用.jar,.war,或.ear文件的端口号。

-host host 指定部署J2EE应用（.jar, .war, .ear）的WebLogic服务器的主机名。

-url url 指定 WebLogic服务器的URL，缺省为localhost:7001

-component componentname: target1, target2 部署到各种目标上的组件，必须指定为：

componentname:target1, target2

可以任意多个组件指定该选项，且可以指定任意多次。

，-username username 连接所使用的用户名，缺省为sytem。

-debug 将部署过程中的详细调试信息输出到stdout。

例子

部署工具可用于多种目的：

查看一个J2EE应用

部署一个新J2EE应用

删除一个J2EE应用

更新一个J2EE应用

查看一个J2EE应用

以下命令可以查看部署在本地服务器上的一个应用

% java weblogic.deploy list password

Password的值为WebLogic服务器系统帐号的口令。

如果要列出远程服务器上所部署的应用，那么应该指定port与host选项，如下所示：

java.weblogic.deploy –port port\_number –host host\_name list password

部署J2EE应用

部署一个还不曾分发到WebLogic的J2EE应用文件（.jar, .war, .ear）或应用目录，使用如下命令：

% java weblogic.deploy -port port\_number -host host\_name deploy password application source

? application为分配给所部署应用的字符串

? source为所要部署的J2EE应用文件的全路径（.jar,.war, .ear），或者是应用目录的全路径。

例如：

% java weblogic.deploy -port 7001 -host localhost deploy weblogicpwd Basic_example c:mysamplesejbbasicBasicStatefulTraderBean.jar

注意：当J2EE文件（.jar, .war, .ear）复制到管理服务器的应用目录时，将以应用的名字重命名该文件。因此，上面这个例子中，应用包的名字. . ./config/mydomain/applications目录从BasicStatefulTraderBean.jar改变为Basic_example.jar。

删除一个J2EE应用

要删除一个已部署的J2EE阴功，只需要引用所分配的应用名，如下图所示：

% java weblogic.deploy -port 7001 -host localhost undeploy weblogicpwd Basic_example

注意：删除一个J2EE应用并没有把该应用从WebLogic服务器中删去。你不能在deploy工具中重用这个应用的名字。你只能在更新所部署的应用时重用应用的名字。具体内容见下节。

更新一个部署了的J2EE应用

要更新J2EE应用，应该使用update参数并指定活动J2EE应用的名字，如下所示：

% java weblogic.deploy -port 7001 -host localhost update weblogicpwd Basic_example c:updatesampleejbbasicBasicStatefulTraderBean.jar

以下命令用于更新一或多个服务器上的指定组件。

% java weblogic.deploy -port 7001 -host localhost –component

BasicStatefulTraderBean.jar:sampleserver,exampleserver update weblogicpwd Basic_example c:updatesampleejbbasicBasicStatefulTraderBean.jar

**getProperty**

你可以用getProperty工具获得系统与Java设置的详细信息。它不需要参数。

语法

$ java utils.getProperty

例子

$ java utils.getProperty

&#8212; listing properties &#8212;

user.language=en

java.home=c:java11bin..

awt.toolkit=sun.awt.windows.WToolkit

file.encoding.pkg=sun.io

java.version=1.1_Final

file.separator=

line.separator=

user.region=US

file.encoding=8859_1

java.vendor=Sun Microsystems Inc.

user.timezone=PST

user.name=mary

os.arch=x86

os.name=Windows NT

java.vendor.url=http://www.sun.com/

user.dir=C:weblogic

java.class.path=c:weblogicclasses;c:javalibcla&#8230;

java.class.version=45.3

os.version=4.0

path.separator=;

user.home=C:

logToZip

The logToZip utility searches an HTTP server log file in common log format, finds the Java classes loaded into it by the server, and creates an uncompressed .zip file that contains those Java classes. It is executed from the document root directory of your HTTP server.

要使用该工具，你必须有访问由HTTP服务器创建的日志文件。

语法

$ java utils.logToZip logfile codebase zipfile

参数 定义

logfile 该参数是必需的。为日志文件的全路径名

codebase 该参数是必需的。Code base for the applet, or "" ifthere is no code base.By

concatenating the code base with the full package name of the applet, you

get the full pathname of the applet (relative to the HTTP document root).

zipfile 该参数是必需的，zipfile是所创建的.zip文件的文件名，该zip文件位于你运行程序的那个目录。该文件的路径可以是相对路径也可以是绝对路径。下面的例子给出了一个相对路径，因此.zip文件被创建在当前目录下。

例子

下面这个例子说明了如何为文档根中（即没有用code base）的一个applet创建一个.zip文件：

$ cd /HTTP/Serv/docs

$ java utils.logToZip /HTTP/Serv/logs/access "" app2.zip

下面这个例子说明了如何为文档根的子目录中的一个applet创建一个.zip文件：

C:>cd HTTPServ

C:HTTPServ>java utils.logToZip logsappletsclasses app3.zip

**MulticastTest**

你可以在配置WebLogic集群时，用该工具测试有关广播的问题。该工具发送广播包并返回广播在网络中的工作效率的信息。特别地，MulticastTest将以下类型的信息显示在标准输出上。

1．服务器所发送的每个消息的确认与序列号。

2．集群服务器所收到的每个消息的序列号与发送方ID

3．当一个消息没有按顺序接收到时的错误顺序警告。

4．当一个预期的消息没有受到时的消息丢失警告。

在使用MulticastTest时，应该在每个需要测试广播消息流量的节点上启动该工具。

警告：在指定MulticastTest工具的广播地址时（由-a 参数指定），注意不要设置为集群的广播地址。在启动集群服务器之前用该工具验证广播是否能正常工作。

有关设置广播地址的详细信息，可以参见WebLogic服务器所在主机的操作系统/硬件的配置文档。更多信息，请参见“使用WebLogic服务器集群”。

语法

$ java utils.MulticastTest -n name -a address \[-p portnumber\] \[-t timeout\] [-s send]

参数 定义

-n name 必需的参数。用以表示顺序消息的发送方。应该为每个启动的测试进程使用不同的名字

-a address 必需的参数。是一个广播地址用于：（a）广播顺序消息；（b）集群中的服务器与其它服务器通信。（集群的广播地址的缺省值不应设为237.0.0.1）

-p portnumber 可选参数。集群中的服务器进行通信的广播端口。（广播端口与WebLogic的监听端口相同，缺省为7001）

-t timeout 可选参数。Idle timeout, in seconds, if no multicast messages are received. 缺省时间为600秒（10分钟）。如果过了超时时间，a positive confirmation of the timeout is sent to sdout。

-s send 可选参数。发送消息的时间间隔，缺省值为2秒。A positive confirmation of each message sent out is sent to stdout。

例子

$ java utils.MulticastTest -N server100 -A 237.155.155.1

Set up to send and receive on Multicast on Address 237.155.155.1 on

port 7001

Will send a sequenced message under the name server100 every 2

seconds.

Received message 506 from server100

Received message 533 from server200

I (server100) sent message num 507

Received message 507 from server100

Received message 534 from server200

I (server100) sent message num 508

Received message 508 from server100

Received message 535 from server200

I (server100) sent message num 509

Received message 509 from server100

Received message 536 from server200

I (server100) sent message num 510

Received message 510 from server100

Received message 537 from server200

I (server100) sent message num 511

Received message 511 from server100

Received message 538 from server200

I (server100) sent message num 512

Received message 512 from server100

Received message 539 from server200

I (server100) sent message num 513

Received message 513 from server100

myip

返回主机的IP地址。

语法

$ java utils.myip

例子

$ java utils.myip

Host toyboat.toybox.com is assigned IP address: 192.0.0.1

**Pem2der**

Pem2der工具用以将PEM格式的X509证书转换为DER格式，转换所得的.der文件与原.pem文件位于同一目录中。

语法

$ java utils.pem2der pemFile

参数 描述

pemFile 要进行转换的证书的文件名。该文件的扩展名必须为.pem，且必须包含一个有效的.pem格式的证书。

例子

$ java utils.pem2der graceland_org.pem 

Decoding

&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;.

&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;.

&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;.

&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;.

&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;.

**Schema**

Schema工具使用WebLogic JDBC驱动将SQL语句上载到一个数据库中。有关数据库连接的详细信息可以参见“WebLogic JDBC编程”中的信息。

语法

$ java utils.Schema driverURL driverClass \[-u username\] \[-p password\][-verbose SQLfile]

参数 定义

driverURL 该参数是必需的。JDBC驱动的URL

driverClass 该参数是必需的。JDBC驱动类的路径名

-u username 可选参数。一个有效的用户名

-p password 可选参数。一个有效的用户名

-verbose 可选参数。打印出SQL语句与数据库的信息

SQLfile 如果用了-verbose参数，那么就应该设置该参数。包含SQL语句的文本文件

例子

下面是一个Schema命令行的例子：

$ java utils.Schema "jdbc:cloudscape:demo;create=true" COM.cloudscape.core.JDBCDriver -verbose examples/utils/ddl/demo.ddl

下面是一个.ddl文件中的内容

DROP TABLE ejbAccounts;

CREATE TABLE ejbAccounts

(id varchar(15),

bal float,

type varchar(15));

DROP TABLE idGenerator;

CREATE TABLE idGenerator

(tablename varchar(32),

maxkey int);

showLicenses

showLicenses工具显示了所安装的BEA产品的许可证信息。

语法

$ java utils.showLicenses

**system**

system工具显示操作系统的基本信息，包括所使用的JDK的制造商与版本号、类路径以及操作系统的详细信息。

语法

$ java utils.system

例子

$ java utils.system

\* \* \* \* \* \* \* java.version \* \* \* \* \* \* \*

1.1.6

\* \* \* \* \* \* \* java.vendor \* \* \* \* \* \* \*

Sun Microsystems Inc.

\* \* \* \* \* \* \* java.class.path \* \* \* \* \* \* \*

javalibclasses.zip;weblogicclasses;

weblogiclibweblogicaux.jar;weblogiclicense

&#8230;

\* \* \* \* \* \* \* os.name \* \* \* \* \* \* \*

Windows NT

\* \* \* \* \* \* \* os.arch \* \* \* \* \* \* \*

x86

\* \* \* \* \* \* \* os.version \* \* \* \* \* \* \*

4.0

t3dbping

该工具用来测试使用两层JDBC驱动程序的WebLogic JDBC连接。使用该工具时，你必须有访问WebLogc与DBMS的权限。

语法

$ java utils.t3dbping WebLogicURL username password DBMS driverClass driverURL

参数 定义

WebLogicURL 该参数是必需的。WebLogic服务器的URL

username 该参数是必需的。一个DBMS用户的用户名

password 该参数是必需的。DBMS用户口令

DBMS 该参数是必需的。数据库的名字

driverClass 该参数是必须的。WebLogic两层驱动程序的完整包名

driverURL 该参数是必需的。WebLogic两层驱动程序的URL。

**verboseToZip**

如果从HTTP服务器的文档根目录中执行该工具，verboseToZip获得运行在verbose模式的标准输出，找到所引用的Java类，并创建一个包含这些Java类的uncompressed .zip文件。

语法

$ java utils.verboseToZip inputFile zipFileToCreate

参数 定义

inputFile 该参数是必须的。它设置了一个临时文件保存以verbose模式运行的应用的输出。

zipFileToCreate 该参数是必须的。要创建的.zip文件的名字。该文件保存在你运行工具所在的目录。

UNIX上的例子

$ java -verbose myapplication > & classList.tmp

$ java utils.verboseToZip classList.tmp app2.zip

NT上的例子

$ java -verbose myapplication > classList.tmp

$ java utils.verboseToZip classList.tmp app3.zip

version

version工具将所安装的WebLogic的版本信息输出到stdout。

语法

$ java weblogic.version

例子

$ java weblogic.version WebLogic Build: 4.0.1 04/05/1999 22:02:11 #41864

**writeLiense**

writeLiense工具将WebLogic的许可证信息写到当前目录中的一个名字为writeLicense.txt文件中，然后可以将这个文件通过email发送给其它人，如WebLogic的技术支持。

语法

$ java utils.writeLicense -nowrite -Dweblogic.system.home=path

参数 定义

-nowrite 该参数是必须的。输出到stdout而不是writeLicense.txt

-Dweblogic.system.home 该参数是必须的。该参数设置了WebLogic system home(WebLogic所在的根目录)

注意：该参数是必须的，但如果从WebLogic system home运行writeLicense工具，那么可以不设置该参数

例子

$ java utils.writeLicense -nowrite

UNIX上的输出示例：

\* \* \* \* \* \* System properties \* \* \* \* \* \*

\* \* \* \* \* \* \* java.version \* \* \* \* \* \* \*

1.1.7

\* \* \* \* \* \* \* java.vendor \* \* \* \* \* \* \*

Sun Microsystems Inc.

\* \* \* \* \* \* \* java.class.path \* \* \* \* \* \* \*

c:weblogicclasses;c:weblogiclibweblogicaux.jar;

c:java117libclasses.zip;c:weblogiclicense

&#8230;

Windows NT上的输出示例：

\* \* \* \* \* \* \* os.name \* \* \* \* \* \* \*

Windows NT

\* \* \* \* \* \* \* os.arch \* \* \* \* \* \* \*

x86

\* \* \* \* \* \* \* os.version \* \* \* \* \* \* \*

4.0

\***\*\\*\*IP\*\*\****

Host myserver is assigned IP address: 192.1.1.0

\* \* \* \* \* \* Location of WebLogic license files \* \* \* \* \* \*

No WebLogicLicense.class found

No license.bea license found in

weblogic.system.home or current directory

Found in the classpath: c:/weblogic/license/license.bea

Last Modified: 06/02/1999 at 12:32:12

\* \* \* \* \* \* Valid license keys \* \* \* \* \* \*

Contents:

Product Name : WebLogic

IP Address : 192.1.1.0-255

Expiration Date: never

Units : unlimited

key : b2fcf3a8b8d6839d4a252b1781513b9

&#8230;

\* \* \* \* \* \* All license keys \* \* \* \* \* \*

Contents:

Product Name : WebLogic

IP Address : 192.1.1.0-255

Expiration Date: never

Units : unlimited

key : b2fcf3a8b8d6839d4a252b1781513b9

&#8230;

\* \* \* \* \* \* WebLogic version \* \* \* \* \* \*

WebLogic Build: 4.0.x xx/xx/1999 10:34:35 #xxxxx

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [久违或遗忘的WebLogic Java工具](http://www.beansoft.biz/2010/08/16/%e4%b9%85%e8%bf%9d%e6%88%96%e9%81%97%e5%bf%98%e7%9a%84weblogic-java%e5%b7%a5%e5%85%b7/)