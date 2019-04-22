[toc]
# Canvas概述

## 什么是Canvas

* Canvas是HTML5出现的新标签，像所有DOM一样，拥有自己的属性、方法和事件，期中就有绘图的方法，JavaScript能够调用它在网页上完成绘图
* Canvas也是HTML5中最强大的特性之一。允许开发者使用动态和交互式可视化方法在Web上实现桌面应用程序的功能
注意：Internet Explorer 8 及更早 IE 版本的浏览器不支持`<canvas>`元素

## 创建Canvas

* `<canvas>`元素会在网页上创建一个空白矩形区域，然后通过API操作这个区域，与空白的<div>元素相似，但用途完全不同
* 默认情况下，创建的`<canvas>`元素没有边框和内容
* 语法：
  `<canvas id="canvas" width="300" height="200"></canvas>`

## getContex()方法

* 在使用`<canvas>`元素时，要调用getContext()方法，其目的是得到画布的绘图上下文。通过这个引用，就可以使用其它的API进行绘图操作
* 语法：

  ```js
  function initial(){
    var elem = document.getElement('canvas')
    var canvas = elem.getContext('2d')
  }
  ```

  注意：该方法可以接受两个值：2d和3d，分别表示二维和三维

### 测试canvas

# Canvas绘图

---

## 绘制矩形

* 在准备好Canvas之后，就可以创建和绘制实际图形了。API提供的工具非常广泛，包括创建图形、颜色、文本等
* API中的一些方法支持在画布上直接绘图，但这些方法专门用于绘制矩形形状，并且是唯一能够生成基础形状的方法。要想绘制其他形状，就要组合使用其他的绘图方法以及复杂路径
* 绘制矩形方法（生成基础形状方法）：
  * fillRect(x,y,width,height)
  * strokeRect(x,y,width,height)
  * clearRect(x,y,width,height)
* fillRect(x,y,width,height)
  * 绘制实心矩形
  * x,y 指定矩形的左上角位置
  * width，height声明其尺寸
* strokeRect(x,y,width,height)
  * 与前一个方法类似，绘制空心矩形
* clearRect(x,y,width,height)
  * 清除属性所指定的区域的像素。类似于矩形擦除器

  ```js
  function initial(){
    var elem=document.getElementBy('canvas'
    var canvas=elem.getContext('2d'
    canvas.strokeRect(100,100,120,120
    canvas.fillRect(110,110,100,100
    canvas.clearRect(120,120,80,80)
  }
  ```

## 颜色

* 在创建图形时如果不设定颜色，那么所有图形都会使用默认颜色-纯黑色
* 可以通过以下属性指定绘图颜色：
  * strokeStyle：声明形状线条的颜色
  * fillStyle：声明形状内部区域的颜色
  * globalAlpha：透明度属性。可以设置画布上图形的透明度

  ```js
  function initial(){
    var elem=document.getElementBy('canvas'
    var canvas=elem.getContext('2d')
    canvas.fillStyle="#000099"
    canvas.strokeStyle="#990000"
    canvas.strokeRect(100,100,120,120
    canvas.fillRect(110,110,100,100
    canvas.clearRect(120,120,80,80)
  }
  ```

### 绘制矩形

* 绘制不同位置、不同颜色的矩形
* 移动的矩形

## 渐变

* Canvas支持的渐变效果包括线性渐变或射线渐变，并且支持设置颜色转折点
* 语法：
  * createLinerGradient(x1,y1,x2,y2)：在画布上创建一个线性渐变对象
  * createRadialGradient(x1,y1,r1,x2,y2,r2)：在画布上创建一个射线渐变对象
  * addColorStop(posrition,color)：指定渐变颜色值

  ```js
  function initial(){
    var elem=document.getElementBy('canvas')
    var canvas=elem.getContext('2d')
    var grad=canvas.createLinerGradient(0,0,10,100)
    grad.addColorStop(0.5,'#0000FF')
    grad.addColorStop(1,'#FF0000')
    canvas.fillStyle=grad
    canvas.fillRect(10,10,100,100)
    canvas.fillRect(150,10,200,100)
  }
  ```

