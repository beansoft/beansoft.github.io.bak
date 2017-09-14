---
id: 1241
title: 'Debugging WebLogic 6.x 7.x Platform Internals[forward]'
date: 2010-09-23T09:05:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1241
permalink: /2010/09/23/debugging-weblogic-6-x-7-x-platform-internalsforward/
views:
  - "5725"
original_post_id:
  - "1241"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - Debug
  - Flag
  - WebLogic
---
<p class="MsoNormal" style="text-align:left;" align="left">
  <b><span lang="EN-US" style="font-size:24pt;color:black;font-family:&quot;">Debugging WebLogic Platform Internals </p> 
  
  <p>
    </span></b>
  </p>
  
  <p class="MsoNormal">
    <span lang="EN-US"><a href="http://weblogic.sys-con.com/node/42733">http://weblogic.sys-con.com/node/42733</a> </p> 
    
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
        <b><span lang="EN-US">Note</span></b><span lang="EN-US">: this article is for WebLogic 6.x,7.x </p> 
        
        <p>
          </span>
        </p>
        
        <p class="MsoNormal">
          <span lang="EN-US"><a href="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image0012.gif"><img title="clip_image001" style="border-right:0;border-top:0;display:inline;border-left:0;border-bottom:0;" height="92" alt="clip_image001" src="http://www.beansoft.biz/wp-content/uploads/2010/09/clip_image001_thumb2.gif" width="92" border="0" /></a></span><span lang="EN-US"> </p> 
          
          <p>
            </span>
          </p>
          
          <p class="MsoNormal">
            <span class="apple-style-span"><span lang="EN-US" style="font-size:9pt;text-transform:uppercase;color:#939598;font-family:&quot;">BY</span></span><span class="apple-converted-space"><span lang="EN-US" style="font-size:9pt;text-transform:uppercase;color:#939598;font-family:&quot;">&#160;</span></span><span lang="EN-US"><a href="http://stevebuzzard.sys-con.com/"><b><span style="font-size:9pt;text-transform:uppercase;color:#939598;font-family:&quot;">STEVE BUZZARD</span></b></a></span><strong><span lang="EN-US" style="font-size:9pt;text-transform:uppercase;color:#939598;font-family:&quot;"> </p> 
            
            <p>
              </span></strong>
            </p>
            
            <p class="MsoNormal">
              <span class="apple-style-span"><span lang="EN-US" style="font-size:9pt;text-transform:uppercase;color:#939598;font-family:&quot;">MARCH 27, 2003 12:00 AM EST</span></span><span lang="EN-US"> </p> 
              
              <p>
                </span>
              </p>
              
              <p class="MsoNormal" style="text-align:left;" align="left">
                <i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">If you&#8217;ve ever worked as a Weblogic consultant, chances are this scenario will look all too familiar: <br />You&#8217;re at a high-profile client site as the "BEA WebLogic Expert." You were called in last minute because they are having "intermittent" problems in their newly deployed production system. The problems appear related to the WebLogic (Server/Portal/Integration) <insert here> subsystem, but you can&#8217;t be sure. There is absolutely nothing unusual in the standard output; neither is there anything amiss in the WebLogic server or domain logs.</span></i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                
                <p>
                  </span>
                </p>
                
                <p class="MsoNormal" style="text-align:left;" align="left">
                  <i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">Despite poring over the docs, newsgroups, dev2dev, and the support site ("Ask BEA"), you still can&#8217;t get a handle on the problem. You&#8217;ve double and triple checked the client&#8217;s code and their WebLogic configuration, and verified that they&#8217;re following the <insert here> specs. You finish off the usual checklist:&#160; </p> 
                  
                  <p>
                    </span></i>
                  </p>
                  
                  <p class="MsoNormal" style="text-align:left;" align="left">
                    <i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span></i><i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Is the OS Patch Level reasonably current (at least to the level required by the JVM used)?</span></i><i><span lang="EN-US" style="font-size:12pt;font-family:宋体;"> </p> 
                    
                    <p>
                      </span></i>
                    </p>
                    
                    <p class="MsoNormal" style="text-align:left;" align="left">
                      <i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span></i><i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>How&#8217;s the OS environment (file descriptors, TCP parameters, network parameters, ulimit settings, etc.)? </p> 
                      
                      <p>
                        </span></i>
                      </p>
                      
                      <p class="MsoNormal" style="text-align:left;" align="left">
                        <i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span></i><i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Anything really off with JVM version and/or parameters?</span></i><span lang="EN-US" style="font-size:12pt;font-family:宋体;"> </p> 
                        
                        <p>
                          </span>
                        </p>
                        
                        <p class="MsoNormal" style="text-align:left;" align="left">
                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span><i>Any type-2 JDBC drivers or other native code lurking about that could cause problems?</i> </p> 
                          
                          <p>
                            </span>
                          </p>
                          
                          <p class="MsoNormal" style="text-align:left;" align="left">
                            <i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">No smoking gun here, unfortunately, and the client senior management is beginning to breathe down your neck. You&#8217;d fire up your favorite debugger in their QA environment (can you reproduce it there?) in an attempt to track it down, but it&#8217;s not really that kind of "bug." It could very well be a product issue, you think.&#160; You check the latest release notes but nothing seems even vaguely related.&#160; Better open up a support case.&#160; You open up t<br /> he case and the support engineer is researching the issue but can find no related CRs, so the odds of a quick fix or workaround are long.&#160; Maybe it&#8217;s not a product issue&#160; &#8230;</span></i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                            
                            <p>
                              </span>
                            </p>
                            
                            <p class="MsoNormal" style="text-align:left;" align="left">
                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">Does this provide you with a touch of d</span><span style="font-size:13.5pt;color:black;font-family:&quot;">é<span lang="EN-US">ja` vu? I&#8217;ve run into variations of this scenario countless times and have subsequently uncovered a set of "undocumented" debugging parameters and properties that have helped me track down the source of trouble and saved my hide on more than one occasion. Several of these parameters have been bandied about quite a bit on the various BEA newsgroups, but never specified as a whole. </p> 
                              
                              <p>
                                </span></span>
                              </p>
                              
                              <p class="MsoNormal" style="text-align:left;" align="left">
                                <b><i><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">Warning:</span></i></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> The debugging parameters I&#8217;m about to describe are undocumented. This means that they are also officially unsupported by BEA and subject to change (or removal) at any time. </p> 
                                
                                <p>
                                  </span>
                                </p>
                                
                                <p class="MsoNormal" style="text-align:left;" align="left">
                                  <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">WebLogic Server 5.1</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> <br />For those who still indulge in 5.1, Table 1 lists its debugging parameters. They are specified as system properties (either on the command line or within the global, cluster, and/or server weblogic.properties files). </p> 
                                  
                                  <p>
                                    </span>
                                  </p>
                                  
                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                    <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">WebLogic Server 6.x/7.x</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> <br />The WebLogic Server 6.x and 7.x Debugging Parameters are tied to the ServerDebug MBean within the app server&#8217;s JMX infrastructure. A WebLogic Domain&#8217;s admin server and each associated managed server have a corresponding <ServerDebug> element within the config.xml file (subordinate to that server&#8217;s <Server> element). Note that because these parameters are undocumented, you cannot update them using the WebLogic Console but must hand-edit the config.xml file directly. For the uninitiated, the config.xml file holds the configuration for a WebLogic Domain and lives in the domain&#8217;s top-level directory for the admin server. Almost all the parameters are of the "true/false" variety (a noted exception is "DebugJAXRPCDebugLevel", which is an integer value greater than 0: the higher the number, the more verbose the output). Be sure that the administration server is not running before you edit the config.xml (otherwise, your changes may get overwritten by the running server). Also be sure that you back up the config.xml file before you begin modifying it so that you have a valid configuration should you "mess up." Note that the debugging parameters I list below are based on 7.0 sp1 and some parameters are not valid in 6.1 (the server will quickly let you know which ones upon start up!). The debug information is printed to the standard output, so ensure that you are not redirecting stdout to /dev/null (as is often the case in a test or production environment). Also, setting these parameters to "true" can result in very verbose output, so flip the debug "switches" judiciously, based on the subsystem you suspect is associated with the problems you&#8217;re trying to track down (e.g., if it&#8217;s an EJB-related issue, set only the DebugEJB&#8230; parameters to "true"; see Listing 1). </p> 
                                    
                                    <p>
                                      </span>
                                    </p>
                                    
                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">In addition to these JMX-based debugging parameters, there is a set of system properties you can set for additional debugging information that is written to the WebLogic log. Most of the properties are set as such: </p> 
                                      
                                      <p>
                                        </span>
                                      </p>
                                      
                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                        <span lang="EN-US" style="font-size:13.5pt;color:green;font-family:&quot;">-Dweblogic.Debug=<debug-parameter1, <br />debug-parameter2,debug-parameter3,&#8230;></span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                        
                                        <p>
                                          </span>
                                        </p>
                                        
                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">These debug parameters include: </p> 
                                          
                                          <p>
                                            </span>
                                          </p>
                                          
                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                            <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">IIOP</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                            
                                            <p>
                                              </span>
                                            </p>
                                            
                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.iiop.ots </p> 
                                              
                                              <p>
                                                </span>
                                              </p>
                                              
                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.iiop.transport </p> 
                                                
                                                <p>
                                                  </span>
                                                </p>
                                                
                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.iiop.marshal </p> 
                                                  
                                                  <p>
                                                    </span>
                                                  </p>
                                                  
                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.iiop.startup </p> 
                                                    
                                                    <p>
                                                      </span>
                                                    </p>
                                                    
                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                      <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">JDBC/Data Sources</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                      
                                                      <p>
                                                        </span>
                                                      </p>
                                                      
                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JDBCConn </p> 
                                                        
                                                        <p>
                                                          </span>
                                                        </p>
                                                        
                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JDBCSQL </p> 
                                                          
                                                          <p>
                                                            </span>
                                                          </p>
                                                          
                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JDBCConnStackTrace </p> 
                                                            
                                                            <p>
                                                              </span>
                                                            </p>
                                                            
                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                              <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">JMX/Deployment</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                              
                                                              <p>
                                                                </span>
                                                              </p>
                                                              
                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.commoAdmin </p> 
                                                                
                                                                <p>
                                                                  </span>
                                                                </p>
                                                                
                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.commoProxy </p> 
                                                                  
                                                                  <p>
                                                                    </span>
                                                                  </p>
                                                                  
                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.deployerRuntime </p> 
                                                                    
                                                                    <p>
                                                                      </span>
                                                                    </p>
                                                                    
                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.MasterDeployer </p> 
                                                                      
                                                                      <p>
                                                                        </span>
                                                                      </p>
                                                                      
                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.deployTask </p> 
                                                                        
                                                                        <p>
                                                                          </span>
                                                                        </p>
                                                                        
                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.deployHelper </p> 
                                                                          
                                                                          <p>
                                                                            </span>
                                                                          </p>
                                                                          
                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.MasterDeployer </p> 
                                                                            
                                                                            <p>
                                                                              </span>
                                                                            </p>
                                                                            
                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.OamDelta </p> 
                                                                              
                                                                              <p>
                                                                                </span>
                                                                              </p>
                                                                              
                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.OamVersion </p> 
                                                                                
                                                                                <p>
                                                                                  </span>
                                                                                </p>
                                                                                
                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.slaveDeployer.semaphore </p> 
                                                                                  
                                                                                  <p>
                                                                                    </span>
                                                                                  </p>
                                                                                  
                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.slaveDeployer </p> 
                                                                                    
                                                                                    <p>
                                                                                      </span>
                                                                                    </p>
                                                                                    
                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.ConfigMBean </p> 
                                                                                      
                                                                                      <p>
                                                                                        </span>
                                                                                      </p>
                                                                                      
                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.ConfigMBeanEncrypt </p> 
                                                                                        
                                                                                        <p>
                                                                                          </span>
                                                                                        </p>
                                                                                        
                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.ConfigMBeanSetAttribute </p> 
                                                                                          
                                                                                          <p>
                                                                                            </span>
                                                                                          </p>
                                                                                          
                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.management.DynamicMBeanImpl </p> 
                                                                                            
                                                                                            <p>
                                                                                              </span>
                                                                                            </p>
                                                                                            
                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.management.DynamicMBeanImpl.setget </p> 
                                                                                              
                                                                                              <p>
                                                                                                </span>
                                                                                              </p>
                                                                                              
                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.mbeanProxyCache </p> 
                                                                                                
                                                                                                <p>
                                                                                                  </span>
                                                                                                </p>
                                                                                                
                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.mbeanDelete </p> 
                                                                                                  
                                                                                                  <p>
                                                                                                    </span>
                                                                                                  </p>
                                                                                                  
                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.mbeanQuery </p> 
                                                                                                    
                                                                                                    <p>
                                                                                                      </span>
                                                                                                    </p>
                                                                                                    
                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.MBeanInteropList </p> 
                                                                                                      
                                                                                                      <p>
                                                                                                        </span>
                                                                                                      </p>
                                                                                                      
                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.mbeanProxy </p> 
                                                                                                        
                                                                                                        <p>
                                                                                                          </span>
                                                                                                        </p>
                                                                                                        
                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.registerMBean </p> 
                                                                                                          
                                                                                                          <p>
                                                                                                            </span>
                                                                                                          </p>
                                                                                                          
                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.getMBeanInfo </p> 
                                                                                                            
                                                                                                            <p>
                                                                                                              </span>
                                                                                                            </p>
                                                                                                            
                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.getMBeanAttributes </p> 
                                                                                                              
                                                                                                              <p>
                                                                                                                </span>
                                                                                                              </p>
                                                                                                              
                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.addDependenciesRecursively </p> 
                                                                                                                
                                                                                                                <p>
                                                                                                                  </span>
                                                                                                                </p>
                                                                                                                
                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.MBeanListener </p> 
                                                                                                                  
                                                                                                                  <p>
                                                                                                                    </span>
                                                                                                                  </p>
                                                                                                                  
                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.application </p> 
                                                                                                                    
                                                                                                                    <p>
                                                                                                                      </span>
                                                                                                                    </p>
                                                                                                                    
                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.deployer </p> 
                                                                                                                      
                                                                                                                      <p>
                                                                                                                        </span>
                                                                                                                      </p>
                                                                                                                      
                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.appPoller </p> 
                                                                                                                        
                                                                                                                        <p>
                                                                                                                          </span>
                                                                                                                        </p>
                                                                                                                        
                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.appManager </p> 
                                                                                                                          
                                                                                                                          <p>
                                                                                                                            </span>
                                                                                                                          </p>
                                                                                                                          
                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.BootstrapServlet </p> 
                                                                                                                            
                                                                                                                            <p>
                                                                                                                              </span>
                                                                                                                            </p>
                                                                                                                            
                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.fileDistributionServlet </p> 
                                                                                                                              
                                                                                                                              <p>
                                                                                                                                </span>
                                                                                                                              </p>
                                                                                                                              
                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">Application Deployment</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                
                                                                                                                                <p>
                                                                                                                                  </span>
                                                                                                                                </p>
                                                                                                                                
                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.J2EEApplication </p> 
                                                                                                                                  
                                                                                                                                  <p>
                                                                                                                                    </span>
                                                                                                                                  </p>
                                                                                                                                  
                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.applicat<br /> ion </p> 
                                                                                                                                    
                                                                                                                                    <p>
                                                                                                                                      </span>
                                                                                                                                    </p>
                                                                                                                                    
                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.appPoller </p> 
                                                                                                                                      
                                                                                                                                      <p>
                                                                                                                                        </span>
                                                                                                                                      </p>
                                                                                                                                      
                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.appManager </p> 
                                                                                                                                        
                                                                                                                                        <p>
                                                                                                                                          </span>
                                                                                                                                        </p>
                                                                                                                                        
                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                          <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">JTA</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                          
                                                                                                                                          <p>
                                                                                                                                            </span>
                                                                                                                                          </p>
                                                                                                                                          
                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAGateway </p> 
                                                                                                                                            
                                                                                                                                            <p>
                                                                                                                                              </span>
                                                                                                                                            </p>
                                                                                                                                            
                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAGatewayStackTrace </p> 
                                                                                                                                              
                                                                                                                                              <p>
                                                                                                                                                </span>
                                                                                                                                              </p>
                                                                                                                                              
                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTA2PC </p> 
                                                                                                                                                
                                                                                                                                                <p>
                                                                                                                                                  </span>
                                                                                                                                                </p>
                                                                                                                                                
                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTA2PCStackTrace </p> 
                                                                                                                                                  
                                                                                                                                                  <p>
                                                                                                                                                    </span>
                                                                                                                                                  </p>
                                                                                                                                                  
                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAHealth </p> 
                                                                                                                                                    
                                                                                                                                                    <p>
                                                                                                                                                      </span>
                                                                                                                                                    </p>
                                                                                                                                                    
                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAPropagate </p> 
                                                                                                                                                      
                                                                                                                                                      <p>
                                                                                                                                                        </span>
                                                                                                                                                      </p>
                                                                                                                                                      
                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTARecovery </p> 
                                                                                                                                                        
                                                                                                                                                        <p>
                                                                                                                                                          </span>
                                                                                                                                                        </p>
                                                                                                                                                        
                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAXA </p> 
                                                                                                                                                          
                                                                                                                                                          <p>
                                                                                                                                                            </span>
                                                                                                                                                          </p>
                                                                                                                                                          
                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAXAStackTrace </p> 
                                                                                                                                                            
                                                                                                                                                            <p>
                                                                                                                                                              </span>
                                                                                                                                                            </p>
                                                                                                                                                            
                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAResourceHealth </p> 
                                                                                                                                                              
                                                                                                                                                              <p>
                                                                                                                                                                </span>
                                                                                                                                                              </p>
                                                                                                                                                              
                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTAMigration </p> 
                                                                                                                                                                
                                                                                                                                                                <p>
                                                                                                                                                                  </span>
                                                                                                                                                                </p>
                                                                                                                                                                
                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTARecoveryStackTrace </p> 
                                                                                                                                                                  
                                                                                                                                                                  <p>
                                                                                                                                                                    </span>
                                                                                                                                                                  </p>
                                                                                                                                                                  
                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTANaming </p> 
                                                                                                                                                                    
                                                                                                                                                                    <p>
                                                                                                                                                                      </span>
                                                                                                                                                                    </p>
                                                                                                                                                                    
                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTATLOG </p> 
                                                                                                                                                                      
                                                                                                                                                                      <p>
                                                                                                                                                                        </span>
                                                                                                                                                                      </p>
                                                                                                                                                                      
                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>weblogic.JTALifecycle </p> 
                                                                                                                                                                        
                                                                                                                                                                        <p>
                                                                                                                                                                          </span>
                                                                                                                                                                        </p>
                                                                                                                                                                        
                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">A concrete example of debugging a TxDataSource problem might be to set the following on your server&#8217;s start-up command line: </p> 
                                                                                                                                                                          
                                                                                                                                                                          <p>
                                                                                                                                                                            </span>
                                                                                                                                                                          </p>
                                                                                                                                                                          
                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:green;font-family:&quot;">-Dweblogic.Debug=weblogic.JDBCConn, <br />weblogic.JDBCSQL,weblogic.JTA2PC</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                                                            
                                                                                                                                                                            <p>
                                                                                                                                                                              </span>
                                                                                                                                                                            </p>
                                                                                                                                                                            
                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">There are also a few other system properties floating around WebLogic Server that are set on the command line:&#160; </p> 
                                                                                                                                                                              
                                                                                                                                                                              <p>
                                                                                                                                                                                </span>
                                                                                                                                                                              </p>
                                                                                                                                                                              
                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.cache.debug </p> 
                                                                                                                                                                                
                                                                                                                                                                                <p>
                                                                                                                                                                                  </span>
                                                                                                                                                                                </p>
                                                                                                                                                                                
                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.cache.verbose </p> 
                                                                                                                                                                                  
                                                                                                                                                                                  <p>
                                                                                                                                                                                    </span>
                                                                                                                                                                                  </p>
                                                                                                                                                                                  
                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dejb.enableCacheDump </p> 
                                                                                                                                                                                    
                                                                                                                                                                                    <p>
                                                                                                                                                                                      </span>
                                                                                                                                                                                    </p>
                                                                                                                                                                                    
                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.cmp.rdbms.debug </p> 
                                                                                                                                                                                      
                                                                                                                                                                                      <p>
                                                                                                                                                                                        </span>
                                                                                                                                                                                      </p>
                                                                                                                                                                                      
                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.cmp.rdbms.verbose </p> 
                                                                                                                                                                                        
                                                                                                                                                                                        <p>
                                                                                                                                                                                          </span>
                                                                                                                                                                                        </p>
                                                                                                                                                                                        
                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.persistence.debug </p> 
                                                                                                                                                                                          
                                                                                                                                                                                          <p>
                                                                                                                                                                                            </span>
                                                                                                                                                                                          </p>
                                                                                                                                                                                          
                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.persistence.verbose </p> 
                                                                                                                                                                                            
                                                                                                                                                                                            <p>
                                                                                                                                                                                              </span>
                                                                                                                                                                                            </p>
                                                                                                                                                                                            
                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.compliance.debug </p> 
                                                                                                                                                                                              
                                                                                                                                                                                              <p>
                                                                                                                                                                                                </span>
                                                                                                                                                                                              </p>
                                                                                                                                                                                              
                                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.compliance.verbose </p> 
                                                                                                                                                                                                
                                                                                                                                                                                                <p>
                                                                                                                                                                                                  </span>
                                                                                                                                                                                                </p>
                                                                                                                                                                                                
                                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.deployment.debug </p> 
                                                                                                                                                                                                  
                                                                                                                                                                                                  <p>
                                                                                                                                                                                                    </span>
                                                                                                                                                                                                  </p>
                                                                                                                                                                                                  
                                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.deployment.verbose </p> 
                                                                                                                                                                                                    
                                                                                                                                                                                                    <p>
                                                                                                                                                                                                      </span>
                                                                                                                                                                                                    </p>
                                                                                                                                                                                                    
                                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.dd.xml </p> 
                                                                                                                                                                                                      
                                                                                                                                                                                                      <p>
                                                                                                                                                                                                        </span>
                                                                                                                                                                                                      </p>
                                                                                                                                                                                                      
                                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.deployer.debug </p> 
                                                                                                                                                                                                        
                                                                                                                                                                                                        <p>
                                                                                                                                                                                                          </span>
                                                                                                                                                                                                        </p>
                                                                                                                                                                                                        
                                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.deployer.verbose </p> 
                                                                                                                                                                                                          
                                                                                                                                                                                                          <p>
                                                                                                                                                                                                            </span>
                                                                                                                                                                                                          </p>
                                                                                                                                                                                                          
                                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.verbose.deployment </p> 
                                                                                                                                                                                                            
                                                                                                                                                                                                            <p>
                                                                                                                                                                                                              </span>
                                                                                                                                                                                                            </p>
                                                                                                                                                                                                            
                                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.ejbc.debug </p> 
                                                                                                                                                                                                              
                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                </span>
                                                                                                                                                                                                              </p>
                                                                                                                                                                                                              
                                                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.ejbc.verbose </p> 
                                                                                                                                                                                                                
                                                                                                                                                                                                                <p>
                                                                                                                                                                                                                  </span>
                                                                                                                                                                                                                </p>
                                                                                                                                                                                                                
                                                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.runtime.debug </p> 
                                                                                                                                                                                                                  
                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                    </span>
                                                                                                                                                                                                                  </p>
                                                                                                                                                                                                                  
                                                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.runtime.verbose </p> 
                                                                                                                                                                                                                    
                                                                                                                                                                                                                    <p>
                                                                                                                                                                                                                      </span>
                                                                                                                                                                                                                    </p>
                                                                                                                                                                                                                    
                                                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.jms.poll.debug </p> 
                                                                                                                                                                                                                      
                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                      
                                                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.jms.poll.verbose </p> 
                                                                                                                                                                                                                        
                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                          </span>
                                                                                                                                                                                                                        </p>
                                                                                                                                                                                                                        
                                                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.security.debug </p> 
                                                                                                                                                                                                                          
                                                                                                                                                                                                                          <p>
                                                                                                                                                                                                                            </span>
                                                                                                                                                                                                                          </p>
                                                                                                                                                                                                                          
                                                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb20.security.verbose </p> 
                                                                                                                                                                                                                            
                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                            
                                                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.locks.debug </p> 
                                                                                                                                                                                                                              
                                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                                </span>
                                                                                                                                                                                                                              </p>
                                                                                                                                                                                                                              
                                                                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.locks.verbose </p> 
                                                                                                                                                                                                                                
                                                                                                                                                                                                                                <p>
                                                                                                                                                                                                                                  </span>
                                                                                                                                                                                                                                </p>
                                                                                                                                                                                                                                
                                                                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.bean.manager.debug </p> 
                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                                    </span>
                                                                                                                                                                                                                                  </p>
                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.bean.manager.verbose </p> 
                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                    <p>
                                                                                                                                                                                                                                      </span>
                                                                                                                                                                                                                                    </p>
                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.pool.InstancePool.debug </p> 
                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.pool.InstancePool.verbose </p> 
                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                                          </span>
                                                                                                                                                                                                                                        </p>
                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.swap.debug </p> 
                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                          <p>
                                                                                                                                                                                                                                            </span>
                                                                                                                                                                                                                                          </p>
                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.ejb.swap.verbose </p> 
                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.j2ee.dd.xml </p> 
                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                                                </span>
                                                                                                                                                                                                                                              </p>
                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dweblogic.kernel.debug </p> 
                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                <p>
                                                                                                                                                                                                                                                  </span>
                                                                                                                                                                                                                                                </p>
                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                  <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">WebLogic Portal</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> <br />WebLogic Portal (both 4.0 and 7.0) uses System Properties to control their debug output. These Portal properties are tied to specific classes and can be set in two different ways:&#160; <br />1.&#160;&#160; <b><i>Set one or more system properties on the command line</i></b>. These property names are of the form: </p> 
                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                                                    </span>
                                                                                                                                                                                                                                                  </p>
                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:green;font-family:&quot;">debug.<fully qualified class name>.</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                    <p>
                                                                                                                                                                                                                                                      </span>
                                                                                                                                                                                                                                                    </p>
                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">For example, if I want debugging information on the processing of the Entitlements Access Controller class, I&#8217;d add the following to my Portal Server start-up command line: </p> 
                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:green;font-family:&quot;">-Ddebug.com.bea.p13n.entitlements. <br />accesscontroller.AccessController=true</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                                                          </span>
                                                                                                                                                                                                                                                        </p>
                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">2.&#160;&#160; Create a file entitled "debug.properties" in the Portal Server working directory (in 7.0, this is the domain directory; in 4.0, this is the parent of the "config" directory). For each Portal class you desire debug output from, add a line in this file of the form: </p> 
                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                          <p>
                                                                                                                                                                                                                                                            </span>
                                                                                                                                                                                                                                                          </p>
                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:green;font-family:&quot;"><fully qualified class name>=true.</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">For example, if I want debugging information on the Portal Management sub-system, I create a "debug.properties" file with content similar to: </p> 
                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                                                                </span>
                                                                                                                                                                                                                                                              </p>
                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:green;font-family:&quot;">com.bea.portal.manager.internal.PortalManagerDelegateImpl=true <br />com.bea.portal.manager.internal.PagePersonalizationImpl=true <br />com.bea.portal.manager.internal.PortalParser=true <br />com.bea.portal.manager.internal.PortalPersistenceManager=true <br />com.bea.portal.manager.internal.PortletParser=true <br />com.bea.portal.manager.internal.PortletPersistenceManager=true <br />com.bea.portal.manager.internal.PortletStateImpl=true <br />com.bea.portal.manager.internal.UserPortalStatePolicy=true</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                <p>
                                                                                                                                                                                                                                                                  </span>
                                                                                                                                                                                                                                                                </p>
                                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                  <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">WebLogic Integration</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> <br />WebLogic Integration also uses System Properties to enable debugging information, but the scheme here is less complex (and, some would say, less flexible) than that of Portal. Simply set the following properties on your WLI Server start up command line according to your needs:&#160; </p> 
                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                                                                    </span>
                                                                                                                                                                                                                                                                  </p>
                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwlc.debug.signature=true </p> 
                                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                    <p>
                                                                                                                                                                                                                                                                      </span>
                                                                                                                                                                                                                                                                    </p>
                                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Deci.repository.helper.debug=true </p> 
                                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.client.security.debug=true </p> 
                                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                                                                          </span>
                                                                                                                                                                                                                                                                        </p>
                                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.studio.timeprocessor.debug=true </p> 
                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                          <p>
                                                                                                                                                                                                                                                                            </span>
                                                                                                                                                                                                                                                                          </p>
                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.studio.debug=true </p> 
                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.common.timedevent.debug=true </p> 
                                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                                                                                </span>
                                                                                                                                                                                                                                                                              </p>
                                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                              <p style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.common.xmltemplate.debug=true </p> 
                                                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                                <p>
                                                                                                                                                                                                                                                                                  </span>
                                                                                                                                                                                                                                                                                </p>
                                                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.eventprocessor.addrmsgdebug=true </p> 
                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                                                                                    </span>
                                                                                                                                                                                                                                                                                  </p>
                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.eventprocessor.debug=true </p> 
                                                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                                    <p>
                                                                                                                                                                                                                                                                                      </span>
                                                                                                                                                                                                                                                                                    </p>
                                                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.jms.debug=true </p> 
                                                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.plugin.debug=true </p> 
                                                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                                                                                          </span>
                                                                                                                                                                                                                                                                                        </p>
                                                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.workflow.debug=true </p> 
                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                          <p>
                                                                                                                                                                                                                                                                                            </span>
                                                                                                                                                                                                                                                                                          </p>
                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.businesscalendar.debug=true </p> 
                                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                              <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.busop.debug=true </p> 
                                                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                                                                                                </span>
                                                                                                                                                                                                                                                                                              </p>
                                                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.workflow.action.taskduedate.debug=true </p> 
                                                                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                                                <p>
                                                                                                                                                                                                                                                                                                  </span>
                                                                                                                                                                                                                                                                                                </p>
                                                                                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                                                <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                  <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.workflow.timedevent.debug=true </p> 
                                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                                                                                                    </span>
                                                                                                                                                                                                                                                                                                  </p>
                                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                                  <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                    <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.xml.debug=true </p> 
                                                                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                                                    <p>
                                                                                                                                                                                                                                                                                                      </span>
                                                                                                                                                                                                                                                                                                    </p>
                                                                                                                                                                                                                                                                                                    
                                                                                                                                                                                                                                                                                                    <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                      <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.xslt.debug=true </p> 
                                                                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                                                      <p>
                                                                                                                                                                                                                                                                                                        </span>
                                                                                                                                                                                                                                                                                                      </p>
                                                                                                                                                                                                                                                                                                      
                                                                                                                                                                                                                                                                                                      <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                        <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.workflow.start.debug=true </p> 
                                                                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                                                        <p>
                                                                                                                                                                                                                                                                                                          </span>
                                                                                                                                                                                                                                                                                                        </p>
                                                                                                                                                                                                                                                                                                        
                                                                                                                                                                                                                                                                                                        <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                          <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.bpm.server.workflowprocessor.debug=true </p> 
                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                          <p>
                                                                                                                                                                                                                                                                                                            </span>
                                                                                                                                                                                                                                                                                                          </p>
                                                                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                                                          <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                            <span lang="EN-US" style="font-size:13.5pt;color:black;font-family:symbol;">·</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"><span>&#160; </span>Dwli.common.server.errorlistener.debug=true </p> 
                                                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                                                            <p>
                                                                                                                                                                                                                                                                                                              </span>
                                                                                                                                                                                                                                                                                                            </p>
                                                                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                                                            <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                              <b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;">Summary</span></b><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> <br />These debugging parameters can be of great help (BEA Support often recommends trying out particular debugging parameters to help track down specific issues) and can also aid in your understanding of how the WebLogic Server, Portal, and Integration internals operate (which in turn sharpens your troubleshooting skills). Although they are official undocumented and unsupported (who needs real "support" for a debug property?), they can truly be a lifesaver. </p> 
                                                                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                                                              <p>
                                                                                                                                                                                                                                                                                                                </span>
                                                                                                                                                                                                                                                                                                              </p>
                                                                                                                                                                                                                                                                                                              
                                                                                                                                                                                                                                                                                                              <p class="MsoNormal" style="text-align:left;" align="left">
                                                                                                                                                                                                                                                                                                                <span lang="EN-US" style="font-size:12pt;color:black;font-family:&quot;">© 2008 SYS-CON Media Inc.</span><span lang="EN-US" style="font-size:13.5pt;color:black;font-family:&quot;"> </p> 
                                                                                                                                                                                                                                                                                                                
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
                                                                                                                                                                                                                                                                                                                  
                                                                                                                                                                                                                                                                                                                  <p>
                                                                                                                                                                                                                                                                                                                    转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2010/09/23/debugging-weblogic-6-x-7-x-platform-internalsforward/">Debugging WebLogic 6.x 7.x Platform Internals[forward]</a>
                                                                                                                                                                                                                                                                                                                  </p>