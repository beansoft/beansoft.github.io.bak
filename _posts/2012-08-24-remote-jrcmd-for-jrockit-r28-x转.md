---
id: 2978
title: 'Remote JRCMD for JRockit R28.x[转]'
date: 2012-08-24T17:12:07+00:00
author: 刘长炯
layout: post
guid: http://weblogic.clawz.com/?p=2978
permalink: '/2012/08/24/remote-jrcmd-for-jrockit-r28-x%e8%bd%ac/'
views:
  - "3285"
image: /wp-content/uploads/2012/09/1257252433_java.png
categories:
  - JVM
tags:
  - JRockit
  - JVM
---
## Tuesday, April 24, 2012

### <a href="http://hirt.se/blog/?p=207" rel="bookmark">Remote JRCMD for JRockit R28.x</a>

<div>
  Filed under: <a title="View all posts in Programming" href="http://hirt.se/blog/?cat=3" rel="category">Programming</a> — Marcus @ 15:02
</div>

<div>
  <p>
    On popular demand, here is how write a remote JRCMD for R28.x:
  </p>
  
  <pre>import java.lang.management.ManagementFactory;
import java.net.MalformedURLException;
import java.util.HashMap;
import java.util.Iterator;
import java.util.Map;

import javax.management.Attribute;
import javax.management.InstanceNotFoundException;
import javax.management.MBeanAttributeInfo;
import javax.management.MBeanServerConnection;
import javax.management.ObjectName;
import javax.management.remote.JMXConnector;
import javax.management.remote.JMXConnectorFactory;
import javax.management.remote.JMXServiceURL;

/**
 * Simple code example on how to execute
 * ctrl-break handlers remotely.
 *
 * Usage:
 * RemoteJRCMD -host -port -user -pass -command []
 *
 * All arguments are optional. If no command is
 * specified, all performance counters and their
 * current values are listed.
 *
 * @author Marcus Hirt
 */
public final class RemoteJRCMD {
	private final static String KEY_CREDENTIALS =
		"jmx.remote.credentials";
	private final static String JROCKIT_PERFCOUNTER_MBEAN_NAME =
		"oracle.jrockit.management:type=PerfCounters";
	private final static String JROCKIT_CONSOLE_MBEAN_NAME =
		"oracle.jrockit.management:type=JRockitConsole";
	private final static String[] SIGNATURE =
		new String[] {"java.lang.String"};
	private final static String DIAGNOSTIC_COMMAND_MBEAN_NAME =
		"oracle.jrockit.management:type=DiagnosticCommand";

	public static void main(String[] args)
			throws Exception {
		HashMap commandMap =
			parseArguments(args);
		executeCommand(
				commandMap.get("-host"),
				Integer.parseInt(commandMap.get("-port")),
				commandMap.get("-user"),
				commandMap.get("-password"),
				commandMap.get("-command"));
	}

	private static HashMap parseArguments(
			String[] args) {
		HashMap commandMap =
			new HashMap();
		commandMap.put("-host", "localhost");
		commandMap.put("-port", "7091");
		for (int i = 0; i &lt; args.length; i++) {
			if (args[i].startsWith("-")) {
				StringBuilder buf = new StringBuilder();
				int j = i + 1;
				while (j &lt; args.length
						&& !args[j].startsWith("-")) {
					buf.append(" ");
					buf.append(args[j++]);
				}
				commandMap.put(args[i],
						buf.toString().trim());
				i = j - 1;
			}
		}
		return commandMap;
	}

