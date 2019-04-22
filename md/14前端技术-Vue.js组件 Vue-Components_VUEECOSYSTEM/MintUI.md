# VUE 组件概述

---

## 什么是 Vue.js UI 组件

  * Vue.js UI 组件 是一种基于Vue.js 平台针对于移动端用
  户提供CSS,JS库
  * Vue.js 组件有如下两种类型：
    * PC端组件 element-UI；
    * 移动端组件 Mint-UI；MUI；
  * Vue.js 组件 当前的应用领域十分广泛，例如：
    * 编写在移动端或者PC端网页中，实现各种用户交互效果

# 使用 Mint-UI

---

## 搭建Mint-UI运行环境

* 方式一：安装独立的Min-UI

    ```bash
    //安装
    #Vue 1.x
    npm insall mint-ui@1 -S
    # Vue 2.0
    npm install mint-ui -S
    ```

* 方式二：使用客户端加载Mint-UI组件

    ```vue
    <!-- 引入样式 -->
    <link rel="stylesheet" href="https://unpkg.com/mint-ui@1/lib/style.css">
    <!-- 引入组件库 -->
    <script src="https://unpkg.com/mint-ui@1/lib/index.js"></script>
    ```

# JS Components

---

## Toast

 简短的消息提示框，支持自定义位置、持续时间和样式

   ```vue
   import { Toast } from 'mint-ui';#引入
   Toast('提示消息')；#用法
   ```

 详细用法

### 综合示例

* 通过程序控制Toast显示的时间（5秒），后
* 关闭
  提示：使用定时器setTime+Toast

## Lazy load

 图片懒加载指令：运行效果图

 引入组件 Lazy load与对应样式文件

   ```vue
   import { Lazyload } from 'mint-ui';
   Vue.use(Lazyload)\
   import "mint-ui/style.css"
   ```

 模板中调用lazy load指令

   ```vue
   <ul>
    <li v-for="item in list">
      <img v-lazy="item">
    </li>
  </ul>
  ```

 指定图片与懒加载时样式

   ```vue
   img[lazy=loading]{
     width:40px
     height:300px
     margin:auto
   }
   ```

 Vue cli BUG
 去除按需加载组件，加载所有组件

### 综合示例

* 学子商城图片列表按需加载

## Swipe

 图片轮播组件：运行效果图

 模板中调用Swipe指令

   ```vue
   <mt-swipe :auto="3000">
    <mt-swipe-item>
      <img src="1.jpg"/>
    </mt-swipe-item>
    ...
   </mt-swipe>
   ```

 引入组件 Swipe与对应样式文件

   ```vue
   #app{
     height:200px
   }
   #app.mint-swipe-item{
     width:100%
     height:100%
   }
   ```

 默认Swipe组件不能正确显示
 原因
 父元素高度为0一定要设置高度否则看不到结果

### 综合示例

 * 学子商城首页图片轮播

# CSS Components

---

## Header

 顶部导航栏，支持显示按钮、自定义文字和固定在顶部

 引入组件

 ```vue
 Header import { Header } from 'mint-ui';  

 Vue.component(Header.name,Header)
 ```

## mt-header

 模板中调用mt-header指令

 ```vue
 <mt-header fixed tittle="固定在顶部"></mt-header>
 ```

## mt-header属性值

slot

### 综合示例

* 学子商城顶部标题

## Navbar

 顶部选项卡，依赖 tab-item 组件
 引入组件 navbar

   ```vue
   import { Navbar, TabItem } from 'mint-ui'  

   Vue.component(Navbar.name, Navbar)
   Vue.component(TabItem.name, TabItem)
   ```

