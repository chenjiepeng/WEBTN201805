# SVG 概述

---

## 什么是 SVG

* SVG（Scalable Vector Graphics）是一种使用XML技术描述二维图形的语言。
* SVG 可以使用三种方式描述二维图形：
  * 矢量图（vector graphic shapes），例如直线或曲线构成的路径。
  * 图片（images）
  * 文本（text）

## SVG 的优势

* SVG 可通过文本编辑器来创建和修改。
* SVG 可被搜索、索引、脚本化或压缩。
* SVG 可在任何的分辨率下被高质量地打印。
* SVG可在图像质量不下降地情况下被方法

## SVG 与 Canvas的区别

* SVG
  * 不支持分辨率
  * 支持事件处理器
  * 最适合带有大型渲染区域地应用程序（例如百度地图）
  * 不适合游戏
* Canvas
  * 依赖分辨率
  * 不支持事件处理器
  * 能够以“.png”或“.jpg”格式保存结果图像
  * 最适合图像密集型的游戏

## SVG 示例

* 绘制一个黑边蓝底的矩形：

  ```html
  <svg width="100%" height="300">
    <rect x="100" y="100" width="300"
    height="100" fill="blue" stroke="black"
    stroke-width="4"/>
  </svg>
  ```

  * svg 标签：用于嵌入SVG 图像。
  * rect 标签：用于描述该图形是一个矩形。
  * x 和 y 属性：表示该矩形的左上点的坐标值。
  * stroke 属性：表示该矩形的边框颜色。
  * stroke-width 属性：表示该矩形的边框宽度

## SVG 使用方式

* 单独的 SVG 文件形式：
  * 使用XML文件定义：

  ```html
  <!DOCTYPE svg PUBLIC "-//W3C//DTD SVG 1.1//EN"
  "http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd">
  ```

  * 指定特殊的命名空间：

  ```html
  <svg width="100%" height="100" version="1.1"
  xmlns="http://www.w3.org/2000/svg"></svg>
  ```

  * 定义 SVG 与在HTML 方式相同
* 使用 svg 标签嵌入在 HTML 页面
* 使用 embaed、object和iframe等标签嵌入在 HTML页面中
* 内嵌在 XHTML页面中

### 测试 SVG 绘图

* 使用单独的 svg 文件绘制矩形
* 使用`<svg>`标签绘制矩形
  
# SVG 元素

---

## SVG 元素种类

* SVG 预定义元素
  * 矩形元素
  * 圆形元素
  * 椭圆元素
  * 线条元素
  * 折线元素
  * 多边形元素
  * 文本元素
  * 图像元素
* SVG 特效元素
  * SVG 滤镜
  * SVG 渐变

## SVG 矩形元素

* SVG 使用`<rect>`标签来创建矩形，代码如下：  

  ```html
  <svg width="100%" height="300">
    <rect width="300" height="100"
    style="fill:rgb(0,0,255);stroke-width:1;
    stroke:rgb(0,0,0)" />
  </svg>
  ```

  * rect 的 width 和 height 属性：定义矩形的宽度和高度
  * style 属性用来定义 CSS 属性
  * CSS 的 fill 属性定义矩形的填充颜色CSS 的 stroke-width 属性定义矩形边框的宽度
  * CSS 的 stroke 属性定义矩形边框的颜色

### 使用 SVG 绘制矩形

* 用`<svg>`标签绘制不同位置和颜色的矩形
* 绘制移动的矩形
* 绘制带动画的矩形
* 使用 js 动态随机绘制矩形

## SVG 圆形元素

* SVG 使用`<circle>`标签来创建圆形，代码如下：

  ```html
  <svg width="100%" height="100">
    <circle cx="100" cy="50" r="40"
    stroke="black" stroke-width="2" fill="red"/>
  </svg>
  ```

  * cx 和 cy 属性定义圆点的 x 和 y 坐标（如果省略 cx 和 cy ，圆的中心会被设置为(0,0))
  * r 属性定义圆的半径

### 使用 SVG 绘制圆形

* 用`<svg>`标签绘制圆形
* 使用 js 动态绘制圆形

## SVG 椭圆元素

* SVG 使用`<ellipse>`标签来创建椭圆，代码如下：

  ```html
  <svg width="1000" height="500">
  <ellipse cx="300" cy="150" rx="200" ry="80"
  style="fill:rgb(200, 100, 50);
  stroke:rgb(0, 0, 100);stroke-width:2"/>
  </svg>
  ```

  * cx 属性定义圆点的 x 坐标
  * cy 属性定义圆点的 y 坐标
  * rx 属性第河南巩义水平半径
  * ry 属性定义垂直半径

### 使用 SVG 绘制椭圆

* 用`<svg>`标签绘制椭圆

## SVG 线条元素

* SVG 使用`<line>`标签来创建线条，代码如下：

  ```html
  <svg width="500" height="500">
    <line x1="0" y1="0" x2="300" y2="300"
    style="stroke:rgb(99, 99, 99);stroke-width:2"/>
  </svg>
  ```

  * x1 属性在 x 轴定义线条的开始
  * y1 属性在 y 轴定义线条的开始
  * x2 属性在 x 轴定义线条的结束
  * y2 属性在 y 轴 定义线条的结束

