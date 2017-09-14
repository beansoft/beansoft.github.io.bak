---
id: 1050
title: 'MyEclipse 6 Java 开发中文教程独家连载 &#8211; 第六章 管理应用服务器'
date: 2010-09-09T20:46:47+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1050
permalink: '/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e7%ac%ac%e5%85%ad%e7%ab%a0-%e7%ae%a1%e7%90%86%e5%ba%94%e7%94%a8%e6%9c%8d%e5%8a%a1/'
views:
  - "6114"
original_post_id:
  - "1050"
image: /wp-content/uploads/2012/09/clip_image002_thumb41.jpg
categories:
  - MyEclipse6中文教程
---
<p class="MsoNormal" style="margin-left:5.25pt;text-indent:15.75pt;">
  <span class="Apple-style-span" style="word-spacing:0;font:medium 微软雅黑;text-transform:none;color:#000000;text-indent:0;white-space:normal;letter-spacing:normal;border-collapse:separate;orphans:2;widows:2;"><span class="Apple-style-span" style="font-size:12px;color:#444444;line-height:18px;font-family:&#039;text-align:justify;"><strong><span style="color:#ff0000;">如果您需要转载本书内容, 请与本站联系! Email:<span class="Apple-converted-space"> </span></span></strong><strong><span style="color:#ff0000;">wlsmon@qq.com</span></strong><strong><span style="color:#ff0000;">.</span></strong></span></span>
</p>

<p class="MsoNormal">
  <span lang="EN-US"> </span>
</p>

## <a name="_Toc201479634"><span lang="EN-US">6.1</span></a><span><span style="font-family:宋体;">简介</span></span><span lang="EN-US"></p> 

