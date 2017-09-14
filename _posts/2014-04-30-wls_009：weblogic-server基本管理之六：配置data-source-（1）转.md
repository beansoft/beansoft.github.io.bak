---
id: 3645
title: 'WLS_009：WebLogic Server基本管理之六：配置Data Source （1）[转]'
date: 2014-04-30T18:05:29+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3645
permalink: '/2014/04/30/wls_009%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e5%85%ad%ef%bc%9a%e9%85%8d%e7%bd%aedata-source-%ef%bc%881%ef%bc%89%e8%bd%ac/'
views:
  - "3238"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
来源: [http://maping930883.blogspot.jp/2009/03/wls009weblogic-serverdata-source.html](http://maping930883.blogspot.jp/2009/03/wls009weblogic-serverdata-source.html "http://maping930883.blogspot.jp/2009/03/wls009weblogic-serverdata-source.html")

[domain_name]-> Services-> JDBC-> Data Sources   
Data Source的作用是从数据库连接池中获取数据库连接，使用完毕后，再放回数据库连接池。   
[<img border="0" alt="" src="http://2.bp.blogspot.com/-rlCMasDSiJA/TtwV4W8ec4I/AAAAAAAACQ8/guxx9seWaY0/s400/WLS_Admin_DS.gif" />](http://2.bp.blogspot.com/-rlCMasDSiJA/TtwV4W8ec4I/AAAAAAAACQ8/guxx9seWaY0/s1600/WLS_Admin_DS.gif)   
**1. 配置DataSource：pointbase数据库**   
[<img border="0" alt="" src="http://4.bp.blogspot.com/-wM5ZRyMxxnM/TggednNbZ0I/AAAAAAAABYs/VEdMedcXKwg/s400/WLS_Admin_DS_1.gif" />](http://4.bp.blogspot.com/-wM5ZRyMxxnM/TggednNbZ0I/AAAAAAAABYs/VEdMedcXKwg/s1600/WLS_Admin_DS_1.gif)   
[<img border="0" alt="" src="http://3.bp.blogspot.com/-LdXQk_IBkL0/Tggeh0lh69I/AAAAAAAABY0/9jVRJ0oqGw4/s400/WLS_Admin_DS_2.gif" />](http://3.bp.blogspot.com/-LdXQk_IBkL0/Tggeh0lh69I/AAAAAAAABY0/9jVRJ0oqGw4/s1600/WLS_Admin_DS_2.gif)   
配置成功后，应该能在DataSource所target的Server上的JNDI Tree中，能看到DataSource的JNDI值。   
[<img border="0" alt="" src="http://1.bp.blogspot.com/-QCK9qreAhAY/TggguIkePsI/AAAAAAAABY8/irGnm0ddm5U/s400/WLS_Admin_DS_3.gif" />](http://1.bp.blogspot.com/-QCK9qreAhAY/TggguIkePsI/AAAAAAAABY8/irGnm0ddm5U/s1600/WLS_Admin_DS_3.gif)   
**2. 在testdatasource.jsp中访问DataSource，获取数据库连接。**

<pre><strong>
&lt;HTML&gt;
&lt;HEAD&gt;&lt;TITLE&gt;Testing Connection Pools&lt;/TITLE&gt;&lt;/HEAD&gt;

&lt;BODY&gt;

&lt;%@ page import="java.sql.*,javax.naming.*,javax.sql.*" %&gt;
&lt;FONT SIZE="5" COLOR="navy"&gt;
&lt;table&gt;
&lt;tr&gt;&lt;td align="left"&gt;&lt;%@ include file="pages/includes/DWRHeader1.jspf" %&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;tr&gt;&lt;td&gt;&lt;CENTER&gt;&lt;b&gt;Dizzyworld Testing Center&lt;/b&gt;&lt;/CENTER&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;/table&gt;

&lt;FORM NAME="testCP" ACTION="testdatasource.jsp" METHOD="POST"&gt;
&lt;TABLE WIDTH="50%" ALIGN="left" BGCOLOR="silver"&gt;
 &lt;TR&gt;&lt;TD ALIGN="right" WIDTH="50%"&gt;Data Source Name&lt;/TD&gt;
  &lt;TD WIDTH="50%"&gt;&lt;INPUT TYPE="text" NAME="txtDataSource" VALUE="dizzyworldDS"&gt;&lt;/TD&gt;
 &lt;/TR&gt;
 &lt;TR&gt;&lt;TD ALIGN="right"&gt;Table Name&lt;/TD&gt;
  &lt;TD&gt;&lt;INPUT TYPE="text" NAME="txtTableName" VALUE="EMPLOYEE"&gt;&lt;/TD&gt;
 &lt;/TR&gt;
 &lt;TR&gt;&lt;TD ALIGN="right"&gt;Username&lt;/TD&gt;
  &lt;TD&gt;&lt;INPUT TYPE="text" NAME="txtUsername" VALUE="system"&gt;&lt;/TD&gt;
 &lt;/TR&gt;
 &lt;TR&gt;&lt;TD ALIGN="right"&gt;Password&lt;/TD&gt;
  &lt;TD&gt;&lt;INPUT TYPE="text" NAME="txtPassword" VALUE="weblogic"&gt;&lt;/TD&gt;
 &lt;/TR&gt;
 &lt;TR&gt;&lt;TD ALIGN="center" COLSPAN="2"&gt;
   &lt;INPUT TYPE="submit" NAME="btnSubmit" VALUE="Test Data Source"&gt;
  &lt;/TD&gt;
 &lt;/TR&gt;
 
&lt;/TABLE&gt;
&lt;/FORM&gt;

&lt;%
 String datasource = request.getParameter("txtDataSource");
 String table = request.getParameter("txtTableName");
 String username = request.getParameter("txtUsername");
 String password = request.getParameter("txtPassword");

 if ((datasource != null) && (!datasource.equals(""))) {
  if ((table != null) && (!table.equals(""))) {
   try {

    InitialContext ic = new InitialContext();
    DataSource ds = (DataSource) ic.lookup(datasource);
    System.out.println("Looking up the " + datasource + " data source.");
    Connection connection = ds.getConnection(username, password);
    System.out.println("Getting the connection from the database.");

    Statement statement = connection.createStatement();
    String sql = "SELECT * FROM " + table;

    ResultSet rs = statement.executeQuery(sql);
    System.out.println("Querying the database.");
    ResultSetMetaData meta = rs.getMetaData();
    int numColumns = meta.getColumnCount();
%&gt;
    
    &lt;BR&gt;
    &lt;BR&gt;
    &lt;BR&gt;
    &lt;BR&gt;
    &lt;BR&gt;
    &lt;BR&gt;
    &lt;p&gt;
    &lt;TABLE WIDTH="670" BGCOLOR="wheat" ALIGN="left"&gt;
    
&lt;%
    out.print("&lt;TR&gt;");
    for (int j=1; j&lt;numColumns; j++) {
     out.print("&lt;TD&gt;" + meta.getColumnName(j) + "&lt;/TD&gt;");
    }
    out.print("&lt;/TR&gt;");
    while (rs.next()) {
     out.print("&lt;TR&gt;");
     for (int i=1; i&lt;numColumns; i++) {
      out.print("&lt;TD&gt;" + rs.getString(i) + "&lt;/TD&gt;");
     }
     out.print("&lt;/TR&gt;");
    }
%&gt;
    &lt;/TABLE&gt;
    &lt;/p&gt;
&lt;%
    if (statement != null)
     statement.close();
    if (connection != null)
     connection.close();

   } catch (SQLException sqle) {
%&gt;

    &lt;/FONT&gt;&lt;FONT SIZE="4" COLOR="navy"&gt;
    Error: &lt;%= sqle.getMessage() %&gt;&lt;BR&gt;&lt;BR&gt;
&lt;%
   }catch (Exception e) {out.print("error: " + e); }

  }
 }

%&gt;
&lt;/FONT&gt;

&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;BR&gt;
&lt;p&gt;
&lt;%@ include file="pages/includes/DWRFooter1.jspf" %&gt;&lt;/td&gt;&lt;/tr&gt;
&lt;/p&gt;

&lt;/BODY&gt;
&lt;/HTML&gt;</strong></pre>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WLS_009：WebLogic Server基本管理之六：配置Data Source （1）[转]](http://www.beansoft.biz/2014/04/30/wls_009%ef%bc%9aweblogic-server%e5%9f%ba%e6%9c%ac%e7%ae%a1%e7%90%86%e4%b9%8b%e5%85%ad%ef%bc%9a%e9%85%8d%e7%bd%aedata-source-%ef%bc%881%ef%bc%89%e8%bd%ac/)