## SVG 折线元素

* SVG 使用`<ployline>`标签来创建折线，代码如下：

  ```html
  <svg width="100%" height="100%">
    <polyline points="0,0 0,20 20,20 20,40 40,40 40,60"
    style="fill:white;stroke:red;stroke-width: 2"/>
  </svg>
  ```

  * points属性用于存储折线中的起点、折点和终点的 x 和 y 轴坐标值
  0,0 表示起点
  0,20 20,20 20,40 40,40 表示折点
  40,60 表示终点

### 使用 SVG 绘制直线和折线

* 用`<svg>`标签绘制折线
* 用`<svg>`标签绘制折线

## SVG 多边形元素

* SVG 使用`<polygon>`标签来创建含有不少于三个边的多边形，代码如下：

  ```html
  <svg width="500" height="500">
    <polygon points="220,100 300,210 170,250"  style="fill:#cccccc;stroke:#000000;
    stroke-width:1"/>
  </svg>
  ```

* points 属性定义多边形每个角的 x 和 y 坐标

### 使用 SVG 绘制多边形

* 用`<svg>`标签绘制多边形
* 用`<svg>`标签绘制图表

## SVG 文本

* SVG 使用`<text>`标签来创建文本，代码如下：

  ```html
  <svg width="500" height="500">
    <text x="" y="" font-size=""
    font-family="">
      文本内容
    </text>
  </svg>
  ```

* SVG 中的文字是可以选中的
  * Canvas中的 fillText()则不能

## SVG 图像

* SVG 使用`<image>`标签来创建图像，代码如下：

  ```html
  <svg width="500" height="500">
    <image xlink:href="img/disc.png"
    x="250" y="200"
    width="200" height="200"></image>
  </svg>
  ```

### 使用 SVG 绘制文本和图像

* 用`<SVG>`标签绘制文本
* 用`<SVG>`标签绘制图像

## SVG 高斯模糊滤镜元素

* SVG 使用`<filter>`标签来创建滤镜：

  ```html
  <svg width="500" height="500">
    <defs>
      <filter id="Gaussian_Blur">
        <feGaussianBlur in="SourceGraghic"
        stdDeviation="3"/>
      </filter>
    </defs>
  </svg>
  ```

* SVG 使用`<filter>`标签来创建滤镜
  * `<filter>`标签的 id  属性可为滤镜定义一个唯一的名称（同一滤镜可被文档中的多个元素使用）
  * 滤镜效果是通过`<feGaussianBlur>`标签进行定义的
  * `<feGaussianBlur>`标签的 stdDeviation 属性可定义模糊的程度
  * in="SourceGraphic" 这个部分定义了有整个图像创建效果
* SVG 使用`<ellipse>`标签来调用高斯模糊：

  ```html
  <ellipse cx="200" cy="150" rx="70" ry="40"
  style="fill:#ff0000;stroke:#000000;
  stroke-width:2;filter:url(#Gaussian_Blur)"/>
  ```

  * filter:url 属性用来把元素链接到滤镜。当链接滤镜 id 时，必须使用 # 字符

## SVG 渐变元素

* 什么是渐变
  * 渐变是一种从一种颜色到另一种颜色的平滑过渡（可以将多个颜色的过渡应用到同一个元素上）
* SVG 渐变类型：
  * SVG 线性渐变，使用`<linerGradient>`标签定义线性渐变。
  * SVG 放射性渐变，使用`<radialGradient>`标签定义放射性渐变。
  SVG 渐变必须在`<defs>`标签中进行定义。
* SVG 使用`<linerGradient>`标签来创建线性渐变：

  ```html
  <svg width="500" height="500">
    <defs>
      <linerGradient id="orange_red" x1="0%" y1="0%"
      x2="100%" y2="0%">
        <stop offset="0%"
        style="stop-color: rgb(255, 255, 0);     stop-opacity:1"/>
        <stop offset="100%" style="stop-color: rgb(255, 0, 0);     stop-opacity:1"/>
      </linerGradient>
    </defs>
  </svg>
  ```

* SVG 使用`<linerGradient>`标签来创建线性渐变：
  * `<linerGradient>`标签的 id 属性可为渐变定义一个唯一的名称
  * `<linerGradient>` 标签的 x1、x2、y1、y2 属性可定义渐变的开始和结束位置
  * 渐变的颜色范围可由两种或多种颜色组成。每种颜色通过一个`<stop>`标签来规定。offset 属性用来定义渐变的开始和结束位置。
* SVG 使用`<ellipse>`标签来调用线性渐变：

  ```html
  <ellipse cx="200" cy="190" rx="85" ry="55"
  style="fill:url(#orange_red)"/>
  ```

  * fill:url(#orange_red) 属性把 ellipse 元素链接到此渐变

### 使用 SVG 实现渐变和模糊滤镜效果

* 该矩形的填充颜色是由红色到蓝色的渐变
* 该矩形使用高斯模糊达到阴影效果