	@SuppressWarnings("unchecked")
	public static void executeCommand(
			String host, int port, String user,
			String password, String command)
			throws Exception {
		MBeanServerConnection server = null;
		JMXConnector jmxc = null;
		Map map = null;
		if (user != null || password != null) {
			map = new HashMap();
			final String[] credentials = new String[2];
			credentials[0] = user;
			credentials[1] = password;
			map.put(KEY_CREDENTIALS, credentials);
		}
		// Use same convention as Sun. localhost:0 means
		// "VM, monitor thyself!"
		if (host.equals("localhost") && port == 0) {
			server = ManagementFactory.getPlatformMBeanServer();
		} else {
			jmxc = JMXConnectorFactory.newJMXConnector(
					createConnectionURL(host,
							port), map);
			jmxc.connect();
			server = jmxc.getMBeanServerConnection();
		}

		System.out.println("Connected to " + host
				+ ":" + port);

		try {
			server.getMBeanInfo(new ObjectName(
					JROCKIT_CONSOLE_MBEAN_NAME));
		} catch (InstanceNotFoundException e1) {
			server.createMBean(
					"oracle.jrockit.management.JRockitConsole",
					null);
		}

		if (command == null) {
			ObjectName perfCounterObjectName = new ObjectName(
					JROCKIT_PERFCOUNTER_MBEAN_NAME);
			System.out.println("Listing all counters...");
			MBeanAttributeInfo[] attributes = server.getMBeanInfo(
					perfCounterObjectName).getAttributes();
			System.out.println("Counter\tValue\n=======\t====");

			String[] attributeNames = new String[attributes.length];
			for (int i = 0; i &lt; attributes.length; i++) {
				attributeNames[i] = attributes[i].getName();
			}
			Iterator valueIter = server.getAttributes(
					perfCounterObjectName,
					attributeNames).iterator();
			while (valueIter.hasNext()) {
				Attribute attr = (Attribute) valueIter.next();
				System.out.println(attr.getName()
						+ "\t=\t"
						+ attr.getValue());
			}
		} else {
			System.out.println("Invoking the ctrl-break command '"
					+ command + "'...");
			ObjectName consoleObjectName = new ObjectName(
					DIAGNOSTIC_COMMAND_MBEAN_NAME);
			Object[] params = new Object[1];
			params[0] = command;
			System.out.println("The CtrlBreakCommand returned: \n"
					+ server.invoke(
							consoleObjectName,
							"execute", params,
							SIGNATURE));
		}

		if (jmxc != null) {
			jmxc.close();
		}
	}

	private static JMXServiceURL createConnectionURL(
			String host, int port)
			throws MalformedURLException {
		return new JMXServiceURL("rmi", "", 0,
				"/jndi/rmi://" + host + ":"
						+ port + "/jmxrmi");
	}
}</pre>
  
  <p>
    (This example can also be found in the <a href="http://www.amazon.com/Oracle-JRockit-The-Definitive-Guide/dp/1847198066/ref=ntt_at_ep_dpt_1">JRockit book</a>, at the end of chapter 11.)
  </p>
  
  <p>
    The following example would list all the performance counters and their values on the JVM running the RemoteJRCMD itself:
  </p>
  
  <blockquote>
    <p>
      <code>java RemoteJRCMD –port 0</code>
    </p>
  </blockquote>
  
  <p>
    The following example would list all the available commands in a JVM with a management agent open on the default port (7091) on localhost:
  </p>
  
  <blockquote>
    <p>
      <code>java RemoteJRCMD –command help</code>
    </p>
  </blockquote>
  
  <p>
    The following example would print the help on the command “print_threads”, which performs a thread stack dump:
  </p>
  
  <blockquote>
    <p>
      <code>java RemoteJRCMD –command help print_threads</code>
    </p>
  </blockquote>
  
  <p>
    The following example would print a heap histogram per class for the JVM running on port 4711 on the host adastra:
  </p>
  
  <blockquote>
    <p>
      <code>java RemoteJRCMD –port 4711 –host adastra –command print_object_summary</code>
    </p>
  </blockquote>
</div>

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Remote JRCMD for JRockit R28.x[转]](http://www.beansoft.biz/2012/08/24/remote-jrcmd-for-jrockit-r28-x%e8%bd%ac/)