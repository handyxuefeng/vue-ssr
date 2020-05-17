## Vue 的SSR有什么优势
- SSR 服务端渲染(页面在服务端渲染后，返回给前端)
- SPA页面<div id='app'></div>无法去爬取dom元素，不利于seo优化
- 多页面有利于seo优化，像原生开发页面可以建立很多html 去实现seo
- vue-server-render  vue实现了可以在node中解析vue 实现将实列渲染成一个字符串

> 预渲染机制(内部启动一个浏览器，生成html 加载这个页面的时候先显示html再进行替换，适合一些静态页面)

## SSR的缺陷
- SSR会占用很多服务器内存，解决方案是缓存，比如redis缓存
- 浏览器一些api无法正常使用  如在vue中 通过ssr渲染时，ajax 一般都写在vue生命周的created

> 页面渲染完后，客户端发起ajax请求数据，用请求来的数据渲染页面(js 很大，首页白屏问题)，服务端在请求数据，把数据塞到页面直接渲染（可以减少白屏时间）

> 通过一份代码打包出 两份代码 -> 用node渲染服务端打包的结果 -> node 渲染出的一个字符串(代码没有交互能力) ->再把一份打包的结果插入到页面中

## 配置一个vue的开发环境
- webpack 打包的
- webpack-cli 解析参数
- webpack-dev-server  webpack开发环境
- vue-loader 用来解析后缀为.vue的文件
- vue-template-loader 解析 template标签
- vue-style-loader 支持服务端渲染
- css-loader 处理css 后，通过vue-style-loader放到style 标签中
- @babel/core babel核心模块  
- @babel/preset-env 高级语法转成成低级语法
- babel-loader 解析js文件
- html-webpack-plugin 打包html 插入到页面中
- webpack-merge webpack 合并文件

## 1.安装服务端代码依赖
```
npm init -y 或者 yarn init
npm install vue vue-server-renderer koa @koa/router nodemon
或者
yarn add vue vue-server-renderer koa @koa/router nodemon

```

## 2.安装客户端依赖

```

yarn add webpack webpack-cli  webpack-dev-server vue-loader vue-template-loader vue-style-loader css-loader @babel/core @babel/preset-env babel-loader html-webpack-plugin webpack-merge

```

## 2.安装前后端都同时打包的依赖
```
yarn add concurrently -D

```

