---
id: 1716
title: 讨论：JDBC连接Oracle 10g 出错的问题及其解决
date: 2011-02-12T19:51:50+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1716
permalink: '/2011/02/12/%e8%ae%a8%e8%ae%ba%ef%bc%9ajdbc%e8%bf%9e%e6%8e%a5oracle-10g-%e5%87%ba%e9%94%99%e7%9a%84%e9%97%ae%e9%a2%98%e5%8f%8a%e5%85%b6%e8%a7%a3%e5%86%b3/'
views:
  - "8012"
original_post_id:
  - "1716"
image: /wp-content/uploads/2012/09/image_thumb19.png
categories:
  - Oracle
---
最近好多网友询问 MyEclipse 连接 Oracle 10g 的连接问题，因为电脑没来得及装Oracle 10g，但是我装的是Oracle 10g Express，我想应该差不多吧。

核心提示：

**MyEclipse Database Explorer 连接使用 Oracle 10g 或者 9i 中提供的 classes12.jar 即可。**

**普通Java开发使用 ojdbc14.jar 即可。**

**仅测试过 Oracle 10g Express，期待得到Oracle 10g正式版证实。**

****&#160;

初步试了一下，发现如下情况：

驱动程序使用的是 C:oraclexeapporacleproduct10.2.0serverjdbclibojdbc14.jar

有个官方的说明文件 C:oraclexeapporacleproduct10.2.0serverjdbcReadme.txt 里面提到支持 Java 5，以下是文档中的部分说明：

> Oracle JDBC Drivers release 10.2.0.1.0 production (10g R2) README   
> ===================================================== 
> 
> What Is New In This Release ?   
> &#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8212;&#8211; 
> 
> Support for J2SE 5.0   
> &#160;&#160;&#160; J2SE 5.0 (AKA J2SE 1.5 and Tiger) is fully supported. 5.0 supports   
> &#160;&#160;&#160; JDBC 3.0, the same as J2SE 1.4, so there are no additional   
> &#160;&#160;&#160; standard JDBC features. Prior to this release J2SE 5.0 was not   
> &#160;&#160;&#160; officially supported. 
> 
> These are a few simple things that you should do in your JDBC program: 
> 
> 1. Import the necessary JDBC classes in your programs that use JDBC.   
> &#160;&#160;&#160; For example: 
> 
> &#160;&#160;&#160;&#160;&#160; import java.sql.*;   
> &#160;&#160;&#160;&#160;&#160; import java.math.*; // if needed 
> 
> &#160;&#160;&#160; To use OracleDataSource, you need to do:   
> &#160;&#160;&#160;&#160;&#160; import oracle.jdbc.pool.OracleDataSource; 
> 
> 2. Create an OracleDataSource instance. 
> 
> &#160;&#160;&#160;&#160;&#160; OracleDataSource ods = new OracleDataSource(); 
> 
> 3. set the desired properties if you don&#8217;t want to use the   
> &#160;&#160;&#160; default properties. Different connection URLs should be   
> &#160;&#160;&#160; used for different JDBC drivers. 
> 
> &#160;&#160;&#160;&#160;&#160; ods.setUser("my_user");   
> &#160;&#160;&#160;&#160;&#160; ods.setPassword("my_password"); 
> 
> &#160;&#160;&#160; For the JDBC OCI Driver:   
> &#160;&#160;&#160;&#160;&#160; To make a bequeath connection, set URL as:   
> &#160;&#160;&#160;&#160;&#160; ods.setURL("jdbc:oracle:oci:@"); 
> 
> &#160;&#160;&#160;&#160;&#160; To make a remote connection, set URL as:   
> &#160;&#160;&#160;&#160;&#160; ods.setURL("jdbc:oracle:oci:@<database>"); 
> 
> &#160;&#160;&#160;&#160;&#160; where <database> is either a TNSEntryName   
> &#160;&#160;&#160;&#160;&#160; or a SQL*net name-value pair defined in tnsnames.ora.   
> &#160;&#160;&#160; For the JDBC Thin Driver, or Server-side Thin Driver:   
> &#160;&#160;&#160;&#160;&#160; ods.setURL("jdbc:oracle:thin:@<database>"); 
> 
> &#160;&#160;&#160;&#160;&#160; where <database> is either a string of the form   
> &#160;&#160;&#160;&#160;&#160; //<host>:<port>/<service_name>, or a SQL*net name-value pair,   
> &#160;&#160;&#160;&#160;&#160; or a TNSEntryName. 
> 
> &#160;&#160;&#160; For the JDBC Server-side Internal Driver:   
> &#160;&#160;&#160;&#160;&#160; ods.setURL("jdbc:oracle:kprb:"); 
> 
> &#160;&#160;&#160;&#160;&#160; Note that the trailing &#8216;:&#8217; is necessary. When you use the   
> &#160;&#160;&#160;&#160;&#160; Server-side Internal Driver, you always connect to the   
> &#160;&#160;&#160;&#160;&#160; database you are executing in. You can also do this: 
> 
> &#160;&#160;&#160;&#160;&#160; Connection conn =   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; new oracle.jdbc.OracleDriver().defaultConnection(); 
> 
> 4. Open a connection to the database with getConnection()   
> &#160;&#160;&#160; methods defined in OracleDataSource class. 
> 
> &#160;&#160;&#160;&#160;&#160; Connection conn = ods.getConnection(); 
> 
> &#160;

