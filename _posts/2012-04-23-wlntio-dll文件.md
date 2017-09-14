---
id: 2892
title: wlntio.dll文件
date: 2012-04-23T20:53:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2892
permalink: '/2012/04/23/wlntio-dll%e6%96%87%e4%bb%b6/'
views:
  - "4283"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
tags:
  - IO
  - WebLogic
---
wlntio使用 Microsoft Dependency Walker分析的结果，可初步判断是用于操作输入输出的一个本地性能增强库。

D:\bea\wlserver_10.3\server\native\win\32\wlntio.dll

long Java\_weblogic\_socket\_NTSocketMuxer\_getFD(struct JNIEnv_ \*,class \_jclass \*,class \_jobject *)   
void WL\_Init(struct JNIEnv\_ *)   
void WL\_SetIoCompletionDataFields(struct JNIEnv\_ \*,class _jobject \*,int,int,int)   
void WL\_ThrowArrayIndexOutOfBoundsException(struct JNIEnv\_ \*,char const \*)   
void WL\_ThrowIllegalStateException(struct JNIEnv\_ \*,char const \*)   
void WL\_ThrowIoException(struct JNIEnv\_ \*,char const \*)   
void WL\_ThrowNullPointerException(struct JNIEnv\_ \*,char const \*)   
void WL\_ThrowOutOfMemoryError(struct JNIEnv\_ \*,char const \*)   
void WL\_ThrowSocketException(struct JNIEnv\_ \*,char const \*)   
void throwNewAsUnicode(struct JNIEnv_ \*,class _jclass \*,char const *)   
\_Java\_weblogic\_socket\_NTSocketMuxer_addIoRecordArrayChunk@8   
\_Java\_weblogic\_socket\_NTSocketMuxer_copyData@28   
\_Java\_weblogic\_socket\_NTSocketMuxer_getBuildTime@8   
\_Java\_weblogic\_socket\_NTSocketMuxer_getIoCompletionResult@12   
\_Java\_weblogic\_socket\_NTSocketMuxer_initIoRecord@16   
\_Java\_weblogic\_socket\_NTSocketMuxer_initNative@20   
\_Java\_weblogic\_socket\_NTSocketMuxer_initiateNativeIo@12   
\_Java\_weblogic\_socket\_NTSocketMuxer_setDebug@12

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [wlntio.dll文件](http://www.beansoft.biz/2012/04/23/wlntio-dll%e6%96%87%e4%bb%b6/)