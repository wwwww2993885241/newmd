# Front End Coding Policies 前端编码规范

## HTML规范

### 标签
- 自闭合（self-closing）标签，无需闭合，例如： 
```
    <img>
    <input>
    <br>
    <hr>
```
- 可选的闭合标签（closing tag），需闭合，例如：
```
    </li>
    </body> 
```
- 尽量减少标签数量

### Class 与 ID
- class 应以功能或内容命名，不以表现形式命名。
- class 与 id 单词字母小写，多个单词组成时，采用中划线-分隔。
- 使用唯一的 id 作为 Javascript hook, 同时避免创建无样式信息的 class。

### 属性顺序
HTML 属性应该按照特定的顺序出现以保证易读性。

- id
- class
- name
- data-xxx
- src, for, type, href
- title, alt
- aria-xxx, role

### 嵌套

### HEAD 模板
```
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
    <title>Style Guide</title>
    <meta name="description" content="不超过150个字符">
    <meta name="keywords" content="">
    <meta name="author" content="name, email@gmail.com">

    <!-- 为移动设备添加 viewport -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- iOS 图标 -->
    <link rel="apple-touch-icon-precomposed" href="/apple-touch-icon-57x57-precomposed.png">

    <link rel="alternate" type="application/rss+xml" title="RSS" href="/rss.xml" />
    <link rel="shortcut icon" href="path/to/favicon.ico">
</head>
```

## CSS规范

### 在没有必要的情况下避免元素选择器叠加 Class、ID 使用

### Class 和 ID

- 使用语义化、通用的命名方式。
- 使用连字符 - 作为 ID、Class 名称界定符，不要驼峰命名法和下划线。
- 避免选择器嵌套层级过多，尽量少于 3 级。
- 避免选择器和 Class、ID 叠加使用。

## VUE规范 

### 慎用 this.$refs、this.$parent、this.$root、provide/inject
```
【数据流向】(#数据流向)
【慎用全局注册】(#慎用全局注册)
【组件名称】(#组件名称)
【组件中的 CSS】(#组件中的-css)
【统一标签顺序】(#统一标签顺序)
【其它注意事项】(#其它注意事项)
【 !!!其它则严格遵守 vue 官方风格指南】(#a-target_blank-hrefhttpscnvuejsorgv2style-guide其它则严格遵守-vue-官方风格指南a)
```
### 数据流向
```
props、data/$store/$route、computed (由前面派生)
  ↓
template/render
  ↓
用户交互事件、初始化的异步回调
  ↓
data/$store/$route
```

### 目录结构
```
|-- .env.development ------------ dev 环境变量
|-- .env.development.local ------ dev 本地环境变量 (被 git 忽略，需手动新建，用来重写部分环境变量)
|-- .env.production-stage ------- stage 环境变量
|-- .env.production ------------- prod 环境变量
|-- .env.test
|-- .vscode --------------------- 统一 VSCode 插件及配置
|-- static-server.js ------------ 静态资源服务 (node 运行)，通常用于预览/检查打包结果，或者临时给其他人员启用前端服务
|-- docs ------------------------ 开发文档
|   |-- README.html ------------- 由 ../README.md 手动生成 (使用 VSCode 插件 Markdown Preview Enhanced)
|   |-- xxx.md
|   |-- xxx.html
|-- public
|   |-- favicon.ico
|   |-- index.html
|   |-- libs -------------------- 不支持模块化加载的第三方 ES5 类库/模块 (只能通过全局变量引用)
|-- src
    |-- main.js
    |-- App.vue
    |-- libs -------------------- 支持模块化加载但是无法通过 npm 安装的第三方 ES5 类库/模块
    |-- assets
    |-- styles
    |   |-- global.less
    |   |-- reset.less
    |   |-- vars.less ----------- less 全局变量/函数 (webpack 自动注入)
    |   |-- xxx.less
    |-- scripts
    |   |-- utils --------------- 通用方法
    |   |-- constants ----------- 常量 (多使用 Object.freeze)
    |   |-- xxx.js
    |   |-- http ---------------- axios 实例
    |       |-- index.js
    |       |-- http.js
    |       |-- createAxios.js
    |       |-- xxx.js
    |-- injects ----------------- vue 全局注册 (慎用)
    |   |-- index.js
    |   |-- $xxx.js
    |   |-- v-xxx.js
    |   |-- mixin_xxx.js
    |   |-- xxx.js
    |-- element-ui
    |   |-- index.js
    |   |-- rewrite ------------- 主题样式复写
    |       |-- index.less
    |       |-- xxx.less
    |-- vant
    |   |-- index.js
    |   |-- vars.less ----------- 内置变量复写
    |   |-- rewrite ------------- 主题样式复写
    |       |-- index.less
    |       |-- xxx.less
    |-- router
    |   |-- index.js
    |   |-- routes.js
    |   |-- registerInterceptor.js
    |-- store
    |   |-- index.js
    |   |-- root.js
    |   |-- xxx.js
    |-- api
    |   |-- xxx.js
    |   |-- mock ---------------- 模拟数据
    |       |-- index.js
    |       |-- createMock.js
    |       |-- xxx.js
    |-- components
    |   |-- BaseXxx.vue --------- 非业务通用组件
    |   |-- TheXxx.vue ---------- 单例组件
    |   |-- ExXxx.vue ----------- 扩展/包装第三方开源组件或内部公共库组件
    |   |-- XxxXxx.vue
    |   |-- ComponentExamples --- 非单例公共组件需要在这里写示例
    |   |   |-- index.vue
    |   |   |-- XxxXxx.vue
    |   |-- SvgIcon ------------- svg-sprite 图标组件
    |   |   |-- index.vue
    |   |   |-- icons
    |   |-- directives ---------- 可复用的自定义指令（局部注册）
    |   |   |-- xxx.js
    |   |-- mixins -------------- 可复用的混入（局部注册）
    |       |-- xxx.js
    |-- views
        |-- Xxx.vue
        |-- Xxx ----------------- 除了 api 和 vuex，其它的专属模块要内聚在同一目录下
            |-- index.vue
            |-- Xxx.vue --------- 相关页面/子页面/子路由
            |-- xxx.js
            |-- xxx.module.less
            |-- components ------ 存放私有组件
```