下面是我的简装版 Oracle 启动的服务：

[<img height="86" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/02/image_thumb.png" width="537" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/02/image.png) 

为了保险，我用的是这个新版本的驱动，然后我在管理器中启用了HR这个账户（密码是hr)：

[<img height="342" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/02/image_thumb1.png" width="601" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/02/image1.png) 

然后使用一款名为 DbVisualizer 的工具访问数据，使用 JDK 1.4 和 JDK 1.6来连接都没有问题，唯独没测试 JDK 1.5.

[<img height="322" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/02/image_thumb2.png" width="481" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/02/image2.png) 

[<img height="388" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/02/image_thumb3.png" width="617" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/02/image3.png) 

可以看到数据，很好。

下面是MyEclipse中的测试，使用 Database Explorer 出了问题了：

[<img height="256" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/02/image_thumb4.png" width="525" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/02/image4.png) 

然后我用 JDK 1.5 和 MyEclipse 自带的 JRE 编写了个Java程序，运行很正常，没发现上面的那个错误信息：

[<img height="124" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/02/image_thumb5.png" width="236" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/02/image5.png) 

> import java.sql.SQLException;   
> /**   
> * 第一个 JDBC 的 HelloWorld 程序, 数据库访问 Mysql.   
> * @author Administrator   
> * @version 0.1 2007-09-26   
> */   
> public class JDBCHelloWorld { 
> 
> &#160;&#160;&#160; /**   
> &#160;&#160;&#160;&#160; * @param args   
> &#160;&#160;&#160;&#160; * @throws SQLException   
> &#160;&#160;&#160;&#160; */   
> &#160;&#160;&#160; public static void main(String[] args) throws SQLException {   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; // 1. 注册驱动 
> 
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; new oracle.jdbc.OracleDriver(); 
> 
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; // 2. 获取数据库的连接   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; java.sql.Connection conn = java.sql.DriverManager.getConnection(   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; "jdbc:oracle:thin:@localhost:1521:xe", "hr", "hr");   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; // 3. 获取表达式   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; java.sql.Statement stmt = conn.createStatement();   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; // 4. 执行 SQL   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; java.sql.ResultSet rs = stmt.executeQuery("select * from jobs");   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; // 5. 显示结果集里面的数据   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; while(rs.next()) {   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println(rs.getString(1));   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println(rs.getString(2));   
> &#160;&#16
  
> 0;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160; System.out.println();   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; }   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; // 6. 释放资源   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; rs.close();   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; stmt.close();   
> &#160;&#160;&#160;&#160;&#160;&#160;&#160; conn.close(); 
> 
> &#160;&#160;&#160; } 
> 
> } 
> 
> &#160;

输出：

> AD_PRES   
> President 
> 
> AD_VP   
> Administration Vice President 
> 
> AD_ASST   
> Administration Assistant 
> 
> FI_MGR   
> Finance Manager 
> 
> FI_ACCOUNT   
> Accountant 
> 
> AC_MGR   
> Accounting Manager 
> 
> AC_ACCOUNT   
> Public Accountant 
> 
> SA_MAN   
> Sales Manager 
> 
> SA_REP   
> Sales Representative 
> 
> PU_MAN   
> Purchasing Manager 
> 
> PU_CLERK   
> Purchasing Clerk 
> 
> ST_MAN   
> Stock Manager 
> 
> ST_CLERK   
> Stock Clerk 
> 
> SH_CLERK   
> Shipping Clerk 
> 
> IT_PROG   
> Programmer 
> 
> MK_MAN   
> Marketing Manager 
> 
> MK_REP   
> Marketing Representative 
> 
> HR_REP   
> Human Resources Representative 
> 
> PR_REP   
> Public Relations Representative 

把Eclipse换成 JDK 1.6 启动，start eclipseeclipse.exe -clean -vm C:Javajdk1.6.0_10binjavaw.exe

Database Explorer依然报错如故。

最后，Google 吧：cannot access nls data files JDBC

结果得到结果：原来换用classes12.jar就行了啊！看来还是没Google到位！

&#160;

期待试过Oracle 10g正式版的同志，给个答案！

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [讨论：JDBC连接Oracle 10g 出错的问题及其解决](http://www.beansoft.biz/2011/02/12/%e8%ae%a8%e8%ae%ba%ef%bc%9ajdbc%e8%bf%9e%e6%8e%a5oracle-10g-%e5%87%ba%e9%94%99%e7%9a%84%e9%97%ae%e9%a2%98%e5%8f%8a%e5%85%b6%e8%a7%a3%e5%86%b3/)