---
id: 3941
title: React Native 集成 HttpDNS
date: 2017-09-15T18:00:38+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3941
permalink: '/2017/09/15/React-Native-HttpDNS/'
views:
  - "106"
categories:
  - ReactNative
  
---

这个功能暂时还没有完全开发完成, 完成后会发布开源版本.

这里只列一些参考资料, Android的版本相对容易解决, 参考网易新闻客户端一位安卓开发者的文章: [https-httpDNS遇到的那些坑](http://glanwang.com/2016/12/21/Android/https-httpDNS%E9%81%87%E5%88%B0%E7%9A%84%E9%82%A3%E4%BA%9B%E5%9D%91/) . 

iOS的则因为无法替换系统的域名解析, 目前市面上的腾讯云和阿里云都是通过替换为IP直连+Host头的方式解决. 由于Apple不允许应用使用Http协议, 只能用Https, 那么SSL的证书验证失败就成了一个迈不过去的坎. 解决方案参考文档: [https://www.qcloud.com/document/product/379/6471]( https://www.qcloud.com/document/product/379/6471)腾讯云免费版API接入  [https://github.com/tencentyun/httpdns-ios-sdk](https://github.com/tencentyun/httpdns-ios-sdk) 腾讯云ios Demo

最后则是需要集成到React Native中, 安卓需要替换 MainReactPackage 为自己的实现, 只为了覆盖 NetworkingModule 中的 OKHttpClient, 核心代码如下:

```java
package com.facebook.react.modules.network;// 必须放入这个包名, 否则无法调用NetworkingModule的包私有构造器

/**
 * Package defining basic modules and view managers.
 * 代码复制自 MainReactPackage, 需要进行修改.
 */
public class HackNetWorkMainReactPackage extends LazyReactPackage {

@Override
public List<ModuleSpec> getNativeModules(final ReactApplicationContext context) {
  return Arrays.asList(
    ... // 其它系统Module
    new ModuleSpec(NetworkingModule.class, new Provider<NativeModule>() {
      @Override
      public NativeModule get() {
        return new NetworkingModule(context, "app/corpapp", OkHttpClientProvider.getOkHttpClient());
      }
    }),
    ...
    }
```

然后在自己的应用Application中最早执行如下示意代码:

```java
public class MainApplication extends NavigationApplication {

    @Override
    public boolean isDebug() {
        return BuildConfig.DEBUG;
    }

    @Override
    public void onCreate() {
        OkHttpClient client = createClient();
        if(client != null) {
            OkHttpClientProvider.replaceOkHttpClient(client);
        }
        super.onCreate();
      ...
    }
  
    public static OkHttpClient createClient() {
        OkHttpClient client = OkHttpClientProvider.getOkHttpClient();
        if (client != null) {
            OkHttpClient.Builder clientBuilder = client.newBuilder();
            client = clientBuilder.dns(new HttpDns()).build();
            return client;
        } else {
            return null;
        }
    }
```

类 HttpDns 实现了使用Http进行域名解析的逻辑.

iOS的仍然在研发中.



参考资料:

[从理论到实践，全方位认识DNS（理论篇）](https://www.cloudxns.net/Support/detail/id/737.html)

[HTTPDNS 在 iOS 中的实践](http://nathanli.cn/2016/12/20/httpdns-%E5%9C%A8-ios-%E4%B8%AD%E7%9A%84%E5%AE%9E%E8%B7%B5/) 