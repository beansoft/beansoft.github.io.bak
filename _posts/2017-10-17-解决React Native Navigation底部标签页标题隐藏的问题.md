---
id: 3941
title: 解决React Native Navigation底部标签页标题隐藏的问题
date: 2017-10-17T16:00:00+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3942
permalink: '/2017/09/15/React-Native-Navigation-Bottom-Title-Hidden/'
views:
  - "106"
categories:
  - ReactNative
  
---

开发中遇到了一个奇怪的问题, React Native Navigation 底部初始化了4个标签页的时候, 只会显示当前选中的标签页的标签标题, 其它几个标签的标题则隐藏了.

参考官方文档:

# [修改标签页的样式](https://pilipa-cn.github.io/react-native-navigation/#/styling-the-tab-bar?id=%e4%bf%ae%e6%94%b9%e6%a0%87%e7%ad%be%e9%a1%b5%e7%9a%84%e6%a0%b7%e5%bc%8f)

You can style the tab bar appearance by passing a `tabsStyle` object when the app is originally created (on `startTabBasedApp`).

```javascript
Navigation.startTabBasedApp({
  tabs: [ ... ],
  tabsStyle: { // optional, **iOS Only** add this if you want to style the tab bar beyond the defaults
    tabBarButtonColor: '#ff0000'
  }
});
```

#### [Style object format](https://pilipa-cn.github.io/react-native-navigation/#/styling-the-tab-bar?id=style-object-format)

```javascript
{
  tabBarHidden: false, // make the tab bar hidden
  tabBarButtonColor: '#ffff00', // change the color of the tab icons and text (also unselected)
  tabBarSelectedButtonColor: '#ff9900', // change the color of the selected tab icon and text (only selected)
  tabBarBackgroundColor: '#551A8B' // change the background color of the tab bar
  tabBarTranslucent: false // change the translucent of the tab bar to false
  tabBarTextFontFamily: 'Avenir-Medium' //change the tab font family
  tabBarLabelColor: '#ffb700', // iOS only. change the color of tab text
  tabBarSelectedLabelColor: 'red', // iOS only. change the color of the selected tab text
  forceTitlesDisplay: true // Android only. If true - Show all bottom tab labels. If false - only the selected tab's label is visible.
  tabBarHideShadow: true // iOS only. Remove default tab bar top shadow (hairline)
  forceTitlesDisplay: true // Android only. If true - Show all bottom tab labels. If false - only the selected tab's label is visible.
}
```

On Android, add BottomTabs styles to `AppStyle`:

```javascript
Navigation.startTabBasedApp({
  tabs: [...],
  appStyle: {
    tabBarBackgroundColor: '#0f2362',
    tabBarButtonColor: '#ffffff',
    tabBarSelectedButtonColor: '#63d7cc',
    tabBarTranslucent: false,
    tabFontFamily: 'Avenir-Medium.ttf'  // for asset file or use existing font family name
  },
...
}
```

最终解决很简单:

appStyle中加入一行 `forceTitlesDisplay: true // Android only. If true - Show all bottom tab labels. If false - only the selected tab's label is visible.` 即可