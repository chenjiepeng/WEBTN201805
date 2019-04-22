[TOC]
# 条件渲染

## Tab选项卡

* 上面的每个按钮添加一个不同事件
* 下面的每个显示隐藏用一个变量控制

  ```wxml
  <view class="container">
    <view class="top">
      <view bindtap="ch1">新闻</view>
      <view bindtap="ch1">财经</view>
      <view bindtap="ch1">体育</view>
    </view>
    <view class="bottom">
      <view style="display:{{a1}}">123</view>
      <view style="display:{{a2}}">333</view>
      <view style="display:{{a3}}">444</view>
    </view>
  </view>
  ```

* 每个事件里面控制三个变量的值实现显示隐藏

  ```js
  Page({
    data:{
      a1:"block",
      a2:"none",
      a3:"none",
      arr:["block","none","none"]
    },
    ch1:function(){
      var that=this;
      that.setData({
        a1:"block",
        a2:"none",
        a3:"none",
      })
    }
    ,
    ch2:function(){
      var that=this;
      that.setData({
        a1:"noen",
        a2:"block",
        a3:"none",
      })
    }
  ```  

## 事件传参

* 因为微信小程序调用函数没有小括号，那么传参怎么办？
* 可以使用事件上的event来访问

  ```wxml
  <view id="tapTest" data-hi="WeChat" bindtap="tapName"> Click me!
  </view>
  ```

  ```js
  Page({
    tapName:funcion(event){
      console.log(event.target.dataset.hi)
  })
  ```

* 利用带参函数解决

  ```js
  Page({
    data:{
      a1:"block",
      a2:"none",
      a3:"none",
      arr:["block","none","none"]
    },
    ch:function(e){
      var that=this;
      var m=e.target.dataset.param
      if(m==0){
        that.setData({
          a1:"block",
          a2:"none",
          a3:"none"
        })
      }else if(m==1){
        that.setData({
          a1:"noen",
          a2:"block",
          a3:"none",
        })
      }
    }
  )}
  ```

* 如果把三个变量省略写成数组更容易维

  ```wxml
  <view class="bottom">
    <view style="display:{{arr[0]}};">123</view>
    <view style="display:{{arr1]}};">333</view>
    <view style="display:{{arr[0]}};">444</view>
  <view>
  ```

  ```wxml
  <view class="top">
    <view bindtap="ch" data-param="0" class="{{brr[0]}}">新闻</view>
    <view bindtap="ch" data-param="1" class="{{brr[1]}}">财经</view>
    <view bindtap="ch" data-param="2" class="{{brr[2]}}">体育</view>
  </view>
  ```

### 选项卡

* 点击后实现tab切换效果-每个按钮对应一个函数
升级1：利用传递参数只写一个函数
升级2：改变数组的值 上下都需要改变

## 条件渲染

* Wxml可以使用一些特殊的语法让自己的结构根据变量来进行变化

  ```wxml
  <view wx:if="{{condition}}"> True </view>
  ```

  ```wxml
  <block wx:if="{{true}}">
    <view> view1 </view>
    <view> view2 </view>
  </block>
  ```

  ```wxml
  <view wx:if="{{lengh > 5}}"> 1 </view>
  <view wx:elif="{{lengh > 2}}"> 2 </view>
  <view wx:else> 3 </view>
  ```

### 对选项卡使用条件渲染

* Tab选项卡，修改变量，让对应的view显示
* 利用条件渲染

  ```js
  Page({
    data:{
      brr:["active","",""]
      arr:0
    },
    ch:function(e){
      var that=this;
      var m=parseInt(e.target.dataset.param)
      var tmparr=that.data.arr
      var tmpbrr=that.data.brr
      for (var i=0;i<that.data.brr.length;i++){
        tnpbrr[i]=""
      }
      tmparr=m
      tmpbrr[m]="active"
      that.setData({
        arr:tmparr,
        brr:tmpbrr
      })
    }
  })
  ```

# 列表渲染

## 列表渲染

* For指令的使用

  ```wxml
  <view wx:for="{{array}}">
    {{index}}:{{item.message}}
  </view>
  ```

  ```wxml
  <view wx:for-index="idx" wx:for-item="itemName">
    {{idx}}:{{itemName.message}}
  </view>
  ```

## 模板渲染

```wxml
<template name="msgItem">
  <view>
    <text>{{index}}:{{msg}}</text>
    <text> Time:{{time}}</text>
  </view>
</template>
```

```wxml
<template is="msgItem" data="{{...item}}"/>
```

```js
Page({
  data:{
    item:{
      index:0,
      msg:'this is a template',
      time: '2016-09-15'
    }
  }
})
```

### 使用列表渲染

* Tab选项卡，修改变量，让对应的view显示
* 利用条件渲染改变下面的显示隐藏，利用列表渲染改变上面的焦点

# 复杂事件

## 复杂事件

* bindtap类似onclick事件，那么在小程序只有这一个事件码？
  * 其实还有很多bindlongtap、bindtouchstart、bindtouchmove、bindtouchend、bindtouchcancel
  * 上述事件中的bind还可以换为catch，也就是catchtap
  * 另外特殊组件还有特殊事件 比如bindinput
* 事件中的e包含触摸点和输入等信息

  ```wxml
  <view bindtap=" chg "></view>//index.html

  Page({
    chg:function(e){
      console.dir(e)
    }
  })//index.js
  ```

* 事件中的e包含触摸点和输入等信息

  | 键名           | 用途           |
  | -------------- | -------------- |
  | changedTouches | 动点坐标数组   |
  | currentTarget  | 当前触发事件   |
  | detail         | 其它详情       |
  | timeStamp      | 时间戳         |
  | touches        | 屏幕触摸点数组 |
  | type           | 时间类别       |

### 使用复杂事件

* 制作一种算法，可以判断触摸的方向
* 利用触摸事件制作一款小程序版本的放大图片效果
* 在手指滑动中可以在悬浮区域显示详细信息

## 获取输入内容

* event内幕
* 输入事件 bindinput
* 输入内容获取其中的值 e.derail.value

### 计算器

* 简单的计算器
  * 三个输入框，前两个是输入的，最后一个是输出结果的
  * 然后有个计算按钮。当点击计算的时候可以将前两个框中的数据计算和放入地三个框中
* 汇率计算器
  * 输入一个数字然后，根据这个数组进行计算
  * 不考虑汇率的变化（获得联网的比率数据）
  * 参考汇率助手

# 引用

## 引用

* wxml分片-模板外置 tmp.wxml

  ```wxml
  <template name="item">
    <text>{{text}}</text>
  </template>
  ```

  ```wxml
  <import src= "tmp.wxml"/>
  <template is="item" data="{{text:'forbar'}}"/>
  ```

  ```wxml
  <include src="header.wxml"/>
  <view> body </view>
  <includes src="footer.wxml"/>
  ```

* js文件分片-公用代码放一个单独js文件com.js

  ```js
  function sayHello(name){
    console.log(name)
  }
  module.exports.sayEx = sayHello
  ```

  ```js
  var cm=require( 'com.js')
  Page({
    say:function(){ cm.sayEx( 'hello')}
  })
  ```

### 引用案例

* 利用定时器显示当前时间 innerHTML+setInterval
* 利用定时器和旋转css布局
* 挑战：改造以前 2048变成小程序版
  * 尝试把功能js外置出去成单独文件以减少主文件大小