---
sidebar_position: 4
title: StatusBar 状态栏
---

### 何时使用
适合页脚显示全局加载信息或滚动加载动效状态场景
### 代码演示
![statusBar demo](../../../static/img/statusBar.png)
<details>
  <summary>代码</summary>
  ```html
  <template>
     <erStatusBar>
      <erRollLoading :loading="true" :outStyleRollLoading="{'margin-right': '80px'}" />
    </erStatusBar>
  </template>
  ```
</details>

### API
### erStatusBar Attributes
|属性名|说明|类型|默认值|
|:------|:------|:------|:------|
|message|全局展示状态信息|string|就绪|
|outStyleStatusBar|状态最外层容器样式|Object|—|
|outStyleMessage|状态信息样式|object|—|

### erRollLoading Attributes
|属性名|说明|类型|默认值|
|:------|:------|:------|:------|
|loading|是否显示滚动加载动效|boolean|false|
|outStyleRollBar|滚动加载动效的样式|Object|—|
|outStyleRollLoading|滚动加载动效容器样式|object|—|