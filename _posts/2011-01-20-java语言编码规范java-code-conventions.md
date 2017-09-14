---
id: 1634
title: Java语言编码规范(Java Code Conventions)
date: 2011-01-20T19:53:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1634
permalink: '/2011/01/20/java%e8%af%ad%e8%a8%80%e7%bc%96%e7%a0%81%e8%a7%84%e8%8c%83java-code-conventions/'
views:
  - "8084"
original_post_id:
  - "1634"
categories:
  - Java SE
---
</p> 

<table border="0" cellspacing="0" cellpadding="3" width="100%" align="center">
  <tr width="100%">
    <td width="98%">
      <center>
        </p> 
        
        <h4>
          Java语言编码规范(Java Code Conventions)
        </h4>
        
        <table>
          <tr align="left" colspan="3">
            <td width="10%">
            </td>
            
            <td valign="top">
              <table class="middletext" border="1" cellpadding="5" width="100%">
                <tr>
                  <td width="60">
                    <strong>名称</strong>
                  </td>
                  
                  <td>
                    Java语言编码规范(Java Code Conventions)
                  </td>
                </tr>
                
                <tr>
                  <td>
                    <strong>译者</strong>
                  </td>
                  
                  <td>
                    晨光（Morning）
                  </td>
                </tr>
                
                <tr>
                  <td>
                    <strong>简介</strong>
                  </td>
                  
                  <td>
                    本文档讲述了Java语言的编码规范，较之陈世忠先生《c++编码规范》的浩繁详尽，此文当属短小精悍了。而其中所列之各项条款，从编码风格，到注意事项，不单只Java，对于其他语言，也都很有借鉴意义。因为简短，所以易记，大家不妨将此作为handbook，常备案头，逐一对验。
                  </td>
                </tr>
                
                <tr>
                  <td>
                    <strong>声明</strong>
                  </td>
                  
                  <td>
                    如需复制、传播，请附上本声明，谢谢。 <br />原文出处：<a title="http://www.oracle.com/technetwork/java/codeconvtoc-136057.html" href="http://www.oracle.com/technetwork/java/codeconvtoc-136057.html">http://www.oracle.com/technetwork/java/codeconvtoc-136057.html</a>， <br />译文出处：http://morningspace.51.net/，moyingzz@etang.com
                  </td>
                </tr>
                
                <tr>
                  <td colspan="2">
                    <p>
                      <strong>目录</strong>
                    </p>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#1">1 介绍</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#11">1.1 为什么要有编码规范</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#12">1.2 版权声明</a>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#2">2 文件名</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#21">2.1 文件后缀</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#22">2.2 常用文件名</a>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#3">3 文件组织</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#31">3.1 Java源文件</a> <ul>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#311">3.1.1 开头注释</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#312">3.1.2 包和引入语句</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#313">3.1.3 类和接口声明</a>
                          </li>
                        </ul>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#4">4 缩进排版</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#41">4.1 行长度</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#42">4.2 换行</a>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#5">5 注释</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#51">5.1 实现注释的格式</a> <ul>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#511">5.1.1 块注释</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#512">5.1.2 单行注释</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#513">5.1.3 尾端注释</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#514">5.1.4 行末注释</a>
                          </li>
                        </ul>
                      </li>
                      
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#52">5.2 文挡注释</a>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#6">6 声明</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#61">6.1 每行声明变量的数量</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#62">6.2 初始化</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#63">6.3 布局</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#64">6.4 类和接口的声明</a>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#7">7 语句</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#71">7.1 简单语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#72">7.2 复合语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#73">7.3 返回语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#74">7.4 if，if-else，if else-if else语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#75">7.5 for语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#76">7.6 while语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#77">7.7 do-while语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#78">7.8 switch语句</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#79">7.9 try-catch语句</a>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#8">8 空白</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#81">8.1 空行</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#82">8.2 空格</a>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#9">9 命名规范</a> <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a">10 编程惯例</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a1">10.1 提供对实例以及类变量的访问控制</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a2">10.2 引用类变量和类方法</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a3">10.3 常量</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a4">10.4 变量赋值</a>
                      </li>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a5">10.5 其它惯例</a> <ul>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a51">10.5.1 圆括号</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a52">10.5.2 返回值</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a53">10.5.3 条件运算符"?"前的表达式"?"前的表达式</a>
                          </li>
                          <li>
                            <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#a54">10.5.4 特殊注释</a>
                          </li>
                        </ul>
                      </li>
                    </ul>
                    
                    <p>
                      <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#b">11 代码范例</a>
                    </p>
                    
                    <ul>
                      <li>
                        <a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#b1">11.1 Java源文件范例</a>
                      </li>
                    </ul>
                  </td>
                </tr>
              </table>
            </td>
            
            <td width="10%">
            </td>
          </tr>
          
          <tr align="left" colspan="3">
            <td width="10%">
            </td>
            
            <td valign="top">
              <p class="middletitle">
                <a name="1">1 介绍(Introduction)</a>
              </p>
              
              <p class="middletitle">
                <a name="11">1.1 为什么要有编码规范(Why Have Code Conventions)</a>
              </p>
              
              <p>
                编码规范对于程序员而言尤为重要，有以下几个原因：
              </p>
              
              <p>
                &#8211; 一个软件的生命周期中，80%的花费在于维护 <br />&#8211; 几乎没有任何一个软件，在其整个生命周期中，均由最初的开发人员来维护 <br />&#8211; 编码规范可以改善软件的可读性，可以让程序员尽快而彻底地理解新的代码 <br />&#8211; 如果你将源码作为产品发布，就需要确任它是否被很好的打包并且清晰无误，一如你已构建的其它任何产品
              </p>
              
              <p>
                为了执行规范，每个软件开发人员必须一致遵守编码规范。每个人。
              </p>
              
              <p class="middletitle">
                <a name="12">1.2 版权声明(Acknowledgments)</a>
              </p>
              
              <p>
                本文档反映的是Sun MicroSystems公司，Java语言规范中的编码标准部分。主要贡献者包括：Peter King，Patrick Naughton，Mike DeMoney，Jonni Kanerva，Kathy Walrath以及Scott Hommel。
              </p>
              
              <p>
                本文档现由Scott Hommel维护，有关评论意见请发至shommel@eng.sun.com
              </p>
              
              <p class="middletitle">
                <a name="2">2 文件名(File Names)</a>
              </p>
              
              <p>
                这部分列出了常用的文件名及其后缀。
              </p>
              
              <p class="middletitle">
                <a name="21">2.1 文件后缀(File Suffixes)</a>
              </p>
              
              <p>
                Java程序使用下列文件后缀：
              </p>
              
              <table border="1">
                <tr>
                  <td>
                    文件类别
                  </td>
                  
                  <td>
                    文件后缀
                  </td>
                </tr>
                
                <tr>
                  <td>
                    Java源文件
                  </td>
                  
                  <td>
                    .java
                  </td>
                </tr>
                
                <tr>
                  <td>
                    Java字节码文件
                  </td>
                  
                  <td>
                    .class
                  </td>
                </tr>
              </table>
              
              <p class="middletitle">
                <a name="22">2.2 常用文件名(Common File Names)</a>
              </p>
              
              <p>
                常用的文件名包括：
              </p>
              
              <table border="1">
                <tr>
                  <td>
                    文件名
                  </td>
                  
                  <td>
                    用途
                  </td>
                </tr>
                
                <tr>
                  <td>
                    GNUmakefile
                  </td>
                  
                  <td>
                    makefiles的首选文件名。我们采用gnumake来创建（build）软件。
                  </td>
                </tr>
                
                <tr>
                  <td>
                    README
                  </td>
                  
                  <td>
                    概述特定目录下所含内容的文件的首选文件名
                  </td>
                </tr>
              </table>
              
              <p class="middletitle">
                <a name="3">3 文件组织(File Organization)</a>
              </p>
              
              <p>
                一个文件由被空行分割而成的段落以及标识每个段落的可选注释共同组成。超过2000行的程序难以阅读，应该尽量避免。"Java源文件范例"提供了一个布局合理的Java程序范例。
              </p>
              
              <p class="middletitle">
                <a name="31">3.1 Java源文件(Java Source Files)</a>
              </p>
              
              <p>
                每个Java源文件都包含一个单一的公共类或接口。若私有类和接口与一个公共类相关联，可以将它们和公共类放入同一个源文件。公共类必须是这个文件中的第一个类或接口。
              </p>
              
              <p>
                Java源文件还遵循以下规则：
              </p>
              
              <p>
                &#8211; 开头注释（参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#311">开头注释</a>"） <br />&#8211; 包和引入语句（参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#312">包和引入语句</a>"） <br />&#8211; 类和接口声明（参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#313">类和接口声明</a>"）
              </p>
              
              <p class="middletitle">
                <a name="311">3.1.1 开头注释(Beginning Comments)</a>
              </p>
              
              <p>
                所有的源文件都应该在开头有一个C语言风格的注释，其中列出类名、版本信息、日期和版权声明：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  /*
   * Classname
   *
   * Version information
   *
   * Date
   *
   * Copyright notice
   */
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="312">3.1.2 包和引入语句(Package and Import Statements)</a>
              </p>
              
              <p>
                在多数Java源文件中，第一个非注释行是包语句。在它之后可以跟引入语句。例如：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  package java.awt;

  import java.awt.peer.CanvasPeer;
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="313">3.1.3 类和接口声明(Class and Interface Declarations)</a>
              </p>
              
              <p>
                下表描述了类和接口声明的各个部分以及它们出现的先后次序。参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#b1">Java源文件范例</a>"中一个包含注释的例子。
              </p>
              
              <table border="1">
                <tr>
                  <td>
                    &#160;
                  </td>
                  
                  <td>
                    类/接口声明的各部分
                  </td>
                  
                  <td>
                    注解
                  </td>
                </tr>
                
                <tr>
                  <td>
                    1
                  </td>
                  
                  <td>
                    类/接口文档注释(/**……*/)
                  </td>
                  
                  <td>
                    该注释中所需包含的信息，参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#52">文档注释</a>"
                  </td>
                </tr>
                
                <tr>
                  <td>
                    2
                  </td>
                  
                  <td>
                    类或接口的声明
                  </td>
                  
                  <td>
                    &#160;
                  </td>
                </tr>
                
                <tr>
                  <td>
                    3
                  </td>
                  
                  <td>
                    类/接口实现的注释(/*……*/)如果有必要的话
                  </td>
                  
                  <td>
                    该注释应包含任何有关整个类或接口的信息，而这些信息又不适合作为类/接口文档注释。
                  </td>
                </tr>
                
                <tr>
                  <td>
                    4
                  </td>
                  
                  <td>
                    类的(静态)变量
                  </td>
                  
                  <td>
                    首先是类的公共变量，随后是保护变量，再后是包一级别的变量(没有访问修饰符，access modifier)，最后是私有变量。
                  </td>
                </tr>
                
                <tr>
                  <td>
                    5
                  </td>
                  
                  <td>
                    实例变量
                  </td>
                  
                  <td>
                    首先是公共级别的，随后是保护级别的，再后是包一级别的(没有访问修饰符)，最后是私有级别的。
                  </td>
                </tr>
                
                <tr>
                  <td>
                    6
                  </td>
                  
                  <td>
                    构造器
                  </td>
                  
                  <td>
                    &#160;
                  </td>
                </tr>
                
                <tr>
                  <td>
                    7
                  </td>
                  
                  <td>
                    方法
                  </td>
                  
                  <td>
                    这些方法应该按功能，而非作用域或访问权限，分组。例如，一个私有的类方法可以置于两个公有的实例方法之间。其目的是为了更便于阅读和理解代码。
                  </td>
                </tr>
              </table>
              
              <p class="middletitle">
                <a name="4">4 缩进排版(Indentation)</a>
              </p>
              
              <p>
                4个空格常被作为缩进排版的一个单位。缩进的确切解释并未详细指定(空格 vs. 制表符)。一个制表符等于8个空格(而非4个)。
              </p>
              
              <p class="middletitle">
                <a name="41">4.1 行长度(Line Length)</a>
              </p>
              
              <p>
                尽量避免一行的长度超过80个字符，因为很多终端和工具不能很好处理之。
              </p>
              
              <p>
                注意：用于文档中的例子应该使用更短的行长，长度一般不超过70个字符。
              </p>
              
              <p class="middletitle">
                <a name="42">4.2 换行(Wrapping Lines)</a>
              </p>
              
              <p>
                当一个表达式无法容纳在一行内时，可以依据如下一般规则断开之：
              </p>
              
              <p>
                &#8211; 在一个逗号后面断开<br /> <br />&#8211; 在一个操作符前面断开
              </p>
              
              <p>
                &#8211; 宁可选择较高级别(higher-level)的断开，而非较低级别(lower-level)的断开
              </p>
              
              <p>
                &#8211; 新的一行应该与上一行同一级别表达式的开头处对齐
              </p>
              
              <p>
                &#8211; 如果以上规则导致你的代码混乱或者使你的代码都堆挤在右边，那就代之以缩进8个空格。
              </p>
              
              <p>
                以下是断开方法调用的一些例子：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  someMethod(longExpression1, longExpression2, longExpression3, 
                   longExpression4, longExpression5);

  var = someMethod1(longExpression1, 
                            someMethod2(longExpression2, 
                                               longExpression3));
          </pre>
              
              <p>
              </p>
              
              <p>
                以下是两个断开算术表达式的例子。前者更好，因为断开处位于括号表达式的外边，这是个较高级别的断开。
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  longName1 = longName2 * (longName3 + longName4 - longName5)
                     + 4 * longname6; //PREFFER

  longName1 = longName2 * (longName3 + longName4 
                                         - longName5) + 4 * longname6; //AVOID
          </pre>
              
              <p>
              </p>
              
              <p>
                以下是两个缩进方法声明的例子。前者是常规情形。后者若使用常规的缩进方式将会使第二行和第三行移得很靠右，所以代之以缩进8个空格
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  //CONVENTIONAL INDENTATION
  someMethod(int anArg, Object anotherArg, String yetAnotherArg, 
                    Object andStillAnother) {
    ...
  }

  //INDENT 8 SPACES TO AVOID VERY DEEP INDENTS
  private static synchronized horkingLongMethodName(int anArg,
          Object anotherArg, String yetAnotherArg,
          Object andStillAnother) {
    ...
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                if语句的换行通常使用8个空格的规则，因为常规缩进(4个空格)会使语句体看起来比较费劲。比如：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  //DON'T USE THIS INDENTATION
  if ((condition1 && condition2)
      || (condition3 && condition4)
      ||!(condition5 && condition6)) { //BAD WRAPS
      doSomethingAboutIt();             //MAKE THIS LINE EASY TO MISS
  }

  //USE THIS INDENTATION INSTEAD
  if ((condition1 && condition2)
          || (condition3 && condition4)
          ||!(condition5 && condition6)) {
      doSomethingAboutIt();
  }

  //OR USE THIS
  if ((condition1 && condition2) || (condition3 && condition4)
          ||!(condition5 && condition6)) {
      doSomethingAboutIt();
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                这里有三种可行的方法用于处理三元运算表达式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  alpha = (aLongBooleanExpression) ? beta : gamma;

  alpha = (aLongBooleanExpression) ? beta
                                   : gamma;

  alpha = (aLongBooleanExpression)
          ? beta
          : gamma;
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="5">5 注释(Comments)</a>
              </p>
              
              <p>
                Java程序有两类注释：实现注释(implementation comments)和文档注释(document comments)。实现注释是那些在C++中见过的，使用/*&#8230;*/和//界定的注释。文档注释(被称为"doc comments")是Java独有的，并由/**&#8230;*/界定。文档注释可以通过javadoc工具转换成HTML文件。
              </p>
              
              <p>
                实现注释用以注释代码或者实现细节。文档注释从实现自由(implementation-free)的角度描述代码的规范。它可以被那些手头没有源码的开发人员读懂。
              </p>
              
              <p>
                注释应被用来给出代码的总括，并提供代码自身没有提供的附加信息。注释应该仅包含与阅读和理解程序有关的信息。例如，相应的包如何被建立或位于哪个目录下之类的信息不应包括在注释中。
              </p>
              
              <p>
                在注释里，对设计决策中重要的或者不是显而易见的地方进行说明是可以的，但应避免提供代码中己清晰表达出来的重复信息。多余的的注释很容易过时。通常应避免那些代码更新就可能过时的注释。
              </p>
              
              <p>
                注意：频繁的注释有时反映出代码的低质量。当你觉得被迫要加注释的时候，考虑一下重写代码使其更清晰。
              </p>
              
              <p>
                注释不应写在用星号或其他字符画出来的大框里。注释不应包括诸如制表符和回退符之类的特殊字符。
              </p>
              
              <p class="middletitle">
                <a name="51">5.1 实现注释的格式(Implementation Comment Formats)</a>
              </p>
              
              <p>
                程序可以有4种实现注释的风格：块(block)、单行(single-line)、尾端(trailing)和行末(end-of-line)。
              </p>
              
              <p class="middletitle">
                <a name="511">5.1.1 块注释(Block Comments)</a>
              </p>
              
              <p>
                块注释通常用于提供对文件，方法，数据结构和算法的描述。块注释被置于每个文件的开始处以及每个方法之前。它们也可以被用于其他地方，比如方法内部。在功能和方法内部的块注释应该和它们所描述的代码具有一样的缩进格式。
              </p>
              
              <p>
                块注释之首应该有一个空行，用于把块注释和代码分割开来，比如：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  /*
   * Here is a block comment.
   */
          </pre>
              
              <p>
              </p>
              
              <p>
                块注释可以以/*-开头，这样indent(1)就可以将之识别为一个代码块的开始，而不会重排它。
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  /*-
    * Here is a block comment with some very special
    * formatting that I want indent(1) to ignore.
    *
    *    one
    *        two
    *            three
    */
          </pre>
              
              <p>
              </p>
              
              <p>
                注意：如果你不使用indent(1)，就不必在代码中使用/*-，或为他人可能对你的代码运行indent(1)作让步。
              </p>
              
              <p>
                参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#52">文档注释</a>"
              </p>
              
              <p class="middletitle">
                <a name="512">5.1.2 单行注释(Single-Line Comments)</a>
              </p>
              
              <p>
                短注释可以显示在一行内，并与其后的代码具有一样的缩进层级。如果一个注释不能在一行内写完，就该采用块注释(参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#511">块注释</a>")。单行注释之前应该有一个空行。以下是一个Java代码中单行注释的例子：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  if (condition) {

    /* Handle the condition. */
    ...
  }
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="513">5.1.3 尾端注释(Trailing Comments)</a>
              </p>
              
              <p>
                极短的注释可以与它们所要描述的代码位于同一行，但是应该有足够的空白来分开代码和注释。若有多个短注释出现于大段代码中，它们应该具有相同的缩进。
              </p>
              
              <p>
                以下是一个Java代码中尾端注释的例子：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  if (a == 2) {
      return TRUE;              /* special case */
  } else {
      return isPrime(a);         /* works only for odd a */
  }
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="514">5.1.4 行末注释(End-Of-Line Comments)</a>
              </p>
              
              <p>
                注释界定符"//"，可以注释掉整行或者一行中的一部分。它一般不用于连续多行的注释文本；然而，它可以用来注释掉连续多行的代码段。以下是所有三种风格的例子：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  if (foo &gt; 1) {

      // Do a double-flip.
      ...
  }
  else {
      return false;          // Explain why here.
  }

  //if (bar &gt; 1) {
  //
  //    // Do a triple-flip.
  //    ...
  //}
  //else {
  //    return false;
  //}
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="52">5.2 文档注释(Documentation Comments)</a>
              </p>
              
              <p>
                注意：此处描述的注释格式之范例，参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#b1">Java源文件范例</a>"
              </p>
              
              <p>
                若想了解更多，参见"How to Write Doc Comments for Javadoc"，其中包含了有关文档注释标记的信息(@return, @param, @see)：
              </p>
              
              <p>
                <a href="http://java.sun.com/javadoc/writingdoccomments/index.html">http://java.sun.com/javadoc/writingdoccomments/index.html</a>
              </p>
              
              <p>
                若想了解更多有关文档注释和javadoc的详细资料，参见javadoc的主页：
              </p>
              
              <p>
                <a href="http://java.sun.com/javadoc/index.html">http://java.sun.com/javadoc/index.html</a>
              </p>
              
              <p>
                文档注释描述Java的类、接口、构造器，方法，以及字段(field)。每个文档注释都会被置于注释定界符/**&#8230;*/之中，一个注释对应一个类、接口或成员。该注释应位于声明之前：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  /**
    * The Example class provides ...
    */
  public class Example { ...
          </pre>
              
              <p>
              </p>
              
              <p>
                注意顶层(top-level)的类和接口是不缩进的，而其成员是缩进的。描述类和接口的文档注释的第一行(/**)不需缩进；随后的文档注释每行都缩进1格(使星号纵向对齐)。成员，包括构造函数在内，其文档注释的第一行缩进4格，随后每行都缩进5格。
              </p>
              
              <p>
                若你想给出有关类、接口、变量或方法的信息，而这些信息又不适合写在文档中，则可使用实现块注释(见5.1.1)或紧跟在声明后面的单行注释(见5.1.2)。例如，有关一个类实现的细节，应放入紧跟在类声明后面的实现块注释中，而不是放在文档注释中。
              </p>
              
              <p>
                文档注释不能放在一个方法或构造器的定义块中，因为Java会将位于文档注释之后的第一个声明与其相关联。
              </p>
              
              <p class="middletitle">
                <a name="6">6 声明(Declarations)</a>
              </p>
              
              <p class="middletitle">
                <a name="61">6.1 每行声明变量的数量(Number Per Line)</a>
              </p>
              
              <p>
                推荐一行一个声明，因为这样以利于写注释。亦即，
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  int level;  // indentation level
  int size;   // size of table
          </pre>
              
              <p>
              </p>
              
              <p>
                要优于，
              </p>
              
              <p>
                int level, size;
              </p>
              
              <p>
                不要将不同类型变量的声明放在同一行，例如：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  int foo,  fooarray[];   //WRONG!
          </pre>
              
              <p>
              </p>
              
              <p>
                注意：上面的例子中，在类型和标识符之间放了一个空格，另一种被允许的替代方式是使用制表符：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  int               level;         // indentation level
  int           size;          // size of table
  Object        currentEntry;  // currently selected table entry
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="62">6.2 初始化(Initialization)</a>
              </p>
              
              <p>
                尽量在声明局部变量的同时初始化。唯一不这么做的理由是变量的初始值依赖于某些先前发生的计算。
              </p>
              
              <p class="middletitle">
                <a name="63">6.3 布局(Placement)</a>
              </p>
              
              <p>
                只在代码块的开始处声明变量。（一个块是指任何被包含在大括号"{"和"}"中间的代码。）不要在首次用到该变量时才声明之。这会把注意力不集中的程序员搞糊涂，同时会妨碍代码在该作用域内的可移植性。
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  void myMethod() {
      int int1 = 0;         // beginning of method block

      if (condition) {
          int int2 = 0;     // beginning of "if" block
          ...
      }
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                该规则的一个例外是for循环的索引变量
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  for (int i = 0; i &lt; maxLoops; i++) { ... }
          </pre>
              
              <p>
              </p>
              
              <p>
                避免声明的局部变量覆盖上一级声明的变量。例如，不要在内部代码块中声明相同的变量名：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  int count;
  ...
  myMethod() {
      if (condition) {
          int count = 0;     // AVOID!
          ...
      }
      ...
  }
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="64">6.4 类和接口的声明(Class and Interface Declarations)</a>
              </p>
              
              <p>
                当编写类和接口是，应该遵守以下格式规则：
              </p>
              
              <p>
                &#8211; 在方法名与其参数列表之前的左括号"("间不要有空格<br /> <br />&#8211; 左大括号"{"位于声明语句同行的末尾
              </p>
              
              <p>
                &#8211; 右大括号"}"另起一行，与相应的声明语句对齐，除非是一个空语句，"}"应紧跟在"{"之后
              </p>
              
              <pre xml:space="preserve">  class Sample extends Object {
      int ivar1;
      int ivar2;

      Sample(int i, int j) {
          ivar1 = i;
          ivar2 = j;
      }

      int emptyMethod() {}

      ...
  }
          </pre>
              
              <p>
                &#8211; 方法与方法之间以空行分隔
              </p>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="7">7 语句(Statements)</a>
              </p>
              
              <p class="middletitle">
                <a name="71">7.1 简单语句(Simple Statements)</a>
              </p>
              
              <p>
                每行至多包含一条语句，例如：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  argv++;       // Correct
  argc--;       // Correct
  argv++; argc--;       // AVOID!
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="72">7.2 复合语句(Compound Statements)</a>
              </p>
              
              <p>
                复合语句是包含在大括号中的语句序列，形如"{ 语句 }"。例如下面各段。
              </p>
              
              <p>
                &#8211; 被括其中的语句应该较之复合语句缩进一个层次<br /> <br />&#8211; 左大括号"{"应位于复合语句起始行的行尾；右大括号"}"应另起一行并与复合语句首行对齐。
              </p>
              
              <p>
                &#8211; 大括号可以被用于所有语句，包括单个语句，只要这些语句是诸如if-else或for控制结构的一部分。这样便于添加语句而无需担心由于忘了加括号而引入bug。
              </p>
              
              <p class="middletitle">
                <a name="73">7.3 返回语句(return Statements)</a>
              </p>
              
              <p>
                一个带返回值的return语句不使用小括号"()"，除非它们以某种方式使返回值更为显见。例如：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  return;

  return myDisk.size();

  return (size ? size : defaultSize);
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="74">7.4 if，if-else，if else-if else语句(if, if-else, if else-if else Statements)</a>
              </p>
              
              <p>
                if-else语句应该具有如下格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  if (condition) {
      statements;
  }

  if (condition) {
      statements;
  } else {
      statements;
  }

  if (condition) {
      statements;
  } else if (condition) {
      statements;
  } else{
      statements;
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                注意：if语句总是用"{"和"}"括起来，避免使用如下容易引起错误的格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  if (condition) //AVOID! THIS OMITS THE BRACES {}!
      statement;
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="75">7.5 for语句(for Statements)</a>
              </p>
              
              <p>
                一个for语句应该具有如下格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  for (initialization; condition; update) {
      statements;
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                一个空的for语句(所有工作都在初始化，条件判断，更新子句中完成）应该具有如下格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  for (initialization; condition; update);
          </pre>
              
              <p>
              </p>
              
              <p>
                当在for语句的初始化或更新子句中使用逗号时，避免因使用三个以上变量，而导致复杂度提高。若需要，可以在for循环之前(为初始化子句)或for循环末尾(为更新子句)使用单独的语句。
              </p>
              
              <p class="middletitle">
                <a name="76">7.6 while语句(while Statements)</a>
              </p>
              
              <p>
                一个while语句应该具有如下格式
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  while (condition) {
      statements;
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                一个空的while语句应该具有如下格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  while (condition);
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="77">7.7 do-while语句(do-while Statements)</a>
              </p>
              
              <p>
                一个do-while语句应该具有如下格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  do {
      statements;
  } while (condition);
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="78">7.8 switch语句(switch Statements)</a>
              </p>
              
              <p>
                一个switch语句应该具有如下格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  switch (condition) {
  case ABC:
      statements;
      /* falls through */
  case DEF:
      statements;
      break;

  case XYZ:
      statements;
      break;

  default:
      statements;
      break;
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                每当一个case顺着往下执行时(因为没有break语句)，通常应在break语句的位置添加注释。上面的示例代码中就包含注释/* falls through */。
              </p>
              
              <p class="middletitle">
                <a name="79">7.9 try-catch语句(try-catch Statements)</a>
              </p>
              
              <p>
                一个try-catch语句应该具有如下格式：
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  try {
      statements;
  } catch (ExceptionClass e) {
      statements;
  }
          </pre>
              
              <p>
              </p>
              
              <p>
                一个try-catch语句后面也可能跟着一个finally语句，不论try代码块是否顺利执行完，它都会被执行。
              </p>
              
              <p>
              </p>
              
              <pre xml:space="preserve">  try {
      statements;
  } catch (ExceptionClass e) {
      statements;
  } finally {
      statements;
  }
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="8">8 空白(White Space)</a>
              </p>
              
              <p class="middletitle">
                <a name="81">8.1 空行(Blank Lines)</a>
              </p>
              
              <p>
                空行将逻辑相关的代码段分隔开，以提高可读性。
              </p>
              
              <p>
                下列情况应该总是使用两个空行：
              </p>
              
              <p>
                &#8211; 一个源文件的两个片段(section)之间<br /> <br />&#8211; 类声明和接口声明之间
              </p>
              
              <p>
                下列情况应该总是使用一个空行：
              </p>
              
              <p>
                &#8211; 两个方法之间<br /> <br />&#8211; 方法内的局部变量和方法的第一条语句之间
              </p>
              
              <p>
                &#8211; 块注释（参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#511">5.1.1</a>"）或单行注释（参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#512">5.1.2</a>"）之前
              </p>
              
              <p>
                &#8211; 一个方法内的两个逻辑段之间，用以提高可读性
              </p>
              
              <p class="middletitle">
                <a name="82">8.2 空格(Blank Spaces)</a>
              </p>
              
              <p>
                下列情况应该使用空格：
              </p>
              
              <p>
                &#8211; 一个紧跟着括号的关键字应该被空格分开，例如：<br />
              </p>
              
              <pre xml:space="preserve">  while (true) {
      ...
  }
          </pre>
              
              <p>
                注意：空格不应该置于方法名与其左括号之间。这将有助于区分关键字和方法调用。
              </p>
              
              <p>
                &#8211; 空白应该位于参数列表中逗号的后面
              </p>
              
              <p>
                &#8211; 所有的二元运算符，除了"."，应该使用空格将之与操作数分开。一元操作符和操作数之间不因该加空格，比如：负号("-")、自增("++")和自减("&#8211;")。例如：
              </p>
              
              <pre xml:space="preserve">    a += c + d;
    a = (a + b) / (c * d);

    while (d++ = s++) {
        n++;
    }
    printSize("size is " + foo + "\n");
          </pre>
              
              <p>
                &#8211; for语句中的表达式应该被空格分开，例如：
              </p>
              
              <pre xml:space="preserve">    for (expr1; expr2; expr3)
          </pre>
              
              <p>
                &#8211; 强制转型后应该跟一个空格，例如：
              </p>
              
              <pre xml:space="preserve">    myMethod((byte) aNum, (Object) x);
    myMethod((int) (cp + 5), ((int) (i + 3)) + 1);
          </pre>
              
              <p>
              </p>
              
              <p class="middletitle">
                <a name="9">9 命名规范(Naming Conventions)</a>
              </p>
              
              <p>
                命名规范使程序更易读，从而更易于理解。它们也可以提供一些有关标识符功能的信息，以助于理解代码，例如，不论它是一个常量，包，还是类。
              </p>
              
              <table border="1">
                <tr>
                  <td>
                    标识符类型
                  </td>
                  
                  <td>
                    命名规则
                  </td>
                  
                  <td>
                    例子
                  </td>
                </tr>
                
                <tr>
                  <td>
                    包(Packages)
                  </td>
                  
                  <td>
                    一个唯一包名的前缀总是全部小写的ASCII字母并且是一个顶级域名，通常是com，edu，gov，mil，net，org，或1981年ISO 3166标准所指定的标识国家的英文双字符代码。包名的后续部分根据不同机构各自内部的命名规范而不尽相同。这类命名规范可能以特定目录名的组成来区分部门(department)，项目(project)，机器(machine)，或注册名(login names)。
                  </td>
                  
                  <td>
                    com.sun.eng<br /> <br />com.apple.quicktime.v2 </p> 
                    
                    <p>
                      edu.cmu.cs.bovik.cheese</td> </tr> 
                      
                      <tr>
                        <td>
                          类(Classes)
                        </td>
                        
                        <td>
                          命名规则：类名是个一名词，采用大小写混合的方式，每个单词的首字母大写。尽量使你的类名简洁而富于描述。使用完整单词，避免缩写词(除非该缩写词被更广泛使用，像URL，HTML)
                        </td>
                        
                        <td>
                          class Raster;<br /> <br />class ImageSprite;
                        </td>
                      </tr>
                      
                      <tr>
                        <td>
                          接口(Interfaces)
                        </td>
                        
                        <td>
                          命名规则：大小写规则与类名相似
                        </td>
                        
                        <td>
                          interface RasterDelegate;<br /> <br />interface Storing;
                        </td>
                      </tr>
                      
                      <tr>
                        <td>
                          方法(Methods)
                        </td>
                        
                        <td>
                          方法名是一个动词，采用大小写混合的方式，第一个单词的首字母小写，其后单词的首字母大写。
                        </td>
                        
                        <td>
                          run();<br /> <br />runFast(); </p> 
                          
                          <p>
                            getBackground();</td> </tr> 
                            
                            <tr>
                              <td>
                                变量(Variables)
                              </td>
                              
                              <td>
                                除了变量名外，所有实例，包括类，类常量，均采用大小写混合的方式，第一个单词的首字母小写，其后单词的首字母大写。变量名不应以下划线或美元符号开头，尽管这在语法上是允许的。<br /> <br />变量名应简短且富于描述。变量名的选用应该易于记忆，即，能够指出其用途。尽量避免单个字符的变量名，除非是一次性的临时变量。临时变量通常被取名为i，j，k，m和n，它们一般用于整型；c，d，e，它们一般用于字符型。
                              </td>
                              
                              <td>
                                char c;<br /> <br />int i; </p> 
                                
                                <p>
                                  float myWidth;</td> </tr> 
                                  
                                  <tr>
                                    <td>
                                      实例变量(Instance Variables)
                                    </td>
                                    
                                    <td>
                                      大小写规则和变量名相似，除了前面需要一个下划线
                                    </td>
                                    
                                    <td>
                                      int _employeeId;<br /> <br />String _name; </p> 
                                      
                                      <p>
                                        Customer _customer;</td> </tr> 
                                        
                                        <tr>
                                          <td>
                                            常量(Constants)
                                          </td>
                                          
                                          <td>
                                            类常量和ANSI常量的声明，应该全部大写，单词间用下划线隔开。(尽量避免ANSI常量，容易引起错误)
                                          </td>
                                          
                                          <td>
                                            static final int MIN_WIDTH = 4;<br /> <br />static final int MAX_WIDTH = 999; </p> 
                                            
                                            <p>
                                              static final int GET_THE_CPU = 1;</td> </tr> </tbody> </table> 
                                              
                                              <p class="middletitle">
                                                <a id="a" name="a">10 编程惯例(Programming Practices)</a>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a1" name="a1">10.1 提供对实例以及类变量的访问控制(Providing Access to Instance and Class Variables)</a>
                                              </p>
                                              
                                              <p>
                                                若没有足够理由，不要把实例或类变量声明为公有。通常，实例变量无需显式的设置(set)和获取(gotten)，通常这作为方法调用的边缘效应 (side effect)而产生。
                                              </p>
                                              
                                              <p>
                                                一个具有公有实例变量的恰当例子，是类仅作为数据结构，没有行为。亦即，若你要使用一个结构(struct)而非一个类(如果java支持结构的话)，那么把类的实例变量声明为公有是合适的。
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a2" name="a2">10.2 引用类变量和类方法(Referring to Class Variables and Methods)</a>
                                              </p>
                                              
                                              <p>
                                                避免用一个对象访问一个类的静态变量和方法。应该用类名替代。例如：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  classMethod();             //OK
  AClass.classMethod();      //OK
  anObject.classMethod();    //AVOID!
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a3" name="a3">10.3 常量(Constants)</a>
                                              </p>
                                              
                                              <p>
                                                位于for循环中作为计数器值的数字常量，除了-1,0和1之外，不应被直接写入代码。
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a4" name="a4">10.4 变量赋值(Variable Assignments)</a>
                                              </p>
                                              
                                              <p>
                                                避免在一个语句中给多个变量赋相同的值。它很难读懂。例如：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  fooBar.fChar = barFoo.lchar = 'c'; // AVOID!
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p>
                                                不要将赋值运算符用在容易与相等关系运算符混淆的地方。例如：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  if (c++ = d++) {        // AVOID! (Java disallows)
      ...
  }
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p>
                                                应该写成
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  if ((c++ = d++) != 0) {
    ...
  }
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p>
                                                不要使用内嵌(embedded)赋值运算符试图提高运行时的效率，这是编译器的工作。例如：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  d = (a = b + c) + r;        // AVOID!
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p>
                                                应该写成
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  a = b + c;
  d = a + r;
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a5" name="a5">10.5 其它惯例(Miscellaneous Practices)</a>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a51" name="a51">10.5.1 圆括号(Parentheses)</a>
                                              </p>
                                              
                                              <p>
                                                一般而言，在含有多种运算符的表达式中使用圆括号来避免运算符优先级问题，是个好方法。即使运算符的优先级对你而言可能很清楚，但对其他人未必如此。你不能假设别的程序员和你一样清楚运算符的优先级。
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  if (a == b && c == d)     // AVOID!
  if ((a == b) && (c == d))  // RIGHT
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a52" name="a52">10.5.2 返回值(Returning Values)</a>
                                              </p>
                                              
                                              <p>
                                                设法让你的程序结构符合目的。例如：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  if (booleanExpression) {
      return true;
  } else {
      return false;
  }
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p>
                                                应该代之以如下方法：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  return booleanExpression;
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p>
                                                类似地：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  if (condition) {
      return x;
  }
  return y;
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p>
                                                应该写做：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  return (condition ? x : y);
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a53" name="a53">10.5.3 条件运算符"?"前的表达式(Expressions before &#8216;?&#8217; in the Conditional Operator)</a>
                                              </p>
                                              
                                              <p>
                                                如果一个包含二元运算符的表达式出现在三元运算符" ? : "的"?"之前，那么应该给表达式添上一对圆括号。例如：
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">  (x &gt;= 0) ? x : -x;
          </pre>
                                              
                                              <p>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="a54" name="a54">10.5.4 特殊注释(Special Comments)</a>
                                              </p>
                                              
                                              <p>
                                                在注释中使用XXX来标识某些未实现(bogus)的但可以工作(works)的内容。用FIXME来标识某些假的和错误的内容。
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="b" name="b">11 代码范例(Code Examples)</a>
                                              </p>
                                              
                                              <p class="middletitle">
                                                <a id="b1" name="b1">11.1 Java源文件范例(Java Source File Example)</a>
                                              </p>
                                              
                                              <p>
                                                下面的例子，展示了如何合理布局一个包含单一公共类的Java源程序。接口的布局与其相似。更多信息参见"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#313">类和接口声明</a>"以及"<a href="file:///D:/Documents%20and%20Settings/Administrator.JACKYLIU/Local%20Settings/Temp/CodeWeb/Java.mdb29.htm#52">文挡注释</a>"。
                                              </p>
                                              
                                              <p>
                                              </p>
                                              
                                              <pre xml:space="preserve">/*
 * @(#)Blah.java        1.82 99/03/18
 *
 * Copyright (c) 1994-1999 Sun Microsystems, Inc.
 * 901 San Antonio Road, Palo Alto, California, 94303, U.S.A.
 * All rights reserved.
 *
 * This software is the confidential and proprietary information of Sun
 * Microsystems, Inc. ("Confidential Information").  You shall not
 * disclose such Confidential Information and shall use it only in
 * accordance with the terms of the license agreement you entered into
 * with Sun.
 */


package java.blah;

import java.blah.blahdy.BlahBlah;

/**
 * Class description goes here.
 *
 * @version     1.82 18 Mar 1999
 * @author      Firstname Lastname
 */
public class Blah extends SomeClass {
    /* A class implementation comment can go here. */

    /** classVar1 documentation comment */
    public static int classVar1;

    /**
     * classVar2 documentation comment that happens to be
     * more than one line long
     */
    private static Object classVar2;

    /** instanceVar1 documentation comment */
    public Object instanceVar1;

    /** instanceVar2 documentation comment */
    protected int instanceVar2;

    /** instanceVar3 documentation comment */
    private Object[] instanceVar3;

    /**
     * ...constructor Blah documentation comment...
     */
    public Blah() {
        // ...implementation goes here...
    }

    /**
     * ...method doSomething documentation comment...
     */
    public void doSomething() {
        // ...implementation goes here...
    }

    /**
     * ...method doSomethingElse documentation comment...
     * @param someParam description
     */
    public void doSomethingElse(Object someParam) {
        // ...implementation goes here...
    }
}</pre></td> </tr> </tbody> </table> 
                                              
                                              <p>
                                                </center></td> </tr> </tbody> </table> 
                                                
                                                <p>
                                                  转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/01/20/java%e8%af%ad%e8%a8%80%e7%bc%96%e7%a0%81%e8%a7%84%e8%8c%83java-code-conventions/">Java语言编码规范(Java Code Conventions)</a>
                                                </p>