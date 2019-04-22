[toc]
# 接口概述

---

## 接口的支持

* 用法：微信将小程序的所有接口都做成了 wx.功能() 函数。这个函数用object作为参数
* 大部分接口都有seccess fail complete 方法（不完全）
* 有的还有一些其它的存储数据用 的键
* 格式如下

  ```js
  wx.xx({
	  其他值：键,
	  success:function(res){ },
	  fail;function(e){},
	  complete:function(e){}
  })
  ```

# 网络和媒体

---

## 网络

接口|用途
---|---
wx.request|发起请求
wx.uploadFile|上传文件
wx.downloadFile|下载文件
wx.connectSocket|创建连接
wx.sendSocketMessage|发送信息
wx.closeSocket|关闭连接
wx.onSocketOpen|当连接打开的时候
wx.onSocketError|当连接出错的时候
wx.onSocketMessage|当发送请求的时候
wx.onSocketClose|当连接关闭的时候

* request：对象中的键的设定

  ```js
  wx.request({
    url:'test.php',//仅为示例，并非真是的接口地址
    data:{
      x:'',
      y:''
    },
    header:{
      'contend-type':'application/json'
    },
    success:function(res){
      console.log(res.data)
    }
  })
  ```

## 媒体

接口|用途
---|---
wx.chooseImage| 选图
wx.previewImage|预览图
wx.getImage|获取图信息
wx.startRecord|开始录音
wx.stopRecord|停止录音
wx.playVoice|播放音频
wx.pauseVoice|暂停音频
wx.stopVoice|暂停音频
wx.getBackgroundAudioPlayerState|获取背景音乐状态
wx.palyBackGroundAudio|播放背景音乐
wx.pauseBackgroundAudio|暂停背景音乐
wx.seekBackgroundAudio|控制进度
wx.stopBackgroundAudio|停止背景音乐
wx.onBackgroundAudioplay|当背景音乐播放时
wx.onBackgroundAudioPause|当背景音乐暂停时
wx.onBackgroundAudioStop|当背景音乐暂停时
wx.chooseVideo|选择视频文件
wx.createAudioContext|创建音频

# 文件和缓存

---

## 文件

接口|用途
---|---
wx.saveFile|保存文件
wx.getSavedFileList|获取保存文件列表
wx.getSavedFileInfo|获取保存文件信息
wx.removeSavedFile|删除文件
wx.openDocument|打开页面

### 修改页面内容

* 点击后实现点赞数量不断增加
  * 获取原有值3020 再自增，再设置值
* 挑战：根据本地存储接口，可以实现点击赞之后不能点赞，API
  * wx.getStorage()
  * wx.setStorage()

## 缓存

接口|用途
---|---
wx.setStorage|异步保存本地存储
wx.getStorage|异步获取本地存储
wx.getStorageInfo|异步获取存储状态
wx.removeStorage|异步删除本地存储
wx.clearStorage|异步清除本地存储
wx.setStorageSync|同步设置本地存储
wx.getStorageSync|同步获取本地存储
wx.getStorageInfoSync|同步获取存储状态
wx.RemoveStorageSync|同步删除本地存储
wx.clearStorageSync|同步删除本地存储

### 试题小程序

* 改进守丧面的试题小程序一，让小程序有倒计时功能
  * 记录用户是否考过，从而让考过试的打开小程序不能重考
* 利用前面的案例
  * 挑战：改造以前的 2048变成小程序版。
  * 提升记录上次的 成绩 记录最高成绩到缓存中
  
# 其它常用接口

---

## 位置

接口|用途
---|---
wx.getLocation|获取坐标
wx.chooseLocation|选择坐标
wx.openLoaction|打开坐标
wx.createMapContext|创建地图上下文

### 膜拜单车

* 首页插入地图项
  * 搜索附近功能，得到当前你的位置输出，通过request认证过的url获取附近的车
  * 绘制图表

## 设备

接口|用途
---|---
wx.getSystemInfo|异步得到系统信息
wx.getSystemInfoSync|同步获得系统信息
wx.getNetworlType|获取网络类型
wx.onAccelerometerChange|当中里感应改变的时候
wx.onCompassChange|当罗盘数据改变的时候
wx.makePhoneCall|拨打电话
wx.scanCode|调用二维码扫描

### 触摸翻页

* 缓动翻页新闻列表

## 界面

* 弹框
  接口|用途
  ---|---
  wx.showToast|显示弹框
  wx.hideToast|隐藏弹框
  wx.showModal|显示模拟弹框
  wx.showActionSheet|显示操作菜单

* 导航条和导航
  接口|用途
  ---|---
  wx.setNavigationBarTitle|设置导航标题
  wx.showNavigationBarLoading|设置导航动画
  wx.hideNavigationBarloading|隐藏导航动画
  wx.navigateTo|设置导航到
  wx.redirectTo|定向到
  wx.switchTab|Tab 切换到
  wx.navigateBack|导航回滚

* 动画
  接口|用途
  ---|---
  wx.createAnimation|创建动画

* 绘图
  接口|用途
  ---|---
  wx.navigateTo|设置导航到
  wx.redirectTo|定向到
  wx.switchTab|Tab 切换到
  wx.navigateBack|导航回滚

* 下拉刷新
  接口|用途
  ---|---
  wx.onPullDownRefresh|当下拉刷新时
  wx.stopPullDownRefresh|停止下拉刷新

## 开放接口

* 登录
  接口|用途
  ---|---
  wx.login|登录
  wx.checkSession|检查会话
  wx.getUserInfo|获取用户信息
  wx.login|登录
  wx.checkSession|检查会话
  wx.getUserInfo|获取用户信息

* 支付
  接口|用途
  ---|---
  wx.requestPayment|调用支付
  wx.onShareAppMessage|分享软件

### 接口

* API汇总