---
id: 654
title: JNDI 访问外部 WebLogic 11 数据源的操作步骤
date: 2010-08-31T22:00:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=654
permalink: '/2010/08/31/jndi-%e8%ae%bf%e9%97%ae%e5%a4%96%e9%83%a8-weblogic-11-%e6%95%b0%e6%8d%ae%e6%ba%90%e7%9a%84%e6%93%8d%e4%bd%9c%e6%ad%a5%e9%aa%a4/'
views:
  - "4137"
original_post_id:
  - "654"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
1. 执行文件 wljarbuilder.jar
  
cd E:beawlserver_10.3serverlib
  
java -jar wljarbuilder.jar
  
2. 复制得到的 wlfullclient.jar 到客户端项目中去, 否则无法执行数据源远程操作

相关代码:

<div id="codeSnippetWrapper">
  <div id="codeSnippet" style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;padding:0;">
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">import</span> java.sql.Connection;</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">import</span> java.sql.ResultSet;</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">import</span> java.sql.Statement;</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">import</span> java.util.Properties;</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">import</span> javax.naming.Context;</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">import</span> javax.naming.InitialContext;</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">import</span> javax.sql.DataSource;</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#008000;">/**</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#008000;"> * 使用JNDI访问数据源的测试代码.</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#008000;"> */</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"><span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> WlsJNDIDataSourceTest</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">{</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    <span style="color:#0000ff;">public</span> WlsJNDIDataSourceTest()</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    {</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        <span style="color:#0000ff;">try</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        {</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            Properties prop = <span style="color:#0000ff;">new</span> Properties();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            prop.setProperty(Context.INITIAL_CONTEXT_FACTORY,</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">                    <span style="color:#006080;">"weblogic.jndi.WLInitialContextFactory"</span>);</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            prop.setProperty(Context.PROVIDER_URL, <span style="color:#006080;">"t3://localhost:7001"</span>);</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            InitialContext initial = <span style="color:#0000ff;">new</span> InitialContext(prop);</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            DataSource dataSource = (DataSource) initial.lookup(<span style="color:#006080;">"jdbc/oracle"</span>);</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            Connection conn = dataSource.getConnection();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            Statement statement = conn.createStatement();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            ResultSet rs = statement</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">                    .executeQuery(<span style="color:#006080;">"SELECT * FROM T_USER_ENTITY"</span>);</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            <span style="color:#0000ff;">while</span> (rs.next())</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            {</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">                System.out.println(rs.getString(1));</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            }</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            <span style="color:#008000;">// realease when press a key</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            <span style="color:#008000;">// System.in.read();</span></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            rs.close();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            statement.close();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            conn.close();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        } <span style="color:#0000ff;">catch</span> (Exception ex)</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            conn.close();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        } <span style="color:#0000ff;">catch</span> (Exception ex)</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        {</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">            ex.printStackTrace();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        }</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    }</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;"></pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">static</span> <span style="color:#0000ff;">void</span> main(String[] args)</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    {</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:white;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">        <span style="color:#0000ff;">new</span> WlsJNDIDataSourceTest();</pre>
    
    <p>
      <!--CRLF-->
    </p>
    
    <pre style="text-align:left;line-height:12pt;background-color:#f4f4f4;width:100%;font-family:'Courier New', courier, monospace;direction:ltr;color:black;font-size:8pt;overflow:visible;border-style:none;margin:0;padding:0;">    }</pre>
    
    <p>
      <!--CRLF-->
      
      <br /> <pre style="text-align: left; line-height: 12pt; background-color: white; margin: 0em; width: 100%; font-family: 'Courier New', courier, monospace; direction: ltr; color:</div> </div> 
      
      <p>
        转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/08/31/jndi-%e8%ae%bf%e9%97%ae%e5%a4%96%e9%83%a8-weblogic-11-%e6%95%b0%e6%8d%ae%e6%ba%90%e7%9a%84%e6%93%8d%e4%bd%9c%e6%ad%a5%e9%aa%a4/">JNDI 访问外部 WebLogic 11 数据源的操作步骤</a>
      </p>