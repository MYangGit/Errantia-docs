---
sidebar_position: 1
title: 目录结构
---
## 项目目录结构
```
├── dist                                  编译结果目录
|
├── src                                   源码目录
|   ├── hooks                             hooks文件目录
|   |   └── useConnectSyslabCenter.js     同Syslab建立读写路径通信示例  
|   |       
|   ├── request                           Syslab通信请求目录
|   |   ├── connectBase.js                与Syslab请求api封装
|   |   └── readme.md                     Syslab请求api文档
|   |       
|   ├── app.vue                           项目入口文件
|   └── main.js                           项目核心文件，入口配置
|
├── .gitignore                            gitCommit忽略文件配置
├── .vscodeignore                         vsce打包忽略文件配置
├── app-icon.png                          Syslab App 显示图标
├── errantia.cjs                          Syslab App 启动与显示信息配置
├── extension.cjs                         vs插件激活运行配置文件
|
├── index.html                            首页入口文件，你可以添加一些 meta 信息或统计代码啥的。
├── tsconfig.json                         TypeScript 配置 （ts模板）
├── package-edit.cjs                      更新package.json配置文件
├── tsconfig.json                         TypeScript 配置 （ts模板）
├── vite.config.js                        vite 配置
|
└── package.json                          npm模板与vs配置文件
```
## 编译配置
```
└──vite.config.js      vite 项目编译配置   
```
## 项目配置
```
├── errantia.cjs      Syslab App 启动与显示信息配置
└──package.json       项目配置 
```
配置好 `errantia.cjs` 后运行 `yarn updata-package` 会自动更新`package.json`文件。