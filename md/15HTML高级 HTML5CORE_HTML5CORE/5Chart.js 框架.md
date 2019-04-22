[toc]

# Chart.js 概述

---

## Chart.js是什么

Chart.js是一个简单、面向对象、为设计者和开发者准备的图标绘制工具库。
官方网址：http://www.chartjs.org/

## Chart,js的特点

基于HTML 5

* Chart.js基于HTML5 canvas技术，支持所有现代浏览器，并且针对IE7/8提供了降级代替方案。

简单、灵活

* Chart.js不依赖任何外部工具库，轻量级（压缩之后仅有4.5k），并且提供了加载外部参数的方法。

## Chart.js的功能

Chart.js帮你用不同的方式让你的数据变得可视化。
每种类型的图标都由动画效果，并且看上去非常棒，即便是在retina屏幕上。
6种图表类型

* 曲线图
* 柱状图
* 雷达图
* 饼状图
* 极地区域图
* 环形图
  
# Chart.js 入门

---

## 如何使用Chart.js框架

在HTML页面中引入Chart.js文件
`<script src="Chart.js"></scrpit>`
创建`<canvas>`元素

* 用于显示Chart图表的容器
  `<canvas id="mychart" width="400" height="400"></canvas>`

获取Canvas对象
`document.getElementById("myChart").getContext("2d")`
创建Chart图表
`new Chart(ctx,{type:"bar", data:data, options:options})`

## Chart.js全局配置

* Chart.js 全局配置是在chart.js 第一个正式版中引入
* Chart.js 全局配置用于改变所有图表的类型，避免了需要在每一个图表中单独进行设置
* 当然，Chart.js 全局配置也可以专门为某一个特定的图标进行配置
* 语法:
Chart.defaults.global.参数名 = 参数值
* 举例：
`Chart.defaults.global.responsive = true`
创建指定图表时，responsive选项值为true

# Chart.js 使用

---

## 曲线图

* 曲线图
  * 就是将多个数据点绘制在一条线上
  * 通常用于展示趋势的数据或两组数据之间的对比

* 方法
  `new Chart(ctx,{type:"line", data:data, options:options})`
  * data：用于设置曲线上的数据、样式及名称
  * options：选项，用于配置曲线图

## 柱状图

* 柱状图
  * 就是使用柱状方式显示数据的一种方式
  * 通常被用于展示趋势的数据或多组数据之间的比较
* 方法
  new Chart(ctx,{type:"bar",data:data,options:options})
  * data：用于设置柱状图上的数据、样式及名称
  * options：选项，用于配置柱状图

### 使用 chart.js 绘制柱状图

* -使用 chart.js 绘制柱状图

## 饼状图

* 饼状图
  * 可能是所有图表中最为常见的一种
  * 就是将一个圆划分成若干个部分，每个弧形展示每个数据的比例值
  * 通常被用于展示多组数据之间的比例
* 方法
  `new Chart(ctx,{type:"pie",data:data,options:options})`
  * data：用于设置饼状图上的数据、样式及名称*
  * options：选项，用于配置饼状图

## 雷达图

* 雷达图
  * 就是一种展示多个数据点以及它们之间变化的方式
  * 通常被用于比较点的两个或多个不同的数据集
* 方法
  `new Chart(ctx,{type:"radar",data:data,options:options})`
  * data：用于设置雷达图上的数据、样式及名称
  * options：选项，用于配置雷达图

## 极地区域图

* 极地区域图
  * 类似于饼状图，但每一个扇形的角度和半径取决于不同的值
  * 通常被用于需要展示类似于饼状图的比较数据的基础上，还需要展示范围值的比较
* 方法
  `new Chart(ctx,{type:"polarArena",data:data,options:options})`
  * data：用于设置极地区域图的数据、样式及名称
  * options：选项，用于配置极地区域图

## 环形图

* 环形图
  * 类似于饼状图，但环形图是一个空心的环形形状
  * 通常被用于展示多组数据之间关系的比例
* 方法
  `new Chart(ctx,{type:"doughnut",data:data,options:options})`
  * data：用于设置环形图上的数据、样式及名称*
  * options：选项，用于配置环形图