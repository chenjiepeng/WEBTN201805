# React.js 概述

---

## 概述

  * React：为数据提供渲染HTML视图的开源JavaScript库
  * 由Facebook，Instagram和一些社群（由个人开发者和企业组成）维护

为什么会推出React？
  
  * React 起源于 Facebook 的内部项目，因为该公司对市场上所有 JavaScript MVC 框架，都不满意，就决定自己写一套，用来架设 Instagram 的网站。做出来以后，发现这套东西很好用，就在2013年5月开源了

主要解决什么问题？
We built React to solve one problem：
building large application with data that changes over time.

发展历史：

  * 11年由FaceBook工程师Jordan Walker创建，刚开始部署在FaceBook的newsfeed
  * 12年部署在Instagram（同年被FB10亿美金收购）
  * 13年5月 在JSConf US宣布开源
  * 14年React称为在github达到1万star的旗舰开源项目
  * 15年3月 在JSConf US，发布React Native

学子资料推荐：

  * 中文社区：http://rectjs.cn
  * gitbook：https://www.gitbook.com/book/hulufei/react-tutorial/details
  * 菜鸟教程：http://www.runoob.com/react/react/tutorial.html
  * 书籍：React引领未来的用户界面开发框架（资料中有pdf电子书）

## React.js 特点

  * 声明式设计
  * 高效
  * 灵活
  * JSX
  * 组件
  * 单向响应的数据流

## 核心思想

  * React的核心思想是：封装组件。
  * 各个组件维护自己的状态和UI，当状态改变，自动重新绘制整个组件

  * react应用都是构建在组件之上的。页面上，和用户交互的结构、动态的元素、可以复用的结构，都可以封装成组件

## 核心概念

  * 组件
  * JSX
  * VirtualDOM
  * 单向数据绑定

# 环境搭建

---

## 搭建React开发环境

  * 依赖三个js文件：
  * react.js、react-dom 和 browser.js

  * react.js 是 React 的核心库，
  * react-dom.js 是提供与 DOM 相关的功能
  * browser.js 的作用是将 JSX 语法转为 JavaScript 语法

  * 将上述三个文件，引入工程，即可开始React之旅！

