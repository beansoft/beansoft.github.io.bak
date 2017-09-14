---
id: 1851
title: 用开源软件edtftpj实现FTP文件上传下载,无中文问题
date: 2008-11-26T21:05:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=1851
permalink: '/2008/11/26/%e7%94%a8%e5%bc%80%e6%ba%90%e8%bd%af%e4%bb%b6edtftpj%e5%ae%9e%e7%8e%b0ftp%e6%96%87%e4%bb%b6%e4%b8%8a%e4%bc%a0%e4%b8%8b%e8%bd%bd%e6%97%a0%e4%b8%ad%e6%96%87%e9%97%ae%e9%a2%98/'
views:
  - "3669"
original_post_id:
  - "1851"
image: /wp-content/uploads/2012/09/image_thumb41.png
categories:
  - OpenSource
---
上周给某单位做了一次开发培训, 学员们希望学习用FTP上传下载的Java实现. 上网找了下, 最后找到了两个, 一个是 Apache的Jakarta Commons Net来实现, 其设置选项还是挺多的, 网上的资料也很多, Google一下一大把, 另一个则是[http://www.enterprisedt.com/](http://www.enterprisedt.com/ "http://www.enterprisedt.com/") 开发的一个开源和商业版本的FTP类库, 商业版本支持批量目录的上传和下载. 用的过程中发现了中文问题, 不过最后还是胜利解决了.

&#160;&#160;&#160; 先说一下搭建测试FTP服务器, 一般Windows下用的多的有Server-U(收费)等, 开源的有FileZilla FTP Server(经测试貌似无法上传超过100MB的文件, 不知道哪里有设置, 最后否定了), 目前使用的是一款免费绿色小巧的FTP服务器来做测试: TYPSoft FTP Server. 下载后直接解压缩即可运行, 不过如果要显示中文界面的话, 请修改config.ini:

> LangFile=chineses

之后建立用户进行测试就可以了. 界面如下所示:

[<img title="image" style="display:inline;border-width:0;" height="419" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/03/image_thumb4.png" width="430" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/03/image4.png) 

&#160;

一般的客户端连接中文Windows下的FTP服务器, 默认编码是GB2312, 因此不加设置的话很容易无法上传和下载中文附件. 网上有一些代码片段讨论Jakarta Commons Net, 但是看起来正确的解决此问题的代码不多. 其实FtpClient类已经提供了设置的方法, 调用:

> ftpClient.setControlEncoding("gb2312"); 

即可, 这样在打开Socket的时候都会才用正确的reader和writer了. 相关的源码片段如下:

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;"><span style="color:#008000;">/**</span>
<span style="color:#008000;"> * Sets the character encoding used by the FTP control connection.</span>
<span style="color:#008000;"> * Some FTP servers require that commands be issued in a non-ASCII</span>
<span style="color:#008000;"> * encoding like UTF-8 so that filenames with multi-byte character</span>
<span style="color:#008000;"> * representations (e.g, Big 8) can be specified.</span>
<span style="color:#008000;"> *</span>
<span style="color:#008000;"> * @param encoding The new character encoding for the control connection.</span>
<span style="color:#008000;"> */</span>
<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">void</span> setControlEncoding(String encoding) {
    _controlEncoding = encoding;
}


<span style="color:#008000;">/**</span>
<span style="color:#008000;"> * @return The character encoding used to communicate over the</span>
<span style="color:#008000;"> * control connection.</span>
<span style="color:#008000;"> */</span>
<span style="color:#0000ff;">public</span> String getControlEncoding() {
    <span style="color:#0000ff;">return</span> _controlEncoding;
}</pre>
</div>

&#160;

下面要说的是edtftpj, 去其官方网站下载得到ZIP, 解压缩后即可运行其自带的例子, 不过默认清空下不支持汉字. 例子及压缩包内容如下图所示:

[<img title="image" style="display:inline;border-width:0;" height="359" alt="image" src="http://www.beansoft.biz/wp-content/uploads/2011/03/image_thumb5.png" width="292" border="0" />](http://www.beansoft.biz/wp-content/uploads/2011/03/image5.png) 

可见支持的功能还是挺全面的, 要看的例子就是upload\_download\_and\_delete\_a_file, 现在新建一个Java项目, 把libedtftpj.jar加入项目即可,然后将例子复制进来编译运行, 如下所示:

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;">import com.enterprisedt.net.ftp.FileTransferClient;
import com.enterprisedt.util.debug.Level;
import com.enterprisedt.util.debug.Logger;
import java.io.File;

<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> UploadDownloadFiles {

    <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">static</span> <span style="color:#0000ff;">void</span> main(String[] args) {

        <span style="color:#008000;">// we want remote host, user name and password</span>
        <span style="color:#0000ff;">if</span> (args.length &lt; 3) {
            System.<span style="color:#0000ff;">out</span>
                    .println(<span style="color:#006080;">"Usage: run remote-host username password"</span>);
            System.exit(1);
        }

        <span style="color:#008000;">// extract command-line arguments</span>
        String host = args[0];
        String username = args[1];
        String password = args[2];
        String filename = <span style="color:#006080;">"UploadDownloadFiles.java"</span>;

        <span style="color:#008000;">// set up logger so that we get some output</span>
        Logger log = Logger.getLogger(UploadDownloadFiles.<span style="color:#0000ff;">class</span>);
        Logger.setLevel(Level.INFO);

        FileTransferClient ftp = <span style="color:#0000ff;">null</span>;

        <span style="color:#0000ff;">try</span> {
            <span style="color:#008000;">// create client</span>
            log.info(<span style="color:#006080;">"Creating FTP client"</span>);
            ftp = <span style="color:#0000ff;">new</span> FileTransferClient();

            <span style="color:#008000;">// set remote host</span>
            ftp.setRemoteHost(host);
            ftp.setUserName(username);
            ftp.setPassword(password);

            <span style="color:#008000;">// connect to the server</span>
            log.info(<span style="color:#006080;">"Connecting to server "</span> + host);
            ftp.connect();
            log.info(<span style="color:#006080;">"Connected and logged in to server "</span> + host);

            log.info(<span style="color:#006080;">"Uploading file"</span>);
            ftp.uploadFile(filename, filename);
            log.info(<span style="color:#006080;">"File uploaded"</span>);

            log.info(<span style="color:#006080;">"Downloading file"</span>);
            ftp.downloadFile(filename + <span style="color:#006080;">".copy"</span>, filename);
            log.info(<span style="color:#006080;">"File downloaded"</span>);

            log.info(<span style="color:#006080;">"Deleting remote file"</span>);
            ftp.deleteFile(filename);
            log.info(<span style="color:#006080;">"Deleted remote file"</span>);

            File file = <span style="color:#0000ff;">new</span> File(filename + <span style="color:#006080;">".copy"</span>);
            file.delete();
            log.info(<span style="color:#006080;">"Deleted local file copy"</span>);

            <span style="color:#008000;">// Shut down client</span>
            log.info(<span style="color:#006080;">"Quitting client"</span>);
            ftp.disconnect();

            log.info(<span style="color:#006080;">"Example complete"</span>);

        } <span style="color:#0000ff;">catch</span> (Exception e) {
            e.printStackTrace();
        }
    }

}</pre>
</div>

<div>
  具体操作包括上传,下载,不过当文件名为中文时候, 上传和下载都会出现问题, 报错提示服务器找不到文件. 最终解决方法是继承FileTransferClient,然后获取连接时的配置信息然后修改交互时的字符集:
</div>

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;">import com.enterprisedt.net.ftp.FileTransferClient;

<span style="color:#008000;">/**</span>
<span style="color:#008000;"> * 可以设置连接时的字符集的FTP客户端.</span>
<span style="color:#008000;"> * @author BeanSoft</span>
<span style="color:#008000;"> * 2008-11</span>
<span style="color:#008000;"> */</span>
<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> SetEncodingFileTransferClient extends FileTransferClient {
    <span style="color:#008000;">/**</span>
<span style="color:#008000;">     * 设置连接时的字符集, 默认值是US-ASCII.</span>
<span style="color:#008000;">     * @param controlEncoding 字符集名, 如GB2312等</span>
<span style="color:#008000;">     */</span>
    <span style="color:#0000ff;">public</span> synchronized <span style="color:#0000ff;">void</span> setControlEncoding(String controlEncoding) {
        super.masterContext.setControlEncoding(controlEncoding);
   }
}</pre>
</div>

相应的测试代码是:

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;">import java.io.File;

import com.enterprisedt.util.debug.Level;
import com.enterprisedt.util.debug.Logger;

<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> UploadDownloadFiles {

    <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">static</span> <span style="color:#0000ff;">void</span> main(String[] args) {
        <span style="color:#008000;">// extract command-line arguments</span>
        String host = <span style="color:#006080;">"localhost"</span>;
        String username = <span style="color:#006080;">"test"</span>;
        String password = <span style="color:#006080;">"test"</span>;
        String filename = <span style="color:#006080;">"图片输出.gif"</span>;

        <span style="color:#008000;">// set up logger so that we get some output</span>
        Logger log = Logger.getLogger(UploadDownloadFiles.<span style="color:#0000ff;">class</span>);
        Logger.setLevel(Level.INFO);

        SetEncodingFileTransferClient ftp = <span style="color:#0000ff;">null</span>;

        <span style="color:#0000ff;">try</span> {
            <span style="color:#008000;">// create client</span>
            log.info(<span style="color:#006080;">"Creating FTP client"</span>);
            ftp = <span style="color:#0000ff;">new</span> SetEncodingFileTransferClient();

            <span style="color:#008000;">// set remote host</span>
            ftp.setRemoteHost(host);
            ftp.setUserName(username);
            ftp.setPassword(password);
            ftp.setControlEncoding(<span style="color:#006080;">"GB2312"</span>);

            <span style="color:#008000;">// connect to the server</span>
            log.info(<span style="color:#006080;">"Connecting to server "</span> + host);
            ftp.connect();
            log.info(<span style="color:#006080;">"Connected and logged in to server "</span> + host);

            log.info(<span style="color:#006080;">"Uploading file"</span>);
            ftp.uploadFile(filename, filename);
            log.info(<span style="color:#006080;">"File uploaded"</span>);

            log.info(<span style="color:#006080;">"Downloading file"</span>);
            ftp.downloadFile(filename + <span style="color:#006080;">".copy"</span>, filename);
            log.info(<span style="color:#006080;">"File downloaded"</span>);

            log.info(<span style="color:#006080;">"Deleting remote file"</span>);
            <span style="color:#008000;">//ftp.deleteFile(filename);</span>
            log.info(<span style="color:#006080;">"Deleted remote file"</span>);

            File file = <span style="color:#0000ff;">new</span> File(filename + <span style="color:#006080;">".copy"</span>);
           <span style="color:#008000;">// file.delete();</span>
            log.info(<span style="color:#006080;">"Deleted local file copy"</span>);

            <span style="color:#008000;">// Shut down client</span>
            log.info(<span style="color:#006080;">"Quitting client"</span>);
            ftp.disconnect();

            log.info(<span style="color:#006080;">"Example complete"</span>);

        } <span style="color:#0000ff;">catch</span> (Exception e) {
            e.printStackTrace();
        }
    }

}</pre>
</div>

