---
sidebar_position: 1
title: API 说明
---
Syslab 的 API 包括 Syslab 内置提供的 API 以及对Vscode云的端能力 API 的封装。 

其中，对Vscode云的端能力 API 的封装，主要会基于Vscode云的 API 规范，对于其它自定义的 API，会在 Errantia 中适配为 Vscode云 API 的规范格式，并且都挂载在 Window 命名空间下。

例如: 在Web端准备获取与 Syslab 进行通信是API对象
```js
let vscode;
if (window.acquireVsCodeApi) {
  vscode = window.acquireVsCodeApi();
  window.vscode = vscode
} else {
  vscode = window.parent;
}
```
而对于 Errantia App，可以通过 `vscode.postMessage` 发送消息到 Syslab 平台，然后通过 `window.addEventListener('message', event => {...})` ，接收类型为 `receiveData` 来自 Syslab 的消息。

当然，由于 Syslab 平台的迭代非常快速，Errantia 要不断跟进 Syslab 的更新，有时候难免有些 API 没有或者其它功能要加入 Errantia 适配，你可以通过提 PR 或者 issue，来获得帮助。

同时，为了方便代码书写，Errantia 提供了对 Syslab 的异步 API 进行了 promisify 化，你可以像使用 Promise 那样进行调用，例如：
```js
 import { post } from '../request/connectBase' // 文件存在于使用create-errantia-app 创建的项目

 let message = await post({
   key: 'checkVar',
   command: 'getWorkspaceVariables',
   filePath: getFilePath(),
 })
 console.log(message)
```
:::tip 提示
  上面的 `../request/connectBase` 文件，使用 [create-errantia-app](../../plug_app/quick_start/installUse.mdx) 创建的App项目会自动装置。
:::