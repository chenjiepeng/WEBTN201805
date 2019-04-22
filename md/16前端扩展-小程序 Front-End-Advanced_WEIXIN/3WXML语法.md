[toc]

# WXML语法基础

## 数据绑定

* 使用ng的用法用{{}}调用变量

  ```wxml
  <view>{{ message }}</view>
  ```

* 调用的是js中page方法中对象的data的变量

  ```js
  Page({
    data:{
      message:'Hello MINA! '
    }
  })
  ```

## 数据获取

* 数据的获取

  ```js
  var a=this.data.key
  ```

## 数据修改

* 数据的设置

  ```js
  this.setData({
    key:60
  })
  ```

## 简单事件

* 简单事件使用。

  ```wxml
  <view id="tapText" data-hi="WeChat" bindtap= "show"> Click me!
  </view>
  ```

  ```html
  <div onclick="show()">Click me!</div>
  ```

  ```js
  Page({
    tapName:function(event){
      console.log(event)
    }
  })
  ```

# 交互区别

---

## 修改innerHTML

* 小程序无DOM所以也不存在innerHTML属性，把要修改的内容变成变量来

  ```wxml
  <view>你好白<view>
  <button>点击我修改view中的文字</button>
  ```

* 改为变量

  ```wxml
  <view>{{var}}</view>
  <button>点击我修改view中的文字</button>
  ```

* 设置初始值

  ```js
  Page({
    data:{ va:"你好白" }
  })
  ```

* 添加事件

  ```wxml
  <view>{{va}}</view>
  <button bindtap= "show ">点击我修改view中的文字</button>
  ```

* 写函数事件

  ```js
  Page({
    data:{va:"你好白" }，
    show:function(){
      this.setData({
        va:" 你好黑"
      })
    }
  })
  ```

### 修改页面内容（一）

* 利用按钮控制文中数量-由0到1的过程
* 美团外卖小程序中的控制订餐数量的按钮
* 利用按钮控制文中数量比上次自增-连续自增
* 美团外卖小程序中的控制订餐数量的按钮

## 修改style

* 添加事件

  ```wxml
  <view style="display:{{va}}">点击按钮才能看到我</view>
  <button bindr=tap= "show">点击我</button>
  ```

* 写事件函数

  ```js
  Page({
    data:{va:" none"},
    show:function(){
      this.setData({
        va:" block"
      })
    }
  })
  ```

## 修改class

* 添加事件

  ```wxml
  <view class= "{{va}}" >点击按钮才能看到我</view>
  <button bindtap="show" >点击我</button>
  ```

* 写事件函数

  ```js
  Page({
    data:{va:" old" },
    show:function(){
      this.setData({
        va:" nn"//修改va全局变量的值由old类（初始值）修改为 nn类实现样式变化
      })
    }
  })
  ```

* xx.wxss

  ```css
  .old{ display:none; }
  .nn{ display:block; color:#f00;}
  /*这种修改方式更容易控制样式，占用的变量少*/
  ````

### 修改页面内容（二）

* 利用按钮控制文中数量比上次自增
* 当按钮数量大于1实现减号按钮的显示，小于1减号按钮消失
* 美团外卖小程序 点餐数量

## 定时修改

* 因为微信小程序没有window对象，但是定时器和之前学习的一样

  ```js
  timer=setInterval(function(){
    console.log( "df" )
  },30)
  ```

  ```js
  clearInterval(timer)
  ```

* 我们将定时器中的代码写到page函数之外

  ```js
  var that=this
  that.data.timer=setInterval(function(){
    detail(that)
  },30)
  ```

  ```js
  function detail(o){
    clearInterval(o.data.timer)
  }
  ```

---
WXML高级语法

* 条件渲染
  * Tab选项卡
  * 事件传参
  * 条件渲染
* 列表渲染
  * 列表渲染
  * 模板渲染
* 复杂事件
  * 复杂事件
  * 获取输入内容
* 引用
  * 引用