## Hello React

  * 打开WebStorm，新建工程
  * 创建名为js的文件夹
  * 将react.js react-dom.js browser.js文件导入工程中的js目录

  * 接下来，使用React来实现第一个React.js程序

    步骤分析：
      * 1、通过script标签引入个js文件，完成依赖引入
      * 2、调用React提供的方法，显示Hello React

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
    <meta charset="UTF-8">
    <script src="js/react.js"></script>
    <script src="js/react-dom.js"></script>
    <script src="js/browser.min.js"></script>
    <title>hello React</title>
  </head>
  <body>
  <div id="exmaple"></div>
  
  <scrpit type="text/babel">

    ReactDOM.render(
      <h1>hello React</h1>,document.getElementById('example')
    )

  </script>
  </body>
  </html>
  ```

## render方法介绍

  * ReactDom.render 是 React 的 最基本方法，用于将模板转为 HTML 语言，并插入指定的 DOM 节点

  ```html
  ReactDOM.render(
    <h1>Hello,world!</h1>,
    document.getElementById('example')
  )
  ```

## Babel 简介

  * `<script>` 标签的 type 属性为text/babel，那么为什么要指定类型为babel呢？

  * 这是因为 React独有的 JSX 语法，跟 JavaScript 不兼容
    * 凡是使用 JSX 的地方，都要加上 type= "text/babel",
    * Babel是一个 JavaScript 编译器，由于Babel 内嵌了对 JSX 的支持，所以识别JSX语法

# JSX

---

## JSX 概述

  * 什么是JSX？
    * JSX=JavaScriptXML 是一种在React组件内部构建标签的类XML语法，基于ECMAScript的一种新特性，并不是一种新的语言。

  * 为什么要有JSX？
    * React 认为组件才是王道，而且组件是和模板紧密关联的，组建模板和组建逻辑分离让问题复杂化了，所以通过 JSX 这种语法，就是为了把 HTML 模板直接嵌入到 JS 代码里面，这样就做到了模板和组件关联

## JSX特点

  * 类XML语法，容易接受

  * 增强JS语义

  * 抽象程度高（虚拟DOM操作）

  * 代码模块化

## JSX语法

  * JSX在定义类似HTML这种树状结构时，简单明了，所以推荐使用JSX语法

  ```html
  #使用JSX
  React.render(
    <div>
      <div>
        <div>content</div>
      </div>
    </div>,
    document.getElementById('example')
  )

  # 不使用JSX
  React.render(
    React.creatElement('div',null,
      React.creatElement('div',null,
        React.creatElement('div',null,'content')
      )
    ),
    document.getElementById('example')
  )
  ```

  * 我们可以在JSX中使用JavaScript表达式，表达式写在{}中

  * 那么如果既有html又有js，React是如何解析的？
    * 遇到HTML标签（以<开头），就用HTML解析
    * 遇到代码块（以{开头）就用js来解析

### 使用 JSX 语法

  * 使用 JSX 验证常见的js表达式

  * 分析：
    * 在花括号{}中，编写算术运算、三目运算等的常见js表达式，验证执行情况

# 组件

---

## 组件

  * React 允许将代码封装成组件（component）,然后像插入普通 HTML 标签一样，在网页中插入这个组件。

    ```html
    var HelloMsg = React.createClass({
      render:function(){
        return(
          <div>
            <h1>hello world</h1>
          </div>
        )
      }
    })
    ReactDOM.render(<HelloMsg/>,document.getElementById("example"))
    ```

  * 变量HelloMsg 就是一个自定义组件类
  * React.createClass 方法就是用于生成一个组件类
    模板插入`<HelloMsg/>`时，会自动生成 HelloMsg 的一个实例。

  * 注意：
    * 组件类的第一个字母必须大写，否则显示会有问题
    * 组件 类只能包含一个顶层标签，否则也会有问题
    * 组件类都必须有自己的 render 方法，用于输出组件！

## 复合组件

  * 目的
    * 使用组件的目的就是通过构建模块化的组件，相互组合组件，最后组装成一个复杂的应用。
  
  * 如何操作
    * 在 React 组件中要包含其他组件作为子组件，只需要把组件当做一个 DOM 元素引入就可以了。

  * 接下来，创建两个组件Title、Link，并将其组合成一个复合组件Tarena，代码如下：

    ```html
    var Tarena = React.createClass({
      render:function(){
        return(
          <div>
            <Title/>
            <Link/>
          </div>
        )
      }
    })

    var Title = React.createClass({
      render:function(){
        return(<h1>达内教育</h1>)
      }
    })

    var Link = React.createClass({
      render:function(){
        return(<a href="www.tmooc.cn"</a>)
      }
    })

    ReactDOM.render
    (<Tarena/>,document.getElementById('example'))
    ```

## 组件间通信

  * 父子组件间通信
    * 这种情况下很简单，就是通过 props 属性传递。
    * 在父组件给子组件设置 props，然后子组件就可以通过 props 访问到父组件的数据/方法，这样就搭建起了父子组件间通信的桥梁

  ```html
  var HelloReact = React.createClass({
    render:function(){
      return(
        <div>
          <h1>{ this.props.name}</h1>
          <p>{this.props.tips}</p>
        </div>
      )
    }
  })

  ReactDOM.render(<HelloReact tips="hello" name="Web1603"/>,document.getElementById('example'))
  ```

  * 父组件如何访问子组件？用refs。

  * 可以通过 this.refs.[refName] 属性获取的是真实 DOM
    * 注意：必须等待虚拟 DOM 插入文档以后，才能使用这个属性，否则会报错

  ```html
  var MyComponent = React.createClass({
    handlerClick:function(){
      this.refs.inputSth.focus()
    }
    render:function(){
      return(
        <div>
          <input ref='inputSth' placeholder='请输入内容'/>
          <button onClick={this.handlerClick}>点击</button>
        </div>
      )
    }
  })
  RenderDOM.render(<MyComponent/>,document.getElementById('example'))
  ```

### 使用组件

  * 综合练习refs和props

    分析：
      * 父组件中声明name，传递给子组件显示
      * 子组件：
        h1标签用来显示name，input标签获取用户输入，
        button按钮，点击按钮，通过refs获取input中输入的内容