### 使用渐变色

* 使用线性渐变
* 使用射线渐变

## 文字

* 在画布上写文字非常简单，只需要定义一些属性和方法即可
* 属性
  * font：与css的font属性类似，接受值也完全相同
  * textAlign：水品对齐方式，值可以是left、right和center
  * textBaseline：文本基线，值可以是top、hanging（悬挂基线）、middle、alphabetic（默认值，字母基线）和bottom
  * strokeText(text,x,y)：在位置(x,y)处绘制指定文字的轮廓
  * fillText(text,x,y)：与上一个方法相似，区别是该方法绘制的是实心文字
  * measureText()：返回指定文字的大小信息

  ```js
    function initial(){
      var elem=document.getElementById('canvas')
      canvas=elem.getContext('2d')
      canvas.font="bold 24px verdana,sans-serif"
      canvas.textAlign="start"
      canvas.textBaseline="bottom"
      canvas.fillText("Beijing Tarena",100,124)
      var size=canvas.measureText("Beijing Tarena")
      canvas.strokeRect(100,100,size.width,32)
    }
    ```

## 阴影

* 阴影也是Canvas API的重要组成部分。每一条路径和文字都可以创建阴影效果。API提供了4个实现阴影效果的属性。
  * shadowColor：使用CSS语法声明阴影颜色 -
  * shadowOffsetX：接受一个数字，确定对象阴影的水平投射距离
  * shadowOffsetY：接受一个数字，确定对象阴影的水平投射距离
  * shadowBlur：为阴影生成模糊效果

  ```js
  function initial(){
    var elem=document.getElementById('canvas')
    var canvas=elem.getContext('2d')
    canvas.shadowColor="rgba(0,0,0,0.5)"
    canvas.shadowOffsetX=4
    canvas.shadowOffsetY=4
    canvas.shadowBlur=5
    canvas.font="bold 50px verdana,sans-serif"
    canvas.fiilText("Tarena",100,100)
  }
  ```

### 文字和阴影

* 绘制文字
* 渐变色的文字
* 使用阴影

## 创建路径

* 以上介绍的方法都是直接在画布上绘图，但是针对一些复杂图形的绘制，就需要自己通过路径进行描绘。
* 路径就是画笔  移动的地图，路径建立后，将其发送给上下文，就可以在画布上实际地绘制出图形。
* 方法：
  * beginPath()：开始一个新的形状描述。创建路径之前，必须先调用这个方法。
  * closePath()：关闭路径，用直线将最后一个点与原点相连，如果想保留开放路径，则不需要调用这个方法
* 除此之外，还有三个方法可以在画布上绘制路径
  * stroke()：将路径绘制为轮廓形状
  * fill()：将路径绘制为实心形状。使用该方法时可以不用closePath关闭路径。该方法会通过直线连接最后一个点与第一个点实现封闭
  * clip()：在上下文中设置裁剪区域。
* 以下方法可用于设置路径和创建真正的形状：
  * moveTo(x,y)：将笔触移到指定的位置
  * lineTo(x,y)：绘制一条直线，连接当前笔触位置到x和y属性声明的新位置
  * rect(x,y,width,height)：生成一个矩形路径
  * arc(x,y,radius,startAngle,endAngle,direction)：这个方法可以在位置(x,y)上生成弧线或圆形，半径和弧度分别由属性指定，direction是布尔类型，表示顺时针或逆时针方向

  ```js
  function drawCircle(){
    elem=document.getElementById('canvas')
    canvas=elem.getContext('2d')
    canvas.beginPath()
    canvas.arc(100,100,40,0,Math.PI*2,false)
    canvas.closePath()
    canvas.fillstyle="yellow"
    canvas.fill()
  }
  ```

