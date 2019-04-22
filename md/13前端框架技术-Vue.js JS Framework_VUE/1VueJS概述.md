# 概述

---

## 概述

  * Vue.js 是一套构建用户界面的**渐进式框架**
  * 特点
    * 响应式编程
    * 组件化
    * 轻量
    * 模块化
    * 简洁
  * Vue.js技术栈
    * Vue-cli
    * Vue-router
    * vuex
    * ES6
    * NPM
    * Webpack
    * Babel
    * weex

## 环境搭建

  * 方案1：直接用`<script>`引入
    * 官网下载独立的js文件
    * https://cn.vuejs.org/v2/guide/installation.html
  * script标签引入的vue.js文件会创建window.Vue对象
  * 方案2：命令行工具（CLI）
    * Vue.js提供的官方命令行工具（https://cli.vuejs.org/）,可
    用于快速搭建大型单页应用。该工具提供开箱借用的构建
    工具配置，带来现代化的前端开发流程，使用步骤如下：

    ```cmd
    #1.全局安装 vue-cli
          npm install -g @vue/cli
    #2.创建一个新的空白项目，并下载依赖的模块
          vue create my-project
    #3.进入项目目录，并运行该项目
          cd my-project
          npm run serve
    ```

      注意：不同版本的Vue-CLI工具的使用方法差别比较大

### VueJS 环境搭建

  * VueJS环境搭建
  
# Vue.js基础

---

## Vue基础

  * Vue.js 的核心是一个允许采用简洁的模板语法来声明式的将数据渲染进 DOM

    ```vue
    <div id="app">
    {{ message }}
    </div>

    var vm= new Vue({
      el:'#app',
      data:{
        message:'Hello Vue!'
        }
    })
    ```

### Hello Vue

  * 创建第一个VueJS 应用