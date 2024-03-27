---
sidebar_position: 1
title: getWorkspaceVariables
---
获取工作区变量列表。
### 示例代码
``` js
let message = await post({
  key: 'checkVar',
  command: 'getWorkspaceVariables',
  filePath: getFilePath(),
})
console.log(message.data.value)
```