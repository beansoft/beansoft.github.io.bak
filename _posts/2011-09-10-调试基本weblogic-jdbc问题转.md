---
id: 2251
title: '调试基本WebLogic JDBC问题[转]'
date: 2011-09-10T21:03:31+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2251
permalink: '/2011/09/10/%e8%b0%83%e8%af%95%e5%9f%ba%e6%9c%acweblogic-jdbc%e9%97%ae%e9%a2%98%e8%bd%ac/'
views:
  - "18150"
original_post_id:
  - "2251"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Debug
  - JDBC
  - WebLogic
---
来源: [http://middlewaremagic.com/weblogic/?p=2477](http://middlewaremagic.com/weblogic/?p=2477 "http://middlewaremagic.com/weblogic/?p=2477")

22

Jul/10

#### [Debugging Basic JDBC Issues](http://middlewaremagic.com/weblogic/?p=2477)

by [JaySenSharma](http://middlewaremagic.com/weblogic/?author=1) under [Debug](http://middlewaremagic.com/weblogic/?cat=38), [JDBC](http://middlewaremagic.com/weblogic/?cat=19)

[Tweet](http://twitter.com/share)

Hi,

Jay SenSharma

Here is a Simple demonstration of Debugging Jdbc N/W Connectivity issues. Some very basic and common tools and simple Jdbc programs helps us a lot in debugging the JDBC issues.

You can also refer to the WebLogic JDBC related some very common tips: <http://middlewaremagic.com/weblogic/2010/02/10/jdbc-tips/>

#### Common Jdbc Issues-1).

If you get the following Error:

<pre>&#160;</pre>

<pre>&lt;BEA-149205&gt; &lt;Failed to initialize the application ‘TestDataSource’ due to error weblogic.application.ModuleException: .</pre>

<pre>weblogic.application.ModuleException:</pre>

<pre>at weblogic.jdbc.module.JDBCModule.prepare(JDBCModule.java:289)</pre>

<pre>at weblogic.application.internal.flow.ModuleListenerInvoker.prepare(ModuleListenerInvoker.java:93)</pre>

<pre>at weblogic.application.internal.flow.DeploymentCallbackFlow$1.next(DeploymentCallbackFlow.java:387)</pre>

<pre>.</pre>

<pre>.</pre>

<pre>weblogic.common.ResourceException: Could not create pool connection. The DBMS driver exception was: The Network Adapter could not establish the connection</pre>

<pre>- – - – - – or - – - – - -</pre>

<pre>weblogic.common.ResourceException: weblogic.common.ResourceException: Could not create pool connection. The DBMS driver exception was: Io exception: The Network Adapter</pre>

**Degugging the root Cause of above Issue:**

The Above Exception: java.io.IOException: The Network Adapter could not establish the connection

It simply suggest that the Database URL may not be correct in the DataSource XML file locatied inside “<DOMAIN_HOME>configjdbc” directoryor may be the TNS name OR some n/w issue between WLS BOX and the DB Box. Please try the following to Double Check it.

**Step1).** Add JDBC Driver also in the Classpath or Better run **“. ./setWLSEnv.sh”** 

(**NOTE:** While running the above script please use two DOTs like mentioned above. The first DOT represents that set the Environment in the Current Shell and the second DOT (./) Slash represents that pick up the Script from the current Location. Both DOTs are separated by a single space. Once u run “. ./setWLSEnv.sh” after that try to echo the values of $CLASSPATH and $PATH to make sure that the env is set properly)

**Step2).** Use WLS&#160;&#160; **dbping** utility to test the Database Network Connectivity from the WebLogic Server Box:

**Syntax:**

java -classpath /bea103/wl\_server103/server/lib/weblogic.jar utils.dbping ORACLE\_THIN <dbUserName> <dbPasswoes> <dbURL>

**Example:**

java -classpath /bea103/wl\_server103/server/lib/weblogic.jar utils.dbping ORACLE\_THIN scott tiger databaseHostName:1521:P15215h

**Step 3).** Try doing a **telnet** to connect to the Database Box on the Database Listen Port like following Just to make sure that the Database has started listening on the Mentioned Listen Port or Not …..:

**telnet&#160;&#160; databaseHostName&#160;&#160; 1521**

————————————————————————–

#### Common Jdbc Issues-2).

Many times we see that DataSource configured on WebLogic Server was running fine sometimes back and suddenly we start seeing the following Error:

<pre>&#160;</pre>

<pre>Caused by: java.sql.SQLException: Io exception: Got minus one from a read call</pre>

<pre>at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:112)</pre>

<pre>at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:146)</pre>

<pre>at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:255)</pre>

<pre>at oracle.jdbc.driver.T4CConnection.logon(T4CConnection.java:387)</pre>

