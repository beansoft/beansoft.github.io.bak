---
id: 3672
title: 'Objective C: NSInteger和int'
date: 2014-05-29T21:00:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3672
permalink: '/2014/05/29/objective-c-nsinteger%e5%92%8cint/'
views:
  - "2937"
categories:
  - iOS
---
<pre class="objectivec" style="box-sizing: border-box; overflow: auto; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 0.92857em; display: block; padding: 10px; margin: 20px 0px; line-height: 1.3; word-break: break-all; word-wrap: break-word; color: #333333; border: 0px; border-top-left-radius: 2px; border-top-right-radius: 2px; border-bottom-right-radius: 2px; border-bottom-left-radius: 2px; max-height: 400px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; widows: auto; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: #f5f5f5;"><span style="color: #333333; font-family: 'Helvetica Neue', Helvetica, 'Trebuchet MS', Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 21px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: auto; word-spacing: 0px; -webkit-text-stroke-width: 0px; display: inline !important; float: none; background-color: #ffffff;">看官方给出的示例代码，一般用于计算的，返回的整数都是用 NSInteger的，但是一般for循环的计数器就都是int了</span>
</pre>

<pre class="objectivec" style="box-sizing: border-box; overflow: auto; font-family: Menlo, Monaco, Consolas, 'Courier New', monospace; font-size: 0.92857em; display: block; padding: 10px; margin: 20px 0px; line-height: 1.3; word-break: break-all; word-wrap: break-word; color: #333333; border: 0px; border-top-left-radius: 2px; border-top-right-radius: 2px; border-bottom-right-radius: 2px; border-bottom-left-radius: 2px; max-height: 400px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; widows: auto; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: #f5f5f5;"><span class="preprocessor" style="box-sizing: border-box; color: #999999; font-weight: bold;">#if __LP64__ || (TARGET_OS_EMBEDDED && !TARGET_OS_IPHONE) || TARGET_OS_WIN32 || NS_BUILD_32_LIKE_64</span>
<span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">typedef</span> <span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">long</span> <span class="built_in" style="box-sizing: border-box; color: #0086b3;">NSInteger</span>;
<span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">typedef</span> <span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">unsigned</span> <span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">long</span> NSUInteger;
<span class="preprocessor" style="box-sizing: border-box; color: #999999; font-weight: bold;">#else</span>
<span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">typedef</span> <span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">int</span> <span class="built_in" style="box-sizing: border-box; color: #0086b3;">NSInteger</span>;
<span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">typedef</span> <span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">unsigned</span> <span class="keyword" style="box-sizing: border-box; color: #333333; font-weight: bold;">int</span> NSUInteger;
<span class="preprocessor" style="box-sizing: border-box; color: #999999; font-weight: bold;">#endif</span>
</pre>

<p style="box-sizing: border-box; margin: 20px 0px; color: #333333; font-family: 'Helvetica Neue', Helvetica, 'Trebuchet MS', Arial, sans-serif; font-size: 14px; font-style: normal; font-variant: normal; font-weight: normal; letter-spacing: normal; line-height: 21px; orphans: auto; text-align: start; text-indent: 0px; text-transform: none; white-space: normal; widows: auto; word-spacing: 0px; -webkit-text-stroke-width: 0px; background-color: #ffffff;">
  这是NSInteger的定义<br style="box-sizing: border-box;" />对于不同平台32,64位有不同的最大值（int long）。<br style="box-sizing: border-box;" />可以直接转化。<br style="box-sizing: border-box;" />所以mac os或者ios上的系统api都是使用NSInteger作为参数。
</p>

附示例代码:

//
  
// **HostEntity.h**
  
//

#import <Foundation/Foundation.h>

@interface HostEntity : NSObject
  
/// 服务器ip
  
@property (strong, nonatomic) NSString *ip;
  
@property (nonatomic) NSInteger port;

@end

**main.m**

#import <Foundation/Foundation.h>
  
#import &#8220;HostEntity.h&#8221;

int main(int argc, const char * argv[])
  
{
  
@autoreleasepool {
  
NSInteger a = 1;
  
NSInteger b = 2;

NSLog(@&#8221;Hello, World!&#8221;);
  
NSLog(@&#8221;Hello, World %li!&#8221;, a+b);

HostEntity *entity = [[HostEntity alloc] init];
  
entity.ip = @&#8221;127.0.0.1&#8243;;
  
[entity setPort:(NSInteger)8080];
  
// 下面两种代码等价, 仅用于属性模式
  
// [entity setPort:[[NSNumber numberWithInt:8090] integerValue]] ;
  
// entity.port = [[NSNumber numberWithInt:8080] integerValue];
  
NSLog(@&#8221;entity.port %ld!&#8221;, (long)[entity port]);

}
  
return 0;
  
}

参考: http://segmentfault.com/q/1010000000124408

转载请注明：[WebLogic Android 博客](http://www.beansoft.biz) &raquo; [Objective C: NSInteger和int](http://www.beansoft.biz/2014/05/29/objective-c-nsinteger%e5%92%8cint/)