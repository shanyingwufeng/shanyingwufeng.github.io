---
title: Vue 移动端项目创建须知
date: 2021-09-14 15:52:53
categories:
- 前端
tags:
- Vue
---

### 移动端 REM 适配

如果需要使用 rem 单位进行适配，推荐使用以下两个工具：

* [lib-flexible](https://github.com/amfe/lib-flexible) 用于设置 rem 基准值
* [postcss-pxtorem](https://github.com/cuth/postcss-pxtorem) 是一款 PostCSS 插件，用于将 px 单位转化为 rem 单位

<!-- more -->

**1、安装 amfe-flexible 依赖**

```
npm install amfe-flexible
```

**2、在  main.js 中加载  amfe-flexible  模块**

```javascript
import 'amfe-flexible'
```

**3、安装 postcss-pxtorem 依赖（将 px 转为 rem）**

```
# -D 是 --save-dev 的简写
npm install postcss-pxtorem -D 
```

**4、PostCSS 配置**

下面提供了一份基本的 PostCSS 示例配置，可以在此配置的基础上根据项目需求进行修改

```javascript
// postcss.config.js（项目根目录创建该文件）
module.exports = {
  plugins: {
    'postcss-pxtorem': {
      rootValue: 37.5,
      propList: ['*'],
    },
  },
};
```

### 项目目录结构

目录包含的文件夹：api、assets、components、router、store、styles、utils、views
