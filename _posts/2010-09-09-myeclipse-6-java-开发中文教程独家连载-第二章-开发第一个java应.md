---
id: 806
title: 'MyEclipse 6 Java 开发中文教程独家连载 &#8211; 第二章 开发第一个Java应用程序'
date: 2010-09-09T20:26:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=806
permalink: '/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e7%ac%ac%e4%ba%8c%e7%ab%a0-%e5%bc%80%e5%8f%91%e7%ac%ac%e4%b8%80%e4%b8%aajava%e5%ba%94/'
views:
  - "5302"
original_post_id:
  - "806"
image: /wp-content/uploads/2012/09/clip_image002_thumb21.jpg
categories:
  - MyEclipse6中文教程
---
**<font color="#ff0000">如果您需要转载本书内容, 请与本站联系! Email: </font>**[**<font color="#ff0000">wlsmon@qq.com</font>**](mailto:wlsmon@qq.com)**<font color="#ff0000">.</font>**

&#160;

## <a name="_Toc201479562"><span lang="EN-US">2.1 </span></a><span><span style="font-family:宋体;">介绍</span></span>     <span lang="EN-US"></p> 

<p>
  </span></h2> 
  
  <p class="MsoNormal" style="text-indent:21.75pt;">
    <span style="font-family:宋体;">本章通过对比手工开发和使用</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">开发第一个</span><span lang="EN-US">HelloWorld</span><span style="font-family:宋体;">的</span><span lang="EN-US">Java</span><span style="font-family:宋体;">程序，让读者对手工写代码和使用开发工具有一定的比较。</span><span lang="EN-US"> </p> 
    
    <p>
      </span>
    </p>
    
    <p class="MsoNormal" style="text-indent:21.75pt;">
      <span style="font-family:宋体;">本章内容参考视频：</span><span lang="EN-US"><a href="http://www.blogjava.net/beansoft/archive/2007/09/24/147651.html">http://www.blogjava.net/beansoft/archive/2007/09/24/147651.html</a> <b>MyEclipse 6 </b></span><b><span style="font-family:宋体;">实战开发讲解视频入门</span><span lang="EN-US"> 0: </span></b><b><span style="font-family:宋体;">下载</span> </b><b><span style="font-family:宋体;">安装</span> </b><b><span style="font-family:宋体;">运行</span><span lang="EN-US"> HelloWorld</span></b><span style="font-family:宋体;">。</span><span lang="EN-US"> </p> 
      
      <p>
        </span>
      </p>
      
      <h2>
        <a name="_Toc201479563"><span lang="EN-US">2.2 </span></a><span><span style="font-family:宋体;">手工编写，编译并运行</span><span lang="EN-US">Java</span></span><span><span style="font-family:宋体;">程序</span></span><span lang="EN-US"> </p> 
        
        <p>
          </span></h2> 
          
          <p class="MsoNormal" style="text-indent:21.75pt;">
            <span style="font-family:宋体;">要进行本节所介绍的操作，请务必首先按照第二章的</span><span lang="EN-US"><a href="#_JDK_的下载，安装和配置（可选）">JDK <span lang="EN-US" style="font-family:宋体;"><span lang="EN-US">的下载，安装和配置</span></span></a></span><span style="font-family:宋体;">一节配置好</span><span lang="EN-US">JDK</span><span style="font-family:宋体;">开发环境。</span><span lang="EN-US"> </p> 
            
            <p>
              </span>
            </p>
            
            <p class="MsoNormal" style="text-indent:21.75pt;">
              <span style="font-family:宋体;">双击桌面上的<b>我的电脑</b>图标，接着双击</span><b><span lang="EN-US">C</span></b><b><span style="font-family:宋体;">盘</span></b><span style="font-family:宋体;">，再选择菜单<b>工具</b></span><b><span lang="EN-US">(T)… > </span></b><b><span style="font-family:宋体;">文件夹选项</span><span lang="EN-US">(O)…</span></b><span style="font-family:宋体;">，按照下图设置显示已知文件类型的扩展名：</span><span lang="EN-US"> </p> 
              
              <p>
                </span>
              </p>
              
              <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0022.jpg"><img title="clip_image002" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="407" alt="clip_image002" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image002_thumb2.jpg" width="335" border="0" /></a> </p> 
                
                <p>
                  </span>
                </p>
                
                <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                  <span style="font-family:宋体;">图</span><span lang="EN-US">2.1 </span><span style="font-family:宋体;">设置</span><span lang="EN-US">Windows</span><span style="font-family:宋体;">显示所有文件的扩展名</span><span lang="EN-US"> </p> 
                  
                  <p>
                    </span>
                  </p>
                  
                  <p class="MsoNormal" style="text-indent:21.75pt;">
                    <span style="font-family:宋体;">。这样做的目的是为了以后能方便的区分出来</span><span lang="EN-US">Hello.txt</span><span style="font-family:宋体;">，</span><span lang="EN-US">Hello.java</span><span style="font-family:宋体;">，</span><span lang="EN-US">Hello.class</span><span style="font-family:宋体;">这些不同的文件类型，也为了使记事本软件不会自作聪明的把我们要写的程序最后给保存成</span><span lang="EN-US">HelloWorld.java.txt</span><span style="font-family:宋体;">。</span><span lang="EN-US"> </p> 
                    
                    <p>
                      </span>
                    </p>
                    
                    <p class="MsoNormal" style="text-indent:21.75pt;">
                      <span style="font-family:宋体;">然后选择</span><span lang="EN-US">Windows</span><span style="font-family:宋体;">的<b>开始</b>菜单，依次选择<b>所有程序</b></span><b><span lang="EN-US"> > </span></b><b><span style="font-family:宋体;">附件</span><span lang="EN-US"> > </span></b><b><span style="font-family:宋体;">记事本</span></b><span style="font-family:宋体;">来启动文本编辑器记事本，当然你也可以用自己喜欢的写文本的软件例如</span><span lang="EN-US">EditPlus</span><span style="font-family:宋体;">，</span><span lang="EN-US">UltraEdit</span><span style="font-family:宋体;">，</span><span lang="EN-US">Notepad2</span><span style="font-family:宋体;">，</span><span>Notepad++</span><span style="font-family:宋体;">等，但是不要使用</span><span lang="EN-US">Word</span><span style="font-family:宋体;">这样的软件来写代码。启动后输入下面的代码：</span><span lang="EN-US"> </p> 
                      
                      <p>
                        </span>
                      </p>
                      
                      <div align="center">
                        <table class="Char" style="background:#e0e0e0;border-collapse:collapse;" cellspacing="0" cellpadding="0" border="0">
                          <tr>
                            <td style="width:320.4pt;padding:0 5.4pt;" valign="top" width="427">
                              <p class="MsoNormal">
                                <span lang="EN-US">public class HelloWorld { </p> 
                                
                                <p>
                                  </span>
                                </p>
                                
                                <p class="MsoNormal">
                                  <span lang="EN-US"> </p> 
                                  
                                  <p>
                                    &#160;
                                  </p>
                                  
                                  <p>
                                    </span>
                                  </p>
                                  
                                  <p class="MsoNormal" style="text-indent:10.5pt;">
                                    <span lang="EN-US">public static void main(String[] args) { </p> 
                                    
                                    <p>
                                      </span>
                                    </p>
                                    
                                    <p class="MsoNormal" style="text-indent:21pt;">
                                      <span lang="EN-US">System.out.println("</span><span style="font-family:宋体;">你好</span> <span style="font-family:宋体;">世界</span><span lang="EN-US">!"); </p> 
                                      
                                      <p>
                                        </span>
                                      </p>
                                      
                                      <p class="MsoNormal" style="text-indent:10.5pt;">
                                        <span lang="EN-US">} </p> 
                                        
                                        <p>
                                          </span>
                                        </p>
                                        
                                        <p class="MsoNormal">
                                          <span lang="EN-US"> </p> 
                                          
                                          <p>
                                            &#160;
                                          </p>
                                          
                                          <p>
                                            </span>
                                          </p>
                                          
                                          <p class="MsoNormal">
                                            <span lang="EN-US">} </p> 
                                            
                                            <p>
                                              </span>
                                            </p></td> </tr> </tbody> </table></div> 
                                            
                                            <p class="MsoNormal" style="text-indent:21.75pt;">
                                              <span style="font-family:宋体;">接着点击记事本的菜单<b>文件</b></span><b><span lang="EN-US"> > </span></b><b><span style="font-family:宋体;">保存</span></b><span style="font-family:宋体;">，在弹出的文件保存对话框中输入路径：</span><i><span lang="EN-US">C:HelloWorld.java</span></i><span style="font-family:宋体;">，然后点击对话框的<b>保存</b>按钮即可。</span><span lang="EN-US"> </p> 
                                              
                                              <p>
                                                </span>
                                              </p>
                                              
                                              <p class="MsoNormal" style="text-indent:21.75pt;">
                                                <b><span style="color:red;font-family:宋体;">注意：</span></b><span style="font-family:宋体;">文件名后缀以及大小写均不能写错，<b>使用输入法的时候不要使用中文标点或者全角字母来输入代码</b>，否则会出现无法识别的情况。</span><span lang="EN-US"> </p> 
                                                
                                                <p>
                                                  </span>
                                                </p>
                                                
                                                <p class="MsoNormal" style="text-indent:21.75pt;">
                                                  <span style="font-family:宋体;">接着我们需要编译和运行这个程序。点击<b>开始</b>菜单，选择<b>运行</b>，输入</span><i><span lang="EN-US">cmd</span></i><span style="font-family:宋体;">后点击确定按钮启动命令解释器。接着输入下列命令：</span><span lang="EN-US"> </p> 
                                                  
                                                  <p>
                                                    </span>
                                                  </p>
                                                  
                                                  <table class="Char" style="background:#e0e0e0;border-collapse:collapse;" cellspacing="0" cellpadding="0" border="0">
                                                    <tr>
                                                      <td style="width:426.1pt;padding:0 5.4pt;" valign="top" width="568">
                                                        <p class="MsoNormal">
                                                          <span lang="EN-US">cd C: </p> 
                                                          
                                                          <p>
                                                            </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal">
                                                            <span lang="EN-US">javac HelloWorld.java </p> 
                                                            
                                                            <p>
                                                              </span>
                                                            </p>
                                                            
                                                            <p class="MsoNormal">
                                                              <span lang="EN-US">java HelloWorld </p> 
                                                              
                                                              <p>
                                                                </span>
                                                              </p></td> </tr> </tbody> </table> 
                                                              
                                                              <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                <span style="font-family:宋体;">如果没有出现任何错误的话，将会打印出：</span><span lang="EN-US"> </p> 
                                                                
                                                                <p>
                                                                  </span>
                                                                </p>
                                                                
                                                                <table class="Char" style="background:#e0e0e0;border-collapse:collapse;" cellspacing="0" cellpadding="0" border="0">
                                                                  <tr>
                                                                    <td style="width:426.1pt;padding:0 5.4pt;" valign="top" width="568">
                                                                      <p class="MsoNormal">
                                                                        <span style="font-family:宋体;">你好</span> <span style="font-family:宋体;">世界</span><span lang="EN-US">! </p> 
                                                                        
                                                                        <p>
                                                                          </span>
                                                                        </p></td> </tr> </tbody> </table> 
                                                                        
                                                                        <h2>
                                                                          <a name="_Toc201479564"></a><a name="_使用Eclipse/MyEclipse来编写，编译并运行Java程序"></a><a name="_2.3_使用Eclipse/MyEclipse来编写，编译并运行Jav"></a><span><span lang="EN-US">2.3 </span></span><span><span style="font-family:宋体;">使用</span><span lang="EN-US">Eclipse/MyEclipse</span></span><span><span style="font-family:宋体;">来编写，编译并运行</span><span lang="EN-US">Java</span></span><span><span style="font-family:宋体;">程序</span></span><span lang="EN-US"> </p> 
                                                                          
                                                                          <p>
                                                                            </span></h2> 
                                                                            
                                                                            <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                              <span style="font-size:10pt;font-family:宋体;">从菜单栏选择</span><span style="font-size:10pt;"> <strong><span lang="EN-US" style="font-family:&quot;">File > New > Java Project</span></strong></span><span style="font-size:10pt;font-family:宋体;">，接着会打开</span><span style="font-size:10pt;"> <b><span lang="EN-US">New Java Project</span></b><span lang="EN-US"> </span></span><span style="font-size:10pt;font-family:宋体;">（新建</span><span lang="EN-US" style="font-size:10pt;">Java</span><span style="font-size:10pt;font-family:宋体;">项目）向导</span><span style="font-family:宋体;">，如图</span><span lang="EN-US">2.2</span><span>所示。在</span><b><span lang="EN-US">Project name </span></b><span style="font-family:宋体;">（项目名称）中输入</span><i><span lang="EN-US">HelloWorld</span></i><span style="font-family:宋体;">，点击</span><b><span lang="EN-US">Finish</span></b><span style="font-family:宋体;">（完成）按钮关闭对话框，这样一个</span><span lang="EN-US">Java</span><span style="font-family:宋体;">项目就建立完毕了。</span><span lang="EN-US"> </p> 
                                                                              
                                                                              <p>
                                                                                </span>
                                                                              </p>
                                                                              
                                                                              <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                                <span style="font-family:宋体;">此对话框中属性的详细介绍如下表所示：</span><span lang="EN-US"> </p> 
                                                                                
                                                                                <p>
                                                                                  </span>
                                                                                </p>
                                                                                
                                                                                <table class="MsoNormalTable" style="border-right:medium none;border-top:medium none;border-left:medium none;width:450pt;border-bottom:medium none;border-collapse:collapse;" cellspacing="0" cellpadding="0" width="600" border="1">
                                                                                  <tr>
                                                                                    <td style="border-right:windowtext 1pt solid;border-top:windowtext 1pt solid;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                      <p class="MsoNormal">
                                                                                        <b><span style="font-family:宋体;">选项</span><span lang="EN-US"> </p> 
                                                                                        
                                                                                        <p>
                                                                                          </span></b>
                                                                                        </p></td> 
                                                                                        
                                                                                        <td style="border-right:windowtext 1pt solid;border-top:windowtext 1pt solid;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                          <p class="MsoNormal">
                                                                                            <b><span style="font-family:宋体;">描述</span><span lang="EN-US"> </p> 
                                                                                            
                                                                                            <p>
                                                                                              </span></b>
                                                                                            </p></td> </tr> 
                                                                                            
                                                                                            <tr>
                                                                                              <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                <p class="MsoNormal">
                                                                                                  <b><span lang="EN-US">Contents </p> 
                                                                                                  
                                                                                                  <p>
                                                                                                    </span></b>
                                                                                                  </p></td> 
                                                                                                  
                                                                                                  <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                    <p class="MsoNormal">
                                                                                                      <span style="font-family:宋体;">项目内容</span><span lang="EN-US"> </p> 
                                                                                                      
                                                                                                      <p>
                                                                                                        </span>
                                                                                                      </p></td> </tr> 
                                                                                                      
                                                                                                      <tr>
                                                                                                        <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                          <p class="MsoNormal">
                                                                                                            <b><span lang="EN-US">Create new project in workspace </p> 
                                                                                                            
                                                                                                            <p>
                                                                                                              </span></b>
                                                                                                            </p></td> 
                                                                                                            
                                                                                                            <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                              <p class="MsoNormal">
                                                                                                                <span style="font-family:宋体;">在工作区中创建新项目</span><span lang="EN-US"> </p> 
                                                                                                                
                                                                                                                <p>
                                                                                                                  </span>
                                                                                                                </p></td> </tr> 
                                                                                                                
                                                                                                                <tr>
                                                                                                                  <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                                    <p class="MsoNormal">
                                                                                                                      <b><span lang="EN-US">Create project from existing source </p> 
                                                                                                                      
                                                                                                                      <p>
                                                                                                                        </span></b>
                                                                                                                      </p></td> 
                                                                                                                      
                                                                                                                      <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                                        <p class="MsoNormal">
                                                                                                                          <span style="font-family:宋体;">从现有代码中创建项目，在</span><span lang="EN-US">Directory</span><span style="font-family:宋体;">右侧文本框中输入现有项目的目录</span><span lang="EN-US"> </p> 
                                                                                                                          
                                                                                                                          <p>
                                                                                                                            </span>
                                                                                                                          </p></td> </tr> 
                                                                                                                          
                                                                                                                          <tr>
                                                                                                                            <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                                              <p class="MsoNormal">
                                                                                                                                <b><span lang="EN-US">JRE </p> 
                                                                                                                                
                                                                                                                                <p>
                                                                                                                                  </span></b>
                                                                                                                                </p></td> 
                                                                                                                                
                                                                                                                                <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                                                  <p class="MsoNormal">
                                                                                                                                    <span style="font-family:宋体;">选择项目的</span><span lang="EN-US">JRE </p> 
                                                                                                                                    
                                                                                                                                    <p>
                                                                                                                                      </span>
                                                                                                                                    </p></td> </tr> 
                                                                                                                                    
                                                                                                                                    <tr>
                                                                                                                                      <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                                                        <p class="MsoNormal">
                                                                                                                                          <b><span lang="EN-US">Use default JRE(Currently ‘MyEclipse6.0’) </p> 
                                                                                                                                          
                                                                                                                                          <p>
                                                                                                                                            </span></b>
                                                                                                                                          </p></td> 
                                                                                                                                          
                                                                                                                                          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                                                            <p class="MsoNormal">
                                                                                                                                              <span style="font-family:宋体;">使用默认</span><span lang="EN-US">JRE</span><span style="font-family:宋体;">，可以点击</span><b><span lang="EN-US">Configure default..</span></b><span lang="EN-US">.</span><span style="font-family:宋体;">链接来配置默认的</span><span lang="EN-US">JRE </p> 
                                                                                                                                              
                                                                                                                                              <p>
                                                                                                                                                </span>
                                                                                                                                              </p></td> </tr> 
                                                                                                                                              
                                                                                                                                              <tr>
                                                                                                                                                <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                                                                  <p class="MsoNormal">
                                                                                                                                                    <b><span lang="EN-US">Use an execution enviroment JRE </p> 
                                                                                                                                                    
                                                                                                                                                    <p>
                                                                                                                                                      </span></b>
                                                                                                                                                    </p></td> 
                                                                                                                                                    
                                                                                                                                                    <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                                                                      <p class="MsoNormal">
                                                                                                                                                        <span style="font-family:宋体;">使用运行时候所选择的</span><span lang="EN-US">JRE </p> 
                                                                                                                                                        
                                                                                                                                                        <p>
                                                                                                                                                          </span>
                                                                                                                                                        </p></td> </tr> 
                                                                                                                                                        
                                                                                                                                                        <tr>
                                                                                                                                                          <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                                                                            <p class="MsoNormal">
                                                                                                                                                              <b><span lang="EN-US">Layout </p> 
                                                                                                                                                              
                                                                                                                                                              <p>
                                                                                                                                                                </span></b>
                                                                                                                                                              </p></td> 
                                                                                                                                                              
                                                                                                                                                              <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                                                                                <p class="MsoNormal">
                                                                                                                                                                  <span style="font-family:宋体;">项目布局</span><span lang="EN-US"> </p> 
                                                                                                                                                                  
                                                                                                                                                                  <p>
                                                                                                                                                                    </span>
                                                                                                                                                                  </p></td> </tr> 
                                                                                                                                                                  
                                                                                                                                                                  <tr>
                                                                                                                                                                    <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                                                                                      <p class="MsoNormal">
                                                                                                                                                                        <b><span lang="EN-US">Use project folder as root for sources and class files </p> 
                                                                                                                                                                        
                                                                                                                                                                        <p>
                                                                                                                                                                          </span></b>
                                                                                                                                                                        </p></td> 
                                                                                                                                                                        
                                                                                                                                                                        <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                                                                                          <p class="MsoNormal">
                                                                                                                                                                            <span style="font-family:宋体;">使用项目目录作为源代码和类的根目录。<b><span style="color:red;">注意：</span></b>这种方式不推荐，因为</span><span lang="EN-US">.java</span><span style="font-family:宋体;">和</span><span lang="EN-US">.class</span><span style="font-family:宋体;">文件混杂一起</span><span lang="EN-US"> </p> 
                                                                                                                                                                            
                                                                                                                                                                            <p>
                                                                                                                                                                              </span>
                                                                                                                                                                            </p></td> </tr> 
                                                                                                                                                                            
                                                                                                                                                                            <tr>
                                                                                                                                                                              <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:windowtext 1pt solid;width:185.4pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="247">
                                                                                                                                                                                <p class="MsoNormal">
                                                                                                                                                                                  <b><span lang="EN-US">Create separate folders for sources and class files </p> 
                                                                                                                                                                                  
                                                                                                                                                                                  <p>
                                                                                                                                                                                    </span></b>
                                                                                                                                                                                  </p></td> 
                                                                                                                                                                                  
                                                                                                                                                                                  <td style="border-right:windowtext 1pt solid;border-top:medium none;border-left:medium none;width:264.6pt;border-bottom:windowtext 1pt solid;padding:0 5.4pt;" valign="top" width="353">
                                                                                                                                                                                    <p class="MsoNormal">
                                                                                                                                                                                      <span style="font-family:宋体;">使用分开的目录来分别存放源代码和类文件，这种方式推荐使用。也可以</span><span style="font-family:宋体;">点击</span><b><span lang="EN-US">Configure default&#8230;</span></b><span style="font-family:宋体;">链接来配置默认的项目布局。</span><span lang="EN-US"> </p> 
                                                                                                                                                                                      
                                                                                                                                                                                      <p>
                                                                                                                                                                                        </span>
                                                                                                                                                                                      </p></td> </tr> </tbody> </table> 
                                                                                                                                                                                      
                                                                                                                                                                                      <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                                                                                                                                        <span lang="EN-US"> </p> 
                                                                                                                                                                                        
                                                                                                                                                                                        <p>
                                                                                                                                                                                          &#160;
                                                                                                                                                                                        </p>
                                                                                                                                                                                        
                                                                                                                                                                                        <p>
                                                                                                                                                                                          </span>
                                                                                                                                                                                        </p>
                                                                                                                                                                                        
                                                                                                                                                                                        <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                                                                                                                                                                                          <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0041.jpg"><img title="clip_image004" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="520" alt="clip_image004" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image004_thumb1.jpg" width="447" border="0" /></a> </p> 
                                                                                                                                                                                          
                                                                                                                                                                                          <p>
                                                                                                                                                                                            </span>
                                                                                                                                                                                          </p>
                                                                                                                                                                                          
                                                                                                                                                                                          <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                                                                                                                                                                                            <span style="font-family:宋体;">图</span><span lang="EN-US">2.2 </span><span style="font-family:宋体;">新建</span><span lang="EN-US"> Java </span><span style="font-family:宋体;">项目</span><span lang="EN-US"> </p> 
                                                                                                                                                                                            
                                                                                                                                                                                            <p>
                                                                                                                                                                                              </span>
                                                                                                                                                                                            </p>
                                                                                                                                                                                            
                                                                                                                                                                                            <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                                                                                                                                              <span style="font-family:宋体;">稍等片刻会弹出一个切换透视图的对话框：</span><span lang="EN-US"> </p> 
                                                                                                                                                                                              
                                                                                                                                                                                              <p>
                                                                                                                                                                                                </span>
                                                                                                                                                                                              </p>
                                                                                                                                                                                              
                                                                                                                                                                                              <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                                                                                                                                                                                                <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0061.jpg"><img title="clip_image006" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="180" alt="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image006_thumb1.jpg" width="462" border="0" /></a> </p> 
                                                                                                                                                                                                
                                                                                                                                                                                                <p>
                                                                                                                                                                                                  </span>
                                                                                                                                                                                                </p>
                                                                                                                                                                                                
                                                                                                                                                                                                <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                                                                                                                                                                                                  <span style="font-family:宋体;">图</span><span lang="EN-US">2.3 </span><span style="font-family:宋体;">切换到响应的透视图的对话框</span><span lang="EN-US"> </p> 
                                                                                                                                                                                                  
                                                                                                                                                                                                  <p>
                                                                                                                                                                                                    </span>
                                                                                                                                                                                                  </p>
                                                                                                                                                                                                  
                                                                                                                                                                                                  <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                                                                                                                                                    <span style="font-family:宋体;">为了避免造成更多的麻烦，我们一般选择</span><b><span lang="EN-US">No</span></b><span style="font-family:宋体;">按钮就可以了。接着选择菜单</span><strong><span lang="EN-US" style="font-size:10pt;font-family:&quot;">File > New >Class</span></strong><strong><span style="font-size:10pt;font-family:宋体;">，</span></strong><strong><span style="font-weight:normal;font-size:10pt;font-family:宋体;">然后新建类的对话框就出现了：</span></strong><strong><span lang="EN-US" style="font-weight:normal;font-size:10pt;font-family:&quot;"> </p> 
                                                                                                                                                                                                    
                                                                                                                                                                                                    <p>
                                                                                                                                                                                                      </span></strong>
                                                                                                                                                                                                    </p>
                                                                                                                                                                                                    
                                                                                                                                                                                                    <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                                                                                                                                                                                                      <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0081.jpg"><img title="clip_image008" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="491" alt="clip_image008" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image008_thumb1.jpg" width="499" border="0" /></a> </p> 
                                                                                                                                                                                                      
                                                                                                                                                                                                      <p>
                                                                                                                                                                                                        </span>
                                                                                                                                                                                                      </p>
                                                                                                                                                                                                      
                                                                                                                                                                                                      <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                                                                                                                                                                                                        <span style="font-family:宋体;">图</span><span lang="EN-US">2.4 </span><span style="font-family:宋体;">新建类的对话框</span><span lang="EN-US"> </p> 
                                                                                                                                                                                                        
                                                                                                                                                                                                        <p>
                                                                                                                                                                                                          </span>
                                                                                                                                                                                                        </p>
                                                                                                                                                                                                        
                                                                                                                                                                                                        <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                                                                                                                                                          <span style="font-family:宋体;">在</span><b><span lang="EN-US">Name</span></b><span style="font-family:宋体;">输入框中输入</span><i><span lang="EN-US">HelloWorld</span></i><span style="font-family:宋体;">，点击完成，也可以在</span><b><span lang="EN-US">Package</span></b><span style="font-family:宋体;">中输入自己希望用的包名。接着将编辑器里面的代码修改成如下所示：</span><span lang="EN-US"> </p> 
                                                                                                                                                                                                          
                                                                                                                                                                                                          <p>
                                                                                                                                                                                                            </span>
                                                                                                                                                                                                          </p>
                                                                                                                                                                                                          
                                                                                                                                                                                                          <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                                                                                                                                                            <span lang="EN-US"> </p> 
                                                                                                                                                                                                            
                                                                                                                                                                                                            <p>
                                                                                                                                                                                                              &#160;
                                                                                                                                                                                                            </p>
                                                                                                                                                                                                            
                                                                                                                                                                                                            <p>
                                                                                                                                                                                                              </span>
                                                                                                                                                                                                            </p>
                                                                                                                                                                                                            
                                                                                                                                                                                                            <div align="center">
                                                                                                                                                                                                              <table class="Char" style="background:#e0e0e0;border-collapse:collapse;" cellspacing="0" cellpadding="0" border="0">
                                                                                                                                                                                                                <tr>
                                                                                                                                                                                                                  <td style="width:320.4pt;padding:0 5.4pt;" valign="top" width="427">
                                                                                                                                                                                                                    <p class="MsoNormal">
                                                                                                                                                                                                                      <span lang="EN-US">public class HelloWorld { </p> 
                                                                                                                                                                                                                      
                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                      
                                                                                                                                                                                                                      <p class="MsoNormal" style="text-indent:10.5pt;">
                                                                                                                                                                                                                        <span lang="EN-US">public static void main(String[] args) { </p> 
                                                                                                                                                                                                                        
                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                          </span>
                                                                                                                                                                                                                        </p>
                                                                                                                                                                                                                        
                                                                                                                                                                                                                        <p class="MsoNormal" style="text-indent:21pt;">
                                                                                                                                                                                                                          <span lang="EN-US">System.out.println("</span><span style="font-family:宋体;">你好</span> <span style="font-family:宋体;">世界</span><span lang="EN-US">!"); </p> 
                                                                                                                                                                                                                          
                                                                                                                                                                                                                          <p>
                                                                                                                                                                                                                            </span>
                                                                                                                                                                                                                          </p>
                                                                                                                                                                                                                          
                                                                                                                                                                                                                          <p class="MsoNormal" style="text-indent:10.5pt;">
                                                                                                                                                                                                                            <span lang="EN-US">} </p> 
                                                                                                                                                                                                                            
                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                            
                                                                                                                                                                                                                            <p class="MsoNormal">
                                                                                                                                                                                                                              <span lang="EN-US">} </p> 
                                                                                                                                                                                                                              
                                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                                </span>
                                                                                                                                                                                                                              </p></td> </tr> </tbody> </table></div> 
                                                                                                                                                                                                                              
                                                                                                                                                                                                                              <p class="MsoNormal">
                                                                                                                                                                                                                                <span style="font-family:宋体;">。当你的代码编写完毕后，</span><span lang="EN-US">MyEclipse</span><span style="font-family:宋体;">会自动将代码编译成类文件。</span><span lang="EN-US"> </p> 
                                                                                                                                                                                                                                
                                                                                                                                                                                                                                <p>
                                                                                                                                                                                                                                  </span>
                                                                                                                                                                                                                                </p>
                                                                                                                                                                                                                                
                                                                                                                                                                                                                                <p class="MsoNormal" style="text-indent:21.75pt;">
                                                                                                                                                                                                                                  <span style="font-family:宋体;">接下来就可以运行写好的类了，选择菜单</span> <b><span lang="EN-US">Run <span>&#160;</span>> <span>&#160;</span>Run </span></b><span style="font-family:宋体;">或者按下快捷键</span><b><span lang="EN-US"> Ctrl+F11</span></b><span style="font-family:宋体;">，就可以看到</span><span lang="EN-US">Eclipse</span><span style="font-family:宋体;">会自动调用</span><span lang="EN-US">Java</span><span style="font-family:宋体;">解释器，然后在</span><b><span lang="EN-US">Console</span></b><span style="font-family:宋体;">视图中输出“你好，世界”，如下图所示：</span><span lang="EN-US"> </p> 
                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                                    </span>
                                                                                                                                                                                                                                  </p>
                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                  <p class="MsoNormal" style="text-indent:21.7px 5pt;text-align:center;" align="center">
                                                                                                                                                                                                                                    <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0101.jpg"><img title="clip_image010" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="119" alt="clip_image010" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image010_thumb1.jpg" width="428" border="0" /></a> </p> 
                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                    <p>
                                                                                                                                                                                                                                      </span>
                                                                                                                                                                                                                                    </p>
                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                    <p class="MsoNormal" style="text-indent:21.75pt;text-align:center;" align="center">
                                                                                                                                                                                                                                      <span style="font-family:宋体;">图</span><span lang="EN-US">2.5 </span><span style="font-family:宋体;">运行并查看程序输入</span><span lang="EN-US"> </p> 
                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                      <h2>
                                                                                                                                                                                                                                        <a name="_Toc201479565"><span lang="EN-US">2.4</span></a><span><span style="font-family:宋体;">小结</span></span><span lang="EN-US"> </p> 
                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                                          </span></h2> 
                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                          <p class="MsoNormal">
                                                                                                                                                                                                                                            <span lang="EN-US"><span>&#160;&#160;&#160; </span></span><span style="font-family:宋体;">通过比较，我们可以看到除了新建</span><span lang="EN-US">Java Project</span><span style="font-family:宋体;">外，使用</span><span lang="EN-US">Eclipse</span><span style="font-family:宋体;">来开发</span><span lang="EN-US">Java</span><span style="font-family:宋体;">类显然要方便快捷的多。而且</span><span lang="EN-US">Eclipse</span><span style="font-family:宋体;">提供语法高亮显示和错误纠正功能，这在做大型项目时尤其有用。然而，</span><span lang="EN-US">Eclipse</span><span style="font-family:宋体;">的开发模式也和手工来进行开发一样，需要经过创建</span><span lang="EN-US">.java</span><span style="font-family:宋体;">文件，编译（</span><span lang="EN-US">Eclipse</span><span style="font-family:宋体;">使用的是内置自动编译器）以及运行的过程。</span><span lang="EN-US"> </p> 
                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                                              转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/09/myeclipse-6-java-%e5%bc%80%e5%8f%91%e4%b8%ad%e6%96%87%e6%95%99%e7%a8%8b%e7%8b%ac%e5%ae%b6%e8%bf%9e%e8%bd%bd-%e7%ac%ac%e4%ba%8c%e7%ab%a0-%e5%bc%80%e5%8f%91%e7%ac%ac%e4%b8%80%e4%b8%aajava%e5%ba%94/">MyEclipse 6 Java 开发中文教程独家连载 &#8211; 第二章 开发第一个Java应用程序</a>
                                                                                                                                                                                                                                            </p>