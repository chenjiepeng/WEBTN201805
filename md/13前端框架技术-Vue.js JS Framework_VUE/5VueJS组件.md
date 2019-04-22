# 组件中的路由

---

## 路由机制

  * 在VueJS中的路由，可以通过Vue-Router来处理
    * https://router.vuejs.org/
    * vue-router是Vue.js官方的路由插件，它和vue.js是深度集
    成的，适合用于构建单页面应用。
    * vue的单页面应用是基于路由和组件的，路由用于设定访
    问路径，并将路径和组件映射起来 传统的页面应用，是
    用一些超链接来实现页面切换和跳转的 在vue-router单
    页面应用中，则是路径之间的切换，也就是组件的切换。

## 路由实现的基本步骤

路由实现的基本步骤

  * 指定一个盛放组件的容器
    * `<router-view></router-view>`
  * 创建各个组件
  * 配置路由词典
  * 访问指定路由下的组件
      超链接
      编程导航

## 配置路由词典

  * 配置路由词典时，需要有vue-router的模块；然后引入
    进来，才可以配置

      ```vue
      import Router from 'vue-router';

      Vue.use(Router);

      export default new Router({
        routes:[
          { path:'/start',component: Start }
          { path:'/main',component: Main }
        ]
      })
      ```

## 路由跳转

  * 3种基本方式
    * 超链接
    * router-link
    * js

    ```vue
    超链接：
    <a href= "#/foo">jump to foo</a>

    自定义指令跳转：
    <router-link to="/foo">Go to Foo</router-link>

    js跳转：
    this.router.navigateByUrl('/foo')
    ```

### 使用VueRouter来实现一个SPA

  * 创建2个代码片段
    * Login.html Register.html
    * Login上按钮，在点击时跳转到Register
    * Register上放超链接，点击跳转到Login

## 路由跳转传参

  * 基本步骤
    * 明确发送方、接收方
    * 配置接收方的参数
    * 发送参数

    ```vue
    配置接收方的路由:
    { path: '/detail/:id', component:Detail }

    接受参数:
    this.$route.params.id

    发送参数:
    this.router.navigateByUrl('/detail/' + id)
    ```

### 使用VueRouter来实现传参SPA

  * 创建3个代码片段
    * Check.html Pay.html Send.html
    * Check上按钮，在点击时跳转到Pay，并发送参数
    * Pay接受参数并显示，放超链接，点击跳转到Send
    * Send放超链接，点击跳转到Check

## 路由嵌套

  * 基本步骤
    * 在父组件中，指定上router-view用来盛放子组件
    * 在配置父组件的路由地址时，指定上children属性

      ```vue
      const routes= [
        {path: '/'user',component: User,
          children: [
            {path: 'profile', component: UserProfile},
            {path: 'profile', component: UserPosts}
          ]
        }
      ]
      ```

### 使用VueRouter来实现路由嵌套

  * 创建一个SPA，有3个代码片段，分别是settings.html
  wifi.html bluetooth.html
    * wifi.html 和 bluewifi.html要嵌套在settings.html
    * wifi.html模拟个wifi名称列表
    * bluetooth.html模拟个蓝牙设备名称列表
    * settings.html是个列表，有两个选项分别是：wifi和
      蓝牙，点击加载对应的页面
  
# 网络请求

---

## VueResource介绍

  * VueJS的生态圈除了Vue-Router之外，还有很多的插
  件，在网络请求中，vue是借助于vue-resource模块来
  进行异步请求、跨区请求
  * vue-resource是Vue.js的一款插件，它可以通过
  XMLHttpRequest或JSONP发起请求并处理响应。也就
  是说，$.ajax能做的事情，vue-resource插件一样也能
  做到，而且vue-resource的API更为简洁。
  * 特点：
    * 1.体积小
      vue=resource非常小巧，在压缩以后只有约12KB，服务端启用
      gzip压缩之后只有4.5KB大小
    * 2.支持主流的浏览器
      和vue.js一样，vue-resource除了不支持IE 9以下的浏览器，其他主流
      的浏览器都支持。
    * 3.支持Promise API和URI Templates
      Promise是ES6的特性，Promise的中文含义为“先知”，Promise对
      象用于异步计算
      URI Teplates表示URI模板，有些类似于ASP.NET MVC的路由模板。
    * 4.支持拦截器
      拦截器是全局的，拦截器可以在请求发送前和发松请求后做一些处理。
      拦截器在一些场景下会非常有用，比如请求发送前在header中设置access_token，或者在请求失败时，提供共通的处理方式。

## VueResource使用步骤

  * 使用步骤
    * 安装vue-resource
      `npm instal --save vue-resource`
    * 引入vue-resource模块
      `import VueResource from 'vue-resource'`
      `Vue.use(VueResource)`
    * 调用模块中$http发起请求

      ```vue
      this.$http.get( 'url')
      .then(function(response){
      })
      ```

## VueResource使用拦截器

  ```vue
  Vue.http.interceptors.push((req,next)=>{
    //发送请求前的处理逻辑
    next((res) => {
      //请求发送后的处理逻辑
      //res参数会返回给successCallbck
      //或errorCallback
      return res
    })
  })
  ```

  ```mermaid
  graph TD
    id1[发送请求前] -- inteceptor --> id2[处理请求]
  graph TD
    id2[处理请求] --> id3[发送请求后（接受请求）]
  ```

# 过渡效果

---
  
# 综合练习

---

## ToDoList

  * 目标：采用VueJS来实现ToDoList
    * ToDoList中综合了组件的创建和使用、嵌套组件之间数据的传输等知识点
  * 采用VueJS来实现ToDoList基本步骤
    * 组件的划分
        将整个应用作为一个复合组件ToDoBox，
        ToDoBox中有ToDoInput和ToDoList构成
        在ToDoInput中有一个标题、输入框、按钮构成
        在ToDoList中有多个ToDoItem构成
        在ToDoItem中有一个按钮和span标签构成
    * 实现添加功能
      ToDoInput中按钮点击时的数据怎么传递到ToDoBox？
      这属于子组件向父组件传输数据，可以借助自定义事件来实现
      ToDoBox中的数据怎么显示在ToDoList中？
      这属于父组件向子组件传递数据，可以借助于props来传递数据
    * 实现删除功能
        点击ToDoItem的删除按钮，怎么操作ToDoBox中的数据呢？
        可以借助于自定义事件，但是ToDoItem并不是ToDoBox的子组件，
        而是属于ToDoList中的子组件，事先传递给ToDoItem才可以，
        ToDoItem中接收到事件后，继续触发ToDoBox中的自定义事件即可