<pre>at oracle.jdbc.driver.PhysicalConnection.&lt;init&gt;(PhysicalConnection.java:420)</pre>

**Degugging the root Cause of above Issue:**

The error “_Caused by: java.sql.SQLException: Io exception: Got minus one from a read call_” clearly indicates the root cause of this issue. “We get the following error “Got minus one from a read call” if the **Database goes under Maintenance…..or Database is in inconsistent State** (Due to any reason like Database Maintenance or Database unmounting…etc ).

WLS is asking a JDBC driver for a connection and getting that exception, which means the DBMS or network dropped the socket during the driver-DBMS handshake.

The above error ensures that there is Nothing Wrong from WebLogic Side …we need to contact the Database Administrator only.

**Step1).** Open the Server Log and check the timestamp of the first occurance of that Error in the Server log.

**Step2).** Confirm with the Database Administrator…. What was the activity happening on the Database side at that time (90% cases u will find that the Database might be under Maintenance that time)

#### ——-Make Use of Appropriate Debug Flags:———

**-Dweblogic.resourcepool.max\_test\_wait_secs=xx**

Where xx is the amount of time, in seconds, WebLogic Server waits for connection test before considering the connection test failed. By default, a server instance is assigned a value of 10 seconds. This command line flag manages failures, such as a DBMS network failure, which can cause connection tests and applications to hang for extended periods of time (for example, 10 minutes). If the assigned time period expires, the server instance purges and disables the pool (closes all connections and blocks further reserve attempts) and re-enables the pool as soon as it is possible to reconnect.

**You can use the following Debug Flags:**

-Dweblogic.debug.DebugJDBCSQL=true

-Dweblogic.log.StdoutSeverity=Debug

Use the Following WLST Script to Enable the JDBC related Debug Flags
    
  
**“ExampleDebugJdbc.py”**

—————————————————————–

user=’weblogic’

password=’weblogic’

url=’t3://localhost:7001′

connect(user, password, url)

edit()

cd(‘Servers/TestServer/ServerDebug/TestServer’)

startEdit()

set(‘DebugJDBCSQL’,&#8217;true’)

save()

activate()

—————————————————————–

#### Common Jdbc Issues-3).

If you see that the Database is going into **DataSource is moving to SUSPENDED/Disabled State**….The first of all check the database connectivity. If the dfatabase connectivity is OK and WLS is able to establish the Connectivity with the database Successfully then Please try to use the “weblogic.Admin” utility to Restore (Resume) the DataSource.

You can use “weblogic.Admin” utility to Enable and Disable the Pool (DataSource) Just to Confirm whether the dataSource is actually active or not:

**Step1).** run **“. ./setWLSEnv.sh”** first in the same Shell prompt….then do the following:

**Step2).** To suspend:

**java weblogic.Admin -url t3://localhost:7001 -username weblogic -password weblogic SUSPEND_POOL YourDataSourceName**

**Step3).** To re-enable:

**java weblogic.Admin -url t3://localhost:7001 -username weblogic -password weblogic RESUME_POOL YourDataSourceName**

