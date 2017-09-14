---
id: 1981
title: 'WebLogic versioned deployment side-by-side[转]'
date: 2011-04-20T20:37:22+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1981
permalink: '/2011/04/20/weblogic-versioned-deployment-side-by-side%e8%bd%ac/'
views:
  - "5874"
original_post_id:
  - "1981"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
From: <http://eelzinga.wordpress.com/2009/08/05/weblogic-side-by-side-deployment/>

Weblogic, side-by-side deployment

August 5, 2009 by [Eric Elzinga](http://eelzinga.wordpress.com/author/eelzinga/) [3 Comments](http://eelzinga.wordpress.com/2009/08/05/weblogic-side-by-side-deployment/#respond)

Weblogic Server supports a nice feature called side-by-side deployment (or versioned deployment). This function is extremely usefull when you need to deploy a new version of an application and still keep the old one up and running. So the running instances will still use the current version and all new instances will be able to invoke the new deployed version of the application.   
As soon as all the sessions who’re using the old version of the application are expired, Weblogic will recognize it and will deactivate the old version. So at this moment only the new deployed version is active and all new sessions will make us of it.

So how does this work.

You could either use wlst to deploy the application and specifiy the versionnumber on deployment as one of the parameters or you can use the manifest.mf file. We’ll be using the last one.

  1. Create a webservice project 
  2. Edit to manifest file located in WebContent > META-INF and add the next on a new row : ‘WebLogic-Application-Version: v1′   
     <img title="clip_image001" style="display:inline;border-width:0;" height="100" alt="clip_image001" src="http://www.beansoft.biz/wp-content/uploads/2011/04/clip_image001.png" width="400" border="0" />
  3. Package the service and deploy it in the console 

**Deployment**

  1. Go to the Weblogic Console > Deployments. Click ‘Lock & Edit’ and in the deployments part click Install 
  2. Select the just created archive   
     <img title="clip_image002" style="display:inline;border-width:0;" height="93" alt="clip_image002" src="http://www.beansoft.biz/wp-content/uploads/2011/04/clip_image002.png" width="454" border="0" />
  3. Install this deployment as an application 
  4. Optional Settings. And in here we will see the ‘Archive Version’ of our application. Change the name to ‘MyService’ and leave the rest on default value   
     <img title="clip_image003" style="display:inline;border-width:0;" height="174" alt="clip_image003" src="http://www.beansoft.biz/wp-content/uploads/2011/04/clip_image003.png" width="455" border="0" />

If you look in the list of deployments we will see our application is labeled with a version indication (v1).   
     <img title="clip_image004" style="display:inline;border-width:0;" height="35" alt="clip_image004" src="http://www.beansoft.biz/wp-content/uploads/2011/04/clip_image004.png" width="455" border="0" />  
The current version is still active.

Now create a new version of the application and change the v1 in the manifest file to v2, and package it.

**Update Deployment**

  1. Go to the Weblogic Console > Deployments. Click ‘Lock & Edit’, select the application we want to update (MyService) and in the deployments part click Update 
  2. Click Change Path of the source path and select the just created archive (v2), the application will be deployed as version v2 

If we now look in the list of deployments, we will see 2 versions of our application deployed.   
<img title="clip_image005" style="display:inline;border-width:0;" height="27" alt="clip_image005" src="http://www.beansoft.biz/wp-content/uploads/2011/04/clip_image005.png" width="455" border="0" />

Version v1 gets status ‘Retired’ and the new version v2 will get status ‘Active’.

**Running instances**   
We have the next scenarios

  1. Version v1 is deployed. Deploy version v2. The new version v2 will get status ‘Active’ and the old version v1 will get status ‘Retired’.   
    Since there aren’t any open sessions Weblogic will recognize this and changed the status of the version v1 
  2. Version v1 is deployed and has open sessions. Deploy version v2. The new version v2 will get status ‘Active’ and the old version v1 will stay on status ‘Active’ untill all sessions to it will be closes. After that, Weblogic will change the status to ‘Retired’ and the only ‘Active’ version will be v2 

**Resources**

http://edocs.bea.com/wls/docs100/deployment/redeploy.html#wp1020276

http://weblogic.sys-con.com/node/185310

Filed under [weblogic](http://en.wordpress.com/tag/weblogic/)

<img title="clip_image006" style="display:inline;border-width:0;" height="70" alt="clip_image006" src="http://www.beansoft.biz/wp-content/uploads/2011/04/clip_image006.png" width="70" border="0" />**About Eric Elzinga**   
Eric Elzinga I&#8217;m an integration consultant located in The Netherlands. Mainly doing projects based on Oracle integration stacks (Oracle SOA Suite/Oracle Service Bus (OSB)), Java development, and opensource integration products.

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [WebLogic versioned deployment side-by-side[转]](http://www.beansoft.biz/2011/04/20/weblogic-versioned-deployment-side-by-side%e8%bd%ac/)