<p>
  </span></h2> 
  
  <p class="MsoNormal">
    <span lang="EN-US"><span> </span>MyEclipse</span><span style="font-family:宋体;">支持对多达</span><span lang="EN-US">20</span><span style="font-family:宋体;">种应用服务器（</span><span lang="EN-US">Application Server</span><span style="font-family:宋体;">）的启动，停止，发布，重新发布，测试，调试，查看服务器输出信息等等。这些服务器包括：</span><span lang="EN-US">Glassfish</span><span style="font-family:宋体;">，</span><span lang="EN-US">JBoss</span><span style="font-family:宋体;">，</span><span lang="EN-US">Jetty</span><span style="font-family:宋体;">，</span><span lang="EN-US">Jonas</span><span style="font-family:宋体;">，</span><span lang="EN-US">JRun</span><span style="font-family:宋体;">，</span><span lang="EN-US">Oracle</span><span style="font-family:宋体;">，</span><span lang="EN-US">Orion</span><span style="font-family:宋体;">，</span><span lang="EN-US">Resin</span><span style="font-family:宋体;">，</span><span lang="EN-US">Sun App Server</span><span style="font-family:宋体;">，</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">，</span><span lang="EN-US">BEA WebLogic Server</span><span style="font-family:宋体;">，</span><span lang="EN-US">IBM WebSphere</span><span style="font-family:宋体;">等等。</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">通过对每个服务器配置连接器（</span><span lang="EN-US">Connector</span><span style="font-family:宋体;">）来管理这些服务器。</span><span lang="EN-US"> </span>
  </p>
  
  <p class="MsoNormal">
    <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">不过，</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">只支持在本机安装的服务器的管理，不能对远程服务器进行管理。另外，这些服务器最好通过</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">来启动，<strong>尽量不要使用</strong></span><strong><span lang="EN-US">JRE</span></strong><span style="font-family:宋体;">。不过，在实践中发现</span><span lang="EN-US">Tomcat 5</span><span style="font-family:宋体;">，</span><span lang="EN-US">Tomcat 6</span><span style="font-family:宋体;">和</span><span lang="EN-US">JBoss 4.2 </span><span style="font-family:宋体;">是可以通过</span><span lang="EN-US">JRE</span><span style="font-family:宋体;">正常启动和运行的。</span><span lang="EN-US"> </span>
  </p>
  
  <p class="MsoNormal" style="text-indent:21pt;">
    <span style="font-family:宋体;">只有</span><span lang="EN-US"> MyEclipse Java EE </span><span style="font-family:宋体;">类型的项目</span><span lang="EN-US"> (Enterprise</span><span style="font-family:宋体;">，</span><span lang="EN-US">EJB</span><span style="font-family:宋体;">和</span><span lang="EN-US">WEB)</span><span style="font-family:宋体;">才能用</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">来进行发布。</span><span lang="EN-US"> </span>
  </p>
  
  <p class="MsoNormal">
    <span lang="EN-US"><span> </span>MyEclipse 6 </span><span style="font-family:宋体;">自带了一个</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">服务器，因此除了开发</span><span lang="EN-US">EJB</span><span style="font-family:宋体;">项目外，可以不用单独下载和安装</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">服务器。</span><span lang="EN-US"> </span>
  </p>
  
  <h2>
    <a name="_Toc201479635"></a><a name="servermgr"><span><span lang="EN-US">6.2 Servers </span></span></a><span><span><span style="font-family:宋体;">视图</span></span></span><span lang="EN-US"></p> 
    
    <p>
      </span></h2> 
      
      <p class="MsoNormal">
        <strong><span lang="EN-US">Servers</span></strong><span style="font-family:宋体;">是一个特殊的</span><span lang="EN-US"> MyEclipse </span><span style="font-family:宋体;">视图，可以查看全面所有配置的应用服务器连接器的状态。这个视图是</span><strong><span lang="EN-US">MyEclipse Java Enterprise</span></strong><span style="font-family:宋体;">透视图的一个标准部分（参考图</span><span lang="EN-US">6.1</span><span style="font-family:宋体;">）。</span><span lang="EN-US"> </span>
      </p>
      
      <p class="MsoNormal" style="margin-bottom:12pt;text-indent:21pt;">
        <span style="font-family:宋体;">从菜单栏选择</span><span style="font-family:&"> <strong><span style="font-family:&" lang="EN-US">Windows > Show View > Other</span></strong></span><strong><span style="font-weight:normal;font-family:宋体;">，在弹出的对话框中选择节点</span></strong><strong><span style="font-family:&" lang="EN-US">MyEclipse Java Enterprise > Servers</span></strong><span style="font-family:宋体;">，就可以打开</span><strong><span style="font-family:&" lang="EN-US">Servers</span></strong><span style="font-family:宋体;">视图。这个视图的工具栏按钮分成两大部分（见途中红线框中的部分），左边的一侧可以配置服务器，启动和关闭，右边的一侧则管理发布到选中的服务器上的</span><span style="font-family:&" lang="EN-US">J2EE</span><span style="font-family:宋体;">项目。表</span><span style="font-family:&" lang="EN-US">6.1</span><span style="font-family:宋体;">列出了每个工具栏按钮功能的简要描述。</span><span style="font-family:&" lang="EN-US"> </span>
      </p>
      
      <p class="MsoNormal" style="margin-bottom:12pt;text-indent:21pt;">
        <strong><span style="color:red;font-family:宋体;">注意：</span></strong><span style="font-family:宋体;">这个图中的</span><strong><span style="font-family:&" lang="EN-US">MyEclipse Derby</span></strong><span style="font-family:宋体;">是内置的数据库服务器，而</span><strong><span style="font-family:&" lang="EN-US">MyEclipse Tomcat</span></strong><span style="font-family:宋体;">则是内置的</span><span style="font-family:&" lang="EN-US">JSP</span><span style="font-family:宋体;">服务器。</span><span style="font-family:&" lang="EN-US"> </span>
      </p>
      
      <p class="MsoNormal" style="margin-bottom:12pt;text-align:center;">
        <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0024.jpg"><img style="display:inline;border:0;" title="clip_image002" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image002_thumb4.jpg" border="0" alt="clip_image002" width="553" height="132" /></a><br /> </span><span style="font-family:宋体;">图</span><span style="font-family:&" lang="EN-US">6.1 Servers</span><span style="font-family:宋体;">视图以及工具栏按钮</span><span style="font-family:&" lang="EN-US"> </span>
      </p>
      
      <table class="MsoTableTheme" style="border-collapse:collapse;border:medium none;" border="1" cellspacing="0" cellpadding="0">
        <tr>
          <td style="border:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image003.gif"><img style="display:inline;border:0;" title="clip_image003" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image003_thumb.gif" border="0" alt="clip_image003" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:windowtext 1pt solid;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">以运行模式启动所选应用服务器</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0041.gif"><img style="display:inline;border:0;" title="clip_image004" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image004_thumb.gif" border="0" alt="clip_image004" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">以调试模式启动所选应用服务器，支持热替换调试</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image005.gif"><img style="display:inline;border:0;" title="clip_image005" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image005_thumb.gif" border="0" alt="clip_image005" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">重启服务器（先停止，再启动）</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006.gif"><img style="display:inline;border:0;" title="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006_thumb.gif" border="0" alt="clip_image006" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">停止所选应用服务器</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image007.gif"><img style="display:inline;border:0;" title="clip_image007" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image007_thumb.gif" border="0" alt="clip_image007" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">配置所选应用服务器的连接器</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image008.gif"><img style="display:inline;border:0;" title="clip_image008" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image008_thumb.gif" border="0" alt="clip_image008" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">打开</span><span style="font-family:&" lang="EN-US">Deployment Manager</span><span style="font-family:宋体;">（发布管理器）</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image009.gif"><img style="display:inline;border:0;" title="clip_image009" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image009_thumb.gif" border="0" alt="clip_image009" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">删除已经发布的</span><span style="font-family:&" lang="EN-US">J2EE </span><span style="font-family:宋体;">项目</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image010.gif"><img style="display:inline;border:0;" title="clip_image010" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image010_thumb.gif" border="0" alt="clip_image010" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">重新发布选中的已发布过的</span><span style="font-family:&" lang="EN-US">J2EE </span><span style="font-family:宋体;">项目（做开发是比较有用）</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
        
        <tr>
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image011.gif"><img style="display:inline;border:0;" title="clip_image011" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image011_thumb.gif" border="0" alt="clip_image011" width="16" height="16" /></a> </span>
            </p>
          </td>
          
          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top">
            <p class="MsoNormal" style="margin:6pt 0;">
              <span style="font-family:宋体;">打开文件浏览器来浏览服务器的自动发布目录以及发布后的项目文件所在的位置</span><span style="font-family:&" lang="EN-US"> </span>
            </p>
          </td>
        </tr>
      </table>
      
      <p class="MsoNormal" style="text-align:center;">
        <span style="font-family:宋体;">表</span><span style="font-family:&" lang="EN-US">6.1 </span><span style="font-family:宋体;">服务器管理工具栏功能描述</span><span style="font-family:&" lang="EN-US"> </span>
      </p>
      
      <h2>
        <a name="_Toc201479636"><span lang="EN-US">6.3 </span></a><span><span style="font-family:宋体;">浏览应用服务器连接器</span></span><span lang="EN-US"></p> 
        
        <p>
          </span></h2> 
          
          <p class="MsoNormal">
            <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">想连接到自己用的应用服务器的话，可以点击</span><span lang="EN-US">Servers</span><span style="font-family:宋体;">视图的工具栏上的</span><span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0071.gif"><img style="display:inline;border:0;" title="clip_image007" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image007_thumb1.gif" border="0" alt="clip_image007" width="16" height="16" /></a></span><span style="font-family:宋体;">按钮来打开服务器配置对话框，或者从主菜单中选择</span><strong><span lang="EN-US">Window > Preferences</span></strong><span style="font-family:宋体;">，这样就可以打开配置对话框。</span><span lang="EN-US"> </span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">当配置对话框打开后，可以展开左侧的树，选择</span><strong><span lang="EN-US">MyEclipse > Servers</span></strong><span style="font-family:宋体;">，然后就可以看到可用的应用服务器连接器了。如下图所示：</span><span lang="EN-US"> </span>
          </p>
          
          <p class="MsoNormal" style="text-align:center;">
            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0131.jpg"><img style="display:inline;border:0;" title="clip_image013" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image013_thumb1.jpg" border="0" alt="clip_image013" width="553" height="500" /></a> </span>
          </p>
          
          <p class="MsoNormal" style="text-align:center;">
            <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.2 </span><span style="font-family:宋体;">查看服务器连接器列表</span><span lang="EN-US"> </span>
          </p>
          
          <p class="MsoNormal">
            <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">下图则展示了一个配置好的</span><span lang="EN-US">JBoss</span><span style="font-family:宋体;">服务器的例子：</span><span lang="EN-US"> </span>
          </p>
          
          <p class="MsoNormal" style="text-align:center;">
            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0151.jpg"><img style="display:inline;border:0;" title="clip_image015" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image015_thumb1.jpg" border="0" alt="clip_image015" width="553" height="180" /></a> </span>
          </p>
          
          <p class="MsoNormal" style="text-align:center;">
            <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.3 JBoss 4 </span><span style="font-family:宋体;">的配置</span><span lang="EN-US"> </span>
          </p>
          
          <p class="MsoNormal">
            <span style="font-family:宋体;">除了服务器的安装目录外，还可以设置一些额外的信息和启动参数等等。</span><span lang="EN-US"> </span>
          </p>
          
          <h2>
            <a name="_Toc201479637"><span lang="EN-US">6.4 </span></a><span><span style="font-family:宋体;">配置连接器</span></span><span lang="EN-US"></p> 
            
            <p>
              </span></h2> 
              
              <p class="MsoNormal">
                <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">配置一个服务器基本上来说需要</span><span lang="EN-US">2</span><span style="font-family:宋体;">到</span><span lang="EN-US">3</span><span style="font-family:宋体;">步，包括：</span><span lang="EN-US"> </span>
              </p>
              
              <p class="MsoNormal" style="margin-left:21pt;text-indent:-21pt;">
                <span lang="EN-US"><span>1.<span style="font:7pt &"> </span></span></span><span style="font-family:宋体;">配置服务器的安装信息；</span><span lang="EN-US"> </span>
              </p>
              
              <p class="MsoNormal" style="margin-left:21pt;text-indent:-21pt;">
                <span lang="EN-US"><span>2.<span style="font:7pt &"> </span></span></span><span style="font-family:宋体;">启用连接器；</span><span lang="EN-US"> </span>
              </p>
              
              <p class="MsoNormal" style="margin-left:21pt;text-indent:-21pt;">
                <span lang="EN-US"><span>3.<span style="font:7pt &"> </span></span></span><span style="font-family:宋体;">指定启动时需要的</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">或者</span><span lang="EN-US">JRE</span><span style="font-family:宋体;">（可选）。</span><span lang="EN-US"> </span>
              </p>
              
              <p class="MsoNormal" style="text-indent:21pt;">
                <strong><span style="color:red;font-family:宋体;">注意：</span></strong><span style="font-family:宋体;">一些特殊的服务器需要额外的配置信息，这时候你可以去查看对应服务器的使用说明书和帮助文档以及从技术支持人员那里获得帮助（可能会付费）。</span><span lang="EN-US"> </span>
              </p>
              
              <p class="MsoNormal" style="text-indent:21pt;">
                <span style="font-family:宋体;">下面就以配置常用的</span><span lang="EN-US">Tomcat 5</span><span style="font-family:宋体;">为例来介绍如何配置连接器。</span><span lang="EN-US"> </span>
              </p>
              
              <h3>
                <a name="_Toc201479638"></a><span><span lang="EN-US">6.4.1</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">第</span><span lang="EN-US">1</span></span><span><span style="font-family:宋体;">步</span> </span><span><span style="font-family:宋体;">配置服务器的安装信息</span></span><span lang="EN-US"></p> 
                
                <p>
                  </span></h3> 
                  
                  <p class="MsoNormal">
                    <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">首先我们选中服务器节点</span><strong><span lang="EN-US">Tomcat 5.x</span></strong><span style="font-family:宋体;">，然后点击</span><strong><span lang="EN-US">Browse&#8230;</span></strong><span style="font-family:宋体;">按钮来选择</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">的安装根目录，如图</span><span lang="EN-US">6.4</span><span style="font-family:宋体;">所示。接下来</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">会尝试根据服务器的默认设置填入其它的设置信息，如图</span><span lang="EN-US">6.5</span><span style="font-family:宋体;">所示。在这个例子中选择的安装目录是</span><em><span lang="EN-US">E:apache-tomcat-5.5.20-cn</span></em><span style="font-family:宋体;">。</span><span lang="EN-US"> </span>
                  </p>
                  
                  <p class="MsoNormal">
                    <span lang="EN-US"><span> </span><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0171.jpg"><img style="display:inline;border:0;" title="clip_image017" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image017_thumb1.jpg" border="0" alt="clip_image017" width="553" height="140" /></a> </span>
                  </p>
                  
                  <p class="MsoNormal" style="text-align:center;">
                    <span style="font-family:宋体;">图</span><span lang="EN-US">6.4 </span><span style="font-family:宋体;">选择</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">的安装目录</span><span lang="EN-US"> </span>
                  </p>
                  
                  <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                    <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0192.jpg"><img style="display:inline;border:0;" title="clip_image019" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image019_thumb2.jpg" border="0" alt="clip_image019" width="505" height="171" /></a> </span>
                  </p>
                  
                  <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                    <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.5 </span><span style="font-family:宋体;">默认的</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">设置信息</span><span lang="EN-US"> </span>
                  </p>
                  
                  <h3>
                    <a name="_Toc201479639"></a><span><span lang="EN-US">6.4.2</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">第</span><span lang="EN-US">2</span></span><span><span style="font-family:宋体;">步</span> </span><span><span style="font-family:宋体;">启用连接器</span></span><span lang="EN-US"></p> 
                    
                    <p>
                      </span></h3> 
                      
                      <p class="MsoNormal" style="text-indent:21pt;">
                        <span style="font-family:宋体;">要想使用这个服务器，必须启用连接器，之后你才能在</span><strong><span lang="EN-US">Servers</span></strong><span style="font-family:宋体;">视图中看到它并对它进行管理。如图</span><span lang="EN-US">6.6</span><span style="font-family:宋体;">所示。到这一步可以点击</span><strong><span lang="EN-US">OK</span></strong><span style="font-family:宋体;">按钮就可以完成配置了。</span><span lang="EN-US"> </span>
                      </p>
                      
                      <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                        <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0211.jpg"><img style="display:inline;border:0;" title="clip_image021" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image021_thumb1.jpg" border="0" alt="clip_image021" width="504" height="72" /></a> </span>
                      </p>
                      
                      <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                        <span style="font-family:宋体;">图</span><span lang="EN-US">6.6 </span><span style="font-family:宋体;">启用</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">连接器</span><span lang="EN-US"> </span>
                      </p>
                      
                      <h3>
                        <a name="_Toc201479640"></a><span><span lang="EN-US">6.4.3</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">第</span><span lang="EN-US">3</span></span><span><span style="font-family:宋体;">步</span> </span><span><span style="font-family:宋体;">选择启动服务器时候所用的</span><span lang="EN-US">JDK</span></span><span lang="EN-US"></p> 
                        
                        <p>
                          </span></h3> 
                          
                          <p class="MsoNormal">
                            <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">最后一步可选的操作是为服务器指定合适版本的</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">，对于</span><span lang="EN-US">Tomcat 5</span><span style="font-family:宋体;">，</span><span lang="EN-US">Tomcat 6</span><span style="font-family:宋体;">和</span><span lang="EN-US">JBoss 4</span><span style="font-family:宋体;">来说，默认的</span><span lang="EN-US">JRE</span><span style="font-family:宋体;">（一般是</span><span lang="EN-US">1.5</span><span style="font-family:宋体;">版本或者更高，例如</span><span lang="EN-US">MyEclipse6.0</span><span style="font-family:宋体;">）就可以了，不需要</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">。然而对于一些低版本的服务器，例如</span><span lang="EN-US">Tomcat 4</span><span style="font-family:宋体;">，则只能选择</span><span lang="EN-US">JDK 1.4</span><span style="font-family:宋体;">（不能用</span><span lang="EN-US">JRE 1.4</span><span style="font-family:宋体;">），这时候就必须指定</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">。而</span><span lang="EN-US">Tomcat 5</span><span style="font-family:宋体;">则必须是</span><span lang="EN-US">JDK 5</span><span style="font-family:宋体;">或者更高版本。点击左侧的</span><strong><span lang="EN-US">JDK</span></strong><span style="font-family:宋体;">节点，然后选择右侧的</span><strong><span lang="EN-US">Tomcat JDK name</span></strong><span style="font-family:宋体;">下方的</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">列表下拉框，可以选中对应版本的</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">。如下图所示：</span><span lang="EN-US"> </span>
                          </p>
                          
                          <p class="MsoNormal" style="text-align:center;">
                            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0231.jpg"><img style="display:inline;border:0;" title="clip_image023" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image023_thumb1.jpg" border="0" alt="clip_image023" width="554" height="85" /></a> </span>
                          </p>
                          
                          <p class="MsoNormal" style="text-align:center;">
                            <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.7 Tomcat JDK </span><span style="font-family:宋体;">设置页面</span><span lang="EN-US"> </span>
                          </p>
                          
                          <p class="MsoNormal">
                            <span style="font-family:宋体;">最后点击</span><strong><span lang="EN-US">OK</span></strong><span style="font-family:宋体;">按钮就可以完成配置了。</span><span lang="EN-US"> </span>
                          </p>
                          
                          <h4>
                            <a name="_Toc201479641"></a><span><span lang="EN-US">6.4.3</span></span><span><span lang="EN-US">.1 </span></span><span><span style="font-family:宋体;">可选操作：添加</span><span lang="EN-US"> JVM</span></span><span lang="EN-US"></p> 
                            
                            <p>
                              </span></h4> 
                              
                              <p class="MsoNormal">
                                <span style="font-family:宋体;">如果您要使用的</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">版本在列表里没有出现，请点击</span><strong><span lang="EN-US">Add&#8230;</span></strong><span style="font-family:宋体;">按钮来启动</span><strong><span lang="EN-US">Add JVM</span></strong><span style="font-family:宋体;">对话框，如图</span><span lang="EN-US"> 6.8 </span><span style="font-family:宋体;">所示：</span><span lang="EN-US"> </span>
                              </p>
                              
                              <p class="MsoNormal" style="text-align:center;">
                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0251.jpg"><img style="display:inline;border:0;" title="clip_image025" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image025_thumb1.jpg" border="0" alt="clip_image025" width="500" height="378" /></a> </span>
                              </p>
                              
                              <p class="MsoNormal" style="text-align:center;">
                                <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.8 Add JVM </span><span style="font-family:宋体;">对话框</span><span lang="EN-US"> </span>
                              </p>
                              
                              <p class="MsoNormal">
                                <span style="font-family:宋体;">在这个对话框里面点击</span><strong><span lang="EN-US">Browse&#8230;</span></strong><span style="font-family:宋体;">按钮，然后在目录选择对话框中选中</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">安装目录的根目录，例如</span><em><span lang="EN-US">c:jdk1.5</span></em><span style="font-family:宋体;">，而不是选中其中的</span><span lang="EN-US">JRE</span><span style="font-family:宋体;">子目录，例如</span><em><span lang="EN-US">c:jdk1.5jre</span></em><span style="font-family:宋体;">，之后点击目录选择对话框的<strong>确定</strong>按钮返回</span><strong><span lang="EN-US">Add JVM</span></strong><span style="font-family:宋体;">对话框，这时候</span><strong><span lang="EN-US">JRE name</span></strong><span style="font-family:宋体;">输入框会自动输入一个名称，你也可以手工输入一个新名称。最后点击</span><strong><span lang="EN-US">OK</span></strong><span style="font-family:宋体;">按钮就完成了</span><span lang="EN-US">JVM</span><span style="font-family:宋体;">的添加工作，接下来你就可以在</span><span lang="EN-US">Tomcat JDK </span><span style="font-family:宋体;">配置页面选中这个新加入的</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">了。</span><span lang="EN-US"> </span>
                              </p>
                              
                              <h2>
                                <a name="_Toc201479642"><span lang="EN-US">6.5 </span></a><span><span style="font-family:宋体;">发布并运行</span><span lang="EN-US">Java EE</span></span><span><span style="font-family:宋体;">项目</span></span><span lang="EN-US"></p> 
                                
                                <p>
                                  </span></h2> 
                                  
                                  <h3>
                                    <a name="_Toc201479643"></a><span><span lang="EN-US">6.5.1</span></span><span><span lang="EN-US"> Java EE </span></span><span><span style="font-family:宋体;">项目的发布类型</span></span><span lang="EN-US"></p> 
                                    
                                    <p>
                                      </span></h3> 
                                      
                                      <p class="MsoNormal" style="text-indent:21pt;">
                                        <span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">支持发布</span><span lang="EN-US">Web, EJB</span><span style="font-family:宋体;">和</span><span lang="EN-US"> Enterprise Application</span><span style="font-family:宋体;">项目到任何</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">支持的服务器上。它支持散包和打包发布。请找服务器的顾问或者文档来了解是否支持散包发布。目前来说</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">和</span><span lang="EN-US">JBoss</span><span style="font-family:宋体;">都是支持散包发布的。</span><span lang="EN-US"> </span>
                                      </p>
                                      
                                      <h4>
                                        <a name="_Toc201479644"></a><span><span lang="EN-US">6.5.1</span></span><span><span lang="EN-US">.1 </span></span><span><span style="font-family:宋体;">散包发布</span></span><span lang="EN-US"></p> 
                                        
                                        <p>
                                          </span></h4> 
                                          
                                          <p class="MsoNormal">
                                            <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">散包发布一般是开发时候来使用，</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">会把所有的文件按照</span><span lang="EN-US">Java EE</span><span style="font-family:宋体;">规定的目录结构放在服务器的发布目录下。在这种情况下，</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">还会自动把修改过的文件，例如</span><span lang="EN-US">JSP</span><span style="font-family:宋体;">文件，类文件等等复制过去，实现自动同步功能，这时修改了</span><span lang="EN-US">JSP</span><span style="font-family:宋体;">页面不需要重新发布就能在浏览器里刷新后看到新的结果。这样对开发来说是非常方便的。但是需要指出的是：<strong>并非所有服务器都支持散包发布，散包发布也不是</strong></span><strong><span lang="EN-US">Java EE</span></strong><strong><span style="font-family:宋体;">规范所规定的内容，</span><span lang="EN-US">Java EE</span></strong><strong><span style="font-family:宋体;">规范只要求所有服务器都必须支持打包发布方式。</span><span lang="EN-US"> </span></strong>
                                          </p>
                                          
                                          <p>
                                            <strong> </strong>
                                          </p>
                                          
                                          <p>
                                            <strong> </strong>
                                          </p>
                                          
                                          <h4>
                                            <a name="_Toc201479645"></a><span><span lang="EN-US">6.5.1</span></span><span><span lang="EN-US">.2 </span></span><span><span style="font-family:宋体;">打包发布</span></span><span lang="EN-US"></p> 
                                            
                                            <p>
                                              </span></h4> 
                                              
                                              <p class="MsoNormal">
                                                <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">这种模式一般是用在生产机上的，也就是打算正式上线并把应用产品化的时候选择的。它会把所有的文件按</span><span lang="EN-US">Java EE </span><span style="font-family:宋体;">规范打包成单个的</span><span lang="EN-US">ZIP</span><span style="font-family:宋体;">文件（后缀可能是</span><span lang="EN-US">.EAR</span><span style="font-family:宋体;">，</span><span lang="EN-US">.JAR</span><span style="font-family:宋体;">，</span><span lang="EN-US">.WAR</span><span style="font-family:宋体;">等等），然后放到服务器的发布目录下完成发布过程。这种模式下的缺点就是</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">不会自动更新</span><span lang="EN-US">ZIP</span><span style="font-family:宋体;">文件里面的内容，也无法自动重新发布。</span><span lang="EN-US"> </span>
                                              </p>
                                              
                                              <h3>
                                                <a name="_Toc201479646"></a><a name="_6.5.2向服务器发布应用"></a><span><span lang="EN-US">6.5.2</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">向服务器发布应用</span></span><span lang="EN-US"></p> 
                                                
                                                <p>
                                                  </span></h3> 
                                                  
                                                  <p class="MsoNormal">
                                                    <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">在</span><span lang="EN-US">MyEclipse 6</span><span style="font-family:宋体;">中，向服务器发布应用的最快最方便的办法是在</span><strong><span lang="EN-US">Package Explorer</span></strong><span style="font-family:宋体;">视图中选中项目节点，接着选择菜单</span><strong><span lang="EN-US">Run > Run As > 3 MyEclipse Server Application</span></strong><span style="font-family:宋体;">，之后</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">可能会显示一个可用的服务器列表，选中其中的服务器之一例如</span><em><span lang="EN-US">MyEclipse Tomcat</span></em><span style="font-family:宋体;">并点击</span><strong><span lang="EN-US">OK</span></strong><span style="font-family:宋体;">按钮后，就会自动发布或者重新发布应用然后启动服务器。如果选中的是</span><strong><span lang="EN-US">MyEclipse Tomcat</span></strong><span style="font-family:宋体;">这个服务器，甚至可以自动打开一个</span><strong><span lang="EN-US">MyEclipse Web Browser</span></strong><span style="font-family:宋体;">视图，并在这个内置浏览器中打开</span><span lang="EN-US">Web</span><span style="font-family:宋体;">项目的首页面。这个方法是比较方便快捷的过程。</span><span lang="EN-US"> </span>
                                                  </p>
                                                  
                                                  <p class="MsoNormal">
                                                    <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">传统的发布方式，步骤比较多，可以参考下面的说明来进行。</span><span lang="EN-US"> </span>
                                                  </p>
                                                  
                                                  <h4>
                                                    <a name="_Toc201479647"></a><span><span lang="EN-US">6.5.2</span></span><span><span lang="EN-US">.1 </span></span><span><span style="font-family:宋体;">打开发布对话框</span></span><span lang="EN-US"></p> 
                                                    
                                                    <p>
                                                      </span></h4> 
                                                      
                                                      <p class="MsoNormal" style="text-indent:21pt;">
                                                        <span style="font-family:宋体;">点击主界面工具栏上的</span><span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0081.gif"><img style="display:inline;border:0;" title="clip_image008" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image008_thumb1.gif" border="0" alt="clip_image008" width="16" height="16" /></a></span><span style="font-family:宋体;">按钮，就可以打开</span><strong><span style="font-family:&" lang="EN-US">Project Deployments</span></strong><span style="font-family:宋体;">对话框，如下图所示：</span><span style="font-family:&" lang="EN-US"> </span>
                                                      </p>
                                                      
                                                      <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                                                        <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0271.jpg"><img style="display:inline;border:0;" title="clip_image027" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image027_thumb1.jpg" border="0" alt="clip_image027" width="464" height="392" /></a> </span>
                                                      </p>
                                                      
                                                      <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                                                        <span style="font-family:宋体;">图</span><span style="font-family:&" lang="EN-US">6.9 </span><span style="font-family:宋体;">项目发布向导对话框</span><span style="font-family:&" lang="EN-US"> </span>
                                                      </p>
                                                      
                                                      <p class="MsoNormal" style="text-indent:21pt;">
                                                        <span style="font-family:宋体;">如果点击的是</span><span style="font-family:宋体;">或者</span><span style="font-family:&" lang="EN-US">Servers</span><span style="font-family:宋体;">视图工具栏的</span><span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0082.gif"><img style="display:inline;border:0;" title="clip_image008" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image008_thumb2.gif" border="0" alt="clip_image008" width="16" height="16" /></a></span><span style="font-family:宋体;">按钮，则会打开</span><span style="font-family:&" lang="EN-US">Servers Deployments</span><span style="font-family:宋体;">对话框，显示的内容略有不同而已，如下图所示：</span><span style="font-family:&" lang="EN-US"> </span>
                                                      </p>
                                                      
                                                      <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                                                        <span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0291.jpg"><img style="display:inline;border:0;" title="clip_image029" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image029_thumb1.jpg" border="0" alt="clip_image029" width="460" height="388" /></a> </span>
                                                      </p>
                                                      
                                                      <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                                                        <span style="font-family:宋体;">图</span><span style="font-family:&" lang="EN-US">6.10 </span><span style="font-family:宋体;">服务器发布向导对话框</span><span style="font-family:&" lang="EN-US"> </span>
                                                      </p>
                                                      
                                                      <h4>
                                                        <a name="_Toc201479648"></a><span><span lang="EN-US">6.5.2</span></span><span><span lang="EN-US">.2</span></span><span><span style="font-family:宋体;">点击</span><span lang="EN-US">Add</span></span><span><span style="font-family:宋体;">按钮启动新建发布对话框并完成发布</span></span><span lang="EN-US"></p> 
                                                        
                                                        <p>
                                                          </span></h4> 
                                                          
                                                          <p class="MsoNormal" style="text-indent:21pt;">
                                                            <span style="font-family:&" lang="EN-US"><span> </span></span><span style="font-family:宋体;">当点击图</span><span style="font-family:&" lang="EN-US">6.9</span><span style="font-family:宋体;">中的</span><strong><span style="font-family:&" lang="EN-US">Add</span></strong><span style="font-family:宋体;">按钮后，可以启动</span><strong><span style="font-family:&" lang="EN-US">New Deployment </span></strong><span style="font-family:宋体;">向导，如下图所示：</span><span style="font-family:&" lang="EN-US"> </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                                                            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0311.jpg"><img style="display:inline;border:0;" title="clip_image031" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image031_thumb1.jpg" border="0" alt="clip_image031" width="553" height="308" /></a> </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal" style="text-indent:21pt;text-align:center;">
                                                            <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.11 </span><span style="font-family:宋体;">新建发布对话框</span><span lang="EN-US"> </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal">
                                                            <span style="font-family:宋体;">在这一步我们可以指定将项目发布到的服务器，以及发布的类型。点击</span><strong><span lang="EN-US">Server</span></strong><span style="font-family:宋体;">右侧的下拉框选择对应的服务器定义，选择</span><strong><span lang="EN-US">Deploy type</span></strong><span style="font-family:宋体;">中的两个单选钮之一来指定发布类型（左侧的为散包发布，开发模式；右侧的为打包发布，生产机模式），而</span><strong><span lang="EN-US">Deploy Location</span></strong><span style="font-family:宋体;">则显示了最终项目文件被发布到的目标目录。点击</span><strong><span lang="EN-US">Finish</span></strong><span style="font-family:宋体;">按钮就可以显示发布的进程并等待最终完成发布过程。发布结束后会在</span><strong><span style="font-family:&" lang="EN-US">Project Deployments</span></strong><span style="font-family:宋体;">对话框里面显示此次发布的结果和状态，如下图所示：</span><span style="font-family:&" lang="EN-US"> </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal" style="text-align:center;">
                                                            <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0331.jpg"><img style="display:inline;border:0;" title="clip_image033" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image033_thumb1.jpg" border="0" alt="clip_image033" width="506" height="193" /></a> </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal" style="text-align:center;">
                                                            <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.12 </span><span style="font-family:宋体;">发布结果对话框</span><span lang="EN-US"> </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal">
                                                            <span style="font-family:宋体;">如果是通过图</span><span lang="EN-US">6.10</span><span style="font-family:宋体;">开始的发布过程，点击</span><strong><span lang="EN-US">Add</span></strong><span style="font-family:宋体;">按钮后只是对话框中选项的位置略有不同，其它概念和操作都是相似的。点击</span><strong><span lang="EN-US">Remove</span></strong><span style="font-family:宋体;">按钮会删除这个发布，点击</span><strong><span lang="EN-US">Redeploy</span></strong><span style="font-family:宋体;">按钮则会重新发布这个应用，点击</span><strong><span lang="EN-US">Browse</span></strong><span style="font-family:宋体;">按钮则会在系统的文件浏览器中打开发布后的应用所在的目录。</span><span lang="EN-US"> </span>
                                                          </p>
                                                          
                                                          <h2>
                                                            <a name="_Toc201479649"><span lang="EN-US">6.6 </span></a><span><span style="font-family:宋体;">应用服务器的管理和调试</span></span><span lang="EN-US"></p> 
                                                            
                                                            <p>
                                                              </span></h2> 
                                                              
                                                              <h3>
                                                                <a name="_Toc201479650"></a><a name="_启动服务器"></a><a name="_6.6.1启动服务器"></a><span><span lang="EN-US">6.6.1</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">启动服务器</span></span><span lang="EN-US"></p> 
                                                                
                                                                <p>
                                                                  </span></h3> 
                                                                  
                                                                  <p class="MsoNormal">
                                                                    <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">要运行服务器有两种办法，一种是在</span><span lang="EN-US">Servers</span><span style="font-family:宋体;">视图中选中服务器，之后点击视图工具栏上的</span><span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0031.gif"><img style="display:inline;border:0;" title="clip_image003" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image003_thumb1.gif" border="0" alt="clip_image003" width="16" height="16" /></a></span><span style="font-family:宋体;">按钮以运行模式启动服务器，或者点击</span><span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image034.gif"><img style="display:inline;border:0;" title="clip_image034" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image034_thumb.gif" border="0" alt="clip_image034" width="16" height="16" /></a></span><span style="font-family:宋体;">按钮以调试模式启动服务器。或者点击主界面工具栏上的</span><strong><span style="font-family:&" lang="EN-US">Run/Stop/Restart MyEclipse Servers</span></strong><span style="font-family:宋体;">按钮来启动服务器，如下图所示：</span><span style="font-family:&" lang="EN-US"> </span>
                                                                  </p>
                                                                  
                                                                  <p class="MsoNormal" style="text-align:center;">
                                                                    <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0364.jpg"><img style="display:inline;border:0;" title="clip_image036" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image036_thumb4.jpg" border="0" alt="clip_image036" width="285" height="184" /></a> </span>
                                                                  </p>
                                                                  
                                                                  <p class="MsoNormal" style="text-align:center;">
                                                                    <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.13 </span><span style="font-family:宋体;">工具栏上的启动服务器按钮</span><span lang="EN-US"> </span>
                                                                  </p>
                                                                  
                                                                  <p class="MsoNormal">
                                                                    <span style="font-family:宋体;">。这样就可以启动所选择的服务器了。</span><span lang="EN-US"> </span>
                                                                  </p>
                                                                  
                                                                  <h3>
                                                                    <a name="_Toc201479651"></a><span><span lang="EN-US">6.6.2</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">监控服务器启动过程</span></span><span lang="EN-US"></p> 
                                                                    
                                                                    <p>
                                                                      </span></h3> 
                                                                      
                                                                      <p class="MsoNormal">
                                                                        <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">服务器启动之后，输出的日志就会显示在</span><span lang="EN-US">Console</span><span style="font-family:宋体;">视图中，便于我们浏览和跟踪查看日志来判断服务器是否正常启动完毕。例如下图显示了正常的</span><span lang="EN-US">Tomcat</span><span style="font-family:宋体;">启动完毕后的输出日志：</span><span lang="EN-US"> </span>
                                                                      </p>
                                                                      
                                                                      <p class="MsoNormal" style="text-align:center;">
                                                                        <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0382.jpg"><img style="display:inline;border:0;" title="clip_image038" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image038_thumb2.jpg" border="0" alt="clip_image038" width="540" height="154" /></a> </span>
                                                                      </p>
                                                                      
                                                                      <p class="MsoNormal" style="text-align:center;">
                                                                        <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.14 Tomcat</span><span style="font-family:宋体;">服务器启动成功的日志输出</span><span lang="EN-US"> </span>
                                                                      </p>
                                                                      
                                                                      <h3>
                                                                        <a name="_Toc201479652"></a><span><span lang="EN-US">6.6.3</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">停止服务器</span></span><span lang="EN-US"></p> 
                                                                        
                                                                        <p>
                                                                          </span></h3> 
                                                                          
                                                                          <p class="MsoNormal">
                                                                            <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">可以点击</span><strong><span lang="EN-US">Console</span></strong><span style="font-family:宋体;">视图工具栏上的</span><span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0061.gif"><img style="display:inline;border:0;" title="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006_thumb1.gif" border="0" alt="clip_image006" width="16" height="16" /></a></span><span style="font-family:宋体;">来强制终止服务器进程，或者可以通过</span><strong><span style="font-family:&" lang="EN-US">Servers</span></strong><span style="font-family:宋体;">视图上的</span><span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0062.gif"><img style="display:inline;border:0;" title="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006_thumb2.gif" border="0" alt="clip_image006" width="16" height="16" /></a></span><span style="font-family:宋体;">按钮来正常停止服务器，也可以通过图</span><span style="font-family:&" lang="EN-US">6.13</span><span style="font-family:宋体;">上的</span><span style="font-family:&" lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0063.gif"><img style="display:inline;border:0;" title="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006_thumb3.gif" border="0" alt="clip_image006" width="16" height="16" /></a>Stop</span><span style="font-family:宋体;">菜单项来停止服务器。服务器关闭过程中的日志也会显示在</span><strong><span style="font-family:&" lang="EN-US">Console</span></strong><span style="font-family:宋体;">视图中。</span><span lang="EN-US"> </span>
                                                                          </p>
                                                                          
                                                                          <h3>
                                                                            <a name="_Toc201479653"></a><a name="_6.6.4调试发布的企业应用"></a><span><span lang="EN-US">6.6.4</span></span><span><span lang="EN-US"> </span></span><span><span style="font-family:宋体;">调试发布的企业应用</span></span><span lang="EN-US"></p> 
                                                                            
                                                                            <p>
                                                                              </span></h3> 
                                                                              
                                                                              <p class="MsoNormal">
                                                                                <span lang="EN-US"><span> </span>MyEclipse</span><span style="font-family:宋体;">扩展了</span><span lang="EN-US">Eclipse</span><span style="font-family:宋体;">的调试器，这样它可以在</span><span lang="EN-US">JSP</span><span style="font-family:宋体;">中设置断点和进行调试，也可以对</span><span lang="EN-US">EJB</span><span style="font-family:宋体;">进行调试。可以像在</span><span lang="EN-US"><a href="#_断点和调试器"><span style="font-family:宋体;" lang="EN-US"><span lang="EN-US">断点和调试器</span></span></a></span><span style="font-family:宋体;">一节所介绍的那样来对</span><span lang="EN-US">JSP</span><span style="font-family:宋体;">或者</span><span lang="EN-US">Servlet</span><span style="font-family:宋体;">设置调试信息。<strong><span style="color:red;">注意：</span></strong>服务器一定要以调试模式启动，参考</span><span lang="EN-US"><a href="#_启动服务器"><span style="font-family:宋体;" lang="EN-US"><span lang="EN-US">启动服务器</span></span></a></span><span style="font-family:宋体;">一节的内容。其它的操作和普通的调试都是一样的，可以进行单步执行等操作。这样对开发时解决问题来说是非常的方便快捷的，当然另一种更好的办法实在代码里面用</span><span lang="EN-US">System.out.println(“</span><span style="font-family:宋体;">调试信息</span><span lang="EN-US">”)</span><span style="font-family:宋体;">来输出调试代码。</span><span lang="EN-US"> </span>
                                                                              </p>
                                                                              
                                                                              <p class="MsoNormal" style="text-align:center;">
                                                                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0401.jpg"><img style="display:inline;border:0;" title="clip_image040" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image040_thumb1.jpg" border="0" alt="clip_image040" width="553" height="388" /></a> </span>
                                                                              </p>
                                                                              
                                                                              <p class="MsoNormal" style="text-align:center;">
                                                                                <span style="font-family:宋体;">图</span><span lang="EN-US"> 6.15 </span><span style="font-family:宋体;">对</span><span lang="EN-US">JSP</span><span style="font-family:宋体;">进行调试</span><span lang="EN-US"> </span>
                                                                              </p>
                                                                              
                                                                              <h2>
                                                                                <a name="_Toc201479654"><span lang="EN-US">6.7</span></a><span><span style="font-family:宋体;">小结</span></span><span lang="EN-US"></p> 
                                                                                
                                                                                <p>
                                                                                  </span></h2> 
                                                                                  
                                                                                  <p class="MsoNormal">
                                                                                    <span lang="EN-US"><span> </span></span><span style="font-family:宋体;">在本章中我们对如何使用</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">进行服务器管理，调试，配置等进行了详细的讨论，本节内容将会对以后理解</span><span lang="EN-US">Web</span><span style="font-family:宋体;">项目的开发有很大的帮助。</span><span lang="EN-US"> </span>
                                                                                  </p>
                                                                                  
                                                                                  <p>
                                                                                    转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e7%ac%ac%e5%85%ad%e7%ab%a0-%e7%ae%a1%e7%90%86%e5%ba%94%e7%94%a8%e6%9c%8d%e5%8a%a1/">MyEclipse 6 Java 开发中文教程独家连载 &#8211; 第六章 管理应用服务器</a>
                                                                                  </p>