### 使用路径绘图

* 绘制路径
* 绘制带坐标的柱状统计图

## 线型

* 到目前为止，所有画布操作都使用相同的线型，寂寞人线型。实际上线条的宽度、端点都可以根据实际绘图需要进行调整。
* 以下是修改线型的属性：
  * linewidth：指定线条粗细，默认值是1.0
  * lineCap：指定线条端点形状，支持的值有以下三个
    * butt：默认。向线条的每个末端添加平直的边缘
    * round：向线条的每个末端添加圆形线帽
    * square：向线条的每个末端添加正方向线帽
      注意：round和square会使线条略变微长
  * lineJoin：指定两条线之间的连接点形状，可选值
    * round：创建圆角
    * bevel：创建斜角
    * miter：默认，创建尖角
  * miterLimit：与lineJoin一起使用，当lineJoin设置为miter时，可用于确定线条交接点的延伸范围

### 使用线型绘图

* 绘制圆形路径
* 绘制动态圆形
* 绘制吃豆人

# 处理Canvas中的图像

---

## 绘制图像

* 在HTML5中，不仅可以使用Canvas API来绘制图形，还可以读取磁盘或网络中的图像文件，然后使用Canvas API将该图像绘制在画布中
* 绘制图像时，是要使用drawImage方法，定义如下：
  * drawImage(image,x,y)
    * image：可以是image元素、video元素、js中的Image对象
    * x：起始横坐标
    * y：起始纵坐标
* drawImage(image,x,y,w,h)
  * w：宽度
  * h：高度

  ```js
  function initial(){
    var elem=document.getElementByI('canvsa')
    var canvas=elem.getContext('2d')
    for(var i=0;i<3;i++){
      image=new Image()
      img.src="img/monster3.gif"
      image.onload=function(){
        canvas.drawImage(image,i*50,i*50,150,148)
      }
    }
  }

## 平铺图像

* 所谓平铺图像就是用按一定比例缩小后的图像将画布填满。实现图像平铺的方式有两种，一种是前面介绍的drawImage方法；另一种是使用上下文对象的createPattern()方法
* 语法：canvas.createPattern(image,type)
* image：要平铺的图像
* type：平铺方式
  * no-repeat：不平铺
  * repeat-x：水平方向平铺
  * repeat-y：垂直方向平铺
  * repeat：全方向平铺

  ```js
  function initial(){
    elem=document.getElementById('canvas')
    canvas=elem.getContext('2d')
    var img=new Image()
    img.src="img/monster3.gif"
    var ptrn=canvas.createPattern(img,'repeat')
    canvas.fillStyle=ptrn
    canvas.fillRect(0,0,400,300)
  }

## 切割元素

* 在Canvas中，不仅能以各种方式平铺绘制的图像，还可以通过上下文环境中的clip()方法切割画布中的绘制图像。clip()方法调用格式如下：
* canvas.clip()
* 该方法用于切割使用路径方式在画布中绘制的区域。因此，在使用该方法前，必须使用路径在画布中绘制一个区域

  ```js
  elem=document.getElementById('canvas')
    canvas=elem.getContext('2d')
    image=new Image()
    image.src="img/flower.jpg"
    image.onload=function(){
    canvas.drawImage(image,0,0,280,190)
    }
    canvas.beginPath()
    canvas.arc(140.95.60.0,Math.PI*2,true)   canvsa.closePath()
    canvas.clip()

### 在画布中绘制图像

* 绘制图像
* 动画绘制图像

## 画布方法

* 状态方法
  * save()，保存当前画布属性、状态
  * restore()，恢复画布属性、状态
* 转换方法
  * scale()，缩放当前绘图更大或更小
  * translate()，重新映射画布上的(0,0)位置
  * rotate()，旋转当前画布，公式为 degress * Math.PI / 180

## 旋转的图像

* 绘制旋转的图像