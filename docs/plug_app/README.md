<!-- <p align="center">
  <a href="#">
    <img width="200" src="./public/logo.png">
  </a>
  <h1 align="center">TyComponents</h1>
  <p align="center">一套支持建模与仿真的组件库</p>
</p> -->

## 用户手册

* [1. 特性](#1-特性-top)
* [2. 环境](#2-环境-top)
* [3. 安装](#3-安装-top)
* [4. 使用](#4-使用-top)
* [5. 组件](#5-组件-top)
    * [5.1 TyLoading](#51-tyloading-top)
    * [5.2 TyDocument](#52-tydocument-top)
    * [5.3 TyModelParams](#53-tymodelparams-top)
    * [5.4 TyModelAttributes](#54-tymodelattributes-top)
    * [5.5 TySvgViewer](#55-tysvgviewer-top)
    * [5.6 TyChart](#56-tychart-top)
    * [5.7 TyModelText](#57-tymodeltext-top)

## 1. 特性 [:top:](#用户手册)

- 📦 开箱即用的高质量建模与仿真组件。
- 🌍 中英文语言支持。

## 2. 环境 [:top:](#用户手册)

- 除IE外的现代浏览器

## 3. 安装 [:top:](#用户手册)

``` bash
$ npm install TyComponents -S
```
## 4. 使用 [:top:](#用户手册)

在 `main.js` 文件中引入插件并注册

``` bash
# main.js
import TyComponents from 'TyComponents'
Vue.use(TyComponents)
```

在项目中使用 TyComponents

```js
<template>
  <TyLoading :visible="visible" />
</template>
<script>
  export default {
    data () {
      return {
        visible: true
      }
    }
  }
</script>
```
## 5. 组件 [:top:](#用户手册)

| 组件名称   | 说明  
|------|------|
| TyLoading | 一个展示Loading状态的组件，用于mols的连接过程
| TyDocument | 一个支持对模型的html数据格式文档的预览的组件
| TyModelParams | 一个支持对模型组件的参数进行设置的组件
| TyModelAttributes | 一个支持对模型的仿真属性进行设置的组件
| TySvgViewer | 一个用于展示模型图形的组件
| TyChart | 一个用于展示仿真结果曲线的组件
| TyModelText | 一个支持以代码的形式查看模型文本内容的组件

### 5.1 TyLoading [:top:](#用户手册)
  TyLoading支持等待状态、失败状态和成功状态的自定义，也可以控制组件的显示及当前进度的设置。
#### 示例
<!-- <p align="center">
  <img width="400" src="./public/TyLoading.png">
</p> -->

#### 使用方法
```js
<TyLoading :visible="visible" />
```

#### 属性
| 参数             | 说明                                 | 类型            | 可选值        | 默认值       |
|------------------|------------------------------------|-----------------|---------------|--------------|
| visible          | 控制组件的显示                   | boolean | true/false            | false           |
| percentage      | 当前的进度值                 | number  | 0~100           | 0           |
| status     | 当前的状态                 | number          | 100, 101, 102, 103, 104, 105, 106            | 100         |
| waitColor        | 等待状态的背景色                     | string          | 颜色值 | #e6a23c       |
| successColor | 成功状态的背景色                       | string         | 颜色值    | green        |
| failColor       | 失败状态的背景色                         | string      | 颜色值           | red   |

  status各状态码详解：
| 状态码             | 说明                     
|------------------|------------------------
| 100          | 正在启动服务...       
| 101      | 服务启动失败，请刷新重试        
| 102     | 服务启动成功，正在进行连接...                 
| 103        | 服务连接失败，请刷新重试或检查网络状态                
| 104 | 服务连接成功，正在加载模型...           
| 105       | 模型加载失败，请刷新重试       
| 106       | 模型加载成功，即将进入建模空间...     

### 5.2 TyDocument [:top:](#用户手册)
  TyDocument支持对模型的html数据格式文档的预览。
#### 示例
<!-- <p align="center">
  <img width="700" src="./public/TyDocument.png">
</p> -->

#### 使用方法
```js
<TyDocument :data="data" />
```

#### 属性
| 参数             | 说明                                 | 类型            | 可选值        | 默认值       |
|------------------|------------------------------------|-----------------|---------------|--------------|
| data          | 模型文档的html数据                   | string |      --       |    --       |
 
#### 方法
| 方法名             | 说明                                 | 参数            |
|------------------|------------------------------------|-----------------|
| clearFileName          | 清除文档里的文件名称                   | -- |

### 5.3 TyModelParams [:top:](#用户手册)
  TyModelParams支持对模型组件的参数进行设置。
#### 示例
<!-- <p align="center">
  <img width="700" src="./public/TyModelParams.png">
</p> -->

#### 使用方法
```js
<TyModelParams :data="data" />
```

#### 属性
| 参数             | 说明                                 | 类型            | 可选值        | 默认值       |
|------------------|------------------------------------|-----------------|---------------|--------------|
| data          | 组件的参数数组数据                   | array |      --       |    --       |

#### 事件
| 事件名             | 说明                                 | 回调参数            |
|------------------|------------------------------------|-----------------|
| refreshModel          | 参数更新事件                   | 当前修改的配置项的名称和值， { 'paramName', 'paramValue'} |
| changeUnit          | 参数单位改变事件                   | 当前修改的配置项的名称和单位， { 'paramName', 'newParameterUnit' } |
 
#### 方法
| 方法名             | 说明                                 | 参数            |
|------------------|------------------------------------|-----------------|
| setActiveName          | 设置当前Tab页签                   | value: Tabs页签的name |

### 5.4 TyModelAttributes [:top:](#用户手册)
  TyModelAttributes支持对模型的仿真属性进行设置。
#### 示例
<!-- <p align="center">
  <img width="700" src="./public/TyModelAttributes.png">
</p> -->

#### 使用方法
```js
<TyModelParams :data="data" />
```

#### 属性
| 参数             | 说明                                 | 类型            | 可选值        | 默认值       |
|------------------|------------------------------------|-----------------|---------------|--------------|
| projectData          | 模型详情数据                   | object |      --       |    --       |

#### 事件
| 事件名             | 说明                                 | 回调参数            |
|------------------|------------------------------------|-----------------|
| updateSimulateData          | 数据更新事件                   | 表单数据 |
 
#### 方法
| 方法名             | 说明                                 | 参数            |
|------------------|------------------------------------|-----------------|
| handleConfirm          | 提交仿真属性设置表单             | -- |

### 5.5 TySvgViewer [:top:](#用户手册)
  TySvgViewer支持以图形的方式查看模型。
#### 示例
```js
<p align="center">
  <img width="700" src="./public/TySvgViewer.png">
</p>
```

#### 使用方法
```js
<TySvgViewer :value="value" />
```

#### 属性
| 参数             | 说明                                 | 类型            | 可选值        | 默认值       |
|------------------|------------------------------------|-----------------|---------------|--------------|
| value          | 模型的图形数据                   | object |      --       |    --       |

#### 事件
| 事件名             | 说明                                 | 回调参数            |
|------------------|------------------------------------|-----------------|
| click          | 画布上的组件的点击事件                   | 当前点击的组件的id |
| dbclick          | 画布上的组件的双击事件                   | 当前双击的组件的id |
 
#### 方法
| 方法名             | 说明                                 | 参数            |
|------------------|------------------------------------|-----------------|
| clearSelect          | 清空选中效果             | -- |
| zoomIn          | 缩小视图             | -- |
| zoomOut          | 放大视图             | -- |
| zoomRecovery          | 重置视图             | -- |

### 5.6 TyChart [:top:](#用户手册)
  TyChart支持以图表的形式查看仿真结果，基于Echarts实现，其大小随容器的大小自适应变化。
#### 示例
<!-- <p align="center">
  <img width="700" src="./public/TyChart.png">
</p> -->

#### 使用方法
```js
<TyChart :data="data" :options="options" />
```

#### 属性
| 参数             | 说明                                 | 类型            | 可选值        | 默认值       |
|------------------|------------------------------------|-----------------|---------------|--------------|
| data          | 模型的图形数据                   | object |      --       |    --       |
| options          | 图表的配置项                 | object |      --       |    --       |

  options配置项详解：
| 状态码             | 说明                     
|------------------|------------------------
| showLineMenu          | 是否展示曲线右键菜单       
| showChartMenu      | 是否展示图表右键菜单       
| showDeleteMenu     | 是否展示删除曲线功能的右键菜单                 
| showUnitMenu        | 是否展示切换单位功能的右键菜单              
| showAxisMenu     | 是否展示切换坐标轴位置功能的右键菜单          
| showStyleMenu       | 是否展示改变曲线样式功能的右键菜单    
| showAttrMenu       | 是否展示配置属性功能的右键菜单 
| showZoomMenu     | 是否展示缩放功能的右键菜单                 
| showRangeMenu        | 是否展示设置范围功能的右键菜单              
| showTipMenu     | 是否展示切换游标功能的右键菜单          
| showGridMenu       | 是否展示切换网格功能的右键菜单    
| showSelectMenu       | 是否展示选择功能的右键菜单 

#### 事件
| 事件名             | 说明                                 | 回调参数            |
|------------------|------------------------------------|-----------------|
| ready          | 图表渲染完成的回调                   | -- |
| legendClick          | 图表上的标题的点击事件                   | options中对应的serie数据 |
 
### 5.7 TyModelText [:top:](#用户手册)
  TyModelText支持以代码的形式查看模型文本内容，基于codeMirror实现。
#### 示例
<!-- <p align="center">
  <img width="700" src="./public/TyModelText.png">
</p> -->

#### 使用方法
```js
<TyModelText :data="data" />
```

#### 属性
| 参数             | 说明                                 | 类型            | 可选值        | 默认值       |
|------------------|------------------------------------|-----------------|---------------|--------------|
| data          | 模型文本内容                   | string |      --       |    --       |

#### 事件
| 事件名             | 说明                                 | 回调参数            |
|------------------|------------------------------------|-----------------|
| change          | 文本改变事件                   | 修改后的文本内容 |