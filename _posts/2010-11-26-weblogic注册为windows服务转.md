---
id: 1444
title: 'weblogic注册为windows服务[转]'
date: 2010-11-26T12:43:27+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1444
permalink: '/2010/11/26/weblogic%e6%b3%a8%e5%86%8c%e4%b8%bawindows%e6%9c%8d%e5%8a%a1%e8%bd%ac/'
views:
  - "6800"
original_post_id:
  - "1444"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
  - 转载区
---
转自:&#160; <http://www.tonyxu.net/weblogic/201011369/weblogic-service-windows.html> 作者: Tony Xu

环境:

windows 2003 server,weblogic816

安装weblogic及创建domain的过程略。

[<img title="截图04" height="375" alt="截图04" src="http://www.tonyxu.net/wp-content/uploads/2010/11/04_thumb.png" width="575" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/11/04.png)

将myserver注册为windows服务的脚本如下:

1、路径 C:bea816user_projectsdomainsmydomaininstallService.cmd

脚本的内容如下（重点需注意的地方加粗）

> @rem \***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\****   
> @rem This script is used to install WebLogic Server as a service for the   
> @rem domain in the current working directory.&#160;   
> @rem   
> @rem To create your own domain script, all you need to set is   
> @rem SERVER\_NAME, then call %WL\_HOME%serverbininstallSvc.cmd   
> @rem   
> @rem Other variables that installService takes are:   
> @rem   
> @rem WLS_USER&#160;&#160;&#160;&#160; – cleartext user for server startup   
> @rem WLS_PW&#160;&#160;&#160;&#160;&#160;&#160; – cleartext password for server startup   
> @rem PRODUCTION_MODE&#160;&#160;&#160; – true for production mode servers, false for   
> @rem&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; development mode   
> @rem JAVA_OPTIONS – Java command-line options for running the server. (These   
> @rem&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; will be tagged on to the end of the JAVA\_VM and MEM\_ARGS)   
> @rem JAVA_VM&#160;&#160;&#160;&#160;&#160; – The java arg specifying the VM to run.&#160; (i.e. -server,   
> @rem&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; -hotspot, etc.)   
> @rem MEM_ARGS&#160;&#160;&#160;&#160; – The variable to override the standard memory arguments   
> @rem&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; passed to java   
> @rem   
> @rem For additional information, refer to the WebLogic Server Administration   
> @rem Console Online Help(<http://e-docs.bea.com/wls/docs81/ConsoleHelp/startstop.html)>   
> @rem \***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\****
> 
> echo off   
> SETLOCAL
> 
> **set WL_HOME=C:bea816weblogic81**
> 
> @rem Set Production Mode.&#160; When this is set to true, the server starts up in   
> @rem production mode.&#160; When set to false, the server starts up in development   
> @rem mode.&#160; If it is not set, it will default to false.   
> set PRODUCTION_MODE=true
> 
> @rem Set JAVA_VENDOR to java virtual machine you want to run on server side.   
> set JAVA_VENDOR=BEA
> 
> @rem Set JAVA_HOME to java virtual machine you want to run on server side.   
> **set JAVA\_HOME=C:bea816jrockit81sp6\_142_10**
> 
> call "%WL_HOME%commonbincommEnv.cmd"
> 
> @rem USERDOMAIN_HOME is preset to the domain directory.   
> set USERDOMAIN\_HOME=C:bea816user\_projectsdomainsmydomain
> 
> @rem Set SERVER_NAME to the name of the server you wish to start up.   
> **set SERVER_NAME=myserver**
> 
> @rem Set DOMAIN_NAME to the name of the server you wish to start up.   
> **set DOMAIN_NAME=mydomain**
> 
> @rem Set WLS\_USER equal to your system username and WLS\_PW equal&#160;   
> @rem to your system password for no username and password prompt   
> @rem during server startup.&#160; Both are required to bypass the startup   
> @rem prompt.   
> **set WLS_USER=weblogic   
> set WLS_PW=weblogic**
> 
> if NOT "%1" == "" set WLS_USER=%1   
> if NOT "%2" == "" set WLS_PW=%2
> 
> if "%WLS_USER%" == "" goto usage   
> if "%WLS_PW%" == ""&#160; goto usage   
> goto continue
> 
> :usage   
> echo Need to set WLS\_USER and WLS\_PW environment variables or specify   
> echo them in command line:   
> echo Usage: installService.cmd \[WLS\_USER\] \[WLS\_PW\]   
> echo for example:   
> echo installService.cmd user password   
> goto finish
> 
> :continue
> 
> @rem Set JAVA_OPTIONS to the java flags you want to pass to the vm. i.e.:   
> @rem set JAVA_OPTIONS=-Dweblogic.attribute=value -Djava.attribute=value   
> set JAVA_OPTIONS=
> 
> @rem Set JAVA_VM to the java virtual machine you want to run.&#160; For instance:   
> @rem set JAVA_VM=-server   
> @rem set JAVA_VM=
> 
> @rem Set MEM_ARGS to the memory args you want to pass to java.&#160; For instance:   
> **set MEM_ARGS=-Xms384m -Xmx384m   
>** @rem set MEM_ARGS=
> 
> @rem Check that the WebLogic classes are where we expect them to be   
> :checkWLS   
> if exist "%WL_HOME%serverlibweblogic.jar" goto checkJava   
> echo The WebLogic Server wasn’t found in directory %WL_HOME%server.   
> echo Please edit your script so that the WL_HOME variable points   
> echo to the WebLogic installation directory.   
> goto finish
> 
> @rem Check that java is where we expect it to be   
> :checkJava   
> if exist "%JAVA_HOME%binjava.exe" goto runWebLogic   
> echo The JDK wasn’t found in directory %JAVA_HOME%.   
> echo Please edit your script so that the JAVA_HOME variable   
> echo points to the location of your JDK.   
> goto finish
> 
> :runWebLogic
> 
> @echo on
> 
> set CLASSPATH=%WEBLOGIC_CLASSPATH%;%CLASSPATH%
> 
> @echo \***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***   
> @echo \*&#160; To start WebLogic Server, use the password&#160;&#160;&#160;&#160; \*   
> @echo \*&#160; assigned to the system user.&#160; The system&#160;&#160;&#160;&#160;&#160;&#160; \*   
> @echo \*&#160; username and password must also be used to&#160;&#160;&#160;&#160; \*   
> @echo \*&#160; access the WebLogic Server console from a web&#160; \*   
> @echo \*&#160; browser.&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; \*   
> @echo \***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***
> 
> rem \*** Set Command Line for service to execute within created JVM
> 
> @echo off
> 
> if "%ADMIN_URL%" == "" goto runAdmin   
> @echo on   
> set CMDLINE="%JAVA\_VM% %MEM\_ARGS% %JAVA\_OPTIONS% -classpath "%CLASSPATH%" -Dweblogic.Name=%SERVER\_NAME% -Dweblogic.management.username=%WLS\_USER% -Dweblogic.management.server="%ADMIN\_URL%" -Dweblogic.ProductionModeEnabled=%PRODUCTION\_MODE% -Djava.security.policy="%WL\_HOME%serverlibweblogic.policy" weblogic.Server"   
> goto installSvc
> 
> :runAdmin   
> @echo on   
> set CMDLINE="%JAVA\_VM% %MEM\_ARGS% %JAVA\_OPTIONS% -classpath "%CLASSPATH%" -Dweblogic.Name=%SERVER\_NAME% -Dweblogic.management.username=%WLS\_USER% -Dweblogic.ProductionModeEnabled=%PRODUCTION\_MODE% -Djava.security.policy="%WL_HOME%serverlibweblogic.policy" weblogic.Server"
> 
> :installSvc   
> rem \*** Set up extrapath for win32 and win64 platform separately   
> if not "%WL\_USE\_64BITDLL%" == "true" set EXTRAPATH=%WL\_HOME%serverbin;%JAVA\_HOME%jrebin;%JAVA\_HOME%bin;%WL\_HO
  
> ME%serverbinoci920_8
> 
> if "%WL\_USE\_64BITDLL%" == "true" set EXTRAPATH=%WL\_HOME%serverbinwin64;%WL\_HOME%serverbin;%JAVA\_HOME%jrebin;%JAVA\_HOME%bin;%WL\_HOME%serverbinwin64oci920\_8
> 
> rem \*** Install the service   
> "%WL\_HOME%serverbinbeasvc" -install -svcname:"beasvc %DOMAIN\_NAME%\_%SERVER\_NAME%" -javahome:"%JAVA\_HOME%" -execdir:"%USERDOMAIN\_HOME%" -extrapath:"%EXTRAPATH%" -password:"%WLS_PW%" -cmdline:%CMDLINE%
> 
> :finish   
> ENDLOCAL

2、执行该脚本后，在windows服务里可以看到

[<img title="截图02" height="213" alt="截图02" src="http://www.tonyxu.net/wp-content/uploads/2010/11/02_thumb1.png" width="639" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/11/021.png)

3、beasvc mydomain_myserver即为注册好的myserver服务，随后重启操作系统，weblogic服务也启动成功。

4、这里有一个问题，当weblogic服务注册成功后，修改JAVA堆大小后，重启windows，发现堆大小仍为修改之前的值。经过试验后，发现需要先取消掉服务，然后重新注册方能生效。

取消服务的命令:

[<img title="截图01" height="152" alt="截图01" src="http://www.tonyxu.net/wp-content/uploads/2010/11/01_thumb1.png" width="678" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/11/011.png)

这里我把-Xms和-Xmx均从384m修改为256m.

重新注册服务后，堆大小修改成功

修改前：

[<img title="截图00" height="216" alt="截图00" src="http://www.tonyxu.net/wp-content/uploads/2010/11/00_thumb.png" width="657" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/11/00.png)

修改后：

[<img title="截图03" height="230" alt="截图03" src="http://www.tonyxu.net/wp-content/uploads/2010/11/03_thumb.png" width="677" border="0" />](http://www.tonyxu.net/wp-content/uploads/2010/11/03.png)

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [weblogic注册为windows服务[转]](http://www.beansoft.biz/2010/11/26/weblogic%e6%b3%a8%e5%86%8c%e4%b8%bawindows%e6%9c%8d%e5%8a%a1%e8%bd%ac/)