To test whether you are getting any Exception or Error while doing this….If yes u are getting any Error or exception then It means there May be some Database connectivity issue…
    
  
If a datasource gets destroyed then even if u are having DataSource Configuration Entries in the “config.xml” and the_ **“<DOMAIN_HOME>/config/jdbc/*.xml”**_ files …still u wont be able to see that datasource in the Monitoring Tab in the AdminConsole. Because as soon as the datasource gets destroyed (Due to N/W disconnect or someother reason) the MBean Object gets destroyed.

#### Common Jdbc Issues-4).

<pre>&#160;</pre>

<pre>&lt;Warning&gt; &lt;JDBC&gt; &lt;BEA-001153&gt; &lt;Forcibly releasing inactive connection</pre>

<pre>“weblogic.jdbc.wrapper.PoolConnection_oracle_jdbc_driver_T4CConnection@3″ back into the connection pool “TestDataSource”, currently reserved by: java.lang.Exception</pre>

<pre>at weblogic.jdbc.common.internal.ConnectionEnv.setup(ConnectionEnv.java:291)</pre>

<pre>at weblogic.common.resourcepool.ResourcePoolImpl.reserveResource(ResourcePoolImpl.java:314)</pre>

<pre>at weblogic.common.resourcepool.ResourcePoolImpl.reserveResource(ResourcePoolImpl.java:292)</pre>

<pre>at weblogic.jdbc.common.internal.ConnectionPool.reserve(ConnectionPool.java:425)</pre>

<pre>at weblogic.jdbc.common.internal.ConnectionPool.reserve(ConnectionPool.java:316)</pre>

If we see above kind of exceptions in our Server Logs then definately we need to look into the Application Code.  **“That is either your application reserving and Hholding the jdbc connections (they aren’t lost means leaked), or maybe they are hanging waiting for the DBMS to respond.”**

Usually we see this Warning When the Application code obtains a JDBC connection from the WLS datasource, then not using it and not closing it, Means Just Holding the Connection Reference, for longer than your datasource/pool is configured to allow (IdleConnectionTimeout). Make sure that u close all the JDBC related Objects in a proper sequence. like exactly in the following&#160; Order…Always close the ResultSet, Statement and Connection objects insode the finally{} Block in the following order:

<pre>&#160;</pre>

<pre>&#160;</pre>

<pre>finally {</pre>

<pre>try {resultset.close();}</pre>

<pre>catch (Exception rse) {}</pre>

<pre>try {statement.close();}</pre>

<pre>catch (Exception sse) {}</pre>

<pre>try {connection.close();</pre>

<pre>catch (Exception cse) {}</pre>

<pre>}</pre>

#### Common Jdbc Issues-5).

Many times we get the following kind of error/exception while using a Connection object:

<pre>&#160;</pre>

<pre>java.sql.SQLException: Closed Connection</pre>

<pre>at oracle.jdbc.driver.SQLStateMapping.newSQLException(SQLStateMapping.java:70)</pre>

<pre>at oracle.jdbc.driver.DatabaseError.newSQLException(DatabaseError.java:133)</pre>

<pre>at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:199)</pre>

<pre>at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:263)</pre>

<pre>at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:271)</pre>

<pre>at oracle.jdbc.driver.DatabaseError.throwSqlException(DatabaseError.java:445)</pre>

<pre>at oracle.jdbc.driver.OracleStatement.ensureOpen(OracleStatement.java:3620)</pre>

<pre>at oracle.jdbc.driver.OracleCallableStatement.execute(OracleCallableStatement.java:3853)</pre>

<pre>at oracle.jdbc.driver.OraclePreparedStatementWrapper.execute(OraclePreparedStatementWrapper.java:1374)</pre>

<pre>at weblogic.jdbc.wrapper.PreparedStatement.execute(PreparedStatement.java:99)</pre>

In these cases we need to make sure that you enable the “Test Connection On Reserve” is disabled. for your Connection Pool.This is the best way the pool can ensure That connection pool provides us a good connection when an application ask for it.
    
  
Also provide a simple SQL query for connection testing in the DataSource configuration like ‘SELECT * FROM DUAL’

#### Common Jdbc Issues-6).

If you get the following Error:

<pre>&#160;</pre>

<pre>java.sql.SQLException: No more data to read from socket</pre>

<pre>at oracle.jdbc.driver.T4CMAREngine.unmarshalUB1(T4CMAREngine.java:1200)</pre>

<pre>at oracle.jdbc.driver.T4CMAREngine.unmarshalSB1(T4CMAREngine.java:1155)</pre>

<pre>at oracle.jdbc.driver.T4CTTIfun.receive(T4CTTIfun.java:279)</pre>

<pre>at oracle.jdbc.driver.T4CTTIfun.doRPC(T4CTTIfun.java:186)</pre>

<pre>at oracle.jdbc.driver.T4C8Oall.doOALL(T4C8Oall.java:521)</pre>

<pre>at oracle.jdbc.driver.T4CStatement.doOall8(T4CStatement.java:194)</pre>

<pre>at oracle.jdbc.driver.T4CStatement.executeForDescribe(T4CStatement.java:853)</pre>

<pre>at oracle.jdbc.driver.OracleStatement.executeMaybeDescribe(OracleStatement.java:1145)</pre>

<pre>at oracle.jdbc.driver.OracleStatement.doExecuteWithTimeout(OracleStatement.java:1267)</pre>

<pre>at oracle.jdbc.driver.OracleStatement.executeInternal(OracleStatement.java:1882)</pre>

<pre>at oracle.jdbc.driver.OracleStatement.execute(OracleStatement.java:1847)</pre>

<pre>at oracle.jdbc.driver.OracleStatementWrapper.execute(OracleStatementWrapper.java:301)</pre>

This error occurs if an applications that uses a database connections from the DataSource/Pool and When the application checked out a connection that has been already “timed out” or has been “staled”, still the application uses it to connect to the database, this error occurs.

In this case eother we need to start the Oracle Database Server or the Application Server which is maintaining the Connection Pool (Reseting the DataSource is also a valid option) sothat the staled connection should be cleared out and a new connection should be establised automatically.
    
  
.

.

Thanks

Jay SenSharma

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [调试基本WebLogic JDBC问题[转]](http://www.beansoft.biz/2011/09/10/%e8%b0%83%e8%af%95%e5%9f%ba%e6%9c%acweblogic-jdbc%e9%97%ae%e9%a2%98%e8%bd%ac/)