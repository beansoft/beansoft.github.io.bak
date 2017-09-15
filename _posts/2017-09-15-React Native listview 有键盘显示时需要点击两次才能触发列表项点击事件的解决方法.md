---
id: 3939
title: React Native listview 有键盘显示时需要点击两次才能触发列表项点击事件的解决方法
date: 2017-09-15T14:08:38+00:00
author: 刘长炯
layout: post
guid: http://www.beansoft.biz/?p=3939
permalink: '/2017/09/15/React Native listview 有键盘显示时需要点击两次才能触发列表项点击事件的解决方法/'
views:
  - "106"
categories:
  - ReactNative
  
---



  因为listview事实上会自动生成一个scrollview套在最外层. 结果导致首次点击时事件会发送到scrollview上. 

ListView默认生成的scrollview代码如下:

```javascript
<ListView    style={[{flex : 1 ,backgroundColor:'#FAFAFA'}]}
             dataSource={this.state.dataIndexSource}
             enableEmptySections={true}
             onEndReachedThreshold={10}
             renderRow={this._renderRow.bind(this)}
             keyboardDismissMode='on-drag'
             keyboardShouldPersistTaps='always'
/>
```

<http://reactnative.cn/docs/0.44/scrollview.html>

#### keyboardDismissMode enum('none', "interactive", 'on-drag') 

用户拖拽滚动视图的时候，是否要隐藏软键盘。

- none（默认值），拖拽时不隐藏软键盘。
- on-drag 当拖拽开始的时候隐藏软键盘。
- interactive 软键盘伴随拖拽操作同步地消失，并且如果往上滑动会恢复键盘。安卓设备上不支持这个选项，会表现的和none一样。

#### keyboardShouldPersistTaps enum('always', 'never', 'handled', false, true) 

如果当前界面有软键盘，那么点击scrollview后是否收起键盘，取决于本属性的设置。（译注：很多人反应TextInput无法自动失去焦点/需要点击多次切换到其他组件等等问题，其关键都是需要将TextInput放到ScrollView中再设置本属性）

- 'never'（默认值），点击TextInput以外的子组件会使当前的软键盘收起。此时子元素不会收到点击事件。
- 'always'，键盘不会自动收起，ScrollView也不会捕捉点击事件，但子组件可以捕获。
- 'handled'，当点击事件被子组件捕获时，键盘不会自动收起。这样切换TextInput时键盘可以保持状态。多数带有TextInput的情况下你应该选择此项。
- false，已过期，请使用'never'代替。
- true，已过期，请使用'always'代替。