---
id: 2224
title: 使用WLST创建和删除DataSource
date: 2011-08-29T20:13:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2224
permalink: '/2011/08/29/%e4%bd%bf%e7%94%a8wlst%e5%88%9b%e5%bb%ba%e5%92%8c%e5%88%a0%e9%99%a4datasource/'
views:
  - "4468"
original_post_id:
  - "2224"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - WLST
---
File 1: **datasource.properties**

<font face="Consolas" size="2">dsname=testpool <br />server=AdminServer <br />testTableName=SQL SELECT 1 FROM DUAL <br /></font><font face="Consolas" size="2">#testTableName=jndi=jdbc/oracle <br />driver=oracle.jdbc.driver.OracleDriver <br />url=jdbc:oracle:thin:@localhost:1521:ORCL <br />userid=xxxx <br />password=xxxx <br />maxCapacity=9</font>

File 2: **createDatasource.py**

&#160;

<font face="Consolas">""" <br />This script configures a JDBC data source as a System Module and deploys it <br />to the server <br />""" <br />connect("weblogic","weblogic") <br />edit() </font>

<font face="Consolas"># Load config params <br />from java.io import FileInputStream </font>

<font face="Consolas">propInputStream = FileInputStream("datasource.properties") <br />configProps = Properties() <br />configProps.load(propInputStream) <br />propInputStream.close() <br /># Init vars <br />dsname=configProps.get("dsname") <br />server=configProps.get("server") <br />testTableName=configProps.get("testTableName") <br />jndi=configProps.get("jndi") <br />maxCapacity=Integer.parseInt(configProps.get("maxCapacity")) <br />url=configProps.get("url") <br />driver=configProps.get("driver") <br />userid=configProps.get("userid") <br />password=configProps.get("password") </font>

<font face="Consolas">cd("Servers/"+server) <br />target=cmo <br />cd("../..") </font>

<font face="Consolas">try: <br />&#160;&#160;&#160; startEdit() <br />&#160;&#160;&#160; # start creation <br />&#160;&#160;&#160; print &#8216;Creating JDBCSystemResource with name &#8216;+dsname <br />&#160;&#160;&#160; jdbcSR = create(dsname,"JDBCSystemResource") <br />&#160;&#160;&#160; theJDBCResource = jdbcSR.getJDBCResource() <br />&#160;&#160;&#160; theJDBCResource.setName(dsname) <br />&#160;&#160;&#160; connectionPoolParams = theJDBCResource.getJDBCConnectionPoolParams() <br />&#160;&#160;&#160; connectionPoolParams.setInactiveConnectionTimeoutSeconds(60) <br />&#160;&#160;&#160; connectionPoolParams.setMaxCapacity(maxCapacity) <br />&#160;&#160;&#160; connectionPoolParams.setTestTableName(testTableName) <br />&#160;&#160;&#160; dsParams = theJDBCResource.getJDBCDataSourceParams() <br />&#160;&#160;&#160; dsParams.addJNDIName(jndi) <br />&#160;&#160;&#160; driverParams = theJDBCResource.getJDBCDriverParams() <br />&#160;&#160;&#160; driverParams.setUrl(url) <br />&#160;&#160;&#160; driverParams.setDriverName(driver) <br />&#160;&#160;&#160; driverParams.setPassword(password) <br />&#160;&#160;&#160; # driverParams.setLoginDelaySeconds(60) <br />&#160;&#160;&#160; driverProperties = driverParams.getProperties() <br />&#160;&#160;&#160; proper = driverProperties.createProperty("user") <br />&#160;&#160;&#160; #proper.setName("user") <br />&#160;&#160;&#160; proper.setValue(userid) <br />&#160;&#160;&#160; jdbcSR.addTarget(target) <br />&#160;&#160;&#160; save() <br />&#160;&#160;&#160; activate(block="true") <br />&#160;&#160;&#160; print &#8216;Done configuring the data source of &#8216; + dsname </font>

<font face="Consolas">except: <br />&#160;&#160;&#160; print &#8216;Failed to configuring the data source of &#8216; + dsname; <br />&#160;&#160;&#160; cancelEdit(&#8216;y&#8217;); <br />&#160;&#160;&#160; #undo(&#8216;true&#8217;, &#8216;y&#8217;); <br />disconnect();</font>

<font face="Consolas"></font>

<font face="Consolas"><strong>删除 DataSource:</strong></font>

try:   
&#160;&#160;&#160; connect("weblogic", "weblogic", "t3://localhost:7001")   
&#160;&#160;&#160; edit()   
&#160;&#160;&#160; startEdit()   
&#160;&#160;&#160; delete(&#8216;testpool&#8217;,&#8217;JDBCSystemResource&#8217;)   
&#160;&#160;&#160; activate()   
&#160;&#160;&#160; print "Done deleting a datasource &#8211; " + dsname   
&#160;&#160;&#160; disconnect();   
except Exception:   
&#160;&#160;&#160; print "Error: Caught exception in delDataSource(). Exiting!"   
&#160;&#160;&#160; dumpStack()

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [使用WLST创建和删除DataSource](http://www.beansoft.biz/2011/08/29/%e4%bd%bf%e7%94%a8wlst%e5%88%9b%e5%bb%ba%e5%92%8c%e5%88%a0%e9%99%a4datasource/)