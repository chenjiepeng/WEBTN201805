# Vuex概述

---

## 什么是 Vuex

* Vuex 是一个专为 Vue.js 应用程序开发的状态管理模式。它采用集中式存储管理应用的所有组件的状态，并以相应的规则保证状态以一种可预测的方式发生变化
* Vuex，有如下两种呈现方式：
  * 独立安装——如Vue.js 组件脚手架;
  * 嵌入在浏览器中的 JS 解释器;

# 使用 Vuex

## 搭建Vuex运行环境

* 方式一：安装独立的Vuex

```js
npm install vuex --save
```

* 方式二：使用客户端加载Vuex

```js
<script src="./js/vuex.js"></script>
<script src="./js/vue2.0.js"></script>
```

## 第一个 Vuex 示例

如何使用Vuex 示例

1. 运行NPM安装 Vuex
2. 注册到 VUE中并且创建Vuex实例
3. 在Vuex实例中创建共享数据与操作数据的方法
4. 其它模块调用

示例：Vuex 共享数据

## 第一个 Vuex 示例

如何使用Vuex 示例

1. **运行NPM安装 Vuex**
2. 注册到 VUE中并且创建Vuex实例
3. 在Vuex实例中创建共享数据与操作数据的方法
4. 其它模块调用

## 运行NPM 安装 Vuex

选择下载镜像

1. cnpmjs镜像  
http://r.cnpmjs.org/
2. 使用taobao 下载 Vuex  
http://registry.npm.taobao.com
3. 配置npm的registry地址  
npm install -g cnpm --registry=https://registry.npm.taobao.org
4. 下载vuex  
cnpm i vuex -S

-S -save #dependencies 生产环  
-D -save-dev #devDependencies 开发环境

## 第一个 Vuex 示例

如何使用Vuex 示例

1. 运行NPM安装 Vuex
2. **注册到 VUE中并且创建Vuex实例**
3. 在Vuex实例中创建共享数据与操作数据的方法
4. 其它模块调用

## 注册到 VUE

在入口文件main.js  
main.js

```js
import Vuex from 'vuex' //导入包  
Vue.use(Vuex)          //在VUE中注册Vuex
```

## 创建 Vuex 实例

在入口文件main.js  
main.js

```js
var store = new Vuex.Store({
  state:{ ...},  //类似data
  mutations:{
    ...         //类似method
  },
  getters:{
    ...
  }
})
```

## 创建 Vuex 实例(续一)

在入口文件main.js  
main.js

```js
import App from './App.vue'
  const vm = new Vue({
  el:"#app"
  render:c=>(App)
  store
})
```

***将 vuex 创建的 store 挂载到 vm 实例上，只要挂载到了 vm 上，任何组件都能使用 store 来存取数据***

## 第一个 Vuex 示例

如何使用Vuex 示例

1. 运行NPM安装 Vuex
2. 注册到 VUE中并且创建Vuex实例**
3. **在Vuex实例中创建共享数据与操作数据的方法**
4. 其它模块调用

## 创建 Vuex 实例

在入口文件main.js  
main.js

```js
var store = new Vuex.Store({
  state:{ count:0}   //count全局共享数据
  mutations:{
    ...
    }
  getters:{
    ...
    }
  })
```

## 创建 Vuex 实例(续一)

在入口文件main.js  
main.js

```js
var store = new Vuex.store({   state:{ count:0}}
mutations:{
  increment(state){  //全局操作共享数据方法
    state.count++
  },
  substract(state){//全局操作共享数据方法
    state.count -=1
  }
}，
})
```

## 创建 Vuex 实例(续二)

在入口文件main.js  
main.js

```js
var store = new Vuex.store({
  ...
    getters:{
      optCout:function(state){//获取数据方法
        return '#'+state.count;
      }
    }
})
```

## 第一个 Vuex 示例

如何使用Vuex 示例

1. 运行NPM安装 Vuex
2. 注册到 VUE中并且创建Vuex实例**
3. 在Vuex实例中创建共享数据与操作数据的方法
4. **其它模块调用**

## 其他模块调用（一）

amount.vue

``` HTML
<template>
  <div>
    <input value="减少"@click="remove">
    <input value="增加"@click="add">
  </div>
</template>
```

## 其他模块调用（二）

amount.vue

``` js
methods: {
  add(){
    this.$store.commit("increment")
  }
  remove(){
    this.$store.commit("substract")
  }
},
```

## 其他模块调用（三）

counter.vue

``` HTML
<template>
  <div>
    //读取数据
    <h3>{{$store.getters.optCount}}</h3>
  </div>
</template>
```

## Vuex 小结

1. sate中的数据，不能直接修改，如果想要修改，必须通过mutations
2. 如果组件想要直接从 state 上获取数据：需要this.$store.state.***
3. 如果组件，想要修改数据，必须使用 mutations 提供的方法，需要通过 this.$store.commit('方法的名称'，唯一的一个参数)
4. 如果 store 中 state 上的数据，在对外提供的时候，需要做一层包装，那么，推荐使用 getters，如果需要使用 getters，则用this.$store.getters.***