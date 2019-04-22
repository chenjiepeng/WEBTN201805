# Two.js 概述

---

## Two.js 是什么

* Two.js 是一个面向现代Web浏览器提供绘制二维图形的API，它允许使用不同的上下文，而使用相同的API进行绘制。
* Two.js 所支持的上下文：
  * SVG
  * Canvas
  * WebGl
  * 官方网站：http://jonobr1.github.io/two.js/

## Two.js 的特点

* 专注于矢量图：
  * Two.js 是深度实现具有动画效果的矢量图
  * Two.js 致力于更简洁地创建矢量图及动画效果
  * Two.js 不支持文本或图片
* 场景：
  * Two.js 的核心是依赖于场景
  * 当创建或绘制一个对象（ Two.Polygon 或 Two.Group ）时，是同时存储并记忆
* 循环动画：
  * Two.js 具有一个内置的循环动画
  * Two.js 的动画效果可以很简单的实现，也可以与其他动画库配置使用
* SVG 解释器：
  * Two.js 具有 SVG 解释器
  * Two.js 允许开发者或设计者在商业应用中创建 SVG ，例如使用Adobe Illustrator 创建的 SVG 元素纳入 Two.js 的场景中

# Two.js 入门

---

## 如何使用 Two.js 框架

* 在HTML页面引入Two.js文件：
  `<script src="two.js"></script>`
* 在HTML页面定义用于显示矢量图的容器：
  `<div id="draw-shapes"></div>`
* javascript代码获取元素：
  `document.getElementById("draw-shapes")`
* 使用 Two.js 提供的API进行绘制
  `new Two(params).appendTo(elem)`

## 绘制矩形元素

* Two.js 框架使用makeRectangle(x,y,width,height)方法绘制矩形：
  makeRectangle(x,y,width,height)
  * x：指定绘制的矩形左上角的坐标值x
  * y：指定绘制的矩形的左上角的坐标值y
  * width：指定绘制的矩形的宽度
  * height：指定绘制矩形的高度

## 绘制圆形元素

* Two.js 框架使用makeCircle(x,y,radius)方法绘制矩形：
  makeCircle(x,y,radius)
  * x：指定绘制圆形的圆心的坐标值x
  * y：指定绘制圆形的圆心的坐标值y
  * radius：指定绘制的圆形的半径

### 使用 Two.js 绘图

* 使用 Two.js 绘制矩形
* 使用 Two.js 绘制圆形

## 元素分组

* 元素分组：
  * Two.js 框架允许绘制在页面的多个图形分为一组或多组
  * Two.js 提供的API方法允许针对组进行操作或实现动画
* 创建分组：
  * 通过Two.js 框架提供的构造器 Two.Group()实现
  * 通过 Two.js 提供提供的的相关API方法或属性进行操作
* 将已绘制的图形分为一组或多组：
  * 通过创建的two对象调用makeGrouop()方法
  * makeGroup()方法允许传递多个绘制图形对象
  * 通过 Two.js 框架提供的相关API方法或属性进行操作

## 添加动画

* two.play()方法：
  * 该方法向 requestAnimationFrame loop 添加一个实例，使该实例实现动画效果
* two.pause()方法：
  * 该方法从 requestAnimationFrame loop 删除一个示例，使该示例的动画效果停止
* two.update()方法：
  * 该方法用于更新在HTML页面中绘制的图形的尺寸，增加动画效果

### 使用 Two.js 动画

* 使用 Two.js 实现旋转动画