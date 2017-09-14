---
id: 2031
title: 'weblogic.security.internal.encryption.EncryptionServiceException: com.rsa.jsafe.JSAFE_PaddingException: Could not perform unpadding: invalid pad byte'
date: 2011-06-16T21:23:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=2031
permalink: /2011/06/16/weblogic-security-internal-encryption-encryptionserviceexception-com-rsa-jsafe-jsafe_paddingexception-could-not-perform-unpadding-invalid-pad-byte/
views:
  - "15432"
original_post_id:
  - "2031"
image: /wp-content/uploads/2012/04/WebLogic.png
categories:
  - WebLogic
---
<p style="MARGIN: 0cm 0cm 0pt">
  weblogic.security.internal.encryption.EncryptionServiceException: com.rsa.jsafe.JSAFE_PaddingException: Could not perform unpadding: invalid pad byte
</p>

<p style="MARGIN: 0cm 0cm 0pt">
  <p style="MARGIN: 0cm 0cm 0pt">
    <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
      本文内容适用于WebLogic 9.x, 10.x. 作者: BeanSoft.biz <strong>禁止转载</strong>.
    </p>
    
    <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
      有时候,复制config.xml到其它一个WebLogic Domain下修改后启动(通常用于手动复制集群节点的操作), 或者Domain中的文件遭到了部分损坏, 那么启动过程中, 会在出现Security错误后,服务器进入强制退出状态, 一份可能的log如下所示:
    </p>
    
    <table cellpadding="0" width="400" style="WIDTH: 300pt; mso-padding-alt: 1.5pt 1.5pt 1.5pt 1.5pt; mso-cellspacing: 0cm; mso-yfti-tbllook: 1184" border="0" cellspacing="0">
      <tr style="mso-yfti-irow: 0; mso-yfti-firstrow: yes; mso-yfti-lastrow: yes">
        <td width="400" style="BORDER-BOTTOM: #d4d0c8; BORDER-LEFT: #d4d0c8; PADDING-BOTTOM: 1.5pt; BACKGROUND-COLOR: transparent; PADDING-LEFT: 1.5pt; WIDTH: 300pt; PADDING-RIGHT: 1.5pt; BORDER-TOP: #d4d0c8; BORDER-RIGHT: #d4d0c8; PADDING-TOP: 1.5pt" valign="top">
          <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
            <2011-6-25 下午09时57分30秒 CST> <Critical> <WebLogicServer> <BEA-000386> <Server subsystem failed. <br />Reason: java.lang.AssertionError: java.lang.reflect.InvocationTargetException <br />java.lang.AssertionError: java.lang.reflect.InvocationTargetException <br />at weblogic.descriptor.DescriptorManager$SecurityServiceImpl$SecurityProxy._invokeServiceMet <br />hod(DescriptorManager.java:175) <br />at weblogic.descriptor.DescriptorManager$SecurityServiceImpl$SecurityProxy.decrypt(Descripto <br />rManager.java:192) <br />at weblogic.descriptor.DescriptorManager$SecurityServiceImpl.decrypt(DescriptorManager.java: <br />114) <br />at weblogic.descriptor.internal.AbstractDescriptorBean._decrypt(AbstractDescriptorBean.java: <br />1092) <br />at weblogic.management.configuration.SecurityConfigurationMBeanImpl.getCredential(SecurityCo <br />nfigurationMBeanImpl.java:736) <br />Truncated. see log file for complete stacktrace <br />Caused By: java.lang.reflect.InvocationTargetException <br />at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) <br />at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39) <br />at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25) <br />at java.lang.reflect.Method.invoke(Method.java:597) <br />at weblogic.descriptor.DescriptorManager$SecurityServiceImpl$SecurityProxy._invokeServiceMet <br />hod(DescriptorManager.java:173) <br />Truncated. see log file for complete stacktrace <br />Caused By: weblogic.security.internal.encryption.EncryptionServiceException: com.rsa.jsafe.JSAFE_Pad <br />dingException: Could not perform unpadding: invalid pad byte. <br />at weblogic.security.internal.encryption.JSafeEncryptionServiceImpl.decryptBytes(JSafeEncryp <br />tionServiceImpl.java:136) <br />at weblogic.security.internal.encryption.JSafeEncryptionServiceImpl.decryptString(JSafeEncry <br />ptionServiceImpl.java:184) <br />at weblogic.security.internal.encryption.ClearOrEncryptedService.decrypt(ClearOrEncryptedSer <br />vice.java:96) <br />at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) <br />at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39) <br />Truncated. see log file for complete stacktrace <br /><strong>Caused By: com.rsa.jsafe.JSAFE_PaddingException: Could not perform unpadding: invalid pad byte. <br />at com.rsa.jsafe.c.a(Unknown Source) <br /></strong> <strong>at com.rsa.jsafe.JSAFE_SymmetricCipher.decryptFinal(Unknown Source)</strong> <br />at weblogic.security.internal.encryption.JSafeEncryptionServiceImpl.decryptBytes(JSafeEncryp <br />tionServiceImpl.java:124) <br />at weblogic.security.internal.encryption.JSafeEncryptionServiceImpl.decryptString(JSafeEncry <br />ptionServiceImpl.java:184) <br />at weblogic.security.internal.encryption.ClearOrEncryptedService.decrypt(ClearOrEncryptedSer <br />vice.java:96) <br />Truncated. see log file for complete stacktrace <br />> <br /><2011-6-25 下午09时57分30秒 CST> <Notice> <WebLogicServer> <BEA-000365> <Server state changed to FAI <br />LED> <br /><2011-6-25 下午09时57分30秒 CST> <Error> <WebLogicServer> <BEA-000383> <A critical service failed. T <br />he server will shut itself down> <br /><2011-6-25 下午09时57分30秒 CST> <Notice> <WebLogicServer> <BEA-000365> <Server state changed to FOR <br />CE_SHUTTING_DOWN>
          </p>
        </td>
      </tr>
    </table>
    
    <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        Log中粗体的的部分显示了出错的真正原因是在JSAFE包中进行解密(decrypt)时报错, 而调用此功能的是WebLogic安全模块的解密字符串方法. JSafe是rsa公司出品的一个收费的加密解密安全相关的软件包. 后台细节不必深究, 我们只需要关注解密字符串的部分即可. 首先需要指出的是密码加密后的内容只和文件 $DOMAIN_HOME/security/<strong>SerializedSystemIni.dat</strong> 相关.
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        解决方法1: 修改config.xml中的加密内容.
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        首先, 必须找一份能正常运行的Domain文件, 然后使用 <a href="http://www.beansoft.biz/?p=1813">如何破解WebLogic管理密码?</a> 中提到的解密工具, 来得到原始密码.
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        需要解密的config.xml中的内容如下粗体部分所示:
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        <default-realm>myrealm</default-realm> <br /><strong>(1)</strong> <credential-encrypted>{AES}QIo54gGfn2Y+y62DqTCE7Q01ll5DF48PbAI1gBX22wR8sWEuVlvdHXSc9kDAfknTJGfo1n1bO/RxkYMogv4XNZ4bFTmbAe1zYfpsBtSFbzI97Y2HE3lwd5c9dv9gDISU</credential-encrypted> <br /><node-manager-username>weblogic</node-manager-username> <br /><strong>(2)</strong> <node-manager-password-encrypted>{AES}stQ8+dVzw1jEDpF4xj+ub1m460793ijKqI0YBhpkZNE=</node-manager-password-encrypted>
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        &#8230;.
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        <embedded-ldap> <br /><name>1034</name> <br /><strong>(3)</strong> <strong><credential-encrypted>{AES}OYLOL/6/sVdiwG/rkqTj8U2TdFUXIa9PgZRzWKlJqju1cVvUFKcWzqir1N4qtQHy</credential-encrypted> <br /></strong> </embedded-ldap>
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        (1) 解密后的内容是WebLogic启动密码, (2), (3) 则为数字(似乎是随机的内容).
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        然后需要动用WebLogic自带的明文加密工具weblogic.security.Encrypt, 在新的Domain中得出这几个密码的新内容并替换到正确的位置中. 相关文档请访问 <a href="http://download.oracle.com/docs/cd/E11035_01/wls100/admin_ref/utils.html#wp1209592">http://download.oracle.com/docs/cd/E11035_01/wls100/admin_ref/utils.html#wp1209592</a>.
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        如果boot.properties有类似问题, 使用相同方法处理后即可.
      </p>
      
      <p style="TEXT-ALIGN: left; MARGIN: 7.5pt 0cm; mso-pagination: widow-orphan">
        解决方法2: 替换新Domain中的 <strong>SerializedSystemIni.dat</strong> 为能正常运行的Domain中的相同文件, 此方法步骤最简单(不推荐, 可能有安全隐患).
      </p>
      
      <p style="MARGIN: 0cm 0cm 0pt">
        <p style="MARGIN: 0cm 0cm 0pt">
          <p>
            转载请注明：<a href="http://www.beansoft.biz">WebLogic Android 博客</a> &raquo; <a href="http://www.beansoft.biz/2011/06/16/weblogic-security-internal-encryption-encryptionserviceexception-com-rsa-jsafe-jsafe_paddingexception-could-not-perform-unpadding-invalid-pad-byte/">weblogic.security.internal.encryption.EncryptionServiceException: com.rsa.jsafe.JSAFE_PaddingException: Could not perform unpadding: invalid pad byte</a>
          </p>