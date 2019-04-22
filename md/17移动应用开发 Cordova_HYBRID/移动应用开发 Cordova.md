# PhoneGap概述

## 认识PhoneGap

---

### phoneGap介绍

* PhoneGap是一个基于HTML、CSS、JS创建跨平台移动应程序的快速开发平台

### PhoneGap历史

* 08年在苹果举行的DevCamp上，一名iOS程序员无法忍受oc的语法，PhoneGap产生
* 09年-10年 支持平台到6个（iOS、Andoird、BlackBerry、Symbian、Palm）
* 11年，发布1.0版本
* 11年10月，被Adobe收购
* 截止到16年7月份，应更新到6.2版本，已经支持到window10

### PhoneGap与Cordova关系

* PhoneGap在11年被Adobe收购后，将核心的关于跨平台代码贡献给Adobe，Adobe将这些代码开源并称之为Cordova
* 区别：PhoneGap是一个商业产品，Cordova为开源的、核心的跨平台模块
* 联系：Cordova与PhoneGap关系就像，WebKit与Chrome的关系

### 推荐网站

## 环境搭建

---

### 方式1：命令行方式

* Windows+R，输入cmd，点击确定，进入命令行操作界面
* 通过npm安装cordova：
  * 方式1：npm install -g cordova（速度很慢，有时无法下载）
  * 方式2：npm.taobao.org 这是淘宝做的镜像，和npm官网资源保持一致（每10分钟更新一次）

     ```cmd
     npm install -g cordova --registry
     http://registry.npm.taobao.org info
     ```

* 检查是否安装成功
  * 直接在命令行中输入cordova -version ，如果能够显示版本信息，安装成功
* Cordova常用命令
  * 增加或删IOS平台：
    * cordova platform add ios
    * cordova platform remove ios
  * 增加或删Android平台：
    * cordova platform add android
    * cordova platform remove android
  * 查看当前项目所支持的平台
    * cordova platform ls
  * 检查coredova项目是否具备build条件：
    * cordova requirement
  * 检查cordova项目可运行的设备列表
    * cordova run -list
  * 编译cordova项目为指定平台下的应用
    * cordova run android
    * cordova run ios

### 方式2：图形化工具

* XDK（Intel）
* VisualStudio（Microsoft）
* PhoneGap官方工具（PhoneGap）
* 使用PhoneGap官方工具的步骤：
* http://PhoneGap.com/getstarted/,
* 步骤1：下载安装PC端（Mac、Windows）
* 步骤2：安装移动端（Android、IOS、Windows）
* 步骤3：使用PC端，创建工具，同时自动启动服务器
* 步骤4：同一局域网下，将移动端打开，输入PC的IP和端口，点击connext连接PC
* 步骤5：此时修改PC端代码，服务器会自动同步代码到移动端
* PhoneGap官方工具原理图：

### 官网工具之PC端

### 官方工具之移动端

* ADB（Android Debug Bridge），是一个命令行工具，可以和模拟器或者Android真机进行通讯，典型应用：将apk应用安装到模拟器或者真机上
* adb常用命令：
  * adb version 查看adb的版本
  * adb install **.apk 安装某个应用
  * adb devices 获取连接到本电脑的设备列表
  * adb -s "emulator-5554" install **.apk 为指定的某个设备安装某个应用
  * adb shell ** 后边可以接一些命令，比如查看目录，或者查看某个文件目录
  * adb shell ls `//查看当前目录有哪些内容`
  * adb start-server
    adb kill-server

## Hello PhoneGap

---

### Hello PhoneGap

* 修改工程代码，来实现Hello PhoneGap

* 首先，确保PhoneGap的PC端和移动端已经在运行；

* 然后，打开WebStorm，打开附件中的工程，修改制定的文件，具体请看图

#### 使用 PhoneGap

* 搭建 PhoneGap 的开发环境
* 创建应用

# PhoneGap开发

## PhoneGap基础知识

---

### 基础知识

* PhoneGap最大的优势在于能够调用底层的硬件，那么对于PhoneGap来说，是如何操作硬件的？

* 举个例子，比如说PhoneGap中有device这个类，在这个类中，可以通过调用js代码，来实现在各个平台（Android、IOS等）的设备信息，那么是如何实现的？
  * PhoneGap提供了各种plugin来操作不同的硬件，以device为例（该对象包含设备信息），我么在通过js调用device信息时，plugin会根据当前所处的平台调用对应的原生代码得到json对象并返回给用户

### 常用事件

* PhoneGap除了上述案例中的deviceready事件，还支持什么事件？常用的十余个事件如下所示：

#### 使用PhoneGap提供的事件

* 使用PhoneGap提供的按键事件，指定回调函数执行指定的操作
* 分析
  * 首先确定事件名称
  volumedownbutton/volumeupbutton
  * 添加该事件的监听，监听到后调用alert提醒

## 读取硬件信息

---

### 核心API介绍

* PhoneGap可以操作的硬件很多，核心API如下：

### 设备信息

* 如果要获取详细的设备信息，需要用到device类，那么device有哪些属性可供用到？
* 找到资料中的中文手册，点击左侧列表中的Device，即可查看device中的属性
* 通过查看文档，device类的属性有name、platform、uuid、version、phonegap，那么如何使用这些属性？

### 加速度传感器

* 加速度传感器是一种用来检测物体相对运动方向以及沿着xyz三个方向运动的不见，phonegap提供了accelerometer类用来接收来自加速度传感器的数据，从而检测到设备在控件上的位置变化，比如说现在很流行的手环，或者说实现类似微信摇一摇功能的，都是使用传感器附加上一些算法来实现的。
* 如何使用？
  * navigator.accelerometer.getCurrentAcceleration(accelerometerSuccess,accelerometerError);

### 音视频录制

* 在phonegap中，如果需要进行录音、拍照、录制视频，可以使用phonegap提供的以下方法：
  * captureAudio，captrueImage、captureVideo
* 如何使用？
  * navigator.device.capture.captureAudio(captureSuccess,captureError,options)
  * 需要手工指定方法执行成功、失败的回调函数

### 文件读写操作

* phoneGap通常是将一类操作完全封装在同一个对象中，比如设备信息都在device类中，但是phoneGap对文件的操作方法却封装在了许多不同的对象中，所以这是phoneGap稍复杂的一类对象。
* 文件如何完成基本的读写操作？
  * fileReader，是一个允许用户读取文件的对象，文件以文本或者Base64编码的字符串样式读出来，用户注册自己的事件监听器来接受loadstart、loadend等事件
  * fileWriter 是一个允许用户进行读写操作的对象

#### 使用PhoneGap读取硬件信息

* 使用API读取硬件信息