## 什么是docsify
 docsify 可以快速帮你生成文档网站。它不会生成静态的 .html 文件，所有转换工作都是在运行时。

## Docsify的特性
+ 无需构建，写完文档直接发布
+ 容易使用并且轻量 (压缩后 ~21kB)
+ 智能的全文搜索
+ 提供多套主题
+ 丰富的 API
+ 支持 Emoji
+ 兼容 IE11
+ 支持服务端渲染 SSR (示例)

## 全局安装docsify
```
npm i docsify-cli -g
```
## 初始化项目
```
docsify init ./docs

```

## 启动
```
docsify serve 
```

## 初始化目录文件
> 这里默认加载为README.md

+ index.html 入口文件

+ README.md 会做为主页内容渲染

+ .nojekyll 用于阻止 GitHub Pages 会忽略掉下划线开头的文件

## 基础配置项
+ 修改index.html 文件
```js
 window.$docsify = {
    name: '',
    loadSidebar: true, // 侧边栏
    loadNavbar: true, // 导航栏
  }
```