## 模板中调用navbar指令

 模板中调用navbar指令先创建一个列表组

   ```vue
   <!-- tab-container -->
   <mt-tab-container v-model="selected">
    <mt-tab-container-item id="1">
      <mt-cell v-for="n in 10" :title="'内容' + n"/>
    </mt-tab-container-item>
    .....
   </mt-tab-container>
   ```

 模板中调用navbar指令

   ```vue
    <mt-navbar v-model="selected">
     <mt-tab-item id="1">选项一</mt-tab-item>  
     <mt-tab-item id="2">选项二</mt-tab-item>  
     <mt-tab-item id="3">选项三</mt-tab-item>
    </mt-navbar>
   ```

 模板中调用navbar指令先创建一个列表组

   ```js
   <script>
      new Vue({
        data:function(){
          return {selected:"1"}
        }
      })
   </script>
   ```

   1；选中的卡片的值一定双引号

## navbar属性值

### 综合示例

* 综合示例 产品 相册 新闻 选项卡

## Tabbar

 底部选项卡，点击 tab 会切换显示的页面。依赖 tab-item 组件

 引入组件 Tabbar

   ```vue
   import { Tabbar, TabItem } from 'mint-ui'  

   Vue.component(Tabbar.name, Navbar)
   Vue.component(TabItem.name, TabItem)
   ```

 模板中调用Tabbar
 指令先创建一个列表组

   ```vue
   <mt-tab-container v-model="selected">
     <mt-tab-container-item id="1">
       <mt-cell v-for="n in 10" :title="'内容' + n"/>
     </mt-tab-container-item>
   ...
   </mt-tab-container>
  ```

 模板中调用Tabbar指令先创建一个列表组

   ```vue
   <mt-navbar v-model="selected">
    <mt-tab-item id="1">外卖</mt-tab-item>
    <mt-tab-item id="2">订单</mt-tab-item>   <mt-tab-item id="3">我的</mt-tab-item>
   </mt-navbar>
   ```

Tabbar属性值

  slot

### 综合示例

* 学子商城商品列表切换
  
# Form Components

## Swich 开关按钮

  开关按钮

  引入 Switch

    import { Switch } from 'mint-ui';  
    Vue.component(Switch.name,Switch)

  模板中调用Switch指令先创建一个列表组

    示例一：
    <mt-switch v-model="value"></mt-switch>
    示例二：带内容的开关
    <mt-switch-model="value">开关</mt-switch>

  Switch 开关按钮

    <script>
    export default {
      data(){
        return {
          input:''
        }
      }
    }
    </script>

## Switch 开关按钮属性值

### 综合示例

* 学子商城顶部标题

## Checklist

  复选框列表，依赖 cell 组件。

  引入 Checklist

    import { Checklist } from 'mint-ui';  
    Vue.component(Checklist.name,Checklist)

  模板中调用Checklist指令先创建一个复选框组件
  
    <mt-checklist
      v-model="value"      :options="options">
    </mt-checklist>
    {{value}}

## Checklist 复选框组件

  ```js
  <script>
  var m = new Vue({
    data(){
      return {
        value:[],
      ....
  ```

  ```js
  <script>
    options:[{
      label:'选项A'
      value:'A',
      disabled:true//可以禁用选项
    }，
    {
      label:'选项B',
      value:'B',
      disabled:true
    }]
  </script>
  ```

## Checklist 复选框组件

### 综合示例

* 学子商城商品列表

## Field

  表单编辑器

    import { Field} from 'mint-ui';  

    Vue.component(Field.name,Field)

  模板中调用Field指令先创建一个组件

    <mt-field label="邮箱" state="success" v-model="email"></mt-field>
    <mt-field label="邮箱" state="error" v-model="email"></mt-field>
    <mt-field label="邮箱" state="warning" v-model="email"></mt-field>

    <mt-field label="用户名" placeholder="请输入用户名"
    v-model="username"></mt-field>
    <mt-field label="邮箱" placeholder="请输入邮箱"
    type="email" v-model="email"></mt-field>

    <script>
    var m = new Vue({
      data(){
        return {
          username:"",
          email:"",
      ...

### 综合示例

* 学子商城用户注册