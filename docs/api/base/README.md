---
sidebar_position: 2
title: 基础通信
---
用于 Errantia App 和 Syslab 通信的 api，提供Post函数
## 支持的指令
* `getFilePath` 获取会话临时存储路径
* `importTextFile` 导入文件(读取文件)，返回文本内容
* `excute` 传递代码到 Syslab 运行
* `getWorkspaceVariables` 获取 Syslab 工作区变量列表
### 1 获取会话临时存储文件路径 `getFilePath`, 返回临时存储文件路径
```
let message = await post({
  key: 'filePath',
  command: 'getFilePath'
})
console.log(message.data.value)
// 对外暴露临时存储文件路径
const getFilePath = () => message.data.value;
```

### 2 导入文件(读取文件) `importTextFile`, 返回文本内容
```
let message = await post({
  key: 'importTextFile', // 自定义key，表示此代码执行的任务
  command: 'importTextFile',
  filePath: getFilePath() // 临时存储文件路径
})
console.log(message.data.value)
```

### 3 代码执行 `excute`
```
let message = await post({
  key: key, // 自定义key，表示此代码执行的任务
  command: 'excute', // 
  code: code, // julia执行代码
  filePath: getFilePath(), // 临时存储文件路径
})
console.log(message.data.value)
```

### 4 获取工作区变量列表 `getWorkspaceVariables`
```
let message = await post({
  key: 'checkVar',
  command: 'getWorkspaceVariables',
  filePath: getFilePath(),
})
console.log(message.data.value)
```
:::warning 警告
  post 函数是 Errantia 团队封装在文件 `../request/connectBase` 的函数，需要提前引入，使用 [create-errantia-app](../../plug_app/quick_start/installUse.mdx) 创建的App项目会自动装置。
:::