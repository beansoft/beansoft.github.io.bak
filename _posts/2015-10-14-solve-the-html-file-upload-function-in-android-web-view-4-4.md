---
id: 3770
title: Solve the html file upload function in android web view 4.4
date: 2015-10-14T20:29:38+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3770
permalink: /2015/10/14/solve-the-html-file-upload-function-in-android-web-view-4-4/
views:
  - "5557"
categories:
  - Android
---
CN:&nbsp;解决Android 4.3 和 4.4 系列中H5不能发起文件上传的BUG

Solution: Using Crosswalk from Intel Open Source

Ref code:&nbsp;https://github.com/dougdiego/CrosswalkDemo

**Ref Article:&nbsp;**

<blockquote data-secret="fd6BIbwZGR" class="wp-embedded-content">
  <p>
    <a href="http://www.mobibrw.com/2015/1934">Crosswalk入门</a>
  </p>
</blockquote>



http://stackoverflow.com/questions/19882331/html-file-input-in-android-webview-android-4-4-kitkat

http://stackoverflow.com/questions/20067508/get-real-path-from-uri-android-kitkat-new-storage-access-framework

And I’ll post the full code later to github, please wait.



Key Code:

package org.diego.android.crosswalkdemo;



import android.app.Activity;

import android.content.Intent;

import android.net.Uri;

import android.os.Bundle;

import android.util.Log;

import android.webkit.ValueCallback;



import org.xwalk.core.XWalkPreferences;

import org.xwalk.core.XWalkResourceClient;

import org.xwalk.core.XWalkUIClient;

import org.xwalk.core.XWalkView;



import java.io.File;





public class XWalkWebViewActivity extends Activity {

&nbsp; &nbsp; class UIClient extends XWalkUIClient {

&nbsp; &nbsp; &nbsp; &nbsp; public UIClient(XWalkView xwalkView) {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; super(xwalkView);

&nbsp; &nbsp; &nbsp; &nbsp; }



&nbsp; &nbsp; &nbsp; &nbsp; public void openFileChooser(XWalkView view,

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ValueCallback<Uri> uploadFile, String acceptType, String capture) {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; super.openFileChooser(view, uploadFile, acceptType, capture);



&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; mFilePathCallback = uploadFile;

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Log.d(&#8220;fchooser&#8221;, &#8220;Opened file chooser.&#8221;);

&nbsp; &nbsp; &nbsp; &nbsp; }



&nbsp; &nbsp; }



&nbsp; &nbsp; private XWalkView xWalkWebView;

&nbsp; &nbsp; private ValueCallback mFilePathCallback;



&nbsp; &nbsp; @Override

&nbsp; &nbsp; protected void onCreate(Bundle savedInstanceState) {

&nbsp; &nbsp; &nbsp; &nbsp; super.onCreate(savedInstanceState);

&nbsp; &nbsp; &nbsp; &nbsp; setContentView(R.layout.activity\_xwalk\_web_view);



&nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView=(XWalkView)findViewById(R.id.xwalkWebView);

&nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView.setUIClient(new UIClient(xWalkWebView));

&nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView.load(&#8220;http://www.google.com&#8221;, null);



&nbsp; &nbsp; &nbsp; &nbsp; // turn on debugging

&nbsp; &nbsp; &nbsp; &nbsp; XWalkPreferences.setValue(XWalkPreferences.REMOTE_DEBUGGING, true);

&nbsp; &nbsp;&nbsp;

&nbsp; &nbsp; }



&nbsp; &nbsp; public void onActivityResult(int requestCode, int resultCode, Intent intent) {

&nbsp; &nbsp; &nbsp; &nbsp; super.onActivityResult(requestCode, resultCode, intent);



&nbsp; &nbsp; &nbsp; &nbsp; if (xWalkWebView != null) {



&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (mFilePathCallback != null) {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Uri result = intent == null || resultCode != Activity.RESULT_OK ? null

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; : intent.getData();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (result != null) {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; File file = ImageUtils.getPhotoFromResult(this, intent);

// &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;String path = ImageUtils.getRealPathFromURI(this, result);

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println(&#8220;上传。。。&#8221; + file);



&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Uri uri = Uri.fromFile(file);

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; mFilePathCallback.onReceiveValue(uri);

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; } else {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; mFilePathCallback.onReceiveValue(null);

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }



&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; mFilePathCallback = null;

&nbsp; &nbsp; &nbsp; &nbsp; }

// &nbsp; &nbsp; &nbsp; &nbsp;xWalkWebView.onActivityResult(requestCode, resultCode, intent); // 加了浏览器就说重复调用, 会崩溃



&nbsp; &nbsp; }



&nbsp; &nbsp; @Override

&nbsp; &nbsp; protected void onPause() {

&nbsp; &nbsp; &nbsp; &nbsp; super.onPause();

&nbsp; &nbsp; &nbsp; &nbsp; if (xWalkWebView != null) {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView.pauseTimers();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView.onHide();

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; }



&nbsp; &nbsp; @Override

&nbsp; &nbsp; protected void onResume() {

&nbsp; &nbsp; &nbsp; &nbsp; super.onResume();

&nbsp; &nbsp; &nbsp; &nbsp; if (xWalkWebView != null) {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView.resumeTimers();

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView.onShow();

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; }



&nbsp; &nbsp; @Override

&nbsp; &nbsp; protected void onDestroy() {

&nbsp; &nbsp; &nbsp; &nbsp; super.onDestroy();

&nbsp; &nbsp; &nbsp; &nbsp; if (xWalkWebView != null) {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; xWalkWebView.onDestroy();

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; }



}



To reduce the app file path, please add following code to build.grade:



&nbsp; &nbsp; productFlavors {

&nbsp; &nbsp; &nbsp; &nbsp; armv7 {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ndk {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; abiFilters &#8220;armeabi-v7a&#8221;, &#8220;&#8221;

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; x86 {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ndk {

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; abiFilters &#8220;x86&#8221;, &#8220;&#8221;

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; &nbsp; &nbsp; }

&nbsp; &nbsp; }

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Solve the html file upload function in android web view 4.4](http://www.beansoft.biz/2015/10/14/solve-the-html-file-upload-function-in-android-web-view-4-4/)