运行后服务器可看到正确的文件名, 而本机则可以下载到正确的文件副本.

输出日志为:

> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.203 : Creating FTP client
      
>   
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.359 : Connecting to server localhost
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.546 : Connected and logged in to server localhost
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.546 : Uploading file
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.703 : File uploaded
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.703 : Downloading file
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.734 : File downloaded
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.734 : Deleting remote file
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.734 : Deleted remote file
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.734 : Deleted local file copy
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.734 : Quitting client
> 
> INFO [ftp.UploadDownloadFiles] 26 十一月 2008 21:02:48.734 : Example complete</p> 

运行后一切正常, 非常好. 而此软件包的付费版本可支持目录批量上传和下载(Apache Commons Net 貌似不支持), 当然了, 许可证就要自己想办法Crack了:

<div>
  <pre style="font-size:8pt;overflow:visible;width:100%;color:black;line-height:12pt;font-family:consolas, &#039;background-color:#f4f4f4;border-style:none;margin:0;padding:0;">import com.enterprisedt.net.ftp.FTPClient;
import com.enterprisedt.net.ftp.pro.ProFTPClient;
import com.enterprisedt.util.debug.Level;
import com.enterprisedt.util.debug.Logger;
import java.io.File;

<span style="color:#0000ff;">public</span> <span style="color:#0000ff;">class</span> TransferMultipleFilesDirectories {

    <span style="color:#0000ff;">public</span> <span style="color:#0000ff;">static</span> <span style="color:#0000ff;">void</span> main(String[] args) {

        <span style="color:#008000;">// we want remote host, user name and password</span>
        <span style="color:#0000ff;">if</span> (args.length &lt; 5) {
            System.<span style="color:#0000ff;">out</span>
                    .println(<span style="color:#006080;">"Usage: run remote-host username password localdir remotedir"</span>);
            System.exit(1);
        }

        <span style="color:#008000;">// extract command-line arguments</span>
        String host = args[0];
        String username = args[1];
        String password = args[2];
        String localDir = args[3];
        String remoteDir = args[4];

        <span style="color:#008000;">// set up logger so that we get some output</span>
        Logger log = Logger.getLogger(TransferMultipleFilesDirectories.<span style="color:#0000ff;">class</span>);
        Logger.setLevel(Level.DEBUG);

        ProFTPClient ftp = <span style="color:#0000ff;">null</span>;

        <span style="color:#0000ff;">try</span> {
            <span style="color:#008000;">// create client</span>
            log.info(<span style="color:#006080;">"Creating FTP client"</span>);
            ftp = <span style="color:#0000ff;">new</span> ProFTPClient();

            <span style="color:#008000;">// set remote host</span>
            log.info(<span style="color:#006080;">"Setting remote host"</span>);
            ftp.setRemoteHost(host);

            <span style="color:#008000;">// connect to the server</span>
            log.info(<span style="color:#006080;">"Connecting to server "</span> + host);
            ftp.connect();
            log.info(<span style="color:#006080;">"Connected to server "</span> + host);

            <span style="color:#008000;">// log in</span>
            log.info(<span style="color:#006080;">"Logging in with username="</span> + username + <span style="color:#006080;">" and password="</span>
                    + password);
            ftp.login(username, password);
            log.info(<span style="color:#006080;">"Logged in"</span>);

            log.info(<span style="color:#006080;">"Uploading directory"</span>);
            ftp.mput(localDir, remoteDir, <span style="color:#006080;">"*.html"</span>, <span style="color:#0000ff;">true</span>);
            log.info(<span style="color:#006080;">"Directory uploaded"</span>);

            log.info(<span style="color:#006080;">"Downloading directory"</span>);
            ftp.mget(localDir + <span style="color:#006080;">".copy"</span>, remoteDir, <span style="color:#006080;">"*.html"</span>, <span style="color:#0000ff;">true</span>);
            log.info(<span style="color:#006080;">"Directory downloaded"</span>);

            log.info(<span style="color:#006080;">"Deleting remote directory"</span>);
            ftp.rmdir(remoteDir, <span style="color:#0000ff;">true</span>);
            log.info(<span style="color:#006080;">"Remote directory deleted"</span>);

            <span style="color:#008000;">// Shut down client</span>
            log.info(<span style="color:#006080;">"Quitting client"</span>);
            ftp.quit();

            log.info(<span style="color:#006080;">"Example complete"</span>);

        } <span style="color:#0000ff;">catch</span> (Exception e) {
            e.printStackTrace();
        }
    }

}</pre>
</div>

至此, 我们的任务已经完成, 可以加上定时器之类的软件或者类库实现定时同步/备份文件等功能. 想获取本项目源代码? 请点击 [http://cid-519b3f7aa2172030.skydrive.live.com/self.aspx/java/opensource/javaftp.zip](http://cid-519b3f7aa2172030.skydrive.live.com/self.aspx/java/opensource/javaftp.zip "http://cid-519b3f7aa2172030.skydrive.live.com/self.aspx/java/opensource/javaftp.zip") 138KB 下载(单线程下载, 请不要用下载软件如迅雷).

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [用开源软件edtftpj实现FTP文件上传下载,无中文问题](http://www.beansoft.biz/2008/11/26/%e7%94%a8%e5%bc%80%e6%ba%90%e8%bd%af%e4%bb%b6edtftpj%e5%ae%9e%e7%8e%b0ftp%e6%96%87%e4%bb%b6%e4%b8%8a%e4%bc%a0%e4%b8%8b%e8%bd%bd%e6%97%a0%e4%b8%ad%e6%96%87%e9%97%ae%e9%a2%98/)